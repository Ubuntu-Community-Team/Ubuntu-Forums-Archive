---
title: "Going into terminal without X?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by gogogo111 on 2008-04-24
Ok, I just installed Ubuntu 8.04 64-bit. My specs are C2Q, 2gb ram, 8800gt.

I downloaded the 64bit nvidia driver, and it says I need to install the driver without X. How to I get to the terminal without using X? If anyone could answer that'd be great. Thanks. :)

---

### Post by gogogo111 on 2008-04-24
Bump

---

### Post by gogogo111 on 2008-04-24
Actually I just want to say. I went to the Hardware drivers again, and I can now check the box. Before it said "not in use" but the check box was checked. I may report that bug to the devs.

---

### Post by neurostu on 2008-04-24
To install without X switch a virtual terminal:

CNTL+ALT+F1

Then run the installer!

---

### Post by zvacet on 2008-04-24
```
sudo /etc/init.d/gdm stop
```

---

### Post by gogogo111 on 2008-04-24
Thanks guys, but I was able to get the hardware driver working from ubuntu. Thanks.

---

### Post by starcannon on 2008-04-24
```
CTRL-ALT-F1
login
password
sudo /etc/init.d/gdm stop                               *stop x and the gnome desktop
cp /etc/X11/xorg.conf /home/yourhome/xorg.conf.bak      *back up the old xorg file
sudo rm /etc/X11/xorg.conf                              *remove the old xorg file
cd /some/directory/where/NVIDIA*.run                    *enter directory where your driver is
sudo chmod a+x ./NVIDIA*                                *make the driver executable
sudo apt-get install build-essentials                   *grab additional requirements
sudo ./NVIDIA*                                          *run the driver installer
sudo /etc/init.d/gdm start                              *start x and gnome up again
``` 
Now to get the driver to run every boot:
```
Alt-F2
gksudo gedit /etc/modules
type in the word "nvidia" without the quotes
save
exit.
```

If all went well you should now have a loverly looking desktop, if not we backed up your old xorg.conf and can restore it back to how it was by.
```
sudo cp /home/yourhome/xorg.conf.bak /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

---

