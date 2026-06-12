---
title: "help me with ubuntu"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by thantserpelis on 2008-10-13
i have installed ubuntu 8.04 with wubi program
and i have some problems
1)when it is going on the login screen i don't have the original login screen i have something like the old windows boot screen
2)when i am going to shut it down there is nowhere the button sht down or restart
3)when i am doing log out it gives me a screen this screen below
[img]http://img406.imageshack.us/img406/7791/dsc00051ej3.jpg[/img]

about the first program this is the pic of the login screen
[img]http://img98.imageshack.us/img98/3421/dsc00049hi3.jpg[/img]
and about the second:
[img]http://img504.imageshack.us/img504/885/dsc00050xm5.jpg[/img]

please somebody help me!

---

### Post by ibizatunes on 2008-10-13
have you done a memery check on your computer to see if you have faulty hardware?
have you check the CD for defects?

---

### Post by thantserpelis on 2008-10-13
yeah it is working fine and i started ubuntu 2 times and it was working normally but at the third time it became like this u saw

---

### Post by NewJack on 2008-10-13
First, if you don't know how to do so, visit this page to find out how to check hash files:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Then, make sure that the Ubuntu file you downloaded has the correct hash, listed here for your download:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Also, what speed did you burn your Ubuntu image?  General feeling is, the slower the better.  I usually burn at 4x or 8x, others will suggest 1x.  I haven't had any problems burning at 4x or 8x.

Hope this helps!

Joe

---

### Post by thantserpelis on 2008-10-13
hey newjack it seems that u didn't read the up part of the thread
i told that i installed them with wubi

---

### Post by NewJack on 2008-10-13
Whoops, sorry bout that.  I am at work and was flipping through your post before the boss decided to pass my way.  :lolflag:

---

### Post by thantserpelis on 2008-10-14
so is anyone here who can help me ?

---

### Post by ByteJuggler on 2008-10-14
It looks like somehow something has become corrupted (quite hard to guess what might be happening really) - anyway, seeing as you already installed a couple of times, I'd suggest uninstalling again and reinstalling again.  Sorry for not being able to be more specific.

---

### Post by hyper_ch on 2008-10-14
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

---

### Post by redseventyseven on 2008-10-14
> **thantserpelis said:**
> i have installed ubuntu 8.04 with wubi program
and i have some problems
1)when it is going on the login screen i don't have the original login screen i have something like the old windows boot screen
2)when i am going to shut it down there is nowhere the button sht down or restart
3)when i am doing log out it gives me a screen this screen below
*img*

about the first program this is the pic of the login screen
*img*
and about the second:
*img*

please somebody help me!

I can help with the first problem - maybe it'll help you solve the rest.

The login screen you show in your picture is the KDE default login screen (don't worry, it's nothing to do with MS Windows). KDE is a graphical desktop environment for Linux - the default for several popular Linux distributions in fact - but it is not the default in Ubuntu. The default for Ubuntu is called GNOME.

Edit: The login screen is called "KDM" which is short for "KDE Desktop Manager". Not quite sure how it got there, but that's what it is.

Somewhere along the line I would suggest you may have installed some KDE elements when you were installing packages.

I would echo the suggestion that you re-install and start again - be prepared to do several re-installs when you're first starting out. Re-installing Ubuntu (or any Linux distribution) is a much less painful and time-consuming process than a Windows re-install, and it helps you to understand what you're doing a bit better.

Once you've reinstalled - slow down! Don't rush into installing lots of packages that you don't quite understand. Try to work out exactly what you need and get that sorted out first. If something goes wrong, try to make a mental (or written) note of what you were doing immediately before it went wrong. That'll definitely help the community to help you.

Edit: I removed the enormous pictures as they were unnecessarily large. Screenshots are generally a good idea - definitely helps to see what the problem is - but please try to reduce their size to something that fits on our monitors!

---

