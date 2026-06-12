---
title: "Seeking help compiling xfce from source.  Total compiling newbie!"
date: 2015-04-14
forum: New to Ubuntu
---

### Post by rcstck on 2015-04-14
So, I've been using Ubuntu for about 3 months.  I love it, though now I want to stretch out and try compiling something a bit more advanced!  I'd love to compile xfce 4.12 desktop environment.

I've looked over the instructions provided on the site, and my head is spinning!  I have no idea how to even start!  I'm dedicated to learning it now, but I feel a tad frustrated.  Is there anyone able to help with some questions, or point me in the direction of a detailed, newbie-friendly guide to compiling something like this?  Any help would be appreciated, as I feel totally hopeless (rightfully so!)

---

### Post by rcstck on 2015-04-14
Hi!

I'm trying to compile xfce, and one of the requirements is a "working GNU toolchain."  I've seen an explanation for what this is, but where do I go to get such a thing?  Any suggestions?

---

### Post by Geoffrey_Arndt on 2015-04-14
Do you have "build-essential" installed?  (found in Ubuntu Software Center).

---

### Post by steeldriver on 2015-04-14
Can you provide a link? AFAIK it generally doesn't mean anything more than gcc/g++, GNU make and the associated preprocessor, assembler, linker binaries. Unless you are cross-compiling, it's probably sufficient to install the build-essential metapackage.

---

### Post by lisati on 2015-04-15
Hi rcstck, and welcome to the forums. I've merged your two threads as they seem to be related.

There may be an option easier for you than compiling XFCE, e.g. installing the xubuntu desktop. Are you able to provide a link to the examples you have reading?

---

### Post by rcstck on 2015-04-15
Yes, I have build-essential installed.

---

### Post by rcstck on 2015-04-15
Thank you for the clean-up, I'm also a total forum newbie, imagine that.

Here is the link to the build instructions: [http://docs.xfce.org/xfce/building](http://docs.xfce.org/xfce/building)

Also, I have installed the Xubuntu desktop before on another machine.  While this is the easier route, I'm very interested in learning more about the compiling process

---

### Post by rcstck on 2015-04-15
Oh good, and thanks for the reply.  I do have build-essential installed.  Here is the build page: [http://docs.xfce.org/xfce/building](http://docs.xfce.org/xfce/building) 

Under the build requirements, the first item mentioned is the GNU toolchain.

---

### Post by Bucky Ball on 2015-04-15
> **lisati said:**
> Hi rcstck, and welcome to the forums. I've merged your two threads as they seem to be related.

There may be an option easier for you than compiling XFCE, e.g. installing the xubuntu desktop. Are you able to provide a link to the examples you have reading?

Better still, just install the desktop environment, xfce4, from the Software Centre, log out, choose 'xfce4 session' from the Sessions menu, login. Installing xubuntu-desktop is pretty much equivalent to installing xubuntu on top of your Ubuntu install. Messy. ;)

---

### Post by Elfy on 2015-04-15
Just making the point here that the thread is obviously about a learning experience, even more so that it's obvious the OP can install Xubuntu.

Thanks :)

---

### Post by steeldriver on 2015-04-15
If you want to try a baby step to make sure that you have the basic toolchain and gtk+ development packages in place, you could build the "Hello World in GTK" sample code from the Gnome developer site:

[https://developer.gnome.org/gtk-tutorial/2.90/c39.html](https://developer.gnome.org/gtk-tutorial/2.90/c39.html)

---

### Post by rcstck on 2015-04-15
thank you very much for the suggestion. :)  I have actually done this previously.   I had installed it this way on an older machine, and it's where I found that I liked xfce.  On this new laptop install, since I wanted to learn more about installing from source, I wanted to give installing it this way a shot. 

Part of the fun for me is getting a handle on this OS!  I've used "easy-mode" .exe files so much that I really want to take the training wheels off and give this compiling deal a go.

---

### Post by rcstck on 2015-04-15
hi!  Thanks for the input!  While installing Xubuntu has crossed my mind, and I may do that in the future, at the moment, I'm very much committed to this particular endeavour.  I want to learn how to do this :)

---

### Post by rcstck on 2015-04-15
Steeldriver!  My new friend!  Thank you very much for this!  I'm okay with baby-steps, gotta start somewhere!

---

