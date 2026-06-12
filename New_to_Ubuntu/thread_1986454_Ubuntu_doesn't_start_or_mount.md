---
title: "Ubuntu doesn't start or mount"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by mk04 on 2012-05-24
When I try to start my laptop Ubuntu goes into a busybox error. When I try to access my files via a LiveCD, I get dbus error when it tries to mount the filesystem. I'll post pictures of the error. Specs are in signature.

---

### Post by mk04 on 2012-05-25
Btt....any help would be greatly appreciated! Thank you

---

### Post by mapes12 on 2012-05-26
I've done some Googling about dBus errors and it looks as if your system is screwed. Unless you are quite technical then it looks to me like a fresh install is called for. But as you say getting your files off the machine is proving to be a problem. Given that you can get the machine going from a live CD try getting into your files from Nautilus but with root permissions. Go the the Terminal ```
gksu nautilus
```and see if you can get to your stuff that way.

---

### Post by coffeecat on 2012-05-26
One thing you might want to try is to check the filesystem of your Ubuntu system. Boot up with the live Ubuntu CD, don't try to mount the Ubuntu root partition from nautilus, but open Gparted. Right-click on your root partition and select "check" and then click on apply. Do the same with your home partition if you have a separate one. If it finds filesystem errors it will attempt to repair them.

You also need to exclude the possibility of a failing hard drive. While you are in the live session, close Gparted and open Disk Utility. Highlight your laptop internal HD in the left pane and then look for SMART status in the right pane.

---

### Post by mk04 on 2012-05-26
Thanks for the help. I'll try it out and post the results. FYI I'm dual booting with windows vista which is also corrupted, unrelated, but I can still access the files via Ubuntu liveCD. I'm waiting for the Ubuntu 12.04 to be shipped to me, I'm using my 10.04 Live CD for now.

---

