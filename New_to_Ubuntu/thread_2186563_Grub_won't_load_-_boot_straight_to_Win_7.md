---
title: "Grub won't load - boot straight to Win 7"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by mbphillips83 on 2013-11-07
I have an HP Pavilion HPE desktop with two 1TB HDs installed. The desktop came with one hard drive and I installed the second. My intent is to dual boot with Windows 7 on one hard drive and Ubuntu 13.10 on a 150GB partition of the second drive.
I installed from Live CD. Win 7 was not recognized so I manually created necessary partitions and installed. Installation seemed to work fine. When I start the computer it boots directly to Windows. I have made sure that the Ubuntu drive has priority over the Windows drive. I am lost. Thanks to anyone who can help. I have to warn you - I can bring up a console window, but I'm a total noob beyond that.
I ran boot-repair and got this output:

[http://paste.ubuntu.com/6374350/](http://paste.ubuntu.com/6374350/)

---

### Post by oldfred on 2013-11-08
Welcome to the forums.

You do not have grub2's boot loader installed to the MBR of the second drive. As Boot-Repair says:
>  GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. 



You can create a tiny 1 or 2MB unformatted partition anywhere on drive and add a bios_grub flag (right click to set flags). 
Then rerun Boot-Repair but do not run the auto repair as it will install grub to both drives. You want to keep the Windows boot loader on the Windows drive. Uncheck auto repair in advanced and check update MBR, then under MBR options choose your sdb Ubuntu drive and Ubuntu partition as source of system to use.

Then set BIOS to boot Ubuntu drive. 
You may have to run this to add Windows to grub boot menu after you boot into Ubuntu.
sudo update-grub

And if you ever need it you can change BIOS back to Windows or use one time boot key to directly boot Windows as it still has Windows boot loader in that drive's MBR.

---

### Post by fantab on 2013-11-08
```

Model: ATA ST31000524AS (scsi)
Disk **/dev/sda**: 1000GB
Sector size (logical/physical): 512B/512B
**Partition Table: msdos**
```

The above HDD has, as you can see above, 'msdos' partition table. Whereas the Second HDD has GPT partition table, as you can see below:

```
Model: ATA WDC WD10EZEX-00K (scsi)
Disk **/dev/sdb**: 1000GB
Sector size (logical/physical): 512B/4096B
**Partition Table: gpt**
```

You are installing Ubuntu on a GPT formatted /dev/sdb. Ubuntu will boot from GPT only if it has separate /boot partition, like oldfred points out in his post #2.

So you have two options:
1. Do as oldfred suggests, create a 2-5mb partition and add '**bios-grub**' flag to it. (I recommend this).
Or
2. Convert the Partitio table to 'msdos' with Gparted. After the conversion run [**FIXPARTS**]("http://www.rodsbooks.com/fixparts/") to remove backup GPT data. And install ubuntu.

Either way you have to change in BIOS the HDD boot priority to boot your second HDD, WDC WD10EZEX-00K or /dev/sdb FIRST. Presently its booting your /dev/sda.

---

### Post by oldfred on 2013-11-08
If not installing Windows to a gpt drive easiest to just leave as gpt. Windows only boots from gpt partitioned drives with UEFI which is on newer systems in place of BIOS. Ubuntu boots from gpt with either BIOS or UEFI if correct supporting partitions are on drive.

 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by mbphillips83 on 2013-11-08
Thanks for the fast response! I have gone into Gparted and created the partition, but when I right click to add the bios_grub flag, the "manage flags" option is greyed out?

---

### Post by oldfred on 2013-11-08
Did you run the check in menu to create partition first? Otherwise it is just a scheduled event.

---

### Post by mbphillips83 on 2013-11-10
[IMG]https://dl.dropboxusercontent.com/u/99813613/Screenshot%20from%202013-11-10%2018%3A17%3A18.png[/IMG]


Sorry for the huge screenshot. Tried to follow oldfred's instructions as closely as I could, but it didn't solve the problem.
Created the BIOS-Boot partition and applied the flag - that seems to have worked fine.
Notice my Boot Repair screen doesn't show the options that were called out. Also, my MBR Options tab is totally unavailable.
?????

---

### Post by mbphillips83 on 2013-11-10
Also, when I clicked "Apply" in Boot Repair it asked me to enter some code into the terminal. I did that fine until I came across some seperate app that asked about installing GRUB to a location. I selected my sdb drive and the next screen gave me a warning that I would not be installing anything?
I was still able to finish out the boot repair process, I believe - Just don't know how successful that was?

---

### Post by oldfred on 2013-11-10
Please attach screenshots, not in line. You can easily attach with the paperclip icon in the advance mode editor.

First test is does it boot? And if not post new link to bootinfo report.

---

### Post by mbphillips83 on 2013-11-10
It does boot, but it's still going straight into Win 7.

Here's the latest bootinfo:
[http://paste.ubuntu.com/6396748/](http://paste.ubuntu.com/6396748/)

---

### Post by fantab on 2013-11-10
Have you set the BIOS Boot Priority/Order to boot /dev/sdb FIRST, that is your second HDD with Ubuntu? Because BIOS is booting your /dev/sda with Windows is booting first, when it should be Ubuntu HDD. You can change it in BIOS Menu.

---

### Post by oldfred on 2013-11-10
It looks like the Windows boot loader is in sda and grub is in sdb. 
You need to go into BIOS and change boot order to sdb first and sda second.
You can also test with one time boot key which is f12 on my system but it does vary by vendor.

---

### Post by mbphillips83 on 2013-11-10
I dont know how that's possible. I've gone into the BIOS (F10 @ startup for my machine) and changed the order. I've even tried completely disabling the Windows drive and when I try to boot it like that it just gives an error message.

---

### Post by mbphillips83 on 2013-11-10
Attached is my boot order and second is the screen I get when I turn off Sata0.

---

### Post by fantab on 2013-11-10
Now run the Boot-Repair... and make your GRUB is being installed to /dev/sdb.

From the first screenshot, your HDD boot order is SATA1 - SATA0, its appears to be correct if SATA1 is /dev/sdb with Ubuntu on it.

---

### Post by mbphillips83 on 2013-11-10
I ran the Boot Repair. Results are in post #7 & 8.

---

### Post by mbphillips83 on 2013-11-10
If I disconnected the Windows drive from the computer and ran the Ubuntu installation again with automatic partitioning, would that solve the problem?

---

### Post by fantab on 2013-11-10
First enable SATA0, but make sure it is a second boot device, first being SATA1. If need be disable UEFI boot and switch to 'Legacy/CSM' in BIOS.
Run the Boot-Repair again, from Grub Location see that its being installed to /dev/sdb. If it still does not work post the Boot-info summary LINK.

What is happening is that When you have SATA0 or /dev/sda as your first boot device, its loading into Windows, because there is NO Grub on that HDD. To Boot with GRUB with dual-boot options you need to make the second HDD, SATA1 or /dev/sdb as your first boot device which has GRUB and Ubuntu installed to it.

Basically, its a BIOS setting that you have to manage. If need be consult the Laptop or motherboard manual to see how its done. I don't think re-installing Ubuntu will solve the issue. If all the above fails then try re-installing but I must stress that if you manage your BIOS menu you may not have to re-install.

---

### Post by mbphillips83 on 2013-11-10
fantab, SATA1 has been first in boot order since I installed Ubuntu. Boot repair has been run after. 
There are no options in my BIOS menu to disable UEFI boot or switch to legacy/csm.

Boot Info from that is here:
[http://paste.ubuntu.com/6396748/](http://paste.ubuntu.com/6396748/)

---

### Post by oldfred on 2013-11-10
You cannot be booting Windows from sdb, whether UEFI/BIOS sees that as SATA0 or SATA1 I am not sure.

When you boot from the Ubuntu drive what error message do you get? There are a few BIOS that have to see a boot flag on a partition to let you boot. Grub does not use a boot flag and with gpt a boot flag is only supposed to be on an efi partition as in gpt it is not really the same as a BIOS/MBR boot flag. If it is a BIOS error try creating a small efi partition formatted FAT32 with boot flag. In BIOS mode it should not be used, so is not vital.

---

### Post by mbphillips83 on 2013-11-10
Ubuntu is on SATA1. SATA0 is the oem drive with Windows. SATA1 is the drive I added and installed Ubuntu on. SATA1 IS set on top in boot priority. I have already attached pictures of that. When I turn OFF: SATA0(Windows drive), the computer gets hung on a screen. Picture of it is attached in an earlier post. At the bottom it reads: "ERROR: No boot disk has been detected or the disk has failed."

---

### Post by oldfred on 2013-11-10
That is a BIOS error and could be the missing boot flag type issue.

---

### Post by mbphillips83 on 2013-11-10
So I need to add a second partition with a boot flag? I already made the one flagged with [COLOR=#000000]bios_grub flag as you instructed earlier?[/COLOR]

---

### Post by fantab on 2013-11-11
Alright...

In my [post #3]("http://ubuntuforums.org/showthread.php?t=2186563&p=12842163#post12842163") I had suggested as second option that you 'create a new partition table' as 'msdos' with Gparted, and then run fixparts to remove the backup GPT data. Do that and re-create your partitions and re-install ubuntu.

EDIT: do this for the GPT HDD only.

---

### Post by oldfred on 2013-11-11
I prefer gpt, but you can convert with gdisk.

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

I often sugest both an efi partitioin and a bios_grub partition at the beginning of every new drive with gpt. Then you can boot with UEFI or BIOS or change, but not both at same time.

---

### Post by mbphillips83 on 2013-11-12
Ok, so I read a little about converting from GPT, and without spending the next three days trying to school myself on what all that means, I decided to try out another option first. I disconnected the Windows drive and just did an _automatic_ install on the Ubuntu drive. It went well and I can boot into Ubuntu fine now. GRUB wouldn't show up at first so I had to force it to show. The problem now is that GRUB isn't showing an option to load Windows 7. Just Ubuntu. I know Win 7 works because I disconnected the Ubuntu drive and Windows sparked right up. I have found articles talking about forcing the GRUB to show a Windows 7 option but it just didn't work for me. I added the following code to the bottom of /etc/grub.d/40_custom:

[COLOR=#3B3537][FONT=Inconsolata]**menuentry ‘Windows 7&#8242; {**[/FONT][/COLOR]
[COLOR=#3B3537][FONT=Inconsolata]**set root=’(hd0,0)’**[/FONT][/COLOR]
[COLOR=#3B3537][FONT=Inconsolata]**chainloader +1**[/FONT][/COLOR]
[COLOR=#3B3537][FONT=Inconsolata][B]}
[/B][/FONT][/COLOR]
On restart, GRUB shows a 'Windows option, but can't load anything.
Here's a current Boot Info

[http://paste.ubuntu.com/6408849/](http://paste.ubuntu.com/6408849/)

---

### Post by fantab on 2013-11-12
Remove what you've added and run the following in Ubuntu:

```
sudo update-grub
```

Windows Drive must be connected when you do this. If you see that, when both drives are connected, the system boot directly to Windows, then you MUST change the HDD boot order in your BIOS to boot the Ubuntu disk first.

---

### Post by mbphillips83 on 2013-11-13
Done. The problem persists.

[http://paste.ubuntu.com/6413577/](http://paste.ubuntu.com/6413577/)

---

### Post by fantab on 2013-11-13
Ok, your Ubuntu is installed in EFI-mode, Windows is not.
You have not created a 5mb unformatted partition with 'bios-grub' flag on /dev/sdb.
See if you can boot Ubuntu from BIOS/UEFI directly. If it works then you have boot from BIOS only if you want to switch between OS.

Or.. 
Do as suggested in earlier posts.
Either use 5mb partition with 'bios-grub' flag on GPT /dev/sdb Or Change the GPT disk to MBR [msdos] or re-install Windows in EFI mode changing MBR dist to GPT.

Good Luck.

---

### Post by oldfred on 2013-11-13
Grub is not installing correctly in BIOS mode. Boot-Repair tells you:

>  GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted.



Then use Boot-Repair to reinstall grub in BIOS mode and run after booting into Ubuntu (it should have already worked, but just in case):
sudo update-grub

Do not run the auto repair in Boot-Repair as that will also put grub in the MBR of sda. You want to keep Windows boot loader in sda, so from advanced uncheck auto and check update MBR and choose to reinstall grub from sdb2 into MBR of sdb.

Also since we now have drives of TB size one very large / (root) partition may force drive to read system files from anywhere on drive. A bit more efficent to have a smaller 25GB / partition and use the rest of the drive for /home or data partition(s). You may want part to be NTFS formatted to share data with Windows.

---

