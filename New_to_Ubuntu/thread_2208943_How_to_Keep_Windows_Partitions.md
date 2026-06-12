---
title: "How to Keep Windows Partitions"
date: 2014-03-03
forum: New to Ubuntu
---

### Post by bukhari2 on 2014-03-03
Hi
I'm using windows 7 and having 3 partitions c,d and e. I want to install Ubuntu and remove windows but want keep my partitions d and e as there is a lot of data . As I installed Ubuntu on my home pc but I lost all my partitions and data.
Please guide me how to install Ubuntu keeping my old partitions of windows.

---

### Post by sudodus on 2014-03-03
Welcome to the Ubuntu Forums :-)

Please run the boot info script and post the address to the pastebin  address. It will show details about your computer, that makes it  possible to give relevant advice.

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Mark Phelps on 2014-03-03
You most likely have four partitions, the other one being a boot partition for Win7 -- and if that is true, you can NOT add any more partitions; instead, you would have to remove one to create an Extended partition in its place.  The script that sudodus told you to run will show us what you have on your drive.

But BEFORE you charge into installing anything, you should use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will provide you the means to repair or restore the Win7 boot loader -- should it become damaged later.

Also, you seriously need to consider making an image backup of Win7, as folks have made the mistake of wiping out Win7 trying to install Ubuntu -- and if that is done, there is no simple way to get it back.

---

### Post by bukhari2 on 2014-03-05
hello thank you
when I type the 
sudo add-apt-repository ppa:yannubuntu/boot-repair & & sudo apt-get update
it syas   bash: syntax error near unexpected token `&'

---

### Post by bukhari2 on 2014-03-05
this is waht all I got
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair & & suduapt-get update
bash: syntax error near unexpected token `&'
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair & suduapt-get update
[1] 5827
suduapt-get: command not found
ubuntu@ubuntu:~$ You are about to add the following PPA to your system:
 Simple tool to repair frequent boot problems.

