---
title: "[SOLVED] Start-up (booting) issue/problem/something with 8.04 Can you help me?"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by suomalainen on 2008-07-02
Hello Fellow Ubunteros!

I have the following two screens pop-up each time I try to boot Linux-Ubuntu 8.04.

I'd like to do away with these two "formalities"/procedures. Can you help me to do so????

Thanks!

P.S. Please note that:

1. File Screenshot-dsc03426.jpg is the first screen request to appear.
2. File Screenshot-dsc03428.jpg is the second screen request to appear.

---

### Post by overdrank on 2008-07-02
> **suomalainen said:**
> Hello Fellow Ubunteros!

I have the following two screens pop-up each time I try to boot Linux-Ubuntu 8.04.

I'd like to do away with these two "formalities"/procedures. Can you help me to do so????

Thanks!

P.S. Please note that:

1. File Screenshot-dsc03426.jpg is the first screen request to appear.
2. File Screenshot-dsc03428.jpg is the second screen request to appear.

Hi and you can edit you boot menu with this command 
```
gksu gedit /boot/grub/menu.lst
```
and place a # comment in front of the title except for the first of course. 
```
Example
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
[COLOR="Red"]title[/COLOR]		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=f37fe8d7-11b8-4ae5-8158-5c967ab313c3 ro single 
initrd		/boot/initrd.img-2.6.22-14-386
savedefault
boot
```
and also change the default time to 0
```
Example
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR="Red"]timeout		10[/COLOR]
```

But I would recommend leaving at least the recovery mode in case something happens and you need to rescue your system

---

### Post by markjensen on 2008-07-02
Well, the first part looks like the normal GRUB boot where it should select default boot OS selection from your /boot/grub/menu.lst unless you hit a key.

The second image looks like normal GRUB menu selection.

Did you want to remove all ability to access GRUB and its menus?   It can be useful to get to these areas to troubleshoot boot problems (as GRUB has a commandline interface that you can manually specify kernel boot files and such in the event of a disaster).

I do think that if you have GRUB set to be quiet, you should see the first one only, that will time out and start the boot.   The second screen should only come up if not set up that way, or if you hit a key to indicate you need the menu.

---

### Post by suomalainen on 2008-07-02
Thanks for the help on this.

1. How is GRUB set to quiet?
2. What happens if I need to use recovery mode someday? How would I access it?

Thanks

---

### Post by overdrank on 2008-07-02
> **suomalainen said:**
> Thanks for the help on this.

1. How is GRUB set to quiet?
2. What happens if I need to use recovery mode someday? How would I access it?

Thanks

Hi and for the first I am unaware but you may look here
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
If you would like to access the grub list at boot for recovery mode then when you see grub load then press the escape key and it will show the menu list.

---

### Post by suomalainen on 2008-07-02
ok. I'm getting confused now.....

All I would like to do is have Linux Ubuntu 8.04 boot automatically into the user name and password.

Based on the directives I'm reading, it appears certain things "which even I remain unclear about" are being modified.

Would it be possible to backup and start over.

Thanks for the help.

---

### Post by suomalainen on 2008-07-02
Team,

As suggested, I changed the default time, i.e. "timeout    3" (post says 10 mine was 3) value to 0. The hope being that when Linux-Ubuntu booted up I would bypass both of the screens I was receiving during system boot. Pics of these screens have been attached. Please see first post above.

I launched terminal and applied necessary adjustments as noted above.

I rebooted system and boot process went immeadiately to user name window and then password window. Just like I wanted!

I shut down system. Waited 10 minutes and rebooted again. After BIOS boot I pressed "Esc" repeatedly and was brought into the window I noted above in "screen Two". The importance of this is that I retain access to recovery mode should/when it be needed.

I appreciate all efforts to assist me as they were sincere and conducted in the spirit of a free community helping each other! I became lost, however, when I was told to place "#" in front of commands that I didn't need to do nor understand why I was being told to do so.

Thank you very much for helping me make the necessary adjustments on my PC.

Your efforts on my behalf are fully appreciated!

---

