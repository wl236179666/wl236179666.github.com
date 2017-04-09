---
layout: post
title: jQuery发送ajax的几种情况
date: 2017-04-09 21:56
---

<p>详细介绍用jQuery发送ajax的几种情况,以及$.ajax(),$.get(),$.post()三者的关系.
ajax是一个方法,方法的参数{}是一个对象,里面是对象的属性和值</p>

### $.ajax()
{% highlight ruby %}
<script>
    //ajax是一个方法,方法的参数{}是一个对象,里面是对象的属性和值
    $.ajax({
        type    : "post",  //发送类型,get或post,默认为get
        async   : true,  //true为异步,false为同步,默认为true
        url      : "http://localhost:8080/comment.php", //请求的后台地址
        data     : "name=wang&comment=hello", //往后台传递的参数,可以是object或string类型,但最终都会被转换为字符串格式
        data     : {name:"wang",comment:"hello"},
        data     : {foo:["bar1","bar2"]},//被转换为 &foo=bar1&foo=bar2
        data     : $("#form1").serialize(),
        dataType : "text", //预期服务器返回的数据类型,可以为text,json,html,xml,script等,text表示返回数据为纯文本字符串
        cache    : true,  //true使用浏览器缓存,false不适用,默认为true
//        contentType :   //string类型,默认为"application/x-www-form-urlencoded",适合大多数应用场合
        success   : statechange  //成功时的回调函数
    });

    function statechange(data) {
        //用于接收应答数据的回调函数,参数在data中
    }
</script>
{% endhighlight %}