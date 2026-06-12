---
title: "How to remove gnu grub"
date: 2013-11-17
forum: New to Ubuntu
---

### Post by m_goad on 2013-11-17
I saw a post that was similar but was still a bit different.  I have a desktop I built last year.  My main OS is Windows 7 pro and I installed ubuntu alongside it for fun.  After the computer turns on, I would get a black screen with white letters that would let me choose either windows or ubuntu, with windows at the top.  Today when I logged into Ubuntu it asked to upgrade to version 13.10, so I did.  The upgrade went sour and I ended up completely deleting ubuntu and then just reinstalling version 13.10.  Now when I turn on the PC though, this gnu grub comes up asking which one to load.  It defaults to ubuntu.  If you choose the ubuntu, that will load right up, if you choose the windows, then it goes to the black screen that I'm used to where it asks whether to load windows or ubuntu.  Everything seems to be working find but this completely unneccessary step of grub got in the way.  Is there some way to make it disappear so it will go straight to my normal black screen with white letters option?

---

### Post by elliotn on 2013-11-17
I think you might have messed up the windows boot....get a windows 7 DVD and repair boot then when u can boot to windows, u must fix grub to boot to Ubuntu

---

### Post by oldfred on 2013-11-17
If Windows was on top with first boot screen, was this a wubi install?
Wubi is being discontinued and last supported version is 12.04, although it seems you may be able to install newer versions.

Wubi uses the Windows boot loader, so you should fix Windows first.

---

### Post by coffeecat on 2013-11-18
If you remove grub, you will remove the bootloader and you will not be able to boot anything. From what you have posted, the sequence of events would appear to be:

1 - You originally installed a pre-13.10 version of Ubuntu as a wubi install - that is, Ubuntu in a pseudo-partition inside the Windows partition. The white on black menu with Windows as the first choice certainly sounds like a wubi menu.

2 - You upgraded your Ubuntu to 13.10, but the upgrade went wrong. 

3 - You "deleted" Ubuntu. I presume you uninstalled it from within Windows? Which is the way wubi installs are removed.

4 - You made a fresh installation of 13.10. Since you have ended up with a grub menu, this would have been a conventional installation with Ubuntu on its own partition.

5 - The appearance of the black wubi menu would be because the wubi uninstallation was incomplete and the Windows boot files need further editing.

If my surmise is correct, then everything is working as it should and there is nothing to fix with the exception of the residual wubi menu. Before we look at that, I suggest you post some information to confirm that you do now have a conventional dual-boot with Ubuntu on its own partition. Open a terminal in Ubuntu and post the output of:

```
sudo fdisk -l
```

Also - it sounds from what you say as though Windows is booting correctly when you select it from the black menu. Please confirm this.

---

### Post by m_goad on 2013-11-18
I looked better at that black screen, and it's a Windows boot loader.  So when I turn on my pc, first comes up the grub, if I choose windows, then the windows boot loader shows up giving me the same options.  Windows does still load good after choose the windows loader from the grub and then again windows from the windows boot loader.
 I just looked at the black screen closer and at the top is says, "WINDOWS BOOT MANAGER".  That's the screen that always used to be what I used to choose and much prefer over grub.
I just did a little more analyzing.  If I choose the Ubuntu from the "windows boot manager" it tries to install it fresh, and then errors because of no live something or other.  I'm guessing it's looking for what I put on the dvd.  Also, when I initally uninstalled ubuntu using remove programs in windows, the windows boot manager also didn't show up anymore.  When I reinstalled it using the osi on the dvd, then both grub and windows boot manager showed up again.

---

### Post by m_goad on 2013-11-18
And yes, to uninstall I went through windows.  To reinstall I downloaded an osi file and put in a dvd and installed from there.

---

### Post by m_goad on 2013-11-18
Does this look like the right information your looking for?  I'm pretty sure I entered that command in right. 


