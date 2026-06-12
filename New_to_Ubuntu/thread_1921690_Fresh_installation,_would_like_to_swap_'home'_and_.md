---
title: "Fresh installation, would like to swap 'home' and 'usr' folders"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by DreamcasterTM on 2012-02-07
Hello everyone.
As an 'Absolute Beginner' with Linux and Ubuntu, I hope my complete ignorance and linux-blasphemy will be forgiven. :)

I have installed Ubuntu 11.10 beside Windows7 on my Samsung N220 Netbook following a guide I had found online. I managed to dual-boot properly.
4 primary partitions were already in use by Windows7 (recovery, boot, system and documents), so I deleted the NTFS document primary partition and created an extended partition in order to divide it in several logical sub-partitions, at least 4 as the guide suggested. (1 each for *boot*, */*, *usr*, *swap*; the guide also said one could want to create partitions also for important folders such as *var* and *tmp*)
So I created:

[LIST=1]
[*] */boot* (500MB), where I put Grub
[*]*/ *(10GB), where the system itself installed
[*] */usr* (105GB), where the guide stated most of my media files will eventually be stored (I later found out this was wrong)
[*] *swap* (2+ GB)
[/LIST]
Here's a screenshot of Gparted with my HD partitions:

[U][[IMG]http://img9.imageshack.us/img9/2895/screenshotat20120207121.th.png[/IMG]]("http://imageshack.us/photo/my-images/9/screenshotat20120207121.png/")


[/U]Now, either I was too drunk (which is a possibility) or the guide is  wrong: I didn't want to have a huge *usr* folder. I wanted a pretty capable *home* one, where to store all my docs, videos, mp3s, pics and downloads! :sad:
How can I solve this now? I really don't know what the *usr* folder is meant for  (I assume it contains some important files, probably related to  logging-in sessions? But I can also see a *games *folder in it, so I guess also installed apps go here?) so I wouldn't just get rid of it. Still, I would  like to re-place it in the same partition where the system is and also use the 105GB partition as my *home* folder.
Is that possible? And how can I do it?
Thanks to whoever is going to reply this.

_Additional info_
Ubuntu won't let me write on any of the NTFS partitions, as well as in the *usr* one. I guess my account hasn't the required privileges?

---

### Post by nothingspecial on 2012-02-07
If you've just installed Ubuntu, I would start again. I'd up the 10 gig partition to about 15-20 but 10 will be fine unless you plan on installing a lot of applications. Also I'd forget about a /boot partition.

Then run the install again (from the cd or usb).

When the installer asks how you want to install Ubuntu choose "Something Else"

In the partition editor select the big partition (currently 105 gigs). Choose to use it as an Ext4 journaling file system. Give it a mountpoint of /home and choose to format it.

Then select the smaller partition (currently 10 gig) and choose to use as a Ext4 journaling file system and to format it. Give this partitiuon a mountpoint of /

The installer should pickup the swap partition.

Do not touch the windows partition.

So

Small partition - mountpoint /
Big partition   - mountpoint /home

You will loose any data you currently have on your Ubuntu install through doing this. It is always a good idea to back up any data on that computer before partitioning or installing an operating system.

---

### Post by DreamcasterTM on 2012-02-07
Thanks for the quick reply, nothingspecial.
So, there's really no need of a boot partition? I can choose to boot from the / partition?
I had already thought about reinstalling the whole thing once again...and that's what I'll probably do.

But, just out of curiosity: is there any other way one can fix/play with/resize/move/rename/change the system folders/partitions?

Are there any guides or relevant information about important topics such /home, /var, /usr and /temp folders I can read? Could you please link one or more?

Cheers :)

---

### Post by oldfred on 2012-02-07
this is how you can move a /home:

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Most desktops do not need the extra system partitions.
You may need the extra partitions if installing a server and old instructions were often server based. Some old Desktops could not boot from beyond 137GB, so they sometimes needed a separate /boot if  Windows used the first 120 GB for example. If you installed RAID or LVM which are more common on servers you might also need a separate /boot.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Details on system partitions, more for complex or server systems
[http://www.ibm.com/developerworks/aix/library/au-unixfilesys/index.html](http://www.ibm.com/developerworks/aix/library/au-unixfilesys/index.html)

---

### Post by eriktheblu on 2012-02-07
A boot partition can have value, but I would not recommend it in your situation. 

For the record, I endorse the start from scratch method. To sate your curiosity, it would go something like this:
1. Boot with a live CD/USB session. You cannot unmount / or /usr on your active OS and you will need these partitions unmounted
2. Resize /dev/sda7 in Gparted to make room for expanding /dev/sda6 (you're getting shoort on space which can cause issues.
3. Mount /dev/sda7 and copy all files to /dev/sd6/usr (the /usr partition is mounted as this folder). Verify that it coppied correctly, and clean format the partition. 
4. Move everything from /dev/sda6/home to /dev/sda7
5. edit /dev/sda6/etc/fstab and change the mount point for /dev/sda7 from /usr to /home
6. Cross fingers, reboot to hard disk.

You can do pretty much the same thing for /boot, and delete /dev/sda5.

Again, I don't recommend this unless you have a good understanding of the file system.

---

### Post by oklokl on 2012-02-07
I only
 / 
34G


 Build

 Is automatically generated
 Build

 swap
 512
 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

[COLOR=#FF0000]sudo fallocate -l 512m /mnt/512Mb.swap[/COLOR]
[COLOR=#FF0000]sudo chmod 600 /mnt/512Mb.swap[/COLOR]
[COLOR=#FF0000]sudo dd if=/dev/zero of=/mnt/512Mb.swap bs=1024 count=524288
[/COLOR]
[COLOR=#FF0000]sudo mkswap /mnt/512Mb.swap[/COLOR]
[COLOR=#FF0000]
[/COLOR]
[COLOR=#FF0000]gksudo gedit /etc/fstab[/COLOR]
[COLOR=#FF0000]/mnt/512Mb.swap  none  swap  sw  0 0


[COLOR=black]
The remainder
[/COLOR][/COLOR]Space
[COLOR=#FF0000][COLOR=black] Make a partition in the After through gparted

[/COLOR][/COLOR]

---

### Post by DreamcasterTM on 2012-02-08
Thank you everyone for your replies and for the useful information you have linked to.
I will definitely read everything about partitioning, home moving, but for now I will stick with system folders understanding.

From what I now understand, applications are installed in *bin*, *sbin* and *usr* folders, as well as in the *opt* one (third-party apps - and games? - go here).
That means the space used by these folders can considerably increase, accordingly to how many applications one installs.

I won't bother creating a partition for *tmp*  folder, since I reckon that fragmentation is not a big issue on Linux  systems (I would definitely keep a separate partition for temporary  files on a Windows system, so I could delete/defrag that partition more  quickly and also avoid fragmentation of the system partition).

What I will try to do now is to follow eriktheblu suggestions and resize the partitions.
Eventually, I will use just 1 partition for Ubuntu (Herman's explanation on the [thread]("http://ubuntuforums.org/showthread.php?t=1410392")  linked by oldfred is very appealing, although I will still use a swap  partition, I guess) plus 1 partition shared by Ubuntu and Windows where  my data will be kept (I still have to figure out how my /home will link  to this NTFS partition, though...or if it's better to do this the other  way around, which means format it as a ext2/3 or ext4 and use an  application on Windows who allows me to read/write on such partitions,  although I do understand that trying to mess with ext4 partitions from  Windows can be tricky).

@oklokl I don't quite understand what you have written.

Anyway, thank you for your replies guys.

I'll keep you posted!

Giorgio

---

### Post by oldfred on 2012-02-08
/home has to have a linux format.

You can link folders into /home. I have both a shared NTFS and a data ext3 partition with folders linked into my /home.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition older:
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

