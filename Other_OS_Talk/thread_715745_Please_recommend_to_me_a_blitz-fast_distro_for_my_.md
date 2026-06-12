---
title: "Please recommend to me a blitz-fast distro for my notebook"
date: 2008-03-05
forum: Other OS Talk
---

### Post by shuttleworthwannabe on 2008-03-05
I realise this subject has been discussed. I have a 3 year old notebook: HP Compaq nw8240, 2.13GHz Centrino, ATI V5000, 2G RAM, 100G HDD 7200RPM (I upgraded as you can see to highest specs possible when I bought in 2005).
I have Gutsy Gnome running on it, but with time it is becoming sluggish in responding..much like windows getting bloated with each new installation of programs, but not as bad as Windows. Anyway, I am looking to make this machine a full-linux, but want to benefit from these high-end specs. Also, not Ubuntu recognizes all my hardware perfectly weel, and I want to stick with debians rather than rpm distro's (rpm do not like my hardware for some reason).

What distro would you recommend that would run really fast on my system. I have tried Xubuntu, but again, after I installed some gnome apps (like printing gui) I felt the system slowing down. It is snappy immediately after first install, but returns to sluggish behaviour after some use. Sluggish, it the sense, it is slow on opening apps, responding to window chnages, bootup, etc.

Could anyone recommend me a distro?
-? Linux Mint
-? gOS (enlightenment)...going to GNOME I beleive??
-? ZenWalk?
-? Wolvix?
other/

Many thanks for the help,

S

---

### Post by wieman01 on 2008-03-05
I'd try PuppyLinux perhaps.

[www.puppylinux.org]("www.puppylinux.org")

---

### Post by kpkeerthi on 2008-03-05
Zenwalk 5 or Arch + XFCE

---

### Post by Changturkey on 2008-03-05
You can experiment with Puppy though, the standard ISO is about ~100 MB, and the puplets increase from that.

---

### Post by lespaul_rentals on 2008-03-05
Wolvix and Dreamlinux are my personal favorites.  Wolvix is Slax-based and Dreamlinux is Debian-based, so no RPM is involved.

---

### Post by drcranium on 2008-03-05
I like Wolvix a lot also.  The last time I used it, the installer was experimental though.  If you want to jump into it, Arch with xfce4.

---

### Post by mips on 2008-03-06
Try Arch.

I run Arch+KDEmod on a hp nx6110, 1.4GHz celeron, 512MB ram which is way worse than your laptop and arch is snot fast on it.

---

### Post by kadath on 2008-03-06
Zenwalk or Arch.

---

### Post by shuttleworthwannabe on 2008-03-06
I just checked Arch, that is a KDE based distro, so what makes it faster than KDE (Kubuntu, or others??)
Just curious

---

### Post by Hallvor on 2008-03-06
Sidux should be pretty fast.

---

### Post by deepclutch on 2008-03-06
Arch Linux baby!:p

---

### Post by mips on 2008-03-06
> **shuttleworthwannabe said:**
> I just checked Arch, that is a KDE based distro, so what makes it faster than KDE (Kubuntu, or others??)
Just curious

for one Arch is optimised for processor i686 and actually has no support for older processors. With arch you basically install everything yourself so it does not have all the bloat of a out of a box distro.

Also have a look at KDEmod which is very modular and makes for a lean kde install. [http://kdemod.ath.cx/](http://kdemod.ath.cx/)

---

### Post by djbsteart1 on 2008-03-06
Arch or Dreamlinux, if you are happy with making yourself a distro then go for arch, otherwise try dream, they have just realised rc1 for version 3 and you can choose xfce or gnome, I found the xfce very fast.

---

### Post by chris4585 on 2008-03-06
> **shuttleworthwannabe said:**
> I just checked Arch, that is a KDE based distro, so what makes it faster than KDE (Kubuntu, or others??)
Just curious

Arch is not kde based, arch you build, you can make it have, kde if you want, xfce, gnome, fluxbox etc... you pretty much make the distro on your computer you should check out the arch beginners wiki

Also.. its super fast, no bloat, you install the arch base and add on whatever you want, there's another post in other os talk > arch that talks about what does make arch faster

---

### Post by jseiser on 2008-03-06
install Crux - Its the fastest distro I have ever used

you could also try sourcemage linux.

---

### Post by cardinals_fan on 2008-03-06
Zenwalk.  It should run crazy fast on that hardware.  Plus the forums are fabulous and the Zen team makes great use of Xfce's power.  Package management is weak but improving fast.

---

### Post by djbsteart1 on 2008-03-07
> **cardinals_fan said:**
> Zenwalk.  It should run crazy fast on that hardware.  Plus the forums are fabulous and the Zen team makes great use of Xfce's power.  Package management is weak but improving fast.

This was what I found, bar the package management it is one of my favourite distro's, and fast doesnt really describe it

---

### Post by Extreme Coder on 2008-03-07
What do you mean by rpm's do not like my hardware? :D
Try Mandriva :)

---

### Post by djbsteart1 on 2008-03-07
> **Extreme Coder said:**
> What do you mean by rpm's do not like my hardware? :D
Try Mandriva :)

+1, I have 2008 on a p4 2.4GHz with only 512Mb of ram, so you should be able to run it fine. I don't see how hardware can affect package management on that scale.

---

### Post by MONODA on 2008-03-07
try out arch. Download the core iso. It takes some time to learn and get used to but its worth it. If you dont want to take so much time into setting up your system, then try Zenwalk its great. theres also wolvix.

---

### Post by chris4585 on 2008-03-07
crunchbang would go zoooom! on it :)

---

### Post by kerry_s on 2008-03-07
looking for speed, stay away from the distro de bloat, go custom install, use lite applications known to be fast, install only what you use. wm's are not tied to everything, they don't slow down. avoid distro's that customize alot of feature's, that can make things not function properly.

i recommend a debian custom install using the net installer.
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-businesscard.iso)

do a base install, that means when it gets to the package selection part, uncheck both.

log in as root
apt-get install xorg gdm synaptic (wm-you-want) (what-ever-else)
reboot(ctrl+alt+delete)
log in as your user, open synaptic, continue getting what you want.

example:
apt-get install xorg gdm synaptic icewm rox-filer leafpad iceweasel
or maybe fluxbox
apt-get install xorg gdm synaptic fluxbox rox-filer leafpad iceweasel
or you might want that really empty look
apt-get install xorg gdm synaptic openbox rox-filer leafpad iceweasel
i prefer jwm
apt-get install xorg gdm synaptic jwm rox-filer leafpad iceweasel

---

### Post by MattBD on 2008-03-08
Fluxbuntu is pretty fast. I've only ever tried it in VirtualBox, but it was fast there.

---

