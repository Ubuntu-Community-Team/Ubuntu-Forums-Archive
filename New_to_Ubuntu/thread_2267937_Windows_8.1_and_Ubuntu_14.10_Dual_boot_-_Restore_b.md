---
title: "Windows 8.1 and Ubuntu 14.10 Dual boot - Restore boot entry for Ubuntu"
date: 2015-03-05
forum: New to Ubuntu
---

### Post by austin30 on 2015-03-05
Current Laptop - Lenovo Yoga 2 Pro
My only experience with Ubuntu is setting up a Dual boot system with an old Dell Laptop as described in this thread: [https://shakeelosmani.wordpress.com/2014/07/31/dual-boot-windows-7-and-ubuntu-14-04/](https://shakeelosmani.wordpress.com/2014/07/31/dual-boot-windows-7-and-ubuntu-14-04/)

That worked like a charm. 
But with the new UEFI based boot I am not really able to make it. 
At first on installing Ubuntu, even though I gave a specific boot partition for GRUB as mentioned in the above post, it showed GRUB directly on boot. Then I added BCD entry for UBUNTU using EasyBCD. Also set c:\windows within Windows using bcdedit. After that windows boot menu comes with Ubuntu, but not able to boot Ubuntu. Windows was working fine. But later on I could see that if I go to boot menu with the Novo button in the laptop there is entry for Ubuntu and that booted too. 
Somewhat what I wanted though the Windows boot menu Ubuntu was not working. So I was about to ask how to remove Ubuntu from the windows menu or make it work. 

But today I was in call with the Lenovo support for a touchscreen issue and I had to restore it from a recovery backup. After that the EFI boot entry for Ubuntu is gone. But the partitions where Ubuntu was installed including the 500 mb Ubuntu partition is still there. What can I do in this situation? I want an entry of Ubuntu in either the EFI boot menu or preferably in Windows boot menu that works. 
I am newbie to Ubuntu and these UEFI stuff.
Do I need to install Ubuntu again, if yes how and  if not what?

Can anyone help me?
Thanks in advance.

---

### Post by oldfred on 2015-03-05
Do not reinstall without reading link in my signature below. Even recovery may not work unless you use Something Else.

Post link to Summary report from Boot-Repair.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
      
Issue with HiDPI
[http://ubuntuforums.org/showthread.php?t=2267886](http://ubuntuforums.org/showthread.php?t=2267886)
 Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)
Yoga2
[http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/](http://bregmatter.wordpress.com/2014/01/16/the-future-looks-very-small/)
Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)

---

### Post by austin30 on 2015-03-05
Hi oldfred,

I got confused on reading these.
Could you please clarify on the exact steps I need to perform.
Another info which I missed, before installing Ubuntu I had set the SecureBoot to Disable.

Please let me know if you need any more info from my side. But I need precise steps, because as I told I am quite new to all these.

---

### Post by JeQhdMD on 2015-03-05
Although I have no experience in installing any Linux distro on a UEFI/GPT firmware PC . . . I've read that if you install correctly you should:

>  _disable_ fast/quick boot
>  keep secure boot _enabled_
>  use 64 bit ubuntu or similar UEFI enabled distro

Because of these kind of issues (even tho I've installed Linux on at least 20-25 PC's over the years - - now I just buy pre-installed Linux (System76 and Zareason) - - 5 to 10 minute setup.   MLS (makes life simple).

But, the above is kind of boring and I'm not learning anything new, so,  I may bite the bullet and buy a cheapie laptop w/UEFI-GPT to gain the experience and fun of installing Ubuntu.

---

### Post by oldfred on 2015-03-05
First post link to Summary report from Boot-Repair, so we can see where you are at. 

It looks like you can install, but the HiDPI may cause issues. 
I know there are improvements in kernel, support software & video drivers, so may be best to install newest version of Ubuntu.

---

### Post by austin30 on 2015-03-05
Thanks [**[COLOR=#000000]JeQhdMD[/COLOR]**]("http://ubuntuforums.org/member.php?u=1841810")

Hi oldfred,
Thanks a lot for your response.
What I installed was Ubuntu 14.10.
And here is the Boot Repair Summary:
[http://paste.ubuntu.com/10542874/](http://paste.ubuntu.com/10542874/)

---

### Post by oldfred on 2015-03-05
You are not showing the /EFI/ubuntu folder which is where the grub2 boot loader would install.
From Boot-Repair run the suggested fix.
And then see if UEFI offers Ubuntu as a choice. Or one time boot key.

---

### Post by austin30 on 2015-03-06
I performed boot repair. Then on restart it was the GRUB menu. Both OS loaded fine.
Then in Windows I did bcdboot C:\windows which made it boot directly to Windows.

In the BIOS menu I am able to see Windows and two Ubuntu etries, any will take to Ubuntu.Is this the best achievable situation, if yes I can close the thread as answered. Also is it possible to remove that extra entry in BIOS boot menu.

---

### Post by oldfred on 2015-03-06
You probably have two entries as one is grub and the other shim which is the secure boot version of grub.

       Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

I think UEFI adds entries it finds in efi partition. So you may have to delete either grub or shim and even then on grub update they will get replaced. So not sure you can permanently delete.
If booting in secure boot mode only shim should be shown. But then I do not think you can boot Windows from grub menu, but only from UEFI menu.

---

### Post by austin30 on 2015-03-06
This seems complicated for me. :)
I think I can live with it.

Everything else looks good except for the notorious yellow issue, more prominent with Linux.
I think I need to put another thread for that. 
Thanks a lot.

---

