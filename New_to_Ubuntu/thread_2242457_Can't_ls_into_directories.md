---
title: "Can't ls into directories"
date: 2014-09-01
forum: New to Ubuntu
---

### Post by Sean_Andreas on 2014-09-01
So, I just put a new SATA drive into my desktop and I wanted to store all my music from my iTunes folder on my Macbook there. I had done that and was having trouble sharing that drive over my network. So, i moved my /home over to the new SATA and was able to share that over my network. My new problem is that I kept the music files on that drive while I was moving my /home to the same drive. I moved the music files to /home/user/Music and they showed up perfectly, but the size of my space taken up on the drive almost doubled. I deleted the original music folder and there is still an extra 30-ish GB on the drive than there needs to be (I do not have a lot else in my /home, maybe 1GB at most).

I booted from a live USB and sudo nautilus to delete more music files that were locked when I tried to delete them earlier. When I went into terminal and typed:

shondray@shondray-OptiPlex-320:~$ ls
Desktop    examples.desktop      Pictures   Temporary Items
Documents  Music                 Public     Videos
Downloads  Network Trash Folder  Templates
shondray@shondray-OptiPlex-320:~$ /media
bash: /media: Is a directory
shondray@shondray-OptiPlex-320:~$ cd /media
shondray@shondray-OptiPlex-320:/media$ ls
floppy  floppy0  home  shondray
shondray@shondray-OptiPlex-320:/media$ cd home
shondray@shondray-OptiPlex-320:/media/home$ ls
shondray@shondray-OptiPlex-320:/media/home$ cd ..
shondray@shondray-OptiPlex-320:/media$ cd shondray
shondray@shondray-OptiPlex-320:/media/shondray$ ls
Media
shondray@shondray-OptiPlex-320:/media/shondray$ cd Media
shondray@shondray-OptiPlex-320:/media/shondray/Media$ ls
shondray@shondray-OptiPlex-320:/media/shondray/Media$ 


So, I can't get into those directories for some reason. Also, as you can see my /media doesn't show up in my first ls. I don't know if that is an issue or not.

Any help would be appreciated. Thanks!

---

### Post by claracc on 2014-09-02
When you run the first ls command you are in your /home/your_user_name/ folder, for this reason media folder is not listed, is not there.

Then you run command cd /media and you access your media folder and you can list files and folders inside with ls command. See atached image.

I don't understand very well your problem, I think you are a little confused about cd and ls commands. 

To see all files and folders inside directories I recommend you use command:```
ls -la
``` being inside the folder or directory  you want to see the files inside. The format is more appropriate, since "l" gives you the output in a list way and "a" shows all the files inside, hidden and not hidden ones.

---

### Post by mcduck on 2014-09-02
Could you explain in a bit more detail the steps you took to move your home to the new drive? Based on the ls output you have a bit strange setup now with multiple directories using same names in different locations (which is probably making things a bit more confusing o you as well)

I can at least spot these:
/home
/home/shondray

...which are fine and as user homes should be. But then you also have these:

/media/home
/media/shondaray
/media/shondaray/Media

...which might be ok if you were just using them as backups or temporary storage to move the files around, but keep in mind that these are not the home directories you can actually *use*.

Also getting a better look at your mounted drives&partitions might be helpful, so could you post the output of "sudo fdisk -l" here?

(One more thing to keep in mind, if you already set the new home drive to mount as /home, did you remove any existing files & home directories first? If not, those files are still going to take space on your root drive, even though they are not visible or accessible as long as the separate home drive is mounted)

---

### Post by Sean_Andreas on 2014-09-02
Here is the output for sudo fdisk -l :

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cce96

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   186263551    93130752    7  HPFS/NTFS/exFAT
/dev/sda2       186265598   312498175    63116289    5  Extended
/dev/sda5       186265600   227225599    20480000   83  Linux
/dev/sda6       310474752   312498175     1011712   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d0635

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      499711      248832   83  Linux
/dev/sdb2          501758   312498175   155998209   83  Linux
shondray@shondray-OptiPlex-320:~$ 


I used [this website]("http://www.maketecheasier.com/move-home-folder-ubuntu/") to move /home to the second partition.

Let me see if I can explain a little better. On dev/sda I have a Windows partition and the boot partition for Ubuntu, some space for the Linux swap and some empty space. On dev/sdb is where I have /home currently. I am new to Linux and so I do not doubt that I botched something up. I know that the second hard disk was mounted on /media. So, I thought that I had to mount my /home onto /media to show up on the second hard drive. Following the website above is how I did that. I will include a copy of my /ect/fstab below and maybe you might find something there that needs to be fixed:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=bec992ac-9fb2-4dde-9fbd-b0d6b6f2cc17 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4775752c-ef73-4f52-bc81-9f2a0b7ce42b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb2 /media/shondray/Media ext4 defaults,x-gvfs-show 0 0
UUID=012cff5b-e175-4964-9259-60ad72501d88    /home    ext4    nodev,nosuid    0    2

Sorry if the text is close together to be difficult to read. If I knew how to space it apart correctly I would do so.

I thought I deleted the directory after I moved the my things to the new /home, but I might not have. In step 4 on the website I just changed /media/home to /home and so that might not have removed the /media/home that is shown in the fstab.

I do appreciate your help and let me know if you need anything else. Thanks!

---

### Post by sotiris2 on 2014-09-02
Ok you couldn't see your files in /media/shondray/Media because you run it from a live cd. Live cd doesn't care about your installations fstab. 

Now **from your installation** do you have your music files in /home/user/music? If so you just need to delete the old /home folder to free up some space on the sda drive.
[COLOR=#000000]
To do so you **will have to use the livecd**. In that you will mount sda5 and remove the home folder. Also remove home_backup if you made it in step3 of that guide. To do so in a **LIVE CD/USB**
```
sudo mkdir /media/temp ; sudo mount /dev/sda5 /media/temp ; cd media/temp ; ls
```
You should get a listing of the root directory. For example bin dev lib .... home ... srv usr 
If so then run ```
sudo rm -r /home
```
[/COLOR]

---

### Post by Sean_Andreas on 2014-09-03
Well needless to say that I deleted /home that I had moved to the second hard drive, which was the one I was using. So, I have to start over again. At least I learned that I shouldn't do things like this after a 12 hour shift. Wasn't focusing enough. I have everything saved elsewhere so I didn't lose anything, except for yours and my time. My apologies.

I think the main thing I learned was to not name directories the same/similar names because it was quite confusing. I named the second hard drive Media because it was storing my media and didn't think twice about my Media drive being stored in /media which became quite confusing when a problem needed to be fixed.

Anyway, thanks again for you help and sorry I wased your time.

---

