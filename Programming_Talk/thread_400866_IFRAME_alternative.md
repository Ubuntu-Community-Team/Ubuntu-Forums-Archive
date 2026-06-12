---
title: "IFRAME alternative"
date: 2007-04-04
forum: Programming Talk
---

### Post by Praill on 2007-04-04
I looked all over this site and google and could not find any information regarding an alternative for the annoying <IFRAME> tag. I finally figured it out and would like to post my findings for anyone else  in my position. This board has always been great to me, so I decided to post it here for fellow ubuntu users :)

The solution is.. use tables and php instead of iframe.

The following code creates the appearance of two centered frames. The left frame is the menu with page links in it. And the right frame is the area where the links load.

*code for index.php*
```
<body>
<center>
<table style="width: 700px; height: 100%;" border=0>
<tbody>
<tr>
<td style="width: 200px; height: 100%;">
<a href="index.php?page=home.html">Home</a href><br>
<a href="index.php?page=somepage.html">Some Page</a href>
</td>
<td style="width: 500px; height: 100%;">
<?php
$page;
if( $_GET[page]==NULL ) $page="home.html";
else $page=$_GET[page];
include($page);
?>
</td>
</tr>
</table>
</center>
</body>
```

The key now is making all links load through index.php by passing the page as a variable. So if you wanted to load the page ubuntu.html the link code would be index.php?page=ubuntu.html.

This way of doing things is much better than any kind of frame because:
1) tables auto-resize to fit content (iframes dont without messy javascript that rarely works on all browsers)
2) tables are much more flexible than regular frames.
3) the address bar updates as the the person surfs so they can link a certain portion of your site to others. Any kind of frame uses the "target" argument so the address bar never changes.


This might be an obvious solution, but it really wasnt for me. And like I said, searching for this for 2 days returned no help. 
Hopefully this can help someone.

---

