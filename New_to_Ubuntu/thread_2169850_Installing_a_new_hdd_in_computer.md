---
title: "Installing a new hdd in computer"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by emerson1979 on 2013-08-23
Hello Everyone
                        I'm trying to  install a new HDD. I'll give so some outputs to give an idea of where I'm
at.

  	 	 	 	   an@dan-MS-7369:~$ blkid 
 /dev/sda1: UUID="fd0435a8-ec0d-45a9-93f3-a3638ce77a24" TYPE="ext4"  
 /dev/sda2: LABEL="_CentOS-6.4-x86_" UUID="ff6cfa12-2f82-41f6-83d4-cb45068e089b" TYPE="ext4"  
 /dev/sda3: UUID="97932ae7-97f5-478b-8f40-dd5e5967fdab" TYPE="ext4"  
 /dev/sdb1: UUID="b7102437-1276-401a-b336-e94ac7d6330c" TYPE="ext4"  
 /dev/sdb5: UUID="06bfc3f8-796d-4659-bd02-64a398fb7cfc" TYPE="swap"  
 /dev/sdb6: UUID="25ca7960-4ca2-40b3-b5db-ea4a53980e19" TYPE="ext4"  

 /dev/sdb7: UUID="02efb423-2624-43fd-bbe8-94e68ab33a99" TYPE="ext4"  
 /dev/sdc1: LABEL="space" UUID="543ff458-da4d-4ce4-b8a8-6e3a6b5f901d" TYPE="ext2"  

 /dev/sdd1: LABEL="data" UUID="8fd68c34-251f-4b6d-bf6a-a0d8fe6a07bf" TYPE="ext4"  

 dan@dan-MS-7369:~$  

  
 

  


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=02efb423-2624-43fd-bbe8-94e68ab33a99 /               ext4    errors=remoun$
# /boot was on /dev/sdb1 during installation
UUID=b7102437-1276-401a-b336-e94ac7d6330c /boot           ext4    defaults     $
# /home was on /dev/sdb6 during installation
UUID=25ca7960-4ca2-40b3-b5db-ea4a53980e19 /home           ext4    defaults     $
# swap was on /dev/sdb5 during installation
UUID=06bfc3f8-796d-4659-bd02-64a398fb7cfc none            swap    sw           $
#/dev=/sdc1
UUID=                                                                                         defaults   0  0
543ff458-da4d-4ce4-b8a8-6e3a6b5f901d" TYPE="ext2"

  	 	 	 	   scd1 is the hdd I'm trying to install. I entered the info on  /etc/fstab(shown above) I entered the UUID and tried to save the info in nano but was unsuccessful. Could you please guide on what to do.
 

  Thank YOU

---

### Post by deadflowr on 2013-08-23
Well first off you need to determine your mount point.
The mount point is the path and place in the file directory where the drive will be mounted.
Typically, most make a directory in the /mnt folder, but you can put it almost anywhere.
An example would be
```
sudo mkdir /mnt/disk2
```
This will make a subdirectory in /mnt directory.
Then change ownership 
```
sudo chown user:user /mnt/disk2
```
When you've got your mount point figured out, then follow guide in fstab

First file system.
This is where the UUID=long-string-of-numbers-go.

Then the mount point.
This is where you add the path you've chosen. (/mnt/disk2)

Then the type
This is the type of file system, most likely ext4, but it could be others.

Then options
There are a bunch of variations for this one, but defaults is usually the best one as it covers, well the base defaults.

Then dump
Just set it to 0(zero)

Then pass
This is the setting for fsck when it runs on reboot.
The root is set as 1, meaning it gets checked first, so it's standard to set it as 2 so it runs a check after root, or 0 if you don't want it to run a pass.

So a basic line should look like this
```
UUID=[COLOR=#000000]543ff458-da4d-4ce4-b8a8-6e3a6b5f901d /mountpoint ext4 defaults 0 2[/COLOR]
```

But the mount point is critical, as without it the drive won't be anywhere.
And note you can make the mount point anywhere, really(well most anywhere, but it's best to put it where you won't mess up the rest of the system, which is why /mnt, or even your home folder are good choices)

If you want to learn more, then run
man fstab
to get an archiac experience.

added: I found this, which should give you a better understanding of fstab, and in particular, functions like options and types
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

