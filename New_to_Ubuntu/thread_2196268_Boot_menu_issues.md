---
title: "Boot menu issues"
date: 2013-12-28
forum: New to Ubuntu
---

### Post by audentio on 2013-12-28
Hi there!

So Im having trouble actually accessing/installing? Ubuntu 13.10. Here is what is going on:

1. I have Windows 8.1 x64
2. I wanted Ubuntu so I installed it on a DVD. I do not know if it was a live DVD or not, I'm assuming not as it is a DVD-R
3. I booted from the CD drive, and got to the installation. It asked me language, etc. even partition size. I put 200GB. I did not have an internet connection, but it didnt seem to matter.
4. When it was done installing, no error message everything went smooth. I restarted, hoping to see a boot menu to tell me to either go into Ubuntu or Windows 8.1, but did not find any, it automatically went into Win 8.
5. I thought the internet connection might have missed an update, so I ran an ethernet and did a re-install along side windows 8. So Im guessing it just deleted the files then re-installed. All went well again, but..
6. No boot menu still, and no idea how to access Ubuntu

I checked in Windows -> Disk Management. I see a nameless partition of 178.6GB or something like that, and a bunch of other smaller ones which Im guessing either the manufacturer creates for backups or something, but all of them (except windows 8.1 partition) show 100% available space.

Any help would be much appreciated! I did do a search, talked about re-installing grub but I cannot get into the ubuntu terminal to run those commands, so I dont think that is what I need. I also installed EasyBCD2.2 to get a boot menu but that also only showed Windows 8.1, nothing else.

Thanks,
Mike

---

### Post by oldfred on 2013-12-29
The Ubuntu installer does not reset UEFI/BIOS to boot ubuntu entry in UEFI. You have to go into UEFI and choose what system to boot and perhaps set ubuntu as first entry.

Windows seems to like to reset itself as first in UEFI menu, so it may change if you touch BCD or some other configuration settings in Windows.

Be careful on re-installs. Some have overwritten Windows with auto install where Windows was not shown. It may just say overwrite Ubuntu. Users think it will just overwrite the Ubuntu install, but since Windows is hibernated or needs chkdsk it is not seen, it overwrite entire drive.

Did you install in UEFI mode?
With UEFI menu and efi partition, you do not need EasyBCD as a boot manager. With BIOS some preferred that over grub menu.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.


 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

---

### Post by plurga on 2013-12-29
i hope this link can help u 

