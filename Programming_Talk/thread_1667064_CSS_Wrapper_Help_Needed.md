---
title: "CSS Wrapper Help Needed"
date: 2011-01-14
forum: Programming Talk
---

### Post by rcayea on 2011-01-14
Hey Everyone,

I'll get right to it becaue I have two questions that I think may be related to each other - not sure. My questions are, why does my website "div wrapper" stop where my header stops? And, Why when I try to set the body tag in xhtml to a specific color, say red, the color red totally covers everything?

What I would like to accomplish is in the attachment. In the attachment you see I squared-off where the left margin is a different color(not by much) but still different. Each time I try to do this, my whole page is one color. 


Here is my code:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<meta http-equiv="content-type" content="text/html; charset=utf-8">
<meta name="description" content=" Tux and Pucks will offer linux tips and HOWTOs, hockey news, poetry"/>
<meta name="keywords" content="hockey, linux, grudgelist, tux, boston bruins, montreal canadians, nhl, linux, ubuntu, HOWTO, ubuntu linux, "/>
<title>Tux and Pucks: Linux and Hockey. All In One!</title>
<link rel="StyleSheet" type="text/css" href="index.css">
</head>

<body>   						
	<div id="wrapper">																													
      <i>A linux loving hockey fan welcomes you to...</i>      
     <div id="header">
     <h1>Tux and Pucks |  Linux and Hockey. All In One! |</h1>
      </div><!--header-->
<!-- End Header Stuff-->


<div id="navleft">
```

And the CSS:
```
#wrapper
{
background-image:url("/images/banners/gradient.jpg");
width:73%;
height:100%;
margin-left: auto;
margin-right: auto;
font-family: ‘Ubuntubeta’, ‘Ubuntu’, 
‘Bitstream Vera Sans’, ‘DejaVu Sans’, 
Tahoma, sans-serif
}
/*header stuff*/
#header
{
width:100%;
padding-bottom:20px;
background-repeat: no-repeat;
background-position:left center;
text-align:center;
}
h1
{
text-align:center;
}
h2
{
text-align:center;
font-size:22px;
margin-top:0px;
}
h4
{
font-size:24px;
border-top:solid 3px purple;
border-bottom:solid 3px orange;
text-align:center;
}
#mail
{
position:absolute;
top:10px;
right:350px;
}
#headerTaPlogo
{position:absolute; top:35px;}

/*end of header stuff*/
```

If you need more of my code, please let me know. 
Thanks in advance, this has been very frustrating.

---

