---
title: "[ubuntu] New to Ubuntu, Need Help"
date: 2015-07-25
forum: New to Ubuntu
---

### Post by kristamaranatha on 2015-07-25
I am a total newbie. I consider myself computer literate and I'm often asked to help fix Windows PCs, but Linux is all new to me. My parents asked me to fix a (former) Windows 7 computer that my brother "borrowed" and put Kali Linux on. He moved away and won't tell me the password. I don't have a recovery disk or Windows 7 install CD. Anyways, after browsing the internet I found that I could perhaps fix the Windows password with "chntpw". I was having trouble working in Kali, so I used an Ubuntu live USB to install Ubuntu. Now I'm stuck in Grub rescue ](*,)

I just want to get back into Windows 7 so I can fix the password and get rid of everything else that my brother did this computer. Please help.

I figure that my first task is to fix my problem of being stuck in Grub Rescue. I followed the steps found here: 

[http://askubuntu.com/questions/493826/grub-rescue-problem-after-deleting-ubuntu-partition](http://askubuntu.com/questions/493826/grub-rescue-problem-after-deleting-ubuntu-partition)

I ran the "ls" command and found that my Ubuntu partition is (hd0,msdos5). I get as far as the "insmod normal" and get "error:file not found"

How can I fix Grub? Are these even the right instructions for my particular situation?

---

### Post by Bashing-om on 2015-07-25
kristamaranatha; Hello;

As you have now installed ubuntu, the only help I can offer is to get ubuntu booting. We fix grub ( GRand Unified Bootloader).
To that end show us what there is to work with:
Boot the liveUSB to "try ubuntu mode" at the desktop key combo ctl+alt+t will yield a terminal interface.
Here execute terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
and post these outputs - Between Code Tags, please - maintains readability .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

From these we know where to install grub's config files.

Once grub is installed, perhaps then we can get grub to also boot Windows.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kristamaranatha on 2015-07-25
Thank you for taking the time to answer my question. 

```

sudo fdisk -lu

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00029661

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2   *      206848   635168767   317480960    7  HPFS/NTFS/exFAT
/dev/sda3       635170814  1250263039   307546113    5  Extended
/dev/sda5       635170816  1234309487   299569336   83  Linux
/dev/sda6      1234311168  1250263039     7975936   82  Linux swap / Solaris

Disk /dev/sdb: 4026 MB, 4026531840 bytes
31 heads, 30 sectors/track, 8456 cylinders, total 7864320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4a8a71bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         992     7864319     3931664    b  W95 FAT32
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA TOSHIBA MK6465GS (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs
 2      106MB   325GB  325GB   primary   ntfs            boot
 3      325GB   640GB  315GB   extended
 5      325GB   632GB  307GB   logical   ext4
 6      632GB   640GB  8167MB  logical   linux-swap(v1)


Model: Generic Flash Disk (scsi)
Disk /dev/sdb: 4027MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      508kB  4027MB  4026MB  primary  fat32        boot


```

---

### Post by Bashing-om on 2015-07-25
kristamaranatha; OK;

Let's see what we can do:
Boot the liveUSB to try ubuntu mode, to a terminal:
```

sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```
Reboot, and set the 1st hard drive as boot priority.
I do expect that you boot ubuntu, in ubuntu get to a terminal and now execute :
```

sudo apt update
sudo apt upgrade
sudo apt full-upgrade
sudo update-grub

```

With the expectation of grub picking up the Windows install, and chainloading Windows to the grub boot menu.

Reboot once more. Here now I expect that you will boot to grub with the options to choose which operating system to boot.

[INDENT][INDENT]hey it could happen
[/INDENT][/INDENT]

---

### Post by leunam12 on 2015-07-25
You can also run boot-repair:

[URL="https://help.ubuntu.com/community/Boot-Repair"]https://help.ubuntu.com/community/Boot-repair
[/URL]
After you solve your booting problem here is how you can fix the password problem:

1-Boot Ubuntu, either from HDD or from USB.
2-Using Nautilus mount the hard drive that contains Windows. Just click on it on the left pane. You know this is the right drive because you will see the Windows folder.
3-Once you have mounted the right drive press Ctrl+L (on Nautilus) to see where it is mounted. Let's say it's /media/whatever/duh.
4-Open terminal and navigate to /media/whatever/duh/Windows/System32
```
cd /media/whatever/duh/Windows/System32
```
5-Once you are in System32 type these commands pressing enter at the end of each line:
```
mv sethc.exe sethc.bak
cp cmd.exe sethc.exe
```.
You are done with Linux, now boot Windows; when you get to the login screen press the shift key five times in a row, a command line box will open.
In the command line type: ```
net user
``` you will see a list of users. Remember the name of the user whose password you want to break, lets say is ArtVandelay. Now type ```
net user ArtVandelay abc123
```Press enter. The new password is abc123.

---

### Post by kristamaranatha on 2015-07-25
Thank you for these instructions. The first set of code worked fine without error. When I went to boot from the hard drive however, I got stuck in GNU GRUB version 2.02~beta2-9ubuntu1 What did I do wrong?

---

### Post by leunam12 on 2015-07-25
You may try with chroot: boot the liveUSB open terminal and do:
```

sudo mount /dev/sda5 /mnt
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev

sudo chroot /mnt

grub-install /dev/sda
update-grub
```
Exit chroot with Ctrl+D and do
```
sudo reboot
```

However, I recommend boot-repair.

---

### Post by kristamaranatha on 2015-07-25
```

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.
root@ubuntu:/# update grub
No command 'update' found, did you mean:
 Command 'pupdate' from package 'pbuilder-scripts' (universe)
 Command 'xupdate' from package 'libxml-xupdate-libxml-perl' (universe)
 Command 'uupdate' from package 'devscripts' (main)
 Command 'lupdate' from package 'qtchooser' (main)
update: command not found

```

When trying to follow the Boot-Repair instructions in the terminal:

```

ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: https://sourceforge.net/p/boot-repair/home
 More info: https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp7td8bife/secring.gpg' created
gpg: keyring `/tmp/tmp7td8bife/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp7td8bife/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release i386 (20150218.1) trusty InRelease
Ign cdrom://Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release i386 (20150218.1) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release i386 (20150218.1) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release i386 (20150218.1) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.2 LTS _Trusty Tahr_ - Release i386 (20150218.1) trusty/restricted Translation-en
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://archive.ubuntu.com trusty InRelease                                 
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Get:2 http://security.ubuntu.com trusty-security Release [63.5 kB]
Hit http://archive.ubuntu.com trusty Release.gpg                               
Get:3 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Get:4 http://security.ubuntu.com trusty-security/main Sources [88.7 kB]        
Hit http://archive.ubuntu.com trusty Release                                   
Get:5 http://archive.ubuntu.com trusty-updates Release [63.5 kB]               
Get:6 http://security.ubuntu.com trusty-security/restricted Sources [2,061 B]  
Get:7 http://security.ubuntu.com trusty-security/universe Sources [28.1 kB]    
Get:8 http://security.ubuntu.com trusty-security/main i386 Packages [300 kB]   
Hit http://archive.ubuntu.com trusty/main Sources                              
Hit http://archive.ubuntu.com trusty/restricted Sources                        
Get:9 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
Hit http://archive.ubuntu.com trusty/universe Sources                          
Get:10 http://security.ubuntu.com trusty-security/universe i386 Packages [111 kB]
Hit http://archive.ubuntu.com trusty/main i386 Packages                        
Hit http://archive.ubuntu.com trusty/restricted i386 Packages                  
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://archive.ubuntu.com trusty/universe i386 Packages                    
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Hit http://archive.ubuntu.com trusty/restricted Translation-en                
Hit http://archive.ubuntu.com trusty/universe Translation-en                  
Get:11 http://archive.ubuntu.com trusty-updates/main Sources [223 kB]         
Get:12 http://archive.ubuntu.com trusty-updates/restricted Sources [3,433 B]   
Get:13 http://archive.ubuntu.com trusty-updates/universe Sources [127 kB]      
Get:14 http://archive.ubuntu.com trusty-updates/main i386 Packages [567 kB]    
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:15 http://ppa.launchpad.net trusty Release.gpg [316 B]                     
Get:16 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Get:17 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [11.8 kB]
Get:18 http://archive.ubuntu.com trusty-updates/universe i386 Packages [297 kB]
Get:19 http://ppa.launchpad.net trusty/main i386 Packages [1,970 B]            
Get:20 http://ppa.launchpad.net trusty/main Translation-en [2,123 B]           
Hit http://archive.ubuntu.com trusty-updates/main Translation-en               
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en           
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Fetched 1,918 kB in 14s (132 kB/s)                                             
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


```

Going to try making a boot disk repair usb next. Will post progress.

---

### Post by Bashing-om on 2015-07-25
kristamaranatha; Hey;

The CHange Root looks to have been good.
The command " # update grub " is incorrect as you missed the '-' . Correct to be
```

update-grub

```
If you are still in the CHange Root environment . Else from the install, run with " sudo" .

[INDENT][INDENT]we will, we will
[INDENT][INDENT][INDENT]get you booting
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kristamaranatha on 2015-07-25
I always miss one silly keystroke.

So that line of code worked. But when I went to reboot, I got a bunch of errors and "unable to read" lines. "input/output error"

EDIT - I restarted again and it worked!

Now I just have to fix the password

---

### Post by kristamaranatha on 2015-07-25
It worked! I have now succesfully changed the password and got back into Windows. Thanks so much for your help!

Now to reinstall Windows.

Also, how do I change this thread to SOLVED?

---

### Post by Bashing-om on 2015-07-25
kristamaranatha; Hey hey !

Bet you feel better now.
Here are easy instructions to reset your password in Ubuntu:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Here:
[INDENT][INDENT]help is on the way
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-07-25
> **kristamaranatha said:**
> It worked! I have now succesfully changed the password and got back into Windows. Thanks so much for your help!

Now to reinstall Windows.

Also, how do I change this thread to SOLVED?

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
1st post -> thread tools drop down .

[INDENT][INDENT]just my bit to try and help
[/INDENT][/INDENT]

---

### Post by leunam12 on 2015-07-25
Good! Did you use chntpw or did you follow my instructions to reset the password?

---

### Post by kristamaranatha on 2015-07-25
Problem solved =d> Thanks again for the help! (My parents thank you too)

I followed your instructions. I couldn't get chntpw to work.

---