Website: [https://launchpad.net/boot-repair](https://launchpad.net/boot-repair)
 More info: [https://launchpad.net/~yannubuntu/+archive/boot-repair](https://launchpad.net/~yannubuntu/+archive/boot-repair)
Press [ENTER] to continue or ctrl-c to cancel adding it


[1]+  Stopped                 sudo add-apt-repository ppa:yannubuntu/boot-repair
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair & & suduapt-get update
bash: syntax error near unexpected token `&'
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair && suduapt-get update
You are about to add the following PPA to your system:
 Simple tool to repair frequent boot problems.

Website: [https://launchpad.net/boot-repair](https://launchpad.net/boot-repair)
 More info: [https://launchpad.net/~yannubuntu/+archive/boot-repair](https://launchpad.net/~yannubuntu/+archive/boot-repair)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpgMMlud/secring.gpg' created
gpg: keyring `/tmp/tmpgMMlud/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpgMMlud/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
suduapt-get: command not found
ubuntu@ubuntu:~$ sudo apt-get install-y boot repair && boot repair
E: Invalid operation install-y
ubuntu@ubuntu:~$ sudo apt-get install -y boot repair && boot repair 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot
E: Unable to locate package repair
ubuntu@ubuntu:~$ boot-repair
boot-repair: command not found
ubuntu@ubuntu:~$ boot -repair
No command 'boot' found, did you mean:
 Command 'boom' from package 'alliance' (universe)
 Command 'boom' from package 'prboom' (universe)
 Command 'boog' from package 'alliance' (universe)
 Command 'hboot' from package 'lam-runtime' (universe)
 Command 'brot' from package 'fortunes-de' (universe)
 Command 'booi' from package 'boo' (universe)
 Command 'booc' from package 'boo' (universe)
boot: command not found
ubuntu@ubuntu:~$ boot -repair
No command 'boot' found, did you mean:
 Command 'boom' from package 'alliance' (universe)
 Command 'boom' from package 'prboom' (universe)
 Command 'boog' from package 'alliance' (universe)
 Command 'hboot' from package 'lam-runtime' (universe)
 Command 'brot' from package 'fortunes-de' (universe)
 Command 'booi' from package 'boo' (universe)
 Command 'booc' from package 'boo' (universe)
boot: command not found
ubuntu@ubuntu:~$ boot-repair
boot-repair: command not found
ubuntu@ubuntu:~$ boot -repair
No command 'boot' found, did you mean:
 Command 'boom' from package 'alliance' (universe)
 Command 'boom' from package 'prboom' (universe)
 Command 'boog' from package 'alliance' (universe)
 Command 'hboot' from package 'lam-runtime' (universe)
 Command 'brot' from package 'fortunes-de' (universe)
 Command 'booi' from package 'boo' (universe)
 Command 'booc' from package 'boo' (universe)
boot: command not found
ubuntu@ubuntu:~$

---

### Post by bukhari2 on 2014-03-05
cant found the boot repair

---

### Post by sudodus on 2014-03-05
There should be no space between the two &-characters.

They two &-characters '&&' should be next to each other meaning logical 'and'. A single &-sign (ampersand) means that the preceding command is put to the background (released from the terminal, from where it is launched).

If you think it is confusing, you can write the commands on separate lines, which works for this purpose:

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
```
```
sudo apt-get update
```
and this line can also be written like that
```
sudo apt-get install -y boot-repair
```
```
boot-repair
```

---

### Post by westie457 on 2014-03-05
There is a small error in the command. You put an extra space in. The red X shows where the error is. sudo add-apt-repository ppa:yannubuntu/boot-repair &[COLOR=#ff0000]X[/COLOR]& sudo apt-get update

If you copy and paste the commands from the Page you were looking at[COLOR=#000000] into the terminal they will work.


Edit. Beaten to it by sudodus.[/COLOR]

---

### Post by xeonix on 2014-03-05
bukhari2:
There should be no space in between & and &
```

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update

```

---

### Post by bukhari2 on 2014-03-18
hello thank you   I got this url
[http://paste.ubuntu.com/7117801/](http://paste.ubuntu.com/7117801/)

---

### Post by sandyd on 2014-03-19
Yep, you have reached the 4-partition limit.
```

Partition Table: msdos
```

You will need to remove a partition in order to setup an extended partition for Ubuntu.

Essentially, you would

1. Create restore disks for Windows
2. Backup all your files to somewhere off the computer.
3. Identify which partition houses Windows, and carefully remove the partition (I recommend gparted)
4. Repartition the drive, creating a extended partition with the space freed up from the removal of the windows partition
5. Choose 'Something Else' when installing Ubuntu, and create a partition for root (/) and swap in the extended partition

---

### Post by bukhari2 on 2014-03-19
u mean that I should remove  sda1 before I start  installation ?

---

### Post by sudodus on 2014-03-19
> **bukhari2 said:**
> hello thank you   I got this url
[http://paste.ubuntu.com/7117801/](http://paste.ubuntu.com/7117801/)

Mark Phelps's guess was right, you have four primary partitions. That means that the partition table is full. See the output of parted.

```
=================== parted -l:

Model: ATA ST500DM002-1BD14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  106MB  105MB  primary  ntfs         boot
2      106MB   105GB  105GB  primary  ntfs
3      105GB   315GB  210GB  primary  ntfs
4      315GB   500GB  186GB  primary  ntfs

```
On the other hand, there is a lot of free space in partitions 3 and 4 as can be seen in the output of df

```
=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
...
/dev/sda1      fuseblk    100M   25M   76M  25% /mnt/boot-sav/sda1
/dev/sda2      fuseblk     98G   36G   62G  37% /mnt/boot-sav/sda2
/dev/sda3      fuseblk    196G   13G  183G   7% /mnt/boot-sav/sda3
/dev/sda4      fuseblk    173G  8.6G  165G   5% /mnt/boot-sav/sda4

```

The two first partitions are important for your Windows installation, and should be kept unchanged. See this summary:

```
============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grldr /bootmgr /Boot/BCD /grldr

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
```

I think that you can copy whatever data there is in the third partition, /dev/sda3 into the fourth partition /dev/sda4, and then ***backup everything or at least all your personal data to another drive*** for example an external drive (USB drive).

Editing partitions and installing operating systems is risky. If you have bad luck, you need the backup to be able to restore your system.

Start ***gparted*** when booted from the Ubuntu install CD/DVD/USB drive.

1. Delete the third partition (the data from there should be in the fourth partition now).

2. Create an extended partition in the unallocated space (which was used by the third partition before).

3. Create a logical partition slightly larger than your RAM. For example, if you have 4 GB RAM, make it 5 GB. Use it for linux swap.

4. Create a logical partition of the rest of the unallocated space in the extended partition. Format it to the ext4 file system. Use it for Ubuntu's root file system '/'.

5. ***Start the installer*** and install Ubuntu. At the partitioning screen, select ***Something Else***, and select the partitions, that you prepared with gparted (the root partition and the swap partition).

6. At the bottom of the partitioning screen, make sure that the bootloader will be installed to the head of the drive, where the partitions are, **/dev/sda** There should be no [partition] number, only the drive letter, which means that you install the bootloader into the head of the drive.

7. Continue the installation ...

---

### Post by sandyd on 2014-03-19
Isnt he looking to remove windows, but keep his two other partitions?

---

### Post by sudodus on 2014-03-19
You are right. I might have misunderstood. In that case it would be even easier. Just remove the two first partitions and use the unallocated space for an extended partition where to put logical partitions for Ubuntu.

Let us wait for *bukhari2* to state again if Windows should be removed, kept, or maybe backed up for a possible restore in the future.

---

### Post by bukhari2 on 2014-03-19
:confused: I ll choose ' something els' then will delete sda1 and sda2 then will create 3 drives one for boot 2nd for SWAP and 3rd for UBUNTU installation :(

---

### Post by sudodus on 2014-03-19
OK, you want to remove Windows.

In any case, please ***backup everything or at least all your personal data to another drive*** to an external drive (USB drive).

And then you can use gparted to edit the partitions:

1. Delete partitions 1 and 2.

2. Create an extended partition using all the unallocated disk space.

3. You need no separate boot partition, but it is certainly possible to have one, if you like. Then I suggest that you make it at least 512 MB, and that you remove old kernels after testing that the new ones are working. Otherwise the boot partition will soon be full, and it will not work to install or update new kernels. You can use the ***Ubuntu Tweak janitor*** for that purpose. Maybe keep one old kernel, alongside the current one.

4. So create [boot partition], root partition and swap partition as logical partitions inside the extended partition.

Then exit gparted and start the installer. At the partitioning window, select ***Something Else*** and use the partitions

---

### Post by 3rdalbum on 2014-03-19
For this situation where he just wants to remove the Windows partition and install Ubuntu, why can't he just boot the Ubuntu installer and choose the "Erase Windows 7 and Install Ubuntu" option?

Easier than using the Something Else screen, especially for a new user who doesn't know what a mount point is.

---

### Post by sudodus on 2014-03-19
He wants to keep two partitions with personal data. I do not rely on those options, too many people have erased the whole drive that way (according to threads at the Ubuntu Forums). I rely on 'Something else'. A bit more complicated, but it is clear what partitions that are selected and used. Particularly if gparted was used to prepare the partition table.

But I started to think after reading your post, *3rdalbum*.

Maybe the best method would be to get a new drive and install Ubuntu, and after that connect the old drive in an external box and copy the personal data to the new system. And finally the old drive (in the external box) can serve to store backups. There is a lot of free space in it.

---

### Post by 3rdalbum on 2014-03-19
Well, it's your prerogative what to recommend, but the "Something Else" screen is not easy for a newcomer. If you recommend the SE screen you will also need to explain to set their Ubuntu partition with a mount point of / and to set their swap at no more than 150% of their RAM. 

Otherwise I'll be answering another "Ubuntu installer says no root file system defined" thread!

---

### Post by sudodus on 2014-03-19
> **3rdalbum said:**
> Well, it's your prerogative what to recommend, but the "Something Else" screen is not easy for a newcomer. If you recommend the SE screen you will also need to explain to set their Ubuntu partition with a mount point of / and to set their swap at no more than 150% of their RAM. 

Otherwise I'll be answering another "Ubuntu installer says no root file system defined" thread!

I tried to do this in post #13. But I will not push the issue. I know that you have a long experience helping people here, and I will stand back and let you continue guiding in this thread. I understand that you know better than I about the guided alternatives for installation, and are confident giving such advice.

@*bukhari2*

*3rdalbum* suggests an easier way to install, and I suggest that you follow that way.

---

### Post by sandyd on 2014-03-19
> **sudodus said:**
> I tried to do this in post #13. But I will not push the issue. I know that you have a long experience helping people here, and I will stand back and let you continue guiding in this thread. I understand that you know better than I about the guided alternatives for installation, and are confident giving such advice.

@*bukhari2*

*3rdalbum* suggests an easier way to install, and I suggest that you follow that way.

Note that dont do this if your reinstalling ubuntu/windows dual boot, or else you will wipe everything [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by bukhari2 on 2014-04-10
finaly i installed it but now im facing problems installing softwares
see screen shots plz

---

### Post by sudodus on 2014-04-10
These programs should be possible to install. But maybe you must update/upgrade your installed systems before doing it.

From a terminal window

```
sudo apt-get update
sudo apt-get dist-upgrade

```
and then install these programs from the software center or via the terminal window

```
sudo apt-get install wine
```

and get the version, that is tested with Ubuntu. It is always risky to get newer versions, that are not tested yet. This command should install the Chromium Browser

```
sudo apt-get install chromium-browser
```

---

### Post by bukhari2 on 2014-04-14
well my Os is update but I get this msg
The following packages have unmet dependencies:

chromium-browser: Depends: libgcc1 (>= 1:4.1.1) but 1:4.8.1-10ubuntu8 is to be installed
                  Depends: libnss3 (>= 2:3.14.3) but 2:3.15.4-0ubuntu0.13.10.2 is to be installed
                  Depends: libudev1 (>= 183) but 204-0ubuntu18 is to be installed
                  Depends: libx11-6 (>= 2:1.4.99.1) but 2:1.6.1-1ubuntu1 is to be installed
                  Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.4.4-1 is to be installed
                  Depends: libxdamage1 (>= 1:1.1) but 1:1.1.4-1ubuntu1 is to be installed
                  Depends: libxi6 (>= 2:1.2.99.4) but 2:1.7.1.901-1ubuntu1 is to be installed
                  Depends: libxss1 but it is not going to be installed
                  Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-1ubuntu1 is to be installed

---

### Post by Mark Phelps on 2014-04-14
You keep adding one problem after another to this thread -- and that's making it confusing.

Please don't keep adding new problems; instead, please start a new thread for each new problem.  You'll get better response that way.

---

