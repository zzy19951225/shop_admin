<template>
    <el-container class="home">
  <el-header>
    <div class="logo"></div>
    <div class="logout">
      欢迎光临
      <a href="javascript:;" @click="logout">退出</a>
    </div>
      <h1 class="title">
      电商后台管理系统
    </h1>
  </el-header>
    <el-container>
      <el-aside width="200px">
            <el-menu
      default-active="2"
      class="el-menu-vertical-demo"
      background-color="#545c64"
      text-color="#fff"
      active-text-color="#ffd04b"
      unique-opened>
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>用户管理</span>
        </template>
        <el-menu-item-group>
          <el-menu-item index="1-1">
        <i class="el-icon-menu"></i>
        <span slot="title">用户列表</span>
      </el-menu-item>
        </el-menu-item-group>
      </el-submenu>
       <el-submenu index="2">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span>权限管理</span>
        </template>
        <el-menu-item-group>
          <el-menu-item index="2-1">
        <i class="el-icon-menu"></i>
        <span slot="title">角色列表</span>
      </el-menu-item>
          <el-menu-item index="2-2">
        <i class="el-icon-menu"></i>
        <span slot="title">权限列表</span>
      </el-menu-item>
        </el-menu-item-group>
      </el-submenu>
    </el-menu>
      </el-aside>
      <el-main>Main</el-main>
    </el-container>
    </el-container>
</template>

<script>
export default {
  methods: {
    logout() {
      this.$confirm('你确定要退出系统吗？', '温馨提示', {
        confirmButtonText: '确定',
        cancelButtonText: '取消',
        type: 'warning'
      })
        .then(() => {
          localStorage.removeItem('token')
          this.$router.push('/login')
          this.$message({
            type: 'success',
            message: '退出成功!',
            duration: 1000
          })
        })
        .catch(() => {
          this.$message({
            type: 'info',
            message: '已取消退出',
            duration: 1000
          })
        })
    }
  }
}
</script>

<style lang='less' scoped>
.home {
  height: 100%;
  .el-header {
    background-color: #b3c1cd;
    .logo {
      width: 180px;
      height: 60px;
      float: left;
      background: url('../assets/logo.png');
      background-size: contain;
      background-repeat: no-repeat;
      background-position: center center;
    }
    .logout {
      width: 180px;
      height: 60px;
      float: right;
      line-height: 60px;
      font-weight: 700;
      text-align: right;
      a {
        color: darkorange;
      }
    }
    .title {
      height: 60px;
      overflow: hidden;
      text-align: center;
      line-height: 60px;
      color: #fff;
      font-size: 28px;
    }
  }
  .el-aside {
    background-color: #545c64;
    .el-submenu {
      width: 200px;
    }
  }
  .el-main {
    background-color: #d4dfe4;
  }
}
</style>
