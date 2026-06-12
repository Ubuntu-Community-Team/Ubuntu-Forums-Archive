---
title: "installing anjuta -- need help"
date: 2006-06-10
forum: Programming Talk
---

### Post by Micik on 2006-06-10
Hello friends,
I have just installed ubuntu 5.04 and want to start programming in C++. I have read that anjuta is highly recommended and very good IDE. However I have tried to installed version 1.2.4 but without any succes. When trying to execute ./config I get error message something about perl xml parser and configure quits.
Please can you give me link and instructions about everything what I need to succesfully install and use anjuta (maybe newer version). I tried several times but no succes. I have very poor experience with linux in general and every help is welcome.
If you need anjuta what would you download?
Please give me advices so I can start working in anjuta. 
Thanks very much

---

### Post by Fafnir on 2006-06-10
Actually, unless you really need to compile from source for some reason you can get precompiled binaries from the repositories - much less effort! Two ways of doing it - console-based and graphics-based. 

Console based: go to Applications->Accessories->Terminal and type:

```
sudo apt-get install anjuta
```

Graphics based: Go to System->Administration->Synaptic Package Manager, then find the package named anjuta, mark it and hit Apply.

Hope that helps!

---

### Post by Micik on 2006-06-10
Thanks for your reply. Unfortunately computer on which is ubuntu installed doesn't have access to the internet. So I need form other computer to download all I need. I don't have to install from source, in fact it gives me a headache. Please if you know post links to all what I need. I already have downloaded source for anjuta 1.2.4 in tar file, but cannot install. If you know where to find precompiled binaries, please post link.
Thanks

---

### Post by FizDev on 2006-06-10
Go there : [ftp://ftp.sk.debian.org/ubuntu/pool/universe/a/anjuta](ftp://ftp.sk.debian.org/ubuntu/pool/universe/a/anjuta)
Download the appropriate version for your computer. Then open a terminal and go to the directory where you put the .deb
```
sudo dpkg -i nameofthedebpackage.deb
```
This should install it, but you will probably still have to install other things after (a couple of depencies)

---

### Post by Fafnir on 2006-06-11
[QUOTE=FizDev]This should install it, but you will probably still have to install other things after (a couple of depencies)[/QUOTE]

Here's a full list:

```
  Depends: libart-2.0-2
  Depends: libatk1.0-0
  Depends: libbonobo2-0
  Depends: libbonoboui2-0
  Depends: libc6
  Depends: libcairo2
  Depends: libfontconfig1
  Depends: libfreetype6
  Depends: libgcc1
  Depends: libgconf2-4
  Depends: libglade2-0
  Depends: libglib2.0-0
  Depends: libgnome-keyring0
  Depends: libgnome2-0
  Depends: libgnomecanvas2-0
  Depends: libgnomeprint2.2-0
  Depends: libgnomeprintui2.2-0
  Depends: libgnomeui-0
  Depends: libgnomevfs2-0
  Depends: libgtk2.0-0
  Depends: libice6
  Depends: libncurses5
  Depends: liborbit2
  Depends: libpango1.0-0
  Depends: libpcre3
  Depends: libpopt0
  Depends: libsm6
  Depends: libstdc++6
  Depends: libvte4
  Depends: libx11-6
  Depends: libxcursor1
  Depends: libxext6
  Depends: libxfixes3
  Depends: libxft2
  Depends: libxi6
  Depends: libxinerama1
  Depends: libxml2
  Depends: libxrandr2
  Depends: libxrender1
  Depends: zlib1g
  Depends: scrollkeeper
  Depends: anjuta-common
  Suggests: libgtk2.0-dev
  Suggests: libgtkmm2.0-dev
  Suggests: libgnome2-dev
  Suggests: <libgnomemm2.0-dev>
  Suggests: <devhelp-books>
 |Suggests: glade-2
    glade
    glade-gnome
  Suggests: glade-gnome-2
    glade-gnome
 |Recommends: gcc
  Recommends: g++
  Recommends: make
  Recommends: cvs
    cvsnt
  Recommends: gnome-terminal
  Recommends: yelp
  Recommends: <automake>
    automake1.4
  Recommends: autoconf
  Recommends: autogen
  Recommends: indent
  Recommends: gdb
  Recommends: <ctags>
    exuberant-ctags
  Recommends: devhelp
  Recommends: gnome-devel
  Recommends: libtool
```

That's the output of ```
apt-cache depends anjuta
``` anyway. You'll probably have most of them already, though - it's not as bad as it looks! I think you should be able to see if you have a given package using Synaptic, with or without Internet access, so check which one's you don't have and install them with dpkg.

Hope that helps!

---

### Post by Micik on 2006-08-08
Guys,
I connected my ubuntu machine to the internet.
I have typed in terminal:
sudo apt-get install anjuta
However I get something like this:
building dependency tree....done
error anjuta could not be found or something similar. I suppose I need to enter source in source list so linux can search for anjuta.
What address to add to source list file in order to install anjuta without problem?
Should I get [ftp://ftp.sk.debian.org/ubuntu/pool/universe/a/anjuta](ftp://ftp.sk.debian.org/ubuntu/pool/universe/a/anjuta) or something else?
Please can you explain me step by step procedure to make this less frustrating.
Thanks

---

