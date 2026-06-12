---
title: "Can't Get back to Windows (have searched other posts, none helped)"
date: 2018-07-12
forum: New to Ubuntu
---

### Post by viperion444 on 2018-07-12
Hello all.

My problem in short:

I tried to install a dual boot Ubuntu 18 / Windows 7. I installed Win7 First, then ubuntu. Since bootmgr was not showing, I tried a  "bcdedit /set "{bootmgr}"" command which made my PC boot directly to ubuntu (still no grub showing). I was getting familiar to ubuntu, when I realized one of My HDs (the really important one) was unaccesible from ubuntu. Somehow, it is shown as 3 different locations, and none of them are accesible. 

So I tried to boot back to windows from the bootmenu, and it is impossible... It seems my ubuntu is booting from a legacy bios, but when I enter my bios it says I'm booting from UEFI. So I'm stucked in ubuntu, with no access to my important data. 

Also, I use a couple PCs in Windows (one in a business I own) in a network, and I can't access my data from another windows PC if I'm booting to ubuntu. I know there are ways to make Linux and Windows machines to communicate between each other, but I'm not an experienced user, and I just would like to get back to windows and check if my HD is ok (my financial and business data are in that HD).

Another thing: in the boot menu, I can choose between the hard drive I have both, win7 and ubuntu installed, or an option that says "windows boot manager". No matter which one I choose, both end up booting ubuntu (no GRUB).

I've looked for several possible solutions, and none of them have worked for me.

Any help will be greatly appreciated.

---

### Post by westie457 on 2018-07-12
Welcome to UF viperion444

Boot your Ubuntu and open a terminal, copy and paste this, ```
[COLOR=#111111][FONT=Consolas][ -d /sys/firmware/efi ] && echo UEFI || echo BIOS 
```
post the result.

Also go to [/FONT][/COLOR]https://help.ubuntu.com/community/Boot-Repair look for the 2nd option, follow the directions to download, install and run.

[COLOR=#111111][FONT=Consolas]DO NOT attempt any repairs yet, select the button to generate a boot report. also post the generated link here so we know what we are looking at.

Thank you.

[/FONT][/COLOR]

---

### Post by yancek on 2018-07-12
More detailed information will be needed on your physical hard drives, partitions and filesystems as well as boot files.  Best way to get that is to go to the site below and download boot repair whle booted into Ubuntu.  Use the 2nd option to download and run the program as instructed on the page.  Make certain you do NOT try to make any repairs but select the option to Create BootInfo Summary and when it finishes, it will give you a link which you can post here for member to view and suggest possible solutions.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by viperion444 on 2018-07-12
Well, after running the first command, the return value is just "BIOS"

I had tried the second option in that page, and I got the "The current session is in legacy mode. Please reboot the computer, and use this software in an EFI session" message.

When entering my BIOS it says I AM in UEFI, so I don't know what else to do.

If it helps, the complete commands and results in my terminal are as follows:

```
viperion@Viper-Ubuntu:~$ [ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
BIOS
viperion@Viper-Ubuntu:~$
```

Thank you for baring with my ignorance.

---

### Post by oldfred on 2018-07-12
The old Windows 7 DVD only installs in BIOS/CSM/Legacy boot mode, even though all new computers in last 5 years are UEFI but have CSM for backward compatibilty.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
Windows 7 can be installed in UEFI boot mode, but you have to copy to flash drive and move/rename a couple of files to make it UEFI bootable.

For newer Windows & Ubuntu, UEFI systems will offer two boot modes for installing system, one clearly UEFI:name and other name where name is name or label of flash drive. If UEFI Secure Boot mode is on, then only UEFI boot option. If legacy on, some systems only boot in Legacy/BIOS/CSM mode and some still let you choose boot mode.

How you boot installer & repair media is then how it installs system. And best to have all systems in same boot mode, but now UEFI somewhat better. But if you have spent a lot of time configuring a BIOS Windows probably better to keep Windows in BIOS mode. Ubuntu can be in UEFI, but then you cannot dual  boot from grub menu, only from UEFI boot menu. Some system work, others may require you to turn on/off UEFI or Legacy to boot the actual install(s) on hard drive.

Post link to Boot-Repair Summary report.
Boot-Repair can convert a UEFI Ubuntu to BIOS boot, but may need you to separately create a partition. After we see report, we can make better suggestions.

---

### Post by viperion444 on 2018-07-12
Well, I tried again to run the Boot-Repair utility, but apparently, it won't let me do a single thing since I'm in legacy... I'm gonna go ape on this machine... I was also thinking of running a bootable USB with Win 7 and "repairing" the system, but I don't know if that would fix anything, and I wanted to ask first.

I wouldn't like to re-install windows, since it's a pain in the ass to re-configure all of it again.

---

### Post by westie457 on 2018-07-12
Try again please, this time booting from your Ubuntu installation media.

Again go to here. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) repeat the instructions to download install and run.