### Post by Mirrorball on 2007-04-04
This is basic PHP, keep learning this language and you are going to discover other amazing things soon. But you should improve your HTML. Here is a good start:
[http://www.456bereastreet.com/lab/developing_with_web_standards/](http://www.456bereastreet.com/lab/developing_with_web_standards/)

---

### Post by Praill on 2007-04-04
Ya, like I said it might have been an obvious solution to someone versed in php. But it wasnt for me. And endless searching never awarded me this solution. I actually figured it out entirely on my own. That's why I posted here, in the hopes that someone in my situation might come along this post sooner.

---

### Post by pmasiar on 2007-04-04
you may want to post it to [ Tutorials & Tips](http://ubuntuforums.org/forumdisplay.php?f=100) forum - here it will be forgotten after it scrolls off first page.

---

### Post by LaRoza on 2007-04-04
You can also use CSS to simulate a framed, including inline frames, site and make roll-over images. The browsers would need to have a little CCS2 support though.

---

### Post by Note360 on 2007-04-04
This is pretty cool, but you neednt use tables. I would suggest learning CSS and XHTML before you move forward with PHP. (1, 2 days tops)

---

### Post by Praill on 2007-05-03
I started developing with CSS positioning and XHTML but abandoned it. It was just a messy and hard to code with as tables and the end result was unpredictable behaviour on all browsers.
Tables are supported on all browsers since the dark ages, in all environments so the solution seems clear to me.

I have NO idea why all these people are developing with CSS positioning instead of tables. The only thing CSS can do that tables cant is absolute positioning.. which sucks because resizing a window breaks the absolute position and you have to implement javascript checks that, again, will vary on different browsers.

---

### Post by LaRoza on 2007-05-03
I have no problems with using CSS to position elements, tables are used to describe tabular data, CSS is used for styling elements. 

Resizing can be a problem if you do not write the CSS properly, but it is easy to fix.

---

### Post by Mirrorball on 2007-05-03
> **Praill said:**
> I have NO idea why all these people are developing with CSS positioning instead of tables.
Then learn [why tables for layout is stupid]("http://www.hotdesign.com/seybold/"). Another article you might want to read:
[http://www.456bereastreet.com/lab/developing_with_web_standards/](http://www.456bereastreet.com/lab/developing_with_web_standards/)

---

### Post by Praill on 2007-05-04
That link offered one statement:
*"...the use of tables is now actually interfering with building a better, more accessible, flexible, and functional Web."*

Which is simply one persons opinion, and even more simply: ridiculous.

CSS's problem is its not standardized browser-wide. Thats it. People using tables is not the problem.


That being said.. honestly.. the best and most guaranteed way to make your website if you were going to create one tomorrow would be a combination of style sheets and tables. *ex. <table style="height: 100px; width: 100px;">*

Using tables with styles is much more efficent (and easier if youre used to it) than using CSS positioning with div tags. I really dont understand why everyone table-hates so much.

---

### Post by LaRoza on 2007-05-04
I don't hate tables, I just use the best tool for the task at hand. Tables for data and CSS for looks. Of course, I always test the page with CSS disabled to make sure it degrades gracefully.

---

### Post by Blacktalon on 2007-05-04
I feel tables are ok for some things, but other stuff I would definately not use them.

And depending on how you want your Iframe or how comforable you feel with you approach, personally I use CSS for my IFrame alternative (to keep it hidden)  And it has came out pretty good.

Not to bash using Tables, I just would suggest using CSS way of IFrames.

---

### Post by Mirrorball on 2007-05-04
> **Praill said:**
> That link offered one statement:
*"...the use of tables is now actually interfering with building a better, more accessible, flexible, and functional Web."*

Which is simply one persons opinion, and even more simply: ridiculous.
Did you read the whole presentation or did you stop after that statement? It's not simply his opinion. He gave a lot of arguments, which you didn't.
> **Praill said:**
> CSS's problem is its not standardized browser-wide. Thats it.
The standards exist:
[http://www.w3.org/TR/CSS21/](http://www.w3.org/TR/CSS21/)
But I know very well that Internet Explorer's CSS implementation is buggy and this is the only reason why table-based layouts are simpler to make. But they are harder to maintain, harder to change, the files are bigger, accessibility suffers. And there are lots of tutorials about how to make CSS layouts that work on Internet Explorer.
> **Praill said:**
> People using tables is not the problem.
Inaccessible sites that use more bandwidth and are harder for search engines to parse and store are definitely a problem.
> **Praill said:**
> Using tables with styles is much more efficent (and easier if youre used to it) than using CSS positioning with div tags. I really dont understand why everyone table-hates so much.
It mixes structure and presentation. If you decide to change the layout, you'll have to change all the pages themselves. With CSS, you edit one file, the style sheet, and all the pages linked to that style sheet change. This could have never been done with tables:
[http://www.csszengarden.com/](http://www.csszengarden.com/)

In table-based layouts, the blocks of content might get all mixed up, not in a logical order. It's a problem for blind users, because when the text is read directly from the code, instead of seeing it displayed on a browser window, it doesn't make sense. The heading might come after the content, form fields and their labels are separated, it's a mess.

Table-based layouts use more markup. Add a few more bytes to a 1000-page site and you will be using a lot more bandwidth. If those thousand pages were linked to one style sheet, it would have been much more economical.

But it's true that Internet Explorer's CSS bugs will shorten any web developer's life. :(

---

### Post by Blacktalon on 2007-05-04
> But it's true that Internet Explorer's CSS bugs will shorten any web developer's life.

Actually this is more of a IE bug over a CSS one, and it can be gotten around, with some code in CSS.  I have seen it done before, and I have done it before.

---

### Post by Praill on 2007-05-07
> **Mirrorball said:**
> 
The standards exist:
[http://www.w3.org/TR/CSS21/](http://www.w3.org/TR/CSS21/)

I'm not overly concerned with "standards" that are, by no means, standard. IE accounts for 80% of the browsers used world-wide.

> **Mirrorball said:**
> Inaccessible sites that use more bandwidth and are harder for search engines to parse and store are definitely a problem.
I did not see this information on that page linked. If it is actually true then it is a very valid point and I concede to you on that aspect of the discussion.

> **Mirrorball said:**
> 
It mixes structure and presentation. If you decide to change the layout, you'll have to change all the pages themselves. With CSS, you edit one file, the style sheet, and all the pages linked to that style sheet change. 

If you use tables with a php include so that all links are passed through index.php with a varible then all pages will use index.php's layout. If you have another layout you would like to use for a different set of pages you make another php file (layout2.php) and use an include function to load unique content into that new layout. It's really the same thing.
> **Mirrorball said:**
> 
In table-based layouts, the blocks of content might get all mixed up, not in a logical order. It's a problem for blind users, because when the text is read directly from the code, instead of seeing it displayed on a browser window, it doesn't make sense. The heading might come after the content, form fields and their labels are separated, it's a mess.

I'm not really sure I follow you here. Could you maybe explain this a little more? Sorry. Id like to know what you are saying though.

> **Mirrorball said:**
> 
Table-based layouts use more markup. Add a few more bytes to a 1000-page site and you will be using a lot more bandwidth. If those thousand pages were linked to one style sheet, it would have been much more economical.

If tables do infact create large page sizes than I suppose this is true. Most websites this large in nature are streaming video, have complicated layouts with several images, etc. I fail to see how they would be worried about saving a few bytes on layout code, but still run all their fancy javascript, shadowed edges, images, etc. However, speaking from a strict economic point of view, if this is true, then I suppose I can agree.
> **Mirrorball said:**
> 
But it's true that Internet Explorer's CSS bugs will shorten any web developer's life. :(
This is the basis for my argument. I tried, originally, to use CSS positioning. Using linux primarily (of course) makes it hard for me test my page in IE (ie6 is all im able to work with using wine.. and even that is unreliable). Essentially it was just a nightmare. Why spend hours learning about and fiddling with unfamiliar layouts when I know tables WILL work? It may save me a few KB of bandwidth a month (and i say MAY because I'm still not convinced of this point) but the fractions of a penny a month are by far worth keeping my blood pressure down :)

---

### Post by Praill on 2007-05-07
> **LaRoza said:**
> ..I just use the best tool for the task at hand. Tables for data and CSS for looks...

I forgot to address this point. I think you mean that you use, what may and may not be considered by varying devlopers as, the PROPER tool for the task at hand. CSS is certainly not standardized and therefore harder to work with. This might not always make it the best tool when considering time invested and user compatibility.

---

### Post by frup on 2007-05-07
[PHP]
<?
$page = $_GET["page"];
$file = $page.".php"; // you can change that to html or txt if you really want to
if (isset($page)) { // check if a var for page is set
 if (!file_exists($page.'.php')) { // check if $page .php exists
      $file = '404.php'; // if page doesnt exist 404 error (instead of PHP error)
    }
  else {
      $file = $page.".php"; // *.php?page=*
	}
}
else {
 // default if page is not set (eg with out going *.php?page=*)
    $file = 'news.php';
      }
?>
      include ($file);  // include the file (add it to your page)
[/PHP]

Takes what you've figured out a little further... :)

---

### Post by Mirrorball on 2007-05-07
> **Praill said:**
> I'm not overly concerned with "standards" that are, by no means, standard. IE accounts for 80% of the browsers used world-wide.
But you should be concerned, because the adoption of web standards will only make our jobs easier and Internet users happier. If more people create sites according to web standards, it will create more pressure on Microsoft to improve Internet Explorer.
> **Praill said:**
> I did not see this information on that page linked.
It was a presentation. You must have missed the "Next" link to the next slides. Here it is again: [http://www.hotdesign.com/seybold/](http://www.hotdesign.com/seybold/)
> **Praill said:**
> If it is actually true then it is a very valid point and I concede to you on that aspect of the discussion.
It's true. The files are usually larger because presentational information must be repeated on each page. When all the pages have only structural information, they are smaller; the presentation is in the style sheet, which the browsers download only once and store in the cache. Also structural markup is better for the search engines. The spiders don't understand that big, bold text is a heading, but they understand the meaning of the h1 element.
> **Praill said:**
> If you use tables with a php include so that all links are passed through index.php with a varible then all pages will use index.php's layout. If you have another layout you would like to use for a different set of pages you make another php file (layout2.php) and use an include function to load unique content into that new layout. It's really the same thing.
Not everyone creates dynamic sites. Static pages would be enough for static information. Sometimes CMSs have their own templates and it's easier to change a style sheet than edit a lot of markup across multiple files.
> **Praill said:**
> I'm not really sure I follow you here. Could you maybe explain this a little more? Sorry. Id like to know what you are saying though.
Suppose that you create this layout table:
```

<table>
  <tr>
    <td>
      <input type="text" name="name"><br>
      <input type="text" name="email">
    </td>
    <td>
      Name<br>
      Email
    </td>
  </tr>
</table>

```
If you see this in a browser, it's clear that you should write your name in the first field and your email in the second, because form fields and labels are visually aligned. But if you read the markup, first you see two form fields and you can't tell what they are for. Then there are the two labels. They are not in a logical order. A blind user, who is browsing your site with a screen reader, will have to guess what the form fields are for. On the other hand, if you use a logical order, semantic markup and CSS for layout:
```

<div>
  <label for="name">Name:</label>
  <input type="text" name="name" id="name">
</div>
<div>
  <label for="email">Email:</label>
  <input type="text" name="email" id="email">
</div>

```
You can read the code and understand it. It's not just meaningless tag soup to make the page look prettier.
> **Praill said:**
> I fail to see how they would be worried about saving a few bytes on layout code.[/code]
A few useless bytes times a billion page views do make a difference. In that link I gave you, they have an example of table layout that is more than 6 times larger than the CSS layout.
[quote=Praill;2608437]Using linux primarily (of course) makes it hard for me test my page in IE (ie6 is all im able to work with using wine.. and even that is unreliable).
I got IE 5, 5.5, 6 and 7 working well enough for this kind of testing with IE4linux:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)
> **Praill said:**
> Essentially it was just a nightmare. Why spend hours learning about and fiddling with unfamiliar layouts when I know tables WILL work?
Sometimes it's hard, but there are free CSS layouts that you can just download and use. There are thousands of "how to create a 2-column layout with CSS" tutorials ([here is one]("http://alistapart.com/articles/holygrail")) and sites that document IE bugs. Post your problems here and we will help you solve them. The more people use web standards now, the more the word will spread and browser vendors will be more motivated to include better CSS support in their products. Also you are tough and won't let IE beat you. ;)

---

### Post by Praill on 2007-05-08
> But you should be concerned, because the adoption of web standards will only make our jobs easier and Internet users happier. If more people create sites according to web standards, it will create more pressure on Microsoft to improve Internet Explorer.
I understand the goal behind the cause, but you have to understand that the cause may be futile. MS owns 80% of browsing activity. So if your site gives little consideration to IE users, then your site gives little consideration to 80% of your clients. Trust me, ideally I would love to run a JS check and limit access to opera users only (I hate firefox just as much for their irresponsible recommendation and support of indiscriminate ad blocking software). However, I have one goal in web development: making money. People dont come to my site to be force fed my ideals, and I dont blame them. With this goal in mind, I have to keep the majority in mind; which unfortunately means worrying primarily about a clear and consice display with IE.

> It was a presentation. You must have missed the "Next" link to the next slides...
No need to be rude. A 1 paragraph per page presentation is a bad layout and causes users to lose interest.

> It's true. The files are usually larger because presentational information must be repeated on each page. When all the pages have only structural information, they are smaller; the presentation is in the style sheet, which the browsers download only once and store in the cache. Also structural markup is better for the search engines. The spiders don't understand that big, bold text is a heading, but they understand the meaning of the h1 element.
Ah, I understand. I will concede to you on this point.. but I still see it as a miniscule improvement not near worth the headaches. Another point you could have got me on here was that display times could be faster for dial-up and lite users if the styles were cached only once :)

> 
<div>
  <label for="name">Name:</label>
  <input type="text" name="name" id="name">
</div>
<div>
  <label for="email">Email:</label>
  <input type="text" name="email" id="email">
</div>

I dont really see how this is much different than:
<table><tbody>
<tr><td>Name:</td><td><input type="text"></td></tr>
<tr><td>Email:</td><td><input type="text"></td></tr>
</tbody></table>
Ive used no more characters than you (if thats even important) and its clear to me what is being presented. But maybe Im just used to reading the code that way. Also, I could now use a style sheet to position my table just as you would have to do with your divs.

> 
I got IE 5, 5.5, 6 and 7 working well enough for this kind of testing with IE4linux:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

Did the same. In lots of spots the way IE will display through wine is drastically different than how it will display in windows. It was the last straw in abondoning CSS for me because I didnt want to reboot every time I changed the code so I could check IE.

> 
Sometimes it's hard, but there are free CSS layouts that you can just download and use. There are thousands of "how to create a 2-column layout with CSS" tutorials... The more people use web standards now, the more the word will spread and browser vendors will be more motivated to include better CSS support in their products. Also you are tough and won't let IE beat you. ;)
See thats where we differ. I dont see this as a "holy quest" against the big bad MS. Im thinking about my users and revenue. My personal opinions and ideals are of no consequence. As far as CSS getting more support.. at this point I dont really care if it does or not. CSS is more programming syntax anyways than scripting. It might confuse new users. And where are the people going to go when they divert from IE? To firefox? I would rather they stay with IE.


I would like to lastly say that Im not neccessarily arguing with you. I agree, youre probably right in that CSS is the new way to design layouts because it was intended as the proper and more efficient way to do so. But you have to understand where Im coming from too. I really dont care to write 30 lines of code, test it in firefox, then ie7 back through 5, re-write, read more, post in forums, etc. Nothing ive done has become nearly big enough for me to worry about the miniscule improvements CSS layouts can offer over the traditional border=0 tables. So why bother?
I suppose it just makes me frustrated that all these fan-boys scream 'LOL NOOB, USE CSS' just because they were told they were supposed to (no one has been able to actually give me REASONS except for you). When LOGICALLY, using css is generally ALOT more work for a smaller site.

---

### Post by LaRoza on 2007-05-08
IE used to have over 90% of users, it is now around 80%. It dropped because of Firefox. Hopefully the browser wars will continue, but this time, it will be a race to embrace standards.

---

### Post by Mirrorball on 2007-05-08
> **Praill said:**
> So if your site gives little consideration to IE users, then your site gives little consideration to 80% of your clients. [...] With this goal in mind, I have to keep the majority in mind; which unfortunately means worrying primarily about a clear and consice display with IE.
I don't block IE users and no one should. They have a right to use the worst browser ever as much as we have a right to use Opera or Firefox. But I won't throw away my dear web standards because of IE. All my layouts work on all major browsers and they use CSS.
> **Praill said:**
> No need to be rude. A 1 paragraph per page presentation is a bad layout and causes users to lose interest.
Sorry if my message was rude. I was just saying that you must have missed the Next link because you must have missed the Next link; anyone can miss a link. I'm not implying anything.
> **Praill said:**
> I dont really see how this is much different than:
In my example, the labels were on the right. With tables, you can't put the labels on the right without placing them after the fields (bad) or using advanced CSS that IE doesn't support (actually I'm not sure if it's possible). And using the label element is better for accessibility, because each label is associated with a field in a way that doesn't depend on visual layout. Copy that code and paste on a page. Then click on the label and see what happens.
> **Praill said:**
> 
Ive used no more characters than you (if thats even important) and its clear to me what is being presented.

That's because it's a table with almost no formatting (cellpadding, cellspacing, width, border etc). It's actually a good table layout as far as table layouts go. But label elements would have been a good addition.
> **Praill said:**
> In lots of spots the way IE will display through wine is drastically different than how it will display in windows.
Are you sure? No one ever complained to me about broken layouts on IE after I had fixed them using wine.
> **Praill said:**
> Im thinking about my users and revenue.
Your users would like to have smaller downloads and more accessible sites that could have been more easily found using search engine. Also if you are more productive, they can get better sites faster. Microsoft is just an obstacle in the way.
> **Praill said:**
> But you have to understand where Im coming from too. I really dont care to write 30 lines of code, test it in firefox, then ie7 back through 5, re-write, read more, post in forums, etc. Nothing ive done has become nearly big enough for me to worry about the miniscule improvements CSS layouts can offer over the traditional border=0 tables. So why bother?
It's the way to be really serious about quality, accessibility, productivity, lower costs and search engine optimization to make the web a better place for users and web designers both. We think forward about how to make better webpages and start now, forcing browsers vendors to adopt web standards.
> **Praill said:**
> I suppose it just makes me frustrated that all these fan-boys scream 'LOL NOOB, USE CSS' just because they were told they were supposed to (no one has been able to actually give me REASONS except for you).
There are stupid fan-boys that will tell you anything. They are not worth listening to.

---

### Post by Praill on 2007-05-09
> 
In my example, the labels were on the right. With tables, you can't put the labels on the right without placing them after the fields (bad) or using advanced CSS that IE doesn't support (actually I'm not sure if it's possible). And using the label element is better for accessibility, because each label is associated with a field in a way that doesn't depend on visual layout. Copy that code and paste on a page. Then click on the label and see what happens.

Ya i already said youd have to format it with styles. So if you wanted the table element that held the text to be aligned right its <td style="text-align: right;">. If you want it to be aligned right and at the top of the element its <td style="text-align: right; vertical-align: top;">


I dont think we need to keep quoting eachother. Let me just say that I appreciate all the information and the constructive conversation.
I will probably write up a CSS prototype when my user-base seems worth it. Hopefully that later date will coinside with better IE support. But right now, its still not worth the headaches.. everything works perfectly fine using tables.

---

### Post by DrFarnsworth on 2007-05-20
> **Praill said:**
> Ya, like I said it might have been an obvious solution to someone versed in php. But it wasnt for me. And endless searching never awarded me this solution. I actually figured it out entirely on my own. That's why I posted here, in the hopes that someone in my situation might come along this post sooner.

I thought i would just post up and say thank you for posting the solution to this. i was looking for something like this i had the idea in my head but i am not the best at php. so i googed it and found this post. 

you have saved me many hours of searching and pulling my hair.

---

### Post by Praill on 2007-05-22
> **DrFarnsworth said:**
> I thought i would just post up and say thank you for posting the solution to this. i was looking for something like this i had the idea in my head but i am not the best at php. so i googed it and found this post. 

you have saved me many hours of searching and pulling my hair.

Very glad to hear it. I know google actively and efficiently crawls these forums for troubleshooting and how-tos so thats why I decided to post here. 
Good luck with the rest of your site.

---

### Post by tturrisi on 2007-05-22
Praill-
It sounds like you ran "not knowing what to do" when using CSS.
CSS is indeed standardized and very reliable.  CSS can do anything that tables can do, only faster & more robust.  CSS positioning should be used in accordance with what is being positioned.  For example, a site logo that should always appear at top left of page is easily done using css: 
<img style="position:absolute; top:0px; left:0px" src="xyz.png" >
or the page heading can be absolute positioned as this section of a page will never change.
and page elements can use % for dimensions.

Scaling the page to always fit the browser window is used on a per page basis anyway, meaning that the content being deliverd is what determines if the page needs to scale to the browser window or not.

I've been doing web dev since 2000 and I used to always use tables for my page layouts, esp nested tables, but that type of coding is bloated spaghetti code that often will break when new content gets added.  Today, I use css to make table-less layouts that work in all browsers.  I refrain from using the php solution you are using as search engines will not usually index included content or they may "penalize" the page.

FYI, framesets can be used so that they scale to the browser window if the dimensions are controlled by % rather than fixed values.  And the CSS overflow & border properties can make any element mimic a frameset, confining content in a designated space.

Here's a simple 3 column layout using only css instead of nested tables.  Save as xxx.html and open in any browser.

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
<title>Demo: CSS 3 Column Layout</title>
<style type="text/css">

body {font-family:sans;
text-size:90%;
margin:10px;}

.heading {border: solid 1px blue;
height:80px;
text-align:center;
vertical-align:middle;}

.container {
width:100%;
margin:0px;
background:#ffffff;}

.left {
width:170px;
margin:0px;
float:left;
padding-top:20px;
border: solid 1px green;}

.menu_item {display:block
margin-bottom:20px;}

.right {
width:200px;
margin:0px;
float:right;
border: solid 1px black;}

.middle {
width:auto;
background:#ffffff;
border: solid 1px red;
margin-top:0px;
margin-left:170px;
margin-right:200px;
padding-top:10px;
padding-left:20px;
padding-right:20px;
padding-bottom:20px;}

.footer {border: solid 1px blue;
height:40px;
text-align:center;
vertical-align:middle;}

.cr {text-size:smaller;}

</style>
</head>
<body>
<!-- BEGIN HEADING --><div class="heading"><h1>CSS 3 Column Layout</h1></div><!-- END HEADING -->

<!-- BEGIN CONTAINER --><div class="container">

<!-- BEGIN LEFT COLUMN --><div class="left">
<h3 style="text-align:center">Left Column</h3>

<p style="height:300px; width:130px; padding:10px; text-align:center;">
<a href="" target="_top">Link Here</a><br>
<a href="" target="_top">Link Here</a><br>
<a href="" target="_top">Link Here</a><br>
<a href="" target="_top">Link Here</a><br>
<a href="" target="_top">Link Here</a><br></p>
</div><!-- END LEFT COLUMN -->

<!-- THIS RIGHT DIV MUST PRECEDE THE MIDDLE DIV -->
<!-- BEGIN RIGHT DIV --><div class="right">
<h3 style="text-align:center">Right Column</h3>

<p style="height:200px; width:180px; padding:10px; text-align:center;">This is a good spot for RSS feeds, news, weather, dynamic content, etc. etc.</p>
</div><!-- END RIGHT DIV -->

<!-- BEGIN MIDDLE DIV --><div class="middle">
<h3>Middle Column</h3>
<p>Anything can go here, such as tables, lists, images, the main content of the page. This middle column is scalable to the browser window, the left & right columns have fixed widths and will move when the browser window size changes, but the content in them does not scale beyond the column borders.</p>
<p>For demonstration purposes, the left and right columns have fixed heights, but on a real site the heights need not be fixed. The divs have different color borders, borders do not need to be used.</p>
<p>A document using this layout will look good in any size browser window. The important thing to remember is to count pixels when adding content.  For example, at a screen resolution of 800x600, the maximum available width of the middle column is approx 400 pixels.  Content wider than that will result in a horizontal scrollbar in the browser.</p>
<p>This is not really an issue because text will scale to the column width, as will any other element whose dimensions are set using percentages. The only concern is if use an image that is wider than the available column width.</p>
<p><img scr="" width="400" height="300" alt="this empty image is 400 pixels width and 300 pixels height">

</div><!-- END MIDDLE DIV -->

</div><!-- END CONTAINER -->

<!-- BEGIN FOOTER DIV --><div class="footer"><p class="cr">&copy 2006 turrisi.org</p></div><!-- END FOOTER -->
</body>
</html>

```

---

### Post by Mirrorball on 2007-05-22
Creating a CSS layout is easier if you use a strict doctype. It puts browsers in a "standards compliance mode" and they behave (mostly) according to the CSS specification. Also I wouldn't add so much inline CSS.

---

### Post by araz on 2007-05-28
Another iframe alternative using XMLHttpRequest. Take a look [here]("http://www.twinhelix.com");)

---

### Post by Praill on 2007-05-31
@ tturrisi and Mirrorball

Thanks for taking to time to show me that code, but unfortunately Im still not convinced. Mirrorball pointed out that style sheets are cached on first visit, which is an amazing thing I didnt know. Because of that I stopped using inline CSS and put everything into a style sheet. However, I still prefer table layouts to CSS. Its just too damn messy trying to get CSS positioning to work on all browsers and the w3c standards seem to be determined to make html scripting harder by depricating methods just for the sake of them being older (or so it seems).

For example, In my adventures with a strict CSS layout I came across several things that just made my eyes roll. One being the deprication of line break... wtf... why? I cant remember them all but another one was the deprication of cellpadding, which wouldnt be so bad except cellpadding is a format on a table element and the new alternative is a padding style on EACH table cell. So instead of typing cellpadding=0 once, you have to create a class and implement it on each cell... lame.

Theres a reason M$ looks at the w3c people and laughs. Standardizing a scripting language is a good thing, but w3c's idea of it is often ridiculous.

---

### Post by Mirrorball on 2007-05-31
- HTML and CSS are not scripting languages.
- Elements were deprecated because they define no meaning, only presentation. Presentation should be defined by CSS.
- The br element, cellpadding and cellspacing haven't been deprecated in HTML4/XHTML1.0.
> So instead of typing cellpadding=0 once, you have to create a class and implement it on each cell... lame.Never heard of element/child selectors?
```

<table class="x">
<tr><td>Cell 1</td><td>Cell 2</td></tr>
<tr><td>Cell 3</td><td>Cell 4</td></tr>
</table>

``````

table.x td {
  background: #000;
}

```It will apply a black background to all table cells inside tables of a class x. It's worth knowing what you are talking about before concluding it's lame.

---

### Post by tturrisi on 2007-06-01
Yes, css for tables is much more efficient than coding each <td> or <table> with cellpadding or cellspacing.  Plus, using css you can have padding & spacing different for each cell inside the table.

Inline css is necesary so as to override style sheet classes.  This is one of the things that makes css efficient, one declares the general styles for page elements and uses inline css as necessary.  CSS order of priority given by the browser is:
1. inline
2. css in head 
3, style sheet

So, if a class is described in the stylesheet such as:
td {background:#ffffff; color:#000000} and
the inline is:
<td style="background:#000000; color:#ffffff;">some text</td>
the bg of the cell will be black & the text white regardless of what is spec'd in the stylesheet.

Any issues re css positioning are because of a lack of understanding opf css positioning, period, save for a few rare browser inconsistancies when using embedded objects, iframes, etc.  The general rule is use css absolute positioning for pages that require it, such as designing for handhelds, phones, specific small screens, etc, static objects like menus, headers, areas of page for static content like ads, etc., and use css relative positioning for everything else, which is the browser default anyway.
Here's an example of absolute positioning I did many years ago when I worked for the 3Dize company (3Dize = Shelby Moore = one of the 3 original Painter programmers)
[www.coolpagehelp.com](www.coolpagehelp.com)

---

### Post by ankursethi on 2007-06-01
I don't mean to be rude, but using table layouts means being stuck in the nineties. CSS is easy to use. You seem to be a professional webmaster, but I'm 16 and I can create advanced layouts with CSS as easily as I can with tables. I don't see what's so tough about it. Plus, IE7 fixes a lot of previous bugs.

You're talking about the practical aspect of using CSS. Imagine this simple situation : you create a medium sized website with, say, 100 pages. One day you have to change not only the theme, but also the layout. Imagine that you have to move the navigation bar, which was previously located at the right hand corner, to the top of the page. I'd really like to see you do it on a website which has a tabular layout. A few minutes of extra frustration learning CSS is well worth the trouble. Table layouts are easier to build initially, but in the long run they just cause problems.

Now imagine another situation. Your website becomes insanely successful, and people demand that it be available on their mobiles. What are you going to do? A large table would just be rendered as it is. Instead of being scaled to screen, the browser willl just put a horizontal scrollbar at the bottom. And you can't change the layout because that would mean changing each one of those 100 pages. With CSS you just have to add another stylesheet for mobile devices, and the browser will find it and do the rest of the work.

You must understand that CSS serves to make the web more semantic, separating information from layout. That enables the user to view the page as he pleases. There is support for cusomized style sheets in most browsers. It also makes the work of the search engine easier.

When you say that table layouts are easier to use and more elegant and blah blah blah, then are you implying that all those websites - Google, Yahoo, Wordpress, even MSN - who use CSS layouts are all idiots? The W3C are idiots and want the developers to suffer? I don't really think so.

It doesn't matter to us whether you use tables or CSS. We are just giving advice. It's your website, do as you please.

Oh, and peace :-). I do not mean to offend.

---

### Post by Mirrorball on 2007-06-19
Good reading for anyone interested in web design:
[The Business Case for Web Standards]("http://icant.co.uk/webstandardsforbusiness/")

---

### Post by DrunkenMonkey on 2008-12-02
I'm looking for a css solution, but now i'm off to learn php :cool:

---

### Post by rtoot3 on 2008-12-02
> **Praill said:**
> I started developing with CSS positioning and XHTML but abandoned it. It was just a messy and hard to code with as tables and the end result was unpredictable behaviour on all browsers.
Tables are supported on all browsers since the dark ages, in all environments so the solution seems clear to me.

I have NO idea why all these people are developing with CSS positioning instead of tables. The only thing CSS can do that tables cant is absolute positioning.. which sucks because resizing a window breaks the absolute position and you have to implement javascript checks that, again, will vary on different browsers.

if the layouts were getting messed up in other browsers, its because you were using absolute positioning. if you just use divs and float them with css, it can prove to be much better than tables

---