[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

---

### Post by audentio on 2014-01-02
Thanks so much for responding. A bit unsure what to do, but was able to run the boot info report: [http://paste.ubuntu.com/6681338/](http://paste.ubuntu.com/6681338/)

---

### Post by chkneater on 2014-01-02
Try wth a LiveDVD 'sudo update-grub' if changing UEFI settings doesn't completely fix it.

---

### Post by audentio on 2014-01-02
Got an error that said: /usr/sbin/grub-probe: error: failed to get canonical path of /cow.

---

### Post by oldfred on 2014-01-02
You have Windows installed in UEFI mode and Ubuntu installed in BIOS mode.
You should be able to boot but have to go into UEFI, and choose Ubuntu from that. You may have to turn off UEFI and secure boot.
Then to boot Windows you have to go into UEFI menu, turn on UEFI, and turn off BIOS/CSM/Legacy boot and boot Windows entry.

You can use Boot-Repair to convert Ubuntu to UEFI install so you an always boot with UEFI. But you need to boot Boot-Repair in UEFI mode.
Do not run the suggested 'buggy' UEFI until we know if you have a system that only boots Windows or will boot ubuntu entry from UEFI menu in UEFI mode.

---

### Post by audentio on 2014-01-02
> **oldfred said:**
> You have Windows installed in UEFI mode and Ubuntu installed in BIOS mode.
You should be able to boot but have to go into UEFI, and choose Ubuntu from that. You may have to turn off UEFI and secure boot.
Then to boot Windows you have to go into UEFI menu, turn on UEFI, and turn off BIOS/CSM/Legacy boot and boot Windows entry.

You can use Boot-Repair to convert Ubuntu to UEFI install so you an always boot with UEFI. But you need to boot Boot-Repair in UEFI mode.
Do not run the suggested 'buggy' UEFI until we know if you have a system that only boots Windows or will boot ubuntu entry from UEFI menu in UEFI mode.
Thanks for the response.

First, where would I go for UEFI? And what would you recommend I do? Ideally I'd like to be prompted during POST which to boot from. Or do I always have to go to the boot menu in BIOS?

---

### Post by oldfred on 2014-01-02
UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

You may have one time boot key also.

But unless both are UEFI you have to go into UEFI/BIOS to boot. Many will let you set Ubuntu as default when both are UEFI, but Windows may periodically reset to make it first. A few have it reset on every boot.

---

### Post by audentio on 2014-01-02
> **oldfred said:**
> UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

You may have one time boot key also.

But unless both are UEFI you have to go into UEFI/BIOS to boot. Many will let you set Ubuntu as default when both are UEFI, but Windows may periodically reset to make it first. A few have it reset on every boot.

OK so I went into Bios and change boot mode from legacy to UEFI. So now I need to change ubuntu from livedvd to do the same? I also ticked off quick boot. PC beeped but then restarted and booted into windows.

---

### Post by audentio on 2014-01-02
I ran boot repair while in UEFI mode as per oldfred's suggestion and am now getting error 1962 no operating system found.

---

### Post by oldfred on 2014-01-02
Did you turn secure boot back on?

You did not run the "buggy" fix from Boot-Repair did you?

Please review links in my signature.

---

### Post by audentio on 2014-01-03
> **oldfred said:**
> Did you turn secure boot back on?

You did not run the "buggy" fix from Boot-Repair did you?

Please review links in my signature.

Not sure what you mean by buggy fix. I thought I was told to run the boot repair after I was in UEFI mode, which is what I did. 

Please don't give up on my yet :( I'd be happy to just get Windows out of hibernation mode at this point, or do I need to go to a Windows forum. I just wanted Ubuntu next to Windows, and I seem to have screwed that up but I was following directions as closely as I could.

---

### Post by oldfred on 2014-01-04
Please run a new copy of BootInfo report from Boot-Repair, so we can see where you are at.

---

### Post by audentio on 2014-01-04
> **oldfred said:**
> Please run a new copy of BootInfo report from Boot-Repair, so we can see where you are at.

Yes sir, here it is: [http://paste.ubuntu.com/6693714/](http://paste.ubuntu.com/6693714/)

---

### Post by oldfred on 2014-01-05
It looks like you have Ubuntu now installed with secure boot files in UEFI mode.
But you booted Boot-Repair in BIOS mode? You need to consistenly boot in UEFI mode.
> The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You also ran the "buggy" UEFI fix which I suggested not to run unless we know if your system only boots Windows. Run the undo function and turn secure boot off. There is also a bug in grub on booting Windows from grub menu with secure boot on.


 It looks like boot repair ran its "buggy" UEFI rename function. I am not sure it is always required, but it is for those UEFI that internally hard code UEFI to only boot the Windows efi file. So Boot-Repair renames the Windows file and makes grub2's shim be the Windows file. The UEFI thinks it is booting Windows but is really booting grub2 and then from grub2 menu you can boot Windows.

   buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)

   Boot-Repairs rename copies this /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi, becomes this:
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.
And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.


   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by audentio on 2014-01-07
> **oldfred said:**
> It looks like you have Ubuntu now installed with secure boot files in UEFI mode.
But you booted Boot-Repair in BIOS mode? You need to consistenly boot in UEFI mode.

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You also ran the "buggy" UEFI fix which I suggested not to run unless we know if your system only boots Windows. Run the undo function and turn secure boot off. There is also a bug in grub on booting Windows from grub menu with secure boot on.


 It looks like boot repair ran its "buggy" UEFI rename function. I am not sure it is always required, but it is for those UEFI that internally hard code UEFI to only boot the Windows efi file. So Boot-Repair renames the Windows file and makes grub2's shim be the Windows file. The UEFI thinks it is booting Windows but is really booting grub2 and then from grub2 menu you can boot Windows.

   buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)

   Boot-Repairs rename copies this /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi, becomes this:
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.
And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.


   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Thank you sir. I do not understand all of what you said, but I did rerun boot-repair and ticked the 'restore EFI backups', It generated another summary ([http://paste.ubuntu.com/6711094/](http://paste.ubuntu.com/6711094/)) and is now asking me to reboot. So that is what Ill do now.

---

### Post by oldfred on 2014-01-07
You should have both a Windows entry and ubuntu entry in UEFI menu. Test that both work.

If still issues with ubuntu and you get grub menu then it may be video issue.

---

### Post by audentio on 2014-01-07
> **oldfred said:**
> You should have both a Windows entry and ubuntu entry in UEFI menu. Test that both work.

If still issues with ubuntu and you get grub menu then it may be video issue.

First off THANK YOU, windows is back at least. Now I still cannot find how to boot Ubuntu but Im hoping we are close, so sorry for the trouble and am very appreciative of your support.

I might have asked this already, but still cannot find where the UEFI menu is. Im on a Lenovo. During POST, I pressed F8 for boot manager. It shows 'EUFI Boot manager'. I click it and it loads Windows. There is one other entry in the boot menu, and when I click that it goes to windows as well. Would you like me to take a screen? Can take it with a camera I guess :P

---

### Post by oldfred on 2014-01-07
You should have two keys. One is what I think you are getting which is just the one time boot key. The other takes you into UEFI/BIOS menu. Often have to check manual. Varies by vendor. See link above for what often is used by vendor, but that even changes by model.

Several examples. You should have tabs at top for different menu options.
What model Lenovo?

---

### Post by audentio on 2014-01-07
> **oldfred said:**
> You should have two keys. One is what I think you are getting which is just the one time boot key. The other takes you into UEFI/BIOS menu. Often have to check manual. Varies by vendor. See link above for what often is used by vendor, but that even changes by model.

Several examples. You should have tabs at top for different menu options.
What model Lenovo?

Here are the 3 screens I felt most relevant. None that showed Ubuntu (or Windows)

---

### Post by oldfred on 2014-01-07
Have you updated UEFI/BIOS? It looks like an early version. But some do not have updates and are just very limited.

 lenovo u310  - install Ubuntu to part of SSD Post #19 
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
Lenovo U410 How to 
[http://ubuntuforums.org/showthread.php?t=2190980](http://ubuntuforums.org/showthread.php?t=2190980)
Lenovo IdeaCentre K410 Pentium 64-bit
[http://ubuntuforums.org/showthread.php?t=2129961](http://ubuntuforums.org/showthread.php?t=2129961)
> Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.


 Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)


 Another lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not anyother entry
[http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470)

---

