---
title: "Pathetic Netbeans"
date: 2008-06-18
forum: Programming Talk
---

### Post by bijeeshvs on 2008-06-18
hi guys i just installed the netbeans ide for linux and was surprised to see it extracted some .exe files to my system, and the whole thing is taking a lot of memory (i installed it coz i want code in java ) and slow so whats your experiance with netbeans and which ide do you prefer for java.
i am not a master in java so i prefer an IDE, please share your opinion.....................................

---

### Post by Brinstar on 2008-06-18
have you tried [eclipse]("http://www.eclipse.org")?

---

### Post by Can+~ on 2008-06-18
As brinstar already mentioned: use Eclipse. It's also available in synaptic, so don't do that typical mistake of downloading it from the page, when you can just do:

```
sudo aptitude install eclipse
```

---

### Post by LaRoza on 2008-06-18
The sticky has a link to the IDE threads.

---

### Post by bijeeshvs on 2008-06-18
hi guys thank you for your comments i will try eclipse................

---

### Post by xlinuks on 2008-06-18
First off I hope you installed the version from the web, not from the repos.
Secondly, eclipse uses SWT, and unless otherwise specified, you'll use the "non-standard" SWT libraries, which besides being buggy and less extensible, are becoming irrelevant especially with the upcoming Java update 10 release.
It is slow, but, it supports Java better than eclipse for a lot of reasons, including visual GUI editor and so on.
If you're doing basic stuff jEdit would be ideal for you I guess, I used it in the past.

---

### Post by xlinuks on 2008-06-18
sent 2 times, connection troubles.

---

### Post by farrell2k on 2008-06-18
Yep, netbeans usually consumes about 100-150mb on me.  It's definitely not memory friendly, but I have plenty of ram, and I've become used to it.

---

### Post by Lau_of_DK on 2008-06-18
> **bijeeshvs said:**
> hi guys i just installed the netbeans ide for linux and was surprised to see it extracted some .exe files to my system, and the whole thing is taking a lot of memory (i installed it coz i want code in java ) and slow so whats your experiance with netbeans and which ide do you prefer for java.
i am not a master in java so i prefer an IDE, please share your opinion.....................................

I think you'll be happy if you stick with Netbeans. Make sure you've got everything set up right, including Swap disks and anything relating to memory.

/Lau

---

### Post by ZylGadis on 2008-06-18
If you are not a master in Java, you should avoid IDEs. Use a simple text editor, perhaps with keyword highlighting. Otherwise you'll learn the IDE, not Java. IDEs are useful because they automate repetitive tasks experienced programmers perform, but if you don't know how to do the task without the IDE, you'll start depending on it, which is bad.

---

### Post by Lau_of_DK on 2008-06-19
> **ZylGadis said:**
> If you are not a master in Java, you should avoid IDEs. Use a simple text editor, perhaps with keyword highlighting. Otherwise you'll learn the IDE, not Java. IDEs are useful because they automate repetitive tasks experienced programmers perform, but if you don't know how to do the task without the IDE, you'll start depending on it, which is bad.

Im not 100% sure, but I think that was the worst advice Ive heard all year :)

/Lau

---

### Post by LaRoza on 2008-06-19
> **Lau_of_DK said:**
> Im not 100% sure, but I think that was the worst advice Ive heard all year :)

/Lau

No, I think it is good advise. For first learning Java, writing all the code yourself with basic syntax highlighing is a good thing.

Java of course, demands more tools when actually using it, but for a first taste of Java, pure code is best.

---

### Post by pmasiar on 2008-06-19
> **ZylGadis said:**
> If you are not a master in Java, you should avoid IDEs. Use a simple text editor, perhaps with keyword highlighting. Otherwise you'll learn the IDE, not Java. IDEs are useful because they automate repetitive tasks experienced programmers perform, but if you don't know how to do the task without the IDE, you'll start depending on it, which is bad.

I disagree, and agree more with Lau_of_DK.

