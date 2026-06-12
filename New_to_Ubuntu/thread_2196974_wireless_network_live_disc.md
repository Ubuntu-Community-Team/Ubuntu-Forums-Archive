---
title: "wireless network live disc"
date: 2014-01-01
forum: New to Ubuntu
---

### Post by Caril Chasens on 2014-01-01
Using the 12.04.2 install ubuntu disc as a live disc, the wireless network which is available is not recognized. Is there any way I can get online with the live disc session?
I live in a remote location, rely on internet for communication (no phone available) and am very reluctant to proceed with upgrading from the 10.04 I have to the supported 12.04 without being able to use a live disc session as a way of getting online in a temporary worst case scenario. ( I also have the 12.04 alternate disc to upgrade from.)

---

### Post by grahammechanical on 2014-01-01
When you say that wireless network is not recognised do you mean that when you click the Network Icon in the top panel your wireless network access point is not in the list? Are any wireless access points in the list? If the live session is not seeing any wireless access points in range and from where you say you live there just may not be any neighbours with wireless routers in range, but it could indicate that you need a driver for your wireless adapter.

Can you make a wired connection to your router? If you need a driver then you will need wired access to that router to get it. In the live session please run this command

```
nm-tool
```

Please paste the output so we can see it. Another command the output of which it would be useful to see is

```
rfkill list
```

You see it could also be possible that the wireless adapter is switched off either in hardware or by software.

Regards.

---

### Post by Caril Chasens on 2014-01-02
Grahammechanical, thanks... Right now I am running 10.04...
When I was using the live disc, when I clicked the Network Icon in the top panel my wireless network access point was not listed. (No close neighbors, live way up in the bush).
I ran nm-tool to scope out the wireless network I am using successfully NOW, for comparison, and also rfkill list (nothing blocked). Would have to wait until I am booted up on the live disc to try the commands there, but first I will try the thing wired. Hope that works, but I may get impatient and go ahead with the upgrade. I may well need the nm-tool and rf kill commands if the upgraded system won't see my wireless.

---

### Post by chkneater on 2014-01-02
First, what wireless adapter are you using?  Is it a newer Belkin?

---

