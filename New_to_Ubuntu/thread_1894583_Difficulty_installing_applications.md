---
title: "Difficulty installing applications"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by pesky_human on 2011-12-12
I recently made the switch to Lubuntu and I love it. The machine I use it on is primarily for doing work on the web. No e-mail, no document creation, nothing other than web browsing. 

I recently found an application that I would like to install and am having a terrible time trying to install it. I see the folder where it was downloaded. I can view the files.  I just cannot seem to get it installed using Lubuntu Software Center or Synaptic package manager. 

I come from a heavy Mac and Windows background and find this part of the Linux experience to be terribly frustrating. I realize that Linux is set up to be more command-line based as far as control of what goes on the machine, but it is almost as if EVERYTHING is hidden. In this regard, it is worse than the most hide-the-ball-for-your-own-good Mac OS versions. All I am trying to do is install an application. 

Any help with this would greatly improve my experience. Thanks in advance.

---

### Post by oldos2er on 2011-12-12
What application, and where did you download it from? Is it a *.deb file, or something else? Did you look in the repositories first?

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by pesky_human on 2011-12-12
> **oldos2er said:**
> What application, and where did you download it from? Is it a *.deb file, or something else? Did you look in the repositories first?

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)


It's Daphne-1.0beta.tar.gz and psychocats says that tar.gz is a last resort and i should come to this forum to get help in installing tar.gz files. Any ideas? Thanks.

---

### Post by 3rdalbum on 2011-12-13
Wow. Esoteric. A laserdisc game emulator.

I can't find a repository or PPA that contains this program, so you would have to compile it from source if you really want it. I can't guarantee that it will work, however. If you'd like to try it, then you need to **navigate your terminal** into the directory that contains the source code. So, basically, the folder that appears after you extracted the .tar.gz file.

Then you generally type:

```
./configure
make
sudo make install
```

When you type "./configure" you'll probably get an error message telling you that it can't find a library. You then need to install the library using Synaptic Package Manager; actually, you'll need the version of the library whose name ends with "-dev". Then start the process again.

If this sounds too hard, then try and stick to packages that contain binary (precompiled) programs, preferably .deb packages or Ubuntu repositories. Most mainstream programs will be easily installable from one of these sources.

---

### Post by lolpenguin on 2011-12-13
Or it might be this:
```
cd /~path of extracted archive~
./autogen.sh --prefix=/usr
make
sudo make install
```

---

### Post by oldos2er on 2011-12-13
The file daphne-1.0beta-linux.tar.gz contains ready-to-run binaries, you'll just need to install some dependencies. Since there's no README or INSTALL file, I suggest you ask for help at their forums: [http://forum.logiqx.com/](http://forum.logiqx.com/)

---

