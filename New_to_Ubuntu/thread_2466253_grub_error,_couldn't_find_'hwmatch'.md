---
title: "grub error, couldn't find 'hwmatch'"
date: 2021-08-24
forum: New to Ubuntu
---

### Post by fabgiese on 2021-08-24
Hi guys, I'm a beginner in Ubuntu, and I have a problem, when I boot my computer show up a problem screen. I think that screen is from grub.


Couldn't find 'hwmatch'
error: invalid environment block
press any key to continue...


When I press any key, mostly it's started normally, but sometimes it's going to initramfs screen and I need to use file system check and fix some problems.
How could I fix this problem?
Thanks, everyone for your attention.

---

### Post by grahammechanical on 2021-08-24
How far along in the OS loading process are you getting? If you dual boot you should see a Grub boot menu. Do you see a Grub boot menu? We need to know if the message <couldn't find hwmatch> is coming from Grub itself or from Linux. If you see a Grub boot menu then select Advanced Options for Ubuntu and then select either an older Linux kernel (that may load to a desktop) or, a Linux kernel with recovery mode. That will load Linux with a recovery menu that will allow us to run commands.

If you are dual booting we need to know that information. Is the motherboard BIOS or UEFI? What version of Ubuntu are you using?

I am posting this link not as a solution but as information for what <hwmatch> means. There are other links that an internet search will offer

[https://www.linux.org/threads/error-cant-find-command-hwmatch-during-boot.32618/](https://www.linux.org/threads/error-cant-find-command-hwmatch-during-boot.32618/)

> hwmatch - This module is **where the Blacklist and Whitelist for hardware are stored**.  One is for the Grub the other for the system these need to match. You  can boot a live usb system and run from that. sudo fsck /dev/sda1. this  should let you know if there are differences.19 Jan 2021





Regards

---

### Post by fabgiese on 2021-08-25
No, my ubuntu starts normally, but grub screen not, this error happens just follow the bios screen, I'm using UEFI and I don't use dual boot.

---

### Post by oldfred on 2021-08-26
You can try this:
[https://askubuntu.com/questions/1174374/grub-issues-message-at-boot-error-cant-find-command-hwmatch/1301092#1301092](https://askubuntu.com/questions/1174374/grub-issues-message-at-boot-error-cant-find-command-hwmatch/1301092#1301092)
> To get rid of the error message, add this line to /etc/default/grub:
 GRUB_GFXPAYLOAD_LINUX=keep


---

### Post by honglonglong2 on 2022-03-18
I have got the same problem:
After bios , it shows : 
error: invalid environment block 
error: can't find command hwmatch

I have edited the /etc/default/grub and add
GRUB_GFXPAYLOAD_LINUX=keep
to the file, and after rebooting it show:

error: invalid environment block

---

### Post by ActionParsnip on 2022-03-19
[https://askubuntu.com/questions/191852/error-invalid-environment-block-press-any-key-to-continue](https://askubuntu.com/questions/191852/error-invalid-environment-block-press-any-key-to-continue)

---

