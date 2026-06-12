---
title: "Changing the Location of Files"
date: 2015-08-14
forum: New to Ubuntu
---

### Post by Iflana on 2015-08-14
Hello.  I am a new Linux user, and looking for a bit of hands on support working with Ubuntu.  Much of the documentation is geared at advanced users, which I am not.

I use Google Drive for files I share between my cell phone and computer.  I found [overGrive]("http://www.thefanclub.co.za/overgrive") since it's not officially supported by Google on Linux.  The install was very easy as I could do it all with the GUI instead of terminal, which I'm not very skilled with.  I did run into one problem or configuration issue rather.  By default the location was set to **/home/usr/Google Drive** and I would like it to be on another drive from my OS.  There was a "change" button during the install, but clicking it did nothing.  There also doesn't appear to be a settings option after it's installed other than turning auto-sync on or off.  Is it possible to change the location of where those files are stored?

I'm also interested to know how to change the location of other default folders to another drive.  Here's how I'd like it setup.  Sorry I've got to reference the locations like in Windows, because I'm not familiar enough with Linux to know how to write those paths.  Music is a big issue, as I have 5500+ MP3 files on a shared drive.  The space these files take up is more than I've allocated to the Linux drive, and I certainly don't want multiple copies for each user.

C:/ Windows 7 - OS, applications
L:/ Linux Ubuntu 14.04 LTS - OS, applications
J:/ Personal files for me  - documents, templates pictures, downloads
R:/ Personal files for another person - documents, templates pictures, downloads
T:/ Shared files - backups, music, videos, Google Drive

---

### Post by yancek on 2015-08-14
If you have a separate partition or partitions for you music files or other data, then you simply create a mount point and mount the partition in Linux.  If you want this permanent, you put an appropriate entry in the /etc/fstab file so they are available on boot.  If you want access to them from both windows and Linux, you will need a windows filesystem format on the partition (vfat, ntfs) as a default windows is incapable of reading or writing to a Linux filesystem.

You use the term 'drive' and I'm not sure if you are referring to 5 separate hard drives or if you are simply referring to partitions on the same hard drive.  In Linux, 'drive' usually refers to a physical hard drive.

---

### Post by grahammechanical on 2015-08-14
I have my music files on another partition. I use Rhythmbox as the music player. That lets me "import" music from any partition on either of my 2 drives and the import process does not mean the audio files are copied into the Ubuntu partition home folder. The same system works when I use Libreoffice. I can open the Libreoffice files stored on any partition on either of my two drives. And I can save newly created files onto any partition.

I think that you will find that the applications have a method for opening files and saving files to any partition on any drive. The standard type "File Open" and "File Save As" dialogs will let you select where you want the files to be. As for Google Drive. I do not use it. so, I cannot help you there.

---

### Post by Iflana on 2015-08-14
> **grahammechanical said:**
> I have my music files on another partition. I use Rhythmbox as the music player. That lets me "import" music from any partition on either of my 2 drives and the import process does not mean the audio files are copied into the Ubuntu partition home folder. The same system works when I use Libreoffice. I can open the Libreoffice files stored on any partition on either of my two drives. And I can save newly created files onto any partition.

Great, thanks for clarifying.  I went to do this with Rhythmbox and canceled in a hurry thinking it was going to duplicate everything! :o That gives me a music player for the time being.  I'm not sure if I'll continue using this one, as it's not very graphical.  I like to see the album covers, so my children can select music as well (they are all under 5 years old).

Now, I understand I can manually select another location.  What I was hoping for was to change the default location.  This way instead of going to **J:/My Documents** each time, I can just click on "documents".

---

### Post by Iflana on 2015-08-15
> **yancek said:**
> If you have a separate partition or partitions for you music files or other data, then you simply create a mount point and mount the partition in Linux.  If you want this permanent, you put an appropriate entry in the /etc/fstab file so they are available on boot.  If you want access to them from both windows and Linux, you will need a windows filesystem format on the partition (vfat, ntfs) as a default windows is incapable of reading or writing to a Linux filesystem.

You use the term 'drive' and I'm not sure if you are referring to 5 separate hard drives or if you are simply referring to partitions on the same hard drive.  In Linux, 'drive' usually refers to a physical hard drive.

