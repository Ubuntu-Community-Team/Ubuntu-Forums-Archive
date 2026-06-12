---
title: "Occasionally freezing for 5-10 seconds at a time"
date: 2017-10-28
forum: New to Ubuntu
---

### Post by spoonyvoid on 2017-10-28
Ubuntu newbie here!

I've got Ubuntu Mate 17.04 installed on my HP Envy 15 j123tx (along with Windows 10).

Occasionally as I'm working on my laptop, everything freezes for 5 to 10 seconds before snapping back to normal. During this freeze, I can only move the mouse around. Nothing I click on responds.

I did a bit of Googling, discovered what "dmesg" does and it generated this:

```
[19513.713939] ata1: exception Emask 0x50 SAct 0x0 SErr 0x4090800 action 0xe frozen
[19513.713948] ata1: irq_stat 0x00400040, connection status changed
[19513.713953] ata1: SError: { HostInt PHYRdyChg 10B8B DevExch }
[19513.713962] ata1: hard resetting link
[19514.426281] ata1: SATA link down (SStatus 0 SControl 310)
[19519.650260] ata1: hard resetting link
[19519.964894] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[19519.966942] ata1.00: configured for UDMA/33
[19519.966948] ata1: EH complete
```

And there were several of these same lines over and over again! This seems like it's a hard drive issue, but I just installed a new hard drive 5 days ago! It can't possibly be a malfunctioning hard drive right?

Some forum threads recommended switching to the Nvidia Propriety Drivers which I did. But the above still occurs.

*Also this hardly occurs on Windows 10. At least not as frequently as it does on Ubuntu and not in such a pronounced manner where everything stops responding. *[B](EDIT: Apologies if this sounds confusing. Windows does not "freeze".)
[/B] 
Any help will be greatly appreciated since I would really like to continue using Ubuntu.

---

### Post by spoonyvoid on 2017-10-29
[B]UPDATE
[/B]
I installed GSmartControl on Linux and ran a short test. It passed with no errors. I then ran an extended test and it was **interrupted at 10% due to a host reset**.

I decided to do the same on Windows 10. I installed GSmartControl and ran an extended test. After ~90 minutes, **the test completed without errors**. I also installed CrystalDiskInfo and it reported that my hard drive's status is "Good".

Could this be a Linux Kernal Issue? Should I try out a different version of Linux? Perhaps Ubuntu Mate 17.10?

---

### Post by HermanAB on 2017-10-29
Is it a Seagate disk?  They tend to be hickety pickety and there is a configuration fix for it.

---

### Post by RobGoss on 2017-10-29
What are the specs for your machine it will help trouble shoot this issue.  Some distributions run better them others you might also want to test drive a few other distributions to see what work and what does not on this machine

---

### Post by spoonyvoid on 2017-10-29
> **HermanAB said:**
> Is it a Seagate disk? They tend to be hickety pickety and there is a configuration fix for it.

Nope. It's an HGST Travelstar Z5K500.B -> [https://www.hgst.com/products/hard-drives/travelstar-z5k500b](https://www.hgst.com/products/hard-drives/travelstar-z5k500b)

> **RobGoss said:**
> What are the specs for your machine it will help trouble shoot this issue.  Some distributions run better them others you might also want to test drive a few other distributions to see what work and what does not on this machine

Laptop Model: HP Envy 15 j123tx
OS: Windows 10 Home (Single Language) & Ubuntu Mate 17.04
Processor: Intel i5-4200M
HDD: HGST Travelstar Z5K500.B (500 GB -> 380 GB for Windows and 12 GB (Root), 8 GB (Swap) and 65 GB (Home) for Ubuntu Mate)
Memory: 4 GB RAM
Display: Intel HD Graphics 4600
Render: Nvidia GeForce GT740M

Any other information you need?

