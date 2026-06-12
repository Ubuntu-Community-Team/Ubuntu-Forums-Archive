---
title: "stop automounting other partition 17.10"
date: 2017-11-07
forum: New to Ubuntu
---

### Post by rburkartjo on 2017-11-07
any idea how to stop. never had problem before/tks

---

### Post by #&amp;thj^% on 2017-11-07
What is the DE?

```
echo $DESKTOP_SESSION
```

[s]I just Love it when someone ask's for help and then just parks there. (Consider other's time please )[/s]
If you are using Gnome follow this:
This is probally the easyist method to use:
Open the terminal and run:

```
gnome-disks
```
A Window will open.
Now on the left side pick the Disk or partition you want to change.
Now in the main Window towards the bottom you will see a Cog...Cilck That.
Now look down that dropbox and look for "Edit Mount Options" and click that.

At the Top of that Window you see "User Session Defaults" toggle that so you have more options.
And Simply un-tick Mount at system startup.
Done.
Screenshots Added for Clarity.
There is also the hard way using blkid to retrieve the partition UUID:

```
sudo blkid 

```
If you want that method let me know and I will explain it more.

---

### Post by rburkartjo on 2017-11-09
this worked for me
[https://askubuntu.com/questions/191527/disable-auto-opening-nautilus-window-after-auto-mount](https://askubuntu.com/questions/191527/disable-auto-opening-nautilus-window-after-auto-mount)

answer 71

---

