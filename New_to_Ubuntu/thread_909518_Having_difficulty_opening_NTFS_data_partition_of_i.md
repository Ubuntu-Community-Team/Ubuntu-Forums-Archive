---
title: "Having difficulty opening NTFS data partition of internal hard disk"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by The Linux Newbie on 2008-09-03
Good evening folks,

A week or so ago I had a wierd problem with my Windows OS, whereby I restarted to find that the laptop wouldn't load Windows anymore, displaying only a blue screen that said some recent Hardware changes had disabled that possibility.

After trying to reformat the OS, with my XP SP2 disk, and being unsuccessful ('asms' was missing (or so the error bar told me) so I was unable to install Windows all over again), I gave up and a friend told me that the last thing I could try (I had tried more than 1 Windows OS disk) was installing Ubuntu, and that if it didn't manage to do that, then that would mean the HD was somehow corrupted (bad sectors or the like).

Anyway, that was just to give context to my situation. 

I'm now running Ubuntu 8.04, and loving it so far, watching a VTC tutorial on it, and trying to learn as much as I can about this really cool environment.

However, even after I went to the relevant section in the Ubuntu site (where manipulating NTFS data is discussed, and how to read or write to NTFS disks), I have thus far been unable to read from my NTFS data partition, which still comes from the old Windows OS, and hasn't been Linux-prepared (I had no opportunity to convert the file types and the rest, seeing as my lappie went down under before I had the chance to).

Anyway, here's the error screen I get on Ubuntu when I try to open that partition:

[IMG]http://i301.photobucket.com/albums/nn52/TorrentialOutpour/problemaccessingdatapartition.png[/IMG]

What am I doing wrong?

Cheers.

---

### Post by billgoldberg on 2008-09-03
> **The Linux Newbie said:**
> Good evening folks,

A week or so ago I had a wierd problem with my Windows OS, whereby I restarted to find that the laptop wouldn't load Windows anymore, displaying only a blue screen that said some recent Hardware changes had disabled that possibility.

After trying to reformat the OS, with my XP SP2 disk, and being unsuccessful ('asms' was missing (or so the error bar told me) so I was unable to install Windows all over again), I gave up and a friend told me that the last thing I could try (I had tried more than 1 Windows OS disk) was installing Ubuntu, and that if it didn't manage to do that, then that would mean the HD was somehow corrupted (bad sectors or the like).

Anyway, that was just to give context to my situation. 

I'm now running Ubuntu 8.04, and loving it so far, watching a VTC tutorial on it, and trying to learn as much as I can about this really cool environment.

However, even after I went to the relevant section in the Ubuntu site (where manipulating NTFS data is discussed, and how to read or write to NTFS disks), I have thus far been unable to read from my NTFS data partition, which still comes from the old Windows OS, and hasn't been Linux-prepared (I had no opportunity to convert the file types and the rest, seeing as my lappie went down under before I had the chance to).

Anyway, here's the error screen I get on Ubuntu when I try to open that partition:

[IMG]http://i301.photobucket.com/albums/nn52/TorrentialOutpour/problemaccessingdatapartition.png[/IMG]

What am I doing wrong?

Cheers.

Ubuntu 8.04 can read and write to nfts out of the box. Just to be clear.

That error happens when you don't turn off Windows properly.

Unless you shut it down properly, you will keep having that error.

I don't exactly know why (Windows is to blame, that's for sure).

You could try to force mount it from the command line.

[http://www.ehow.com/how_2208480_mount-ntfs-drive-ubuntu.html](http://www.ehow.com/how_2208480_mount-ntfs-drive-ubuntu.html)

---

### Post by The Linux Newbie on 2008-09-03
Well accessing Windows to shut the drive down properly is not an option. The last time I shut Windows down it had to be through the button, as the OS had frozen.

Now it's no longer installed.

By the way, I'm trying to follow your link (it's very helpful, thx) but I need to know where I can see my device's name? ("sudo ntfsfix /dev/[DEVICENAME]")

---

### Post by dwanders on 2008-09-03
When Windows is shut down badly (like with the power button) rather than gracefully with Shutdown - it has a bit flipped letting it know so it can start up the menu system for safe mode etc... Using that force option should work fine - I have used it before.

---

### Post by The Linux Newbie on 2008-09-03
> **The Linux Newbie said:**
> By the way, I'm trying to follow your link (it's very helpful, thx) but I need to know where I can see my device's name? ("sudo ntfsfix /dev/[DEVICENAME]")

As in, the letter/number combo Ubuntu assigned it?

---

### Post by dwanders on 2008-09-03
try df -h from command line should give you something like:

danderso@PC095:/dev/disk/by-path$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             145G   14G  125G  10% /
varrun                505M  108K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M   44K  505M   1% /dev
devshm                505M   36K  505M   1% /dev/shm
lrm                   505M   39M  467M   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon      145G   14G  125G  10% /home/danderso/.gvfs

my disk is /dev/sda
that sda1 is the first partition, if I had an NT partion on there to, it might be /dev/sda2

etc...

---

