---
title: "Question regarding Install Partition sizes showing up Incorrect"
date: 2014-10-21
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2014-10-21
Hello, 
Thanks for reading. Please see screen shots. When I oppen GParted,  my Drives all show the correct Size. However, when I go into Install mode (launching each from the Desktop) 
I go to install the distro, I choose "somethiung else" (so that I can pick, the drive to install to). 

The drives then are showing in "MB" vs. "MiB"  (however "ALL" drives are doings this). Also, it's not "SEEING" the "Device for Boot loader" 
the 500GB drive is "Drive 1"

Drive 2 is a 1TB drive partictioned into 376/634

Any suggestioins? Screen shots attached.
-----PS---can't see in this screen shot, but I do have the 376 set up as the "ROOT" drive.

---

### Post by deadflowr on 2014-10-21
I'm confused about what the actual question is.

But aside from that, the install screenie shows that /dev/sda is set to install the bootloader on...

---

### Post by ajgreeny on 2014-10-21
So apart from the difference between MB and MiB, what is your problem?

---

### Post by whereismymindat2 on 2014-10-21
@ajgreeny...THANKS! (pardon the sp's..above) the issue, the size is incorrect, I have 2-drives...500GB and a 1TB---the one TB is the 374/626-partitions. (but when I launch the installer----it shows up in MB---thus of course too small to install on). and incorrect size.

---

### Post by deadflowr on 2014-10-21
The 1tb, I assume, is /dev/sdb.
Partitions /dev/sda7 and /dev/sda8 are on the 500GB drive,  seen as /dev/sda.
Scroll down the installers partition table to see the /dev/sdb drive, and in gparted click on the button in the top right corner to switch viewable hard drives.

---

### Post by whereismymindat2 on 2014-10-27
all. thank you very much!!, for assitance. much appreciated.

---

