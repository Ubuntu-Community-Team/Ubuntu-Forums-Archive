---
title: "Compile and make issues AAARRRGGHHH"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Amiduffer on 2008-08-13
Hi all.

I have a problem. I'm just figuring out how things work and need some direction.

I'm trying to install TVTime so as to be able to use my capture card (unless you can recomend a better capture program). So far, I've run the compile for it, and it tells me that I need ZLIB. So, I get the Zlib TAR.GZ file, unpack it, and compile, no problem, then I run MAKE, and I get this

-desktop:/usr/local/src/zlib-1.2.3$ make install
mkdir: cannot create directory `/usr/local/share/man/man3': Permission denied
make: [install] Error 1 (ignored)
cp zlib.h zconf.h /usr/local/include
cp: cannot create regular file `/usr/local/include/zlib.h': Permission denied
cp: cannot create regular file `/usr/local/include/zconf.h': Permission denied

So, where do I go from here?? Thanks.

---

### Post by perlluver on 2008-08-13
> **Amiduffer said:**
> Hi all.

I have a problem. I'm just figuring out how things work and need some direction.

I'm trying to install TVTime so as to be able to use my capture card (unless you can recomend a better capture program). So far, I've run the compile for it, and it tells me that I need ZLIB. So, I get the Zlib TAR.GZ file, unpack it, and compile, no problem, then I run MAKE, and I get this

-desktop:/usr/local/src/zlib-1.2.3$ make install
mkdir: cannot create directory `/usr/local/share/man/man3': Permission denied
make: [install] Error 1 (ignored)
cp zlib.h zconf.h /usr/local/include
cp: cannot create regular file `/usr/local/include/zlib.h': Permission denied
cp: cannot create regular file `/usr/local/include/zconf.h': Permission denied

So, where do I go from here?? Thanks.

You want to type sudo make install.

---

### Post by Martje_001 on 2008-08-13
perlluver is right. You need to typ 'sudo' before the command. This gives you root acces (Administrator rights) to the system, which is needed to create / delete / copy files to a directory outside your home-directory.

---

### Post by cariboo on 2008-08-13
I don't understand why people try to compile packages that are available in the repositories.

> So, where do I go from here?? Thanks. 

```
sudo apt-get install tvtime
```:)

Jim

---

### Post by Amiduffer on 2008-08-13
cariboo907  	
Re: Compile and make issues AAARRRGGHHH
I don't understand why people try to compile packages that are available in the repositories.


I used to think repositories were products that helped with constipation. ba dum *crash* 

Sorry cariboo907, I am completely new to Linux. For years I've been spoiled by C= Amigas installer, although it was helpful that I'm used to using the shell. I've simply been using a tutorial I've found on the site. I haven't gotten used to the lingo yet, so some things I read in the DOCS go over my head.

---

### Post by Amiduffer on 2008-08-13
Hot Shinola!

> sudo apt-get install tvtime did the trick! Thanks guys!!

Now I have to figure out why there's no sound?? sigh. Video signal comes through nice, but, no audio.

---

### Post by Methuselah on 2008-08-13
> **Amiduffer said:**
> Hot Shinola!

 did the trick! Thanks guys!!

Now I have to figure out why there's no sound?? sigh. Video signal comes through nice, but, no audio.

Most tuner cards have a cable that connects to the soundcard or motherboard CD-in.
If you installed the tuner card, did you do this?
Likely, it was already done if the computer came with it.

Now, double-click the volume control icon in the upper right of the panel and make sure the CD output is not muted and is turned up.
That might do the trick.

---

### Post by Martje_001 on 2008-08-14
Next time you need to install something, start Synaptic and search for it. It's very easy!

Can you now mark this thread as solved, please?

---