### Post by The Linux Newbie on 2008-09-03
> francisco@francisco-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              11G  2.7G  7.5G  27% /
varrun                506M  108K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   52K  506M   1% /dev
devshm                506M  228K  506M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       11G  2.7G  7.5G  27% /home/francisco/.gvfs
/dev/scd0             283M  283M     0 100% /media/cdrom0
francisco@francisco-laptop:~$ sudo ntfsfix /dev/sda5
[sudo] password for francisco: 
sudo: ntfsfix: command not found


Does this 'command not found' message mean it was unsuccessful in fixing or altering the ntfs log?

I'm making all this fuss because it didn't tell me anything about my other partition (sda5) on Terminal when I typed in "df -h"

:/

---

### Post by dwanders on 2008-09-03
That tells us that your Linux Partition is probably /dev/sda6 (the 6th partition on the drive /sda. 

Your Windows partition is probably some where lower like /dev/sda1 or /dev/sda2 - sda5. It did not show up in the df command because it is not mounted yet. Try your mount command on /dev/sda1 or /dev/sda2 etc ... until you find your windows partition.

---

### Post by dwanders on 2008-09-03
The command not found means your OS does not know what ntfsfix is (or it is not installed on your computer).

---

### Post by dwanders on 2008-09-03
It looks like ntfsfix is part of a program package called ntfsprogs (probably for NTFS programs. So try sudo apt-get install ntfsprogs, then try your command ntfsfix after ntfsprogs installs.

---

### Post by The Linux Newbie on 2008-09-04
Thanks for those replies dwanders.

I'm a bit stuck on the last step of the guide on the hyperlink that was given me.

And it's this part:

> When this finishes, type the following into the terminal:

sudo mount -t ntfs-3g /dev/[DEVICENAME] [LOCATIONOFMOUNT] -o force
Where [DEVICENAME] is the name of the drive (i.e. sda1) and [LOCATIONOFMOUNT] is an empty folder to mount the drive to. 

What should I put in LOCATIONOFMOUNT? 

Just create a folder and mount the drive there? I mean could it be a folder located in /dev/sda6?

~~

---

### Post by dwanders on 2008-09-04
You should create a folder under the /mnt folder (that is typically where I put them) so do something like:

sudo mkdir /mnt/ntfs   or sudo mkdir /mnt/windows   etc...

Once thats done, then do your:

sudo mount -t ntfs-3g /dev/[DEVICENAME] [LOCATIONOFMOUNT] -o force

Where [DEVICENAME] is the name of the drive (i.e. sda1) 
Where [LOCATIONOFMOUNT] is the empty folder you made with mkdir something like:

sudo mount -t ntfs-3g /dev/sda5 /mnt/windows -o force

---

### Post by The Linux Newbie on 2008-09-04
I just did everything you said and nothing happened.

> francisco@francisco-laptop:~$ sudo mount -t ntfs-3g /dev/sda5 /mnt/windows -o force
francisco@francisco-laptop:~$

And now when I go to places/computer, I can't even see the 108GB partition anywhere.

*gulp*

---

### Post by dwanders on 2008-09-04
What happens if from command line you go do:

cd /mnt/windows
ls

do you see your files?

---

### Post by dwanders on 2008-09-04
From the GUI - you may need to do:

Places -> Filesystem -> mnt -> windows

---

### Post by The Linux Newbie on 2008-09-04
I do see the files when I put in the code you gave me :) (cd /mnt/windows ls)

What is "Filesystem" though?

I just have Places>Home Folder/Desktop/Documents/Music/Pictures/Videos

---

### Post by Bucky Ball on 2008-09-04
You could try having a look around with gparted (you may have it already installed - try typing **sudo gparted** in the terminal). If not[B]:

[/B]**sudo apt-get install gparted** 

will install it. Then:

**sudo gparted**

will give you the GUI. That will give you a good look at what you have in there and what the partitions are named, filesystem (file type) and where. Windows always wants the first available partition; mucho problemo going anywhere else, and seeing as it was installed first (as it should be) there will be, as was mentioned, a spare partition where it was *before* the Ubuntu partition.

---

### Post by eotakos on 2008-09-04
if you are still struggling with the device name - you can try

sudo fdisk -l

this will list the partition table for you

then, you can

sudo vol_id /dev/[device]

this will show all info for the [device] including the label

---

### Post by The Linux Newbie on 2008-09-04
Yep. Neat little app there :)

I can see both drives.

Now how do I access the files inside sda5? (my data partition from Windoze times)

BTW - I removed Windows completely. Just in case I hadn't made myself clear. (Thus, Bucky, I don't see any third partition - just the Linux (Ubuntu) one, and the other data partition).

---

### Post by The Linux Newbie on 2008-09-04
Worry not, worry not :)

I just found filesystem (went to mnd/windows) and now already listening to music from windaze :D

Cheers for all the really professional help.

---

### Post by Bucky Ball on 2008-09-04
Excellent news! You can use 'Thread Tools' to mark your thread as 'solved' so others can surf here for a fix. Good luck and happy travels. :)

ps: **gparted** should now show up as **System->Administration->Partition Manager** for easy access. If not, go to **System->Preferences->Main Menu->System->Administration** and make sure Partition manager has a tick next to it there.

---

### Post by dwanders on 2008-09-04
My Bad should have been Places -> Computer -> Filesystem -> mnt -> windows

---