```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbfe47ce9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1077034246   538413699+   7  HPFS/NTFS/exFAT
/dev/sda3      1077035006  1953523711   438244353    5  Extended
/dev/sda5      1077035008  1936752639   429858816   83  Linux
/dev/sda6      1936754688  1953523711     8384512   82  Linux swap / Solaris
mattgoad@mattgoad-System-Product-Name:~$
```

---

### Post by oldfred on 2013-11-18
You have to manually remove the wubi entry from Windows with bcdEdit.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

       bcdEdit - bcbc
[http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)
[http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu](http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu)

---

### Post by coffeecat on 2013-11-18
> **m_goad said:**
> Does this look like the right information your looking for?  I'm pretty sure I entered that command in right. 

That's absolutely fine and it confirms what I had supposed had happened. You had a wubi install which you replaced with a conventional dual-boot install when the wubi upgrade went wrong. In fact, that was a good thing. Wubi was only ever really intended for a short-time tryout of Ubuntu. It ran slowly and there were other potential issues. You now have Ubuntu on its own native partition and that's far better. The only thing to fix now is the residual white on black menu which is getting in the way. Here's a link which tells you how:

[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

I think this is the relevant bit:

> For Windows Vista/7, you can use the built-in bcdedit command or install EasyBCD to edit the boot menu. To use bcdedit, run cmd.exe as an administrator, then enter bcdedit to show all boot entries, note the {GUID} specified for the Ubuntu entry, and then remove it: bcdedit /delete {GUID}

To remove Wubi from the add/remove list, delete the registry key: HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi 

I have no experience of having to do that, but I'll simply urge caution if you are unfamiliar with bcdedit. Installing EasyBCD might be a better option but again I have no experience of this. Someone else may be able to comment.

The registry key edit is only needed if Ubuntu is still showing up in the add/remove list.

By the way - I've added code tags to your terminal output. You lose formatting otherwise. If you post terminal output it's always better to use code tags and the easiest way of doing that is to highlight the output in the advanced message editor and then click on the toolbar icon that looks like a #.


**EDIT**: ninja'd by oldfred. Thanks, oldfred! :)

---

### Post by m_goad on 2013-11-18
Thanks  TON for the help all of you.  Sure enough, I looked at that wubi guide some and that windows boot manager is the exact screen that I'm used to.  When I get some time I'll dig into these posts and the guides posted in them.  It would be nice if once I can get rid of this residual wubi, I could get that windows on top though so it's my default.

---

### Post by oldfred on 2013-11-18
Once you remove the wubi entry Windows should directly boot from grub.

If you want Windows first in grub menu you can change that. There is grub customizer but I have not used it and some reports seem to say it modifies too many things.

I prefer some manual edits. And as with all things computer related there are several ways to change things.
You can edit grub settings and change default to correct line number for Windows, note that count starts at zero for first menu entry. Line count is critical. I once changed to a blank spacer line that I added and wondered why I could not boot at all? 
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
But I prefer to use exact text instead of number.
      
 find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default  here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

If you have the new submenu best to review this:
[http://ubuntuforums.org/showthread.php?t=1739336](http://ubuntuforums.org/showthread.php?t=1739336)
Entry then is more like this:
With grub 1.99 and submenus
GRUB_DEFAULT="2>Ubuntu, with Linux 2.6.38-7-generic"


You can rename this to 06_os-prober. Grub processes script in number order. Then it finds Windows before it looks for Linux kernels.

 /etc/grub.d/30_os-prober
But on a major update grub may download new scripts and create a new 30_os-prober and you get entries at top & then at bottom also.

Similarly you can manually copy a Windows boot stanza to 40_custom and copy 40_custom to 06_custom. You have to make sure it is executeable also.

---

### Post by yc.chenyi on 2013-11-18
Wubi is great for beginners from Windows. But sometimes it brings some weird problems.

Use Grub and use a unique partition for your Linux, man.

---

