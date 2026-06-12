---
title: "I'm making a full featured gui frontend for Mencoder"
date: 2011-06-07
forum: Programming Talk
---

### Post by Astrognomical on 2011-06-07
I record a lot of youtube videos. When I switched to ubuntu, I was frustrated that it was so hard to convert videos to a uploadable format. Later I found mencoder, which I currently use.

Mencoder is great, if you know exactly how to do it. There are just so many options though. I've always thought it would be a great idea for me to create a gui frontend for it, that's fully featured. And by that, I mean EVERY mencoder option available.

I'm going through different python gui toolkits. It seems like they're all dead though.

Timeline
-Settle on language [Finished] (python)
-Settle on gui toolkit [Tentative] (pygtk

EDIT: First post! Yheah!

---

### Post by Petrolea on 2011-06-07
I'd say GTK. For C++ bindings, GTKmm.
It isn't hard to program with and has many features and tutorials (there are more on GTK+ though).

A great idea btw. Report back when you create something :).

> **Astrognomical said:**
> 
EDIT: First post! Yheah!

Lol.

---

### Post by Astrognomical on 2011-06-07
I've settled on pygtk. I have more python experience, but at some point, I might do a recode in C++.

I'm stuck though. I can't find any tutorials on pygtk later than 2006. In other words, they don't work.

It's like my local library. The most recent programming book they have is from 1998.

---

### Post by Petrolea on 2011-06-07
> **Astrognomical said:**
> 
It's like my local library. The most recent programming book they have is from 1998.

I know how you feel. Once I was trying to find a book about C and the newest one was from 1983. In that book no includes were written, main was declared as main() without return. So I usually use internet for learning.

---

### Post by nvteighen on 2011-06-07
> **Astrognomical said:**
> 
I'm stuck though. I can't find any tutorials on pygtk later than 2006. In other words, they don't work.

Uh... That's not an issue: the GTK+ 2.x interface hasn't change that much from there to these days. They should work for most cases.

---

### Post by Astrognomical on 2011-06-07
I've made a breakthrough! It turns out pygtk died a while back. Now it pygobject. I'm googling now...

> **nvteighen said:**
> Uh... That's not an issue: the GTK+ 2.x  interface hasn't change that much from there to these days. They should  work for most cases.
all the code that loads the gui is broken.

Edit: I found out that there was a 2011 release of pygtk. I'm going to use that until gobject becomes a package on software center, because I don't want users to have to compile a bunch of source. I'm terrible at packaging apps, so if anyone wants to help, that would be appreciated.

---

### Post by stchman on 2011-06-07
If you are going to make a GUI front end for a command line app, then Java would be the way to go.

Using Java would allow you to use the Java app on any OS.

---

### Post by Petrolea on 2011-06-07
> **stchman said:**
> If you are going to make a GUI front end for a command line app, then Java would be the way to go.

Using Java would allow you to use the Java app on any OS.

Not true. 

Program would be based on mencoder, not Java code. If I understand this correctly, it will be a GUI for command line, which is not portable at all unless you have mencoder on other OSs configured correctly to work with the GUI right away (which can be hard for some OSs, or even impossible).

---

### Post by stchman on 2011-06-07
> **Petrolea said:**
> Not true. 

Program would be based on mencoder, not Java code. If I understand this correctly, it will be a GUI for command line, which is not portable at all unless you have mencoder on other OSs configured correctly to work with the GUI right away (which can be hard for some OSs, or even impossible).

Mencoder is available for OS X.

My argument was that if he programs the GUI using pygtk then you would have to get a GTK+ environment for whatever OS you want to run it on.

Java Swing based apps are far more portable that GTK apps.

---

### Post by Petrolea on 2011-06-08
> **stchman said:**
> Mencoder is available for OS X.

My argument was that if he programs the GUI using pygtk then you would have to get a GTK+ environment for whatever OS you want to run it on.

Java Swing based apps are far more portable that GTK apps.

Yes, Swing is portable (but takes lots of resources). Problem would still occur on Windows though.

So I recommend you start with Ubuntu (or other Linux distros) and then expand it to other OSs (you can do it in Java of course + it shouldn't be too hard since there are many tutorials on it).

---

### Post by cgroza on 2011-06-08
WxWidgets should be the solution to this. It is more portable than pygtk and it has python bindings too: wxPython.

---

### Post by stchman on 2011-06-08
> **Petrolea said:**
> Yes, Swing is portable (but takes lots of resources). Problem would still occur on Windows though.

So I recommend you start with Ubuntu (or other Linux distros) and then expand it to other OSs (you can do it in Java of course + it shouldn't be too hard since there are many tutorials on it).

Netbeans includes a GUI builder so making GUIs is a snap.  All he would need to so is have it call mencoder with the proper command line arguments.

---

