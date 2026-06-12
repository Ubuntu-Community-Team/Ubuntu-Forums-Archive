---
title: "NetBeans 6.9 released!"
date: 2010-06-16
forum: Programming Talk
---

### Post by kahumba on 2010-06-16
It's official folks!
[http://netbeans.org/community/news/show/1480.html](http://netbeans.org/community/news/show/1480.html)

---

### Post by RedMoonReflection on 2010-06-16
Realy good news! I'm using NetBeans too to learn C++. Locking forward to use release 6.9.
 
RedMoonReflection

---

### Post by Reiger on 2010-06-16
Gah, yesterday I reinstalled 6.8...!

---

### Post by evaarties on 2010-06-17
Will this release get available to ubuntu 10.04 via the normal sources? Or is 6.9 large enough only to be included in ubuntu 10.10?

---

### Post by juancarlospaco on 2010-06-17
Just curious, why do you need these so big thing to write code...?

*i use any simple editor, or plain ed*

---

### Post by evaarties on 2010-06-17
> **juancarlospaco said:**
> Just curious, why do you need these so big thing to write code...?

*i use any simple editor, or plain ed*

In the past, I used a text editor as well. Since a few years I 've switched to NetBeans and must say, the autocompletion is the best advantage I can think of.

Give it a try and you'll see what I mean.

---

### Post by juancarlospaco on 2010-06-17
Already tested all, i dont understand it.

i can write my code with paper and pen, ed or NetBeans 8
but Netbeans is like +200Mb :(
vim, emacs, pyroom or ed a few Kb :)

---

### Post by ufis on 2010-06-17
> **juancarlospaco said:**
> Just curious, why do you need these so big thing to write code...?

*i use any simple editor, or plain ed*

Go and try to code/refactor/debug a java system with more than 500 classes with your simple editor and you will see why using IDEs is not only useful but also necessary.

---

### Post by KdotJ on 2010-06-17
I watched a few of the videos, looks very good. I'm already a fan of Netbeans, despite my opinion of it looking horrible in gtk+ look and feel.
I'll definately have a look into using 6.9 and hopefully it will make the cut into 10.10

---

### Post by oc666 on 2010-06-21
Is there any repository for this version?

---

### Post by evaarties on 2010-06-21
After installing Netbeans 6.8 from the repository, I noticed it's the version with Java support not PHP.

This made me decide to just go and download Netbeans 6.9 with PHP support from [www.netbeans.org](www.netbeans.org).

It installed flawlessly on Ubuntu 10.04 64bit and works great!

---

### Post by oc666 on 2010-06-21
> **evaarties said:**
> After installing Netbeans 6.8 from the repository, I noticed it's the version with Java support not PHP.

This made me decide to just go and download Netbeans 6.9 with PHP support from [www.netbeans.org](www.netbeans.org).

It installed flawlessly on Ubuntu 10.04 64bit and works great!

Thanks.
Also confirmed it's working on Ubuntu 10.04 64bit: 6.8 (repository) side by side 6.9 (netbeans.org download). :guitar:

---

### Post by kahumba on 2010-06-21
> **KdotJ said:**
> I watched a few of the videos, looks very good. I'm already a fan of Netbeans, despite my opinion of it looking horrible in gtk+ look and feel.
I'll definately have a look into using 6.9 and hopefully it will make the cut into 10.10
Agree, gtk looks horribly, I sometimes switch to Nimbus L&F (see netbeans.png)
Right-click the applications applet -> Edit Menus, then Programming->NetBeans (see edit.png) and add "--laf Nimbus" to the Command text field and launch NetBeans from the application menu again.

EDIT: But sometimes a few dialog boxes (like "update") don't look as expected since NetBeans hasn't been designed from the ground up with Nimbus in mind. Hopefully these (minor) glitches will be fixed in NetBeans 7.0 or so.

---

### Post by Philio on 2010-06-25
> **evaarties said:**
> After installing Netbeans 6.8 from the repository, I noticed it's the version with Java support not PHP.

This made me decide to just go and download Netbeans 6.9 with PHP support from [www.netbeans.org](www.netbeans.org).

It installed flawlessly on Ubuntu 10.04 64bit and works great!

Just came across this while I was having a quick look to see if there were any debs floating around for 6.9.

The repo version of Netbeans is a fairly basic install, simply go to tools -> plugins and you can add just about every major language to Netbeans! There are 120 odd plugins in 6.8, I have mine setup for PHP and Android dev for example.

---

### Post by kpkeerthi on 2010-06-25
> **juancarlospaco said:**
> Already tested all, i dont understand it.

i can write my code with paper and pen, ed or NetBeans 8
but Netbeans is like +200Mb :(
vim, emacs, pyroom or ed a few Kb :)

Does your editor auto deploy (a J2EE app, for instance) as and when you change code? - Just code, save and test. No build and deploy. Netbeans/Glassfish can even persist session across server reboots so you don't have to start your testcase all over again.

Does your editor display coding errors as and when you type? - No need to compile.

Does your editor allow you to do complex refactorings and automatically find and update references?

Does your editor allow you to visually assemble screens/UI components?

Does your editor allow you to visually debug your application, inspect variable, change code on-the-fly and automatically re-execute the changed code fragment? You could even debug a remote application.

Does your editor allow you to profile your application - Monitor performance/memory metrics, leaks, call trace, etc. visually?

Does your editor allow you to instantly create many different application flavors and automatically setup the required infrastructure required - like a Desktop app, a mobile app, a J2EE app, etc. ?

+ a ton more...

I understand editors like vim/emacs are powerful. But its not fair to compare them with an IDE like Netbeans/Eclipse. IDEs are a different beast altogether. An IDE is not an editor. Enjoy coding :)

---

### Post by KdotJ on 2010-06-25
> **kahumba said:**
> Agree, gtk looks horribly, I sometimes switch to Nimbus L&F (see netbeans.png)
Right-click the applications applet -> Edit Menus, then Programming->NetBeans (see edit.png) and add "--laf Nimbus" to the Command text field and launch NetBeans from the application menu again.

EDIT: But sometimes a few dialog boxes (like "update") don't look as expected since NetBeans hasn't been designed from the ground up with Nimbus in mind. Hopefully these (minor) glitches will be fixed in NetBeans 7.0 or so.


Nice man thanks for the tip, I like nimbus

---

### Post by notmyidea on 2010-06-26
> **kpkeerthi said:**
> 
I understand editors like vim/emacs are powerful. But its not fair to compare them with an IDE like Netbeans/Eclipse. IDEs are a different beast altogether. An IDE is not an editor. Enjoy coding :)

Or get the best of both worlds and install the jVi plug-in :P

---

### Post by wkhasintha on 2010-06-26
> **kahumba said:**
> Agree, gtk looks horribly, I sometimes switch to Nimbus L&F (see netbeans.png)
Right-click the applications applet -> Edit Menus, then Programming->NetBeans (see edit.png) and add "--laf Nimbus" to the Command text field and launch NetBeans from the application menu again.

EDIT: But sometimes a few dialog boxes (like "update") don't look as expected since NetBeans hasn't been designed from the ground up with Nimbus in mind. Hopefully these (minor) glitches will be fixed in NetBeans 7.0 or so.

Thanx for the tip bro!:popcorn:

---

### Post by Lord.Quackstar on 2010-07-06
Is this update going to be included in lucid-backports? If so, when? I would really like to keep with the repository versions instead of going out and downloading 6.9 separately.

---

