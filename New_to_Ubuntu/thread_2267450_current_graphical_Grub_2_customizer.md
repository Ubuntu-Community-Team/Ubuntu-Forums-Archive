---
title: "current graphical Grub 2 customizer"
date: 2015-03-01
forum: New to Ubuntu
---

### Post by kithrup on 2015-03-01
(Apologies if this has been covered elsewhere already.)

Is there one? I'm acquainted with the richter one, but wonder if there's a newer one. A little phobic of CLI stuff due to native clumsiness.

Just did a clean install/dual boot of 14.04 LTS and W7 on a new SSD. everything cool so far. Just wanted to trim down the boot menu list so as to reduce possibility for confusion for other family members.

---

### Post by ashmew2 on 2015-06-21
Hi,

The only other alternative I know of is GRUB2 Editor (link: [http://sourceforge.net/projects/kcm-grub2/](http://sourceforge.net/projects/kcm-grub2/)). It's aimed at KDE, so you might need tons of dependencies in case you plan to run it on another Desktop Environment/Window Manager. 

Also, is there something specific that you find lacking with the richter GRUB2 Editor (Grub-Customizer) which is forcing you to find a newer menu customizer?

---

### Post by Bucky Ball on 2015-06-21
Another option. Open a terminal and (nothing here can damage your machine, copy/paste the command):

```
uname -a
```

Take note of the kernel you are using. install Synaptic Package Manager> launch it> search for 'linux image'> click the 'Installed' column twice. Can you see the kernel you found with the command earlier? Don't do anything to that, leave it installed. Click the box next to any other installed images you don't want and mark for complete removal> hit the 'Apply' button.

Once that's complete, open a terminal and:

```
sudo update-grub
```

(you may not need this bit but not harm). Reboot.

---

