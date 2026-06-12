---
title: "ubuntu desktop environtment"
date: 2023-10-06
forum: New to Ubuntu
---

### Post by rifqilubis on 2023-10-06
So right now im using Kubuntu (KDE), but im seeing its using around 2gib ram.  So i see someone have shown that their linux only using 400mb ram.

Is there linux distro that still supported, but have less ram usage fewer than 1gib ?

---

### Post by rifqilubis on 2023-10-06
I just found out xubuntu and lubuntu.

which you guys recommends?

---

### Post by aljames2 on 2023-10-07
They both are good choices.  Lubuntu is slightly lighter.  I use Xubuntu and it shows to be using about 550mb of ram which is also light weight.  Try & see whichever one you like the look & feel of. 
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

---

### Post by ne29914 on 2023-10-07
I'm on Lubuntu since 18.10 (LXQt) and like it a lot. It's fast and easy to use. If I had to choose today, it'd be a toss-up between Lubuntu and Xubuntu.

---

### Post by ajgreeny on 2023-10-07
There is also a very good sticky thread here on this forum at [https://ubuntuforums.org/showthread.php?t=2415676](https://ubuntuforums.org/showthread.php?t=2415676) which has a lot of detail and some potentially useful information.

---

### Post by rifqilubis on 2023-10-07
thanks for all your comment. really appreciate it.

---

### Post by TenPlus1 on 2023-10-08
Lubuntu will be the lightest on desktop resources, unless you look outside and check out Bodhi Linux 7.0 which is still built on ubuntu 22.04.3 base.

---

### Post by rifqilubis on 2023-10-08
> **TenPlus1 said:**
> Lubuntu will be the lightest on desktop resources, unless you look outside and check out Bodhi Linux 7.0 which is still built on ubuntu 22.04.3 base.

i have a question regarding lubuntu, it runs all apps that debian support right?

and when i reinstall, my second harddrive (kubuntu). Do i need to reinstall AMD Driver?

---

### Post by ajgreeny on 2023-10-08
> **rifqilubis said:**
> i have a question regarding lubuntu, it runs all apps that debian support right?

and when i reinstall, my second harddrive (kubuntu). Do i need to reinstall AMD Driver?
All the applications that are available in Debian are generally also available in Ubuntu and all its flavours though not directly from Debian repos but using the default Ubuntu repos.  You may even find that some things in Ubuntu's repos are not in Debian's but I have never bothered to check.  I do run a virtual install of Debian Unstable just to keep abreast of how it is working (great so far) but I'm not sure if PPAs are available for Debian and I do need one or two of those in my daily usage of my computers.

As for the AMD driver, that will depend very much on what AMD hardware you have; AMD now has very good support for some hardware which is installed with the OS and therefore needing no further action from you after installation.

---

### Post by donald187 on 2023-10-08
PPA's are highly discouraged on Debian.[URL="https://wiki.debian.org/DontBreakDebian#Don.27t_make_a_FrankenDebian"]

[https://wiki.debian.org/DontBreakDebian#Don.27t_make_a_FrankenDebian](https://wiki.debian.org/DontBreakDebian#Don.27t_make_a_FrankenDebian)

Rats!  That link talks about Debian Stable.  Missed that!
[/URL]

---

### Post by guiverc on 2023-10-08
I'll add some thoughts, most are already covered.

Lubuntu maybe the *lightest* Ubuntu *flavor* out of the box, but how many of us actually use the OS we install without additional apps.

Lubuntu uses the LXQt desktop, which uses Qt5 libraries/toolkit. It'll will be *lightest* when its used with Qt5 apps; so consider the apps you'll want to use.

Xubuntu is next *lightest* of the Ubuntu *flavors*, using the Xfce desktop, which uses GTK libraries/desktop (GTK3 for *supported* releases, but release can impact this). It'll perform best if using GTK apps as the user-apps can share resources with the desktop itself; thus this choice may actually be *lighter* than using Lubuntu if the user is using GTK apps; but it'll be far heavier if using anything using Qt5.

Most Qt5 apps are designed for use with KDE Plasma, a Qt5 desktop, however KDE Plasma also requires KF5 (KDE Frameworks 5) which LXQt doesn't use, so not all Qt5 apps are equal in regards what is *lightest* if using Lubuntu/LXQt.

My point is here is whichever is lightest *out of the box*, only matters if you'll use the system *out of the box* without additional apps; and few do this (*beyond people blogging/pasting on social media*).

Different *flavors* or *distributions* also can make different *config *changes as to what auto-starts, which increases performance of general usage, but it means more memory is being used when *idle* (*don't forget unused memory is wasted memory*). This is what the comparisons often miss, the *less memory used* systems are only that way when nothing is being used, and can be slower when apps are started (*as they have to load into memory what the heavier comparison machine has already done*).

Myself, I'm a Ubuntu and Debian user, and I see them as ~equal. I also have Fedora, OpenSuSE & other installs, and again to me they're ~equal.  The differences I see is what is auto-loaded, and configuration changes I can make myself. Ubuntu includes the *snap *infrastructure by default & Debian does not; that's easily reverse if required for example, but that simple *config* difference is recognizable if RAM comparisons only because it's a running vs. not-running comparison. With a few minutes you can make any GNU/Linux distribution perform equally to another (*in almost all cases; though there maybe circumstances where recompiling is required; eg. to enable security features some disable which reduces RAM; but you excluded security in your question*).


FYI:  I still use old devices on occasion that only have 1GB of RAM; old IBM Thinkpads etc with pentium M CPUs dating back from 2003-2005. The OS matters less than what the end-user does with it. Ubuntu no longer *supports* that *i386* architecture so those boxes now run Debian GNU/Linux.

---

