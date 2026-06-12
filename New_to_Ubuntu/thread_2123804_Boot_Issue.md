---
title: "Boot Issue"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by rL1rj19Ko2 on 2013-03-09
Hello Community,
       I am brand new to this forum, and to all operating systems other than Windows! I am currently working at Cisco Systems and am in school at a certification program to finish as a Network Security Specialist. Among these multiple certifications lies Linux and a couple of others relating to the subject, so I figured it was time to get into it and figure it out for myself. I installed Ubuntu 12.10 64-bit to run along side Windows 8, and I have to say, I absolutely love it so far. 

       Anyways, for 2 days now I had been trying to figure out why my GRUB2 boot menu wouldn't load when I boot or restart, and simply loaded Windows instead unless I interrupted the startup and chose Ubuntu from the boot device list. I dug around everywhere and finally discovered that I needed to perform the bcdedit command in Windows, and finally got it to work. Now it takes me to the GRUB2 boot menu to select either Ubuntu or Windows. BUT now, when I select Windows it gives me the following error:
error: can't find command 'drivemap'
error: invalid EFI file path

PLEASE HELP I can't boot back into Windows!
 When I get this issue fixed, I know that there is a different looking boot menu in WIndows 8 that I have seen before when installing incorrectly (lol). It looks like a WIndows 8 tile screen, and allows you to select the operating system you would like to run. I apologize for the lengthy post but I hope someone can help me thanks in advance!!!

---

