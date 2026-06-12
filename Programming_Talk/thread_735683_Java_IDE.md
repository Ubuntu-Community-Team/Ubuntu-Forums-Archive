---
title: "Java IDE"
date: 2008-03-25
forum: Programming Talk
---

### Post by Nuceria on 2008-03-25
Hi,

I'm new to linux and and I am now stuck with it as because of a botched install (really long story). This isn't necessarily a bad thing, but about half of my homework is from my computer science class. My problem is that I can't seem to get my JCreator to run in wine. Any help or suggestions would be greatly appreciated. Thanks

---

### Post by LaRoza on 2008-03-25
Any reason why you are using Wine to program in a cross platform language?

I suggest using a Linux tool. Directions for using Java are in the sticky, and there are many IDE's you can use.

---

### Post by CptPicard on 2008-03-25
Just took a quick look at the JCreator website...

> 
JCreator is written entirely in C++, which makes it fast and efficient compared to the Java based editors/IDE's.

Funny how one needs to advertise an IDE for some language *not* being written in that particular language, because it would make the end result be slow and inefficient :)

@OP, Eclipse and Netbeans are your choices, both are good. I tend to be partial towards Netbeans.

---

### Post by Nuceria on 2008-03-25
Thanks, I will definitely check out some of the Linux programs (I wasn't aware that there were any), but I would love to be able to run J Creator because it was the program that I am the most familiar with and the install that I have on my flash drive is already configured. Anyway, thanks for the fast reply.

---

### Post by pmasiar on 2008-03-25
> **CptPicard said:**
> Funny how one needs to advertise an IDE for some language *not* being written in that particular language, because it would make the end result be slow and inefficient :)


...but but but Java is so enterprisey! Every PHB knows (he overheard it at watercooler) that Java is it!

... and in addition to that, Java was designed to be for desktop apps....

At the last meeting, when we were talking about how to write report supporting the grant for cluster programming we want to get, I teased my colleagues cluster gurus (who use Python to generate customized C programs) to mention "and it will be written in Java". They laughed at me, and boss was mildly confused, but we both understand the joke and did not elaborate :-)

...please go on, no rubbernecking, nothing to see here... :-)

---

### Post by jespdj on 2008-03-26
> **CptPicard said:**
> Just took a quick look at the JCreator website...

*JCreator is written entirely in C++, which makes it fast and efficient compared to the Java based editors/IDE's.*

Funny how one needs to advertise an IDE for some language *not* being written in that particular language, because it would make the end result be slow and inefficient :)
What?! It does really say that on the website... :roll:

Incredible that even a company who is selling an IDE for Java is so stupid to spread this kind of nonsense.

---

### Post by Lord Illidan on 2008-03-26
That said, eclipse is a bit bloated.

---

### Post by CptPicard on 2008-03-26
And its plugins never work. At least that is my experience. With Eclipse you're constantly fighting the setup, having to reinstall all the time from scratch, getting NullPointerExceptions and other mystical errors thrown at you while you're trying to work...

The base Java editor is good though, still better than Netbeans IMO. But Netbeans' other tool integration is just way superior.

---

### Post by Lord Illidan on 2008-03-26
I never use any external plugins, there's way too much work involved to do them. The worst part was trying to make it do UML for a project that we had to hand in the next day. Finally, I gave up, imported it into netbeans and took around 5 minutes :D

---

### Post by themusicwave on 2008-03-26
Ironically I use eclipse for Python development with pydev.  It is a bit nicer to me than IDLE.  I still use IDLE for small stuff though.  I also like it's PHP plugin(although I dislike PHP :)) 

For Java I use Netbeans, same experience as Capt Picard.  The plugins in Eclipse will drive you insane.  Eclipse has it's own version of dependency hell too.  Where plugins depend on each other, so you have to hunt the web to find the link for the referenced plugin.  At least that was my issue.

Netbeans also has a decent swing GUI editor, which I couldn't find for eclipse.  If anyone knows a free on let me know.

I also find Netbeans is a bit faster than Eclipse and a lot nicer to me in general.  Sometimes when I open Eclipse it greets me with a barrage of NullPointerExceptions and I then have to close it and open it again.  It will then magically work, very strange.  I think it may be something wrong with all those plugins...

If you search I think you will find this Eclipse Vs Netbeans thing has been going on on the forums for awhile.

---

### Post by drubin on 2008-03-26
> **CptPicard said:**
> 
Funny how one needs to advertise an IDE for some language *not* being written in that particular language, because it would make the end result be slow and inefficient :)

@OP, Eclipse and Netbeans are your choices, both are good. I tend to be partial towards Netbeans.

Net beans is written in java  :)

---

### Post by CptPicard on 2008-03-26
> **rubinboy said:**
> Net beans is written in java  :)

...yes?

This wasn't criticism of IDEs written in Java, I just found JCreator's statement humorous in general :)

