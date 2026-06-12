---
title: "Making Cool Mysql Error Page Using PHP"
date: 2010-05-30
forum: Programming Talk
---

### Post by astkboy2008 on 2010-05-30
**Benefits**


[LIST]
[*]it give you **cool** _html/css_  page if the connection to mysql is lost becuase of for example the   user or password is incorrect.
[*]It prevents search engines from archiving the current page and  this is great becuase its an error page and this by this code: [PHP]<meta name="robots" content="noindex,nofollow">[/PHP]
[*]it tells search engine crawlers how long to wait before trying  again, which is the main advantage of using this method. The text on the  page can be formatted any way you want, to inform human visitors what  the problem is.
[/LIST]
**demo**

 [IMG]http://img14.imageshack.us/img14/5595/19542798.gif[/IMG]

the code
[PHP]<?php header('Retry-After: 172800'); ?>
<html>
<head>
<meta http-equiv="Content-Language" content="en-us">
<meta http-equiv="Content-Type" content="text/html; charset=windows-1252">
<meta name="robots" content="noindex,nofollow">
<title>Temporarily Closed</title>
<style type="text/css">
<!--
body {
    background: url(background.gif) repeat;
    margin: 5px 5px;
    text-align: center;
}

div.transbox
{
  text-align: left;
  margin: 20% auto 0px auto;    
  width: 420px;
  height: 180px; 
  background-color: #ffffff;
  border: 1px solid black; 
  filter:alpha(opacity=60);
  opacity:0.6; 
  -moz-border-radius-bottomleft: 7px;
  -moz-border-radius-bottomright: 7px;  
}
div.transbox p
{
  margin-left: 30px;
  font-family: "Verdana", sans-serif;
  font-weight: bold;
  color: #000000;
}
div.transbox h1
{
  margin-left: 30px;
}
 
-->
</style>
</head>
<body>

<div class="transbox">
<p><h1>Mysql Error</h1></p>
<p>I can't join to the Specific mysql database.</p>
<p>The mysql is down maybe by server load!</p>
</div>

</body>
</html> 
[/PHP]
download:
[cool-mysql-error-page.zip  [33.29 KB]]("http://www.jooria.com/downloads/474/cool-mysql-error-page.zip")[]("http://www.jooria.com/Tutorials/tricks-18/making-cool-mysql-error-page-using-php-66/index.html#")
[LIST]
[*][noconnection.html  *[1.31 KB]*]("http://www.jooria.com/view/file/474/noconnection.html")
[*][config.php *[336  B]*]("http://www.jooria.com/view/file/474/config.php")
[*][background.gif  *[32.27 KB]*]("http://www.jooria.com/view/file/474/background.gif")
[/LIST]
[the Tutorial link]("http://www.jooria.com/Tutorials/tricks-18/making-cool-mysql-error-page-using-php-66/index.html")

---

