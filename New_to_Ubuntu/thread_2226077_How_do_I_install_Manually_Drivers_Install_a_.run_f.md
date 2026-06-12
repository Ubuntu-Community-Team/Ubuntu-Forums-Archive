---
title: "How do I install Manually Drivers/ Install a .run file"
date: 2014-05-25
forum: New to Ubuntu
---

### Post by balkrish999 on 2014-05-25
Hello, 

How do i manually install drivers?  

I have downloaded the .run file and have my nivdia drivers.

I have the actual file itself 

how do I install it?

Thank You Very much :D


--(
The Main problem i am having is i installed Ubuntu 14 on dual boot, but since i have AMD and nivdia driver,   everything works fine for the first 5 minites BUT THEN everything becomes super super slow, and freezes, thats why i need a quick method to install the drivers as i only have 3-5 minutes )

Thank You

---

### Post by oldrocker99 on 2014-05-25
OK, first open a terminal and type:
```
sudo nano /etc/X11/default-display-manager
```

This will tell you which display manager you're using (*dm). Then press CTRL-ALT-F1 and enter your username and password. Then (assuming, for this example, that your display manager is lightdm), type:

```
sudo service lightdm stop
sudo apt-get install dkms (you'll be glad you did when there's a kernel update)
cd /path/to/.runfile/
sudo sh *.run
sudo service lightdm start
```

Then reboot and the driver should be installed. 

Of course, you'll probably get better results using the "Hardware Drivers" program.

---

