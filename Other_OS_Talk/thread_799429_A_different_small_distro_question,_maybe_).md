---
title: "A different small distro question, maybe? :)"
date: 2008-05-19
forum: Other OS Talk
---

### Post by DaveAK on 2008-05-19
So I'm researching the various options for a small distro, and I've got plenty to choose from, but here's my question :

Most of the requests or advice for small distros are based around small HDD and low RAM, however with my set up I have 8GB HDD and 1GB RAM, but only a 500MHz processor, (it's a Nano-ITX board with solid state drive), so installed footprint isn't a problem, but what is the best way to get the most performance from the CPU?

My plan as it stands is to go with a base install of Ubuntu, and then add xorg, a WM/DE and that's probably it.  Maybe a couple of other items, but this will be a single app machine, which brings me on to another question, that may be better suited for a different forum.

One of the items I need is a TouchScreen driver.  The driver is available as a packaged RPM for RedHat, Fedora and SuSE, or as source for 2.4 and 2.6 kernels.  I plan on setting up an identical system as a virtual machine on my workstation, so if I download and compile the drivers on this VM, how would I transfer them to the single app box?  Do I have to package them in someway, and then install from the package?

Lastly I'll be writing the app myself, but with only 500MHz CPU not sure of the best way to do this.  Python is supposedly the easiest to learn, (I do have plenty of programming experience), but it's interpreted, Java would require the JavaVM, but reportedly isn't much slower than C++.  Would Python be too much to ask of 500MHz?

---

### Post by kerry_s on 2008-05-19
a debian base build up would make that fly, if you use light programs.
[http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso)

something like:
apt-get install xorg jwm menu mc
update-menus
exit
startx

then just keep building up from there, use rungetty for auto log in & startx in bash_profile

trimmed instructions, you sound like you know what to do. let me know if you need more detail.

i run on 450mhz 256mb ram, so your should smoke.

PS: yes, there is a big difference between ubuntu base and debian. debian is faster, more stable, a bit smaller, there's not to much tie together programs, cpu specific kernel(i686 vs generic), etc...

try them both, it's fast.

---

### Post by DaveAK on 2008-05-19
Thanks!!

It just so happens that I downloaded Debian 4.0 earlier, so maybe I'll just try that first.  I like the sound of your suggestion for rungetty, I'll need to look into that one.  And in your screenshots what do you install for the stats in the upper right corner?  That will be useful while I'm testing out the performance.

---

### Post by Milk &amp; Toast &amp; Honey on 2008-05-19
> **DaveAK said:**
> ...  And in your screenshots what do you install for the stats in the upper right corner?  That will be useful while I'm testing out the performance.

It's conky. There's some tutorial and examples for conky setup in the Tutorials section.
[http://ubuntuforums.org/showthread.php?t=205865]("http://ubuntuforums.org/showthread.php?t=205865")
[http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")

---

### Post by DaveAK on 2008-05-19
> **Milk & Toast & Honey said:**
> It's conky. There's some tutorial and examples for conky setup in the Tutorials section.
[http://ubuntuforums.org/showthread.php?t=205865]("http://ubuntuforums.org/showthread.php?t=205865")
[http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865")
Thanks!!  I'm bad at keeping up with this stuff. :D

---

### Post by Milk &amp; Toast &amp; Honey on 2008-05-19
> **DaveAK said:**
> Thanks!!  I'm bad at keeping up with this stuff. :D

No problems. Well, with thousands of applications available on the repo, I think it's a "problem" to keeping up with this stuff :p

Good luck with your research.

---

### Post by kerry_s on 2008-05-19
> **DaveAK said:**
> Thanks!!

It just so happens that I downloaded Debian 4.0 earlier, so maybe I'll just try that first.  I like the sound of your suggestion for rungetty, I'll need to look into that one.  And in your screenshots what do you install for the stats in the upper right corner?  That will be useful while I'm testing out the performance.

yeah, rungetty does the log in for you, so when you power on or reboot it can be made to go straight to the desktop.

install rungetty:
**apt-get install rungetty**

then you need to edit /etc/inittab
(not sure of your preferred editor, so i'll use xedit it comes with xorg)
[B]su
xedit /etc/inittab

1:2345:respawn:/sbin/getty 38400 tty1
to
1:2345:respawn:/sbin/rungetty tty1 --autologin user[/B]

change "user"(aka: DaveAK) to be your login name. click save 2x & quit.

as your regular user, not root:
**xedit ~/.bash_profile**
put 
**startx**
at the bottom

(i know mine says xinit, i have mine set to skip startx, but i always start with startx till i get things set up)

---

### Post by darrelljon on 2008-05-19
Same happened to me, e-mailed the admin, never got a reply so gave up.

---

### Post by kerry_s on 2008-05-19
> **darrelljon said:**
> Same happened to me, e-mailed the admin, never got a reply so gave up.

????

---

### Post by will1911a1 on 2008-05-19
> **kerry_s said:**
> ????

He posted in the wrong thread.

---

