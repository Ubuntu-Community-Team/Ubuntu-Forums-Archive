---
title: "How do I hook copy operations in Gnome/Kde/etc?"
date: 2007-10-01
forum: Programming Talk
---

### Post by burito on 2007-10-01
I've made what atm I'm calling pyAdvancedCopy, which is a blatant clone of the very cool SuperCopier2, done in pygtk, its 90% complete. (plan is to rewrite it in C when its done)

How do I hook the copy operation in nautilus/kde/etc?

For those not familiar with SuperCopier2, its basically a program, that copies files for you, nothing impressive yet, but it maintains its list, which you can save/restore/edit, it gives you the speed, and most importantly, it NEVER fails and quits. In the event of failure, it pauses, and asks you what to do. So if your drive is full, it pauses, so you can free up space, then you hit resume, and you no longer have to redo the 90% of that 4Gb iso you were copying. It's primarily useful to me on windows because it allows resuming from SMB shares, but it has saved me much time using it in general HDD to HDD copying, and its speed indicator gives a very good idea of disk fragmentation. Oh and its GPL2. But its written in Delphi. Many of my friends use this tool in windows, and a few have said "we need SuperCopier for ubuntu", so I figured what better way to learn python, 5 days later here I am.

---

### Post by gebeleizis on 2007-10-02
Man, SuperCopier is one of the programs that I miss from windows.
I love it and I sure will love your pyAdvancedCopy.
Unfortunately I can't help u with programming stuff, but I hope some of the guys so I can put my hands on pyAC.

---

### Post by burito on 2007-10-04
It's good to hear your enthusiasm :-)

Although I've got a bad feeling I'm going to have to earn the insides of nautilus and add the hooking myself :-(

---

### Post by gebeleizis on 2007-11-08
R U there yet? I would love to play with it.

---

### Post by Awalton on 2007-11-08
I'm not sure of what you mean by "hooking". Most file operations inside of Nautilus in its current incarnation are done via gnome_vfs_xfr(), which moves file operations out of Nautilus's territory and into GNOME VFS's territory. The VFS then takes care of the file operation.

What it sounds like is going on, is that SuperCopier is just adding another layer of atomicity on top of those operations, it makes a lot of smaller operations out of one large operation (for example, moving a directory containing a thousand files and turning it into a "create folder", "move file" x 1000, and "delete folder" operations). This would mean that either it's making its own VFS layer within its code (tedious work), or that it's simply breaking up one large VFS move into a lot of smaller operations as noted above.

Right now, that's all sorted out inside of GNOME VFS and isn't "hookable" (basically, you can watch the operation as it happens and cancel it, but as far as I'm aware you can't pause it or change the atomicity of the operation).

What you would need to change is the way that Nautilus transacts those file operations; you would need to make atomic those operations at Nautilus's level, for example. There is some similar work going on that would help you to understand this kind of thing being done by Amos Brocco (there's some work on a global file undo/redo for Nautilus, for example), and that's located here: 
[1] [http://bugzilla.gnome.org/show_bug.cgi?id=167501](http://bugzilla.gnome.org/show_bug.cgi?id=167501)
[2] [http://diuf.unifr.ch/pai/people/broccoa/dev/01_nautilus-undo-initial.patch](http://diuf.unifr.ch/pai/people/broccoa/dev/01_nautilus-undo-initial.patch)

Also, you should know that Nautilus is moving to a new Virtual File System layer that's much easier to understand and write code for, called GIO/GVFS. It's very new, and it's only had one release so far, but by GNOME 2.22 it should be default for at least Nautilus and GEdit, and maybe a few more applications here and there. Breaking up those move operations should be a whole lot easier to understand once you read through the API, the relevant portions being located in gfile.[c/h]. I'm currently helping to document this code (and all of GIO/GVFS eventually).

For GIO/GVFS development outlooks, see: [http://live.gnome.org/GioToDo](http://live.gnome.org/GioToDo)
For GIO itself: [http://svn.gnome.org/viewvc/gio-standalone/trunk/](http://svn.gnome.org/viewvc/gio-standalone/trunk/)

And be sure to snoop around Nautilus's SVN repository too, specifically the GIO branch which is where development is currently underway with moving all of Nautilus over to GIO.

Have fun!

---

### Post by Adrian.C on 2007-11-14
Hi

For the ones interested in a SuperCopier-like for Ubuntu, I created a small Java program. For now it is just a Beta, but you can put transfers in queue, pause a copy, manage the queue of remaining transfers, resume a transfer which has failed (without starting from the beginning). 

I didn't try to "hook copy operations". Even if it was possible, it would be hard to do so for Nautilus, Konqueror, Thunar...

So I used drag'n'drop operations. It works pretty well with Gnome,KDE, XFCE.

For more informations, you can visit the project homepage : (beta 0.1 available for download)
=> [MiniCopier Homepage]("http://a.courreges.free.fr/projets/minicopier/minicopier-en.php") <=

It would be nice if you could give some feedbacks about it. (I already got some good ones from the French forums.)

If you want to test, don't forget :
[LIST=1]
[*]you need Java JRE 5.0 minimum (sudo apt-get install sun-java5-jre)
[*]you must turn OFF Beryl/Compiz.
[/LIST]

---

### Post by godinblack on 2008-04-10
I was offline of this forum for a lot of time and didn't see this thread, that's way I reply now.
A friend of mine and I are developing an application [CopyManager]("http://proyectos.softwarelibre.cu/copymanager/") that fits with the requirements all you are talking here. I invite you all to step by the site and check it out. It is in a very unstable form right now but we're working on it.

---

