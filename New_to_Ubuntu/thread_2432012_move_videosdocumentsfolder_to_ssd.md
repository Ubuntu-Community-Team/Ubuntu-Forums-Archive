---
title: "move videos/documents/folder to ssd"
date: 2019-11-25
forum: New to Ubuntu
---

### Post by dushyant28 on 2019-11-25
Hello,
i have a new ssd on my motherboard and using the linux environment.
is there any way to move the videos or folders from linux desktop to the ssd without using the terminal?
like in windows, we can drag and drop or using copy paste.

is there any way in linux where can copy paste or drag the videos directly into the ssd?

thanks

---

### Post by Tadaen_Sylvermane on 2019-11-25
depends on the permissions of the ssd location. hard to do without the terminal, 2 seconds with it. don't be afraid.

---

### Post by dushyant28 on 2019-11-25
permission of ssd location, meaning?
location is /dev/sda for my ssd. 
i can drag or copy from ssd to other folders but cannot do vice versa.

so no other way in ubuntu to do this without terminal?

---

### Post by TheFu on 2019-11-25
Sure, but you probably need to create a Linux file system on it and then mount it first.  You can do the file system part using **gparted** but mounting it is best handled in the fstab. Performance will be faster and the fstab will mount the SSD permanently, so it is there after every boot, ready for use.

After that is done, you can drag-n-drop as much as you like AND have the best possible performance.

If you want even more flexibility, there are some things you can do for that which will make backups more consistent and if you setup the storage nicely, be much more flexible for future needs.  That requires a little more complexity.

Up to you to decide.

---

### Post by TheFu on 2019-11-25
> **dushyant28 said:**
> permission of ssd location, meaning?
location is /dev/sda for my ssd. 
i can drag or copy from ssd to other folders but cannot do vice versa.

so no other way in ubuntu to do this without terminal?

If we assume sda is correct and that you only want 1 partition .... 

sda is the whole disk.  You need to create a partition table, then create a partition (sda1), then in that partition, create a file system (use ext4).  **gparted** can do those things. There might be other GUI tools, I've never used them. You can use fdisk, gdisk, parted too.   I would actually use gparted for this stuff myself.  

Explaining the next steps using only GUI stuff is just too damn hard. Whereas explaining it using terminal commands is trivial. Any command you don't know, please check the manpage to discover what it does, what each option does.

If sda and sda1 is wrong, then these instructions will be very bad - wipe the entire OS - bad.  After each reboot, the device name can change.

To create the file system AFTER the partition is made, use
```
sudo mkfs -t ext4 /dev/sda1
```
Next you have to choose where you want this file system mounted.  I'd put it in /D, because I'm lazy and don't want long paths.
```
sudo mkdir /D
sudo mount /dev/sda1 /D
sudo chown $LOGNAME:$LOGNAME /D
chmod 775 /D
```
Bam, you have storage, mounted, ready to be used by your userid and nobody else.  If you want others to have access, that's a simple permissions thing.  Search "Unix permissions tutorial" to learn that stuff.  You can use any GUI tool, go to /D and drag-n-drop as much as you like.

We aren't done yet.  You need to put the mount into the fstab file.  1 line.
```
UUID=d62de6a2-xxxx-xxxx-xxxx-91040d274d9e     /D  ext4 nodev,noatime    0       2
```
The UUID you need **is** different from the example.  Use
```
blkid|grep sda1
```
to get the correct UUID, put that into the line, then use **sudoedit /etc/fstab** to put that corrected line into the fstab on the system.  Bottom of the file is fine. All on 1 line.  Do not get the PARTUUID.  Copy paste is your friend. I'd use 2 terminal windows. One for the editor and one for the blkid command.

That's it.   If you skip steps, I can't help.  

I would move my entire /home/ directory structure to the SSD, except the documents and videos.    Those I would leave on a spinning disk to keep the write counts on the  SSD down.  Plus, if you aren't doing video editing, there is ZERO need to put videos onto an SSD.  SSD storage is just too expensive to waste on videos, music, or other things that don't change all that often.  If you are doing video editing, then the SSD makes good sense. But only you know your requirements.

---

### Post by dushyant28 on 2019-12-04
> **TheFu said:**
> Sure, but you probably need to create a Linux file system on it and then mount it first.  You can do the file system part using **gparted** but mounting it is best handled in the fstab. Performance will be faster and the fstab will mount the SSD permanently, so it is there after every boot, ready for use.

After that is done, you can drag-n-drop as much as you like AND have the best possible performance.

If you want even more flexibility, there are some things you can do for that which will make backups more consistent and if you setup the storage nicely, be much more flexible for future needs.  That requires a little more complexity.

Up to you to decide.

i have permanently mounted the ssd by using the fstab and after the reboot it is there.
but still cannot drag and drop to the ssd. but can drag and drop outside from the ssd to other folder.

---

### Post by kevdog on 2019-12-04
So you're trying to drag and drop from your desktop folder to a folder on the SSD?
What are permissions on the folder on the SSD?  You could find these within terminal with simple ls -la command.

---

### Post by ajgreeny on 2019-12-04
You could also do what you want, after carrying out the steps shown by TheFu in post #5, by using symbolic links from the main folders already in your home (Documents, Downloads, Music, Videos, etc etc) to similarly named folders in the SSD's partition.  You could also do this by making a new /home partition on the SSD.

Both are a bit complicated to describe simply to you, but can be done in terminal with the use of a few commands.  Probably the symbolic links is the easiest way to go but let's see what others suggest.

---

### Post by TheFu on 2019-12-04
> **dushyant28 said:**
> i have permanently mounted the ssd by using the fstab and after the reboot it is there.
but still cannot drag and drop to the ssd. but can drag and drop outside from the ssd to other folder.

If only part of the instruction were followed, it won't work.
If you followed the provided instructions, it should work.  Did you?

---

