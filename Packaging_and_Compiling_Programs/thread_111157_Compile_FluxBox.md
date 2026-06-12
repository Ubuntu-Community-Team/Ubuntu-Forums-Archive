---
title: "Compile FluxBox?"
date: 2006-01-01
forum: Packaging and Compiling Programs
---

### Post by evaderus on 2006-01-01
Hi, I was wondering if I should compile [fluxbox]("http://www.fluxbox.org") or download the Debian binary in the download section?
I don't know how to compile, so I would need some help with that if I need to.

---

### Post by noob_Lance on 2006-01-01
i sudo apt-get installed it.. so you should be able to aswell

---

### Post by evaderus on 2006-01-09
```
evad@ubuntu:~$ sudo apt-get install fluxbox
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  fbpager xfonts-artwiz
The following NEW packages will be installed:
  fluxbox
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B/775kB of archives.
After unpacking 2748kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 59913 files and directories currently installed.)
Unpacking fluxbox (from .../fluxbox_0.9.12-1build1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/fluxbox_0.9.12-1build1_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/bsetroot.1.gz', which is also in package blackbox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/fluxbox_0.9.12-1build1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
evad@ubuntu:~$
```

I got a nasty little error, I also went to fluxbox's webpage and found fluxbox_0.9.14-1_i386.deb, which the version I'm getting from apt-get is 9.12, so if I download fluxbox_0.9.14-1_i386.deb, how would I install that?

---

### Post by Spano on 2006-01-10
From terminal -
sudo dpkg -i filename.deb
In my case-
sudo dpkg -i ~/fluxbox_0.9.14-1_i386.deb
because I downloaded the file to my home directory.  
Good luck with fluxbox, it's great!

---

### Post by noob_Lance on 2006-01-10
if you want desktop icons... get fbDesk aswell... except you have to edit the icons file manually..
i on the other hand... am in the process of making a customizable program that will update it for you using the icons you want and such. its a nifty little program... ill PM you when i get it done.. hopefully in a week or so.

~Lance

---

### Post by DoorGunner on 2006-01-10
I just finished doing a bunch of that......

here is a reference.
[http://fluxbox-wiki.org/index.php/Howto_edit_menu](http://fluxbox-wiki.org/index.php/Howto_edit_menu)
[https://wiki.ubuntu.com/Fluxbox](https://wiki.ubuntu.com/Fluxbox)

if you need a hand with customization i can help.....i just did mine.

I installed using synaptic.....just search for fluxbox and install everything (3or4) and leave the bbmail one out.

---

### Post by evaderus on 2006-01-10
Thanks a lot, but I should be fine with the customization, I'm quite familiar with BB4win and BBlean, so I should be fine.

---

