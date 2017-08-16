# 编译tmpl
## 将HTML <%= %> 转化成function
前端使用的模板系统  或  后端Javascript环境发布页面

### 假定事先设置数据为
```javascript
var data={
    title:'baiduTemplate',
    list:['test1<script>','test2','test3']
}
```

### 注释

```html
<!-- 模板中可以用HTML注释 -->  或  <%* 这是模板自带注释格式 *%>

<% //分隔符内支持JS注释  %>
### 输出一个变量

//默认HTML转义，如果变量未定义输出为空
<%=title%>  

//不转义
<%:=title%> 或 <%-title%>

//URL转义，UI变量使用在模板链接地址URL的参数中时需要转义
<%:u=title%>

//UI变量使用在HTML页面标签onclick等事件函数参数中需要转义
//“<”转成“&lt;”、“>”转成“&gt;”、“&”转成“&amp;”、“'”转成“\&#39;”
//“"”转成“\&quot;”、“\”转成“\\”、“/”转成“\/”、\n转成“\n”、\r转成“\r”
<%:v=title%>

//HTML转义（默认自动）
<%=title%> 或 <%:h=title%>
```


### 判断语句

```html
<%if(list.length){%>
    <h2><%=list.length%></h2>
<%}else{%>
    <h2>list长度为0<h2>
<%}%>
```

### 循环语句

```html
<%for(var i=0;i<list.length;i++){%>
        <li><%=list[i]%></li>
<%}%>
```

### 用户可以自定义分隔符，默认为 <% %>，如：
```javascript
//设置左分隔符为 <!
baidu.template.LEFT_DELIMITER='<!';

//设置右分隔符为 <!  
baidu.template.RIGHT_DELIMITER='!>';
```

### 自定义默认输出变量是否自动HTML转义

```javascript
//设置默认输出变量是否自动HTML转义，true自动转义，false不转义
baidu.template.ESCAPE = false;
```
