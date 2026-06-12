---
title: "Livepatch is messed up...?"
date: 2022-11-18
forum: New to Ubuntu
---

### Post by yatski on 2022-11-18
So, for a second day in row Livepatch(and Software Updater, regarding Livepatch) claim they've applied 47 updates since last restart. (I shut my computer for the night.)

Should I get worried and am I the only one Livepatch user getting this message?

---

### Post by grahammechanical on 2022-11-20
I do not use Livepatch. It is my understanding that the purpose of Livepatch is to install software updates without requiring a reboot. This notification shows that the system is working. Have you restarted twice in the last two days/nights? Did you expect not to see the message after the second restart? It might be part of the Livepatch program to repeat the notification if there are additional restarts within in a short period of time. It seems to me that Livepatch expects infrequent restarts.

You cannot the the only one getting this message. Unless there are settings that can be altered to produce this effect.

Regards

---

### Post by yatski on 2022-11-20
> **grahammechanical said:**
> Have you restarted twice in the last two days/nights? Did you expect not to see the message after the second restart? It might be part of the Livepatch program to repeat the notification if there are additional restarts within in a short period of time. 

Yes, I've restarted my computer several times during this time I've had issue with Livepatch.
This is just very odd.

---

### Post by deadflowr on 2022-11-20
Look at what kernel you're booting into at restart.
Any kernel older than the latest will end up getting livepatched.
With the latest kernel having all the patched built in.

Scenario I can think is even though you're probably installing the latest updated kernel through the software updater, maybe your bootloader isn't reloading properly.
But that's just one of a myriad of possibilities.

Another is look at the livepatch's own output to see if it is actually livepatching or if it's some sort of anomaly of the notification system.
Run the command here
```
sudo canonical-livepatch status --verbose

```
to see the current livepatch status.

---

### Post by yatski on 2022-11-20
> **deadflowr said:**
> 
Another is look at the livepatch's own output to see if it is actually livepatching or if it's some sort of anomaly of the notification system.
Run the command here
```
sudo canonical-livepatch status --verbose

```
to see the current livepatch status.

It seems to be anomaly in notification system, since output gives line:
```
patch state: &#10003; all applicable livepatch modules inserted
```

---

