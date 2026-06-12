---
title: "How to remove sda1 from grub menu"
date: 2016-05-26
forum: New to Ubuntu
---

### Post by arranskye on 2016-05-26
**Set up:**  ssd drive ubuntu and toshiba HDD Windows:  Installed windows on Toshiba hdd on a PC with ubuntu **already installed. **Windows demanded a partition for system reserved. Allocated a 500mb partition but windows did not input any files into it. Not MBR or anything else. Result 500mb became free space located in front of the NTFS partition.  Both systems run in mdos mode
**Grub menu:** Ubuntu : sda1 windows boot loader :** sdb2** windows boot loader.  Ubuntu  booted up fine. sda1 & sdb2 . Both booted windows fine but only mounted in ro mode so unable to use windows files from ubuntu. I spent several weeks trying to get windows to mount rwe but failed. Error messages insisted that windows was hibernated but I had disabled secure boot & fast boot in the bios and fast boot hibernation etc in the os immediately following installation.  Eventually I gave up and successfully merged the free space partition with windows ntfs drive. I used boot repair.
**New grub menu**:  Ubuntu : sda1 windows bootloader **: sdb1** windows bootloader.  **sdb1** boots into windows fine including rwx mode.  sda1 tries to boot but enters windows boot repair screen. Result: After selecting Ubuntu to boot an error screen appears with S Skip or M manual repair. clicking S goes straight into Ubuntu.  
It would appear first, that  the small free space partition caused grub to conclude that windows was hibernated when it wasnt and boot repair removed the grub/mbr files from sda1
 Is there any way I can remove sda1 from grub to stop this error page from appearing. Is it possible to get grub to chain load directly to sdb1. Please check out the annotations on the info below.

**Gksu nautilus  24[SUP]th[/SUP] may 2016**
GParted 0.18.0 --enable-libparted-dmraid --enable-online-resize
Libparted 2.3
[TABLE="width: 493"]
[TR]
[TD="width: 489, colspan: 2"]            **Set Partition Label "free space" on            /dev/sdb1**  00:00:01    ( SUCCESS           &nbsp;)             [/TD]
[/TR]
[TR]
[TD="width: 480"]            [TABLE="width: 302"]
[TR]
[TD="width: 298, colspan: 2"]                        calibrate /dev/sdb1  00:00:01    (                        SUCCESS )                         [/TD]
[/TR]
[TR]
[TD="width: 285"]                        [TABLE="width: 192"]
[TR]
[TD="width: 188"]                                    [I]path: /dev/sdb1
start: 2048
end: 1023999
size:                                    1021952 (499.00 MiB)[/I]                                     [/TD]
[/TR]
[/TABLE]
                        
                        [/TD]
[TD="width: 10"][/TD]
[/TR]
[/TABLE]
            [TABLE="width: 478"]
[TR]
[TD="width: 474, colspan: 2"]                        Set partition label to "free space" on                        /dev/sdb1  00:00:00    ( SUCCESS                       &nbsp;)                         [/TD]
[/TR]
[TR]
[TD="width: 459"]                        [TABLE="width: 270"]
[TR]
[TD="width: 266, colspan: 2"]                                    ***ntfslabel --force /dev/sdb1 "free space"***                                                                        [/TD]
[/TR]
[TR]
[TD="width: 185"]                                    [TABLE="width: 9"]
[TR]
[TD="width: 5"][/TD]
[/TR]
[/TABLE]
                                    [TABLE="width: 9"]
[TR]
[TD="width: 5"][/TD]
[/TR]
[/TABLE]
                                    
                                    [/TD]
[TD="width: 77"][/TD]
[/TR]
[/TABLE]
                        
                        [/TD]
[TD="width: 12"][/TD]
[/TR]
[/TABLE]
            
            [/TD]
[TD="width: 5"]========================================[/TD]
[/TR]
[/TABLE]
[TABLE="width: 519"]
[TR]
[TD="width: 515, colspan: 2"]           **Set Partition Label "windows" on            /dev/sdb2**  00:00:00    ( ERROR )                        [/TD]
[/TR]
[TR]
[TD="width: 506"]            [TABLE="width: 302"]
[TR]
[TD="width: 298, colspan: 2"]                        calibrate /dev/sdb2  00:00:00    (                        SUCCESS )                         [/TD]
[/TR]
[TR]
[TD="width: 286"]                        [TABLE="width: 206"]
[TR]
[TD="width: 202"]                                    [I]path: /dev/sdb2
start: 1026048
end:                                    308226047
size: 307200000 (146.48 GiB)[/I]                                     [/TD]
[/TR]
[/TABLE]
                        
                        [/TD]
