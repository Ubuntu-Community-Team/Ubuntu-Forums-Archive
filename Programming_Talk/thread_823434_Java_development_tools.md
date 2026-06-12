---
title: "Java development tools"
date: 2008-06-09
forum: Programming Talk
---

### Post by Despot Despondency on 2008-06-09
Hey. I'm programming with java and I'm looking for a tool to help me with the development of a GUI. My GUI is going to have 40+ buttons and so it would be really helpful if there was a tool that allows me to position the buttons on the screen directly, rather than having to code the position of each button. Is there anything like this available on ubuntu? I'm using eclipse at the moment, so is eclipse has this functionality that would be excellent

---

### Post by CptPicard on 2008-06-09
Netbeans has an excellent GUI builder, and Eclipse has its Visual Editor plugin too...

---

### Post by CameO73 on 2008-06-09
To be honest the Visual Editor plugin is not all that great (at least when I tried it, about a year ago); I do love Eclipse, though.

I've heard great things about the Netbeans editor (Matisse), but I generally don't like the idea of generated (UI) code. The biggest problem is that you can't touch that code ... ever! 

My solution for complicated UI layouts would be to use the [MiG Layout](http://www.miglayout.com/). It's a small JAR, has great documentation and is IMO the best way to (programmatically) create a UI.

---

### Post by lixx on 2008-06-09
> **Despot Despondency said:**
> Hey. I'm programming with java and I'm looking for a tool to help me with the development of a GUI. My GUI is going to have 40+ buttons and so it would be really helpful if there was a tool that allows me to position the buttons on the screen directly, rather than having to code the position of each button. Is there anything like this available on ubuntu? I'm using eclipse at the moment, so is eclipse has this functionality that would be excellent

A "non-free" alternative is to use JFormDesigner. IMHO despite its cost, it is one of the best Swing builders out there. Btw, I never bought it, I just used the evaluation build. But it suits my need. ;)

---

### Post by Despot Despondency on 2008-06-09
Thanks for your suggestions, I'll have a look into them. Is the eclipse visual editor part of the standard eclipse package or do I have to install additional packages. Don't seem to be able to find it with synaptic.

---

### Post by CameO73 on 2008-06-09
No it's not part of the standard Eclipse package. It can be installed separately from [http://www.eclipse.org/vep/WebContent/main.php](http://www.eclipse.org/vep/WebContent/main.php)

Btw, the Eclipse packages in the Ubuntu repository are not very up-to-date. If you want to try the latest, get it from [http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/) (if you're patient, you can wait for the 3.4 release -- that's a real improvement over 3.2!)

If you download Eclipse and put it in a folder you can write to (e.g. your home directory) it will store all configurations in that same folder. The Eclipse version that is installed by Synaptic stores its configuration in ~/.eclipse

So two different Eclipses are normally not a problem (but to be honest, I've been fighting with multiple Eclipse installations a couple of times).

---

### Post by jespdj on 2008-06-09
I like Eclipse, it's the IDE that I use for my job every day.

But frankly, the GUI builder in Netbeans is way better than the Visual Editor in Eclipse. Unfortunately, the VE project seems to have been dead for a long time. It's probably not worth it to look at it for a very long time. I'd try Netbeans if I'd had to build a Swing GUI app.

---

### Post by xlinuks on 2008-06-09
In your case there's no better *free* tool that does visual GUI than NetBeans, but, the one from the ubuntu repositories is old (6.0.1), it's a lot better to download the latest version from Sun:
[http://download.netbeans.org/netbeans/6.1/final/](http://download.netbeans.org/netbeans/6.1/final/)
It's only 31MB (includes the visual editor).

---

### Post by Despot Despondency on 2008-06-10
Thanks for your replies everyone. Think I'll give NetBeans a try as it seems to have the best reviews. Thanks for the heads up on the repository versions, didn't realize they were old. 

Think I'll give the MiG layout manager a try too. I've downloaded the JAR file form the website CameO73 recommended, and imported it into an eclipse project with properties -> Java Build Path -> Libraries -> Add external JARs. However, I don't know how to import it into a class where I want to use it? Sorry, I've never used external JAR files before.

---

### Post by CameO73 on 2008-06-10
A JAR works exactly like the local source code. It's nothing more than a zip with all the compiled classes. This means you import the package as you always do (Eclipse can help you here).

From the example on [The MiG Layout website]("http://www.miglayout.com/") (in the 'Getting started'-section):

```

JPanel panel = new JPanel(new MigLayout());

panel.add(firstNameLabel);
panel.add(firstNameTextField);
panel.add(lastNameLabel,       "gap unrelated");
panel.add(lastNameTextField,   "wrap");
panel.add(addressLabel);
panel.add(addressTextField,    "span, grow");

```You'll probably get an error on the 'new MigLayout()' part. Just press Ctrl-Shift-O (or Source -> Organize Imports) and Eclipse will try to find MigLayout for you. If you have the JAR on your build path this will be no problem. You can then see in your import section that MigLayout is imported (the same as local code).

Be sure to check out the documentation (on the website, section 'MiGLayout Downloads') ... you may want to start with the [QuickStart]("http://www.miglayout.com/QuickStart.pdf").

---

### Post by Lau_of_DK on 2008-06-10
> **CameO73 said:**
> 

I've heard great things about the Netbeans editor (Matisse), but I generally don't like the idea of generated (UI) code. The biggest problem is that you can't touch that code ... ever! 


Matisse is a good editor that in many ways is better than anything Eclipse has to offer. You can "touch", modify and mangle the code anyway you like, there's no hidden magic.

/Lau

---

### Post by Despot Despondency on 2008-06-10
Hey, thanks CameO73, I've imported into my class now so I can play around with it and see how I like it. Still going to give NetBeans a try though. Cheers everyone. :)

---

### Post by CameO73 on 2008-06-10
Oh, don't forget to include the JARs you use (in Eclipse) with your application. You can read more about JARs [here](http://java.sun.com/developer/Books/javaprogramming/JAR/index.html) if you like.

---

### Post by dtmilano on 2008-06-10
You may find these [tutorials]("http://www.netbeans.org/kb/trails/matisse.html") very helpful to understand GUI building.
Hint: pay special attention to *Swing Application Framework*.

---

### Post by MacUntu on 2008-06-12
I use Jigloo with Eclipse: [http://www.cloudgarden.com/jigloo/](http://www.cloudgarden.com/jigloo/)

Add "http://cloudgarden1.com/update-site" to the update manager to get it.

---

