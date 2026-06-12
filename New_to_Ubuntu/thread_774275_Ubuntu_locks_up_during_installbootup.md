---
title: "Ubuntu locks up during install/bootup"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by wicketr on 2008-04-29
I'm not sure what the deal is. I've tried installing 7.10 in the past with the same problems and now 8.04. I've checked the CD's integrity and it's fine. It'll usually lock up around the 90% mark on the progress bar.

I did try the Alternate CD and the install seemed to work fine :), but when it boots up, it locks up :(. The first time it booted up, i was able to enter my login credentials and then it started doing the "startup sound" and then locked up, repeating about a seconds worth of the "startup sound". Now it locks up at random intervals before I even get to the login screen.

I have Vista on another hard drive and it works fine. And XP on another and it works fine. What is the deal with Ubuntu locking up constantly?

I will say that the only thing finicky about my setup is the RAM  voltage has to be 2.1, but the default for the motherboard is 1.8. I'm almost thinking that Ubuntu is changing it, which is causing the lockups. :confused: (I did run the memcheck and everything cleared 4x)

I have:
Intel E6600
2GB OCZ Ram (2x OCZ2P8001GK)
Foxconn P9657AA-8KS2H
Maxtor SATA 250GB hard drive
2 SATA DVD Drives

I really want to try Linux, but with it locking up before I can even say 'YAY', it's kinda hard to jump on the bandwagon. And with the lack of any error messages whatsoever of what's happening, it kinda leaves a crappy taste in my mouth.

---

### Post by wicketr on 2008-04-29
Anyone???? Surely I'm not the only one that has had this situation.

And I forgot to mention it's a Nvidia 7900GS graphics card.

---

### Post by martrn on 2008-04-29
> **wicketr said:**
> Anyone???? Surely I'm not the only one that has had this situation. And I forgot to mention it's a Nvidia 7900GS graphics card.

No you are not the only one. Although doesn't effect most people, but that prhaps won't help you.

[http://ubuntuforums.org/showthread.php?t=768200]("http://ubuntuforums.org/showthread.php?t=768200")
Look here :- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996")

file a bug report at launchpad here :- [https://bugs.launchpad.net/]("https://bugs.launchpad.net/")

If you can logon in recovery mode for a short time have you tried changeing to a diffrent kernel ?
```
sudo apt-get install linux-rt
```
and using the real time kernel, as this handles processing schedules diffrently. ?

---

