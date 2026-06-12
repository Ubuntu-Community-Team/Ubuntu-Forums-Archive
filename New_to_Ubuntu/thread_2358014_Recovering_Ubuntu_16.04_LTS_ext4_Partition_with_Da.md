---
title: "Recovering Ubuntu 16.04 LTS ext4 Partition with Data"
date: 2017-04-08
forum: New to Ubuntu
---

### Post by lpfrost9929 on 2017-04-08
Hi everybody. I know this request/question has already been posted previously, I just really need to make sure that I approach this situation very delicately because I really need my partition and data back. A few hours ago, I accidently deleted my Ubuntu 16.04 LTS partition; when I tried to install Visual Studio Community 2015 on my Windows 8.1 partition. For some dumb reason, Visual Studio Community requires you to install the software across all connected drives. I did not notice that, until I tried reinstalling the software; after it failed. I now have an unallocated partition in place of my precious Linux partition. I really want to know three things:

1.) what is the safest approach to recovering my ext4 partition and files
2.) when I recover my partition, do I get all of my data back
3.) will it be more difficult to recover, the longer I wait to take action

I know I could use Test Disk to recover my partition; but I read that it could produce some damaging results, if I mess up. I want to know the safest way to approach this problem. Just in case I did not make this clear before, I do apologize for that, I am/was dual booting Windows 8.1 and Ubuntu 16.04 LTS on my laptop. Thank you all in advance for your time, and have a wonderful day!

---

### Post by oldfred on 2017-04-08
You were in the chat sub-forum, but since you really need help better to be in one of the support forums.
I put you in Beginners.

STOP using system. If partition actually deleted, you may be overwriting data with all use.

Some Windows major updates just rewrite partition table. And Windows just forgets to write the Linux partition back into partition table.
That would be best case as we can just restore partition table with testdisk or parted rescue.

Post this from 16.04 live installer:
sudo parted -l

 backup partition table before any changes, so you can get back to current if changes not correct, this can save you if you restore wrong set of partitions from testdisk.
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors:
sudo parted /dev/sda unit s print 


