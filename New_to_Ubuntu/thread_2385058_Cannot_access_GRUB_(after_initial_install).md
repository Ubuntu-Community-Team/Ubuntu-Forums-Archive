---
title: "Cannot access GRUB (after initial install)"
date: 2018-02-15
forum: New to Ubuntu
---

### Post by mrfox321 on 2018-02-15
I have a fresh pc.

specs:  intel 8700K coffee lake
gpu: nvidia 1080ti
mobo: asus prime z370-a
ubuntu: 16.04 LTS

Due to the new hardware, I get "nouveau fifo sched_error 08" which is circumvented by the boot param "nomodeselect."  This indeed worked when I ran ubuntu in "try ubuntu without installing".  I am able to use GRUB to edit the install commands to include "nomodeselect".  However, I am not able to access GRUB on subsequent boots (pressing SHIFT) no matter how much I spam or hold.

Is there a way to (or most effective option):

1)  set kernel params permanently at install time?
2) access GRUB in another fashion?
3) setup drivers in the "ubuntu without install" mode and port it over to disc?

I plan on updating the kernel to 4.13 to allow for coffee lake, cuda, and cudnn support.

Thanks

---

### Post by oldfred on 2018-02-15
You should not need nor want nomodeset once you install the correct nVidia driver.
You can install from Ubuntu repository, but since yours is a very new nVidia card, you may need to add the ppa to get newest driver. Do not install directly from nVidia with .run file.

       nVidia install, purge if needed.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

Shift is for BIOS installs. With newer UEFI install you press escape between UEFI and grub loading. Perhaps more than once to have press recognized at right time.

You do need to have fast boot off in UEFI or you may not have time to press a key.
My Asus Z97 had several settings for UEFI, so I have both UEFI & grub at 3 sec, to just give me enough time to press a key. But it increased boot time a lot, since with SSD it is quick.
 
Newer 370 will be similar to older versions.

 Asus Prime Z270-A  Ethernet patch
[https://ubuntuforums.org/showthread.php?t=2351572](https://ubuntuforums.org/showthread.php?t=2351572)
Asus Z97 Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2298896](http://ubuntuforums.org/showthread.php?t=2298896)
Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=297](http://ubuntuforums.org/showthread.php?t=2258575&page=297)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu)

---

### Post by mrfox321 on 2018-02-16
Pressing esc worked like a charm.  I turned off fast boot to have more time to access GRUB.  The ethernet seems to work, but it is EXTREMELY slow.  Would the driver cause speeds to be slow?  Or would it just make the internet not work at all?

---

### Post by oldfred on 2018-02-16
My Z97 has this:

```
fred@Asusz97:~$ lspci -nnk | grep 0200 -A2
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
    DeviceName:  Onboard LAN
    Subsystem: ASUSTeK Computer Inc. Ethernet Connection (2) I218-V [1043:85c4]

```
The link above on z270 is similar just one digit newer?

Best to start new thread with Ethernet issue in title. Then those that know those issues better can help. All my systems have just worked so not as familiar with connection issues.

While this is more for wifi issues, it also tells additional info, probably they will want you to post it also.
Before Posting in Network and Wireless:
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

And post in this sub-forum.
[https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)

---

