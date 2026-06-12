---
title: "I really want to learn javaScript"
date: 2010-02-18
forum: Programming Talk
---

### Post by hoboy on 2010-02-18
I really realy want to learn javaScript so I can use many of the javaScripts at code.google projects.
what ide you guys use when you code in javaScript ? I am used to Eclipse, Netbeans

like this example below how can i set my ide, that I will have code completion ?
for example
google.setOnLoadCallback(onGoogleDataLoad);
I want to be able to write google. to get access to the methods on google object, or this is impossible
to do in JavaScript ? 


<script type="text/javascript" src="http://www.google.com/jsapi"></script>
<script type="text/javascript">

  // Load the latest version of the Google Data JavaScript Client
  google.load('gdata', '2.x');

  function onGoogleDataLoad() {
    // Put your code here
  }

  // Call function once the client has loaded
  google.setOnLoadCallback(onGoogleDataLoad);

</script>

---

### Post by point_man on 2010-02-18
Hey,
I do not know about google objects as such. But a good ide for js would be aptana.. i think it is a form of eclipse. Check it out. My friends like it.

---

### Post by Jonas thomas on 2010-02-18
> **hoboy said:**
> I really realy want to learn javaScript so I can use many of the javaScripts at code.google projects.
what ide you guys use when you code in javaScript ? I am used to Eclipse, Netbeans

like this example below how can i set my ide, that I will have code completion ?
for example
google.setOnLoadCallback(onGoogleDataLoad);
I want to be able to write google. to get access to the methods on google object, or this is impossible
to do in JavaScript ? 


<script type="text/javascript" src="http://www.google.com/jsapi"></script>
<script type="text/javascript">

  // Load the latest version of the Google Data JavaScript Client
  google.load('gdata', '2.x');

  function onGoogleDataLoad() {
    // Put your code here
  }

  // Call function once the client has loaded
  google.setOnLoadCallback(onGoogleDataLoad);

</script>

I've also been very intrigued by Java script.  Check out something called Tiddly Wiki.  I use a Gtd planner called D3 which is based on Tiddly Wiki which uses Java Script.

It's on my todo list to study java script. I just hasn't been high enough on the priorities.

Here's a tutorial link that might be of interest.
[http://www.w3schools.com/JS/js_howto.asp]("http://www.w3schools.com/JS/js_howto.asp")

---

### Post by myrtle1908 on 2010-02-18
This is probably the best JavaScript tutorial you will find.  Brilliantly written.  I recommend it to all beginners.

[http://eloquentjavascript.net/](http://eloquentjavascript.net/)

---

### Post by adeypoop on 2010-02-18
You coulduse any old text editor really such as gedit.  Bluefish editor might be worth a look, i'm not sure, but it may have things like syntax highlighting for javascript. Again I'm not sure but firebug probably lets you step through code and watch variables and stuff. 

sorry for the element of vagueness, i'm also interested in linux options but I do the majority of my coding using Visual Studio in windows.

---

### Post by myrtle1908 on 2010-02-18
> **adeypoop said:**
> You coulduse any old text editor really such as gedit.  Bluefish editor might be worth a look, i'm not sure, but it may have things like syntax highlighting for javascript. Again I'm not sure but firebug probably lets you step through code and watch variables and stuff. 

Eclipse + Aptana is great with JavaScript.  Check out the spket plugin also.  And yes Firebug does indeed let you step through code, set breakpoints, watches etc.  It really is an invaluable tool for the JavaScript programmer.

---

### Post by alexk82 on 2010-02-19
i'd recommend this book as soon as you get a good grasp of javascript.  "javascript the good parts" actually to anyone who thinks they know javascript.  like most people i read the tutorials and thought i knew javascript, and began to hate it. it wasn't until i read this book that i understood it enough to appreciate it a little more

---

### Post by nexx on 2010-02-21
+1 for the book "JavaScript: The Good Parts" by Douglas Crokford.

Also [http://developer.yahoo.com/yui/theater/](http://developer.yahoo.com/yui/theater/) for a lot of high quality video tutorials. And the blogs of the individual yahoo developers are also of great help since yahoo putted all of their javaScript code on an open source license.

For programming, I use geany, a very light and fast text editor. You can see some of my work at: [www.artimap.com](www.artimap.com)

---

