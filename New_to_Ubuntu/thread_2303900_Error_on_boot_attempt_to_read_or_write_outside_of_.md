---
title: "Error on boot: attempt to read or write outside of partition"
date: 2015-11-22
forum: New to Ubuntu
---

### Post by michele19 on 2015-11-22
I have my neighbor's Dell Latitutde E6410 Laptop that I just put on a fresh install of Windows 7. Yesterday I added Ubuntu 14.04.3 to run alongside Windows 7. After the install and reboot I got "Error: attempt to read or write outside of partition. Entering rescue mode.  I tried using boot repair via the live cd but that did not work.  [ATTACH=CONFIG]265726[/ATTACH]

When I enter ls at the grub rescue prompt here is that shows on the screen
[ATTACH=CONFIG]265727[/ATTACH]

Here is a picture of my partition table from Gparted when I used the live cd
[ATTACH=CONFIG]265728[/ATTACH]

I started using Ubuntu regularly again last year with no problems. This is my first problem and I'm not sure what my next steps should be or what I did wrong.  Can anyone help?

---

### Post by oldfred on 2015-11-22
Is this yours, would have been easier if you had posted it.
[http://paste.ubuntu.com/13452734/](http://paste.ubuntu.com/13452734/)

Script shows grub 2.00, but 14.04 uses 2.02 which Boot-Repair says it installed.
I do not see any specific partition table issues.

You do show an old wubi install in Windows, best to delete that in Windows. Wubi not supported any more. Details on typical uninstall here:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Edit:
Is BIOS set for AHCI for hard drive, not IDE?
Some old BIOS which all were IDE could only boot from first 137GB of a drive. But almost all newer systems do not have that issue. But if in IDE mode, it may have some issue??

---

### Post by michele19 on 2015-11-23
Hi, thanks for the reply.  I was unfamiliar with posting the long, hence the picture of the link but next time I will know. Thanks....I'm wondering about the difference in the grub install (2.00 vs 2.02) and the wubi install. I downloaded the newest LTS of ubuntu and yes, I did open wubi through windows but then did reboot and installed Ubuntu that way.

I checked the bios and AHCI is enabled.

However, I am going to close this thread. Her hard drive started making clicking noises last night so I believe it will fail. I don't want to put more work into it until if/when after the hard drive fails and she decides if she wants to replace it.  For the time being I just rewrote the MBR and can boot into windows.  I am going to fix another computer of hers (old desktop) and I am going to see if she will forgo windows and go strictly with Linux. I hope so. She likes to play games (facebook games, etc) and seems to pick up all kinds of viruses, etc. I know she won't have that problem if she uses Linux.

Thanks again for your help!

---

