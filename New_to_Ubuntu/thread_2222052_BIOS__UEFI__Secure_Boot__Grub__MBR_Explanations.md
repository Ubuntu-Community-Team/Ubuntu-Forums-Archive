---
title: "BIOS / UEFI / Secure Boot / Grub / MBR Explanations?"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by teacherjeff2 on 2014-05-04
Could somebody point me in the direction of an explanation of these terms **and how they are related to each other**? Obviously I can do a search and find explanations of each term in isolation, but I'm having trouble understanding the relationship between them. 

Or maybe a better way to ask the same thing would be to ask where I can find an up-to-date explanation of the boot sequence. Or maybe evan a flow chart?  Like "when the computer is first powered on, it executes commands in the firmware that do this and this, and then pass control to xxxx. And so on.)

Sorry if this question is vague. I'm not even sure I know what it is that I don't know.

---

### Post by LastDino on 2014-05-05
This is really old but after reading it I thought it was quite good myself.

[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by squakie on 2014-05-05
If it is Windows 8, then the link above doesn't apply.  AFAIK Windows 8 requires UEFI, and it requires the disk be of a certain type (not physical or brand).

---

### Post by newbie2244 on 2014-05-05
By any chance aare you trying to implement a dual boot Ubuntu/Linux-Windows 8 system?

  <url>http://uefi.org/sites/default/files/resources/UEFI_Clarifying_Common_Misconceptions_White_Paper_April%202014_Final.pdf</url>
<url>windows.microsoft.com/en-us/windows-8/what-uefi&#8206;</url>
<url>http://technet.microsoft.com/en-us/library/hh824987.aspx</url>

The 'Secure Boot' option can be turned off in your BIOS. If you're trying to install Linux on a Windows 8 system for a dual boot configuration, you may have to turn this option off. 

<url>http://www.webopedia.com/TERM/M/microsoft_secure_boot.html</url>

GRUB - <url>www.gnu.org/s/grub</url> -- cannot be used to install Linux alongside Windows 8. Use universal installer.

MBR -master boot record - explained above -- <url>en.wikipedia.org/wiki/Master_boot_record </url>
<url>technet.microsoft.com/en-us/library/cc976786.aspx&#8206;</url>

Regards

By any chance aare you trying to implement a dual boot Ubuntu/Linux-Windows 8 system?

[http://uefi.org/sites/default/files/resources/UEFI_Clarifying_Common_Misconceptions_White_Paper_ April%202014_Final.pdf](http://uefi.org/sites/default/files/resources/UEFI_Clarifying_Common_Misconceptions_White_Paper_ April%202014_Final.pdf)
[windows.microsoft.com/en-us/windows-8/what-uefi&#8206;](windows.microsoft.com/en-us/windows-8/what-uefi&#8206;)
[http://technet.microsoft.com/en-us/library/hh824987.aspx](http://technet.microsoft.com/en-us/library/hh824987.aspx)

The 'Secure Boot' option can be turned off in your BIOS. If you're trying to install Linux on a Windows 8 system for a dual boot configuration, you may have to turn this option off.

[http://www.webopedia.com/TERM/M/microsoft_secure_boot.html](http://www.webopedia.com/TERM/M/microsoft_secure_boot.html)

GRUB - [www.gnu.org/s/grub](www.gnu.org/s/grub)- cannot be used to install Linux alongside Windows 8. Use universal installer.

MBR -master boot record - explained above -- [en.wikipedia.org/wiki/Master_boot_record ](en.wikipedia.org/wiki/Master_boot_record )
[technet.microsoft.com/en-us/library/cc976786.aspx&#8206;](technet.microsoft.com/en-us/library/cc976786.aspx&#8206;)

Regards 

P.S. Sorry about the tags in the prev post.

---

### Post by teacherjeff2 on 2014-05-05
Thanks for the links.

No, I'm not trying to dual boot Ubuntu and Windows 8 at the moment. Just trying to understand things better. I thought I had a basic conceptual understanding about the boot process before UEFI came along. But it has confused me.

Also, newbie2244, could you clarify your comment that GRUB "cannot be used to install Linux alongside Windows 8. Use universal installer"?  Is it really the case that Grub is no longer used to dual-boot Linux and Windows 8?? That seems like a pretty fundamental change to the architecture, and I hadn't read anything to that effect. (Of course, that doesn't necessarily mean anything.)

---

### Post by grahammechanical on 2014-05-05
You may need to research each of those items.

BIOS = Basic Input Output System. It is computer code in an integrated circuit that tells the machine what kind of machine it is.

UEFI = Unified Extensible Firmware Interface. It replaces BIOS on the latest motherboards. 

Secure boot is a means to prevent non-certified computer programs such as operating systems from being installed on a computer.

Grub = GRand Unified Bootloader. It is what it says it is.

MBR = Master Boot Record. It is a special portion of the hard disk that contains information about the partitions of the hard disk. It has been superseded on the latest motherboards by GTP = GUID Partition Table. You left that one out.

The combination of Grub + Linux + Ubuntu can deal with UEFI, Secure boot and GPT. Problems arise by the way the Original Equipment Manufacturers (OEMs) implement the specifications and seek to make their hardware different/better than the hardware of their competitors. Those differences make it even harder to understand how these bit and pieces fit together.

Regards.

---

### Post by oldfred on 2014-05-05
There now are two versions of grub, grub-pc (BIOS boot) and grub-efi (UEFI boot). So grub is still used with both BIOS and UEFI boot but it installs differently as the two ways to boot are different.

BIOS uses MBR for initial boot code on hard drive. And each hard drive has only one MBR, so only one system can be default boot.
UEFI uses an efi partition for initial boot code and each system installed has a separate folder with its boot files. Somewhat like having many MBR's in old BIOS configuration. And from UEFI menu you can choose to boot any system (if not one of those where vendor modifies it to only boot Windows).

       Technical info on Legacy BIOS and  UEFI AMI AptioMar 2012 -  20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)

---

### Post by newbie2244 on 2014-05-31
I apparently made a mistake. I meant to say WUBI cannot be used for W8 dual boot install and Legacy Grub is not supported. Apologies for any confusion. Regards.

---

