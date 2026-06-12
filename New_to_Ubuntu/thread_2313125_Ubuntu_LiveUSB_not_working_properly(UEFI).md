---
title: "Ubuntu LiveUSB not working properly(UEFI)"
date: 2016-02-09
forum: New to Ubuntu
---

### Post by Phantop on 2016-02-09
I'm trying to run Ubuntu 15.10 off a Flash Drive but the system seems to be going insane. First of all, it keeps bringing me to a login screen yet I don't know what it expects me to put in it. It asks for both username and password. Secondly, no attempts to connect to wi-fi work, although my router does show up. Lastly, text renders oddly, with parts of words not showing up. Any ideas on how to fix this? Also, would these problems persist if I installed Ubuntu to my computer?

Specs(according to Speccy):
Operating System
    Windows 10 Home 64-bit
CPU
    Intel Core i7 6700 @ 3.40GHz    75 °F
    Skylake 14nm Technology
RAM
    16.0GB Dual-Channel DDR3 @ 797MHz (11-11-11-28)
Motherboard
    HP 2B47 (U3E1)
Graphics
    S27D590 (1920x1080@60Hz)
    4095MB NVIDIA GeForce GTX 745 (HP)
Storage
    119GB SanDisk SD7SB3Q-128G-1006 (SSD)
    931GB Western Digital WDC WD10EZEX-60M2NA0 (SATA)
    14GB SanDisk Ultra USB Device (SSD)
    29GB Lexar USB Flash Drive USB Device (USB)  <---- What I'm booting Ubuntu off of.
Optical Drives
    hp CDDVDW SU-208GB
Audio
    NVIDIA High Definition Audio

---

### Post by sandyd on 2016-02-09
Hi,

What tool did you use to create the USB, and was the ISO downloaded verified?

You can verify that the ISO has been correctly downloaded by following the instructions at [https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows). If you have downloaded using torrenting, the ISO is automatically verified by your torrent client.

About the text corruption...
By default, Ubuntu uses the open source nouveau drivers. I've seen in some cases text corruption when using the drivers, and a user has reported that it happens on your card as well ([http://comments.gmane.org/gmane.comp.freedesktop.xorg.nouveau/21664](http://comments.gmane.org/gmane.comp.freedesktop.xorg.nouveau/21664)). That being said, you can try installing the proprietary drivers provided by NVIDIA, but they can only be installed after the system is installed.

If you are unsure about testing Ubuntu, you can create what is called a "dual boot" installation which allows you to have Ubuntu and Windows on the same system. This will allow you to test Ubuntu, but still switch back to Windows if there are any Windows-specific programs that you need, or if you are still getting used to Ubuntu.

---

### Post by Phantop on 2016-02-09
I used a torrent to download my ISO and Rufus to create the USB. Has anyone else run into my problem logging into LiveUSB with UEFI. My older PC runs it just fine, its my current one that's the issue. 

I might just go ahead and dual boot, I just wanted to run it a bit but I guess I might as well...

---

### Post by Vladlenin5000 on 2016-02-09
With Rufus you need to specify GPT/UEFI if you need to use it for UEFI hardware. If it works with older computers then it was made with the MBR/BIOS setting.

---

### Post by sandyd on 2016-02-10
Removed some duplicate posts

---

### Post by Phantop on 2016-02-10
I redid my USB like this yet the login screen persists. If I wasn't clear, let me clarify on my problem: I can get into GRUB and load up the LiveUSB but get forced on a login screen asking for both a username and password I don't know.

---

### Post by Vladlenin5000 on 2016-02-10
Where exactly that happens? What option are you choosing in the initial GRUB menu?

---

### Post by Phantop on 2016-02-10
If I remember right, its the first option that says 'live' or whatever. I get the correct UEFI boot and it DOES start the live os but it keeps asking me to log into a non-existent account.

---

### Post by Vladlenin5000 on 2016-02-10
Please check again.
Neither "Try Ubuntu" or "Install..." should be asking for user authentication.

