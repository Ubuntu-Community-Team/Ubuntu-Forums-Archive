---
title: "Sofware problem: apt-file, apt-get"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Cap'n Redbeard on 2008-05-05
Hi Folks,

i'm still having problems with apt-file and apt-get from the command line.

Thanks so far to Nepherte, Oldsoldier2003 and bapoumbia for their help so far.

i'm trying to compile the gEDA package.

Have run it incompletely on X11 Mac, so thought i'd try it on Linux (hence Ubuntu).

Installed Ubuntu Gutsy (7.10) on spare H/D on this wintel box. It worked great (although hadn't had the chance to compile gEDA). Connected it to hub, did a software upgrade and got Ubuntu Hardy installed.

Have had some problems with installing software.

Following the guidelines on the

[URL="http://help.ubuntu.com/community/CompilingEasyHowTo"]

doesn't seem to work because the

```
apt-file update
```

fails to get anything, so apt doesn't know where any files are.

Using bapoumbia's "sources.list" file i've got this far.

However, i'm still having problems finding stuff from the command line, eg:

> redbeard@Redbeard-desktop:~$ apt-file search gtk+-2
libgtk-directfb-2.0-dev: /usr/lib/pkgconfig/libgtk-directfb-2.0-0/gtk+-2.0.pc
libgtk2.0-dev: /usr/lib/pkgconfig/gtk+-2.0.pc
lsb-build-desktop3: /usr/lib/lsb3/pkgconfig/gtk+-2.0.pc
valac: /usr/share/vala/vapi/gtk+-2.0.deps
valac: /usr/share/vala/vapi/gtk+-2.0.vapi
redbeard@Redbeard-desktop:~$ sudo apt-get install gtk+-2.0.pc
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package gtk+-2.0.pc
redbeard@Redbeard-desktop:~$ 

Am i better off doing a re-install to Gutsy 7.10 from CD/DVD with the DSL cable plugged in ?

---

### Post by scragar on 2008-05-05
Is the package not libgtk2.0-dev (```
sudo apt-get install libgtk2.0-dev
```)?

if your not getting any text in ```
sudo apt-get update
``` would you mind posting back your /etc/apt/sources.lst file?
```
cd ~/Desktop && cp /etc/apt/sources.lse ./sources.lst
```

---

### Post by Cap'n Redbeard on 2008-05-05
Thanks for your response scragar,

i've been waiting for µ$2000 to complete "update" since midnight so don't want to re-boot into grub/Proper OS 'till it's done. The missus was messing about with µ$ last night so i thought i'd better sort it out.

The package name "gtk2+-2.0.pc" came from the output of "apt-file search gtk+-2" following the instructions in "http://help.ubuntu.com/community/CompilingEasyHowTo", it is looking for a ".pc" at the end of the file name. However, the "gattrib" file of gEDA requires gtk+-2.4.0. or later.

i had hoped that "apt" would be able to find the proper dependancies to compile files, but my "apt-file" list may not contain the sources.

i realise this is not a problem with Ubuntu Linux because the files requested are not within the Ubuntu domain.

Is your "/etc/apt/sources.lst" in any way related to the "/etc/apt/sources.list" file ?

i'll post it when i can re-boot the wintel box into Linux to check.

Cheers scragar, :KS

---

### Post by scragar on 2008-05-05
it is .list I must have missed the i first time around, and copied and pasted it, sorry.

I tried running apt-file myself, and even though apt-get and apt-cache both work perfectly apt-file isn't working as expected(slow, no output at all. is that normal?)

packages for building things do tend to end in -dev, since they are the development versions(and on ubuntu it's normaly only developers that need them :P).

---

### Post by Cap'n Redbeard on 2008-05-06
Hi scragar,

Phew, wintel update's just finished. i bet it still doesn't work !

Ok, etc/apt/sources.list contents:

> ## General.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse

## Major bug fix updates.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse

## Security.
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse

This is the "sources.list" file i got from bapoumbia. It works rather better than the original (i'll post it if you want).

Yes, apt-get works, but apt-file doesn't work properly. i got a heap of "not found" errors. Since switching to bapoumbia's version of the "sources.list" file there are less "not found" errors, but then again it's not looking for so many files...

Perhaps it's developer files i'm looking for 'coz gEDA isn't exactly yer standard software ?

Should i send you the original "sources.list" this build had ? It has a load of "didn't compile" comments in it.

Any clues ?

---

### Post by hyper_ch on 2008-05-06
with apt-file you can in what package a specific file is and to update its database, like with apt-get, you have to run it as sudo.

---

### Post by Cap'n Redbeard on 2008-05-06
Ah, thank you hyper_ch,

> with apt-file you can in what package a specific file is and to update its database, like with apt-get, you have to run it as sudo. 

the apt-file and apt-get databases of file locations ONLY hold lists of files packaged for a specific Ubuntu release (hardy for example).

So if a specific file or files (in this case "atk-1.9.1", "pango-1.21.0", "cairo-1.6.2", "gtk+-2.8.2") are not listed as available by apt-file, I have to install them manually ?

That being the case, I download each one from GNOME as a ".tar.gz", and expand 'em.

Where should i put them to run "./configure", "make" and "make install" ?

Will apt know where i've put them and link them into it's own database for future use ?

Is this the right way or am i barking up the wrong tree ? :confused:

---

### Post by hyper_ch on 2008-05-06
I don't understand the problem.

---

### Post by Cap'n Redbeard on 2008-05-06
Hi hyper_ch,

The problem is that i'm new to Linux and don't know how it works or what i'm doing.

i'm trying to install a package called "gEDA", very few of whose components (dependancies) are found when i do "apt-file search <filename>" from the command line. None are listed in Synaptic Package Manager.

As i can't use apt or Synaptic to find and install the necessary files, i'm looking to download them from the GNOME archive and build them locally.

If i do this, will apt know where they are on this machine ?

You see, it's a problem of me not understanding.

Cheers,

---

### Post by scragar on 2008-05-06
if you download them to the folder you should be able to run:
```
sudo dpkg -i **/path/to/folder/**
```
although it's proberly easier to just let apt-get do all the leg work:
```
sudo apt-get install geda
```(hardy only), or via the .deb installer - search [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by Cap'n Redbeard on 2008-05-06
Thanks scragar,

i'll do that. Had been running the install CD from the gEDA website, but i'll let apt do all the work.

i was just wondering where i should put and build dependancy files ? Should these go in /usr/local/src ?

Anyway, i'll try 

```
sudo apt-get install geda
```

now and see if it works.

Thanks again,

---

### Post by hyper_ch on 2008-05-06
with apt-file you can search what package contains a specific file. It will return the package name. You can then install that package with apt-get install ...

---

### Post by Cap'n Redbeard on 2008-05-07
Thanks hyper_ch, thanks scragar,

That all seems to work now. i do make things complicated for myself !

:KS:KS

---