[TD="width: 9"][/TD]
[/TR]
[/TABLE]
            [TABLE="width: 504"]
[TR]
[TD="width: 500, colspan: 2"]                        Set partition label to "windows" on                        /dev/sdb2  00:00:00    ( ERROR )                         [/TD]
[/TR]
[TR]
[TD="width: 491"]                        [TABLE="width: 489"]
[TR]
[TD="width: 485, colspan: 2"]                                    ***ntfslabel --force /dev/sdb2 "windows"***                                                                        [/TD]
[/TR]
[TR]
[TD="width: 476"]                                    [TABLE="width: 9"]
[TR]
[TD="width: 5"][/TD]
[/TR]
[/TABLE]
                                    [TABLE="width: 474"]
[TR]
[TD="width: 470"]                                                [I]Windows is hibernated, refused to mount.
Failed                                                to mount '/dev/sdb2': Operation not permitted
The NTFS                                                partition is hibernated. Please resume Windows and turned                                                it 
off properly, so mounting could be done safely.[/I][/TD]
[/TR]
[/TABLE]
                                    
                                    [/TD]
[TD="width: 5"][/TD]
[/TR]
[/TABLE]
                        
                        [/TD]
[TD="width: 5"][/TD]
[/TR]
[/TABLE]
            
            [/TD]
[TD="width: 5"][/TD]
[/TR]
[/TABLE]
========================================
[TABLE="width: 347"]
[TR]
[TD="width: 343"]            **Delete /dev/sdb1 (ntfs, 499.00 MiB) from /dev/sdb**              [COLOR=#b22222] Free space
        [/COLOR][/TD]
[/TR]
[/TABLE]
========================================**Delete /dev/sdb2 (ntfs, 146.48 GiB) from /dev/sdb**
[B][COLOR=#b22222]This is the windows OS but shows on grub menu as sdb1 very confusing[/COLOR]

[/B]
**gksu gedit/etc/fstab  24[SUP]th[/SUP] may 2016**


# /etc/fstab: staticfile system information. 
# 
# <file system><mount point>   <type>  <options>       <dump> <pass> 


#Entry for /dev/sda2:  
UUID=c0d626a9-d88d-4023-bf44-4bd62f1e4232    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda6: 
UUID=89d8ca57-ce09-40e5-a95e-a80cf4088897    /home    ext2    defaults    0    2
#Entryfor /dev/sda1 : 
UUID=2826E9C826E9975A    /media/System_Reserved    ntfs    defaults,nls=utf8,umask=0222    0    0  Boots into windows repair screen
#Entry for /dev/sdb1: 
UUID=62DA972ADA96F98D    /media/System_Reserved_    ntfs    defaults,nls=utf8,umask=0222    0    0
#Entryfor /dev/sdb2 :[COLOR=#b22222] does not appear on grub menu[/COLOR][COLOR=#ffffff] not appear on grub menu[/COLOR]
#Entry for /dev/sda5: 
UUID=2a1f8105-5cd2-480e-a5c6-5ff9d39efd97    none    swap    sw    0    0

  


/dev/disk/by-uuid/28F4EFDDF4EFAB70/mnt/28F4EFDDF4EFAB70 autonosuid,nodev,nofail,x-gvfs-icon=win%20x,noauto,x-udisks-auth 0 0 
/dev/disk/by-uuid/105EDF9E5EDF7B44/mnt/105EDF9E5EDF7B44 auto nosuid,nodev,nofail,x-gvfs-show 0 0

happy to provide any further info required.  Thanks.

---

### Post by oldfred on 2016-05-26
I cannot tell if UEFI install or BIOS install.
If drive is MBR, Windows only boots with BIOS.
If drive is gpt, Windows only boots with UEFI.
But both types of installs require extra partitions. 

 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by grahammechanical on 2016-05-26
Have you tried loading Ubuntu and running

```
sudo update-grub
```

Regards.

---

