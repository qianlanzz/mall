<template>
    <div>
        <el-form :rules="rules" ref="form" :model="loginForm" class="loginContainer">
            <h3 class="loginTitle">系统登录</h3>
            <el-form-item prop="username">
                <el-input type="text" auto-complete="false" v-model="loginForm.username" placeholder="请输入用户名"></el-input>
            </el-form-item>
            <el-form-item prop="password">
                <el-input type="password" auto-complete="false" v-model="loginForm.password" placeholder="请输入密码"></el-input>
            </el-form-item>
            <el-form-item prop="code">
                <el-input type="text" auto-complete="false" v-model="loginForm.code" placeholder="点击图片更换验证码" style="width: 200px;margin-right: 5px"></el-input>
                <img :src="authcode">
            </el-form-item>
            <el-checkbox v-model="checked" class="rememberme">记住我</el-checkbox>
            <el-button type="primary" style="width: 100%" @click="loginCommit">登录</el-button>

        </el-form>
    </div>
</template>

<script>
    export default {
        name: "Login",
        data(){
            return{
                authcode: '',
                loginForm:{
                    username: 'admin',
                    password: '123456',
                    code: '',
                },
                checked: true,
                rules: {
                    username: [{ required: true, message: '请输入用户名', trigger: 'blur' }],
                    password: [{ required: true, message: '请输入密码', trigger: 'blur' }],
                    code:[{ required: true, message: '请输入验证码', trigger: 'blur' }]
                }
            }
        },
        methods:{
            loginCommit(){
                this.$refs.form.validate((valid) => {
                    if (valid) {
                        alert('submit!');
                    } else {
                        this.$message.error('请填写所有字段');
                        return false;
                    }
                });
            }
        }
    }
</script>

<style scoped>

    .loginContainer{
        border-radius: 15px;
        background-clip: border-box;
        margin: 200px auto;
        width: 350px;
        padding: 15px 35px 15px 35px;
        background: #fff;
        border: 1px solid #24ea36;
        box-shadow: 0 0 25px #cac6c6;
    }
    /*标题样式*/
    .loginTitle{
        margin: 0px auto 40px auto;
        text-align: center;
    }
    /*记住我样式*/
    .rememberme{
        text-align: left;
        margin:0px auto 15px 0
    }

    /*.el-form-item__content{*/
    /*    display: flex;*/
    /*    align-items: center;*/
    /*}*/
</style>