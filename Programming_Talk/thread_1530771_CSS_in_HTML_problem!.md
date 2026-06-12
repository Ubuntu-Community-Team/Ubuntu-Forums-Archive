---
title: "CSS in HTML problem!"
date: 2010-07-14
forum: Programming Talk
---

### Post by DanDude on 2010-07-14
Hi!

This is my code:

[HTML]<style type="text/css">
a {text-decoration:none}

ul#list-nav {
list-style:none;
font-family: Helvetica,Arial,sans-serif;
margin:0px;
padding:0;
width:525px
}

ul#list-nav li {
display:inline
}

ul#list-nav li a {
text-decoration:none;
padding:5px 0;
width:100px;
background:url('Images/Icons/nav/nav-fade1.png');
background-repeat:repeat-x
color:#000000;
float:left;
text-align:center;
border-left:1px solid #fff;
}

ul#list-nav li a:hover {
background:url('Images/Icons/nav/nav-fade2.png');
background-repeat:repeat-x
color:#000000
}

ul#list-nav li a:active {
background:url('Images/Icons/nav/nav-fade3.png');
background-repeat:repeat-x
color:#ffffff;
}

  </style>[/HTML]


Yes, <style> and </style> is in the head tags!
All padding and stuff works, but the font color does not change!

I have another script that defines the color of the links on my "Links" page... this is the colors the font color of the ul lists changes to!

[HTML]<body style="color: black; background-color: white; " backgrounds="" alink="#b6f391" link="#b6f391" vlink="#b6f391">[/HTML]

If I remove the script, the font color changes to the standard ones...

---

### Post by trent.josephsen on 2010-07-14
The attributes on <body> are deprecated; [http://www.w3schools.com/tags/tag_body.asp](http://www.w3schools.com/tags/tag_body.asp).  Don't use them.

What's your HTML?

---

### Post by slackthumbz on 2010-07-14
putting CSS in html files is incredibly bad practice. All CSS should be in a separate file and sourced in the header with a link rel tag.

i.e <link rel='stylesheet' type='text/css' href='/css/site.css' />

---

### Post by xsinsx on 2010-07-14
Id put a large Div around all the other body html 

```


<body>
    <div id="BodyWrapper">
        <!-- All your other html -->
    </div>
</body

```

then in your css have something like 
```

#BodyWrapper{
position: relative;
width: 100%
color: black; 
background-color: white;  
backgrounds=""
 alink="#b6f391" 
link="#b6f391" 
vlink="#b6f391"
}
```

that would be linked in from an external file of course.

---

### Post by DanDude on 2010-07-16
Ok, i have put the css in a separate document, now it looks like this:

```
body {font-family: Helvetica,sans-serif;}

a {color:#b6f391}

a:active {color:#b6f391}

a:hover {color:#b6f391}

a:visited {color:#b6f391}

ul#list-nav {
list-style:none;
font-family: Helvetica,Arial,sans-serif;
margin:0px;
padding:0;
width:525px
}

ul#list-nav li {
display:inline
}

ul#list-nav li a {
text-decoration:none;
padding:5px 0;
width:100px;
background:url('../Images/Icons/nav/nav-fade1.png');
background-repeat:repeat-x
color:#000000;
float:left;
text-align:center;
border-left:1px solid #fff;
}

ul#list-nav li a:hover {
background:url('../Images/Icons/nav/nav-fade2.png');
background-repeat:repeat-x
color:#000000
}

ul#list-nav li a:active {
background:url('../Images/Icons/nav/nav-fade3.png');
background-repeat:repeat-x
color:#ffffff;
}
```I have changed 

[HTML]<body style="color: black; background-color: white; " backgrounds="" alink="#b6f391" link="#b6f391" vlink="#b6f391">[/HTML]Into just <body>

Everything works fine, but the links in my nav bar, are still the colors I have set them to in the beginning of the CSS document! I want them to be the colors i set here:

```
ul#list-nav li a {
text-decoration:none;
padding:5px 0;
width:100px;
background:url('../Images/Icons/nav/nav-fade1.png');
background-repeat:repeat-x
color:#000000;
float:left;
text-align:center;
border-left:1px solid #fff;
}

ul#list-nav li a:hover {
background:url('../Images/Icons/nav/nav-fade2.png');
background-repeat:repeat-x
color:#000000
}

ul#list-nav li a:active {
background:url('../Images/Icons/nav/nav-fade3.png');
background-repeat:repeat-x
color:#ffffff;
```Is there anything wrong with the CSS script?
This is how I connect the ul list with the css:

[HTML]<ul id="list-nav">
<li><a href="index.html">Home</a></li>
<li><a href="Scripts/archive.html">Archive</a></li>
<li><a href="Scripts/links.html">Links</a></li>
<li><a href="mailto:xxxxxxx@xxxxxxxxx.com>Contact</a></li>
</ul>[/HTML]Thank you for fast answers :)

---

### Post by howlingmadhowie on 2010-07-16
you're missing a few ';' at the end of css lines.

---

### Post by DanDude on 2010-07-16
Ah, thanks! Now everything works! I am really new to CSS, so sorry for my incompetence :)

---

