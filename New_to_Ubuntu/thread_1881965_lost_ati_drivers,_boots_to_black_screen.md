---
title: "lost ati drivers, boots to black screen"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by kurja on 2011-11-16
Hi,

I am completely new to linux and to this forum as well. I just installed ubuntu 10.04, and after attempting to change the ati display drivers (because I tried if I could play steam games with wine but it did not work, graphics were messed up) system will not start. Powering up, things appear to run normally untill the `splash screen`, which appears only momentarily and then the screen goes black. I tried booting from the CD from which I installed ubuntu, and it starts normally. Is there a way to revert to default ati display drivers, other than re-installing the whole thing?

I have an ati radeon 9600 card on an abit ku8 motherboard, if that makes a difference.

---

### Post by pme 72 on 2011-11-16
Hi Kurja,

The ATI Radeon 9600 card is no longer supported by the Catalyst Driver. You should be able to revert to the default driver by following the instructions in the Lucid Installation Guide under Removing the Driver. Restart and when you get to the Grub Menu choose Recovery Mode, then failsafeX and then "Run Ubuntu in low-graphics mode for just one session". You should be returned to your desktop but in a low-graphics mode. Open up a terminal and run the code in the instructions from "Removing the Driver". Then reboot. 

Here is the link to the instructions:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

Post back if you need more specific instructions or have further issues.

---

### Post by kurja on 2011-11-16
> **pme 72 said:**
> Hi Kurja,

The ATI Radeon 9600 card is no longer supported by the Catalyst Driver. You should be able to revert to the default driver by following the instructions in the Lucid Installation Guide under Removing the Driver. Restart and when you get to the Grub Menu choose Recovery Mode, then failsafeX and then "Run Ubuntu in low-graphics mode for just one session". You should be returned to your desktop but in a low-graphics mode. Open up a terminal and run the code in the instructions from "Removing the Driver". Then reboot. 

Here is the link to the instructions:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

Post back if you need more specific instructions or have further issues.

Thanks, that got me forward - but not quite through yet. When trying to boot in low-graphics mode, I got an error message saying "no display detected" or something to that effect (sorry, the message was visible only momentarily). But, I got on the computer as netroot, and ran the commands to remove drivers and then replace them. Now, system boots and I can see my desktop - yay! - BUT now both my keyboard and mouse are completely dead!!! Any ideas how to remedy that? :confused:


edit- problem solved by running the updater.

---

### Post by lifelike27 on 2011-12-20
I just wanted to mention that I have this same issue as well i.e the keyboard and mouse aren't working..

When you say you ran the updater, do you mean, sudo apt-get update && sudo apt-get upgrade?

---

### Post by kurja on 2012-02-24
late as heck, but yes.

---

