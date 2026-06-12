---
title: "Programming (Java) in Ubuntu"
date: 2009-09-30
forum: Programming Talk
---

### Post by jejune2 on 2009-09-30
I've just started using Ubuntu and I'm taking a class in Java programming. I'm going to need to do some programming at home but I'm having problems getting started. I downloaded BlueJ and after hours of learning about the terminal and getting used to the OS I still haven't managed to get it working. (I can't really follow the installation guide on their website.)

Does anyone know of a simple IDE for beginners that's easy to install? It doesn't need to have any specific features, just the basics. Also is there a guide for getting the JDK on linux? Basically I need a tutorial for novice programmers, I can't seem to find any myself, all the good ones are for windows unfortunately.

Thanks.

---

### Post by howlingmadhowie on 2009-09-30
probably best to install netbeans. it's in the repos so a simple 

sudo apt-get install netbeans

should suffice.  have fun!

---

### Post by credobyte on 2009-09-30
To install JRE ( if already installed, aptitude will skip over it ) and JDK open Terminal and paste in this command:
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-jdk sun-java6-fonts
```

Regarding IDE's - Eclipse, NetBeans, jEdit ( not an IDE, tough, pretty nice Java editor ).

---

### Post by Renée Jade on 2009-09-30
If your course is blueJ based then I would recommend that you do your best to get blueJ working at home. My first Java course used blueJ and they relied on it heavily - it is *not* just an IDE. It has special features that are designed to give a novice programmer solid perspective on the principals of OOP. If you're totally new to coding it will make your first few weeks much less painful. You *can* bypass blueJ and go straight to writing stand-alone programs from the start, but you will have to do extra work than if you were using blueJ (if you have programmer friends then asking them for help will make this extra work much easier). Once you have installed the JRE and JDK, as outlined by credobyte, then you should be able to get blueJ working by following the instructions on the website for UNIX.

If you have coding experience already or if you don't want to bother with blueJ then I would also recommend Netbeans if you want to use an IDE.

If you still have problems just shout. Good luck.

---

### Post by jejune2 on 2009-10-01
> **Renée Jade said:**
> If your course is blueJ based then I would recommend that you do your best to get blueJ working at home. My first Java course used blueJ and they relied on it heavily - it is *not* just an IDE. It has special features that are designed to give a novice programmer solid perspective on the principals of OOP. If you're totally new to coding it will make your first few weeks much less painful. You *can* bypass blueJ and go straight to writing stand-alone programs from the start, but you will have to do extra work than if you were using blueJ (if you have programmer friends then asking them for help will make this extra work much easier). Once you have installed the JRE and JDK, as outlined by credobyte, then you should be able to get blueJ working by following the instructions on the website for UNIX.

If you have coding experience already or if you don't want to bother with blueJ then I would also recommend Netbeans if you want to use an IDE.

If you still have problems just shout. Good luck.

We actually use textpad and there isn't a linux version for it (I don't want to run it with wine). We were told not to use any programs that did the work for us because they want us to write all the code ourselves. I've followed the instructions on this thread and got Netbeans yesterday, and on the startup it has a wizard to name classes and a template, features which I'm not supposed to use... Is there a basic editor like textpad for ubuntu? If not, it doesn't really matter since we're learning on textpad so there won't be anything on there that's not on Netbeans.

---

### Post by Mighty_Joe on 2009-10-01
> **jejune2 said:**
> Is there a basic editor like textpad for ubuntu? 

I use [JEdit]("http://www.jedit.org/") when I'm not using Eclipse.  It's a "programmer's editor" (language-sensitive syntax highlighting and indenting) and can be extended with plug-ins to do pretty much anything.
IDE's can be very handy if you know what you are doing, but if you are just learning, they can be very confusing and sometimes one will end up struggling on getting the IDE to do what they want rather than working on the problem at hand.

---

### Post by The Cog on 2009-10-01
If you use a text editor, I really recommend geany. It's in the repositories. It's available for windows too. It's not a full-blown IDE but an editor with some simple utilities like a compile button that automatically highlights the first compile error, and a list of classes and methods on the left hand side so you can click one and jump straight to the line. It's probably just what your course needs. 

BlueJ might still be worth a try because of its ability to draw a diagram of the way classes use each other, but the fonts in the editor are horrible and they make it most unpleaseant to use.

To install BlueJ, I always download the jar file version, then open a terminal in the directory I downloaded it to, and run the command **java -jar bluej.jar** which launches the installer.

---

### Post by jejune2 on 2009-10-01
> **The Cog said:**
> If you use a text editor, I really recommend geany. It's in the repositories. It's available for windows too. It's not a full-blown IDE but an editor with some simple utilities like a compile button that automatically highlights the first compile error, and a list of classes and methods on the left hand side so you can click one and jump straight to the line. It's probably just what your course needs. 

BlueJ might still be worth a try because of its ability to draw a diagram of the way classes use each other, but the fonts in the editor are horrible and they make it most unpleaseant to use.

To install BlueJ, I always download the jar file version, then open a terminal in the directory I downloaded it to, and run the command **java -jar bluej.jar** which launches the installer.

Thank you this is just what I was looking for. I tried JEdit but using the terminal to compile and run is tedious, with this it's quick.

Thanks everyone.

---

### Post by Renée Jade on 2009-10-02
Ohhhh. OK. Sorry for the misinterpretation.

---

### Post by dvlchd3 on 2009-10-02
> **jejune2 said:**
> We actually use textpad and there isn't a linux version for it (I don't want to run it with wine). We were told not to use any programs that did the work for us because they want us to write all the code ourselves. I've followed the instructions on this thread and got Netbeans yesterday, and on the startup it has a wizard to name classes and a template, features which I'm not supposed to use... Is there a basic editor like textpad for ubuntu? If not, it doesn't really matter since we're learning on textpad so there won't be anything on there that's not on Netbeans.

Textpad is just a text editor.  You can use gedit, or any other text editor in Ubuntu, and then compile your java program from a terminal:
javac myClass.java

To execute:
java myClass

---

### Post by Mighty_Joe on 2009-10-02
> **jejune2 said:**
>  I tried JEdit but using the terminal to compile and run is tedious, 

The in-process compile functionality is available as a [plug-in]("http://plugins.jedit.org/plugins/?JCompiler"), as are many other features of JEdit.

---

### Post by chrisjsmith on 2009-10-02
Try Eclipse.  It might be a little on the "heavy side" for your requirements but it does all the compilation stuff in the background for you.

---

### Post by zoff_ita on 2009-10-03
I suppose Geany will make the deal...
It's very light and amek the job...

Anyway you can try this:
[http://ubuntuforums.org/showthread.php?t=414544](http://ubuntuforums.org/showthread.php?t=414544)

---

### Post by leifjonny on 2009-10-03
I find both Netbeans and Eclipse to be good IDEs, but Netbeans can produce code for you and I find it causes you to loose control over your code. However it is great to develop GUIs.

If you are taking an elementary java course and writing simple programmes I urge you not to use an IDE, but an editor like emacs or vim because it gives you total control over the code and you learn the most.

---