(Mind you, if you write an IDE for Java in something else than Java, you're missing out on a LOT of language features that are great for an IDE... compiler and profiler API integration and introspection to name a couple)

---

### Post by drubin on 2008-03-26
I use netbeans every day.  It still surprises me all that you can do with it.

---

### Post by Lord Illidan on 2008-03-26
What I don't like about Netbeans is the integration. Eclipse looks more like a gnome app than Netbeans, even the fonts look different..this has quite a strong effect on me. Perhaps I'll try it again and see what I'm missing :D

---

### Post by bruce89 on 2008-03-26
> **Lord Illidan said:**
> What I don't like about Netbeans is the integration. Eclipse looks more like a gnome app than Netbeans, even the fonts look different..this has quite a strong effect on me. Perhaps I'll try it again and see what I'm missing :D

Sun don't like SWT, even though it looks nicer.

---

### Post by malfist on 2008-03-26
> **CptPicard said:**
> Just took a quick look at the JCreator website...



Funny how one needs to advertise an IDE for some language *not* being written in that particular language, because it would make the end result be slow and inefficient :)

@OP, Eclipse and Netbeans are your choices, both are good. I tend to be partial towards Netbeans.

Wait a second, how many people have used Bloodshed Dev-C++? Any of the bloodshed line? That's all in Delphi, not in the IDE's language.

---

### Post by LaRoza on 2008-03-26
> **malfist said:**
> Wait a second, how many people have used Bloodshed Dev-C++? Any of the bloodshed line? That's all in Delphi, not in the IDE's language.

That is Windows specific, and uses gcc for compiling which is in C. (the Windows port).

CptPicard just thought the statement was humourous.

---

### Post by jespdj on 2008-03-27
> **CptPicard said:**
> And its plugins never work. At least that is my experience. With Eclipse you're constantly fighting the setup, having to reinstall all the time from scratch, getting NullPointerExceptions and other mystical errors thrown at you while you're trying to work...
You must be using some ugly, buggy plugins then.

I'm using Eclipse every day at work with the Java EE and WTP (Web Tools Platform) plugins, and a third-party plugin for Subversion ([Subclipse](http://subclipse.tigris.org/)). I never have to "fight the setup", reinstall from scratch, or get NPEs or other mystical errors. You're not trying to run Eclipse on crappy GNU gcj / gij, are you? If you are, then install Sun Java 6.

Eclipse works great, it's the most popular IDE for Java, and not without reason.

---

### Post by Lord Illidan on 2008-03-27
Yes, the gcj version is..to put it plainly, slow and useless, I only use Sun Java's implementation.

---

### Post by bruce89 on 2008-03-27
> **jespdj said:**
> You're not trying to run Eclipse on crappy GNU gcj / gij, are you? If you are, then install Sun Java 6.

Even better, install *icedtea-java7-jre* or *openjdk-java6-jre* depending on your use of Gutsy or Hardy (in that order). You get a nice properly free JRE which isn't bad.

---

### Post by perito on 2008-03-27
I use Eclipse everyday and its great

---

### Post by The Cog on 2008-03-27
I don't know how big an IDE you are looking for. You might find geany useful if you are only looking for a fast and lightweight solution. It's in the repositories.

---

### Post by Lord Illidan on 2008-03-27
+1 for Geany!

---

### Post by t.s on 2008-03-28
+1 for geany..

use anjuta before, but now they don't support compiling for just one file anymore.

so, cheer for geany!

---

### Post by jespdj on 2008-03-28
+1 for Geany :KS Geany is a very nice, lightweight and easy to use editor / IDE.

---

### Post by JeffS on 2008-04-10
For Eclipse, use the one you can download from the Eclipse website (v3.3 - the Ubuntu repo still has 3.2), and most definitely use the regular Sun JRE/SDK (preferably v6), not gcj or icedtea.  The latter two are full oss, true, but not complete, robust implementations at this stage.

Also, consider using one of the EasyEclipse distributions.  They have distributions tailored to particular development domains (web, desktop,rcp,mobile, etc), with the pertinent plugins pre-installed and configured.  I'm currently using the EasyEclipse Desktop Java distribution, and it rocks for both SWT and Swing development, and for a form designer, and for distributing an executable JAR.

Also, NetBeans is awesome.  It has tons of great out of the box functionality, and has a rich set of plugins (installable within it's plugin manager, just a few clicks) that "just work".  For Swing apps, the Matisse GUI designer can't be beat.

Again for NetBeans, I would go with the download from the NB website, not the one in the Ubuntu repo (which requires a separate download anyway, so what's the point?), because you'll get a more up to date version, and the installer works flawlessly with Ubuntu.

Finally, I'll chime in with Geany being a great lightweight alternative (albeit far less powerful).  I love Geany - fast and easy.

---

