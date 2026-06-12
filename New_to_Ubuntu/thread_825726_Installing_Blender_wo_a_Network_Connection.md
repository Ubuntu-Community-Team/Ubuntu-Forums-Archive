---
title: "Installing Blender w/o a Network Connection"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by TSRep13 on 2008-06-11
This is kind of more for my friend, but since I couldn't figure it out, I figured I could learn from this experience too.

My friend received some old computers from a school and has installed xubuntu on them.  On the one that he is mainly going to use, he wanted to install some graphics manipulation software like Blender.  The downside is that he cannot connect these computers to a network (at least at this time).

He has downloaded the downloaded the tar.bz2 file straight from the Blender website and then burned it to a CD.  We can copy the file to Xubuntu and even extract it, but we just can't figure out how to get it to work.

He only has installed things through the package manager, I personally like using the terminal.  My problem is all of this is that I am very new to Linux and am just learning how to do some basic things in the terminal.

Here is what I have tried:
1.  There is no ./configure file
2.  It basically tells us that ```
sudo make install /DIRECTORY
``` is useless (there is nothing to make and install just doesn't seem to do anything
3.  We even tried running the blender executable file from the extracted folder, but it didn't do anything.

So here are my questions regarding this problem:

1.  Does anyone know how my friend can get a working copy of Blender on a network deprived Xubuntu driven computer?
2.  For future reference, what is the best way to manually install a compressed file from the terminal?
3.  Why Blender?  Why not Toaster or Food Processor?
4.  Where is a good place to get the basic Linux commands for the terminal (I fully realize that nothing is just as simple as "basic commands" but I'm hoping for a pretty concise list just to start playing with)?

Thanks for your help

---

### Post by decoherence on 2008-06-11
Can you use another computer to get the .deb from the archive and copy it to a USB drive?

[http://archive.ubuntu.com/ubuntu/pool/universe/b/blender/](http://archive.ubuntu.com/ubuntu/pool/universe/b/blender/)

The one you want is probably the 2nd last one in the list, blender_2.45-5ubuntu1_i386.deb

You may have to get dependancies this way as well.

---

### Post by TSRep13 on 2008-06-11
Sweet!  But that brings up two more questions then.  Where would be find .deb files and what do we do with them once we have them?  Sorry, it might seem like we need someone to hold our hands, but neither of us know much about the file systems used in (X)Ubuntu :-\

---

### Post by durand on 2008-06-11
There's an easier way: [http://nonetdebs.unixpod.com/](http://nonetdebs.unixpod.com/)

EDIT: and a forum link: [http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

---

### Post by TSRep13 on 2008-06-11
Wow, that is awesome.  I had to call my buddy right away and give him that URL, that is exactly what he needs!

---

### Post by durand on 2008-06-11
Yay! [IMG]http://www.durand.zephyrhosting.net/dump/smileys/smile-big.png[/IMG] Let me know if it works.

PS: Ubuntu forums should support more smileys >_>

---

