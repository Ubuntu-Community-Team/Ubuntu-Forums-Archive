---
title: "Editing fstab to auto mount drive"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by streat on 2013-03-25
Hello again all! I have been through several tutorials now unsuccessfully so i am back at the forum. I am trying to edit the fstab file to mount a drive automatically for use in a samba server with greyhole. I add the drive to the fstab file according to the instructions here:

[https://github.com/gboudreau/Greyhole/wiki/MountsBestPractice](https://github.com/gboudreau/Greyhole/wiki/MountsBestPractice)

for some reason on startup it always says cannot mount "label ---" skip or manual covery. Can anyone provide some assistance? Thank you!

---

### Post by oldfred on 2013-03-26
Post these. Use code tags from Advanced editor and highlight and click on # -  for blkid output to preserve format.

 cat /etc/fstab
# To clear cache and get new view:
sudo blkid -c /dev/null -o list

---

### Post by streat on 2013-03-26
So here is the result fromsudo blkid -c /dev/null -o list 				 in terminal:

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  vfat    TRANSFER (not mounted)  01CF-12E3
/dev/sdb1  vfat             /boot/efi      D8AF-6A2C
/dev/sdb2  ext4             /              b7f905dd-c06b-4b55-bfa6-bdf8e2c539a1
/dev/sdb3  swap             <swap>         0984d2e8-89f0-4474-96c9-937136d81a8e
/dev/sdc1  ext4    HI.1000.7200.09 (not mounted) a20272df-8a59-4e42-a786-7ee550046973
/dev/sdd1  ext4    WD.500.5400.08 (not mounted) 01297d56-0b49-4dc6-b8cb-6169b93e6953
/dev/sde1  ext4    WDG.500.7200.08 (not mounted) 56ed3966-56d9-4f88-bd17-84339063981d
/dev/sdf1  ext4    WD.32.7200.08 (not mounted) 31101f2b-bcfa-4565-a297-8f666d6e973a
/dev/sdg1  ext4             (not mounted)  8c797b0f-2e01-4ac2-8bd0-e98a2d8ff3a3

What of this information needs to be entered into my fstab file?

---

### Post by deadflowr on 2013-03-26
I think the cat /etc/fstab output would be helpful.

We'd be able to see what the errors are.

---

### Post by streat on 2013-03-26
Here is what is delivered with the cat/etc/fstab command:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=b7f905dd-c06b-4b55-bfa6-bdf8e2c539a1 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=D8AF-6A2C  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=0984d2e8-89f0-4474-96c9-937136d81a8e none            swap    sw              0       0
#

samuel@TreatServer:~$ 

I dont think there is an error so much as I just have not configured it properly within the fstab file

---

### Post by Kopkins on 2013-03-26
> **streat said:**
> 
I dont think there is an error so much as I just have not configured it properly within the fstab file

That would be an error, haha. (EDIT: I see that you hven't added anything to your fstab) Which drive are you trying to mount? 

Code tags look like this (code)(/code) but use brackets  instead of parenthesis. like [ code ] but without spaces. It is better for us to help you if you post the output of the commands inside them. In the advanced post editor you can also click the # button to automatically insert them. 

You need the UUID which is that long string of stuff at the end of blkid output. It should follow the syntax in fstab
<file system> <mount point>   <type>  <options>       <dump>  <pass>
```
UUID=<your-UUID> /where/you/want/mounted (filesystem type; ext3, ext4, etc.; this is also in blkid output) (options; you should be able to use the ones from your tutorial) 0 1
```

You want it to match your fstab pretty well. it should "fit in"

good luck
Kopkins

---

### Post by deadflowr on 2013-03-26
It all looks good. However, and I don't know how important this is, the fstab commented out parts list the devices as /dev/sda, but the blkid output shows the devices as /dev/sdb.
Again, the only thing I noticed that seemed strange.

---

### Post by Kopkins on 2013-03-26
> **deadflowr said:**
> It all looks good. However, and I don't know how important this is, the fstab commented out parts list the devices as /dev/sda, but the blkid output shows the devices as /dev/sdb.
Again, the only thing I noticed that seemed strange.

Looks like he just moved the drive location. That what's nice about UUID 8-) The UUID's match for if the drive was changed from sda to sdb; comparing fstab comments to blkid output.

---

### Post by oldfred on 2013-03-26
I like morbius1's explanation as he gives template and you just need to insert your UUID and mount point. You do have to create mounts like the drive label, a name like music, videos etc, or just the drive and where you want to mount it like in /home, /mnt or /media. I find names help me know what it what.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

>  Example For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2


Be sure that the data partitions you want to mount are unmounted and then run this to make sure fstab is ok. If no errors it will mount them, or else you will see errors you need to fix before rebooting.
      
 ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a

    
You may also have to set ownership & permissions.

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

