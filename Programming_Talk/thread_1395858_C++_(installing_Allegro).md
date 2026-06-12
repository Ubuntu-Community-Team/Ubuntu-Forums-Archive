---
title: "C++ (installing Allegro)"
date: 2010-02-01
forum: Programming Talk
---

### Post by Logan513 on 2010-02-01
Well, I fallowed the golden rule ("Google before posting") And I came up empty handed. I want to install the Allegro Library so I can start using it in my code. I am using GCC. I want it so that I don't have to type anything fancy while compiling the code; just a simple g++ -o blah blah.cpp. But how would I do it? I have never attempted anything like installing a library before so I have no idea on anything that's involved. If someone could please post an absolute n00b spoonfed tutorial for me that would be terriffic!

Also, if I were to share my finished executable with a friend (and it uses allegro). Would he need Allegro too for it to work? And if I were to take the code and compile it in Windows (with Allegro installed) would it work just the same?

Thanks,
-Logan-

---

### Post by Zugzwang on 2010-02-01
The simplest way of installing a library is to use the package manager. So a quick "sudo apt-get install liballegro4.2-dev" should be of help.

However, when linking your program, you will *always* need to specify that you want to link against that library (and hench, need to add something like "-lalleg" to your command). There is no possibility to circumvent this (other than crude hacks).

---

### Post by Logan513 on 2010-02-01
Okay, so let's say I have Allegro installed (which I don't already), how would I incorporate the Allegro Library in my command. I'm not to good with Bash so I don't know how to do this.... Would it be like 'g++ -o -lalleg blah blah.cpp'? :|

---

### Post by Logan513 on 2010-02-01
Wow. I typed in your command to get the library... and this happened;

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-crypto libopenal1 liblash2 libsm-dev python-zopeinterface
  python-twisted-names python-twisted-core python3.0-minimal dvgrab libice-dev
  automake1.4 python-renderpm libatk1.0-dev swh-plugins qjackctl
  libglib2.0-dev libmlt++1 python-twisted-web x11proto-xinerama-dev
  libgfortran3 libpango1.0-dev glade-common libvamp-hostsdk2
  python-twisted-runner liblo0ldbl libxi-dev autoconf libcairo2-dev
  python-lxml python-reportlab-accel libsysfs-dev libdirectfb-extra
  libvamp-sdk1 libsox1 python3.0 libpng12-dev libfontconfig1-dev inigo
  libdirectfb-dev x11proto-composite-dev python-serial python-pam
  python-openssl python-twisted-mail python-numpy cmt
  libgnomecanvasmm-2.6-1c2a x11proto-randr-dev x11proto-damage-dev
  autotools-dev libxcb-render-util0-dev libgtk2.0-dev python-twisted-lore
  libjpeg62-dev python-twisted-conch python-pyopenssl python-twisted-news
  python-twisted-words libphysfs-1.0-0 libxdamage-dev ffmpeg libwmf-bin
  python-twisted zlib1g-dev libavfilter0 libfreetype6-dev libsox-fmt-base
  libfluidsynth1 python-uniconvertor libblas3gf libxcomposite-dev automake
  imagemagick-doc python-setuptools liblapack3gf python3-minimal libxrandr-dev
  libsox-fmt-alsa libexpat1-dev libaubio2 imagemagick libpixman-1-dev
  libxft-dev libxcb-render0-dev jackd ladcca2 libmlt-data perlmagick
  libxinerama-dev python-reportlab gstreamer0.10-gnonlin python-twisted-bin
  libmlt1 libavdevice52
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  liballegro4.2 liballegro4.2-plugin-jack libxpm-dev libxxf86vm-dev
  x11proto-xf86vidmode-dev
Suggested packages:
  timidity-patches liballegro4.2-plugin-esd
The following NEW packages will be installed:
  liballegro4.2 liballegro4.2-dev liballegro4.2-plugin-jack libxpm-dev
  libxxf86vm-dev x11proto-xf86vidmode-dev