Sorry, that's my bad terminology when describing.  Two physical internal drives, and the second has multiple partitions.  Does that sound right?  If I use **sudo fdisk -l** this is what I get.

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7f1d0f82

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   976771071   488384512    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc7318c78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   314574847   157286400    7  HPFS/NTFS/exFAT
/dev/sdb2       314576894   524290047   104856577    5  Extended
/dev/sdb3       524290048  1048578047   262144000    7  HPFS/NTFS/exFAT
/dev/sdb4      1048578048  1953519615   452470784    7  HPFS/NTFS/exFAT
/dev/sdb5       314576896   346574847    15998976   82  Linux swap / Solaris
/dev/sdb6       346576896   524290047    88856576   83  Linux
```

I would want the change permanent.  So what are the "appropriate entries" to add to the fstab file?  I have read the documentation on [MoveMountpointHowTo]("https://help.ubuntu.com/community/MoveMountpointHowto"), but I don't think any of those are exactly what I wanted.  The basic examples look like they are relocating entire partitions, and the advance examples look like they are relocating different groups of files - none of which are the specific ones I'm talking about moving.  This is what my fstab file looks like now.

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb6 during installation
UUID=9e5e6f1b-3e64-4be6-877a-b055502de194 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=3b908f9c-b760-4ff4-a27d-67028ede86cf none            swap    sw              0       0
```

I also want to make sure I'm not deleting any files in the process of doing this.

---

### Post by yancek on 2015-08-15
Are you using Ubuntu 14.04?
Have you looked in the /media/user directory to see if the partitions are available there?
The standard place to mount partitions in Linux is in the /mnt directory.  Are you familiar with the Linux filesystem hierarchy?  Can you find the /mnt directory in other words?  If you don't have any mount points available for the different partitions, you simple create them.

I don't know what you have on the different drives but I assume sda1 is the system files for windows 7 but can't be sure.  If you have your data on the second drive, sdb, you would simply create a mount point.  For sdb1, just for the sake of clarity create with:  sudo mkdir /mnt/sdb1  You should be prompted for your primary user password so enter it and you should then see the new direcotry.  Do that for each partition you want to access.  The next step is to mount or to have the partitions permanently mounted, put an entry in the /etc/fstab file.  All you have there now are the Ubuntu filesystem partition and the swap partition.

Creating a mount point and mounting a partition simply means to make it accessible and does not move anything nor does it delete anything.  There are countless sample entries for fstab available online but if you could give some details on what access limitations you want for users.  Standard Linux permissions aren't understood by windows and entries will be different.  The example below gives just read permissions to users on an ntfs partition.  I don't really use windows so you will probably need to get more knowledgeable advice from someone else.

> /dev/sda2 /mnt/win_7 ntfs-3g auto,user,rw,umask=002 0 0

The example below gives the root user as well as user bob full read/write/execute and other user no permissions, not even read.  So you can see there are options and if you want specifics from someone here you need to explain what limitations you want.  With small children using the computer, you will need limits as it is very easy to accidentally delete files.

> /dev/sdb12 /mnt/win-test ntfs-3g defaults,auto,nouser,uid=bob,rw,umask=077 0 0

---

### Post by jason_gibson2 on 2015-08-15
Just symlink things into the proper /home locations. In the case of /home/user/GoogleDrive just move that folder somewhere else (another partition?) and link it into /home/$USER.

---

### Post by Iflana on 2015-08-16
> **yancek said:**
> Are you using Ubuntu 14.04?
Have you looked in the /media/user directory to see if the partitions are available there?
The standard place to mount partitions in Linux is in the /mnt directory.  Are you familiar with the Linux filesystem hierarchy?  Can you find the /mnt directory in other words?  If you don't have any mount points available for the different partitions, you simple create them.

I don't know what you have on the different drives but I assume sda1 is the system files for windows 7 but can't be sure.  If you have your data on the second drive, sdb, you would simply create a mount point.  For sdb1, just for the sake of clarity create with:  sudo mkdir /mnt/sdb1  You should be prompted for your primary user password so enter it and you should then see the new direcotry.  Do that for each partition you want to access.  The next step is to mount or to have the partitions permanently mounted, put an entry in the /etc/fstab file.  All you have there now are the Ubuntu filesystem partition and the swap partition.

Creating a mount point and mounting a partition simply means to make it accessible and does not move anything nor does it delete anything.  There are countless sample entries for fstab available online but if you could give some details on what access limitations you want for users.  Standard Linux permissions aren't understood by windows and entries will be different.  The example below gives just read permissions to users on an ntfs partition.  I don't really use windows so you will probably need to get more knowledgeable advice from someone else.



The example below gives the root user as well as user bob full read/write/execute and other user no permissions, not even read.  So you can see there are options and if you want specifics from someone here you need to explain what limitations you want.  With small children using the computer, you will need limits as it is very easy to accidentally delete files.

Yes, I am using 14.04 LTS version downloaded in July.  I don't think there are any other partitions, or they would show up with the command I did before wouldn't they?  If I click on files, I get the standard user folders (downloads, documents, music) all in one place that seems to be */home/user*.  So if my Linux OS is on sdb5 then the full path would be *sdb5/home/usr/directory*?  I found the mnt and media directories.  The mnt directory appears to be empty.  The media directory has a folder for my user, which is empty.