If partition cannot be restored with testdisk or parted rescue, then you can use photorec. But that is a slow long process and does not restore full filename, just extension. Its because it is doing a low level scan just looking for anything that looks like a file. 
I have used photorec, & learned to do better backups. I did have a backup, but I had on drive multiple .txt files. Photorec found them and all the older copies. Took me forever to first figure out which was which and then do compares to last backup to get latest data.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

 [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 
      
 [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by lpfrost9929 on 2017-04-08
Thank you for your response, oldfred. I really appreciate you for this. I did not know I had to stop using my system. The problem with that is I have to use my laptop for school work. I have some important data on the Linux partition that was needed for that, as well as other personal files. I just want to be really sure I understand what you are saying. If I am using my laptop, after I accidently deleted my Linux partition; I am actually doing my damage/decreasing my chances of recovering the partition? I have to use this laptop right now. I would have used my LiveCD, but I do not have it with me right now. I do not have any copies with me either, so that is another problem. Will recovering the partition bring everything back, as well? Thank you for your help, oldfred. I really appreciate you for this.

---

### Post by oldfred on 2017-04-09
You always need the Ubuntu live installer for current version installed and the same type of bootable flash drive for Windows as Windows repair flash drive. I believe the full Windows installer also includes the Windows repair console. If you cannot boot and do not have repair disks then you have a brick. Just keep those two flash drives in laptop case.

You can use live installer, just do not do anything that would write data into hard drive.
If you have to recover data using photorec or similar tools you need another hard drive or large flash drive(s) that can hold all of the data.
If you do not have one, get one, as that then an become the drive(s) you use to backup. 
And you must always have versioned backups. What if you dropped laptop, it got stolen, you got a ransomware virus and many other times where if you have backup, you can just restore system.

 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html) 


 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by lpfrost9929 on 2017-04-09
I made an Ubuntu 16.04.2 LTS LiveCD, today. I think I messed up yesterday. Shortly after deleting my partition, I downloaded testdisk to the Windows partition twice (it failed the first time). Is that going to damage my chances of recovering my Ubuntu partition and all of the data that I had on it? I want to thank you again for taking time out of your day to help me. I really appreciate that.

---

### Post by oldfred on 2017-04-09
Again, it depends.
We first need to see current partition layout & you need to immediately back up the existing partition structure.

---

### Post by lpfrost9929 on 2017-04-10
Alright, I am booting my system up now. I am booting up now. Sorry for the late response. I had a lot of school work to catch up on. I will post the results, after typing the commands you posted above.

Here you go.

***Edit:**
```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Hitachi HTS54323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system     Name                          Flags
 1      1049kB  420MB  419MB   ntfs            Basic data partition          hidden, diag
 2      420MB   693MB  273MB   fat32           EFI system partition          boot, esp
 3      693MB   827MB  134MB                   Microsoft reserved partition  msftres
 4      827MB   147GB  146GB   ntfs            Basic data partition          msftdata
 9      147GB   293GB  146GB   ext4
 5      293GB   294GB  887MB   ntfs                                          hidden, diag
 6      294GB   294GB  472MB   ntfs                                          hidden, diag
 7      294GB   298GB  3862MB  linux-swap(v1)
 8      298GB   320GB  22.0GB  ntfs            Basic data partition          hidden, msftdata


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: hp DVD A DS8A8SH (scsi)                                            
Disk /dev/sr0: 1554MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      7389kB  9880kB  2490kB               EFI

```[URL="https://drive.google.com/file/u/0/d/0Bwge8kIPDkbseW8xTzVaS3U0UVk/view?usp=drive_web"]
[/URL]

---

### Post by oldfred on 2017-04-10
Link does not work.
You should just be able to copy paste output from terminal to forum.
If terminal output is long, use code tags which are easy to apply with forum's advanced editor and # icon.
       How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

### Post by lpfrost9929 on 2017-04-10
I edited the source. It works now.

I had taken a picture of the screen with my phone. I will remember to do what you suggested next time. Thanks for the heads up

I uploaded am image from my phone to prevent any additional activities from overwriting my data.

---

### Post by oldfred on 2017-04-10
You show partition sda9 as Linux. 146GB Is that the partition you are looking for?

If from live installer you cannot automount it, it may need repairs.
Make sure you unmount if you run fsck.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda9 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda9
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda9

---

### Post by lpfrost9929 on 2017-04-10
I logged on here via my laptop. I hope that is not a problem to my partition. The 146GB Linux partition is the one I am looking for. Do I type in 
```

umount dev/sda9

```
 to unmount it?

---

### Post by lpfrost9929 on 2017-04-10
Is this code

```

sudo sfdisk -d /dev/sda > PT_sda.txt

```

used to backup my partitions? I have my external hard drive connected, just in case I have to store it there? If not, what is the backup command?

***Edit:** Or do you think it is this code? I just want to make sure I am doing everything right, so I can get everything back. [https://drive.google.com/file/u/0/d/0Bwge8kIPDkbseW8xTzVaS3U0UVk/view?usp=drive_web](https://drive.google.com/file/u/0/d/0Bwge8kIPDkbseW8xTzVaS3U0UVk/view?usp=drive_web)

---

### Post by oldfred on 2017-04-10
Create that file. It probably would be saved in /home on live installer, which means you need to copy it to external drive or some place else.

If you do not click on it in Naultius to see it, then it should not be mounted.
If you did not label it, it may just show with an UUID, I prefer to label all partition.

You can do the umount terminal command, use Disks or gparted to unmount also.

---

### Post by lpfrost9929 on 2017-04-10
I created the file successfully. As you said, it was located in the /home directory, and I copied it over to my External HDD. They have been labeled with UUIDs, as well. Here are the results:

```

label: gpt
label-id: AF22970F-FDA6-4112-8710-2EB48B1B4319
device: /dev/sda
unit: sectors
first-lba: 34
last-lba: 625142414

/dev/sda1 : start=        2048, size=      819200, type=DE94BBA4-06D1-4D40-A16A-BFD50179D6AC, uuid=19908716-8C0A-454B-B045-349B78C76CF0, name="Basic data partition", attrs="RequiredPartiton"
/dev/sda2 : start=      821248, size=      532480, type=C12A7328-F81F-11D2-BA4B-00A0C93EC93B, uuid=719DA7E8-D103-498B-AEE6-552622D55C67, name="EFI system partition"
/dev/sda3 : start=     1353728, size=      262144, type=E3C9E316-0B5C-4DB8-817D-F92DF00215AE, uuid=77213EC4-64EF-4F9D-9F15-82C8436307B0, name="Microsoft reserved partition"
/dev/sda4 : start=     1615872, size=   285149184, type=EBD0A0A2-B9E5-4433-87C0-68B6B72699C7, uuid=E1BA2478-2E1D-4ABE-8AD7-1E8D49EA13E7, name="Basic data partition"
/dev/sda5 : start=   571912192, size=     1732608, type=DE94BBA4-06D1-4D40-A16A-BFD50179D6AC, uuid=EAA266E9-0F8E-4C7F-97F0-1B47FF6099DC, attrs="RequiredPartiton"
/dev/sda6 : start=   573644800, size=      921600, type=DE94BBA4-06D1-4D40-A16A-BFD50179D6AC, uuid=B390C01C-6189-4249-B5DC-6CE8BF4B1F68, attrs="RequiredPartiton"
/dev/sda7 : start=   574568448, size=     7542784, type=0657FD6D-A4AB-43C4-84E5-0933C84B4F4F, uuid=26107807-12A9-4B8A-9585-9D839DDF1AC0
/dev/sda8 : start=   582111232, size=    43030528, type=EBD0A0A2-B9E5-4433-87C0-68B6B72699C7, uuid=E01535A4-533E-457E-AB1E-ED22D6F5E808, name="Basic data partition", attrs="RequiredPartiton"
/dev/sda9 : start=   286765056, size=   285146485, type=0FC63DAF-8483-4772-8E79-3D69D8477DE4, uuid=3040388F-6AD4-47E9-B5FC-313E9E20D475

```

So should I only unmount the partition I want to recover (/dev/sda9) or the entire drive (/dev/sda)? Sorry to ask so many repetitive questions. I just want to make sure I am performing this process correctly.



***Edit:** Just typed this in two minutes ago:

```

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA Hitachi HTS54323 (scsi)
Disk /dev/sda: 625142448s
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start       End         Size        File system     Name                          Flags
 1      2048s       821247s     819200s     ntfs            Basic data partition          hidden, diag
 2      821248s     1353727s    532480s     fat32           EFI system partition          boot, esp
 3      1353728s    1615871s    262144s                     Microsoft reserved partition  msftres
 4      1615872s    286765055s  285149184s  ntfs            Basic data partition          msftdata
 9      286765056s  571911540s  285146485s  ext4
 5      571912192s  573644799s  1732608s    ntfs                                          hidden, diag
 6      573644800s  574566399s  921600s     ntfs                                          hidden, diag
 7      574568448s  582111231s  7542784s    linux-swap(v1)
 8      582111232s  625141759s  43030528s   ntfs            Basic data partition          hidden, msftdata

```

---

### Post by oldfred on 2017-04-10
I do not think it is possible to mount a drive like sda. 
But yes make sure sda9 is umounted & run the fsck commands.
Then see if Naulitus shows partition or gparted. Gparted also may show errors that help figure out issue if you cannot see data from Nautilus.

---

### Post by lpfrost9929 on 2017-04-10
I will update, after entering the "**fsck**" commands.

```

ubuntu@ubuntu:~$ umount /dev/sda9
umount: /dev/sda9: not mounted

```



**Update:**
```

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda9
                                                                               
     1426003 inodes used (16.00%, out of 8912896)
        1464 non-contiguous files (0.1%)
        1654 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 1276720/605
    29272275 blocks used (82.13%, out of 35643310)
           0 bad blocks
           3 large files

     1061747 regular files
      194536 directories
          57 character device files
          25 block device files
           1 fifo
          69 links
      169624 symbolic links (148583 fast symbolic links)
           4 sockets
------------
     1426063 files

```

---

### Post by lpfrost9929 on 2017-04-10
I experienced no failures.

---

### Post by oldfred on 2017-04-10
Can you see files in Naulitus or whatever file manager you use?

---

### Post by lpfrost9929 on 2017-04-10
It says I have to install nautilus. It also said I had to enable "Universe"; so I did, and it started downloading something. I quickly cancelled it. Hopefully, it did not overwrite anything. Should I check the unallocated drive for any data?

**Update:** I do see my files and folders, after mounting my drive! Thank you so much! What do I do now?

---

### Post by lpfrost9929 on 2017-04-10
I did not use

```

sudo e2fsck -f -y -v /dev/sda9 				

```

since I did not have any problems? I know you told me to run both of the **fsck** commands; but I read where you said to use it, if I had any errors.

---

### Post by oldfred on 2017-04-11
If now you can see files, can you boot?
With UEFI, Windows updates may reset Windows to default boot choice, so you have to use f10 or f12 (check manual) to boot ubuntu entry.
And many vendors do not like to boot anything other than "Windows Boot Manager" by description. UEFI standard does not allow use of description like that.
But many work arounds, if needed.

---

### Post by lpfrost9929 on 2017-04-11
When I restarted my computer last night, I tried booting into my partition; and it booted into Windows.

---

### Post by oldfred on 2017-04-11
From UEFI boot menu often f10 or f12 check manual can you choose the ubuntu entry?
What brand/model system?

Post this from live installer:
sudo efibootmgr -v

That will show default boot order in UEFI. You should be able to change boot order in UEFI or you can use efibootmgr to change boot order.
       Change boot order with efibootmgr - o option and order you want, some require all 4 hex char others 1 is ok.
sudo efibootmgr -o 2,1
see also 
man efibootmgr
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)

---

### Post by lpfrost9929 on 2017-04-11
Sorry for the late response. My internet connection failed on me. Here you go:

```

ubuntu@ubuntu:~$ sudo efibootmgr -v
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 3001,3000,2002,2001,2003
Boot0000* Ubuntu    HD(2,GPT,719da7e8-d103-498b-aee6-552622d55c67,0xc8800,0x82000)/File(\EFI\ubuntu\grubx64.efi)RC
Boot0001* Windows Boot Manager    HD(2,GPT,719da7e8-d103-498b-aee6-552622d55c67,0xc8800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...o................
Boot0002* Internal CD/DVD ROM Drive (UEFI)    PciRoot(0x0)/Pci(0x11,0x0)/Ata(0,1,0)/CDROM(1,0xe18,0x1300)RC
Boot0004* EFI Internal Hard Disk or Solid State Disk    RC
Boot0005* EFI Internal Hard Disk or Solid State Disk    RC
Boot0006* USB Drive (UEFI)    RC
Boot0007* Internal CD/DVD ROM Drive (UEFI)    RC
Boot0009* EFI Internal Hard Disk or Solid State Disk    RC
Boot000A* EFI Internal Hard Disk or Solid State Disk    RC
Boot000B* EFI Internal Hard Disk or Solid State Disk    RC
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC
Boot3000* EFI Internal Hard Disk or Solid State Disk    RC
Boot3001* EFI Internal Hard Disk or Solid State Disk    RC
Boot3002* EFI Internal Hard Disk or Solid State Disk    RC
Boot3003* EFI Internal Hard Disk or Solid State Disk    RC
Boot3008* EFI Internal Hard Disk or Solid State Disk    RC

```

---

### Post by oldfred on 2017-04-11
What brand/model system?
Did you try to use efibootmgr to make 0000 first in boot order?

You have a lot of duplicate entries.
Not sure where they all came from?

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by lpfrost9929 on 2017-04-11
I have an HP 2000-bf69WM Notebook PC. My parents bought it for me for Christmas in 2012. Should I try

```

sudo efibootmgr -o 0000

```

to change the boot order to Ubuntu? The boot selection labelled Ubuntu on the boot selection menu boots into Windows 8.1.

---

### Post by lpfrost9929 on 2017-04-11
I entered

```

 man efibootmgr

```

in the terminal, and here is (a small part) what I received:

```

   DISPLAYING THE CURRENT SETTINGS (MUST BE ROOT).
       [root@localhost ~]# efibootmgr
       BootCurrent: 0004
       BootNext: 0003
       BootOrder: 0004,0000,0001,0002,0003
       Timeout: 30 seconds
       Boot0000* Diskette Drive(device:0)
       Boot0001* CD-ROM Drive(device:FF)
       Boot0002* Hard Drive(Device:80)/HD(Part1,Sig00112233)
       Boot0003* PXE Boot: MAC(00D0B7C15D91)
       Boot0004* Linux

```

---

### Post by oldfred on 2017-04-11
The efibootmgr without -v just shows names, not full details of what is use to boot.
That now shows Linux as 0004, I thought summary report showed ubuntu as 0000?
Or did HP delete the ubuntu entry?

Also if in working install use sudo.
The man command is to see details on terminal commands and what switches to use.

Have you run Boot-Repair? 
Do run it from Ubuntu live installer, not its own ISO.

---

### Post by lpfrost9929 on 2017-04-11
I changed the boot order, and it still produces the same result. I see now that the problem is when I tried to install Visual Studio, it wiped my Ubuntu entry from the UEFI/Bios menu. I need it. I can see the data, after typing in 

```

sudo e2fsck -C0 -p -f -v /dev/sda9

```

so that is what brings me to that conclusion.


***Edit:** For some reason, I had two Ubuntu boot entries; and only one led to Ubuntu, while the other led to Windows 8.1.

---

### Post by oldfred on 2017-04-11
It may not be Visual Studio per se, but Windows or HP doing its thing.

You probably need one of the HP work arounds.
Run Boot-Repair and let it run the cp command of shimx64.efi to bootx64.efi.

---

### Post by lpfrost9929 on 2017-04-11
Please forgive my ignorance, but are you talking about the Boot-Repair feature in Windows or Linux? If Linux, how do I do that?

---

### Post by oldfred on 2017-04-11
Boot-Repair is for Linux. It can only do a very few minor Windows fixes.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

I believe its ISO is still 14.04 based, better just to use Ubuntu live installer and add Boot-Repair ppa.

---

### Post by lpfrost9929 on 2017-04-11
How do I install it, without overwriting my Ubuntu partition? I am still logged on via my LiveCD.

**Update:** I read that I could use the LiveCD, then install it; but that makes no sense because there is no more space left on the disk. Do you think I should proceed with the installation? I do not want to lose anything.

**Update (2):** Nevermind. It just clicked that it installs to the free space on my LiveCD. I will let you know how it turns out.

---

### Post by lpfrost9929 on 2017-04-11
I tried installing Boot-Repair. Here are the results:

```

ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair
 Simple tool to repair frequent boot problems.

Website: https://sourceforge.net/p/boot-repair/home
 More info: https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp7vk5cx9h/secring.gpg' created
gpg: keyring `/tmp/tmp7vk5cx9h/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp7vk5cx9h/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK



ubuntu@ubuntu:~$ sudo apt-get update
Ign:1 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial InRelease
Hit:2 cdrom://Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2) xenial Release
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [2,828 B]    
Get:5 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial InRelease [2,828 B]
Get:6 http://archive.ubuntu.com/ubuntu xenial InRelease [2,828 B]
Get:7 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [2,828 B]
Err:4 http://security.ubuntu.com/ubuntu xenial-security InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Err:5 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Err:6 http://archive.ubuntu.com/ubuntu xenial InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Err:7 http://archive.ubuntu.com/ubuntu xenial-updates InRelease
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Fetched 2,828 B in 8s (332 B/s)     

** (appstreamcli:3912): CRITICAL **: Error while moving old database out of the way.
AppStream cache update failed.
Reading package lists... Done
E:  Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/xenial/InRelease  Clearsigned  file isn't valid, got 'NOSPLIT' (does the network require  authentication?)
E: Failed to fetch  http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease   Clearsigned file isn't valid, got 'NOSPLIT' (does the network require  authentication?)
E: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease   Clearsigned file isn't valid, got 'NOSPLIT' (does the network require  authentication?)
E: Failed to fetch  http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/xenial/InRelease   Clearsigned file isn't valid, got 'NOSPLIT' (does the network require  authentication?)
E: Some index files failed to download. They have been ignored, or old ones used instead.



ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-repair

```


**Update:** I have it working now. I will update you, after the process has been completed.

---

### Post by oldfred on 2017-04-11
You just need to post link to Summary Report that it gives, if you are ok with posting details to pastebin.

You actually are just running it in memory, unless your flash drive is configured for persistence. Even then it only saves download, it still has to be re-installed on a new boot.

---

### Post by lpfrost9929 on 2017-04-11
I am going to reboot, and tell you about the results. I will be back shortly.

**Update:** It worked! I can access everything. Thank you so much, oldfred! I will not forget this at all. You really saved my butt, man. Thank you so much for all of your time and patience, and have a wonderful day!

---

### Post by oldfred on 2017-04-12
Glad it worked. :)

You can change to [Solved].

---

