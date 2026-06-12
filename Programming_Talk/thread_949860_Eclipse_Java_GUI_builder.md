---
title: "Eclipse Java GUI builder"
date: 2008-10-16
forum: Programming Talk
---

### Post by tashe on 2008-10-16
I am learning to program graphicaly in Eclipse with Java, but unlike in Visual Studio I can't find a tool that enables you to easily drag-n-drop the components into the window.
A friend of mine mentioned to me about some kind of plugin that enables that, but he couldn't tell me the name. 
Does anyone know any way to do this in Eclipse?
I'm sure it will save me lots of time writing code.
Thanks in advance

---

### Post by jespdj on 2008-10-16
There's the Eclipse [Visual Editor](http://www.eclipse.org/vep/WebContent/main.php). You can install it via Eclipse's software update mechanism (Help / Software Updates).

Unfortunately, however, that project seems to be more or less dead. I don't know why the Eclipse foundation hasn't been giving it any attention the past two years.

[NetBeans](http://www.netbeans.org/) has a much better GUI builder called Matisse (you don't have to install it separately, it comes with the standard NetBeans installation).

I remember that someone ported Matisse to Eclipse, but I don't know if it's really usable.

There are other solutions for Eclipse, such as [WindowBuilder Pro](http://www.instantiations.com/windowbuilderpro/default.htm), but that's not free software (not open source, and it costs money).

---

### Post by tashe on 2008-10-16
thanks for the answer

I'm not familliar with NetBeans. Whats the difference between the two? Is it harder to learn than Eclipse and worth transferring to it?

---

### Post by tinny on 2008-10-17
> **tashe said:**
> thanks for the answer

I'm not familliar with NetBeans. Whats the difference between the two? Is it harder to learn than Eclipse and worth transferring to it?

NetBeans is a solid IDE that can do the same things for you that Eclipse can. IMO both are as easy / difficult to use as each other.

---

### Post by hoboy on 2008-10-17
check this link and search for what you need 

[http://www.eclipse-plugins.info/eclipse/plugins.jsp](http://www.eclipse-plugins.info/eclipse/plugins.jsp)

---

### Post by irrdev on 2008-10-17
A few months ago, I tried to get Eclipse's Visual Editor plugin working on my installation, but it took me nearly 4 hours to setup. The Visual Editor has been included in the Europa repository, but it requires newer dependencies which have to manually found and installed. If you *do* get the Visual Editor working, you'll find that it is about 10x slower than the GUI designer found in Visual Studio, and that the interface is terrible. I would hardly recommend the Visual Editor as an option. Netbeans is definitely is a better option, as its GUI editor is comparable to that of Visual Studio. Make sure you have at least 1GB of RAM, though; Netbeans can run insufferably slow from lack of memory. ;)

---

### Post by hoboy on 2008-10-17
> **irrdev said:**
> A few months ago, I tried to get Eclipse's Visual Editor plugin working on my installation, but it took me nearly 4 hours to setup. The Visual Editor has been included in the Europa repository, but it requires newer dependencies which have to manually found and installed. If you *do* get the Visual Editor working, you'll find that it is about 10x slower than the GUI designer found in Visual Studio, and that the interface is terrible. I would hardly recommend the Visual Editor as an option. Netbeans is definitely is a better option, as its GUI editor is comparable to that of Visual Studio. Make sure you have at least 1GB of RAM, though; Netbeans can run insufferably slow from lack of memory. ;)

I agreed definitelly with you.

---

### Post by shafi on 2008-10-17
> **tashe said:**
> I am learning to program graphicaly in Eclipse with Java, but unlike in Visual Studio I can't find a tool that enables you to easily drag-n-drop the components into the window.
A friend of mine mentioned to me about some kind of plugin that enables that, but he couldn't tell me the name. 
Does anyone know any way to do this in Eclipse?
I'm sure it will save me lots of time writing code.
Thanks in advance

Jigloo is a good GUI builder you can install it via eclipse if you type jigloo into your browser you will find the full description for the installation, if you want to learn how to start using jigloo you will also find the tutorial there , and ofcourse you can find a tutorial inside youtube, just search for jigloo then you will see a video regarding to that.

---

### Post by claudio_99 on 2008-11-09
If you want to draw GUI's in java I would certainly use Netbeans. It's a great IDE (the only reason I have eclipse installed if for it's perl plugin).

An other option is using Glade and the java-gnome bindings. However, in that case your application would be linux only.

C.

---

### Post by drubin on 2008-11-09
Learning to code with out a Visual Designer is a very NB must for all programmers. So you can maintain the code it generates.

I would vote on learning to program in [swing]("http://java.sun.com/docs/books/tutorial/uiswing/") before interacting with designers.

---

### Post by tinny on 2008-11-12
> **drubin said:**
> Learning to code with out a Visual Designer is a very NB must for all programmers. So you can maintain the code it generates.

I would vote on learning to program in [swing]("http://java.sun.com/docs/books/tutorial/uiswing/") before interacting with designers.

+1

I used to feel beaten up by Swing, now after some perseverance I find maintaining swing code to be just fine. 

Challenge yourself to learn Swing, you will be glad you did....

---

### Post by drubin on 2008-11-12
> **tinny said:**
> 
I used to feel beaten up by Swing, now after some perseverance I find maintaining swing code to be just fine. 

Challenge yourself to learn Swing, you will be glad you did....

I find it faster to write my own swing code then use the GUI managers now.

To add to tinny's point learn layout managers!! they are the reason I had GUI designers absolute positioning make maintaining a nightmare. :)

---

