---
title: "I Can No Longer Access Ubuntu After Running Boot-Repair."
date: 2014-08-31
forum: New to Ubuntu
---

### Post by juanbajista on 2014-08-31
Hello!  I have been running Ubuntu for the past year on my ASUS K55N A8.  I always had to first boot Windows 8, then shift-restart, select hard drive, and boot the computer all over again.  I saw a post which seemed to say that I could run Ubuntu from the moment I turned on my computer if I ran Boot-Repair.  I ran Boot-Repair, and I can now no longer access Ubuntu.

Here is the report:  [http://paste.ubuntu.com/8155097/](http://paste.ubuntu.com/8155097/)

I am currently wading through "Managing EFI Boot Loaders for Linux," by Rod Smith, but I am new to Ubuntu and most of the text is over my head.

Any and all help or advice is welcome!

Thanks!

---

### Post by yancek on 2014-08-31
With EFI booting, you need the efi files for ubuntu which should be on the same FAT32 partition which has the windows files.  You don't have any Ubuntu files there.  You also show Grub in the mbr of the drive and that should not be needed.  I'm not familiar enough with EFI to make any suggestions but this where you need to look.

---

### Post by juanbajista on 2014-08-31
I got some great help from Rod Smith at [www.rodsbooks.com](www.rodsbooks.com).  He helped me get my dual boot working with rEFInd.  Now, I can not only access my Ubuntu OS again, but I can boot to either Ubuntu or Windows straight from the opening page when I turn on my computer.

Thanks, Roderick W. Smith!

---

### Post by grahammechanical on 2014-08-31
Can you please explain this?

> [COLOR=#666666]===================[/COLOR] Settings chosen by the user
Boot-Info
This setting will not act on the MBR.

No change has been performed on your computer.

Boot Repair did not do anything to your computer because you did not accept the recommended repair. You had Windows 8 booting in EFI mode and Ubuntu booting in legacy mode.

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in EFI mode or not.
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

