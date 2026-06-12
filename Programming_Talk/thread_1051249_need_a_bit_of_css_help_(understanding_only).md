---
title: "need a bit of css help (understanding only)"
date: 2009-01-26
forum: Programming Talk
---

### Post by sujoy on 2009-01-26
i am a css beginner, was going through this page [here]("http://www.htmlgoodies.com/beyond/css/article.php/3642151")

[HTML]<div id="wrapper">
	<div id="header">Header</div>
	<div id="content">
		<div id="content-left"></div>
		<div id="content-main"></div>
		<div id="content-right"></div>
	</div>
	<div id="footer"></div>
	<div id="bottom"></div>
</div>[/HTML]

what does 

[HTML]
#content div {
		padding:10px;
		border:1px solid #bbb;
		float:left;
}[/HTML]

do?

i can understand css applied to the id tags, but this one confused me. what does the "#content div" mean ? moreover they already have a #content declared as 

[HTML]#content {
		margin-top:10px;
		padding-bottom:10px;
}[/HTML]


any help is appreciated, even links to some good css books or tutorials. i am following the w3schools one at the moment

---

### Post by tturrisi on 2009-01-26
#content div - specified styles apply ONLY to divs within these tags:

<-- content --><div id="content"> stuff </div><-- end content div -->

and will not affect other divs on the page.

#content div { /* applies to all divs nested in the content div */
		padding:10px;
		border:1px solid #bbb;
		float:left;
}

That css & html for a tableless layout is rather goofy.  Here's a much easier to understand method:
[http://www.w3schools.com/css/tryit.asp?filename=trycss_float6](http://www.w3schools.com/css/tryit.asp?filename=trycss_float6)

---

### Post by sujoy on 2009-01-26
> **tturrisi said:**
> ...

That css & html for a tableless layout is rather goofy.  Here's a much easier to understand method:
[http://www.w3schools.com/css/tryit.asp?filename=trycss_float6](http://www.w3schools.com/css/tryit.asp?filename=trycss_float6)

thank you. :) that link makes it easy to grasp it.

---

### Post by qbox on 2009-01-26
# symbol means no succession. All elements in that div tag will have its own characteristics. You can use point . to make  succession. # symbol comes with class="" and point . comes with id=""
Cheers
;)

---

### Post by tturrisi on 2009-01-26
see if you can follow this simple 3 column layout of mine. Copy & save as an html file.
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
<title>Template: </title>
<style type="text/css">

/* font
*******************************/
html,body,div,table,th,tr,td,h1,h2,h3,h4,h5,h6,p,form,input,textarea,select,option,ul,li {
font-family:Arial,sans-serif;
}

/* images
*******************************/
img.alignleft {
float:left;
display:inline;
border:0;
margin:0 8 8 0;
background:transparent;
}

img.alignright {
float:right;
display:inline;
border:0;
margin:0 0 8 8;
background:transparent;
}
img.aligncenter {
margin-left:auto;
margin-right:auto;
text-align:center;
padding:0 0 0 0;
display:block;
}
img {
border:0px;
}

/* body
*******************************/
body {
text-align:center;
margin:0px 0px 0px 0px;
padding:0px;
background:#c0c0c0;
}

/* header
*******************************/
#header {
width:100%;
height:150px;
margin:0px 0px 0px 0px;
padding:0px 0px 0px 0px;
background-color:pink;
}
#header p {
width:auto;
margin:0px auto 0px auto;
padding:0px 0px 0px 0px;
color:black;
background:transparent;
}

/* container 
*******************************/
#container {
width:770px;
margin:0px auto 0px auto;
padding:0px 0px 0px 0px;
background:#f1f1f1;
}

/* left
*******************************/
#left {
float:left;
width:180px;
margin:0px 0px 0px 0px;
padding:0px 0px 0px 0px;
text-align:left;
background:transparent;
}
#left  p {
width:auto;
margin:0px 0px 10px 0px;
padding:0px 0px 0px 4px;
color:#000000;
background:transparent;
}

/* right
*******************************/
#right {
float:right;
width:180px;
margin:0px 0px 0px 0px;
padding:0px 0px 0px 0px;
text-align:left;
background:transparent;
}
#right p {
width:auto;
margin:0px 0px 10px 0px;
padding:4px 8px 0px 8px;
color:#000000;
background:transparent;
}

