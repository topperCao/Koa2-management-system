# management_system 
## 简介
这是一个基于`koa2`的后台管理系统 

使用 `jQuery` 作为前端JS框架  
使用 `bootstrap` 作为CSS框架  
使用 `pug`/`jade` 和 `handlebars` 作为HTML页面模板  
使用 `PostgreSql` 存储业务数据   
使用 `mongodb` 存储 `session`   
使用 `Bookshelf` + `Knex` 作为 `ORM` 和 `Query Builder`  
使用 `Sentry` 作为错误信息的收集反馈平台   
采用 `AJAX` 处理前端请求     

目录结构和babel的配置参考了 https://github.com/17koa/koa-demo   
原链接似乎已经被删掉了，这个是我fork过来的版本 https://github.com/liuyueyi1995/koa2-demo    
网站的前端代码来源于我之前的一个项目  https://github.com/liuyueyi1995/oa 

---
## 基本任务  

- A 后台管理员的登录注册  
- B 已经在EVA平台上注册的用户信息管理  
- C 用户的角色管理  
- D 机构管理  
- E 项目管理  
- F 通过后端分页+`AJAX`显示查询得到的内容  

---
## 完成度  

- 基本的MVC结构已经完成；  
- 任务A已全部完成，包括注册、登录、session读写；  
- 任务B已全部完成，包括用户信息查询、模糊搜索、添加、删除、修改基本信息、修改密码；  
- 任务C已全部完成，包括多表查询、模糊搜索、级联下拉菜单的处理、信息添加和删除；  
- 任务D已全部完成，包括机构信息查询、模糊搜索、添加、删除、修改；  
- 任务E已基本完成，包括项目信息查询、模糊搜索、添加、删除、修改； 
- 所有的下拉菜单已经修改完成；  
- 加入了日期控件；  
- 部分表单的呈现形式做了改良；  
- 任务F已经全部完成；  

--- 
## TODOs   
目前的模糊搜索只完成了对`text`类型的数据的查询；   
对于日期、数字、布尔值的查询还有待完善(例如：timestamp、boolean)；  
对于用户输入的校验还有待完善(例如：email、phone)；  
对于数据的添加和修改还没有做判重(例如：当要添加的数据与已有数据发生冲突时，后台会报错，但还没有把相关信息告知前端)；     
将信息提示改成更友善的方式，替换原来的`alert`；    
把用户登录及其身份与可以使用哪些功能关联起来；  

---
## ISSUEs  

- 级联菜单，有bug，初始时，在没有点击study的情况下，机构名的列表出不来。 
  + 应该是`onchange`的问题。 
  + 未解决。 
- 修改数据库之后，`updated_at`值没有变化。  
  + 已解决，在`model`定义的时候加上`hasTimestamps:true`即可。  
- 修改了某一项之后，列表的顺序会被打乱。  
  + 已解决，在数据库返回搜索结果前使用`orderBy`进行排序。  
- 分页之后，如果修改了后面的内容，修改成功之后会跳转回第一页。 
  + 应该是`reload`的问题。 
  + 未解决。
- 分页之后，搜索结果如果有多页内容，点击第二页之后，会回到为搜索前的原始结果的第二页。 
  + 因为现在只有一个分页的AJAX处理，如果要让搜索后的结果可以分页展示，就需要再加一个状态。
  + 未解决。