---
title: "I killed my GUI!"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by age99 on 2008-11-10
I accidentally removed most of the ubuntu packages/programs that were available with the original installation while trying to re-install libx11 files.  
Can somebody help me get my GUI back?  I Synaptic re-installed, and I tried to install the edubuntu-desktop and associated packages, but I still can't see toolbars etc.

---

### Post by age99 on 2008-11-10
Can anybody help me restore my GUI?  Do I need a re-boot?

---

### Post by mtausig on 2008-11-10
Installing the ubuntu-desktop meta-package with
sudo apt-get install ubunut-desktop
should install all the neccesary stuff.

---

### Post by hyper_ch on 2008-11-10
> **age99 said:**
> Can anybody help me restore my GUI?  Do I need a re-boot?
It is not polite to bump a thread less than 24h after posting!

---

### Post by mapes12 on 2008-11-10
This is what I would do. Others may have alternative solutions.

Make sure you have /home on a separate partition to save all your files and stuff. If it isn't on a separate partition then here's a HowTo: [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

Then reinstall your system from your installation CD onto the other partition for your /(root& system) files.

The state of your current system will determine what you can do. In the future, to save the packages/applications you have on your system you may want to look at aptoncd. Home page here: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) and can be loaded onto your system via System>Administration>Synaptic Package Manager then search for it.

Then if you break your system again and having the above configuration / backup tools, it will be an easy job to get it running again.

---

### Post by age99 on 2008-11-10
Thanks mtausig
That solved it:
> sudo apt-get install ubunut-desktop 

---

