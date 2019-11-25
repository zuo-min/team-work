<template>
  <div class="dashboard-container">
    <div class="app-container">
      <el-row>
        <el-col :span="6">
          学科:
          <el-select v-model="searchForm.subjectID" placeholder="请选择学科">
            <el-option
              v-for="item in subjectIDList"
              :key="item.value"
              :label="item.label"
              :value="item.value"
            ></el-option>
          </el-select>
        </el-col>
        <el-col :span="6">
          难度：
          <el-select v-model="searchForm.difficulty" placeholder="请选择">
            <el-option
              v-for="item in difficultyList"
              :key="item.value"
              :label="item.label"
              :value="item.value"
            ></el-option>
          </el-select>
        </el-col>
        <el-col :span="6">
          试题类型：
          <el-select v-model="searchForm.questionType" placeholder="请选择">
            <el-option
              v-for="item in questionTypeList"
              :key="item.value"
              :label="item.label"
              :value="item.value"
            ></el-option>
          </el-select>
        </el-col>
        <el-col :span="6"></el-col>
      </el-row>
    </div>
  </div>
</template> 

<script>
// 对api接口方法进行导入
import { simple } from '@/api/hmmm/subjects.js'

// import { difficulty, questionType } from '@/api/hmmm/constants.js'
// 设置别名
import {
  difficulty as difficultyList,
  questionType as questionTypeList
} from '@/api/hmmm/constants.js'

export default {
  name: 'QuestionsList',
  // subjectID   学科
  // difficulty   难度
  // questionType   试题类型
  data() {
    return {
      // 系列数据信息
      subjectIDList: [], // 学科
      // difficultyList: difficulty, // 难度
      // questionTypeList: questionType, // 试题类型
      // 简易成员赋值
      difficultyList, // 难度
      questionTypeList, // 试题类型

      // 搜索表单对象
      searchForm: {
        subjectID: '', // 学科
        difficulty: '', // 难度
        questionType: '' // 试题类型
      }
    }
  },
  created() {
    this.getSubjectIDList()
  },
  methods: {
    // 获得下拉列表学科数据
    async getSubjectIDList() {
      var rst = await simple()
      // console.log(rst)
      // 把数据给data成员
      this.subjectIDList = rst.data
    }
  }
}
</script>

<style scoped>
</style>