Your explanation leads me to believe that mounting is necessary for accessing other partitions when using Linux, but I can already read/write files on all other partitions that were setup with the MMC in Windows with an NTFS file system.  This leaves me confused as to why I need to mount anything.  I don't want anyone to be prompted for passwords when accessing any files, and I do want to be able to work with my files in both operating systems.  I'm the primary user, and it's a rare occurrence (save his nightly DDO) that my boyfriend uses the computer.  All my children are under 2 years old, so not an issue as they don't use electronics at all.  Here's how I think the space is allocated using the sd* instead of drive letters.

sda1 Windows 7 - OS, applications

sdb2 Linux Ubuntu 14.04 LTS - OS, applications
sdb1 Personal files for me  - documents, templates pictures, downloads
sdb3 Personal files for another person - documents, templates pictures, downloads
sdb4 Shared files - backups, music, videos, Google Drive

Sorry, these are probably dumb questions, but you're right I am not familiar with any aspect of Linux.  This is my first time installing & using the OS. :oops:  I will have lots of n00b questions about the easy stuff I expect.  I've run out of time here, but I'll check back again tomorrow if I can!  I need to read on what this symlink is.

---

### Post by Geoffrey_Arndt on 2015-08-16
A good thing to do at this point is to find out exactly how your drive is setup.   You can run the program "gparted" and it will show your partition table for each physical drive (see upper right corner of gparted gui to toggle between drive views).   Do a screen-shot of that and post it back here.

