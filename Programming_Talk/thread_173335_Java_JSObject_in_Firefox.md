---
title: "Java: JSObject in Firefox?"
date: 2006-05-10
forum: Programming Talk
---

### Post by hagen00 on 2006-05-10
Hi guys

I've posted on the Java forums, but I thought I'd see what the gurus say here (Is this considered cross posting? If it is, sorry about that). 

Anyway, I'm using JSObject in my applet to call a javascript method. This works fine in IE, but not in Firefox. I've done some searching and have found many with the same problem, but no answers that work. 

Does one of you have any idea of how to user JSObject in Firefox?

Many thanks

Update: Just to say that I've tried using the <Object> and <embed> tags in Firefox, but the only one that seems to render the applet is using <applet>. My search continues.

H

---

### Post by yaaarrrgg on 2006-05-10
The last time I fiddled with Java <-> Javascript communication was about 5      years ago, so I might not be much help.  What I rememeber is that it was a      little flakey across browsers, and possibly could still be.  If you can rewrite the applet to avoid it, that's probably the best approach.

Although, I found an applet example (tested on firefox/windows xp at least) that does java -> javascript communication:
[http://www.javaside.com/asp/mus.asp?page=/us/tips/j_2.shtml](http://www.javaside.com/asp/mus.asp?page=/us/tips/j_2.shtml)
 
also, more notes: 
[http://java.sun.com/products/plugin/1.3/docs/jsobject.html](http://java.sun.com/products/plugin/1.3/docs/jsobject.html)

---

### Post by hagen00 on 2006-05-10
Thanks very much for that example yaaarrrgg. It does work in firefox, you're right. So now I know at least that it can be done! The code at first glance looks very similar, so i'm not sure what i'm missing. 

I remember reading somewhere that on compilation of the applet I might have to include the JSObject in my classpath...

I"m not really a Java programmer, so i'm not sure what that means exactly. What I do is compile the applet normally, just using javac and the create a jar file where i just include the .class files and the netscape/* folder. 

But i'm thinking maybe I need to compile the applet differently so that it also works for Firefox. I'm gonna play around a bit with this. 

None the less, thanks for the link. 

H

Update:
When I use that code from the link that yaaarrrgg gave me, I can also get JSObject to work with firefox. But that's without a jar, referencing the my local machine. 

As soon as I create a jar and upload it to the server, it doesn't work anymore, so Í'm pretty sure the problem is with how i compile my applet and jar. Currently, when creating the jar, i just include netscape/* but that doesn't seem to be working.

---

### Post by yaaarrrgg on 2006-05-10
Well, it sounds like you have your classpath correct then, if it compiles. Java is fairly picky... if it were a classpath problem, you'd probably get a page of errors when you run javac.  

If there are no compiler errors, then the problem is probably in javascript, applet/object/embed tag, or the java code.  The order of the html tags and javascript on the page could matter too (if one calls the the other before it loads).

Also from the sun link, looks like firefox only supports some, but not all of JSObject methods that IE does.

---

### Post by hagen00 on 2006-05-10
I compile the applet and jar on my windows box and then upload onto my Ubuntu Server. The Server only has the JRE, not the SDK. Do you think maybe it's because I don't compile directly on the server?

Thanks for being very helpful!

---

### Post by yaaarrrgg on 2006-05-10
That really shouldn't matter.  AFAIK, JSObject should be included with the browser.  The javac classpath is really more to verify that you are calling the library correctly.

Although, you can watch the JavaScript Console (a firefox extension), and Java console.  These should tell you if there's any runtime errors.

[edit]
Oh, are you packaging up the netscape/* classes with your jar?  I'm not sure you are supposed to do that.  To set the classpath, you can do something like (separated with colons.  include directories or jar files):

javac -cp "/path/to/netscape/classes/:/any/other/file.jar" ...

---

### Post by hagen00 on 2006-05-11
I think you're right that it isn't a classpath issue after all. Everything compiles fine and when i look at the verbose output on compilation, it definitely compiles the JSObject into my applet. 

I've also looked at the firfox java console but can't see any errors there. It just seems like "nothing" happens. 

But anyways...it's not a train smash if i disable the applet for non MSIE users. At this point I can't really spend another couple of hours on something trivial. But thanks a lot for all the suggestions and if I do manage to sort it out I'll post back here. 

Cheers

---

