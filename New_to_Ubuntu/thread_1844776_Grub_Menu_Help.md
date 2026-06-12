---
title: "Grub Menu Help"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by MCorolla on 2011-09-15
Hello, I am new here so I'm sorry if I made a mistake in where to post this thread of if I'm posting a thread that already exists... I didn't find one on this topic. 

Anyway, I am wondering if anyone can tell me if it is possible to get the grub menu to automatically load windows with as little pause as possible while still maintaining the ability to load Ubuntu whenever I want to.

---

### Post by MG&amp;TL on 2011-09-15
This can be done, but it will require some system editing, so if you have anything important, back it up first.

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

Instructions to do this kind of thing here.

---

### Post by drs305 on 2011-09-15
Welcome to the Ubuntu forums.

Yes, you can do that.

I would recommend you install Grub Customizer, a great GUI app that will allow you to tweak the Ubuntu settings without manually editing the Grub 2 configuration files.

I have a guide on using GC, see the "Customizer" link in my signature line.

You would want to change the default OS setting. I would recommend you keep a timeout value of 2-3 seconds at least (10 is the default) so you will have time to select Ubuntu when desired.

If you want to see what's happening under the hood, you can click the "Tasks" link in my signature, which describes how to manually edit the files.

---

### Post by drs305 on 2011-09-15
MCorolla,

Welcome to the Ubuntu forums.  ):P

Yes, you can do that.

I would recommend you install Grub Customizer, a great GUI app that will allow you to tweak the Ubuntu settings without manually editing the Grub 2 configuration files.

I have a guide on using GC, see the "Customizer" link in my signature line.

You would want to change the default OS setting. I would recommend you keep a timeout value of 2-3 seconds at least (10 is the default) so you will have time to select Ubuntu when desired.

If you want to see what's happening under the hood, you can click the "Tasks" link in my signature, which describes how to manually edit the files.

---

### Post by MG&amp;TL on 2011-09-15
+1 for Grub customizer.

Download from here:

[https://launchpad.net/grub-customizer]("https://launchpad.net/grub-customizer")

Then decompress the directory, and in a terminal, follow the readme provided.

And welcome! ):P

---

### Post by anewguy on 2011-09-15
+1 for Grub Customizer - it makes things MUCH easier.

Dave ;)

---

### Post by MG&amp;TL on 2011-09-15
I liked it so much I'm developing a plugin for it. 
GC is really good. Use it. Change the fonts, the background image, whatever you fancy really.

---

### Post by MCorolla on 2011-09-17
Thank you everyone, you were all very helpful.

---