**Do not attempt any repairs.** Just click on the 'Create a Bootinfo summary' button. 

Post the link please.

---

### Post by viperion444 on 2018-07-12
This

---

### Post by viperion444 on 2018-07-12
Sorry, something odd happened while replying. I booted from my flash drive this time, installed the boot  repair tool while on the live version of "try ubuntu" and it says the very same :/. I get the same "the current session is in legacy mode" message again.

I have to freshly instalk win7 again, don't I? :(

---

### Post by #&amp;thj^% on 2018-07-12
> **viperion444 said:**
> This

we don't see this?
See screenshot

---

### Post by viperion444 on 2018-07-12
Sorry again. Last time I was replying on a different device, and somehow I tapped the wrong part of the scree. I'm on the troubled PC again. Here is the report:

[http://paste.ubuntu.com/p/XhcZVkkYXg/](http://paste.ubuntu.com/p/XhcZVkkYXg/)

---

### Post by viperion444 on 2018-07-12
So... In all my despair, I plugged the USB flashdrive containing Win7, and chose the "Repair Windows" option. Now I'm replying from Win7, but can't get back to ubuntu... geeez....

---

### Post by oldfred on 2018-07-12
You show Windows installed in UEFI boot mode.
And you show Ubuntu/grub in BIOS boot mode.
If you boot the Ubuntu installer in UEFI mode from UEFI boot menu, and then run Boot-Repair, in its advanced options should be the total uninstall/reinstall of grub. That will convert from the BIOS boot version of grub to the UEFI version of grub.

You also show major partition issues on sdb, that may be causing other issues. It looks like partition table is totally corrupted. It shows it is MBR(msdos) partitioned, so no backup. Gpt has a backup that often allows easy recovery.
You may be able to use testdisk. Or if mostly Windows partitions, then Windows tools may be better.

---

### Post by viperion444 on 2018-07-12
When I use the USB flashdrive with WIN7 it does let me choose an UEFI type of booting. When I use the one with Ubuntu, I see no way to do an UEFI boot. Is there something I'm missing? Or do I have to create a flashdrive again and choose some kind of option to make it UEFI? I used Rufus for my WIN7 bootable flash drive, but the Ubuntu one I got from a friend.

---

### Post by viperion444 on 2018-07-12
Ok, this works now. What I did:

I created a brand new flashdrive with ubuntu 18 (I used rufus) and I configured it so it would be a UEFI one.
I Ran the live version of ubuntu (Try ubuntu).
I installed the boot repair utility and hitted the recomended option (first one).
The GUI is really pretty straight forward, it tells you to run some commands in the terminal.
After following the instructions I rebooted without entering the bios (a normal boot) and now I could see the GRUB.

Turns out, my problem from the very beginning was the flash drive with which I installed ubuntu, and the major difference between Win7 Being in UEFI and Ubuntu in BIOS (Legacy).

Thank you all for your patience and support.

---

