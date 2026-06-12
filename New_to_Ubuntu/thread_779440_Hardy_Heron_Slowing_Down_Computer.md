---
title: "Hardy Heron Slowing Down Computer"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by licorice_sticks on 2008-05-02
Hello! I recently had a friend install Vista and Ubuntu on my new computer. A year later, I decided to upgrade to Hardy Heron which is wonderful--it fixed that moronic adobe flash issues which prevented me from watching any videos on the net properly (I used gnash...didn't work either). 

ANYWAY, I would like to keep Hardy but it is slowing down my computer and I don't know why. When I switch work places, it's slow. When I type words (like I am now), it's not as fast as it was with the previous Ubuntu version. Opening and closing windows is not quite...it slowly fades in and out. The compiz-fusion is also not running as quickly as it did before.

This is my computer info:
             total       used       free     shared    buffers     cached
Mem:          3041       1882       1159          0         84       1383
-/+ buffers/cache:        414       2627
Swap:         2957          0       2957
Total:        5999       1882       41

I doubt space is the problem though. I went on the IRC and was told to search my computer for problems by using 'dsmegs' and the only thing I could find was this error:

[17562.317613] Buffer I/O error on device sdg1, logical block 1548387
[17562.317619] lost page write due to I/O error on sdg1
[17562.702503] sd 8:0:0:0: [sdg] READ CAPACITY failed
[17562.702510] sd 8:0:0:0: [sdg] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[17562.702515] sd 8:0:0:0: [sdg] Sense not available.
[17562.702944] sd 8:0:0:0: [sdg] Write Protect is off
[17562.702947] sd 8:0:0:0: [sdg] Mode Sense: 00 00 00 00
[17562.702950] sd 8:0:0:0: [sdg] Assuming drive cache: write through

I'm not sure what it means though. Another option that was given to be was to do a clean upgrade instead of a normal upgrade. I have a copy of everything in my /home folder in a USB so I don't mind everything getting deleted. But when everything IS deleted, does that mean I have to reinstall compiz-fusion? Reinstall all those synaptic software? I also have vista running on another partition (my friend installed it for me. I'm too nooby to do it myself) and Vista is running fast. 

Please help.

---

### Post by nowshining on 2008-05-03
yes, u'll have to re-install all ur software that you installed from the repos.

Also have you tested your HD yet, it could be ur HD going out and an immediate backup is recommended and of course getting a newer HD is also recommended - the sooner the better.

---

### Post by licorice_sticks on 2008-05-03
> **nowshining said:**
> yes, u'll have to re-install all ur software that you installed from the repos.

Also have you tested your HD yet, it could be ur HD going out and an immediate backup is recommended and of course getting a newer HD is also recommended - the sooner the better.


What does it mean to test my HD (hard drive)? How would I go about doing this? I don't think it's necessary. My computer is new and everything. It's frustrating watching movies on a slow computer. I took another suggestion which was to delete the old copy of ubuntu. I regret having done that now because I have no back up. What are the steps I can take to do a clean upgrade of Hardy Heron (even though I have already installed Hardy Heron)?

Thanks for responding!

---

