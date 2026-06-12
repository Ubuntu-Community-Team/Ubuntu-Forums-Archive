---
title: "Distros that use xgl by default?"
date: 2007-07-04
forum: Other OS Talk
---

### Post by 67GTA on 2007-07-04
Can someone name some distros that use xgl by default? I like to be able to use composite for a few apps, but my ATI X1600 has to run on fglrx drivers. I need xgl+fglrx to enable composite. Installing a seperate xgl session was not stable enough for me. Would a distro that was built on xgl be more stable? I've tried Sabayon,  but did not like the portage/emerge thing. 3D effects/composite worked flawlessly though.

---

### Post by igknighted on 2007-07-05
Mandriva One (the non-free version) will run XGL on the liveCD.  I think if you install PCLOS and install the ATI drivers yourself it can set up XGL as well.  Suse doesn't do it automagically, but since Novell is the primary backing for the XGL project it's pretty easy to install on Suse (they /strongly/ recommend it over aiglx :)).

---

### Post by ThinkBuntu on 2007-07-05
You might want to give SAM a try. Both it and PCLOS handle 3D effects pretty well.

---

### Post by igknighted on 2007-07-05
> **ThinkBuntu said:**
> You might want to give SAM a try. Both it and PCLOS handle 3D effects pretty well.

:) I'm a little embarassed, you brought up "my" distro after I completely forgot!  Yes, SAM would be a great choice as well.  If you get the 2007.1 test1 image the drivers can be installed through a nice wizard (should be on the desktop), even if you are not online (ie the files are on the disk).  Then run drak3d as root to enable 3d effects.  The only thing I would caution you on is that sometimes fglrx doesn't like the composite extensions that are used in Xfce, but once XGL is running that shouldn't be an issue I don't believe.

---

### Post by ThinkBuntu on 2007-07-05
If you don't mind me asking, what work do you do with SAM? Also, how substantial is the project (is it just a collection of Xfce packages and artwork for PCLOS, or does it include tweaks or wholesale customizations of the base OS?)

---

### Post by 67GTA on 2007-07-05
I've been looking for an excuse to try XFCE. I am actually downloading Mint XFCE edition now. I think I will like it better than |Gnome. If XFCE agrees with me, I will give SAM a try. I'm not sure why, but Ubuntu/Mint were unstable running xgl. I had a feeling that if a distro were built on top of xgl it would run smoother without all the bugs. I saw that Berry Linux ran xgl, but it uses KDE(not for me). Thanks for the info.

---

### Post by ThinkBuntu on 2007-07-05
In my experience, SAM does the best job making Xfce seem like a full-featured environment (GNOME, KDE). Debian, Arch, and Xubuntu are all very solid choices. Zenwalk does the best job of really capturing what I feel is the essence of using Xfce (simplicity, staying out of the way, etc.), and Dreamlinux has a poorly assembled version of Xfce that misses both the OSX and Xfce marks.

---

### Post by izizzle on 2007-07-05
Why the frick is Dreamlinux at #4 on distrowatch? I don't get how ANYONE could like that distro, let alone use it.

---

### Post by jrusso2 on 2007-07-05
> **izizzle said:**
> Why the frick is Dreamlinux at #4 on distrowatch? I don't get how ANYONE could like that distro, let alone use it.

Its pretty

---

### Post by Nekiruhs on 2007-07-05
> **izizzle said:**
> Why the frick is Dreamlinux at #4 on distrowatch? I don't get how ANYONE could like that distro, let alone use it.
I like DL. It Looks like a Mac Wannabe, and it is. But its got all the eycandy preinstalled. Conky, beryl, screenlets, engage. Its a pretty useful CD to show people how Linux CAN look.

---

### Post by 67GTA on 2007-07-05
> **izizzle said:**
> Why the frick is Dreamlinux at #4 on distrowatch? I don't get how ANYONE could like that distro, let alone use it.

Their final release was the 29th. Every distro climbs the ladder when they have releases posted on Distrowatch. Now will it stay there?

---

### Post by izizzle on 2007-07-05
I tried the new relese and HATED it. It was an awful release. Just check out my review of it here: [http://ubuntuforums.org/showthread.php?t=231242&page=26](http://ubuntuforums.org/showthread.php?t=231242&page=26)

---

### Post by Erunno on 2007-07-06
openSUSE installs XGL by default but doesn't activate it. There's a control module in the official repositories that will allow you tp turn it on and off but the last time I tried that it fried X. Just a word of warning ;-)

---

### Post by 67GTA on 2007-07-06
I installed SAM. I am impressed. Got fglrx+xgl running Compiz/Beryl with no crazy bugs. If I can get used to doing things the XFCE way, I'll be okay.

---

### Post by izizzle on 2007-07-06
I could not figure out how to install my nvidia drivers in SAM... Does anyone know how?

---

### Post by 67GTA on 2007-07-06
They are in the repos after installation. Do apt-get update/apt-get upgrade, and then look for them in Synaptic.

---

