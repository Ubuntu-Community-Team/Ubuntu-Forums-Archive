---
title: "Mounting NTFS drive in Kubuntu"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by binaryperson on 2012-11-23
First of all I originally posted this in the wrong section (Desktop environments) and I can't figure out how to delete the thread. My apologies to the Admins.

Hello  everyone, I have three hard drives in my computer: a 250GB XP x64 drive,  a 40GB Linux Kubuntu 10.04 AMD64 LTS drive, and a 2TB storage drive.  The problem is that when I am in Linux I can only access the 2TB drive.  When I try to access the 250Gb drive I get the error: An error occurred  while accessing '232.9 GiB Hard Drive', the system responded: mount:  according to mtab, /dev/sdb1 is already mounted on / mount failed . I  would appreciate some step by step help.

---

### Post by SeijiSensei on 2012-11-23
Post the contents of the file /etc/fstab inside of [noparse]```

```[/noparse] tags.  That file lists all the filesystems that are mounted by root at bootup.  

If, as seems likely, /dev/sdb1 is the Windows partition, then you can try fixing things for yourself like this:

1)  Create a mount point in the file system for the Windows partition.  Ubuntu's manual partitioner offers /windows for this purpose during installation, and that's what I use.  So first let's create the "mount point" which is just an empty directory:

```
sudo mkdir /windows
```

2)  Now take a look in /etc/fstab and see if there is a line starting with /dev/sdb1.  It should include an entry for "ntfs" under the type of filesystem.  The second entry in the line in the mount point.  Change whatever is there to /windows, then save the file.  You can use the nano editor with sudo like this:

```
sudo nano /etc/fstab
```

You'll see a menu of Ctrl-key options at the bottom of the screen.  When you have made your changes, hold down Ctrl and hit S, then hold down Ctrl and hit X.  

3)  Now reboot.  Is the Windows drive now visible under /windows?

---

### Post by binaryperson on 2012-11-24
The contents of fstab:

```


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1cfa86dc-6b7b-4482-b3d7-96e994bb3043 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```Should I try what you suggested before or should I try something else?
I'm not sure if this is important but I'll just mention it. I installed my operating systems in the following manner: First I installed XP on my 250 GB drive, all other drives were disconnected. Then, I installed Kubuntu on my 40GB drive, all drives were again disconnected. I did it this way so that GRUB wouldn't install or interfere with XP. This way, I can remove the Linux drive and XP will boot up normally and vice versa. Not sure if this has anything to do with the problem of not mounting.

---

### Post by Mark Phelps on 2012-11-24
While fstab shows whats mounted by default, to see what is mounted at the time, do the "sudo mount" command.

---

### Post by binaryperson on 2012-11-24
sudo mount :

```

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)

```

---

### Post by SeijiSensei on 2012-11-25
If that is the case, then your Linux installation is using /dev/sdb1.  My guess is Windows is on /dev/sda.  Run "sudo fdisk -l" to get a census of your disk partitions and the devices they are on.  What filesystems have type ntfs? I'm betting it is one of /dev/sda[1-4].

If it is, say, /dev/sda1, then just follow the instructions I gave you earlier using that as the partition to mount on /windows.

---

### Post by binaryperson on 2012-11-25
Sorry, I'm new to all this. Please confirm if I should do what you stated earlier after looking at this post.

sudo fdisk -l:

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2dfa2df9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32300   244187968+   7  HPFS/NTFS
                                                                       
Disk /dev/sdb: 40.0 GB, 40016019456 bytes                              
255 heads, 63 sectors/track, 4865 cylinders                            
Units = cylinders of 16065 * 512 = 8225280 bytes                       
Sector size (logical/physical): 512 bytes / 512 bytes                  
I/O size (minimum/optimal): 512 bytes / 512 bytes                      
Disk identifier: 0x000b4eae                                            

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4660    37427200   83  Linux
/dev/sdb2            4660        4865     1648641    5  Extended
/dev/sdb5            4660        4865     1648640   82  Linux swap / Solaris

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x11a511a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243202  1953512448    7  HPFS/NTFS

Disk /dev/sdd: 1015 MB, 1015808000 bytes
32 heads, 63 sectors/track, 984 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         984      991747+   6  FAT16


```For step 1) creating the mountpoint, where am I suppose to do this, in the home folder?

```
sudo mkdir /windows
```and in step 2) which line should I change in fstab?

---

### Post by SeijiSensei on 2012-11-26
> **binaryperson said:**
> Sorry, I'm new to all this. Please confirm if I should do what you stated earlier after looking at this post.

sudo fdisk -l:

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32300   244187968+   7  HPFS/NTFS

```


That is your Windows partition; as I guessed its /dev/sda1.

> For step 1) creating the mountpoint, where am I suppose to do this, in the home folder?

It doesn't matter where you do it because the mount point is specified as an absolute path /windows.  But if you open a Terminal, you'll be in your home directory.  Just type "sudo mkdir /windows" there.

> in step 2) which line should I change in fstab?

Is there an entry for /dev/sda1 in /etc/fstab already?  If not, add a line at the bottom of the file [like this]("https://help.ubuntu.com/community/Fstab#ntfs"):

```
/dev/sda1 /windows ntfs-3g defaults,locale=en_US.utf8 0 0
```

