---
title: "asus g74 laptop keyboard lights"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by carusoswi on 2012-02-21
I recently purchased the Asus G74 notebook, and have installed Ubuntu 11.10 as a dual boot.

In Win7, my keyboard is back-lit.  This feature is not active in Ubuntu.  I know this is a very minor issue, but does someone out there know how I might get the lights working in Ubuntu?

Caruso

---

### Post by shakenfrog on 2012-03-04
> **carusoswi said:**
> I recently purchased the Asus G74 notebook, and have installed Ubuntu 11.10 as a dual boot.

In Win7, my keyboard is back-lit.  This feature is not active in Ubuntu.  I know this is a very minor issue, but does someone out there know how I might get the lights working in Ubuntu?

Caruso
  Check this out. 
1. Open terminal
2. type "sudo su" without quotes and enter password (just the way I do it, I'm sure you can just sudo)
[SIZE=1]3. type "[/SIZE][SIZE=1]echo 0x00050021 > /sys/kernel/debug/asus-nb-wmi/dev_id" without quotes. Hit enter.
4. type "[/SIZE][SIZE=1]echo 0x82 > /sys/kernel/debug/asus-nb-wmi/ctrl_param" without quotes. Hit enter.
5. type "[/SIZE][SIZE=1]cat /sys/kernel/debug/asus-nb-wmi/devs" without quotes. Hit enter.
Tada! 

Now, 0x80 is lights off
0x81 is lights low
0x82 is lights mid
0x83 is lights high
Just sub the one you want and rerun the cat code. Add all three lines to your /etc/rc.local before the last line to have it happen at boot.

To clarify, if you want the lights to come on at high when the system boots you would add:

[/SIZE][SIZE=1]echo 0x00050021 > /sys/kernel/debug/asus-nb-wmi/dev_id
[/SIZE]  [SIZE=1]echo 0x83 > /sys/kernel/debug/asus-nb-wmi/ctrl_param
[/SIZE]  [SIZE=1]cat /sys/kernel/debug/asus-nb-wmi/devs[/SIZE]

---

### Post by carusoswi on 2012-03-09
Tada! Indeed!
How did you ever figure that out?
Thanks, Shakenfrog.
You have caused me to 'see the light'.
Caruso

---

### Post by shakenfrog on 2012-04-11
I got the laptop and after a bunch of research I came across the important info and saved it in case I would need it later. I got board and played with the values to find that there were 4 settings relating to the device cat calling (or whatever, I'm still a noob to the terminology here). I think it was on [**this thread**.]("http://ubuntuforums.org/showthread.php?t=1752900") (custom deb links have been dead and obsolete for a while.)

Recently I've noticed that one of the recent updates lets the OS recognize the [fn]+[f4] although it doesn't actually change anything on mine yet. Not even if I lower the lights with the echo/dev lines. The [fn]+[f3] still doesn't do anything. I think I saw a script to fix them somewhere, but I can't seem to find it right now.

Glad it helped you out! Don't forget to do step 7 if you haven't already so you can control your screen brightness. :)

---

