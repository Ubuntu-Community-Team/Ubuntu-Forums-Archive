---
title: "Can't mount exfat sd card of gopro"
date: 2014-11-18
forum: New to Ubuntu
---

### Post by fio3 on 2014-11-18
HELLO EVERYONE

I am a newy:-)
A friend of mine installed linux on my small PC (used to be windows xp on it, but due to several problems as not supported anymore we changed it to linux anyway...)
My computer can't read the sdxc card (64gb) when I connect it to the computer with the usb cable (my computer has no sdxc card reader).
So I checked the forums and tries soooomany things, but after 2 hours of trying nothing worked out :(
So this is the message I have when I connect the gopro:

**Error mounting /dev/sdd1 at /media/fio/006A-8B41: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdd1" "/media/fio/006A-8B41"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'**

Can someone can help me out with this please?
I am using  Ubuntu 14.04.1
 Thank you!

Fio
I tried already the following entries:

~$ [COLOR=#ff0000]**dmesg|tail**[/COLOR]
[ 8583.236635] usb-storage 1-2:1.0: USB Mass Storage device detected
[ 8583.238541] scsi8 : usb-storage 1-2:1.0
[ 8584.237495] scsi 8:0:0:0: Direct-Access     GoPro    Storage          v2.0 PQ: 0 ANSI: 0
[ 8584.240618] sd 8:0:0:0: Attached scsi generic sg3 type 0
[ 8584.247985] sd 8:0:0:0: [sdd] 122809344 512-byte logical blocks: (62.8 GB/58.5 GiB)
[ 8584.249226] sd 8:0:0:0: [sdd] Write Protect is off
[ 8584.249241] sd 8:0:0:0: [sdd] Mode Sense: 8f 00 00 08
[ 8584.250489] sd 8:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[ 8584.263673]  sdd: sdd1
[ 8584.272994] sd 8:0:0:0: [sdd] Attached SCSI removable disk

~$ [COLOR=#ff0000]**sudofdisk-lu**[/COLOR]
sudofdisk-lu: command not found

[COLOR=#ff0000]**umount /dev/sdd1**[/COLOR]
umount: /dev/sdd1 is not mounted (according to mtab)

~$[COLOR=#ff0000]** udisks --mount /dev/sdd1**[/COLOR]
Mount failed: Error mounting: mount: unknown filesystem type 'exfat' 


I also tried to download the following:

~$** [COLOR=#ff0000]sudo apt-get update[/COLOR]**
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                      
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) trusty InRelease                              
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages/DiffIndex               
Ign [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) trusty-updates Release.gpg                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) trusty Release                                
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) trusty-updates Release                        
Hit [http://be.archive.ubuntu.com](http://be.archive.ubuntu.com) trusty-backports Release  
(.....)
Fetched 316 B in 48s (6 B/s)                                                   
Reading package lists... Done
**[COLOR=#0000ff]W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4DF9B28CA252A784[/COLOR]**

---

### Post by sudodus on 2014-11-18
Welcome to the Ubuntu Forums :-)

Try acccording to this link

[http://askubuntu.com/questions/370398/how-to-get-a-drive-formatted-with-exfat-working](http://askubuntu.com/questions/370398/how-to-get-a-drive-formatted-with-exfat-working)

> Turns out the packages from the official repositories do the trick, as long as you do a restart after installing them. :)

  Install **exfat-utils** and **exfat-fuse** packages from the official repos:
  ```
sudo apt-get install exfat-utils exfat-fuse
```
  Reboot your computer:
  ```
sudo reboot
```

---

### Post by fio3 on 2014-11-19
THANK YOU SO MUCH SUDODUS!
Problem is solved!
Can enjoy watching the videos now of our adventures;-)

Many thanks!
Fio

---

### Post by sudodus on 2014-11-19
You are welcome :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED. It will make it easier for other users at the Ubuntu Forums to find your solution.

---

