---
title: "Launcher, icons, terminal not working after routine updating ubuntu 12.04 lts"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by dmp_mech on 2013-02-09
I have routine updated ubuntu 12.04 LTS 64 bit. I have dual os: windows 7 and ubuntu 12.04 LTS 64 bit. Grub is working fine. Windows 7 is also working fine. I have installed from a CD  downloaded from ubuntu site. I have updated my 12.04 successfully in last  few months. I did routine update on 12.04 as usual and it asked me to  restart to complete update. I restarted and arrive at a signon screen  which has my username and "Guest". This screen shows the menu at the top  with power, time, calendar, etc. So I entered my password and I am  taken to a screen which only shows a blank screen, empty launcher area  only including dash and trash. The only thing that works is I cam move  my mouse but there is nothing on screen which I can click. Terminal is  also not working using Alt+Ctrl+T key. Please help in this.

---

### Post by dalee on 2013-02-09
Hi,

I have the exact same issue with 12.04 32bit. The only updates delivered were to flash, a new kernel, and an update to linux-libc-dev. My hardware is an Asus laptop with an Intel Core-i3 @ 2.3Ghz with an Intel Sandybridge Mobil x86/MMX/SSE2 video.

The flash update can't cause problems of this sort. And it's hard to see what the new kernel could do to freeze Unity because that's just the desktop.

I'm thinking it has to do with the linux-libc-dev update. Unity 2D at the log in prompt does work fine. As does choosing an older kernel.

I'm not that good at solving such problems, but I will be rummaging around searching for one as best I can. Perhaps some else can help that is more knowledgeable than I am. But you aren't alone with this.

dalee

---

### Post by westcoast01 on 2013-02-09
Same thing here:( Tried recovery mode now I do not have ethernet/lan/network on either OS. windows 7 x64 dual boot Ubuntu 12.04 x64. Still trying to figure this out so will keep an eye on this post for a solution. Best of luck.

---

### Post by kkooman on 2013-02-09
I have the same problem. When I login Ubuntu 3d I can't do anything. When I press ctrl alt F1 and enter my username and password, I can enter "kill -9 -1" and press ENTER. After I logged in again (you'll get the login screen without restarting your computer) I&#314;l get _one_ session in Ubuntu 3d. After logout I have to follow the whole procedures again!

(excuse me for my poor English)

---

### Post by Bashing-om on 2013-02-10
@ all

Try this to restore unity in version 12.04; Terminal code:
```
unity --reset
```which should first reset compiz then unity to the default settings.
[INDENT][INDENT][INDENT]hth

[/INDENT][/INDENT][/INDENT]

---

### Post by chenierm on 2013-02-10
Same problem on my side

unity --reset doesn't work for me. The screen freeze and after a reboot, got the same problem. 

12.04 LTS should the stable distribution...hum, just installed 13.04 a week ago on my laptop because of the same problem and it work well.

---

### Post by dmp_mech on 2013-02-11
> **Bashing-om said:**
> @ all

Try this to restore unity in version 12.04; Terminal code:
```
unity --reset
```which should first reset compiz then unity to the default settings.[INDENT][INDENT][INDENT]hth

[/INDENT][/INDENT][/INDENT]
If I try to open terminal via Alt+Ctrl+T then terminal is not opening. How can I write unity --reset command? Any other way?

---

### Post by kkooman on 2013-02-11
> **dmp_mech said:**
> If I try to open terminal via Alt+Ctrl+T then terminal is not opening. How can I write unity --reset command? Any other way?

CTRL Alt F1, insert your username and password. Now you can enter the code

---

### Post by dmp_mech on 2013-02-11
Hey friends,

I saw new thing. Before routine updating, the OS selection page was (or grub loader page):

Ubuntu, with Linux 3.2.0-38-generic
Ubuntu, with Linux 3.2.0-38-generic (recovery mode)
Memory test (memtest 86+)
Memory test (memtest 86+, serial console 115200)
Windows 7 (loader)(on /dev/sda1)

When move my cursor with arrow key on first line and enter, it will start ubuntu 12.04 in just one step. But after routine updating I did not saw change in grub. New menu is:

Ubuntu, with Linux 3.2.0-38-generic
Ubuntu, with Linux 3.2.0-38-generic (recovery mode)
**Previous Linux Versions**
Memory test (memtest 86+)
Memory test (memtest 86+, serial console 115200)
Windows 7 (loader)(on /dev/sda1)

Here third line (in bold fonts) was newer than the previous grub version. Just for curiosity I entered in third line to check what is in it. It showed following lines
Ubuntu, with Linux 3.2.0-37-generic
Ubuntu, with Linux 3.2.0-37-generic (recovery mode)
Ubuntu, with Linux 3.2.0-36-generic
Ubuntu, with Linux 3.2.0-36-generic (recovery mode)
Ubuntu, with Linux 3.2.0-35-generic
Ubuntu, with Linux 3.2.0-35-generic (recovery mode)
Ubuntu, with Linux 3.2.0-34-generic
Ubuntu, with Linux 3.2.0-34-generic (recovery mode)
Ubuntu, with Linux 3.2.0-33-generic
Ubuntu, with Linux 3.2.0-33-generic (recovery mode)
Ubuntu, with Linux 3.2.0-32-generic
Ubuntu, with Linux 3.2.0-32-generic (recovery mode)
Ubuntu, with Linux 3.2.0-23-generic
Ubuntu, with Linux 3.2.0-23-generic (recovery mode)

When I enter any of the line:1,3,5,7,9,11,13 it will give me my installed ubuntu 12.04 LTS 64 bit with proper functioning and all the previous settings. This gave me my original Ubuntu in two steps of OS selection page. I do not understand why this additional OS menu has been added. And also how to get back to previous one step OS selection page?

---

### Post by deadflowr on 2013-02-11
Looking over post #9, I assume you have proposed-updates enabled.

Unfortunately, if this is the case, breakage, though rare, can be expected.

To avoid breakage, especially, on a production machine, proposed-updates should be kept disabled.

Just a thought.

---

### Post by dalee on 2013-02-13
Hi,

It would seem that the latest update to the kernel headers have resolved the problem for me as of 2/13/13.

Deadflowr is absolutely correct about using proposed updates on an LTS release for a production machine. Still, this is why keeping an old kernel or two handy can keep your machine functioning until a fix for your problem arrives.

dalee

---

### Post by dmp_mech on 2013-02-21
> **deadflowr said:**
> Looking over post #9, I assume you have proposed-updates enabled.

Unfortunately, if this is the case, breakage, though rare, can be expected.

To avoid breakage, especially, on a production machine, proposed-updates should be kept disabled.

Just a thought.

How can disable proposed-updates?

---

### Post by stinkeye on 2013-02-21
In software sources under the updates tab.
The default setting is disabled.

---

