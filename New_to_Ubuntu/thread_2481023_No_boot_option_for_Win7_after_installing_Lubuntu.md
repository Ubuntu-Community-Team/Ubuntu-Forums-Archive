---
title: "No boot option for Win7 after installing Lubuntu"
date: 2022-11-16
forum: New to Ubuntu
---

### Post by lord-carnarvon on 2022-11-16
I had a working win7 installation on a thinkpad 0328a11 (celeron, bit of an older laptop) & wanted to try out Lubuntu. Installed Lubuntu 22.04 and resized the 160Gb hdd into 2 80Gb partitions in the install program from the Lubuntu live desktop. Lubuntu works GREAT but I don't have any boot options for going into Win7. I don't have any important win7 programs that I need to run off this laptop, I was using this laptop as a testbed for Lubuntu installs on other pcs. I can easily find and mount the win7 partition & all the data seems to be there. I gather that grub/lilo or something has overwritten the mbr but I am very new to linux/Lubuntu so not sure as to exactly what has happened or how to fix this. I am pc literate for 40 years (win/dos/osx environments) & have no problem with losing the win7 partition or rewriting or re-installing the whole lot if needed, but what I really want is either to know where I went wrong or how to fix this so that when/if I install Lubuntu on my other pcs that I know what I'm doing.
thanks to all for any help provided

---

### Post by tea for one on 2022-11-17
I suspect that you have Windows 7 installed in Legacy mode and Lubuntu 22.04 in UEFI mode.
Here is some info [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also, Windows 7 is now unsupported and should not be used to connect to the internet.

---

### Post by yancek on 2022-11-17
Are you familiar with the difference between Legacy/CSM installs and UEFI installs?  Newer computers and newer operating systems use UEFI and soon Legacy/CSM will not be available on new computers.  Do you know if you booted and installed Lubuntu in UEFI mode?  If you did, that may be the reason as the standard install of windows 7 is Legacy/CSM while Lubuntu may be UEFI.  Boot Lubuntu and open a terminal and run the following command:

```
 sudo ls /boot/efi/EFI
```

You will be prompted for the sudo (primary user) password and you should see entries for both windows and Lubuntu.  The Lubuntu entry will be ubuntu and the windows entry will be Microsoft.  If you only show ubuntu, then Lubuntu is UEFI and windows 7 is Legacy and Grub will not boot a Legacy windows from a UEFI install of Linux.  You will need to boot and install Lubuntu in Legacy mode.  Another option is to run the command:  ls /sys/firmware/efi to determine if Lubuntu is UEFI.

You can also run the command below and if the machine is UEFI capable you will see different variables and if it is not you will see a message saying UEFI variables are not supported. 

>  sudo efibootmgr

If the problem isn't Legacy windows install with UEFI Lubuntu, post back for more suggestions.  This is about the most common problem in this situation.

---

### Post by Impavidus on 2022-11-17
You could use [boot-repair](https://help.ubuntu.com/community/Boot-Repair) to create a boot info summary. That should tell us all the details. Running the recommended (that is default) repair is not so likely to work here and could do harm.

A mix-up of UEFI mode and legacy mode is one of the possible explanations. Do you remember changing those settings before running your Lubuntu live disk?

---

### Post by lord-carnarvon on 2022-11-17
Hi, thanks for suggestions. Hmmm... hadn't thought of the UEFI issue but I am pretty sure this thinkpad is only BIOS.
ok so tried
paul@paul-THINKPAD:~$  sudo ls /boot/efi/EFI 
[sudo] password for paul:
 ls: cannot access '/boot/efi/EFI': No such file or directory
[FONT=Ubuntu Mono][COLOR=#000000]paul@paul-THINKPAD:~$ ls /sys/firmware/efi [/COLOR][/FONT]
[FONT=Ubuntu Mono][COLOR=#000000]ls: cannot access '/sys/firmware/efi': No such file or directory[/COLOR][/FONT]
[FONT=Ubuntu Mono][COLOR=#000000]paul@paul-THINKPAD:~$ sudo efibootmgr[/COLOR][/FONT]
[FONT=Ubuntu Mono][COLOR=#000000]sudo: efibootmgr: command not found

appears that it's not a UEFI issue?  will have a look at boot-repair (thanks impavidus) & post results[/COLOR][/FONT]
 
well... tried boot-repair & got the results, seems as if not a UEFI thang, the info said something about missing MBR, 
btw have been using the thinkpad for these posts, so it is working, however...
got brave when using boot-repair info & decided that I would let boot-repair do it's recommended repair, so ha-ha .I'm now writing this post under win7 but THAT is now the only boot, no boot options, just straight into win7 .

So now I'm stuck in win7 & can't access the boot-repair info summary on /var     (suppose I can install a ext fs reader, just posting this quickly while I step back & think about things)

---

### Post by lord-carnarvon on 2022-11-18
Hi again,
got it all working (typing this under Lubuntu), just installed easybcd under win7, added linux boot entry (also added grub boot entry) & it worked. Took approx 3 minutes from download of easybcd, EVERYTHING works great. 
Thanks to all who tried to help though

---

### Post by Impavidus on 2022-11-19
Then hope it continues to work, even after installing updates. In particular updates to the kernel and grub. Your configuration seems a bit fragile. With easybcd (installed from Windows) loading grub, which then loads Linux, on a legacy system, it looks like you installed grub to a partition boot record.

---

