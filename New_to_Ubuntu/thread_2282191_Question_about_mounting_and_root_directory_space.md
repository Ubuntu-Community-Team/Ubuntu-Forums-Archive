---
title: "Question about mounting and root directory space"
date: 2015-06-12
forum: New to Ubuntu
---

### Post by RagusLive on 2015-06-12
**TL;DR:**
Is there a way to mount internal storage drives so that they are not a subfolder of the root drive? Is mounting even completely necessary to have a drive be accessible? Particularly from other computers on a network (both local and remote).

------------------------------

I am relatively new to Ubuntu/Linux, having been a Windows guy for a long time, so 'mounting' and the way Linux handles it is kinda new to me. This may be a simple concept, but I could not come up with a way to Google it that returned any meaningful results.

I have set up a private server on Ubuntu 14.04 using Apache and OwnCloud. I am running the OS from a 20gig flash drive and using a trio of 500gig hard drives for my actual data storage. They are currently set up to mount on startup to /mnt/harddrivename.
As I began to upload files from another computer on my network I noticed an error message on my server machine (I am using Ubuntu desktop, not the server version) saying I was almost out of space. It seemed to count the files uploading to my 500gig storage drive against the available space of my 20gig root drive. I watched as my files continued to upload, passing the 20gig "limit" without issue, so I figured I could ignore it.
Now though I am unable to upload files from the OwnCloud mobile app, whereas app uploading was working just fine before I passed the 20gig mark.

Is there another way that these drives can be mounted to be completly separate from the root drive? If not, would there be another workaround to convince my root drive that he does not have to be in any way 'responsible for' the amount of space taken up on my storage drives?

---

### Post by yancek on 2015-06-12
> Is there a way to mount internal storage drives so that they are not a subfolder of the root drive? 

Do you mean / (/ being the symbol for the entire filesystem) or root which is just the /home folder for root user?  If the former, probably not.

> s mounting even completely necessary to have a drive be accessible? 

That's basically the purpose of mounting, making it accessible.  If this is a web server with Apache, it's default location would be the /var directory so the standard would be to create a separate partition on a drive for the /var directory with an entry in the /etc/fstab file indicating this is the case.  I'm not sure how you would do this with multiple drives, LVM?  Someone else will likely be along with more details.

---

### Post by cariboo on 2015-06-12
it would help if you let us know how and where the three hard drives are mounted. Open a terminal and enter the following command:

```
df -h
```

paste the results in your next post,

---

### Post by RagusLive on 2015-06-12
> **yancek said:**
> Do you mean / (/ being the symbol for the entire filesystem)
Yes, that.
Let me be clear that, as a newbie, this was not my intention going in. I was expecting to have my additional hard drives exist 'alongside' my / drive, in much the way Windows has the C, D, E, etc drives act independently of each other. Just for the sake of being completely explicit I will ask; Linux simply does not handle drives in this manner, is that correct?


> **yancek said:**
> That's basically the purpose of mounting, making it accessible.
I figured that would be the case, but I thought I would ask since that is exactly the kind of base concept that I could overlook.


OwnCloud has an extension that allows you to add additional drives which is what I used to include my 3 500gig drives in the operation. I /could/ move the OS over to one of my 500gig drives, but that would be a stay of execution rather than an actual fix, since I would run into the same issue as soon as my total data exceeds 500gigs (which is not far off, I deal with a lot of high quality video and audio).

Thanks for your perspective and knowledge, at my early stage every bit of understanding is a huge help.

---

### Post by bab1 on 2015-06-12
> **RagusLive said:**
> [In response to whether you wanted to mount the "drives" on the / file system]
Let me be clear that, as a newbie, this was not my intention going in. I was expecting to have my additional hard drives exist 'alongside' my / drive, in much the way Windows has the C, D, E, etc drives act independently of each other. Just for the sake of being completely explicit I will ask; Linux simply does not handle drives in this manner, is that correct?

