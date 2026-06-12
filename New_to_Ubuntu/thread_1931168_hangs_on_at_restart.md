---
title: "hangs on at restart"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by battlechaser on 2012-02-24
Hi,
I installed ubuntu 11.10 on my Acer AspireOne D257-13473 and it wont restart. I click on the restart button. it shuts down the computer and attempts to restart and just stays at a black screen. I have to power the computer down manually by pushing the on button then power it back up and ubuntu boots up just fine. Does anyone have a fix to this problem. its really starting to annoy me. ive tried looking it up on google but found no solution.

---

### Post by Jake5 on 2012-02-25
Open the Terminal and run this command   # sudo update-grub  hit enter enter password hit enter  And Welcome! Ive gotten a ton of help here and am very thankful for the community. Ive had the same issue on every machine ive installed ubuntu on.

---

### Post by battlechaser on 2012-02-25
I've tried that and it still hangs on during restart..maybe its just this type of netbook that i have that is causing this?..

ACER AOD257
Intel Atom N570 1.66GHz
2GB RAM
Intel IGDx88/MMX/SSE2....(Intel N10 Family Graphics Controller)
32BIT

I've found other forums with similar problem, but no solution...hibernate, shutdown, etc everything works fine except for restart.

I've even tried installing the kexec-tool and changed the kexe.conf
from "quiet splash" to "off splash" that lets me restart the computer but it also makes the display off color right before it restarts. i didnt want to use that because i was afraid that would eff up my system.

I've also tried installing grub and updating it..doesnt work

---

### Post by Jake5 on 2012-02-25
It may be your machine.
Perhaps report the bug @ [https://launchpad.net/upstart/+bugs](https://launchpad.net/upstart/+bugs)
Otherwise I suggest trying from the Terminal when its needed.
```

sudo reboot

```

I suggest running this first and learning about it.
```

man reboot

```

---

### Post by HeroOfCanton on 2012-02-25
The good thing about doing it from terminal is you will see the kill processes. If it hangs up on a particular line try posting the message here (or just include it in your bug report). Of course, you can't take a screenshot, or copy/paste, at that point so you will need to take a picture or write it down. :(

---

### Post by enjoijesus94 on 2012-02-25
Had This Problem 

All You Do Is Press Shift At Bootup Of Ubuntu.
for example.
(When The Screen Turns Purple)

replace the quiet splash with 'nomodeset'
without quotes.
should be on the second to last line

then crtl+x to boot

---

### Post by battlechaser on 2012-02-27
Tried what enjoijesus suggested still doesnt fix the problem.

---

### Post by audiomick on 2012-02-27
> **Jake5 said:**
> It may be your machine.
Perhaps report the bug @ [https://launchpad.net/upstart/+bugs](https://launchpad.net/upstart/+bugs)
Otherwise I suggest trying from the Terminal when its needed.
```

sudo reboot

```I suggest running this first and learning about it.
```

man reboot

```

from

```
man reboot
```>  When called with --force or when in runlevel 0 or 6, this tool  invokes
       the reboot(2) system call itself and directly reboots the system.  Oth&#8208;
       erwise this simply invokes the shutdown tool  with  the  appropriate
       arguments.
If you are interested, the command for "shutdown" is

```
sudo shutdown -r now
```to turn the computer off completely

```
sudo shutdown -P now
```These commands are worth remembering. They are quite useful sometimes. ;)

---

