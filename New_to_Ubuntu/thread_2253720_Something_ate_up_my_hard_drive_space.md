---
title: "Something ate up my hard drive space"
date: 2014-11-21
forum: New to Ubuntu
---

### Post by Ethan_Ikpeama on 2014-11-21
I just switched using Ubuntu as my primary OS yesterday. When I found out that I couldn't play my favorites games on it, I decided to use some of my hard drive space for Windows 7 and have my games on there. But when I opened up GParted to shrink my primary partition, it said 100% of the space was being used and I only had 12MB left. I know this isn't possible because I just got it yesterday and I didn't download that many things. Could there be something that ate up my hard drive space? Or is this just an error?

---

### Post by carl4926 on 2014-11-21
It doesn't sound like an error, or at least it's unlikely.
It is possible on the other hand that you are confused.

It's not clear from your words, exactly where the problem is. Please try and explain where you think you should have space and what you need to do. Perhaps include a screenshot of the Gparted info.

---

### Post by oldfred on 2014-11-21
Did you use an encrypted install with full drive LVM or just LVM? Those use the entire physical partitions and are logical partitions inside the LVM. You cannot install Windows inside the LVM.

---

### Post by Ethan_Ikpeama on 2014-11-22
> **oldfred said:**
> Did you use an encrypted install with full drive LVM or just LVM? Those use the entire physical partitions and are logical partitions inside the LVM. You cannot install Windows inside the LVM.
I pretty sure I just selected LVM, but I don't think you quite understand what I'm trying to do. I'm just trying to shrink my main partition.
> **carl4926 said:**
> It doesn't sound like an error, or at least it's unlikely.
It is possible on the other hand that you are confused.

It's not clear from your words, exactly where the problem is. Please try and explain where you think you should have space and what you need to do. Perhaps include a screenshot of the Gparted info.
I think I should have space on my main partition, because it's about 500GB, and I just installed Ubuntu yesterday, so I don't have that many things. This causes me to think that something ate up my hard drive space. I'm just trying to shrink my main partition to make room for a second OS.

[http://www74.zippyshare.com/v/26721638/file.html](http://www74.zippyshare.com/v/26721638/file.html)

EDIT: I think I'm just going to delete Ubuntu, install Windows 7, and then reinstall Ubuntu.

This is what the GParted screen looks like. I'm trying to shrink /dev/sda3, but I can't because all the space is being used and I can't figure out why.

---

### Post by carl4926 on 2014-11-22
> [COLOR=#000000]EDIT: I think I'm just going to delete Ubuntu, install Windows 7, and then reinstall Ubuntu[/COLOR]
Yes. 
If it were me though I'd set my partitions up first.

> [COLOR=#000000]all the space is being used and I can't figure out why.[/COLOR]As was pointed out, it's LVM
I wouldn't use that myself anyway, even in a plain Linux install.

---

### Post by yancek on 2014-11-22
You will not be able to change the LVM in the same manner as you do standard partitions.  If you don't have an specific reason for selecting an LVM install then you don't need it.  Never used it myself but you would probably be best off starting over.  You also need to decide in advance whether you are going to use UEFI/GPT or MBR install.  Your image in the initial post shows you have both a standard boot partition as well as an EFI partition.  Definitely lead to problems if you do that.

---

### Post by oldfred on 2014-11-22
If you have UEFI capabile hardware, then you can install each operating system in UEFI or BIOS/CSM boot mode.
But you just about have to have both systems in same boot mode.
Windows 7 seems to default to BIOS with MBR and when it converts from gpt to MBR partitiioning does it incorrectly. So better to modify Windows 7 installer to install in UEFI mode. Some say it does offer that choice so it may depend on version of Windows 7?

How you boot install media BIOS or UEFI is how it installs for both operating systems.
       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

Important to review this when installing Ubuntu in UEFI mode.
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

