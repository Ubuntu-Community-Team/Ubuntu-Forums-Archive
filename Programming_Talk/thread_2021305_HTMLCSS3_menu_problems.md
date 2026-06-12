---
title: "HTML/CSS3 menu problems"
date: 2012-07-09
forum: Programming Talk
---

### Post by Superpelican12 on 2012-07-09
I'm creating a website to help people (who don't know a lot of computers) transition to Linux.

However I have problems with the HTML/CSS(3)menu. The menu made with CSS3 borders and background colors (no images) and the usual <ul><li><a> stuff. However between the "Home"-button and the "GNU/Linux News"-button there is an unnecessary blue "button". Which shouldn't be there. I can't find it's code (so I can delete it)... And there is no padding between the "strange blue button" and the "Home" and "GNU/Linux News" buttons anymore. I just can't find what is wrong.

Here you can visit the website yourself (it's still under development):
[http://switchtolinux.comoj.com]("http://switchtolinux.comoj.com") 
and here's my index.html (with embedded CSS stylesheet)
[http://ubuntuone.com/0UaV1p73vw1EAMaGei8DyU]("http://ubuntuone.com/0UaV1p73vw1EAMaGei8DyU")

or here the code just copied:
```
<html>
<head>
 <link href='http://fonts.googleapis.com/css?family=Ubuntu:400,500' rel='stylesheet' type='text/css'>
 <style type="text/css">
  
  body 
  {
  font-family: "Ubuntu", sans-serif; font-weight: 400;
  background-image:url("http://switchtolinux.comoj.com/background.png");
  font-family: 'Ubuntu', sans-serif;
  }
  
  h1
  {
  background:red;
  border:2px solid;
  border-radius:12px;
  border-color:#FF0000;
  font-family: "Ubuntu", sans-serif; font-weight: 400;
  }

  #welcome
  {
  background:#505050;
  border:2px solid;
  border-radius:12px;
  border-color:#505050;
  font-family: "Ubuntu", sans-serif; font-weight: 400;
  }
  
  #nav {font-family: "Ubuntu", sans-serif; font-weight: 500;}
  
  #nav ul 
  {
  list-style-type: none;
  color:white;
  }
  #nav ul li 
  {
  display: inline;
  margin: 0;
  padding:25px; 
  background:DarkBlue;
  border:2px solid;
  border-radius:12px;
  border-color:Darkblue;  
  color: FloralWhite;
  }
 </style>
 </head>
<body>
 <h1> Switch to GNU/Linux the easy way! </h1>
 <br>
 <br>
 <div id="nav">
    <ul>
      <li><a style="text-decoration:none; color:#FFFFFF" href="/" title="Home">Home</a><li>
      <li><a style="text-decoration:none; color:#FFFFFF" href="/news.html" title="GNU/Linux News">GNU/Linux News</a></li>
      <li><a style="text-decoration:none; color:#FFFFFF"href="/getstarted.html" title="Get started with GNU/Linux!">Get started with GNU/Linux!</a></li>
      <li><a style="text-decoration:none; color:#FFFFFF"href="plusinformation.html" title="+Information">+Information</a></li>
      <li><a style="text-decoration:none; color:#FFFFFF"href="" title="Recommended Hardware">Recommended Hardware</a></li>
    </ul>
 </div>
 <br>
 <br>
 <img src="Tux_2.png" width="170" heigth="200" alt="Tux, the Linux penguin, the mascotte of the Linux OS"/>
 <img src="reiss-head.png" alt="the GNU logo"/>
 <br>
 <br>
 <div id="welcome">
  This website is still under heavy development. Please comeback later!
  This site will help you to easily switch to GNU/Linux and provide various tips and tricks. And also links to useful information.
 </div>
</body>
</html>
```

---

### Post by Vaphell on 2012-07-09
```
<ul>
  **<li>**
    <a style="text-decoration:none; color:#FFFFFF" href="/" title="Home">Home</a>
  **[COLOR="Red"]<li>[/COLOR]**
  <li>
    <a style="text-decoration:none; color:#FFFFFF" href="/news.html" title="GNU/Linux News">GNU/Linux News</a>
  </li>

```

---

### Post by na5h on 2012-07-09
As Vaphell pointed out, you have an extra <li> tag that is actually supposed to be a closing </li> tag.

A few good tips:
Most browsers have got plenty of useful tools and add-ons that make these kinds of error-checks easy as pie: For instance, Firefox has a great add-on called "Firebug" and Opera has it's own built-in suite of developer tools called "Dragonfly". For this problem, it would have been enough in most browsers to simply right-click the "extra button" and select something like "Inspect Element" or similar... 

IDEs like [Aptana Studio]("http://www.aptana.com/") would probably have pointed out this error right away.

It's not a bad idea to [validate]("http://validator.w3.org/") you web-pages either!

---

### Post by Superpelican12 on 2012-07-09
Really thanks for the help. How stupid of me. Maybe I should use something else than Gedit for my Python scripts and webpages. But I really like Gedit and never have been really fan of IDE's (the only IDE, which I really liked was Netbeans, but Eclipse was way to difficult and bloated for me). But anyway I just downloaded Aptana, so I can give it a try.

Also I've validated my page. But it has a lot of errors and warnings :(


Are there some more extensions for Gedit which could make it more IDE'ish?


Also I'm not really into XHTML (with all the horrible things it requires) and the very long DOCTYPE. Is it allowed to mix HTML5/CSS3 with HTML/CSS2? I only use some CSS3 features for styling. What DOCType should I include? The HTML5 DOCTYPE or the "normal" HTML4 "long" DOCTYPE (I read the doctype has been simplified in HTML5).

---

### Post by na5h on 2012-07-09
Bluefish is quite nice too (it's in the Software Center): it's not as heavy and bloated as Netbeans or Eclipse, yet more powerful than a simple text editor...

---

### Post by Superpelican12 on 2012-07-09
Thanks for the tip! Bluefish seems to be very nice. I just downloaded it (so obviously I haven't tried all it' s features yet).

But at first sight I especially like the "collapse block of code"functions. I think that could really help me.:p

---

### Post by na5h on 2012-07-09
> **Superpelican12 said:**
> 
Also I'm not really into XHTML (with all the horrible things it requires) and the very long DOCTYPE. Is it allowed to mix HTML5/CSS3 with HTML/CSS2? I only use some CSS3 features for styling. What DOCType should I include? The HTML5 DOCTYPE or the "normal" HTML4 "long" DOCTYPE (I read the doctype has been simplified in HTML5).

HTML5 is backwards compatible so you can use it if you like. Just keep in mind that many of the new features in HTML5 are not yet be supported by every browser:
[http://html5test.com/results/desktop.html](http://html5test.com/results/desktop.html)

Differences between HTML5 and HTML4 (by W3C):
[http://www.w3.org/TR/html5-diff/](http://www.w3.org/TR/html5-diff/)

Use the [W3C validator]("http://validator.w3.org/") to check your code. You can also [validate your CSS]("http://jigsaw.w3.org/css-validator/")!

---

### Post by Superpelican12 on 2012-07-09
Yes I know that not all browsers support it yet. I'm still thinking of implementing a little piece of JavaScript which detects if the user uses an old version of IE (or another unsupported) browser and ask him (with an "alert box") if he would like to update his browser (preferably switch browser, install Chrome or Firefox ;) ).
I know that it's possible to detect the users browser (and even OS). Also I won't use to exotic functions (only some basic CSS3 functions) and the HTML5 video-tag.

And should I use the HTML4 DOCTYPE or HTML5's one?

---

### Post by na5h on 2012-07-09
The HTML5 doctype will do just fine...

---

### Post by Superpelican12 on 2012-07-10
Thanks for replying. I'm now trying to let my website pass the HTML5 validator. I've already squashed 4 errors. And now still have 2 errors (still working on those two) and two which aren't my fault. But those are the fault of my hosting provider (000webhost.com), the hostingprovider adds <script> tags to my webpage automatically to enable tracking stats. But I don't want tracking stats of 000webhost.com. If I'm going to implent tracking stats I will use Google. How can I fix those "false" errors from the tracking stats code?

---

### Post by trent.josephsen on 2012-07-10
Use HTTPS?

... Maybe, if you can figure out how the host decides where to insert the <script> tags, you can construct your HTML so that that part gets commented out or otherwise ignored. This MIGHT be a violation of your terms of service. Personally I'd switch hosting providers and make sure they know why.

---

### Post by na5h on 2012-07-10
I suppose you'll have to talk to your hosting provider about that. However, I don't think that the errors you mentioned will affect the usability of your website..the important thing is that your own code is somewhat well written.

Besides, it's not like all "professional" websites out there use 100% valid code all the time either. CSS effects such as [box-shadow]("http://www.css3.info/preview/box-shadow/") often look something like this on websites:```
-moz-box-shadow:10px  10px 5px #000000;
-webkit-box-shadow:10px  10px 5px #000000;
box-shadow:10px  10px 5px #000000;
```
The -moz and -webkit prefixes above are not valid by W3C standards, but are needed to make the shadow render correctly in Firefox and Chrome*. Internet Explorer usually takes even more tweaking if you want to get your CSS3 eyecandy to work...

*well...at least in older versions, I believe that "box-shadow" actually *does work* in the *latest* versions of these browsers, but you get the point...

---

