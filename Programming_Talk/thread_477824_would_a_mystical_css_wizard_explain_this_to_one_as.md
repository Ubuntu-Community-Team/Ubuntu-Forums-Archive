---
title: "would a mystical css wizard explain this to one as lowly as i?"
date: 2007-06-18
forum: Programming Talk
---

### Post by locke.dragon on 2007-06-18
[http://csstestingarea.blogspot.com/](http://csstestingarea.blogspot.com/)

why is there a white block underneath the logo before the nav bar?

```

<?xml version="1.0" encoding="UTF-8" ?>
<!--<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">--><html xmlns='http://www.w3.org/1999/xhtml' xmlns:b='http://www.google.com/2005/gml/b' xmlns:data='http://www.google.com/2005/gml/data' xmlns:expr='http://www.google.com/2005/gml/expr'>
  <head>

<link href='http://i159.photobucket.com/albums/t147/clipsandeggs/paperclipszh6-1.png' rel='icon' type='image/x-icon'/>

<link href='http://i159.photobucket.com/albums/t147/clipsandeggs/paperclipszh6-1.png' rel='icon' type='image/png'/>

    <b:include data='blog' name='all-head-content'/>
    <title><data:blog.pageTitle/></title>
    <b:skin><![CDATA[/*
-------------------------------------------------------------------------------------------------------------
                                  ___           ___           ___           ___           ___     
     _____                       /  /\         /  /\         /  /\         /  /\         /  /\    
    /  /::\                     /  /::\       /  /:/_       /  /:/_       /  /:/_       /  /::\   
   /  /:/\:\    ___     ___    /  /:/\:\     /  /:/ /\     /  /:/ /\     /  /:/ /\     /  /:/\:\  
  /  /:/ /::\  /__/\   /  /\  /  /:/  \:\   /  /:/_/::\   /  /:/_/::\   /  /:/ /:/_   /  /:/ /:/  
 /__/:/ /:/\:| \  \:\ /  /:/ /__/:/ \__\:\ /__/:/__\/\:\ /__/:/__\/\:\ /__/:/ /:/ /\ /__/:/ /:/___
 \  \:\/:/ /:/  \  \:\  /:/  \  \:\ /  /:/ \  \:\ /  /:/ \  \:\ /  /:/ \  \:\/:/ /:/ \  \:\/:::::/
  \  \::/ /:/    \  \:\/:/    \  \:\  /:/   \  \:\  /:/   \  \:\  /:/   \  \::/ /:/   \  \::/~~~~ 
   \  \:\/:/      \  \::/      \  \:\/:/     \  \:\/:/     \  \:\/:/     \  \:\/:/     \  \:\     
    \  \::/        \__\/        \  \::/       \  \::/       \  \::/       \  \::/       \  \:\    
     \__\/                       \__\/         \__\/         \__\/         \__\/         \__\/    

                  ___           ___           ___                       ___                       ___     
      ___        /  /\         /__/\         /  /\                     /  /\          ___        /  /\    
     /  /\      /  /:/_       |  |::\       /  /::\                   /  /::\        /  /\      /  /:/_   
    /  /:/     /  /:/ /\      |  |:|:\     /  /:/\:\  ___     ___    /  /:/\:\      /  /:/     /  /:/ /\  
   /  /:/     /  /:/ /:/_   __|__|:|\:\   /  /:/ /:/ /__/\   /  /\  /  /:/ /::\    /  /:/     /  /:/ /:/_ 
  /  /::\    /__/:/ /:/ /\ /__/::::| \:\ /__/:/ /:/  \  \:\ /  /:/ /__/:/ /:/\:\  /  /::\    /__/:/ /:/ /\
 /__/:/\:\   \  \:\/:/ /:/ \  \:\~~\__\/ \  \:\/:/    \  \:\  /:/  \  \:\/:/__\/ /__/:/\:\   \  \:\/:/ /:/
 \__\/  \:\   \  \::/ /:/   \  \:\        \  \::/      \  \:\/:/    \  \::/      \__\/  \:\   \  \::/ /:/ 
      \  \:\   \  \:\/:/     \  \:\        \  \:\       \  \::/      \  \:\           \  \:\   \  \:\/:/  
       \__\/    \  \::/       \  \:\        \  \:\       \__\/        \  \:\           \__\/    \  \::/   
                 \__\/         \__\/         \__\/                     \__\/                     \__\/    

  _________     ____________________________________________________
 /  ___ ___\   /                                                    \ 
| / __/ __| | | This work is licensed under a Creative Commons       |
|| (_| (__  | | Attribution-Noncommercial 3.0 United States License. | 
| \___\___| | | http://creativecommons.org/licenses/by-nc/3.0/us/    |
 \_________/   \____________________________________________________/

Name:        paperclips plus andreas
URL:         http://paperclipsandscrambledeggs.blogspot.com/
Updated by:  Locke Dragon: paperclipsandscrambledeggs@gmail.com
     
------------------------------------------------------------------------------------------------------------- */

#navbar-iframe {
   display: none;
}

  *{margin:0; padding:0;}

body { background: rgb(232, 234, 236) none repeat scroll 0%;
    font-family: Verdana,Tahoma,Arial,sans-serif;
    font-style: normal;
    font-variant: normal;
    font-weight: normal;
    font-size: 76%;
    font-size-adjust: none;
    font-stretch: normal;
    line-height: 1.4em;
    text-align: center;
    color: rgb(48, 48, 48);
    -moz-background-clip: initial;
    -moz-background-origin: initial;
    -moz-background-inline-policy: initial;

background-image: url("http://i159.photobucket.com/albums/t147/clipsandeggs/stripe.png")

    }


a{
color:#BFBFBF;
font-weight:bold;
text-decoration:none;
background-color:inherit;
}

a:hover{color:#2a5a8a; text-decoration:none; background-color:inherit;}
a img{border:none; vertical-align: middle;}

p{padding:0 0 1.6em 0;}
p form{margin-top:0; margin-bottom:20px;}

img.left,img.center,img.right{padding:4px; border:1px solid #505050;}
img.left{float:left; margin:0 12px 5px 0;}
img.center{display:block; margin:0 auto 5px auto;}
img.right{float:right; margin:0 0 5px 12px;}

/**************** Header and navigation styles ****************/

#container{
width:757px;
margin:50px auto; 20px; 20px;
padding:1px 0;
text-align:left;
background:#ffffff;
color:#303030;
border:1px solid #505050;
}
#header1{
height:215px;
margin:0 1px 1px 1px;
background:#ffffff;
color:#ffffff;
}
#header{
height:0px;
padding:0;
margin:0px 1px 1px 1px;
background:#ffffff;
color:#ffffff;
}
#header1 h1{
padding:35px 0 0 20px;
font-size:2.4em;
background-color:inherit;
color:#ffffff;
letter-spacing:-2px;
font-weight:normal;
}
#header1 h2{
margin:10px 0 0 20px;
font-size:1.4em;
background-color:inherit;
color:#ffffff;
letter-spacing:-1px;
font-weight:normal;
}
#navigation{
height:2.4em;
line-height:2.4em;
margin:0 1px;
background:#B8E0C8;
color:#ffffff;
}

#navigation li{
float:left;
list-style-type:none;
border-right:1px solid #ffffff;
white-space:nowrap;
}

#navigation li a{
display:block;
padding:0 10px;
font-size:0.8em;
font-weight:normal;
text-transform:uppercase;
text-decoration:none;
background-color:inherit;
color: #ffffff;
}

* html #navigation a {width:1%;}

#navigation .selected,#navigation a:hover{
background:#9EEFBE;
color:#ffffff;
text-decoration:none;
}

/**************** Content styles ****************/

#content{
	float:left;
	width:500px;
	font-size:0.9em;
	padding:20px 0px 0 30px;
	text-align: justify;
}

#content h2{
display:block;
margin:10px 0 5px 0;
font-size:1.7em;
font-weight:normal;
letter-spacing:-1px;
color:#505050;
background-color:inherit;
}

#content h2 a{font-weight:normal;}
#content h3{margin:0 0 5px 0; font-size:1.4em; letter-spacing:-1px;}
#content a:hover,#subcontent a:hover{text-decoration:underline;}
#content ul,#content ol{margin:0 5px 16px 35px;}
#content dl{margin:0 5px 10px 25px;}
#content dt{font-weight:bold; margin-bottom:5px;}
#content dd{margin:0 0 10px 15px;}

/**************** Sidebar styles ****************/

#subcontent{
float:right;
width:190px;
padding:20px 20px 10px 0;
line-height:1.4em;
}

#subcontent h2{
display:block;
margin:0 0 15px -10px;
font-size:1.7em;
font-weight:normal;
text-align:left;
letter-spacing:-1px;
color:#505050;
background-color:inherit;
}

#subcontent p{margin:0 0 16px 0; font-size:0.9em;}

/**************** Menublock styles ****************/

.menublock{margin:0 0 20px 8px; font-size:0.9em;}
#subcontent li{list-style:none; display:block; padding:2px; margin-bottom:2px;}
#subcontent li a{font-weight:bold; text-decoration:none;}
#subcontent li a:hover{text-decoration:none;}
#subcontent li ul{margin:3px 0 3px 15px; font-size:1em; font-weight:normal;}
#subcontent li ul li{margin-bottom:0;}
#subcontent li ul a{font-weight:normal;}

.widget{margin:0 0 20px 8px; font-size:0.9em;}

/**************** Footer styles ****************/

#footer{
clear:both;
width:755px;
padding:5px 0;
margin:0 1px;
font-size:0.9em;
color:#f0f0f0;
background:#BFBFBF;
}

#footer p{padding:0; margin:0; text-align:center;}
#footer a{color:#f0f0f0; background-color:inherit; font-weight:bold;}
#footer a:hover{color:#ffffff; background-color:inherit; text-decoration: underline;}

/**************** Misc classes and styles ****************/

.splitcontentleft{float:left; width:190px;}
.splitcontentright{
	float:right;
	width:190px;
	text-align: justify;
}
.clear{clear:both;}
.small{font-size:0.9em;}
.hide{display:none;}
.textcenter{text-align:center;}
.textright{text-align:right;}
.important{color:#f02025; background-color:inherit; font-weight:bold;}

.box{
margin:0 0 20px 0;
padding:10px;
border:1px solid #c0c0c0;
background-color:#fafbfc;
color:#505050;
line-height:1.5em;
}
.style2 {font-size: 12px}
blockquote{
	margin:20px 0;
	padding:0 20px 0 50px;
	background:url('http://photos1.blogger.com/blogger/7994/1253/1600/quote.jpg') 10px top no-repeat;
	border:none;
	color: #999999;
}
]]></b:skin>
  </head>

  <body>
  <div id='container'>

    <!-- skip links for text browsers -->
    <span id='skiplinks' style='display:none;'>
      <a href='#main'>skip to main </a> |
      <a href='#sidebar'>skip to sidebar</a>
    </span>

    <div id='header1'>
      <b:section class='header' id='header' maxwidgets='4' showaddelement='yes'>
<b:widget id='HTML1' locked='false' title='' type='HTML'/>
</b:section>
    </div>
 
 <div id='navigation'>
 <ul>
 <li class='selected'><a expr:href='data:blog.homepageUrl'>blog  <img src='http://i159.photobucket.com/albums/t147/clipsandeggs/blog.gif'/></a></li>
 <li><a href='http://www.flickr.com/photos/paperclipsandscrambledeggs/'>flickr  <img src='http://i159.photobucket.com/albums/t147/clipsandeggs/aboutme.gif'/></a></li>
 <li><a href='http://www.thelinuxdock.blogspot.com/'>leaflet  <img src='http://i159.photobucket.com/albums/t147/clipsandeggs/toolbox.gif'/></a></li>
 <li><a href='http://www2.blogger.com/profile/13088056030686503922'>about me  <img src='http://i159.photobucket.com/albums/t147/clipsandeggs/portfolio.gif'/></a></li>
 <li><a href='mailto:paperclipsandscrambledeggs@gmail.com'>email  <img src='http://i159.photobucket.com/albums/t147/clipsandeggs/message.gif'/></a></li>
 </ul>
 </div>


    <div id='content'>

        <b:section class='main' id='main' showaddelement='no'>
<b:widget id='Blog1' locked='true' title='Blog Posts' type='Blog'/>
</b:section>
      </div>

<div class='splitcontentright'><div id='subcontent'>
        <b:section class='sidebar' id='sidebar' preferred='yes'/>
      </div></div>

      <!-- spacer for skins that want sidebar and main to be the same height-->
      <div class='clear'>&#160;</div>

    <div id='footer-wrapper'>
      <b:section class='footer' id='footer'/>
    </div>

  </div><!-- end outer-wrapper -->
</body>
</html>

```

---

### Post by AdamG on 2007-06-18
Start with the following:
on the img src="http://i159.photobucket.com/albums/t147/clipsandeggs/paperclipsbanner.jpg" 
tag, remove the float, position, top and right rules. (They are on the inline style attribute). 

Next you need to not have this rule:
.widget{margin:0 0 20px 8px; }
You can leave the font-size, but get rid of that margin. 

That'll get rid of the whitespace and leaves the rest of it pretty decent (at least in Firefox). 

BTW, if you aren't already you should be using Firebug. It makes CSS debugging ridiculously easy.

---

### Post by Modred on 2007-06-18
The DIV with the "header" class, which is parent to all of your logo stuff, rests directly on top of the nav bar, but the image has been arbitrarily moved upward from its normal position.  This left white space below.

I second the Firebug comment.

---

### Post by locke.dragon on 2007-06-18
first, what is firebug?  a firefox add-on?  and second, i need that extra stuff for the header so that it's positioned correctly.  if i don't have that in, it's too far to the right.

---

### Post by locke.dragon on 2007-06-18
ok.  looked up firebug, downloaded, installed, works like a charm, thanks!  used the above suggestion and it worked!  thanks!  :)

---

