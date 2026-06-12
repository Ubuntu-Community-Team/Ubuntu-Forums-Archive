---
title: "GNOME Eclipse?"
date: 2004-12-07
forum: Programming Talk
---

### Post by Hikaru79 on 2004-12-07
I remember reading somewhere about a version of Eclipse written for GNOME. I've got the normail *NIX one and it's slow as all heck (though I really love it's features). If there was a GNOME version that had similar usability but was natively written for GNOME, that would rule :D Anyone know?

---

### Post by dataw0lf on 2004-12-07
[ftp://download.eclipse.org/R-3.0.1-200409161125/eclipse-SDK-3.0.1-linux-gtk.zip](ftp://download.eclipse.org/R-3.0.1-200409161125/eclipse-SDK-3.0.1-linux-gtk.zip) 

The above is a download link for the Eclipse IDE built with GTK 2 bindings.  Take note that Eclipse is a JRE application, though.  It is still not truly 'native'.
dataw0lf

---

### Post by JeffS on 2004-12-10
My experience with Eclipse, as with other Java IDEs (including JBuilder), is that it's very slow and uses tons of memory.  Eclipse, like all the other Java IDEs, uses the JVM, and SWT.  However, with using GTK for the display, it might help at least a little bit.

---

### Post by Hikaru79 on 2004-12-10
It's definetly done it for me :) This version of Eclipse preforms MUCH better. w00t! Back to my favorite IDE ^ ^

---

### Post by ubuntu_demon on 2004-12-10
I've worked with eclipse.  I haven't tried the gnome-version.

Eclipse is a bit slow if you are using older hardware.

It's a nice environment if you are used to it. The GUI is sometimes a bit strange. If you're only writing a small application eclipse has no benefits above a simple editor.

The integrated CVS support is nice. They also got all kinds of plugins but I can't comment on those because I didn't need them and I haven't tried them.

I've worked on two school projects with eclipse. On the first one using CVS worked like a charm. On the second one CVS was giving all kinds of strange problems. At least part of the problems were the fault of the configuration of the CVS server.

One thing I don't like about eclipse is that you have to specify all kinds of file locations. If you import a project you have to manully get all those file locations right. (java,eclipse libraries,various project files,etc)

---

### Post by dataw0lf on 2004-12-14
> My experience with Eclipse, as with other Java IDEs (including JBuilder), is that it's very slow and uses tons of memory. Eclipse, like all the other Java IDEs, uses the JVM, and SWT. However, with using GTK for the display, it might help at least a little bit.
Try out jedit.  It's Eclipse-esque, with a good selection of plugins you can choose from, but extremely lightweight.  Personally, for the most part, I can't stand Java based apps , but jedit is pretty decent.  
dataw0lf

---

### Post by LinuxDev on 2004-12-15
Hi all,

I use this GTK Eclipse for c++ on Unbuntu and it's very good, much better than Eclipse on Windows XP :)
I've been using Kdevelop for a long time, but I prefer Eclipse, even if java GUI uses a lot of memory.

---

### Post by jwenting on 2004-12-16
[QUOTE=LinuxDev]Hi all,

I use this GTK Eclipse for c++ on Unbuntu and it's very good, much better than Eclipse on Windows XP :)
I've been using Kdevelop for a long time, but I prefer Eclipse, even if java GUI uses a lot of memory.[/QUOTE]
 SWT uses GTK (or other native display controls depending on your version) under the hood :)

Java being slow is a very old misconception. Java indeed used to be slow but it no longer is.
That's not to say you can't build slow applications in Java, just as you can in any language... But that's no fault of the platform as much as the person using it.

Java does tend to use quite a bit of memory as already stated, and if you have little memory available that will indeed hurt performance. But again that's no fault of the platform as is.

How in heck is Eclipse going to automagically get all your file locations for you? No editor does that unless it's so inflexible it doesn't allow you to use anything except its own defaults.

---