IMH (and non-java-expert) O, Java is not a language what can be wrestled with without a help of IDE. Too wast, too rich libraries, too many idiosyncrasies. I happily paid $50 for myEclipse plugin to Eclipse to help me around creating Struts apps. 

Yes I know I am IDE-dependent, but I do not care about learning Java - all what I care about is finishing my job in shortest time possible. This is different from hacking for fun: this is about producing program as product.

And this is why I hate Java: I need complicated (and expensive) IDE to be 10% as productive as I can be in Python with plain editor.

So I would never picked Java if I could avoid it, but if I have to use Java, I want to use any fair and unfair advantage from any IDE I can get.

---

### Post by LaRoza on 2008-06-19
> **pmasiar said:**
> I disagree, and agree more with Lau_of_DK.

IMH (and non-java-expert) O, Java is not a language what can be wrestled with without a help of IDE. 

Yes I know I am IDE-dependent, but I do not care about learning Java - all what I care about is finishing my job in shortest time possible.


But for learning it, don't you think the first taste should be without extra help? Even if it means using the basic libraries and having a reference, I think doing the first coding in Java without extra help would be more beneficial, at least until the rules of Java and the compiling/run process is understood.

---

### Post by dtmilano on 2008-06-19
"I make it a rule not to clutter my mind with simple information that I can find in a book (or in IDE's code completion) in five minutes (1 microsecond)."
Albert Einstein

So, don't waste your time, use an IDE an concentrate on learning how to design and program well.

---

### Post by LaRoza on 2008-06-19
> **dtmilano said:**
> "I make it a rule not to clutter my mind with simple information that I can find in a book (or in IDE's code completion) in five minutes (1 microsecond)."
Albert Einstein

So, don't waste your time, use an IDE an concentrate on learning how to design and program well.

His advise is about memorizing tables (especially the Periodic Table), not knowing the basics.

Memorizing libraries is usually a waste of time, you'll end up knowing what you use most often, and for the rest you know where to look, but for not knowing the basics of the language, or how to really compile, letting that be automated is a bad idea. 

Many people say IDE's make things easier, yet this forum is loaded with problems with IDE's. Such problems are almost impossible to diagnose because you don't know what the IDE is doing.

---

### Post by RIchard James13 on 2008-06-20
I'm with Lau_of_DK too. I think the whole concept that people learn only the IDE is complete rubbish. How many IDE's can automate the entire programming process such that a user does not need to learn how to code?

On the contrary when I learnt Java last term I found eclipse very good along with Suns Java [Documentation]("http://java.sun.com/javase/6/docs/api/") on the website. It makes it easier to understand Java than Visual Studio does Visual BASIC.

---

### Post by Lau_of_DK on 2008-06-20
> **LaRoza said:**
> His advise is about memorizing tables (especially the Periodic Table), not knowing the basics.

Memorizing libraries is usually a waste of time, you'll end up knowing what you use most often, and for the rest you know where to look, but for not knowing the basics of the language, or how to really compile, letting that be automated is a bad idea. 

Many people say IDE's make things easier, yet this forum is loaded with problems with IDE's. Such problems are almost impossible to diagnose because you don't know what the IDE is doing.

LaRoza, dont take this the wrong way, because its not meant in the usual arrogant fashion: How much have you worked with Java / IDEs?

Before switching to Linux and Emacs I spent 100% of my programming time in Visual Studio and based on that experience I think that 99% of your views on IDEs is based on poor knowledge of them and an overly glamorized view of notepad. If Im wrong Im wrong, but if Im right - Youve got some things to think through :)

/Lau

---

### Post by LaRoza on 2008-06-20
> **Lau_of_DK said:**
> LaRoza, dont take this the wrong way, because its not meant in the usual arrogant fashion: How much have you worked with Java / IDEs?

Before switching to Linux and Emacs I spent 100% of my programming time in Visual Studio and based on that experience I think that 99% of your views on IDEs is based on poor knowledge of them and an overly glamorized view of notepad. If Im wrong Im wrong, but if Im right - Youve got some things to think through :)


How much? Well, I have never felt the need to whip up a Java program (as if anyone ever does...).

