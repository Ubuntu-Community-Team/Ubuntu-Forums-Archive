---
title: "HOWTO: Installing GJay"
date: 2005-04-08
forum: Outdated Tutorials &amp; Tips
---

### Post by SFN on 2005-04-08
From the GJay site:

"GJay (Gtk+ DJ) generates playlists across a collection of music (ogg, mp3, wav) such that each song sounds good following the previous song. It is ideal for home users who want a non-random way to wander large collections or for DJs planning a set list. You can generate playlists from within the application, or run GJay as a standalone command-line utility."

GJay works if you just do 

```
sudo apt-get install gjay
```

But...

...and there's always a but...

It does not recognize OGG files as songs. :-?  I went checking through the GJay site to see there was any info about OGGs there. Although there wasn't much, a quick look at the dependencies listed indicated that some files were not getting set as dependencies in the GJay package being used by Ubuntu.

So, if you want to include OGGs in your GJay created playlists, do 

```
sudo apt-get install gjay vorbis-tools
```

and all will be well.

---

### Post by Jad on 2005-04-08
Thank you!

---

### Post by angrykeyboarder on 2005-06-07
[QUOTE=SFN]

....if you want to include OGGs in your GJay created playlists, do 

```
sudo apt-get install gjay vorbis-tools libvorbis-dev libgtk2.0-dev xmms-dev libgsl0-dev 
```

and all will be well.[/QUOTE]

** Can I leave out the *xmms-dev* part?**

---

### Post by pdk001 on 2005-06-07
thanks for the tip

---

### Post by SFN on 2005-06-08
[QUOTE=angrykeyboarder]** Can I leave out the *xmms-dev* part?**[/QUOTE]

xmms-dev is listed as a dependency for gjay on debian. See [this](http://gjay.sourceforge.net/build.html). I'd have to assume that the same would be true for Ubuntu. You could try it without xmms-dev. If it doesn't work, adding xmms-dev should make it work.

---

### Post by rwabel on 2005-07-14
[QUOTE=SFN]xmms-dev is listed as a dependency for gjay on debian. See [this]("http://gjay.sourceforge.net/build.html"). I'd have to assume that the same would be true for Ubuntu. You could try it without xmms-dev. If it doesn't work, adding xmms-dev should make it work.[/QUOTE]
The author talks about building gjay, that's why the dev packages are needed.
If you only want to install the binary via apt, it should be enough to make:
```
sudo apt-get install gjay vorbis-tools
```

---

### Post by nickless on 2005-07-16
Is there a sublime message in the name of the program? :D

---

### Post by SFN on 2005-07-18
[QUOTE=rwabel]The author talks about building gjay, that's why the dev packages are needed.
If you only want to install the binary via apt, it should be enough to make:
```
sudo apt-get install gjay vorbis-tools
```[/QUOTE]

Makes sense. I've already got it installed here using the method that I mentioned above. If anybody can verify that just gjay and vorbis-tools will do it, I'll change the original post.

---

### Post by rwabel on 2005-07-18
[QUOTE=SFN]Makes sense. I've already got it installed here using the method that I mentioned above. If anybody can verify that just gjay and vorbis-tools will do it, I'll change the original post.[/QUOTE]
 I do :-)

---

### Post by SFN on 2005-07-19
[QUOTE=rwabel]I do :-)[/QUOTE]

Thanks, rwabel. The update has been made.

---

### Post by rikxik on 2009-05-27
I can't install gjay in Jaunty:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gjay is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gjay has no installation candidate


Anybody has any idea on what has replaced it? Or any other equivalent software?

---

### Post by imretokyo on 2009-11-19
I am with karmic and when i try to install the deb package it says there are missing dependencies. libgsl0. but libgsl0 is not in synaptyc.HOw can I get it?

---

