---
title: "Something is just not right..."
date: 2008-08-05
forum: New to Ubuntu
---

### Post by nodnarb83 on 2008-08-05
I have a Belkin F5D8073 wireless N ExpressCard that I am trying to set up.  I installed ndiswrapper and I installed the windows XP driver rt2860.inf file.  When it shows if the hardware is present it says no and when I click on configure network a wireless option does not even come up.  Do I need to install something else in order to see the wireless option?  Where have I gone wrong?  I found through browsing the forums that others have got this card to work.

---

### Post by spiderbatdad on 2008-08-05
could you list the commands you ran to install? Or link to any guide you followed?

---

### Post by nodnarb83 on 2008-08-05
Here is the link to the HowTo that I followed.  Apparently it should "just work"

[http://ubuntuforums.org/showthread.php?t=539533](http://ubuntuforums.org/showthread.php?t=539533)

Oh, and I also installed it from the Synaptics Package Manager.

---

### Post by spiderbatdad on 2008-08-05
I'm not an expert at setting up wireless drivers, as mine has always worked, however I would have expected to see some commonly used commands like:
```
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist
```to disable the bcm drivers.Then reboot is required.

And:```
 sudo ndiswrapper -i ~/drivers/drivername.inf
 sudo depmod -a
 sudo modprobe ndiswrapper
```

Also the line:
ndiswrapper

usually needs to be added to /etc/modules.

I'm sorry you are having trouble with this.
Perhaps the package ndis-gtk will provide a graphical tool to ease the installation of this driver.

---

### Post by nodnarb83 on 2008-08-05
I have already done all of those commands that you posted as well.  :sad:

One question, though, you mentioned the package ndis-gtk.  I see that I already have that installed but I am not sure if I have used it.  Is it the Windows Wireless Drivers tool under System or is that the actual ndiswrapper tool.  If not, how do I go about using ndis-gtk.

---

### Post by spiderbatdad on 2008-08-06
Yes windows wireless driver tool.

---

