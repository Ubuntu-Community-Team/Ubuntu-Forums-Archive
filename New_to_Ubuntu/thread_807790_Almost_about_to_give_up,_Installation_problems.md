---
title: "Almost about to give up, Installation problems"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Chelives1928 on 2008-05-26
Okay i've been trying to get the new ubuntu installed on a partition of my hard drive.  I  followed the swap,and root directory just like the installation told me. When it finally does install I get to the desktop and start updating.  When I update ubuntu it seems to stall and the computer freezes when it is installing the updates.  is there any reason for this?  Am I doing something wrong?  Do you need to see my hardware setup to help solve the problem?  One other problem I'm having is with sound.  I don't have sound at all and I haven't been able to find a topic that helps.  Thanks to everyone in advance for their help.

---

### Post by twright on 2008-05-26
you may need to open sound from the preferences window and set everything to alsa

---

### Post by Chelives1928 on 2008-05-26
> **twright said:**
> you may need to open sound from the preferences window and set everything to alsa

What do you think about the other problem?

---

### Post by sayakb on 2008-05-26
For sound, install a package called linux-backports-modules.
Plus, it's better to go for a clean install rather than upgrading. Upgrading screwed up my HAL and my Gutsy or Hardy or whatever it became was unusable.

---

### Post by philinux on 2008-05-26
> **Chelives1928 said:**
> Okay i've been trying to get the new ubuntu installed on a partition of my hard drive.  I  followed the swap,and root directory just like the installation told me. When it finally does install I get to the desktop and start updating.  When I update ubuntu it seems to stall and the computer freezes when it is installing the updates.  is there any reason for this?  Am I doing something wrong?  Do you need to see my hardware setup to help solve the problem?  One other problem I'm having is with sound.  I don't have sound at all and I haven't been able to find a topic that helps.  Thanks to everyone in advance for their help.

In a terminal use these one at a time and note any error messages.

sudo apt-get update
then
sudo apt-get upgrade

---

### Post by Chelives1928 on 2008-05-26
Let me go and try both methods.  I'll give you guys an update.

---

### Post by philinux on 2008-05-26
> **Chelives1928 said:**
> Let me go and try both methods.  I'll give you guys an update.

Best to sort out one problem at a time. :)

---

### Post by Xiong Chiamiov on 2008-05-26
I'd rather use [aptitude instead of apt-get]("http://pthree.org/2007/08/12/aptitude-vs-apt-get/"), but it'll do the same thing.

For sound problems, there is quite [a comprehensive guide]("http://ubuntuforums.org/showthread.php?t=205449") over in the multimedia forum.

---

### Post by philinux on 2008-05-26
> **Xiong Chiamiov said:**
> I'd rather use [aptitude instead of apt-get]("http://pthree.org/2007/08/12/aptitude-vs-apt-get/"), but it'll do the same thing.

For sound problems, there is quite [a comprehensive guide]("http://ubuntuforums.org/showthread.php?t=205449") over in the multimedia forum.

Aptitude and apt-get used to be different but these days there's no difference I've been told.

---

### Post by Xiong Chiamiov on 2008-05-26
There are 2 main differences now, aside from aptitude having a separate interface (try just typing aptitude):
1.  Aptitude will automatically get rid of unused packages, while apt-get will notify you that you should run apt-get autoclean.
2.  Aptitude is much better in how you run commands.  For whatever reason, apt-get is more popular, but that first link in my post convinced me to switch.  It just makes more sense.

---

### Post by philinux on 2008-05-26
> **Xiong Chiamiov said:**
> There are 2 main differences now, aside from aptitude having a separate interface (try just typing aptitude):
1.  Aptitude will automatically get rid of unused packages, while apt-get will notify you that you should run apt-get autoclean.
2.  Aptitude is much better in how you run commands.  For whatever reason, apt-get is more popular, but that first link in my post convinced me to switch.  It just makes more sense.

Interesting read.

---

### Post by hyper_ch on 2008-05-26
aptitude won't allow some package removals without removing whole gnome/kde/xfce....

furthermore aptitude also installs the recommended additional packages and not only the required ones. I used to prefer aptitude but now I'm just using apt-get.

---

