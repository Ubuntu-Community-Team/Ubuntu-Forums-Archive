---
title: "Cannot get into the system after upgrade to 11.10"
date: 2011-09-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ziyuang on 2011-09-01
I am using VirtualBox 4.1.2. My host OS is Windows7 and the guest OS was Ubuntu 11.04. Just now I upgraded my guest OS to Ubuntu 11.10 via

```
sudo do-release-upgrade -d
```

And then I rebooted the VM, entered into recovery mode, mounted the ISO, ran VBoxLinuxAdditions.run and rebooted again. Now I am stuck in a screen saying that Ubuntu is checking battery state which refuses to go on:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201237&stc=1&d=1314905324[/IMG]

If I run into recovery mode, the screen will be like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=201239&stc=1&d=1314905324[/IMG]

Can anybody give hints to help me out? Thank you~

---

### Post by mörgæs on 2011-09-01
We are happy that you are helping to test 11.10, but please remember that when doing so, you are the one helping people (by reporting bugs), not the other way around. 

Best is to see in this forum
[http://ubuntuforums.org/forumdisplay.php?f=403](http://ubuntuforums.org/forumdisplay.php?f=403)
whether the problem is known already. If it is new, please open a bug report in Launchpad.

---

### Post by ziyuang on 2011-09-01
I've run ```
sudo dpkg-reconfigure gdm
```, which enable me to re-select the display manager from GDM to LightDM. Everything is OK now.

---

### Post by dino99 on 2011-09-01
remove gdm
and install lightdm-gtk-greeter if not

---

