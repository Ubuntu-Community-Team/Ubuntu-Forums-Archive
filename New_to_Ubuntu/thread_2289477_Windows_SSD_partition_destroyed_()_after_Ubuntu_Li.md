---
title: "Windows SSD partition destroyed (?) after Ubuntu Live CD"
date: 2015-08-04
forum: New to Ubuntu
---

### Post by xjimdim on 2015-08-04
Hello there!!

I am in need of extreme help right now!! 

I think my windows partion on my KIngston 120GB SSD is destroyed for some reason and everything happened after I run an Ubuntu live disk!!

So what I wanted to do was to install a printer that was not compatible with windows 10 but had drivers for linux and ubuntu. So I went to HP's site to download the drivers and i got redirected to this site: [http://hplipopensource.com]("http://hplipopensource.com?")
So I downloaded a .run file, I made it executable and I run it with a sudo command. 

Finally not even this one could recognise my printer so I gave up and restarted to go back to windows just to find out that my SSD was not readable!!!
I booted back to Ubuntu Live disk and found out that I couldn't even open the disk from Ubuntu!!! 

What happened? I have lots of valuable files in this disk :/ Is there anyway that I can get the windows partition back??
(every other hard drive of my system is fully readable by ubuntu, when i click on my ssd though i get this error:

Error mounting /dev/sdc1 at /media/ubuntu/0AB6539CB65386DB: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sdc1" "/media/ubuntu/0AB6539CB65386DB"' exited with non-zero exit status 13: ntfs_mst_post_read_fixup_warn: magic: 0xffffffff  size: 4096   usa_ofs: 65535  usa_count: 65534: Invalid argument
Actual VCN (0xffffffffffffffff) of index buffer is different from expected VCN (0x3).
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

)

Please help

---

### Post by ruzekle on 2015-08-04
Can you run chkdsk on your SSD?

---

### Post by oldfred on 2015-08-04
Windows issue has nothing to do with your HPLIP install.

Did you leave Windows hibernated which is also its fast startup setting.
The NTFS driver will not mount hibernated NTFS partitions or NTFS needing chkdsk to prevent damage. And grub then cannot boot a hibernated NTFS partition.

You have to directly boot Windows if you did leave it hibernated. That may require temporarily restoring the Windows boot loader if BIOS, or using UEFI menu to boot Windows. And maybe use f8 to get into repair console.
Or boot with Windows repair CD or flash drive which you should have.

 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
      
 WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast startup
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

---

### Post by alextop30 on 2015-08-04
Run chkdsk utility to check the system and the startup repair tool from Microsoft. Also what does the error look like when you are trying to boot into the partition?

---