### Post by dulbirakan on 2013-03-09
I am not sure if I understand the problem correctly but is it similar to this? [http://askubuntu.com/questions/210064/ubuntu-12-10-in-wubi-boots-fine-but-grub-does-not-show](http://askubuntu.com/questions/210064/ubuntu-12-10-in-wubi-boots-fine-but-grub-does-not-show)

---

### Post by varunendra on 2013-03-09
Welcome to the forums JWhite1089 !

Please use default fonts for normal text. Non-default fonts are used only for parts of a post to highlight important stuff.

Thanks.

---

### Post by varunendra on 2013-03-09
Welcome to the forums JWhite1089 !

Please use default fonts for normal text. Non-default fonts are used only for parts of a post to highlight important stuff.

Thanks.

---

### Post by rL1rj19Ko2 on 2013-03-09
Sorry about the font, that's no problem at all. I am currently using default, at least it doesn't tell me any differently in the upper font menu..

But no that's not really the problem. I've read a ton of articles like that where people want to get RID of their grub menu, whereas my problem was the opposite. It was booting directly into Windows 8 and bypassing grub altogether. I did find one or two instances where this was the case, and someone posted instructions when this happens to enter the following command in a Windows command prompt: bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi

Please note, this command WORKED in the sense that I now get the purple grub menu at boot, and it also works when you select Ubuntu. It takes you right to the Ubuntu login, however, if you select to boot Windows 8 from grub, you get the following two errors:
error: can't find command 'drivemap'
error: invalid EFI file path.

Press any key to continue...

It's like it can't find the correct file path for Window 8 since I have changed it to grub with the previously stated command. I haven't tried to boot into Windows from the boot drive menu but either way I need to be able to access both Ubuntu and Windows 8 from the grub menu. I just ran the command sudo update-grub in Ubuntu and it did update some stuff so I'll see if that made any difference but please help! Thanks again.

---

### Post by oldfred on 2013-03-09
Best to see details of your install:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by fiodev on 2013-03-09
uninstall and reinstall grub

---

### Post by rL1rj19Ko2 on 2013-03-10
> **oldfred said:**
> Best to see details of your install:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Okay, the link is [http://paste.ubuntu.com/5603591](http://paste.ubuntu.com/5603591). I am going to follow the second link and perform a boot repair as well, however, after I went into boot device options and selected to boot from the hard drive, it booted into Windows, and since then, it has been booting directly into Windows bypassing the Ubuntu grub screen.
Also, when I went into the boot device options, I noticed that there were like 5 instances of Ubuntu to boot from. What is causing this? There are also a lot of extra partitions on my disk than there were before, and I'm not sure which ones I can remove. I want only the minimum amont of partitions needed to run Windows 8 and Ubuntu. I ran the boot repair and it told me to create a new boot partition. Here is the link that it gave me after the boot repair completed:  [http://paste.ubuntu.com/]("http://paste.ubuntu.com/5603591")[5603603/]("http://paste.ubuntu.com/5603603/") I am going to reboot now and see what happens. Hope this helps! Please let me what I need need to do to correctly configure dual-boot on Windows 8 and get rid of all these extra partitions! Thanks!

---

### Post by rL1rj19Ko2 on 2013-03-10
I rebooted and it booted directly into Windows. I then rebooted again and went into the boot device options, and there were only 2 instances of Ubuntu this time. I chose to boot into the top Ubuntu selection, and it took me to the grub screen, which had many more options on it this time. I don't know what's going on. Please let me know what you think after you read the boot logs! Thanks!

---

### Post by oldfred on 2013-03-11
Because HP put all the recovery .efi files in the efi folder, Boot-Repair added all the options. You may need them someday, but if you want you can manually delete from 25_custom. All the entries in 25_custom are from Boot-Repair.

Do both Ubuntu and Windows boot ok?

UEFI saves some entries in its own memory and may need separate updated or editing from UEFI. I used to think it read efi folder each time, but it seems it saves entries.

---

### Post by rL1rj19Ko2 on 2013-03-11
> **oldfred said:**
> Because HP put all the recovery .efi files in the efi folder, Boot-Repair added all the options. You may need them someday, but if you want you can manually delete from 25_custom. All the entries in 25_custom are from Boot-Repair.

Do both Ubuntu and Windows boot ok?

UEFI saves some entries in its own memory and may need separate updated or editing from UEFI. I used to think it read efi folder each time, but it seems it saves entries.

Windows and Ubuntu boot fine, but only when I interrupt the startup and select to boot off of the HDD or Ubuntu option. It's been very random; yesterday it was booting directly into Windows and I just booted up for the first time today and it went to the grub screen. Although the last time I tried to boot Windows off of the grub screen it gave me the errors. Something's not right.

---

### Post by oldfred on 2013-03-11
I missed it. Boot-Repair did not add the efi Windows entries into 25_custom like it normally does.

You can manually add your own. See bug report for examples. The entries from os_prober will not work.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by rL1rj19Ko2 on 2013-04-03
> **oldfred said:**
> I missed it. Boot-Repair did not add the efi Windows entries into 25_custom like it normally does.

You can manually add your own. See bug report for examples. The entries from os_prober will not work.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

Well I went to boot up last night and give this a shot but it took me directly to a blank page in the following format:

error: unknown filesystem.
grub rescue> _

I have researched this extensively and tried a number of things but nothing is working. I did not do anything to make this happen; I was on my laptop (in Windows 8) for a few hours and it was working just fine. I shut it down appropriately, and when I rebooted later that day I got that message. All of the commands that I have seen are not working. For some reason, when I type the "ls" command and it shows me my partitions, there are SEVEN partitions, as well as (hd0) and (cd0). Where did all of these partitions come from? I have tried to view folder contents of EVERY partition that it shows, and every time it says "unkown filesystem" it's as if there are no boot files anywhere. Please help, I've got to get this laptop working again asap. I do not have my liveCD, and I cannot get it to boot off of the CentOS liveCD that I got from my buddy. It gives me the same error: unkown filesystem.

I've had so many issues with this since day one here's what I want to do... I want to recover my Windows system, delete all Ubuntu partitions and return my laptop to how it came from the factory WHILE RETAINING MY DATA (no, I did not make a backup, the computer is only a couple of months old.. Shoulda coulda woulda..). I then want to reinstall Ubuntu 12.10 CORRECTLY with only the minimum number of partitions. But first, I need to get it working again. Any help would be greatly appreciated.

---

### Post by oldfred on 2013-04-03
With UEFI, there are a lot of partitions, several are unformatted. Windows needs a Windows repair, an efi, a unformatted reserved, main install, and vendor recovery. Then Ubuntu will add its main install and swap. Ubuntu will use the same UEFI partition. If you install incorrectly in BIOS mode it will also add a unformatted bios_grub to boot in BIOS mode.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

    
Are you booting in UEFI mode with secure boot either on or off. Or are you booting with CSM/BIOS/Legacy mode. Windows will only boot in UEFI mode and some systems will only boot with Windows in UEFI mode and secure boot on.
Ubuntu will boot in all modes, if configured to boot in that mode, but if booting Ubuntu in CSM/BIOS you cannot dual boot Windows from grub menu.

Post latest BootInfo report. Error looks more like an old BIOS boot error not UEFI boot error.

---

### Post by rL1rj19Ko2 on 2013-04-06
[QUO*[I][I][I]*[/I][/I][/I]TE=oldfred;12586794]With UEFI, there are a lot of partitions, several are unformatted. Windows needs a Windows repair, an efi, a unformatted reserved, main install, and vendor recovery. Then Ubuntu will add its main install and swap. Ubuntu will use the same UEFI partition. If you install incorrectly in BIOS mode it will also add a unformatted bios_grub to boot in BIOS mode.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

    
Are you booting in UEFI mode with secure boot either on or off. Or are you booting with CSM/BIOS/Legacy mode. Windows will only boot in UEFI mode and some systems will only boot with Windows in UEFI mode and secure boot on.
Ubuntu will boot in all modes, if configured to boot in that mode, but if booting Ubuntu in CSM/BIOS you cannot dual boot Windows from grub menu.

Post latest BootInfo report. Error looks more like an old BIOS boot error not UEFI boot error.[/QUOTE]

This was a big help, thanks; I now know that my system is supposed to have 5 partitions. I have uninstalled Ubuntu and restored my system to its previous state with only 5 partitions. I'm going to hold off on reinstalling until I can get a hard answer on exactly what I need to do to get this booting exactly like I want (from the pretty Windows 8 bootloader :)). I still have a few issues with Ubuntu being in my boot options but I suppose I'll open a new thread for that. Thanks to everyone for the support.

---