Actually both Windows and Linux mount the drives (partitions in Linux speak) to a single file system which starts at a single point.  This single point is called / in Linux.  Windows just hides all this from the user.  Windows partitions (C, D, E, etc. drives) are mounted to a singe file system tree.  They DO NOT work independently.  In Windows when you map a drive you are mounting that partition (drive) to the file sytem. 
> 
OwnCloud has an extension that allows you to add additional drives which is what I used to include my 3 500gig drives in the operation. I /could/ move the OS over to one of my 500gig drives, but that would be a stay of execution rather than an actual fix, since I would run into the same issue as soon as my total data exceeds 500gigs (which is not far off, I deal with a lot of high quality video and audio).

Thanks for your perspective and knowledge, at my early stage every bit of understanding is a huge help.

If you want to use the partitions via Linux you must mount them to the file system tree (map the drive).  You do not want to mount these partitions at / however.  You can mount them anywhere below / (i.e. /data or /mnt or /MyWindowsDrive etc.)  Once mounted you deal with the file system branch separately.  Linux users refer to /home as where the home directories are or /etc as where the config files are.

In the end it's more a matter of naming convention and Windows hiding what is really going on.

---

### Post by RagusLive on 2015-06-12
> **cariboo said:**
> paste the results in your next post,

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd1        13G  6.6G  5.2G  57% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            872M  4.0K  872M   1% /dev
tmpfs           177M  1.2M  176M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            881M   76K  881M   1% /run/shm
none            100M   32K  100M   1% /run/user
/dev/sda1       459G  9.1G  426G   3% /mnt/HD 1
/dev/sdb1       459G   71M  435G   1% /mnt/HD 2
/dev/sdc1       459G   11G  425G   3% /mnt/HD 3

```



> You can mount them anywhere below / (i.e. /data or /mnt or /MyWindowsDrive etc.)
I was attempting to do that but may not have gotten it right.  Does the above attached info help?

---

### Post by bab1 on 2015-06-12
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       459G  9.1G  426G   3% /mnt/HD 1
/dev/sdb1       459G   71M  435G   1% /mnt/HD 2
/dev/sdc1       459G   11G  425G   3% /mnt/HD 3
```

It shows that they are mounted at /mnt.  Try navigating to /mnt and you will see them.  If you want to see them using a terminal command you can do use this```
ls -l /mnt
```

[COLOR="#0000FF"]Edit1:  The questions might be: how did you mount them, and what upload command were you using?[/COLOR]

[COLOR="#008000"]Edit2: Note that the partitions have 9GB or 71MB or 11GB only on them. [/COLOR]

---

### Post by blm-ubunet on 2015-06-12
FWIW
Just a word of advice about setting up extra disks that can expect lots of data...
Create a folder on each of the HDD & only allow writing into the folders. Never write into the top level of each HDD.
 Why: If any HDD fails to mount then the symlink in "/mnt/HD\ 1" is write-able & fills up your system disk.
If you use a sub-folder on each HDD & one fails to mount then you get a error that the folder does not exist.

---

