---
title: "Possible to increase memory on a windows install?"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by crimlaw on 2008-11-05
When I installed Ubuntu 8.04, I used the windows installer within vista.  Because I was not sure what I was doing at the time, and I did not think I would fall in love with it as much as I have.  As a result, I have to admit that I have no idea how much disc space I set aside during the install.  

Therefore, my first question is, how to I figure this out?  

Next, once I figure this out, if I need to increase my space, am I able to do this easily without a complete reinstall?  

Thanks!!!

---

### Post by LowSky on 2008-11-05
well if you used the wubi installer, ubuntu was installed as if it was a file on vista, so its just using the vista partition **(Someone Correct me if I'm wrong)**, In other word you should have to worry about disk space.

If you actually created a new partition, there an easy way right from Windows. New Patitions show up as new Letter Drives, like E: and should show its entire space allocated

in ubuntu open a terminal and type 
```
df -h
```

---

### Post by crimlaw on 2008-11-05
I am almost positive I used the wubi installer.  so, all is well.  Thanks for clearing that up.

---

### Post by Paqman on 2008-11-05
> **LowSky said:**
> well if you used the wubi installer, ubuntu was installed as if it was a file on vista, so its just using the vista partition **(Someone Correct me if I'm wrong)**, In other word you should have to worry about disk space.


You're a little bit right and a little bit wrong.

Wubi installs Ubuntu onto a virtual drive on the Windows partition, yes, but the size is fixed at installation.

Fear not though, LVPM can expand Wubi virtual partitions. [Instructions here](http://lubi.sourceforge.net/lvpm.html) (scroll down to "Resizing virtual disks using LVPM")

---

