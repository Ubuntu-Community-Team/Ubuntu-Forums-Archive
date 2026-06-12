---
title: "Link Coloring / CSS Problem"
date: 2008-01-02
forum: Programming Talk
---

### Post by dhtseany on 2008-01-02
Hi all, I'm so sick of CSS it's not even funny :-P The problem here is when I click on a link and visit that page, the original link that took me there isn't showing the correct **a:visited** color. I believe I've pinpointed the problem to **#credit** but I'm not sure how to fix it.

Thanks for taking the time in advance :)

Sean

Page in action: [Here]("http://www.myaiw.com/news.php")

PS- Go ahead and make fun of my poorly written CSS (I'm still learning it)

Anyways, check out this code:

```

body{
background-image:url('grey_bg.gif');
background-position:center;
background-attachment:fixed;
background-repeat:repeat-xy;
background-height:100%;
margin:0;
padding:0;
font-family:Arial, Helvetica, sans-serif;
font-size:12px;
color:#000;
text-align:left;}
img{border:1 #FF0000;}

/*--Anything to do with Links--*/
#login a:hover{
font-size:10px;
text-decoration:underline;
color: #FFF;}

#login a:link, a:visited, a:active{
font-size:10px;
text-decoration:none;
color:#FFF;}

#navlink a:link{
font-size: 10px;
text-decoration: none;
color: #FFF;
width: 140px;
height: 18px;
background: url(button_off.gif) no-repeat left;
padding-left: 10px;
margin-top: 2px;
padding-top: 1px;
clear: none;
float: left;}

#navlink a:visited{
font-size: 10px;
text-decoration: none;
color: #FFF;
width: 140px;
height: 18px;
background: url(button_off.gif) no-repeat left;
padding-left: 10px;
margin-top: 2px;
padding-top: 1px;
clear: none;
float: left;}

#navlink a:hover{
font-size: 10px;
background: url(button_on.gif) no-repeat;
text-decoration: none;
color: #FFF;
width: 140px;
height: 18px;}

#navlink a:active{
font-size: 10px;
background: url(button_on.gif) no-repeat;
text-decoration: none;
color: #FFF;
width: 140px;
height: 18px;} 

#credits{
color:#FFFFFF;
text-decoration:none;
font-size:10px;}

#credits a, a:visited, a:active{
color:#FFFFFF;
text-decoration:none;
font-size:10px;}

#credits a:hover{
color:#FFFFFF;
text-decoration:underline;
font-size:10px}

/*--End Links--*/

.box{
height:320px;
width:590px;
overflow:auto;}

.borBlack{
border:3px solid #000000;
color:#000000; 
background:#FFFFFF;
text-align:left;
vertical-align:top}

.bordTop{
border:none;
margin:auto;
margin-bottom:1px;
text-align:left;
vertical-align:top;}

.dropdown{
font: 0.7em Arial, Helvetica, sans-serif;
background: #900;
color: #FFF;}

.rbroundbox_ltgry { background: url(black.gif) repeat; }
.rbtop_ltgry div { background: url(tl.gif) no-repeat top left; }
.rbtop_ltgry { background: url(tr.gif) no-repeat top right; }
.rbbot_ltgry div { background: url(black.gif) no-repeat bottom left; }
.rbbot_ltgry { background: url(black.gif) no-repeat bottom right; }
.rbtop_ltgry div, .rbtop_ltgry, .rbbot_ltgry div, .rbbot_ltgry {
width: 100%;
height: 7px;}
.rbcontent_ltgry { margin: 0 7px; }
.rbroundbox_ltgry { width: 100%; margin: .25px auto; }

```

And the source for the problem child page:
```

<html>
<head>
<title>American Iron Works USA</title>
<link href='http://www.myaiw.com/css/new.css' rel='stylesheet' type='text/css'>
</head>
<body>

<br>
<table width="80%" border="0" align="center">
  <tr>
    <td colspan="2">
	<div align="right">
	<form name="events">

<select name="url" size="1" onChange="window.open(this.options[this.selectedIndex].value,'_top')" class="dropdown">
<option value="#" selected>Navigation...</option>
<option value="http://www.myaiw.com/index.php">Home</option>
<option value="http://www.myaiw.com/news.php">AIW News</option>
<option value="http://www.myaiw.com/contact.php">Contact AIW</option>
<option value="http://cat.myaiw.com/nav_redirect.htm">Parts</option>
<option value="http://www.myaiw.com/upload/index.php">Photos</option>
</select>
</form></div></td>
  </tr>

  <tr>
    <td colspan="2"><div class="rbroundbox_ltgry">
        <div class="rbtop_ltgry">
          <div></div>
        </div>
      <div class="rbcontent_ltgry">
<div align="center">
  <table width="100%" border="0">
    <tr>

      <td width="45%"><img src="http://www.myaiw.com/img/ban2.jpg"></td>
      <td width="55%">
	   <div id='login' align='right'><a href='http://www.myaiw.com/secure/login.php'><img src='http://www.myaiw.com/img/mslock.gif' border='0'>Login</a></div>	  
	  </td>
    </tr>
  </table>
</div>
          </div>
      <div class="rbbot_ltgry">

        <div></div>
      </div>
    </div></td>
  </tr>
  <tr>
    <td width="20%" height="148" class="bordTop">
		<div id="navlink">
		<a href="http://www.myaiw.com">Home</a><br>

		<a href="http://www.myaiw.com/news.php">AIW News</a><br>
        <a href="http://www.myaiw.com/contact.php">Contact AIW</a><br>
		<a href="http://cat.myaiw.com" target="_blank">Parts</a><br>
		<a href="http://www.myaiw.com/upload/index.php">Picture Gallery</a>
		
		</div></td>
	  
	  
	  
    <td width="100%" rowspan="2" class="borBlack"><p><h1>AIW News and Updates</h1></p>Click <a href='archive.php'>here to read archived news.	</td>

	
  </tr>
  <tr  class="bordTop" valign="top">
  
  </tr>
  <tr>
    <td height="14" colspan="2" align="center"><div id="credits">
    Phone: 866-793-6935 Fax: 503-885-8481<br/>
    Copyright © 2007 American Iron Works<br>
All Rights Reserved<br>

Website Designed by <a href="http://www.lakecs.net/" target="_blank">LCS</a></div></td>
  </tr>
</table>
</body>
</html>

```

---

### Post by LaRoza on 2008-01-02
You made the visited colour the same colour as the background.

---

### Post by dhtseany on 2008-01-02
Yeah I figured that out but what could be a problem (in my mind anyways) is that I have 2 different background colors. I only need a black colored link inside of the white box while the rest of the links on the page stay white (or grey).

Get what I mean?

---

### Post by ThinkBuntu on 2008-01-02
I don't have time to go over your code, but this is an easy fix. If your "black box" which needs white links is in <div id="black_box">, then add this code:
```
#black_box a {
color: white;
}
```
Add a:visited, etc. if these links don't color properly.

---

