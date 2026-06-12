---
title: "CSS and Firefox help needed, please."
date: 2011-01-15
forum: Programming Talk
---

### Post by rcayea on 2011-01-15
I have another css question. This relates to firefox.

In Google-Chrome my webpage looks how I want it. In firefox, the three column wrapper takes over the whole site. 

The picture on the left is the one I want my site to look like. The other is firefox.

Does anyone know a firefox hack I could use?

I have attached to pictures showing the difference.

thanks in advance,



Randy

---

### Post by akand074 on 2011-01-15
I don't know the answer, but the picture to the left is what your website looks like to me in Firefox (white background not purple).

---

### Post by rcayea on 2011-01-15
Thanks for looking, but I removed the background for now just so it wouldn't look silly. I still have the same problem - haven't figured it out.

---

### Post by worksofcraft on 2011-01-15
> **rcayea said:**
> Thanks for looking, but I removed the background for now just so it wouldn't look silly. I still have the same problem - haven't figured it out.

Well... without access to your CSS and HTML nobody else can either :popcorn:

---

### Post by Shippou on 2011-01-15
> **worksofcraft said:**
> Well... without access to your CSS and HTML nobody else can either :popcorn:

Agreed.

Additional tip: try to check if this problem only occurs when using FF. Or maybe somewhere in the code you are overriding some essential CSS code.

---

### Post by rcayea on 2011-01-15
Thanks for considering my post. Here is the code:
```
[COLOR=#000000][FONT=Times New Roman][FONT=verdana][SIZE=2][COLOR=#000000]Certainly. Thanks for trying to help. I had taken out the problem background color for now because I wanted my site to look decent, so I am going to re-add it back in, into this code so you will have a better opportunity to help me. Thanks! 

Here is the xhtml: 
[/COLOR][/SIZE][/FONT]<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<meta http-equiv="content-type" content="text/html; charset=utf-8"/>
<meta name="description" content=" Tux and Pucks will offer linux tips and HOWTOs, hockey news, poetry"/>
<meta name="keywords" content="hockey, linux, grudgelist, tux, boston bruins, montreal canadians, nhl, linux, ubuntu, HOWTO, ubuntu linux, "/>
<title>Tux and Pucks: Linux and Hockey. All In One!</title>
<link rel="StyleSheet" type="text/css" href="index.css">
</head>

<body> 
<div id="threecolwrapper">
<div id="twocolwrapper"> 
<div id="header">
<i>A linux loving hockey fan welcomes you to...</i> 
<h1>Tux and Pucks | Linux and Hockey. All In One! |</h1>
</div><!--header-->
<!-- End Header Stuff-->


<div id="navleft">[FONT=verdana][SIZE=2][COLOR=#000000] 

I think that should be enough html and here is the css: 
[/COLOR][/SIZE][/FONT]body
{
margin:0; padding:0;

}
#threecolwrapper
{
float:left;
width:100%;
background-color:#772953;
}
#twocolwrapper
{
float:right;
margin-left:20%;
margin-right:20%;
background-color:#white;
font-family: ‘Ubuntubeta’, ‘Ubuntu’, 
‘Bitstream Vera Sans’, ‘DejaVu Sans’, 
Tahoma, sans-serif
}
/*header stuff*/
#header
{
width:100%;
background-image:url("/images/banners/gradient.jpg");
background-repeat:repeat;
padding-bottom:8px;
padding-top:14px;
}
i
{
text-align:left;
padding-left:2%;
}
h1
{
text-align:center;
font-size:1.5em;
}
h2
{
text-align:center;
font-size:1.2em;
margin-top:0px;
}
h4
{
font-size:137.5%;
border-top: solid 2px purple;
border-bottom: solid 2px orange;
text-align:center;
}

/*end of header stuff*/

/*start of navleft stuff*/
#navleft
{
float:left;
margin-top:24px;
background-color:#F5F5DC;
height:1100px;[/FONT][/COLOR]
```

---