(ps - - for what it's worth, I find "Dropbox" to be extremely "Linux" friendly especially if running a gnome based DE like Unity.   The interface was written to use the native "Nautilus" file manager in Ubuntu.    Makes sharing extremely easy between users and various machines.)

---

### Post by Iflana on 2015-08-18
OK I haven't had a chance to read on symlink yet, sorry, but I ran into a wall with gparted.  I tried to access with terminal typing **gparted** and it told me it wasn't installed.  It gave me **sudo apt-get install gparted** to install, so I did that and no errors reported.  Then when I go to access it, I get this error.

[ATTACH=CONFIG]263934[/ATTACH]

---

### Post by Iflana on 2015-08-18
Does this help you determine anything else about my setup?

```
Model: ATA ST3500320AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ntfs         boot


Model: ATA ST31000528AS (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  161GB   161GB   primary   ntfs            boot
 2      161GB   268GB   107GB   extended
 5      161GB   177GB   16.4GB  logical   linux-swap(v1)
 6      177GB   268GB   91.0GB  logical   ext4
 3      268GB   537GB   268GB   primary   ntfs
 4      537GB   1000GB  463GB   primary   ntfs
```

---

### Post by Iflana on 2015-08-18
> **jason_gibson2 said:**
> Just symlink things into the proper /home locations. In the case of /home/user/GoogleDrive just move that folder somewhere else (another partition?) and link it into /home/$USER.

I've been Googling this term, since I don't know what it is.  I find lots of lines of code that I can't make sense out of, or determine what people are trying to accomplish.  The best I can determine... from [here]("http://askubuntu.com/questions/108771/what-is-the-difference-between-a-hard-link-and-a-symbolic-link")... a symlink is basically the equivilent of a Windows shortcut/alias.  Is that correct?  If so, that isn't what I'm looking for.  I want to be able to click the documents button for example, and have it take me to the partition & directory where my documents are located.  I did a screenshot, so you can see.  Right now clicking on documents leads to the default location ubuntu picked within the partition the OS was installed on.  If not, would you be able to point me in the direction so I can learn more?

[ATTACH=CONFIG]263935[/ATTACH]

---

### Post by Iflana on 2015-08-20
UPDATE: I exit overGrive, and when I tried to open it again I was required to setup everything again.  This time it allowed me to change the folder location to **/media/jen/Johann/My Google** like I originally wanted to! Yay!  So that's one issue down, and I think that sheds some light on the paths I was trying to figure out as well.

---

### Post by Iflana on 2015-08-21
> **Geoffrey_Arndt said:**
> A good thing to do at this point is to find out exactly how your drive is setup.   You can run the program "gparted" and it will show your partition table for each physical drive (see upper right corner of gparted gui to toggle between drive views).   Do a screen-shot of that and post it back here.

(ps - - for what it's worth, I find "Dropbox" to be extremely "Linux" friendly especially if running a gnome based DE like Unity.   The interface was written to use the native "Nautilus" file manager in Ubuntu.    Makes sharing extremely easy between users and various machines.)

Here's the screen shot.  I also posted some other information earlier.

[ATTACH=CONFIG]263978[/ATTACH]

---

### Post by Iflana on 2015-08-22
Solutions...

... no solution was needed to change the default overGrive directory.  The application currently prompts you for these settings each time it is opened, and although it didn't allow me to change it the first time the problem didn't continue after that.  Not sure if this is a bug, or something related to it being a trial version.

... in order to change the default directory for other user files (ie: documents, pictures, downloads, music) I ended up finding [Ubuntu-Tweak]("http://www.ubuntu-tweak.com/").  It works on a GUI basis, and has a bunch of other useful settings & tools.  It wasn't necessary to mount or symlink anything.

---

### Post by Geoffrey_Arndt on 2015-08-22
To aid your understanding of the gparted graphical representation of your two hard drives, you should be aware that:

NTFS/Fat16/Fat32 are all Windows file systems, and therefore also Windows partitions.   So you have Windows partitions, directories and files on both physical hard drives.
.......................................................................................................................................


Sda1 (partition 1 of Sda drive) =  all Windows (probably main OS and user Directories and Files)

.........................................................................................................................................

sdb1  (partition 1 of Sdb drive) = Windows 

sdb3  (partition 2 of Sdb drive) = Windows

sdb4  (partition 3 of Sdb drive) = Windows

............................................................................

Sdb2 = _Extended_ Partition (is like a "Container" & Label for many more "logical" partitions))

sdb6 (extended partition  4 of Sdb drive) = Ubuntu OS and all User "Home" directories (each user has own home, with identical default folders such as downloads, music, etc.) - - but can add many custom directories/folders

sdb5 (extended partition 5 of Sdb drive) = Linux Swap 

...............................................................................

---

### Post by Geoffrey_Arndt on 2015-08-22
Iflana,

Just an fyi . . . somehow you developed an impression that directories and partitions always "require" mounting.    Mounting is seldom required insofar as a user action.   Ubuntu will auto-mount most partitions and external drives such as flash-sticks, SD cards, etc.   

Another way to easily share files (and create custom folders) is via an SD card plugged into a wireless printer (most modern printers come with card slots for ease in copying photo files, etc.).   Since the default file type for SD cards is FAT32 - an MS file system, all users can access the SD card directories/folders and files via clicking on "Browse Network" in the file manager.  This is done via the default "Samba" client installed in Ubuntu.    This is sort of like a local network, versus using a Cloud Service such as Dropbox, Google Drive, or Spider Oak etc.

---

### Post by Iflana on 2015-08-22
> **Geoffrey_Arndt said:**
> Iflana,

Just an fyi . . . somehow you developed an impression that directories and partitions always "require" mounting.    Mounting is seldom required insofar as a user action.   Ubuntu will auto-mount most partitions and external drives such as flash-sticks, SD cards, etc.   

Another way to easily share files (and create custom folders) is via an SD card plugged into a wireless printer (most modern printers come with card slots for ease in copying photo files, etc.).   Since the default file type for SD cards is FAT32 - an MS file system, all users can access the SD card directories/folders and files via clicking on "Browse Network" in the file manager.  This is done via the default "Samba" client installed in Ubuntu.    This is sort of like a local network, versus using a Cloud Service such as Dropbox, Google Drive, or Spider Oak etc.

Yes, that's the way it sounded from reading.  I'm glad Ubuntu did this on it's own though!

I know I can plug in external devices, but I really prefer not to.  They bog down the system, in Windows at least, and are easily lost one way or another.  Plus, having a memory stick doesn't allow me to easily share files with my mother for example, who lives a good 4 hours drive from me.  :D  Google Drive & the partitions on my internal drives allow me to accomplish this nicely.

---

### Post by Geoffrey_Arndt on 2015-08-22
Yes . . . shared folders on Cloud Services are perfect for what you describe.     My personal favorite is Dropbox as it's really well integrated into "Nautilus" and "Gnome" (the Ubuntu desktop - Unity, is still about 75% gnomish, although it will be less so in future).     Just remember, Google scans everything . . . . so, if anything at all sensitive (anything that requires a password), be sure to encrypt on you local PC before putting the file into the cloud folder for upload.   BTW, an easy program to use for strong and simple encryption is 7zip (see youtube for info/tutorials).

Best of luck with Ubuntu!

---

### Post by Iflana on 2015-08-23
> **Geoffrey_Arndt said:**
> Yes . . . shared folders on Cloud Services are perfect for what you describe.     My personal favorite is Dropbox as it's really well integrated into "Nautilus" and "Gnome" (the Ubuntu desktop - Unity, is still about 75% gnomish, although it will be less so in future).     Just remember, Google scans everything . . . . so, if anything at all sensitive (anything that requires a password), be sure to encrypt on you local PC before putting the file into the cloud folder for upload.   BTW, an easy program to use for strong and simple encryption is 7zip (see youtube for info/tutorials).

Best of luck with Ubuntu!

Thanks a bunch for the suggestions and info. :D  I really appreciate it, especially since I imagine you had to "dumb it down" for me to understand!  I may not be able to operate strictly without a GUI, but I'm hoping to attain a decent balance between that and terminal type stuff.

---

