---
title: "Brand new, trying to set up a server on a dinosaur machine"
date: 2017-09-06
forum: New to Ubuntu
---

### Post by vgledhill on 2017-09-06
Hi People.

I've grabbed a copy of Ubuntu Server 8.4 I think it is.  and installed it on an old machine, hoping to serve some web pages from it.

I followed a guide which stated that I should type 
```
[COLOR=#000000][FONT=monospace]$ sudo apt-get install openssh-server[/FONT][/COLOR]
``` at the command prompt, but I get errors that say it failed to fetch, which makes me wonder if the computer is connected to the outside world.

I have it connected to Virgin Cable here in the UK, what commands can I run to check if it is connected to the web? 

Regards
VinceG

---

### Post by Tadaen_Sylvermane on 2017-09-06
Install the latest LTS, 8.4 is 9 years old. Hence not supported. Do yourself and the internet a favor and install the current 16.04 LTS.

You are getting the error because the repos for that version are moved to archives.

---

### Post by vgledhill on 2017-09-06
Thanks mate, is that the command line version?  The computer really is a dinosaur.

---

### Post by Tadaen_Sylvermane on 2017-09-06
Download the server version. Will be command line from the start.

---

### Post by westie457 on 2017-09-06
Hello and welcome to Ubuntu Forums.

This [COLOR=#000000] Ubuntu Server 8.4 is the root of your problems. Ubuntu Server 8.04 went End of Life at least 4 years ago and the repositories have been pulled.

Suggest you try Ubuntu 14.04 server edition from here. [/COLOR]http://old-releases.ubuntu.com/releases/14.04.0/

or one of the lighter flavours such as Lubuntu or Xubuntu 16.04.

Explore this page for ideas. [https://www.ubuntu.com/download/ubuntu-flavours](https://www.ubuntu.com/download/ubuntu-flavours)

---

### Post by vgledhill on 2017-09-07
Thanks guys, I went for the 16.04.03 server, and burned DVD after DVD on my win 10 laptop but then realised that the dinosaur machine was a CD drive... doh.... 16.04.03 is too big for a CD.... anyway, cut to the chase, I've managed to put it  onto a memory stick and have it installing as I type this.

---

### Post by Tadaen_Sylvermane on 2017-09-07
A true dinosaur, even 2 old laptops that i wiped so my wifes boss can get rid of them had dvd drives. Stoneage laptops to. I haven't seen an actual cd drive in as long as i can remember.

---

### Post by deadflowr on 2017-09-07
> **vgledhill said:**
> Thanks guys, I went for the 16.04.03 server, and burned DVD after DVD on my win 10 laptop but then realised that the dinosaur machine was a CD drive... doh.... 16.04.03 is too big for a CD.... anyway, cut to the chase, I've managed to put it  onto a memory stick and have it installing as I type this.

Ubuntu 16.04 or 16.04.1 server is smaller than a cd, around 645mb to 670mb, or thereabouts.
Found here: [http://old-releases.ubuntu.com/releases/xenial/]("http://old-releases.ubuntu.com/releases/xenial/")

Typically you want either the amd64.iso(64-bit) or the i386.iso(32-bit), if the machine is old, then go with i386.iso

Even though the page is for old-releases those images are 16.04 images and fully supported, or at least the 16.04 and 16.04.1 images are.
More explain here
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")
and here
[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack]("https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack"))

---

### Post by vgledhill on 2017-09-07
Thanks guys.  8 DVD's later, 2 CD's and countless re-writes of USB sticks, I think I've finally got there.

---