When I learned it, I used Crimson Editor (I was using Windows at the time) and the terminal to compile and run.

My statement about not using an IDE was purely for learning it. The most someone does when learning is a "javac Main.java" and a "java Main" or whatever, nothing fancy.

I think your views on IDE's is based on your 99% use of them and your lack of experience with other tools.

I have used IDE's before, and found them to be very rigid. I used editors customized to suit me (Gedit, Crimson Editor and Vim) and am more productive in them.

---

### Post by StOoZ on 2008-06-20
I tried both eclipse & netbeans , and I prefer netbeans... you should give it some more time to get used to.

---

### Post by doorman on 2008-06-20
Another vote for NetBeans!

Plus, check out all the plugins on the [netbeans]("http://www.netbeans.org") site!

---

### Post by jonterje on 2008-06-20
> **bijeeshvs said:**
>  ... so whats your experiance with netbeans and which ide do you prefer for java ... 

I've used the NetBeans GUI-designer (drag-n-drop) plenty of times for quick design prototyping, which works great; it's fast and easy. (At least at the default layout manager setting (GroupLayout), I don't know about the other layout managers for drag-n-drop, I think they would pretty much break the whole argument.)

The problem is further development, because the auto-generated source is put within one large code block. Editing the source in this block will either break further editing with the GUI-designer or the changes made will be overwritten by the GUI-designer the next time you switch into design-mode. (I think it's the latter, can't remember)

Well, it's a problem for _me_ anyways, as I think the code generated is pretty messy (especially with GroupLayout). Maybe this can be configured, but either way it takes away control of the GUI-code _if_ you want to be able to still edit the GUI in design-mode. If you don't care about how the code looks, then the NetBeans GUI-designer is much better than any other GUI-designer I've tried.

That's about as far as my experience with NetBeans goes, and because of that limited knowledge I can't tell you whether or not if it's good or bad save for the above reasons. 

What I can tell you is that my Java IDE of choice is Eclipse. Lots of plugins and support for, not only Java development, a lot of other languages too, and as mentioned earlier; automates a lot of common repeated tasks.

As for whether or not you should use an IDE at all;
> **pmasiar said:**
>  ... Yes I know I am IDE-dependent, but I do not care about learning Java - all what I care about is finishing my job in shortest time possible ...

> **LaRoza said:**
> ... I think doing the first coding in Java without extra help would be more beneficial, at least until the rules of Java and the compiling/run process is understood...

I completely agree with the points mentioned from both sides. It's important to know at least the very basics (especially at hand-written programming exams O_o) but I would recommend finding and learning an IDE as quick as possible, I think I've actually learned a lot more Java by using one.

---

### Post by farrell2k on 2008-06-20
As a newbie one month into java, I definitely recommend that once you learn that you NEED *public static void main(String[]args)* in your main class, do yourself a favor and use an ide that auto-corrects errors and offers suggestions, like NetBeans.   You still need to do 99% of the work, and you also have the ide constantly showing you what you do wrong, and sometimes even offering to fix it.   I have learned quite a bit from that.

---

### Post by achelis on 2008-06-21
Starting off without an IDE is a good idea IMO. It forces you to learn the basics of the language - compiling, syntax, semantics et.c. 

Once you've got the basics down you can switch to an IDE which will speed up your work by automating repetitive tasks and organize projects.

I never got around to try Netbeans - I will one day though - but eclipse is a great IDE which will safe you a lot of typing.

---

### Post by Rhaddad on 2008-06-21
> **bijeeshvs said:**
> hi guys i just installed the netbeans ide for linux and was surprised to see it extracted some .exe files to my system, and the whole thing is taking a lot of memory (i installed it coz i want code in java ) and slow so whats your experiance with netbeans and which ide do you prefer for java.
i am not a master in java so i prefer an IDE, please share your opinion.....................................

Nah Don't get eclipse stick with NetBeans. Just get the installer version from the website, the repos are screwed.....and yea don't get eclipse.....NetBeans is so much better.

---