Also I've used Linux Mint but I had WiFi issues. I used Ubuntu Mate 16 but I had WiFi issues on that as well. The WiFi worked well on Ubuntu Mate 17.04 when I switched from Network Manager to WICD, but as you obviously already know, now I'm having these issues. I'm a linux newbie and I've heard that the other distros are quite unfriendly to newbies.

---

### Post by RobGoss on 2017-10-29
With the specs you provided you should not have any issues with the system freezing as so, you also mention when you are using Windows is also freezes correct?

---

### Post by spoonyvoid on 2017-10-29
> **RobGoss said:**
> With the specs you provided you should not have any issues with the system freezing as so, you also mention when you are using Windows is also freezes correct?

I think I put that across the wrong way. It doesn't freeze like in Ubuntu where you can only move the mouse and nothing else responds at all for 5-10 seconds. 

I was referring to the temporary "slow-down" that occurs when you load a program on Windows. It's not really a freeze because I can still open files and folders and load other lightweight programs like Notepad++ (while the other program's getting started up) and use them.

Today on Windows it never once froze. But when I was on Linux a few hours ago, it froze for 10 seconds twice.

It's worth mentioning that I did check the event viewer in windows. There were about 20 Disk Errors in total (Event ID 154: The IO operation at logical block address # for Disk 0 failed due to a hardware error) and it seems like I've gotten around 2 or 3 per day since the day after I installed the hard drive (and installed Win10 and Ubuntu Mate).This is a bit weird because I haven't really had any issue with it at all when on Windows. Even during the times when a disk error was logged, the computer did not freeze. In fact a disk error was logged when I was running the extended test on GSmartControl and that wasn't interrupted.

Furthermore I installed HP 3D Driveguard and the Intel Rapid Storage Technology driver today (since they're listed on the HP website for my computer). After doing that (it's been about 2-3 hours so far) I haven't gotten a 154 Disk Error.

---

### Post by spoonyvoid on 2017-10-29
Also, shortly before this started occurring my grub2 boot up menu disappeared. I now have to smash ESC, go to boot options (F9) and select Ubuntu. Only then does it go to the grub2 menu, from where I select Ubuntu again to login.

Could any of this be linked to that?

---

### Post by RobGoss on 2017-10-29
> **spoonyvoid said:**
> Also, shortly before this started occurring my grub2 boot up menu disappeared. I now have to smash ESC, go to boot options (F9) and select Ubuntu. Only then does it go to the grub2 menu, from where I select Ubuntu again to login.

Could any of this be linked to that?

Have you tried running Boot repair [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) follow the instruction and maybe reinstall Grub, this is my best tough seeing you're now able to boot normally from the Grub menu

---

### Post by RobGoss on 2017-10-29
Is this a new installation? 

Have you made any changes to your system?

---

### Post by spoonyvoid on 2017-10-29
> **RobGoss said:**
> Have you tried running Boot repair [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) follow the instruction and maybe reinstall Grub, this is my best tough seeing you're now able to boot normally from the Grub menu

I'll try this out! Thanks.

> **RobGoss said:**
> Is this a new installation? 

Have you made any changes to your system?

Yup. Installed Ubuntu Mate 16 on on Tuesday, but I was having issues with the WiFi and someone recommended upgrading to 17.04. So I did a clean install of 17.04. WiFi speeds were still not consistent so I replaced Network Manager with WICD and that solved the WiFi problem.

I also installed Python 3.6.3, Atom and Chrome.

When this problem started happening, I read somewhere that it could be caused by the Nouveau drivers, so I switched to the Nvidia Propriety Drivers and disabled Secure Boot from the BIOS (I didn't get a prompt as I was applying the changes from the Additional Drivers area probably because the last time I tried to install the propriety drivers I changed my mind and selected "No" when they asked me to disable secure boot). I also switched to using a propriety driver for an Intel Microcode. Not sure what that is because it wasn't described very well, but I enabled it anyway.

But then the problem still occurred.

---

