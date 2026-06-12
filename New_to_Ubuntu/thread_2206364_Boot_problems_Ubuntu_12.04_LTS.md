---
title: "Boot problems Ubuntu 12.04 LTS"
date: 2014-02-18
forum: New to Ubuntu
---

### Post by pgte3 on 2014-02-18
I have this issue from time to time. When I start my machine,  Ubuntu 12.04 LTS  boots and goes to a command line login instead of the "normal" login screen. I have to shutdown or reboot (sometimes more than once) from the command line. The "normal" login screen eventually comes back and I login and work as normal. Any ideas on what is happening? Is there a better way to deal with the issue when it does happen?

---

### Post by Bucky Ball on 2014-02-18
Doesn't fix your problem but may save some time. When you get to the command line login, login and then issue:
```

sudo service lightdm start
```

That should get you to a desktop. Doesn't fix your original problem, but a step forward I hope.

---

### Post by newbietwo on 2014-02-18
Boot your live disc and use boot repair....amazing....

---

### Post by Bucky Ball on 2014-02-18
> **newbietwo said:**
> Boot your live disc and use boot repair....amazing....

? Don't think this has anything to do with it. The machine boots fine most the time, but sometimes it boots to a CLI. Absolutely nothing to do with it not being able to boot from the correct partition or not finding an MBR. Boot Repair is not applicable.

---

### Post by pgte3 on 2014-02-18
I agree with Bucky Ball. The machine boots fine the vast majority of the time. Every now and then it boots to the CLI. What I have been doing is issuing shutdown -H now... then power back on. I am wondering if maybe something is not getting shutdown properly.

---

### Post by fdrake on 2014-02-18
check if this fixes your issue 
```
sudo mv  /var/lib/lightdm/.Xauthority /var/lib/lightdm/.Xauthority_copy
```
restart

if still no luck post here dmesg

---

### Post by Butthead on 2014-02-19
Wouldn't just typing "startx" (after logging in text mode?) work too? :confused:

The reason I'm asking is that my rig did the same thing (I was printing something as the system was crawlng through a slow kernal upgrade process), and got the dreaded "black screen" on the next reboot.  Typing "startex" seemed to get things running again though.

BTW -is "lightdm" the correct thing you enter in Kubuntu when starting and stopping the "X" screen system?  I thought it specifically was "kdm" in Kubuntu?

---

### Post by fdrake on 2014-02-20
> 
BTW -is "lightdm" the correct thing you enter in Kubuntu when starting and stopping the "X" screen system?  I thought it specifically was "kdm" in Kubuntu?

title says :  Boot problems Ubuntu 12.04 LTS, he is most probably using lightdm by default.

---

### Post by Butthead on 2014-02-20
Duh, that makes perfect sense (if I would have stopped and really thought about it). "lightdm" refers to the Unity frontend (if that's what it's refered to?) desktop, right? :oops:

Is Gnome desktop still in use? :?:

---

### Post by MrSteve on 2014-02-20
if using an older system and having boot related problems it may be worth while changing the CMOS battery on the computer
as this battery powers the BIOS for booting into your system, just a thought ...

---