### Post by Shippou on 2011-01-15
> **rcayea said:**
> Thanks for considering my post. Here is the code:
```
[COLOR=#000000][FONT=Times New Roman][FONT=verdana][SIZE=2][COLOR=#000000]Certainly. Thanks for trying to help. I had taken out the problem background color for now because I wanted my site to look decent, so I am going to re-add it back in, into this code so you will have a better opportunity to help me. Thanks! 

Here is the xhtml: 
[/COLOR][/SIZE][/FONT]<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<meta http-equiv="content-type" content="text/html; charset=utf-8"/>
<meta name="description" content=" Tux and Pucks will offer linux tips and HOWTOs, hockey news, poetry"/>
<meta name="keywords" content="hockey, linux, grudgelist, tux, boston bruins, montreal canadians, nhl, linux, ubuntu, HOWTO, ubuntu linux, "/>
<title>Tux and Pucks: Linux and Hockey. All In One!</title>
<link rel="StyleSheet" type="text/css" href="index.css">
</head>

<body> 
<div id="threecolwrapper">
<div id="twocolwrapper"> 
<div id="header">
<i>A linux loving hockey fan welcomes you to...</i> 
<h1>Tux and Pucks | Linux and Hockey. All In One! |</h1>
</div><!--header-->
<!-- End Header Stuff-->


<div id="navleft">[FONT=verdana][SIZE=2][COLOR=#000000] 

I think that should be enough html and here is the css: 
[/COLOR][/SIZE][/FONT]body
{
margin:0; padding:0;

}
#threecolwrapper
{
float:left;
width:100%;
background-color:#772953;
}
#twocolwrapper
{
float:right;
margin-left:20%;
margin-right:20%;
background-color:#white;
font-family: ‘Ubuntubeta’, ‘Ubuntu’, 
‘Bitstream Vera Sans’, ‘DejaVu Sans’, 
Tahoma, sans-serif
}
/*header stuff*/
#header
{
width:100%;
background-image:url("/images/banners/gradient.jpg");
background-repeat:repeat;
padding-bottom:8px;
padding-top:14px;
}
i
{
text-align:left;
padding-left:2%;
}
h1
{
text-align:center;
font-size:1.5em;
}
h2
{
text-align:center;
font-size:1.2em;
margin-top:0px;
}
h4
{
font-size:137.5%;
border-top: solid 2px purple;
border-bottom: solid 2px orange;
text-align:center;
}

/*end of header stuff*/

/*start of navleft stuff*/
#navleft
{
float:left;
margin-top:24px;
background-color:#F5F5DC;
height:1100px;[/FONT][/COLOR]
```

For starters, you have a syntax error at the end of the CSS code.

Also, please try replacing your background url with an absolute one. I think this might be the error. (BTW, I am running the code under Firefox 4 beta 8, and I encountered your problem.)

Debugging further...

---

### Post by Shippou on 2011-01-15
Another tip: I think you are trying to use gradients. If so, you can do this in CSS3. Just make sure to degrade gracefully for non-CSS3 browsers (Firefox less than v 3.6 comes to mind).

For more information, please visit:
[http://www.webdesignerwall.com/tutorials/cross-browser-css-gradient/](http://www.webdesignerwall.com/tutorials/cross-browser-css-gradient/)

---

### Post by Shippou on 2011-01-15
Problem solved!

This is the erroneous part (line 17 in medit):
```

background-color:white;

```

Your code version looks like this:
```

#twocolwrapper
{
float:right;
margin-left:20%;
margin-right:20%;
**background-color:#white;**
font-family: ‘Ubuntubeta’, ‘Ubuntu’, 
‘Bitstream Vera Sans’, ‘DejaVu Sans’, 
Tahoma, sans-serif
}

```

Please do not use hashes for color names. Or use #FFFFFF instead.

---

### Post by rcayea on 2011-01-15
thank you, oh, so very much! I will give this a go right now. I can't believe I missed that this whole time.

---

### Post by rcayea on 2011-01-15
Yes, problem solved! 

thanks again.
Randy

---

