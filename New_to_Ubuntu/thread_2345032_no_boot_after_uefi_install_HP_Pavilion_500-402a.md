---
title: "no boot after uefi install HP Pavilion 500-402a"
date: 2016-11-30
forum: New to Ubuntu
---

### Post by alistair1946 on 2016-11-30
Hi, I need help with a new build. UEFI image was burned using Rufus to USB drive. Here is the post from boot repair.  [http://paste2.org/WkDnjBMI](http://paste2.org/WkDnjBMI)  includes complete script of install.
As a convert to Linux I would appreciate forum input to fix this issue. Thanks in advance. :razz:

---

### Post by ajgreeny on 2016-11-30
You may have fallen foul of the problem that HP's firmware does not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it see [http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889) 

There are a lot more tips on installing in the thread at [https://ubuntuforums.org/showthread.php?t=2147295;](https://ubuntuforums.org/showthread.php?t=2147295;) thanks to our forum's grub/UEFI guru oldfred for all of this info.

See if any of that helps you, but if still no go, come back again and give us any more information on your hardware that might help; you could even consider installing in CSM or legacy BIOS mode which might be easier for you, and may (I'm not totally sure) remove that HP UEFI firmware block on anything except boot files named Windows.

Incidentally is there a good reason for you having separate /var and /tmp partitions?
Normally we would suggest you avoid that as it adds unnecessary complications and can cause extra difficulties in management of the system

---

### Post by oldfred on 2016-11-30
It looks like you have installed in both the BIOS boot from gpt's protective MBR and UEFI boot.
But BIOS boot will not work unless you also have a tiny 1 or 2MB unformatted partition with bios_grub flag.

But your most recent report shows ESP - efi system mount in fstab, so it looks like you are configured for UEFI boot.

HP violates UEFI spec that says NOT to use description as part of boot. And only valid description is "Windows Boot Manger". But multiple work arounds.

Most with HP copy shimx64.efi to bootx64.efi and boot a fallback or hard drive entry as they still have Windows. I only have Ubuntu but also create a fallback boot entry, so I have two working UEFI entries.

But since you only have Ubuntu and no Windows, you can change/create new "Windows" entry that really boots shimx64.efi as HP's UEFI does not check file name it boots, just description.

       **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

Then in UEFI you boot Windows entry to actually boot Ubuntu. 

Boot-Repair will copy shimx64.efi and backup bootx64.efi if you check "Use standard EFI file" in advanced options. 
 
You can add your hard drive entry to boot fallback file (shows extra parameters if not default of sda1, in case others find this thread):
sudo efibootmgr -c -g -d /dev/[COLOR=#0000ff]sdX[/COLOR] -p [COLOR=#ff0000]Y[/COLOR] -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'
[COLOR=#0000ff]sdX[/COLOR] is drive, [COLOR=#ff0000]Y[/COLOR] is efi partition , yours is sda1, so you can use this:
sudo efibootmgr -c -g -d /dev/[COLOR=#0000ff]sda[/COLOR] -p [COLOR=#ff0000]1[/COLOR] -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'
Then you boot UEFI hard drive entry to boot Ubuntu.
 See also:
man efibootmgr
The ubuntu entry in UEFI just will not work with HP. You can have both the Windows entry & hard drive entries if you want.

---

### Post by alistair1946 on 2016-11-30
Hi, Thanks for the prompt replies. As this is a rebuild I don't mind how many times I have to try the install but do not want a bar of Windows any more! Getting back could take me some time as the body is old and grey. The /var and /tmp were advise from old guru friend, not sure how wise? Kindest regards Al

---

### Post by alistair1946 on 2016-11-30
Hi, Thanks for that input; now I have good reason to get engaged in self-help to remedy the situation. I will reply when I have got the grey matter grinding to deal to it. I don't want a bar of Windows bloated ware ever again! kindest regards Al

---

### Post by alistair1946 on 2016-12-03
Hi, Thanks for your wisdom. That worked a real treat. Used   sudo efibootmgr first followed by install and execution of Boot-Repair; next came second  sudo efibootmgr -c -g -d  and so on HEY Presto after reboot.
The only issue I have left is that the Broadcom Wireless card drivers are not functioning. Card ID BCM943142HMBPFXH_2 and the only drivers I have been able to locate are for Windows from the HP website. Are you able to assist here please? Kindest regards, Al

---

### Post by oldfred on 2016-12-03
My Wi-Fi has always just worked, so I have not followed those issues.
Best to post new thread with that issue in title to get those who know those issues to help.
You can search forum as I have seen multiple threads on Broadcom.
Also since so many with issues they have created a script to post data on configuration.

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
It looks like there are two different scripts, best to use one in above link.
Wireless script if wired working :
wget -N -t 5 -T 10 [https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script](https://dl.dropbox.com/s/qjc87hzk1z5x6z0/wireless_script) && chmod +x wireless_script && ./wireless_script
[http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222](http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222)

---

