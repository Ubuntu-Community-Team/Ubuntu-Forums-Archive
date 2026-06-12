---
title: "Eclipse Blues"
date: 2011-09-13
forum: Programming Talk
---

### Post by kunal00731 on 2011-09-13
Hi ,
I am facing a strange issue and google could not help me either here. So now, i need your advices my friends.

I have a file called hello.jsp, the contents are :

[COLOR=Magenta][B]<?xml version="1.0" encoding="ISO-8859-1" ?>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Style-Type" content="text/css; charset=ISO-8859-1" />
<title>FILTER  BY POPUP</title>
<link rel="stylesheet" type="text/css" href="/WebContent/jquery-ui-1.8.14.custom.css" >    
</head>
<body>
<div class="ui-dialog ui-widget ui-widget-content ui-corner-all ui-draggable ui-resizable" style="display: block; z-index: 1002; outline: 0px none; position: absolute; height: auto; width: 600px; top: 21px; left: 279px;" tabindex="-1" role="dialog" aria-labelledby="ui-dialog-title-Filters">
<div class="ui-dialog-titlebar ui-widget-header ui-corner-all ui-helper-clearfix">
<span id="ui-dialog-title-Filters" class="ui-dialog-title">Filter By</span>
<a class="ui-dialog-titlebar-close ui-corner-all" href="#" role="button">
<span class="ui-icon ui-icon-closethick">close</span>
</a>
</div>
<div id="Filters" class="ui-dialog-content ui-widget-content" style="width: auto; min-height: 52.8333px; height: auto;">
<form action="">
<div id="FilterTabs" class="ui-tabs ui-widget ui-widget-content ui-corner-all">
<ul class="ui-tabs-nav ui-helper-reset ui-helper-clearfix ui-widget-header ui-corner-all">
<li class="ui-state-default ui-corner-top ui-tabs-selected ui-state-active">
<a href="#tabs-1">Country</a>
</li>
<li class="ui-state-default ui-corner-top">
<a href="#tabs-2">Funds</a>
</li>
<li class="ui-state-default ui-corner-top">
<a href="#tabs-3">Share Class</a>
</li>
<li class="ui-state-default ui-corner-top">
<a href="#tabs-4">Dates</a>
</li>
</ul>
</form>
</div>
</div>

</body>
</html>[/B][/COLOR]


[COLOR=Black]Now let us  come to the problem, according to the code typed in , i should have got a stylized formatted output like this:


[/COLOR]
[COLOR=Black]


Now, this comes up when i preview the code in eclipse, however when i try to view in the web browser using:
[http://localhost:8080/jspHello](http://localhost:8080/jspHello)

I get the output as:

[/COLOR]So that means that my style sheet is not getting [COLOR=Black] compiled here, perhaps ?

Or what am i missing here ?

BTW, I am  using JBOSS as the server to render my jsp here. 


[https://picasaweb.google.com/104666336491429831525/September132011#](https://picasaweb.google.com/104666336491429831525/September132011#) --> this is where the screens are located. In case u r not able to view this, let me tell you, the basic problem is -->  style sheet is working in preview option of eclipse but not in my browser(either IE or MF) .
[/COLOR]

---

### Post by kunal00731 on 2011-09-13
Hi the two outputs are  attached here , the first one is capture1 , second one is capture2.
The screens are at : [https://picasaweb.google.com/104666336491429831525/September132011#](https://picasaweb.google.com/104666336491429831525/September132011#)
If by any chance  u can't see them, the basic problem is --> style sheet is working in preview option of eclipse IDE but the same does not come up in the browser(either i.e. or M.F.).

---

### Post by ofnuts on 2011-09-13
In your browser, check if you can really get at "[COLOR=Magenta][B]/WebContent/jquery-ui-1.8.14.custom.css". 

[/B][COLOR=Black]IMHO the "/WebContent" bit is very  suspicious,  a CSS file wouldn't be served that way IRL.[COLOR=Magenta] [/COLOR][/COLOR]
[/COLOR]

---

### Post by kunal00731 on 2011-09-14
@[ofnuts]("http://ubuntuforums.org/member.php?u=1382218") :

Should i give the url as :

[https://localhost:8080/WebContent/jquery-ui-1.8.14.custom.css](https://localhost:8080/WebContent/jquery-ui-1.8.14.custom.css)

---

### Post by kunal00731 on 2011-09-20
Hi , i solved the issue , so if some one wonders what the solution is , one thing  that you need to know is where you have kept your js and css  files  either in local or remote , then refer it suing path such as :
<link href="http://localhost:8080/springapp/css/jquery-ui-1.8.14.custom.css" rel="stylesheet"/>
<script type="text/javascript" src="http://localhost:8080/springapp/js/jquery-1.5.1.min.js"></script>

Thanks.

---

