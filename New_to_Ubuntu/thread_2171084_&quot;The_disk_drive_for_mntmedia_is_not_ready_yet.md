---
title: "&quot;The disk drive for /mnt/media is not ready yet or not present&quot;"
date: 2013-08-29
forum: New to Ubuntu
---

### Post by pat4 on 2013-08-29
All,
I have a system with three hard drives installed, all formatted to ext4. One is the main system disc, the others are used for backup and data storage. 

On booting the machine I see a message that reads:
"The disk drive for  /mnt/media is not ready yet or not present. Continue to wait or press S for skip, M for manual recovery"

If I press S (skip) the machine boots OK and all discs become accessible from the home folder side menu. 
Checking in gparted information shows the all the discs as being mounted - one in /media/New Volume
and one in    /media/04d72ae4-3bb2-43d4-8011-c0f3ba9e3632

It seems that the discs are working OK and the message is in some way spurious.

Here is a copy of my fstab entries:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5066087f-fdc8-4b6e-8648-50ee9710c837 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a373ddae-db9c-4c44-8b91-5131786bd626 none            swap    sw              0       0
UUID=646740b5-4d23-4c8f-a580-8cfa63b0ab23 /mnt/media/     ext4 relatime 0 2

Obviously, I would like the machine to boot cleanly without having to press S so any help with a possible cause and resoulution for the problem would be appreciated.

Thank you in anticipation.

---

### Post by mastablasta on 2013-08-29
/media is usually for external devices such as CD, DVD and such.

---

### Post by steeldriver on 2013-08-29
It sounds like the one referred to in your fstab is an obsolete UUID, if you're happy to let the system automount the backup / data disks then you can just edit fstab and remove that line.

OTOH if you want fstab to mount the drives (so you can mount them somewhere other than /media for example) then start by identifying the actual current UUIDs using the blkid command

```
sudo blkid
```

 then adjust fstab accordingly.

---

### Post by pat4 on 2013-08-29
Thank you both for your help..

I checked the UUID numbers and corrected the one that was wrong. Original message at boot now does not appear however another problem has now arisen following the changes made.
When I click on "home folder" the drive in question has disappeared from those listed under "devices" in the left hand column. Checking in gparted tells me that the drive is actually present and mounted.

How can I enable the system to show me the drive (and thus give me access to it) at boot up?

Mastablasta tells me that the drives are mounted in the wrong place - can you tell me where I should have mounted them please? and how to change it if necessary?

Forgive my ignorance - I am new to Ubuntu - and I have tried to find the answer on the web but with no luck.

Regards,

---

### Post by oldfred on 2013-08-29
There is lots of discussion (arguement) over the correct place to mount a drive. If an external drive like a USB hard drive or flash drive it will default mount to /media. But many say you should mount to /mnt if an internal drive.

But Nautilus only shows the /media mounts by default. You can also directly mount in /home. But I used to find mounts in /media would show twice, the second time with an underscore at the end and users would get confused. Where ever you mounted it, you should be able to open that mount in the left panel of Nautilus and drill down to where you mounted it (seems like long way around?).

I actually use /mnt/data for all my data partitions, but then link the folders from the data partition into /home so I see each folder in /home. It just depends on how you want to see data.

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by deadflowr on 2013-08-29
I think mastablasta misread where you've mounted the partitions.

Though the folder is media, the actual mount point directory is /mnt.

In reality, you can mount a partition anywhere you want.
As long as it is mounted after root(/).( /mountpoint = good, mountpoint/ = bad )
You can even make your own directory if it pleases you.
Even though, you can mount it anywhere, it is probably best not to.
Sticking it to the /mnt directory, or maybe somewhere in the /home folder should be best.

So long story short, it's fine where it is.

---

### Post by CaptainMark on 2013-08-30
I think oldfred was emphasising more that Nautilus will only display an entry in devices if the drive is mounted under /media so you can mount it in /mnt if you want but you'll merely have to create a bookmark manually in Nautilus. At least thats the impression I got, I don't use Nautilus but Nemo instead and that holds true here

---

### Post by pat4 on 2013-08-31
Thak you to all who responded. It seems I was under a misapprehension - caused no doubt by my basic lack of understanding of Ubuntu file systems and heirarchy. This is something I am trying hard to correct..

My "problem" is now resolved and I am very grateful for all the help received.

Best regards,

---

