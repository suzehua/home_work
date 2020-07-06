<template>
    <div class="hello" style="width: 60%;margin: 50px auto">
        <div style="margin: 20px 0px">
            <el-button style="float: left" @click="modelalert" type="primary">添加員工</el-button>
            <!--            <el-button @click="toggleSelection()">取消选择</el-button>-->
        </div>

        <el-table
                ref="multipleTable"
                :data="tableData"
                tooltip-effect="dark"
                style="width: 100%"
                @selection-change="handleSelectionChange">
            <el-table-column
                    type="selection"
                    width="55">
            </el-table-column>
            <el-table-column
                    label="姓名"
                    width="120">
                <template slot-scope="scope">{{ scope.row.name }}</template>
            </el-table-column>
            <el-table-column
                    prop="phone"
                    label="手机"
                    width="120">
            </el-table-column>
            <el-table-column
                    prop="mail"
                    label="邮箱"
                    show-overflow-tooltip>
            </el-table-column>
            <el-table-column
                    prop="jobTitle"
                    label="职务"
                    show-overflow-tooltip>
            </el-table-column>
            <el-table-column
                    prop="department"
                    label="部门"
                    show-overflow-tooltip>
            </el-table-column>
            <el-table-column
                    label="操作"
                    fixed="right"
                    align="center"
                    header-align="center"
            >
                <template slot-scope="scope">
                    <el-button type="text" size="small">
                        编辑
                    </el-button>
                </template>
            </el-table-column>
        </el-table>
        <div>
            <el-pagination
                    @size-change="handleSizeChange"
                    @current-change="handleCurrentChange"
                    :current-page="pageNum"
                    :page-sizes="[3, 6, 9, 15]"
                    :page-size="pageSize"
                    layout="total, sizes, prev, pager, next, jumper"
                    :total="data.length">
            </el-pagination>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        },
        data() {
            return {
                data: [{
                    name: '王小虎1',
                    phone: 15515111511,
                    mail: '123456789@qq.com',
                    jobTitle: '部长',
                    department: '吃饭部',
                    date: '2016-05-03',
                }, {
                    name: '王小虎2',
                    phone: 15515111511,
                    mail: '123456789@qq.com',
                    jobTitle: '部长',
                    department: '吃饭部',
                    date: '2016-05-03',
                }, {
                    name: '王小虎3',
                    phone: 15515111511,
                    mail: '123456789@qq.com',
                    jobTitle: '部长',
                    department: '吃饭部',
                    date: '2016-05-03',
                }, {
                    name: '王小虎4',
                    phone: 15515111511,
                    mail: '123456789@qq.com',
                    jobTitle: '部长',
                    department: '吃饭部',
                    date: '2016-05-03',
                }, {
                    name: '王小虎5',
                    phone: 15515111511,
                    mail: '123456789@qq.com',
                    jobTitle: '部长',
                    department: '吃饭部',
                    date: '2016-05-03',
                }, {
                    name: '王小虎6',
                    phone: 15515111511,
                    mail: '123456789@qq.com',
                    jobTitle: '部长',
                    department: '吃饭部',
                    date: '2016-05-03',
                }, {
                    name: '王小虎7',
                    phone: 15515111511,
                    mail: '123456789@qq.com',
                    jobTitle: '部长',
                    department: '吃饭部',
                    date: '2016-05-03',
                }, {
                    name: '王小虎8',
                    phone: 15515111511,
                    mail: '123456789@qq.com',
                    jobTitle: '部长',
                    department: '吃饭部',
                    date: '2016-05-03',
                }],
                multipleSelection: [],
                pageNum: 1,
                pageSize: 3,
                tableData: [{
                    name: '王小虎1',
                    phone: 15515111511,
                    mail: '123456789@qq.com',
                    jobTitle: '部长',
                    department: '吃饭部',
                    date: '2016-05-03',
                }, {
                    name: '王小虎2',
                    phone: 15515111511,
                    mail: '123456789@qq.com',
                    jobTitle: '部长',
                    department: '吃饭部',
                    date: '2016-05-03',
                }, {
                    name: '王小虎3',
                    phone: 15515111511,
                    mail: '123456789@qq.com',
                    jobTitle: '部长',
                    department: '吃饭部',
                    date: '2016-05-03',
                }]

            }
        },

        methods: {
            toggleSelection(rows) {
                if (rows) {
                    rows.forEach(row => {
                        this.$refs.multipleTable.toggleRowSelection(row);
                    });
                } else {
                    this.$refs.multipleTable.clearSelection();
                }
            },
            handleSelectionChange(val) {
                this.multipleSelection = val;
            },
            handleCurrentChange(pageNumber) {
                alert(this.pageNum +  '_' + this.pageSize +  '_' + pageNumber)
                this.tableData = []
                var start = (pageNumber - 1) * this.pageSize
                var end = start + this.pageSize
                this.data.forEach((item, index) => {
                    if (start <= index && end > index) {
                        this.tableData.push(item)
                    }
                })
            },
            handleSizeChange: function (size) {
                this.pageSize = size
                var start = (this.pageNum - 1) * this.pageSize
                var end = start + this.pageSize
                this.data.forEach((item, index) => {
                    if (start <= index && end > index) {
                        this.tableData.push(item)
                    }
                })
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