### Post by RagusLive on 2015-06-12
> **bab1 said:**
> [CODE][COLOR=#008000]Edit2: Note that the partitions have 9GB or 71MB or 11GB only on them. [/COLOR]

Yes I know, which is exactly why I'm surprised that I'm getting an error message saying that my disk is full.
The root drive (a 20gig flash drive) has 5.2 gigs of space, yet I am getting "your disk is almost full" notifications and my network uploads are being stalled/rejected.  Therein lies my problem...

The df -h command I put in seems to display a system with plenty of space, right?  So where is the "disk almost full" error coming from?

---

### Post by blm-ubunet on 2015-06-12
May be you have a folder /mnt/HD/ that is filling up your system disk.
Possibly the unhandled space in mountpoint name is causing this.

You should read my previous post & check this as well
```
ls -al /mnt
```

---

### Post by bab1 on 2015-06-12
> **RagusLive said:**
> Yes I know, which is exactly why I'm surprised that I'm getting an error message saying that my disk is full.
The root drive (a 20gig flash drive) has 5.2 gigs of space, yet I am getting "your disk is almost full" notifications and my network uploads are being stalled/rejected.  Therein lies my problem...

The df -h command I put in seems to display a system with plenty of space, right?  So where is the "disk almost full" error coming from?
Now we need to diagnose why that is.  

As others have suggested, you might have downloaded the data to /mnt before the 3 partitions were mounted.  That's sort of why I asked, how did you mount them (the partitions), and what upload command were you using?

The only way to know if the partitions were NOT mounted when you were downloading is to un-mount the partitions and see what you get from *df -h* then.

---

### Post by RagusLive on 2015-06-13
> **blm-ubunet said:**
> FWIW
Create a folder on each of the HDD & only allow writing into the folders. Never write into the top level of each HDD.

So just as simple as creating a sub-folder on the disk and writing to that, or are you talking about orienting folder permissions in some specific way as well?

Also:
```
ls -al /mnt
total 20
drwxr-xr-x  5 root  root  4096 Jun 12 03:24 .
drwxr-xr-x 22 root  root  4096 Jun 12 01:12 ..
drwxrwxrwx  4 root  root  4096 Jun 12 12:18 HD 1
drwxrwxrwx  3 ragus ragus 4096 Jun 12 12:22 HD 2
drwxrwxrwx  4 ragus ragus 4096 Jun 12 03:47 HD 3

```
In the above code "HD1 HD2 HD3" are all highlighted in green, if that matters.
Also I did restart the system just a bit ago if that effects anything.

---

### Post by RagusLive on 2015-06-13
Update:
As of the system restart I mentioned in the post above, everything seems to be playing nicely (I promise that was not the first time I have restarted my system while dealing with this issue).
However, before I restarted I did unmount the three storage drives (but did not change the "mount on startup" setting).

Here is the output for df -h as of this moment (I have uploaded a few additional files via network while testing it again).
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd1        13G  6.9G  4.9G  59% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            872M  4.0K  872M   1% /dev
tmpfs           177M  1.2M  176M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            881M   80K  881M   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/sda1       459G  9.1G  426G   3% /mnt/HD 1
/dev/sdb1       459G   71M  435G   1% /mnt/HD 2
/dev/sdc1       459G   12G  424G   3% /mnt/HD 3
```



[B]EDIT:
MAY HAVE SPOKEN TOO SOON ON THINGS PLAYING NICELY
GAHH IT'S LATE.  WILL RE-READ ALL SUGGESTIONS AND TRY AGAIN WHEN MORE CLEAR-HEADED
[/B]

---

### Post by abelattila83 on 2015-06-13
Windows mounts the drives too. 

If you don't mount it, you will just have access to the raw device, but that is not very human-friendly

Under Linux, everything needs to be mounted under "/"

See the: 

[https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

for further interesting things about which directory under / does what. 

Best regards, 
IT and IT Security news: [https://somenewsforyou.github.io/](https://somenewsforyou.github.io/)

---

### Post by blm-ubunet on 2015-06-13
The folder in each HDD just needs to be created by your user after they are mounted.
Then change your script/webserver etc to write to this new path..

One of your HDD mount points has different user:group settings..

The colours used in bash/ls by default are :
blue txt - directories
turquoise blue-green txt - symbolic links
green txt - executable
green highlight blk txt - sticky other-writeable with execute bit set.

So that reported highlight colour is little odd but should be okay. Believe this means any user or group or any other can access.
My auto-mounted SD card mountpoint shows as blue txt (directories) & allows only users.
"ls -al /home" is a good way to look at how some of the different permission attributes work.
A directory must have execute bit set to get a content listing.

As mentioned earlier (not me) the method of mounting (/etc/fstab with UUID or auto-mounting) can change the HDDs permissions & which HDD is which.

Remember in windows when c: & d: drives get moved around when you add another HDD..
 
The "proper messy way" to add permanent attached HDDs is to make an entry in "/etc/fstab" for which you need to know the partition UUID & more.. Sadly, I don't think there is a nice GUI tool for this messy job.
I've always just done it in cmd-line:
"sudo blkid" & highlight required UUID <ctrl>+<shift>+<c> then
"sudo gedit /etc/fstab" etc
In the /etc/fstab file you can set permissions/owner etc.

When you add your HDD to /etc/fstab, the auto-mounting process will then not interfere with that HDD.
The auto-mounting udev stuff probably just makes whole disk owned/writeable by users which is normal/expected for a removeable drive.

The way the HDDs were mounted may make it impossible for you <user> to "mkdir" without sudo access.
If the folders are created by sudo then they are owned by root:root & you would need to set user:group.

So I would create the folder in each while using auto-mounting & then try to change just one HDD to use /etc/fstab as trial.

Not a tidy answer but HTH.

---

