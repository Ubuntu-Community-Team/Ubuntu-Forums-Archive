---
title: "Need a little web development help"
date: 2008-02-15
forum: Programming Talk
---

### Post by Yuck on 2008-02-15
Hi,

I have a [[COLOR="Red"]website here[/COLOR].]("http://www.featuregardens.co.uk") It works fine in Firefox and IE7, however there is a problem in IE6. The right hand "side bar" drops to below the main content. I have no clue why this happens.
So if any web guru could give me a tip on how to fix this I would be most grateful.

Thanks

---

### Post by Alex_Fingers on 2008-02-15
I couldn't help you much beyond telling you what I would do about it as someone who used to be a web developer many years ago:

Are you coding it yourself or using something like Dreamweaver? If you want someone to help you properly, you'd need to submit the code to this post in an attachment and a screenshot of what it looks like in IE6..

I'd just use all the tricks and tweaks until I got it right, such as changing the various cellpadding and cellspacing attributes in the table tag until I got it working, difficult to diagnose without seeing the screenshot...

---

### Post by Alex_Fingers on 2008-02-15
...nice design though !

---

### Post by 50words on 2008-02-15
Probably IE's double-margin bug. I had the same problem with my website. Add "display:inline;" to the sidebar and/or content column style, and that should fix it.

---

### Post by Washer on 2008-02-15
I'm not much of a web developer, but I heard some noise being made about this

[http://code.google.com/p/ie7-js/](http://code.google.com/p/ie7-js/)

Supposed to make IE behave like a standards-compliant browser. Anyone here used it?

---

### Post by Namtabmai on 2008-02-15
> **Washer said:**
> I'm not much of a web developer, but I heard some noise being made about this

[http://code.google.com/p/ie7-js/](http://code.google.com/p/ie7-js/)

Supposed to make IE behave like a standards-compliant browser. Anyone here used it?

I've tried it before and it's not bad, but personally I'd rather not really on Javascript hacks. Unfortunately IE is a pain to develop in, especially when compared to Firefox+Firebug.

If I had to hazard a guess at what going from with the OP site, I'd say that it was IE6's box model screwing things up. IE7 will behave because you site is valid and so will use the "normal" box model layout, where as IE6 probably uses IE's box model no matter what. Try fiddling with your paddings/fixed width values.

---

### Post by LaRoza on 2008-02-15
There is an end tag missing, close it to see if that fixes it.

If that doesn't fix it, you will either have to change your design, or accomodate IE6.

---

### Post by Bachstelze on 2008-02-15
Moved to Programming Talk.

---

### Post by RRosset on 2008-02-16
I don't know if i get it since i can't test this site in IE6, but if the problem is the padding in the bottom of the page, you should try this:

Try to remove the top padding of the class LINKS under div class wrapper and/or change the height cause that p Class is moving the bottom of the page

<div class="wrapper">
<p class="links"><b><a href="http://www.featuregardens.co.uk/privacypolicy.html">Privacy
Policy</a></b></p>
<p class="legal"><b>© 2008 Feature Gardens</b></p>
</div>

And as a bonus:

This is a never ending div!!! (neverending story music please)
<div style="clear: both; height: 1px;"/> You should close it or use a <br />

Hope this helps you, if not, lemme know or send me a screenshot in ie with the problem, i'm developing for ie6, ie7, fx and sometimes safari.

Later dude,

Bob


---------------------------------------------------

Edit, in CSS, if you use a _height after a height

it only works in IE6, so you can set two different heights in one CSS-ID-CLASS  just like this:

div#sarasa {
     height: 20px; // This works for FX and IE
     _height: 25px; // This replace ONLY in IE the previous height
}

---

### Post by Geekkit on 2008-02-16
First off ....
Good for you for going with standards and even the challenge of XHTML strict! :) This can sometimes be a daunting task. Good on you. :)

Second: Second, line 78, column 4: end tag is missing (i.e., "ol") and so your document is not strict (not well-formed) ... minor thing.

Third: I would try to take out all style from the HTML code and place it into the separate style sheet that you already have.

Fourth: I think you'll find it easier if you deal in percentages instead of pixel values. This makes it easier to deal with resolutions of any size. When you do this, to please Internet Exploder, you'll want to have your three columns equalling less than 100%. Example: column 1 == 25%, column 2 == 50%, column 3 == 22%. This is a well known IE bug ( [http://www.maxdesign.com.au/presentation/liquid/#fixing](http://www.maxdesign.com.au/presentation/liquid/#fixing) )

Last: Nice design. Very clean and pleasing to look at. :)

---

### Post by Yuck on 2008-03-18
Hi,
Been a while but had other things to do. Thanks for the compliments but I really can't take credit for the site, it is an adapted template I found ages ago. If I had the skill to write it from scratch I would probably not need help to sort this issue out.

Anyway.... it seems that there is a end tag missing. I have (with my limited knowledge) checked and checked again and I just can't find it. I'm going to post the code in the hope that some code guru will spot it right away :)

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
  <meta http-equiv="content-type"
 content="text/html; charset=utf-8" />
  <title>Feature Gardens - Southport Landscaping and Maintenance
Gardeners</title>
  <meta name="keywords"
 content="Southport, Garden, Gardens, Gardening, Gardener, Gardeners, Maintenance, Landscaping, Landscapers, Landscapes, Weeding, Rubbish, Mowing, Lawn, Turf, Fencing, Planting, Ponds, Waterfalls, Waterfeatures, Topsoil, Mulching, Residential, Commercial" />
  <meta name="description"
 content="Feature Gardens of Southport: We Provide Affordable Garden Landscaping - Garden Maintenance - Lawn Mowing - Weeding - Rubbish Removal - Fencing - Garden Design" />
  <link href="default.css" rel="stylesheet"
 type="text/css" />
