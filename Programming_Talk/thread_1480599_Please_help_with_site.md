---
title: "Please help with site"
date: 2010-05-11
forum: Programming Talk
---

### Post by c2483 on 2010-05-11
Here is the HTML sent to the browser
```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">

<head>
<title>Pressure Washer Sales &amp; Service</title>
<meta http-equiv="content-type" content="text/html;charset=utf-8" />
<link rel="stylesheet" href="styles.css" type="text/css" />
</head>

	 
<body id="about">
  <div id="header"><img src="images/header.gif" alt="" /></div>
	<div id="home">
		<a href="index.php"><img src="images/home.gif" width="102" height="37" alt="" /></a>

	</div>
	<div class="clear"></div>
	<table id="links">
		<tr>
		<td id="products_menu"><a href="products.php">PRODUCTS</a></td>
		<td id="services_menu"><a href="services.php">SERVICES</a></td>
		<td id="about_menu"><a href="about.php">ABOUT US</a></td>

		<td id="specials_menu"><a href="specials.php">SPECIALS</a></td>
		<td id="contact_menu"><a href="contact.php">CONTACT US</a></td>
		</tr>
	</table>
<div id="outerspace">
    <div id="wspace">
        <div id="mspace">
            <div class="mtext">&nbsp;</div>

            <div class="wtext">&nbsp;</div>
        </div>
    </div>    
</div>
  <div id="outer">
      <div id="wlayer">
        <div id="mlayer">
            <div class="mtext"><p class="Construction">Site Is Under Construction. Feel Free To Look Around And Call With Questions. </p>
<div id="sitelinks">

	Links to our manufacturers
  <a href="http://www.karchercommercial.com/" rel="external"><img src="images/karcher.jpg" alt="Karcher Commercial" /></a>
  <a href="http://www.mitm.com" rel="external"><img src="images/mitm.jpg" alt="Mi-T-M Corporation" /></a>
</div></div>
            <div class="wtext">coming soon<br /></div>
        </div>
      </div>
      <div id="footer"><img src="images/footer.gif" alt="" /></div>
  </div>

</body>
</html>

```

this is my css
```
 
html, body 
{
	position:relative; 
	margin:0px; 
	padding:0px; 
	background:#aaa; 
	font-family:verdana; 
	font-size:12px;
	z-index:-10;
}
#outer
{
	position:relative;
	float:left;
	width:100%;
	top:-200px;
	z-index:-1;
}
#wlayer 
{
	position:relative;
	float:left;
	width:100%;
	background:white;
}
#mlayer
{
	position:relative;
	float:left;
	width:100%;
	background:maroon;
	right:84%;
}
#outerspace
{
	position:relative;
	float:left;
	width:100%;
	top:-200px;
	z-index:-1;
}
#wspace
{
	position:relative;
	float:left;
	width:100%;
	height:222px;
	background:white;
}
#mspace
{
	position:relative;
	float:left;
	width:100%;
	height:222px;
	background:maroon;
	right:84%;
}
.mtext 
{  
	position:relative;
	float:left;
	width:14%; 
	left:85%;
	overflow:hidden;
	padding-bottom: 20px;
	color:white;
}
.wtext 
{
	position:relative;
	float:left;
	width:78%;   
	left:88%;
	overflow:hidden;
	padding-bottom: 20px;
}
#header img
{
	position:relative;
	width: 100%;
	top:0;
	left:-2px;
}
#footer img
{
	width: 100%;
}


#map
{
	width: 95%;
	border: 0px solid white;
}

#home
{ 
	position: relative; 
	float:right;
	margin-right:30px;
	margin-top:-24px; 
}
#home a 
{  
	position: relative; 
	float:right;
	background:black;
	width:102px;
	height:37px;
	margin-right:30px;  
	margin-top:-10px;  
}
#home a:hover  
{   
	position: relative; 
	float:right;
	background:maroon;
	width:102px;
	height:37px;
	margin-right:30px;  
	margin-top:-10px;  
}
#index #home a  
{   
	background:maroon; 
}
#index #home img 
{   
	border: 3px solid maroon; 
}
#home a img
{
	width:102px;
	height:37px;
	z-index:15;  
}
#home img
{  
	border: 3px solid black;
}

#sitelinks
{
	position: relative; 
	float:left;
	margin-top:20px;
}
#sitelinks a
{
	position: relative; 
	float:left;
	padding-top:6px;
}
#sitelinks img
{
	position: relative; 
	float:left;
	width:70%;
} 

#links
{ 
	margin-left:17%;
	margin-top:8px;
	border: 1px solid black;
	width: 81%; 
	table-layout: fixed;
	border-collapse: collapse;
	background: blue;
}
#links td
{
	border: 1px solid black;
	padding:6px;
	text-align:center;
}
#links td:hover 
{
	background:maroon;
}
#links a
{ 
	display:block;
	text-decoration: none;
	color:white;
	height:100%;
}
p.Construction 
{
	font-family: serif;
	font-style: oblique;
	font-variant: small-caps;
	font-size: medium;
	text-decoration: none;
	text-transform: capitalize;
	margin-top:0px;
}	
span.underlined 
{
	text-decoration: underline;
}
.indent50px
{
	position:absolute;
	left:50px;
}
.indent100px
{
	position:absolute;
	left:100px;
}
.indent150px
{
	position:absolute;
	left:150px;
}
.indent200px
{
	position:absolute;
	left:200px;
}
.prodhead
{
	font-style:italic; 
}
#about td#about_menu
{ 
	background: maroon; 
}
#contact td#contact_menu
{ 
	background: maroon; 
}
#specials td#specials_menu
{ 
	background: maroon; 
}
#products td#products_menu
{ 
	background: maroon; 
}
#services td#services_menu
{ 
	background: maroon; 
}

```

[Link]("http://pressurewashersalesandservice.com/")


The two image links on the side do not work in ie7

---

