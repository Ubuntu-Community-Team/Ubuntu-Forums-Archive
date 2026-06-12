---
title: "Pardus"
date: 2007-01-15
forum: Other OS Talk
---

### Post by deadlydeathcone on 2007-01-15
Since the arbiters of distros seem to hang around here I wanted to point out a fairly unusual one: Pardus, which was just reviewed at [distrowatch]("http://distrowatch.com/weekly.php?issue=20070115#review").

The review goes over it better than I can but in short:

* During updates the package manager (Comar) only downloads the parts of a program that has changed instead of replacing it entirely.

* Is based around a very customized version of KDE, which sports a new control center (Pisi) and a program for easy customization (Kaptan) among other things, and manages to look beautiful as well (especially the icons; and this is coming from a gnome fanatic!)

* Strives to be fast and fairly bleeding edge, and uses a custom, speedier init replacement.

Has anyone tried this yet? I normally don't try out distros, but this looks different enough to be interesting and seems to do KDE justice from a gnomish point of view.

A livecd can be found [here]("http://www.pardus.org.tr/eng/download.html").

---

### Post by SunnyRabbiera on 2007-01-15
Looks interesting, but getting fresh apps for it must be a pain.

---

### Post by deadlydeathcone on 2007-01-15
> **SunnyRabbiera said:**
> Looks interesting, but getting fresh apps for it must be a pain.

Yeah, I definitely wouldn't use this as an everyday desktop. It mainly just seems like an interesting diversion to mess around with on a livecd and likely forget about for a while.

---

### Post by SunnyRabbiera on 2007-01-15
It could be fun for the hobbyests though, it looks good to play around with but yeh I can see it will be totally out of the loop unless it has a package converter like alien

---

### Post by steven8 on 2007-01-15
I'm certain RAV TUX's distro alarm has gone of by now!!  :-)  I think it looks very nice, and will try it out too!!

---

### Post by Jose Catre-Vandis on 2007-03-22
I have installed it three times now, Pardus 2007.1.

First I tried it out on vmware server. Needs a fixed IDE disk of at least 5GB to install. Setup and ran OK, but got tricky when trying to install vmware tools. Looks good and easy for newbies, with the PiSi package manager doing its job nicely.

So tried a HDD install (using same ISO).

Installation went well, but gave me Turkish language all over, even though I selected English. Even changing the locale didn't help as many apps retain their install language. 2nd install did the same thing.

However looks good, easy top use and everything works out of the box

[EDIT]
resolved the language problem.

On installing Pardus I chose to install grub to the root partition and not the mbr, to avoid messing up my current setup. I then copied the pardus grub entry over to my main grub menu.lst file, but I had failed to copy over all of the boot line (as you will see, it is very long!) So copying over the whole line this time, and reboot into Pardus delivered a full english setup.

example menu.lst grub entry for English pardus 2007.1
> default 0
timeout 10
splashimage = (hd0,6)/boot/grub/splash.xpm.gz
background 10333C

title Pardus 2007.1 Felis chaus
root (hd0,6)
kernel (hd0,6)/boot/kernel-2.6.18.8-80 root=/dev/hda7 video=vesafb:nomtrr,pmipal,ywrap,1024x768-32@60 splash=silent,fadein,theme:pardus console=tty2 mudur=language:en quiet resume=/dev/hda6
initrd (hd0,6)/boot/initramfs-2.6.18.8-80 

(May have wrapped on the kernel line! If you see a smiley, replace with a : and a p)

Default gives a US keyboard so you need to edit xorg.conf and change "us" to "gb" in the keyboard section, save, then CTRL+ALT+BACKSPACE to restart X

---

### Post by Raffo on 2007-03-23
Installed it yesterday. I had the same problem with the turkish language because I didn't install grub (pardus includes the option of not install a bootloader, great!)... the default setup is great. Fast boot, nice default look, easy install procedure... I really like this distro. 

Just to say... I installed 3d drivers from the graphical package manager with two or three clicks... then I had to do nvidia-xconfig and restart kdm. Everything worked without problems...

---

### Post by Fopper on 2007-04-10
I have installed Pardus next to my Ubuntu, but I have some problems with it. I installed the grub with Pardus and it took over my grub of Ubuntu. I made a workaround, so the Pardus grub boots Ubuntu, but I would like to use the grub from my Ubuntupartition.. Today I also noticed that Ubuntu doesn't use the swappartition, but Pardus does. How do I configure this?

---

### Post by ThinkBuntu on 2007-04-10
> **deadlydeathcone said:**
> * During updates the package manager (Comar) only downloads the parts of a program that has changed instead of replacing it entirely.
Debian Etch includes that feature with the latest apt-get.

---

### Post by floke on 2007-04-30
Ok so the LiveCD is great (touchpad a bit sensitive but am sure can live with or sort it).
Am going in for an install now...

---

### Post by fastguy on 2007-05-27
Hi,

Just read your comments. I'm currently using:
- Xen Dom0: Ubuntu Gutsy base install with lvm/raid
- Xen DomU: Pardus, English, daily use

- Pardus installs in English if you select it from the boot menu when installing
- Don't think it will go away as it is built by the Scientific & Technologic Research Council of Turkey. It's developed to be used in Government and Military offices besides the public, so has a goal to accomplish.
- Once you try, you can't leave :)
- Near fresh versions of most popular applications are in the package repositories: pardus-2007 and contrib. An application called "pisibul" (means findpisi in Turkish) can also search for beta/test/development/playground repositories to be used at your own risk.
- There's currently around ~5000 packages and expanding.
- Has some interesting ideas as mentioned by this article "Rethinking the Linux Distribution"
[http://www.onlamp.com/pub/a/onlamp/2007/05/10/rethinking-the-linux-distribution.html?page=1](http://www.onlamp.com/pub/a/onlamp/2007/05/10/rethinking-the-linux-distribution.html?page=1)
- Has an advanced init system and package management system.
- You can send an email to pardus-devel or pardus-users mailing lists in English and you'll quickly get an answer.

Best regards,

Fastguy

---