0 upgraded, 6 newly installed, 0 to remove and 158 not upgraded.
Need to get 1568kB of archives.
After this operation, 4690kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com jaunty/main libxpm-dev 1:3.5.7-1 [45.9kB]
Get:2 http://us.archive.ubuntu.com jaunty/main x11proto-xf86vidmode-dev 2.2.2-5ubuntu1 [6952B]
Get:3 http://us.archive.ubuntu.com jaunty/main libxxf86vm-dev 1:1.0.2-1 [17.5kB]
Get:4 http://us.archive.ubuntu.com jaunty/universe liballegro4.2 2:4.2.2-2ubuntu1 [538kB]
Get:5 http://us.archive.ubuntu.com jaunty/universe liballegro4.2-dev 2:4.2.2-2ubuntu1 [954kB]
Get:6 http://us.archive.ubuntu.com jaunty/universe liballegro4.2-plugin-jack 2:4.2.2-2ubuntu1 [5464B]
Fetched 1568kB in 6s (245kB/s)                                                 
Selecting previously deselected package libxpm-dev.
(Reading database ... 163486 files and directories currently installed.)
Unpacking libxpm-dev (from .../libxpm-dev_1%3a3.5.7-1_i386.deb) ...
Selecting previously deselected package x11proto-xf86vidmode-dev.
Unpacking x11proto-xf86vidmode-dev (from .../x11proto-xf86vidmode-dev_2.2.2-5ubuntu1_all.deb) ...
Selecting previously deselected package libxxf86vm-dev.
Unpacking libxxf86vm-dev (from .../libxxf86vm-dev_1%3a1.0.2-1_i386.deb) ...
Selecting previously deselected package liballegro4.2.
Unpacking liballegro4.2 (from .../liballegro4.2_2%3a4.2.2-2ubuntu1_i386.deb) ...
Selecting previously deselected package liballegro4.2-dev.
Unpacking liballegro4.2-dev (from .../liballegro4.2-dev_2%3a4.2.2-2ubuntu1_i386.deb) ...
Selecting previously deselected package liballegro4.2-plugin-jack.
Unpacking liballegro4.2-plugin-jack (from .../liballegro4.2-plugin-jack_2%3a4.2.2-2ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up libxpm-dev (1:3.5.7-1) ...
Setting up x11proto-xf86vidmode-dev (2.2.2-5ubuntu1) ...
Setting up libxxf86vm-dev (1:1.0.2-1) ...
Setting up liballegro4.2 (2:4.2.2-2ubuntu1) ...

Setting up liballegro4.2-dev (2:4.2.2-2ubuntu1) ...
Setting up liballegro4.2-plugin-jack (2:4.2.2-2ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

Did I do it right? Can I now use Allegro? :-s

---

### Post by Logan513 on 2010-02-01
I'm sorry for all these posts. I'm so new to Allegro. Are all the images and sounds and stuff going to be drawn in the console? Or will it be more like a Windows program?

---

### Post by dwhitney67 on 2010-02-01
> **Logan513 said:**
> ```
...
Setting up libxpm-dev (1:3.5.7-1) ...
Setting up x11proto-xf86vidmode-dev (2.2.2-5ubuntu1) ...
Setting up libxxf86vm-dev (1:1.0.2-1) ...
Setting up liballegro4.2 (2:4.2.2-2ubuntu1) ...

Setting up liballegro4.2-dev (2:4.2.2-2ubuntu1) ...
Setting up liballegro4.2-plugin-jack (2:4.2.2-2ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

Did I do it right? Can I now use Allegro? :-s

From the messages above, everything looks good.  As for your other question (from your next post) concerning the runtime behavior of allegro apps, I can't help you with that; I do not have any experience whatsoever with allegro.

---

### Post by Logan513 on 2010-02-01
Okay, who here does have experience with Allegro?

---

### Post by dwhitney67 on 2010-02-01
Just look here for the tutorials.
[http://alleg.sourceforge.net/docs.html](http://alleg.sourceforge.net/docs.html)

It's funny that you chose a library, but know next to nothing about it.  Surely you have some notion of it's capabilities?

---

### Post by Logan513 on 2010-02-01
I've heard you can use it to manipulate sounds and images. That's all I know. And I wan't to learn.

---

### Post by Logan513 on 2010-02-01
Okay, so I decided that I want to use Code::Blocks.... Well, at the startup it looks as though I am going to be using the gcc compiler as the default compiler with Code::Blocks. Does that mean Allegro should just work since I already have it installed? Or do I need to do something more in Code::Blocks?

---

### Post by Logan513 on 2010-02-01
Well, after 76 painstaking pages..... Google prevailed! I found what I was looking for. I'm all set to start learning Allegro! Thanks for the help guys!

---

### Post by scottslinux on 2010-05-14
I realize that your posts about code blocks and allegro were some time ago, but I find myself in the same circumstance.  How did it go with code blocks and y.  Create anything cool. I know how to install allegro but getting it to work with an IDE like codeblocks seems to be the challenge. Any advice on what you did to get it working???

thanks
Scott

---

### Post by pokebirdd on 2010-05-14
I don't know anything about IDEs (never used one) but if you were to compile a simple allegro program using the terminal, you can just go: [HTML]g++ file.cpp `allegro-config --libs`[/HTML] Note that those ` are backticks. The allegro-config file should be automatically generated if you built allegro from source.

---

### Post by dejaime on 2010-07-15
> **pokebirdd said:**
> I don't know anything about IDEs (never used one) but if you were to compile a simple allegro program using the terminal, you can just go: [HTML]g++ file.cpp `allegro-config --libs`[/HTML] Note that those ` are backticks. The allegro-config file should be automatically generated if you built allegro from source.I don't know why, I've been trying to use [SIZE=4]**'**[/SIZE] instead of **[SIZE=4]`[/SIZE]** for about hours... I was 101% sure allegro wasn't installed correctly...

THANks!!! [:

---