### Post by daniel_gv93 on 2009-11-23
yeah =/ im on linux mint 7 and i have the same problem...i got the .dev from the web and when i try to execute it it opens the package installer but with an error saying: Error: Dependency is not satisfiable: libgsl0 (>= 1.4)
any ideas?...already trying installing all the packages it says in the webpage    
* Applications
          o mp3info
          o mpg321
          o vorbis-tools
          o xmms 
    * Libraries
          o libgtk2.0
          o libgsl0
          o libvorbis 
    * Devel packages
          o libvorbis-dev
          o libgtk2.0-dev
          o xmms-dev
          o libgsl0-dev 
but some of them are missing.. any ideas(i think ubuntu and linux mint share repositories(or at least linux mint uses ubuntu repositories also))

---

### Post by jhp88 on 2010-01-25
Same problem on Ubuntu 9.10, fresh install.

> Error: Dependency is not satisfiable: libgsl0 (>= 1.4)

---

### Post by wollac on 2010-03-22
Hi. I too had this problem but resolved it after much package searching and tinkering. So I have complied a tutorial telling you what I did so you can also have GJay on ubuntu or ubuntu variants (may also work on Debian).

Before that I just want to say, **@rikxik:** you need to get a deb for GJay from here: [http://archive.ubuntu.com/ubuntu/pool/universe/g/gjay/]("http://archive.ubuntu.com/ubuntu/pool/universe/g/gjay/") because it is no longer in the repositories. Then you will probably get dependency issues like the rest of us, for which I explain the solutions to below. 
[B][U]
The actual tutorial to fixing the issues with the installation of GJay[/U][/B]

If you get this error:

```
Error: Dependency is not satisfiable: libgsl0 (>= 1.4) 
```

**Then you should download a deb for libgsl0 from here:**
[http://packages.ubuntu.com/dapper/libgsl0]("http://packages.ubuntu.com/dapper/libgsl0")

**Then Install libgsl0:**
When you try to Install libgsl0, you may, as I was, be presented with another error - a conflict involving the breaking of the libgsl0ldbl package. The message was something like (or possibly exactly) this:

```
Error: Breaks exisiting package 'libgsl0ldbl' conflict: libgsl0 ( )
```

To fix which you need to remove libgsl0ldbl with a simple 'sudo apt-get remove libgsl0ldbl' (minus quotes). 

Then re-open the libgsl0 deb and you should now be able to install it.

Next try and install GJay again.

I then got another error when trying to install GJay: 

```
Error: Dependency is not satisfiable: xmms


```

It is quite likely you will also get this. This is because XMMS, Despite being a popular music player for Linux, has been removed from the repositories since the Gutsy Gibbon release.

**_Installing XMMS:_**

**First, open the 'source.list' file:**

*sudo gedit /etc/apt/sources.list*

**Next, add these two lines, then save and close the file:**

(For ubuntu 9.04 or later):

[I]deb [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/jaunty](http://www.pvv.ntnu.no/~knuta/xmms/jaunty) ./
[/I]
_OR _

(For ubuntu 8.04):

[I]deb [http://www.pvv.ntnu.no/~knuta/xmms/hardy](http://www.pvv.ntnu.no/~knuta/xmms/hardy) ./
deb-src [http://www.pvv.ntnu.no/~knuta/xmms/hardy](http://www.pvv.ntnu.no/~knuta/xmms/hardy) ./
[/I]
**Finally, Update and install xmms:**

[I]sudo apt-get update
 
sudo apt-get install xmms[/I]

Now you can go back and Install GJay as all the dependencies should be satisfied! 

And that's how you install GJay on ubuntu! If you have any more problems let me know and i will do my best to help.

---

### Post by imretokyo on 2010-03-26
Sounds promising. I will try to do it. I moved to 10.04 beta 1, but I hope it dosn`t make any differents.

Thank you for your help.

---

### Post by poodlepatrol on 2010-03-27
You, sir, are a steely-eyed missile man. THIS WORKED WELL, and installed GJay in 9.10. TYVM

---

