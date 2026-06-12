---
title: "Random logout from system, possible ATI driver fail"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by antidotcb on 2012-01-24
Hi everyone

Let me describe my problem.

During last several days I'm experiencing one problem:
Eventually screen blackout for a second, and then I'm already on login screen. I have to log in, make log-out once more (because my eclipse don't start correctly after such things), and log in again.
I'm developer, permanently using following software:
* Eclipse Indigo Service Release, Build id: 20110916-0149
* java version "1.6.0_23", OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10)
OpenJDK Server VM (build 20.0-b11, mixed mode)
* ATI Driver [ATTACH]211388[/ATTACH]
* Google Chrome 16.0.912.75
* Banshee 2.2.1
* Latest Android SDK & NDK
This is almost complete list of software I use all the time I use Ubuntu. Maybe Gwibber, dropbox, Evolution I use sometimes. But such random "black-o-log-out" primarly happens when I write java code.

And one more thin, lately I upgraded to 11.10, I have all recent updates installed.

After each such black out following lines apeear in /var/log/kern.log

Jan 24 17:17:03 antidotcb-pc kernel: [26209.408138] [fglrx] IRQ 89 Disabled
Jan 24 17:17:03 antidotcb-pc kernel: [26209.798821] fglrx_pci 0000:01:00.0: irq 89 for MSI/MSI-X
Jan 24 17:17:03 antidotcb-pc kernel: [26209.799282] [fglrx] Firegl kernel thread PID: 27628
Jan 24 17:17:03 antidotcb-pc kernel: [26209.799316] [fglrx] Firegl kernel thread PID: 27629
Jan 24 17:17:03 antidotcb-pc kernel: [26209.799349] [fglrx] Firegl kernel thread PID: 27630
Jan 24 17:17:03 antidotcb-pc kernel: [26209.799415] [fglrx] IRQ 89 Enabled
Jan 24 17:17:03 antidotcb-pc kernel: [26209.904647] [fglrx] Gart USWC size:1280 M.
Jan 24 17:17:03 antidotcb-pc kernel: [26209.904650] [fglrx] Gart cacheable size:508 M.
Jan 24 17:17:03 antidotcb-pc kernel: [26209.904653] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Jan 24 17:17:03 antidotcb-pc kernel: [26209.904655] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
Jan 24 17:17:03 antidotcb-pc kernel: [26209.904657] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000

I can give u any info u want, please, help.
Such eventual log-outs makes me rage each time before I could press "Ctrl+S", to save my codings. :evil:

Thanks in advance.

P.S. Sry for my bad english.

---

### Post by QIII on 2012-01-24
The issue may not be directly related to the fglrx driver itself.

You begin to eliminate or confirm it as the culprit by removing it temporarily to see if the problem persists.

However, the driver may be a red herring.  Does this happen "usually" when you are coding ot always?  Does it happen when you test/debug your code?  Does it happen soon after you open eclipse even if you do not write code?

How much of your code base depends/runs on FireGL ?

You need not apologize for your English.

---

### Post by antidotcb on 2012-01-27
I used this guide to uninstall fglrx:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch)
But I had no luck.
After uninstall and reboot - all I get is blank screen.

The answers on you questions:
Does this happen "usually" when you are coding ot always? 
It's happen when I code, when I watch movies (vlc), when I play minecraft.

Does it happen when you test/debug your code? 
Rarely, primarly when I write code, and when I play minecraft.

Does it happen soon after you open eclipse even if you do not write code?
Not soon, it's about each 2-3 hours.

How much of your code base depends/runs on FireGL ?
Not one line, I write android app. I don't need even to run my code, I got random logout.

Thank you in advance.

---

### Post by QIII on 2012-01-27
(Just to get this out of the way:  "Get an NVIDIA card" is not a solution.  There are posts similar to this from people who use NVIDIA cards.  The link the OP gave even has instructions for that.  This is not a place for a brand loyalty flame war.)

Can you tell me a bit more about the machine specs?

---

### Post by antidotcb on 2012-01-27
GPU: ASUS EAH5850 DirectCU TOP/2DIS/1GD5
CPU: AMD Phenom II X4 975
MB: ASUS Crosshair V Formula
RAM: 8GB
Main HDD: OCZ 120GB Vertex 3

---

### Post by antidotcb on 2012-01-27
One more detail. In latest times such random log-outs have some interesting fact:
After one random log-out appears, and I log-in - do nothing/anything up to 1 min, and second in a row "random" log-out happens.

---

### Post by QIII on 2012-01-27
Did you get the GRUB menu before this all started happening or did your machine boot directly to Ubuntu?

Do you get the black screen before or after the GRUB menu?

If we can get you into recovery mode, you can try the tutorial again -- if you have a laptop or another computer you can use a browser on to follow the instructions.  I have used it several times when testing development releases on machines with AMD graphics when something breaks.  It has always worked for me.

---

### Post by antidotcb on 2012-01-28
Yes, I load into GRUB. I can enter recovery. I tried twice to go with tutorial, but no luck. May I messed something totaly? Is it good idea of clean install of ubuntu from scratch?
The only way to restore Ubuntu boot - is to use fglrx. Any version of it, original:
apt-get update
apt-get install fglrx fglrx-amdcccle fglrx-dev
or another latest proprietary from AMD (i downloaded bin package and converted into 3 .deb packages before).
dpkg -i fglrx*.deb

I want to ask: where I can read some log about why the boot is failing with ati/radeon xorg-driver? Any system journal (analog to System Log in windows) where I could read about what happened to unity, why it logouts, when it with xglrx?

---