/* middle
*******************************/
#middle {
width:auto;
margin:0px 180px 0px 180px;
padding:0px 0px 10px 0px;
text-align:left;
background:#ffffff;
}
#middle h1 {
width:auto;
margin:0px 0px 0px 0px;
padding:20px 0px 10px 10px;
color:#000000;
background:transparent;
}
#middle  p {
width:auto;
margin:0px 0px 10px 0px;
padding:0px 10px 0px 10px;
color:#000000;
background:transparent;
}

/* footer
*******************************/
#footer {
margin:0px;
padding:10px 0px 10px 0px;
width:auto;
background:pink;
}
#footer p {
text-align:center;
font-size:10px;
color:#ffffff;
margin:0px 0px 0px 0px;
background:transparent;
}

</style>
</head>
<body>

<!-- begin header -->
<div id="header">
<p><img src="" width="770" height="150" alt="this empty image is 770 pixels width and 150 pixels height" /></p>
</div><!-- end header -->

<!-- begin container -->
<div id="container">

<!-- begin left column -->
<div id="left">
<p>Menu here.</p>
</div><!-- end left column -->

<!-- begin right column -- right div must follow left div & precede middle div on all pages -->
<div id="right">
<p>Sed ut perspiciatis, unde omnis iste natus error sit voluptatem accusantium doloremque</p>
</div><!-- end right div -->

<!-- begin middle column -->
<div id="middle">
<h1>Heading 1</h1>
<p><img class="alignleft" src="" width="150" height="150" alt="this empty image is 150 pixels width and 150 pixels height" />Sed ut perspiciatis, unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam eaque ipsa, quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt, explicabo.</p>
<p>Nemo enim ipsam voluptatem, quia voluptas sit, aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos, qui ratione voluptatem sequi nesciunt, neque porro quisquam est, qui dolorem ipsum, quia dolor sit, amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt, ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur?</p>
<p><img class="alignright" src="" width="150" height="150" alt="this empty image is 150 pixels width and 150 pixels height" />Quis autem vel eum iure reprehenderit, qui in ea voluptate velit esse, quam nihil molestiae consequatur, vel illum, qui dolorem eum fugiat, quo voluptas nulla pariatur?</p>
<p>At vero eos et accusamus et iusto odio dignissimos ducimus, qui blanditiis praesentium voluptatum deleniti atque corrupti, quos dolores et quas molestias excepturi sint, obcaecati cupiditate non provident, similique sunt in culpa, qui officia deserunt mollitia animi, id est laborum et dolorum fuga. Et harum quidem rerum facilis est et expedita distinctio.</p>
<p>Nam libero tempore, cum soluta nobis est eligendi optio, cumque nihil impedit, quo minus id, quod maxime placeat, facere possimus, omnis voluptas assumenda est, omnis dolor repellendus.</p>
<p>Temporibus autem quibusdam et aut officiis debitis aut rerum necessitatibus saepe eveniet, ut et voluptates repudiandae sint et molestiae non recusandae. Itaque earum rerum hic tenetur a sapiente delectus, ut aut reiciendis voluptatibus maiores alias consequatur aut perferendis doloribus asperiores repellat.</p>
<p><img class="aligncenter" src="" width="380" height="200" alt="this empty image is 380 pixels width and 200 pixels height" /></p>
</div><!-- end middle column -->

<!-- begin footer -->
<div id="footer"><p>&copy 2009 &nbsp;&nbsp;All Rights Reserved</p></div><!-- end footer -->

</div><!-- end container -->

</body>
</html>
```

---

### Post by sujoy on 2009-01-26
@tturrisi

thank you and yes i guess i am understanding it now. 

#abc - applies to all id="abc" tags
#abc p - applies to all <p> under id="abc" tags

i will try some more css tomorrow, practice always helps.

---

### Post by mssever on 2009-01-28
> **tturrisi said:**
> ```
html,body,div,table,th,tr,td,h1,h2,h3,h4,h5,h6,p,form,input,textarea,select,option,ul,li {
font-family:Arial,sans-serif;
}
```
Why not just do ```
body {
  font-family: Arial,sans-serif;
}
```Since all elements are descendents of <body> (at least in any sensible page), there's no point specifying all the child elements. Attach global styles to <body> and then make exceptions where appropriate. Fuller specification, for example:
```
body {
  font-family: verdana,tahoma,sans-serif;
  font-size: 11pt;
  /*
     For accessibility's sake, it's best to specify a global
     color scheme, then override it as necessary.
  */
  color: black;
  background: white;
}

