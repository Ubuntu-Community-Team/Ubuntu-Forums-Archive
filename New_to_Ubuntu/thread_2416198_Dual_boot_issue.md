---
title: "Dual boot issue"
date: 2019-04-06
forum: New to Ubuntu
---

### Post by trungdinh on 2019-04-06
Hi,

I would like to post here since I had a problem while dual booting Window and Linux. I have an Asus FX503VM laptop and I am dual-booting Xubuntu 18.04 lts. After an update, I can still boot to Xubuntu but not Window anymore. When trying to boot to Window, it's stuck on black screen with Asus logo, then boot again and again (infinite loop). I try to repair with boot-repair, but in the report it's shown that boot-repair failed. 

Boot repair pastebin: [http://paste.ubuntu.com/p/nvMSD9xwWH/](http://paste.ubuntu.com/p/nvMSD9xwWH/)

I also thought of boot with Window usb live to repair window boot, but it cannot boot to window usb either. I think it's weird, since it can still boot normally to Xubuntu.

I appreciate any help for my situation.

---

### Post by yancek on 2019-04-06
Your boot repair shows it found the windows entry.  When you boot, do you see the Grub menu and get the problem when you select the windows option?  Do you have Boot Options in the BIOS where you can select to boot from an efi file and select windows that way.  If so, does it boot?  Some computers such as HP have this option.  Not sure about Asus.

I noticed that the EFI partition is not marked as active/boot, at least in boot repair.  You can check that and change it if necessary using GParted.  Make sure the EFI partition (sda2) is NOT mounted when you do this.  In GParted, click the Partition tab and then the Manage Flags option and make sure the boot and esp boxes are checked.  Don't see anything else that might be a problem.

---

### Post by trungdinh on 2019-04-07
Hi yancek,

Thank you for your suggestion. So, I checked your points.

For your first questions, when I boot, I can see the grub menu with option to boot to Window. I can also see boot option to Window in BIOS (it's UEFI for me in fact). I can select the boot priority, enable/disable fast boot, secure boot, etc., but I am not sure that I see something like boot from efi. 

For your second point, I checked with GParted on sda2 and it has boot and esp flags. It means that EFI partition is active for boot, doesn't it? Besides, I found that there is sda3 appearing with a yellow triangle when I look at GParted. I attach the printscreen below. I don't know if it may indicate some kind of errors?

If none of them above may cause problem, can you think of other possibilities? Indeed, the fact is that I can still choose window but when I boot to Window, it just cannot and then reboot again and again. It is just confused for me that I dont know if it's a boot problem or other problems. And the story that I cannot boot to usb with bootable Window, while I still can with bootable Linux really makes me more confused.

I really appreciate any other help.

---

### Post by yancek on 2019-04-07
I don't know what sda3 might be as I rarely boot windows.  It might be an unformatted partition which might be why you see the yellow icon.
When you are in the BIOS, do you have an option "OS Boot Manager"?  If you highlight it and hit the Enter key, do you see options for Ubuntu and windows?  If so, can you boot to windows?  I don't really have any other ideas unless there is a problem with the windows filesystem  Can't fix that from Linux.  Have you tested your windows boot usb on another computer?  If so, does it boot?

---

### Post by oldfred on 2019-04-07
The Microsoft Reserved partition is requried to be unformatted. And gparted flags unformatted partitions. But it should not as a Microsoft reserved partition it has a valid GUID and is required to be unformatted.
[https://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](https://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Is Windows fast start up on? That often is a reason.
Grub only boots working Windows. And if grub does not boot Windows you may be able to directly boot from UEFI. If not then a Windows issue which Linux cannot fix and you will need your Windows repair disk or installer with repair console.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

