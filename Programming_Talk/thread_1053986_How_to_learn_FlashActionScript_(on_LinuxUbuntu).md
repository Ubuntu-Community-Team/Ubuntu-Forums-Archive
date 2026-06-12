---
title: "How to learn Flash/ActionScript (on Linux/Ubuntu)?"
date: 2009-01-29
forum: Programming Talk
---

### Post by cl333r on 2009-01-29
Hi folks,
I'm coming from Java and wanna start writing flash instead of applets.

In Java to create a swing applet I used to:
1) write the source code for the applet.
2) compile it.
3) pack into a jar (optional)
4) write the html page for the applet
5) open the html page in the browser.

Is there such a tutorial that teaches these basic things (which would also run on Linux/Ubuntu) without having to use Windows and their graphical tools?

I'm used to writing Swing interfaces _by hand_ (like applet on the screenshot), but since the applets are only on like 60% of pcs (at least in my country) and flash is on like 98% pcs I'm very motivated to move to flash.

---

### Post by DFord425 on 2009-01-29
Take a look at Adobe Flex [http://www.adobe.com/products/flex](http://www.adobe.com/products/flex)
The flex builder is based off eclipse and i do believe it can run on Linux, but its expensive.

---

### Post by Kilon on 2009-01-29
> **cl333r said:**
> Hi folks,
I'm coming from Java and wanna start writing flash instead of applets.

In Java to create a swing applet I used to:
1) write the source code for the applet.
2) compile it.
3) pack into a jar (optional)
4) write the html page for the applet
5) open the html page in the browser.

Is there such a tutorial that teaches these basic things (which would also run on Linux/Ubuntu) without having to use Windows and their graphical tools?

I'm used to writing Swing interfaces _by hand_ (like applet on the screenshot), but since the applets are only on like 60% of pcs (at least in my country) and flash is on like 98% pcs I'm very motivated to move to flash.

why not JavaFX ?

[http://javafx.com/](http://javafx.com/)

---

### Post by cl333r on 2009-01-29
> **Kilon said:**
> why not JavaFX ?

[http://javafx.com/](http://javafx.com/)

As I stated in the first post, because of the market share, and JavaFX penetration is even lower than that of Java because it requires Java 6 update 10 and above and works bad on Linux.

off-topic, the background sound on your blog is very nice

---

### Post by Kilon on 2009-01-29
JAVAFX was released just this year. Give one year time and will be much more portable and much more popular. Because JAVAFX can import java code directly and simply , it will be only a matter of time before JAVAFX will be breathing on Actionscript neck.  

If you already know java , the JAVAFX is an excellent investment. 

Not that Actionscript is a bad investment either. 

> 
off-topic, the background sound on your blog is very nice

Ahh thank you very much , you are very nice. It is actually music that I have composed, there is player on the right of the blog where you can choose which of my tracks you can listen to.

---

### Post by cl333r on 2009-01-29
I share your optimism and goodwill about JavaFX and when the times comes that JavaFX matures and gains (overwhelming) market share penetration I will of course switch (back).
I used to be a "defender" of Java until I understood that I'm swimming against the current. Even on their forums I was criticizing Sun for not taking decisions developers and designers have been waiting for so long, but they didn't do anything, except for one thing (among many) that I've been suggesting:
- to remove the "Java applet window" sticker from the applet dialogs. But even this issue has not been solved well enough.
Eventually I gave up and decided to switch.

---

### Post by Kilon on 2009-01-29
> **cl333r said:**
> I share your optimism and goodwill about JavaFX and when the times comes that JavaFX matures and gains (overwhelming) market share penetration I will of course switch (back).
I used to be a "defender" of Java until I understood that I'm swimming against the current. Even on their forums I was criticizing Sun for not taking decisions developers and designers have been waiting for so long, but they didn't do anything, except for one thing (among many) that I've been suggesting:
- to remove the "Java applet window" sticker from the applet dialogs. But even this issue has not been solved well enough.
Eventually I gave up and decided to switch.

fair enough, that looks like a good enough reason.

---

### Post by curvedinfinity on 2009-01-29
I've never used it, but give this a shot:
[http://www.mtasc.org/](http://www.mtasc.org/)

:)

---

### Post by cl333r on 2009-02-04
I created my own "Flash Tool" (written in Java) that is a graphical frontend to compile and run ActionScript by just clicking on the corresponding button, simple and easy. Screenshots attached - 1st when compiling, 2nd - when running.

---

### Post by Circus-Killer on 2009-02-04
in terms of JavaFX, should i just download the SDK or does NetBeans offer a lot in terms of JavaFX.

basically i currently am still learning Java, which i use a straight forward text editor. but i want to know will i get more out of JavaFX if i use NetBeans, or should i just carry on using a standard text editor.

---

### Post by cl333r on 2009-02-04
> **Circus-Killer said:**
> in terms of JavaFX, should i just download the SDK or does NetBeans offer a lot in terms of JavaFX.

basically i currently am still learning Java, which i use a straight forward text editor. but i want to know will i get more out of JavaFX if i use NetBeans, or should i just carry on using a standard text editor.

Well, this post is about Flash/ActionScript, and JavaFX is quite another technology, but putting that aside, there's a dedicated NetBeans download pack which has out-of-the-box support for JavaFX, otherwise you'll have to download the plugin manually from Tools->plugins and see whether that's enough. But, Sun doesn't officially support JavaFX on Linux so either wait until it happens or google for workarounds.

[http://www.netbeans.org/downloads/index.html](http://www.netbeans.org/downloads/index.html)
If you check this page from Linux, the option to download the "JavaFX" pack will be disabled for the reason above.

---

