---
title: "Deploying to context root"
date: 2007-09-25
forum: Programming Talk
---

### Post by cjnkns on 2007-09-25
I bought hosting services though dailyrazor.com and I am trying to figure out how deploy my app let's say MyApp.war to my root domain name.
So when someone goes to my url [www.myurl.com](www.myurl.com) they can access and not [www.myurl.com/MyApp](www.myurl.com/MyApp)

I have looked around but can not figure out how this is done.. any ideas?

---

### Post by cjnkns on 2007-09-25
Oops sorry I am missing a lot of information here.

I am using Tomcat 5.x and tomcats admin manager to deploy apps. 
When deploying locally (on my machine) I can just copy an exploded web direcotry to ROOT and it works just fine -but i can't figure out how to copy a war to webapp or to ROOT and still be able to access it from the root url...

Thanks,

---

### Post by mssever on 2007-09-26
If you're running on Apache with mod_rewrite, you could use mod_rewrite.

---

### Post by sgordon on 2007-10-03
Ok, after a lot of fiddling, managed to get this to work. Using the info at:
[http://tomcat.apache.org/tomcat-5.5-doc/config/context.html](http://tomcat.apache.org/tomcat-5.5-doc/config/context.html)

I *can* get an application to deploy and replace the '/' (ROOT) context, but not by using the Tomcat application manager.

I can step through it, but you need access to the filesystem where tomcat is deployed. Can you get this, or are you limited to deploying via the manager application?!

  Si

---