th {
  background: black;
  color: white;
  font-family: times,serif;
}
```

---

### Post by sujoy on 2009-01-28
now why didnt i think of it !!
well i am doing ok with CSS for now :) thanks for all the help guys.

one thing though, all these new web2 or whatever pages, has these nice colors, almost like textures. isnt using background pics a bit wastefull (as in bandwidth)? but just using colors makes my pages looks like i made them in the 90's

---

### Post by myrtle1908 on 2009-01-28
Don't get too overawed by all the bells and whistles some designers are using these days.  Most of the time they are simply not necessary and only serve as means to stoke their own ego ... eg. "hey look at my whizz-bang navigation menu, isn't it fantastic!" when all the end user wants is to get the content they need quickly and with limited fuss.

You should ask yourself what you are trying to deliver with your page/site/application.  Is it a simple "about me" site or a full blown Rich Internet Application (RIA) that may benefit from things like gradients on toolbars, menus etc.

There are some excellent UI/style guides out there.  One that springs to mind is the Yale Style Guide [http://webstyleguide.com/](http://webstyleguide.com/).

---

### Post by sujoy on 2009-01-28
as of now i am not really trying to deliver anything. i am learning django and then realised that i dont even know enough css to make up a webpage, and having learnt a bit, these new flashy sites got me interested. :) i guess i will stick to normal colors for now and get back to aesthetics once i have something to offer.

that style guide has some good content though. thanks for the link :)

---

### Post by myrtle1908 on 2009-01-28
> **sujoy said:**
> that style guide has some good content though. thanks for the link :)

No problem.  Whilst it is a little old, the fundamentals remain true.  Remember, less is (almost always) more and consistency throughout layout and navigation is paramount.

---

### Post by tturrisi on 2009-01-28
> **mssever said:**
> Why not just do ```
body {
  font-family: Arial,sans-serif;
}
```Since all elements are descendents of <body> (at least in any sensible page), there's no point specifying all the child elements. Attach global styles to <body> and then make exceptions where appropriate. Fuller specification, for example:
```
body {
  font-family: verdana,tahoma,sans-serif;
  font-size: 11pt;
  /*
     For accessibility's sake, it's best to specify a global
     color scheme, then override it as necessary.
  */
  color: black;
  background: white;
}

th {
  background: black;
  color: white;
  font-family: times,serif;
}
```
Because not all elements will inherit the font family & font styles from the <body> parent.  For example, tables & their children, and forms and their children won't inherit from the body.  The body font size is really only useful as a means of controlling layout dimension of a sort, it's another way to affect line-height.

I just declare 'em all up front & then I'm done w/ it.

---

### Post by mssever on 2009-01-28
> **tturrisi said:**
> Because not all elements will inherit the font family & font styles from the <body> parent.  For example, tables & their children, and forms and their children won't inherit from the body.  The body font size is really only useful as a means of controlling layout dimension of a sort, it's another way to affect line-height.

I just declare 'em all up front & then I'm done w/ it.
It's been a while since I've cared about what IE does, but in Firefox, tables *do* inherit from <body>. I just tested it in Firebug. I haven't tested forms, though I don't recall ever having a problem with forms. Any implementation in which tables, forms, etc. don't inherit from <body> is brain dead. Of course, a lot of browser support for CSS is brain dead, so that doesn't prove anything.

---

### Post by tturrisi on 2009-01-29
> **mssever said:**
> It's been a while since I've cared about what IE does, but in Firefox, tables *do* inherit from <body>. I just tested it in Firebug. I haven't tested forms, though I don't recall ever having a problem with forms. Any implementation in which tables, forms, etc. don't inherit from <body> is brain dead. Of course, a lot of browser support for CSS is brain dead, so that doesn't prove anything.

Yeah, in most cases they will inherit from <body>, but won't when declaring specific styles for specific elements in some browsers.  IE forms use the browser default font unless declared in the html or css.  As does FF.  Also, FF fonts always appear slightly smaller than the same font in IE.  

Thus, declaring the font family and size all at once as I did allows me to better control container widths in my layouts.  Let's say you've got a left div for a menu that's 180px wide, and in there is a <p> or an <ul> menu.  The 180px may work in FF but in IE the menu overflows beyond the right edge of the menu div, actually it will push the adjacent right div(s) to the right & maybe even cause a horizontal scrollbar on the page.

---