</head>
<body>
<div id="menu">
<ul>
  <li class="first"><a
 href="http://www.featuregardens.co.uk" accesskey="H"
 title=""><b>H</b>omepage</a></li>
  <li><a href="http://www.featuregardens.co.uk/about.html"
 accesskey="A" title=""><b>A</b>bout
Us</a></li>
  <li><a href="maintenance.html" accesskey="M"
 title=""><b>M</b>aintenance</a></li>
  <li><a href="design.html" accesskey="L"
 title=""><b>L</b>andscape
Design</a></li>
  <li><a href="contact.html" accesskey="C"
 title=""><b>C</b>ontact
Us</a></li>
</ul>
</div>
<div id="logo">
<h1><b><a>Feature Gardens of Southport</a></b></h1>
<h2><b><a>Complete Maintenance and Landscaping Service<br />
</a></b></h2>
</div>
<div id="page">
<div id="content">
<div id="welcome">
<h2 class="title"><b>Gardening Excellence</b></h2>
<p><b><strong>Welcome to <span
 style="color: rgb(102, 102, 102);">our Websit</span>e</strong>,
we hope you find the information provided useful. We will be adding new
content
on a frequent basis. Well at least when the time permits!
We are a local and friendly firm of gardeners and cover the area from
Formby
north to Tarleton for maintenance. We travel to within a 50 mile radius
of Southport for Landscaping Contracts. We offer both Residential and
Commercial services.
We are currently updating our website with lots of new content and a
new design. You may find some pages unavailable, it will take us a
couple of days to get everything working. Please call us if you need
any help. Should you have any problems navigating the website please
let
us know
so that we can quickly rectify any fault.</b></p>
</div>
<div class="floating-box" style="margin-right: 20px;">
<p><b><img style="width: 200px; height: 90px;"
 src="images/whatamess.jpg" alt=""
 title="Wow, what a mess!" /></b></p>
<h2 class="title"><b>Garden a Mess?</b></h2>
<p><b>Leave it to us to convert that jungle or bombsite
into a place
that you can admire. Give us a call to chat about your requirements and
we'll give you&nbsp;a FREE quotation. Whether you just want a quick
Tidy Up or regular
maintenace, we can help!</b></p>
<ul>
  <li><b><a href="tidyup.html">See what we can
do in in
just a
day.</a></b></li>
</ul>
</div>
<div class="floating-box">
<p><b><img style="width: 200px; height: 90px;"
 src="images/frosty.jpg" alt=""
 title="It's getting chilly!" /></b></p>
<h2 class="title"><b>Brrr.. It's Cold</b></h2>
<p><b>...and windy! Happy New Year to all our customers!
What better time than now to let us landscape your garden? We will
beaver away while you are tucked up nice and warm. Then next spring
when you get back out there you will have a gorgeous new garden to sit
in.<a href="#"><br />
</a></b></p>
<ol>
</ol>
</div>
<h2 style="text-align: right;"><b><a><span
 style="text-decoration: underline;">Need
a Gardener? Call
us for </span><i style="text-decoration: underline;">Your</i><span
 style="text-decoration: underline;"> FREE Quotation: 07092
308691</span><br />
</a></b></h2>
</div>
<div id="sidebar">
<div id="links">
<ul>
  <li><b><a href="recent.html">Recent Projects</a></b></li>
  <li><b><a href="driveway.html">Driveways</a></b></li>
  <li><b><a href="tidyup.html">Quick Tidy Ups</a></b></li>
  <li><b><a href="turfsupply.html">Turf -
Supply Only</a></b></li>
  <li><b><a href="turf.html">Turf - Laid by
our Team</a></b></li>
  <li><b><a href="fencing.html">Fencing -
Expertly Erected</a></b></li>
  <li><b><a href="indiansandstone.html">Indian
Sandstone</a></b></li>
  <li><a href="waterfeatures.html"><b>Water
Features</b></a></li>
  <li><b><a href="planting.html">Planting</a></b></li>
  <li><b><a href="pressurewashing.html">Pressure
Washing</a></b></li>
  <li><b><a href="gallery.html">Gallery</a></b></li>
  <li><b><a href="video.html">Gardening Videos</a></b></li>
  <li><b><a href="links.html">Links</a></b></li>
</ul>
</div>
<div>
<h2><b>Ms Reyner, Cheshire</b></h2>
<blockquote>
  <p><b>..Feature Gardens did a superb job of
our&nbsp;Indian
Sandstone Patio, the new garden is the envy of the neighbours.</b></p>
</blockquote>
</div>
</div>
<div style="clear: both; height: 1px;"></div>
<!-- end #page -->
<div id="footer">
<div class="wrapper">
<p class="links"><b><a
 href="http://www.featuregardens.co.uk/privacypolicy.html">Privacy
Policy</a></b></p>
<p class="legal"><b>© 2008 Feature Gardens</b></p>
</div>
</div>
</div>
</body>
</html>

```

Appreciate all your suggestions so far, at least I'm closer to finding the problem.
Any further help would be much appreciated, as this webby does actually bring in business for me through natural google ranks.

Thanks.

---

### Post by LaRoza on 2008-03-18
Line 91, Column 4: end tag for "ol" which is not finished.
</ol>

Most likely, you nested tags and closed them in the wrong order. For example <p><em>...</p> is not acceptable, as <em> must be closed before <p>. Acceptable nesting is: <p><em>...</em></p> 

Another possibility is that you used an element which requires a child element that you did not include. Hence the parent element is "not finished", not complete. For instance, in HTML the <head> element must contain a <title> child element, lists (ul, ol, dl) require list items (li, or dt, dd), and so on.

[http://validator.w3.org/check](http://validator.w3.org/check)

---

