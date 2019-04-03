<template>
    <el-card class="box-card" style="width:400px;margin:auto;">
        <div slot="header" class="clearfix">
            <span>注册</span>
        </div>
        <el-form ref="form" :rules="rules" :model="form" label-position="right" label-width="70px">
            <el-form-item label="用户名" prop="username">
                <el-input v-model="form.username" placeholder="请输入用户名"></el-input>
            </el-form-item>
            <el-form-item label="密码" prop="password">
                <el-input type="password" v-model="form.password" placeholder="请输入密码" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="手机号" prop="mobile">
                <el-input v-model="form.mobile" placeholder="请输入手机号"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="register">立即注册</el-button>
            </el-form-item>
        </el-form>
    </el-card>

</template>

<script>


    export default {
        name: "Register",
        data() {
            return {
                form: {
                    username: '',
                    password: '',
                    mobile: ''
                },
                rules: {
                    username: [
                        {required: true, message: '请输入用户名', trigger: 'change'},
                        {min: 2, message: '长度需要大于 2 个字符', trigger: 'change'}
                    ],
                    password: [
                        {required: true, message: '请输入密码', trigger: 'change'}
                    ],
                    mobile: [
                        {required: true, message: '请输入手机号', trigger: 'change'}
                    ]
                }
            }
        },
        methods: {
            register() {
                this.$refs['form'].validate((valid) => {
                    if (valid) {
                        this.axios.post('http://192.168.0.216:8081/user', this.form).then(response => console.log(response))
                    }
                })
            }
        }
    }
</script>

<style scoped>

</style>