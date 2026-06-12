---
title: "Monitor and Resolution problem"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by BuntuFirstTimer on 2008-11-19
I've just installed a new **Nvidia EN8500GT** graphics card and downloaded a stuff to operate this graphics card
.

For some reason, the screen resolution became haywire. I have a Samsung **SyncMaster 920NW** monitor and the Ubuntu 8.04 GUI turned out to have a relatively small, but inconvenient resolution (1024x768) or something. And also, the font looks very squished as well.

I've tried: **sudo displayconfig-gtk**

and then there is no list for SyncMaster 920NW in the model section for configuring the screen.

Any ideas what is going on? Or is there a way to sync my Samsung SyncMaster 920NW with my Ubuntu 8.04?

---

### Post by tuxxy on 2008-11-19
Which driver version did Ubuntu recommend, maybe best to try latest v177 drivers if its not already.

It could maybe fixed in nvidia-settings here you can change res, Hz, colour etc

```
sudo apt-get install nvidia-settings
```

---

### Post by asaellam on 2008-11-19
I am having a similar issue.  I am trying Ubuntu on an older machine to get familiar with it before I deploy it onto my main computer as a replacement to XP.  This machine has an old GeForce2 MX440 graphics card.  After installing Ubuntu, the default display driver would only let me set a max rez of 800 X 600.  Then I activated the driver that was recommended (96.43.09).  After restarting the computer, now my rez is stuck at 640 X 480 and 50Hz.  I have also tried downloading the driver from Nvidia (96.43.07) and when I ran the install, it told me that I have to close the X server in order to install the driver.  This is where I'm stuck.  This is my first time working with Linux, and so far, I haven't found a way to exit from X to get to a terminal.  

If anybody has any suggestions, I would be greatly appreciative.

Thank you.

---

### Post by rggavubt on 2008-11-20
> **asaellam said:**
> I am having a similar issue.  I am trying Ubuntu on an older machine to get familiar with it before I deploy it onto my main computer as a replacement to XP.  This machine has an old GeForce2 MX440 graphics card.  After installing Ubuntu, the default display driver would only let me set a max rez of 800 X 600.  Then I activated the driver that was recommended (96.43.09).  After restarting the computer, now my rez is stuck at 640 X 480 and 50Hz.  I have also tried downloading the driver from Nvidia (96.43.07) and when I ran the install, it told me that I have to close the X server in order to install the driver.  This is where I'm stuck.  This is my first time working with Linux, and so far, I haven't found a way to exit from X to get to a terminal.  

If anybody has any suggestions, I would be greatly appreciative.

Thank you.

You might try this solution 
[http://ubuntuforums.org/showthread.php?t=984137](http://ubuntuforums.org/showthread.php?t=984137)
I had same problem after I installed 8.10 fresh.

---