---

### Post by Phantop on 2016-02-10
I pressed "Try Ubuntu without installing", it gave me some error involving something called BGRT(I think that's what it said) and then sent me to the login screen. Is there some kind of default account in the OS and what is the BGRT thing?

---

### Post by Vladlenin5000 on 2016-02-10
Try *nomodeset*:

When at grub menu press 'e' to edit the entry "Try...". Add nomodeset to the the same line with "quiet splash" and follow instructions to save, exit then use the Try Ubuntu option as usual.

---

### Post by Phantop on 2016-02-10
Now it loaded up the liveos. It didnt show the install ubuntu windows like legacy but I guess thats supposed to happen. From how it looks, I'm guessing this is some sort of safe mode. What do I do now? Its in 800:600 and thinks I have a built in display.

---

### Post by Phantop on 2016-02-10
Also text renders correctly now.

---

### Post by Phantop on 2016-02-10
I made an account to see what would happen and booted without nomodeset and it seems to work... Just hope nothing was broken. Actually, text is. And the account is gone.

---

### Post by Vladlenin5000 on 2016-02-10
Great news :-)

Now you can install as you normally would. The video mode is a generic one due to nomodeset. The problem is your graphics card isn't supported by the default open source driver for Nvidia hence the erros. Now, after installing, you'll have to do the same procedure in the installed grub otherwise you won't have video again. Then open System Settings > Software Properties and the Additional Drivers tab. Select and apply the recommended (proprietary) Nvidia driver and reboot when done. At this point your graphics card should be working with its full potential and automatically adjust for the best resolution available.

---

### Post by Phantop on 2016-02-10
OK, thanks for that. Now, I have a few completely different and unrelated questions (I want to dual boot btw):
A) Would I need to partition any differently than on my Legacy BIOS computer? Would I need other partitions other than /,SWAP, and /home?
B) Can I place /home on a separate drive? (D:/ while / and SWAP are on C:/)
C) Would doing it like this screw up my computer (delete data, delete Windows, etc) if I update to 16.04 LTS (when it comes out)

---

### Post by Vladlenin5000 on 2016-02-10
A) No. The only difference you find in an UEFI system is the shared ESP (EFI System Partition), automatically created when installing Ubuntu as standalone and already there if dual-booting.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

B) C: and D: is Windows terminology. We don't use those and no, when dual-booting your Windows "C:" (recognized by Linux as *probably* sda1) is completely independent of the partitions used by Linux. Besides, Windows requires NTFS and Linux (almost) anything but that. The point is there must be different partitions for each OS.
Yes, you can place /home in a different drive (use "Something Else" when installing) but there's little to no gain by making it as a separated partiiton.

C) Like what exactly?

---

### Post by Phantop on 2016-02-10
B) Sorry about my use of Windows terminology, didn't want to use Linux in case I got it wrong.
C) Say I updated and my Windows partitions were affected. Could something like that happen?

Either way, thanks a ton. Sorry if I was a bit "needy" when asking for help.

Also, quick note for anyone who has a similar login problem with LiveCD, username is Ubuntu with no password

---

### Post by Vladlenin5000 on 2016-02-10
You're welcome :-) , always happy to help those who deserve.

In the scenario you described is highly unlikely such disaster could happen. The other way around not so much. We had a few reports - just a few, to be fair - about an update to and/or within Windows 10 removing the partition table thus rendering Ubuntu unboootable. It can be corrected though. Either way you should always keep updated backups of all your important personal files and if you need to access those from both OSs then I strongly recommend a separated partition for that purpose, formated with a file system that can be 'seen' by both -> NTFS.

---

### Post by Phantop on 2016-02-10
Thanks (for the 2nd time). I use a separate drive for most files so I'm fine. Thanks for the 3rd time!

---

### Post by Vladlenin5000 on 2016-02-10
If you feel your questions were answered to your satisfaction, you can use the thread tools to mark it as solved.

---

