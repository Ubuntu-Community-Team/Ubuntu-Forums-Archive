---
title: "Internet Explorer Breaking my back!"
date: 2007-11-12
forum: Programming Talk
---

### Post by dmwilson86 on 2007-11-12
Okay, I switched over to Ubuntu just before I decided to start making websites, so I designed my site using a simple localhost apache server on my desktop just for testing and getting to know how things work.  However, I designed the site with firefox for testing.  So there are a couple issues that I would like to work out that hindering smooth i.e. parsing.  I'm just gonna throw them out here:

-When using png files the alpha background is changed to white, is there any way to use alpha backgrounds with internet explorer?

-The ajax requests won't work (with i.e.)  I did the standard setup from the Ajax Design Patterns  book by Michael Mahemoff.. I'm just going to attach what i've come up with so far here in a tar file.  There is the index.html, style.css, and javascript.js Any pointers or contsructive criticism would be much appreciated.

-The positioning is terribly different in internet explorer, is there a small application that will cause the browser to be automatically detected and change the documents used according to which browser is being used?  Is this the best way to go about solving this problem?

You guys are awesome!  Thanks again!!!

---

### Post by Compyx on 2007-11-12
Sounds like you've just run into one of the greatest horrors of webdesign: Internet Explorer.

Make sure your code validates by using W3C's validators for HTML and CSS. Then look up 'Internet Explorer hacks' with your favourite search-enige and discover why IE is the nemesis of webdesigners world-wide ;)

---

### Post by geirha on 2007-11-12
> **dmwilson86 said:**
> -When using png files the alpha background is changed to white, is there any way to use alpha backgrounds with internet explorer?

I believe there is a plugin of some sort you can install in internet explorer, but then everyone viewing your page with ie would have to install it.

> **dmwilson86 said:**
> -The positioning is terribly different in internet explorer, is there a small application that will cause the browser to be automatically detected and change the documents used according to which browser is being used?  Is this the best way to go about solving this problem?

It is common to make a stylesheet for IE, and another stylesheet for "everyone else". Microsoft make their own standards, that's just the way it is :) There are some differences between other browsers as well in their support of css, but they can usually be overcome without seperating the stylesheets further. Have a look at wikipedia's stylesheets.

---

### Post by pmasiar on 2007-11-12
for AJAX, you may want to use one of the many available JS libraries, with code workaround for JS incompatibilities. That AJAX library should come with web app framework you use, so just learn it, and don't waste time - incompatibilities are plenty, and everyone is in the situation like you are. Thanks, Mr Gates: standards are good thing, and the more we have, the happier we will be! :-)

---

### Post by Kadrus on 2007-11-12
Internet Explorer must be the worst browsers ever!lol...:P..

---

### Post by g2g591 on 2007-11-12
id say just post a note saying this website is standerds compliant, IE is not, if you want a more standerds compliant browser (which will greatly help the display of this site) use Firefox or Opera

---

### Post by NeillHog on 2007-11-12
This is exactly why I gave up web design. If you get the page working for IE it still may not work in the next version.
The only answer that really works is to keep your design very simple and as far as possible do any scripting server side where you know that it works.
Sorry!
Neill

---

### Post by Kadrus on 2007-11-12
> **dmwilson86 said:**
> Okay, I switched over to Ubuntu just before I decided to start making websites, so I designed my site using a simple localhost apache server on my desktop just for testing and getting to know how things work.  However, I designed the site with firefox for testing.  So there are a couple issues that I would like to work out that hindering smooth i.e. parsing.  I'm just gonna throw them out here:

-When using png files the alpha background is changed to white, is there any way to use alpha backgrounds with internet explorer?

-The ajax requests won't work (with i.e.)  I did the standard setup from the Ajax Design Patterns  book by Michael Mahemoff.. I'm just going to attach what i've come up with so far here in a tar file.  There is the index.html, style.css, and javascript.js Any pointers or contsructive criticism would be much appreciated.

-The positioning is terribly different in internet explorer, is there a small application that will cause the browser to be automatically detected and change the documents used according to which browser is being used?  Is this the best way to go about solving this problem?

You guys are awesome!  Thanks again!!! 

You can just alert the user...if he is using Internet Explorer tell him to install Firefox so he can see all the features of your website

```
<html>
<head>
<script type="text/javascript">
function detectBrowser()
{
var browser=navigator.appName
var b_version=navigator.appVersion
var version=parseFloat(b_version)
if ((browser=="Microsoft Internet Explorer"))
  
  {alert("Please install Firefox so you can see all the features of my website!!")}
}
</script>
</head>

<body onload="detectBrowser()">
</body>

</html>


```

Or something like this..euuh..can you tell me if the code is right because i don't have IE...and i just want to know if it's right..thanks anyway..

---

