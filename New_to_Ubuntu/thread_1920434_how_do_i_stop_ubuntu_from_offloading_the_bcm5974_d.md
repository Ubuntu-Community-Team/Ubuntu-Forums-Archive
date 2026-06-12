---
title: "how do i stop ubuntu from offloading the bcm5974 driver for my macbook trackpad?"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by thebestofall007 on 2012-02-04
Hello, how do I prevent Ubuntu from offloading the bcm5974 kernel module driver that enables my macbook pro's (early 2008
) trackpad to work? Whenever the module gets offloaded/removed by udev (per my findings in xorg.0.log), my trackpad stops working and i have to open a terminal and type ```
sudo rmmod bcm5974 && sudo modprobe bcm5974
``` to enable it again. This gets annoying and i was wondering if there is a permanent fix for this? I am using Linux Mint 9/Ubuntu Lucid (both have the problem).

---

### Post by thebestofall007 on 2012-02-04
Hello, how do I prevent Ubuntu from offloading the bcm5974 kernel module driver that enables my macbook pro's (early 2008
) trackpad to work? Whenever the module gets offloaded/removed by udev (per my findings in xorg.0.log), my trackpad stops working and i have to open a terminal and type ```
sudo rmmod bcm5974 && sudo modprobe bcm5974
``` to enable it again. This gets annoying and i was wondering if there is a permanent fix for this? I am using Linux Mint 9/Ubuntu Lucid (both have the problem).

---

### Post by drs305 on 2012-02-04
Duplicate thread. 

Threads merged.

---

### Post by overdrank on 2012-02-04
My apologies drs305, I have merged the thread at the same time. :oops:
Please do not create multiple threads on the same issue.

---

### Post by thebestofall007 on 2012-02-04
> **overdrank said:**
> My apologies drs305, I have merged the thread at the same time. :oops:
Please do not create multiple threads on the same issue.

whats going on here?

---

### Post by drs305 on 2012-02-04
> **thebestofall007 said:**
> whats going on here?

You made duplicate posts on the same topic. Two moderators attempted to rectify the situation. One of them closed the duplicate while the other was merging the two. Unfortunately both actions occurred at the same time.

I'll clean up the thread by deleting (now) extraneous posts and hope you get an answer to your original post.

---

