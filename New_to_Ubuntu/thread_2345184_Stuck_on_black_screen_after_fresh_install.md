---
title: "Stuck on black screen after fresh install"
date: 2016-12-01
forum: New to Ubuntu
---

### Post by olokos on 2016-12-01
Hello,

My specs:

MSI Z97S SLI Krait Edition
i7 4790K
GTX 1070
OS SSD: GoodRam Iridium Pro 240GB
12GB DDR3
UEFI Mode

My displays:
AOC G2460PG
OPTIMUS OPTIView L 17v

Multiboot with Windows 10 using GRUB

I had some issues with my old ubuntu installation after i switched GTX 970 for a Radeon HD5770, but it was booting. Now that I've got GTX 1070 at last it does not seem to boot at all.

I've done about 4 installations of Ubuntu 16.10, but each and every time after installing it I got Ubuntu logo on my second display and after that it went completely black. I've waited for more than an hour, but it did not boot. A friend of mine told me to try elementary OS, so I gave it a try, fresh install formatting the old ubuntu partition aaand it just stays there with elementary logo displayed on both monitors and it does not go any further.

How do I go about getting linux to boot again? :(

---

### Post by zapp2 on 2016-12-01
Try to update ubuntu with -u

---

### Post by olokos on 2016-12-01
> **zapp2 said:**
> Try to update ubuntu with -u

I have no idea what that means. The ways of updating ubuntu that I'm aware of are sudo apt update/upgrade/dist-upgrade and I've tried all of these in rescue mode.

---

### Post by zapp2 on 2016-12-01
I never have this problem but you might be interested in this: [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by olokos on 2016-12-02
Apparently nomodeset fixed my issue, thank you. I couldn't use CTRL X to boot the edited entry, but google told me F10 could be used instead which worked. Thanks.
/solved

---