(Don't be confused by the reference to "/dev/hda" in that documentation.  That designation is used for the older IDE drives that have been supplanted by SATA.)

---

### Post by oldfred on 2012-11-26
Is part of the issue the incorrect entry in fstab?
```

proc            /proc           proc    nodev,noexec,nosuid 0       0
[COLOR=Red]/dev/sda1  [/COLOR]     /               ext4    errors=remount-ro 0       1

```Since you unplugged drive, the LInux partition was seen as sda1, but now it really is sdb1. Main reason to use UUIDs, not device as entries in fstab.

I do not understand how it is booting, with incorrect fstab entry. Grub will override the different device setting with its search parameter, but fstab does not have a way to change dynamically.

---

### Post by binaryperson on 2012-11-26
I followed [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") instructions and I can access my drive now from the windows folder in root. Thank you for the help.

---

### Post by binaryperson on 2012-11-26
Yes, I too noticed that I have two sda1 entries now that I added windows in fstab, one Linux one Windows. But it boots and I can access the drive now. My goal was to have XP and Kubuntu totally seperate from one another. I first had only a 250GB drive plugged in and installed XP. Then the only drive plugged in was 40GB drive on which I installed Kubuntu. Then I connected all three drives. Of course, at the first bootup the only entry in GRUB was Kubuntu, but then I updated GRUB restarted and now I have Linux and Windows in GRUB. If I remove either drive that contains an operating system they will both bootup normally as if I never had dual boot(except for the XP entry in GRUB). In the BIOS I had to set my Linux drive to boot first instead of the Windows drive. What are  UUIDs?

---

### Post by SeijiSensei on 2012-11-26
> **binaryperson said:**
> Yes, I too noticed that I have two sda1 entries now that I added windows in fstab, one Linux one Windows.

No, that's not good.  Each filesystem should only be mounted in a single location.  Delete any entries in fstab for /dev/sda1 other than the one you just created that uses /windows.

UUIDs are a method of identifying devices based on unique hardware codes.  To see the UUIDs of the devices on your system run the command "sudo blkid". You'll see entries like this:

```
/dev/sda6: UUID="8ad624ae-9a0c-4c6d-af39-f2efd9216d44" TYPE="ext4" 

```

If you reference devices by UUID rather than the /dev/XXX method, the references will be immutable.  Here's how that same partition appears in my /etc/fstab:

```
UUID=8ad624ae-9a0c-4c6d-af39-f2efd9216d44 /home           ext4    defaults
```

So you could use blkid to get the UUIDs for all your partitions, then replace the /dev/sdXX entries in /etc/fstab with their UUIDs.

> **oldfred said:**
> I do not understand how it is booting, with incorrect fstab entry. Grub will override the different device setting with its search parameter, but fstab does not have a way to change dynamically.

I'm guessing the kernel entry in grub.conf has "root=/dev/sdb1" or "root=UUID=UUID_of_sdb1".  I think that overrides whatever appears in /etc/fstab as the filesystem mounted on /.  I'd also bet he has grub installed on /dev/sda, since that's clearly going to be the boot drive.

---

### Post by binaryperson on 2012-11-26
This is what my fstab file looks like after following your instructions:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identif$
# for a device; this may be used with UUID= as a more robust way to na$
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1cfa86dc-6b7b-4482-b3d7-96e994bb3043 none            swap    sw  $
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0    $
/dev/sda1 /windows ntfs-3g defaults,locale=en_US.utf8 0 0


```I should now delete the following line of code, correct?

```
/dev/sda1       /               ext4    errors=remount-ro 0       1
```Or 

should I change the last line to:

```
/dev/sdb1 /windows ntfs-3g defaults,locale=en_US.utf8 0 0
```

I'll get to UUIDs later.

---

### Post by oldfred on 2012-11-26
Because you are connecting & disconnecting drives that is why you have to use UUIDs. 

XP is hard coded in boot.ini as to drive and partition so you really want to keep it first. But Ubuntu can use UUIDs which then make it tolerant to drive order changes. 

If just booting the Ubuntu drive it will be sda1, but if the second drive when you also have XP plugged in then it is sdb1. And you have to spell out drives in both grub & Ubuntu.

---

### Post by binaryperson on 2012-11-26
I tried changing the last line of code to sdb instead of sda and I got an error at startup "windows could not mount".

---

### Post by oldfred on 2012-11-26
Windows is still sda1 unless you reverse the order you plug them in when using both drives. 

It is Ubuntu that will be sdb1 if both drives are plugged in.

---

### Post by binaryperson on 2012-11-26
I changed the first entry in which sda1 appears to sdb1 and now everything works fine.

fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identif$
# for a device; this may be used with UUID= as a more robust way to na$
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1cfa86dc-6b7b-4482-b3d7-96e994bb3043 none            swap    sw  $
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0    $
/dev/sda1 /windows ntfs-3g defaults,locale=en_US.utf8 0 0

```blkid:

```

/dev/sda1: UUID="008CFCFA8CFCEB54" TYPE="ntfs" 
/dev/sdb1: UUID="6ad30473-21e1-4651-922c-6717f164ea83" TYPE="ext4" 
/dev/sdb5: UUID="1cfa86dc-6b7b-4482-b3d7-96e994bb3043" TYPE="swap" 
/dev/sdc1: LABEL="Local Disk" UUID="0C66C40E66C3F68C" TYPE="ntfs" 

```sda1 is my 250GB Windows XP drive
sdb1 is my 40GB Kubuntu drive
sdc1 is my 2TB storage drive

Now, how would I edit fstab to use UUIDs instead of how it is now?

---

### Post by oldfred on 2012-11-26
Copy these entries into your fstab, either delete current or add # to make old entry a comment.

       sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

    

```
UUID=008CFCFA8CFCEB54 /windows ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```

Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:


```
UUID=6ad30473-21e1-4651-922c-6717f164ea83 /               ext4    errors=remount-ro 0       1
```

---

