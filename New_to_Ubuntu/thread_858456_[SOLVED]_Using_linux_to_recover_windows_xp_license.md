---
title: "[SOLVED] Using linux to recover windows xp license key?"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by malathion on 2008-07-13
I work in a PC repair shop and we use ubuntu and knoppix boot disks for various service jobs. One very annoying situation is when the customer needs us to reinstall windows but has lost his license sticker. In this case we have to follow a very laborious process of removing the hard drive from the system, installing it in a local box, and running a poorly designed application that opens the registry hive.

Is there any way to duplicate this process on a livecd? This would be much simpler. Thanks for any advice.

---

### Post by bumanie on 2008-07-13
Not sure about being able to do it from linux, but there is a freeware program called "Magic jellybean" that can do that. You could run it off a usb pendrive.

---

### Post by 91004 on 2008-07-13
I don't know if this would work or not, but have you tried using Magical Jelly Bean Keyfinder?

I'm pretty sure it will work under the Wine.........

[http://www.magicaljellybean.com/keyfinder.shtml](http://www.magicaljellybean.com/keyfinder.shtml)

This is a wonderful little program and it is free!!!

---

### Post by malathion on 2008-07-14
Thanks for the replies. Magic jellybean is what we use. But as I explained above, it requires me to either (A) get into windows on the host machine, which I cant do half the time or (B) pull the drive from the computer and put it into another system, which is both laborious (when you have to do it many times a day for various jobs and various reasons) AND uses up valuable time on the recovery boxes which should be used for time-consuming data recovery jobs. 

Maybe there is a way to get this to work in wine? Other than that, what I really need is a linux app that duplicates that functionality.

---

### Post by malathion on 2008-07-17
Bump. I just ran into a system with this problem that is running a RAID configuration. Due to the setup, it may be impossible to obtain the key unless I can get a way to do this in linux, thus necessitating the customer to purchase another copy of windows. Anyone?

Edit: I was able to extract the key by booting into knoppix and copying the windows folder to our fileserver and loading the hive with magic jellybean. I think this will be our solution to these problems for the time being. Thanks everyone.

---

### Post by sugardaddy_mrbig on 2009-10-21
Also reference this post, where I was able to use MJBKF to get the Windows XP key out of a hosed computer by copying the hive (registry) files to a USB stick.

[http://ubuntuforums.org/showthread.php?p=8140473#post8140473](http://ubuntuforums.org/showthread.php?p=8140473#post8140473)

---

