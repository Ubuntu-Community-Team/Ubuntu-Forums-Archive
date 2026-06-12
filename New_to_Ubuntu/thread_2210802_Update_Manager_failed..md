---
title: "Update Manager failed."
date: 2014-03-12
forum: New to Ubuntu
---

### Post by grey1beard on 2014-03-12
A recent attempt to run update manager failed on this laptop (my wife's) running 12.04, and has left my not knowing what to try next.
I have taken various screenshots in the hope that someone can give me a start on cleaning up the problem.
1. The first shows the original update manager window.
2. The second shot show the first sign of the problem, with the heading "if you are using third party....etc....disable them".
3. As I have no idea if I am in this position, I went to the software manager to seek what resources were being used.
4. Screenshot 3 shows the result, and I assume from this that either I am going the wrong route, or I'm getting further in the mire.
Either way, I am clueless as to what to do next, so I'd appreciate some help.

Thanks,
John

---

### Post by hebrewofyhwh on 2014-03-12
I am a new user  but I had a update failure today too. So I re booted and then clicked on it again. It failed the second time. So I rebooted again, and that time it worked.  So try rebooting a time or two.

---

### Post by ibjsb4 on 2014-03-12
Nice pics, but its not giving the whole story.  Please run:

```
sudo apt-get update
```

And post any errors.  If no errors run:

```
sudo apt-get upgrade
```

Any errors? and ..

```
sudo apt-get dist-upgrade
```

Will attempt to upgrade kernel.

---

### Post by grey1beard on 2014-03-13
hebrewofyhwh - thanks, but 'been there, done that' to no avail.

 
ibjsb4 - many thanks. I'd tried sudo apt-get update, but had errors and then started down the op path.

Must leave now for hospital, but will repost with results this pm.
John

---

### Post by Vladlenin5000 on 2014-03-13
The error returned by "apt-get update" are of vital importance in determining your problem. Please post the results as suggested/requested above. 
Most likely you have one or more PPA (third party software repositories) that, for a yet unknown reason, are currently offline. Whether it's a temporary error or a definitive shutdown needs to be investigated.

---

### Post by grey1beard on 2014-03-13
Hi ibjsb4,

I ran sudo apt-get update, this time no errors.
Ran sudo apt-get upgrade, and the error report is
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-60-generic-pae but it is not installed

(The unmet dependencies were the same as reported when I first tried sudo apt-get update -f as suggested in my first attempt before coming onto the forum.)
Do I now run *apt-get -f install*, as sugested ?

Regards
John

---

### Post by matt_symes on 2014-03-14
Hi

Yep ! Run

```
sudo apt-get -f install
```

Post back any errors and we can help you out.

Kind regards

---

### Post by grey1beard on 2014-03-14
Sorry for long gap between postings - visits to Hospital take priority !

Sudo apt-get install -f produced the following, some of which I understand, some not, especially the comment 'no space left on device'.

When she first ran update manager, she probabply had a usb memory stick attached to the laptop (always watching Scandi-noir !), but I don't think that is relevant.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-60-generic-pae
The following NEW packages will be installed
  linux-headers-3.2.0-60-generic-pae
0 to upgrade, 1 to newly install, 0 to remove and 6 not to upgrade.
2 not fully installed or removed.
Need to get 0 B/978 kB of archives.
After this operation, 11.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 467891 files and directories currently installed.)
Unpacking linux-headers-3.2.0-60-generic-pae (from .../linux-headers-3.2.0-60-generic-pae_3.2.0-60.91_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-60-generic-pae_3.2.0-60.91_i386.deb (--unpack):
 error creating symbolic link `./usr/src/linux-headers-3.2.0-60-generic-pae/scripts/kconfig/zconf.lex.c_shipped': No space left on device
No apport report written because MaxReports has already been reached
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-60-generic-pae_3.2.0-60.91_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


John

---

### Post by JKyleOKC on 2014-03-14
That "no space left" comment could be that the disk is actually full, or it could be that your filesystem is out of inodes (which are part of the housekeeping behind the scenes, and cannot be enlarged without totally reformatting the partition, which would lose everything). Just this week I took part in another thread with similar symptoms, in which inodes were the problem. However the earlier suggestion that you run "apt-get autoremove" to get rid of obsolete files may take care of things in either case, since deleting a file also frees up its associated inode(s). You need to make the command "sudo apt-get autoremove" since full admin privilege is necesary, but if that command completes, then try the "install -f" operation again and post its output.

---

### Post by grey1beard on 2014-03-14
As suggested, I used the autoremove command, then, sudo apt-get -f install, but it takes me round in a very neat circle.
Disc usage manager indicates that only 16.7% of the available space is being used currently.

John

> pippa@pipsqueak:~$ sudo apt-get autoremove
[sudo] password for pippa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-60-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
pippa@pipsqueak:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-60-generic-pae
The following NEW packages will be installed
  linux-headers-3.2.0-60-generic-pae
0 to upgrade, 1 to newly install, 0 to remove and 7 not to upgrade.
2 not fully installed or removed.
Need to get 0 B/978 kB of archives.
After this operation, 11.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 467891 files and directories currently installed.)
Unpacking linux-headers-3.2.0-60-generic-pae (from .../linux-headers-3.2.0-60-generic-pae_3.2.0-60.91_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-60-generic-pae_3.2.0-60.91_i386.deb (--unpack):
 error creating symbolic link `./usr/src/linux-headers-3.2.0-60-generic-pae/scripts/mod/modpost.h': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-60-generic-pae_3.2.0-60.91_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by JKyleOKC on 2014-03-14
At this point I'd try this:
```

sudo apt-get remove linux-headers-3.2.0-29
sudo apt-get remove linux-headers-3.2.0-29-generic-pae

```
If that fails, and it might since you really do seem to be out of inodes, I would next look for any files in my home directory that I could do away with, and delete them (NOT move to trash; it used to be that holding down a shift key while deleting a file got rid of it without just putting it in trash). I would also try emptying the trash in case there are any files there that were "deleted" previously. You might also look into the /var/log directory; any files there that end in a number, such as ".1", would be safe to delete as well. Log files tend to linger for weeks or sometimes months after they are no longer useful.

If you can find as many as half a dozen files to delete, that ought to provide enough inodes for the system to be able to complete apt-get operations. Keep us posted on developments -- and I like your signature line very much!

---

### Post by grey1beard on 2014-03-14
Thanks for your help Jim.
Before I go further, can you tell me briefly the significance of inodes, and headers ?
Thanks,
John

---

### Post by grey1beard on 2014-03-14
Quick search for inodes led me to try this -

> pippa@pipsqueak:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda1       488640 481519    7121   99% /
udev            215806    497  215309    1% /dev
tmpfs           219460    409  219051    1% /run
none            219460      3  219457    1% /run/lock
none            219460      4  219456    1% /run/shm
/dev/sda5      4030464   6881 4023583    1% /home

John

---

### Post by thenh813 on 2014-03-14
IT appears 99% of inodes are used on /.
It could be that it dosent have enough to finish the update and fails. Although 7121 free Inodes should be enough, it does not hurt to clean up.

 Have you tried sudo apt-get clean? This removes all .deb packages that were downloaded and already installed. You would be suprised how many files APT keeps after it installs them.

Hmmm... my inode usage shown that none exist or are used on / or /home. Odd indeed... Probabally because I use ReiserFS which uses inodes differently and stores a file tree.

```

Filesystem     Inodes IUsed  IFree IUse% Mounted on
/dev/sda6           0     0      0     - /
udev           190432   533 189899    1% /dev
tmpfs          192862   446 192416    1% /run
none           192862     1 192861    1% /run/lock
none           192862     3 192859    1% /run/shm
/dev/sda5      128016   251 127765    1% /boot
/dev/sda1           0     0      0     - /home

```

Anyway, all my usage appears to be 1% so I am assuming you probabally need to delete some stuff.

---

### Post by grey1beard on 2014-03-14
Interesting, so I ran apt-get clean, and added 54 inodes to sda1 bringing it to 7175 !

John

PS  Jim - I'll start spring cleaning tomorrow. Time to hit the sack.

---

### Post by thenh813 on 2014-03-14
That means that there was 54 installer packages stored in /var/apt/packages.
I usually dont keep any packages after I install them, its a waste because when you have to download them again, its because they are updated and will be overwritten anyway. Thats why ubuntu recovery mode has it as one of the options, if ABSOLUTELY necessary, you just redownload. It frees up space, and can be easily undone.  Hopefully you can run a apt-get -f install tomorrow. You could run apt-get autoremove afterwards to uninstall unused libraries and files.

---

### Post by JKyleOKC on 2014-03-14
> **grey1beard said:**
> Interesting, so I ran apt-get clean, and added 54 inodes to sda1 bringing it to 7175 !

John

PS  Jim - I'll start spring cleaning tomorrow. Time to hit the sack.That might be enough to let the "install -f" complete!

Understand about being late. I'm currently 5 hours earlier than London's standard time (or 6 hours if you're on Summer time already; we went on it a week ago).

To expand on inodes and headers I'll have to get fairly technical but will try to keep it as simple as I can. The nature of reading and writing to magnetic tape or disks (they're essentially the same technology but disks allow faster access) makes it impractical to handle a single byte at a time, or even a variable number of bytes in a stream. In order to keep everything properly synchronized, they have to deal in standard-sized blocks of bytes. For more than 40 years, the "blocks" used by disks have been called "sectors" since they are sections of a circular "track" on the disk. Putting the data down in concentric circles, instead of the spiral used by old-time phonograph records, is what gives disks their speed advantage compared to tape.

To create a file, then, the system has to allocate enough sectors to that file to hold all its data, and must also include internal bookkeeping information to associate the allocated sectors with the file's name. One of the earliest magnetic disk file systems kept a table, called the File Allocation Table or FAT for short, that listed all of the sectors on the drive. Each cell of the table contained the index of its next-higher neighbor, initially, so that the table linked all of the sector together into an "available space list." When creating a file, that system took enough sectors from the head of the list to hold the data, and used the index of the first such sector's entry as the internal address of the file. It then updated an internal variable that pointed to the available space, so that it pointed to the next free entry.

When deleting a file, its first sector got linked back into the available space list, usually at the end of the list so that the deleted data did not get overwritten immediately.

The FAT was created when a disk was formatted, and its size could not be changed without reformatting the disk. In the very old days, each cell of the table was only a single byte, and since disks were very small, the table's size was (if I remember correctly from CP/M) 256 bytes, with the final cell at index 255 unused and its index used to flag the end of an allocation chain of links.

As disks got larger, that approach sort of fell apart. First, disk sectors were grouped into larger blocks known as clusters, and the FAT then referred to clusters rather than to sectors. Next, when the 8-bit CP/M system gave way to 16-bit MS-DOS, the FAT cell size increased first to 12 bits and later to 16 bits. Eventually it got to 32 bits, known as VFAT32. The basic idea of linking through an available space list remained about the same, though.

Meanwhile, experimenters were developing more exotic ways of keeping track of things. Adding more data to an existing file using the FAT system meant that eventually a single file could be scattered all over the surface of the disk. This is known as fragmenting the disk. When such a file is deleted, the available space list also becomes fragmented. As time goes on, the need for frequently changing the position of the read/write head tends to slow the whole system down.

One of the techniques they came up with was to introduce additional tables into the basic system, and cascade those tables through several levels. This greatly expanded the number of clusters that could be tracked, and at the same time tended to reduce fragmentation since the intermediate levels could be reorganized on the fly to keep files almost totally unfragmented. Each such intermediate table, like the original FAT, had to be created at the time of formatting and cannot be expanded, though.

And that's where the inodes come into the picture. Each inode is simply a cell in the highest-level table used by the file system. Once all of them are in use, it's not possible to create an additional file, or to increase the size of one that already exists, although you can continue to update existing files.

This has gotten rather long, and it's extremely over-simplified (even as complicated as the process sounds). Hopefully it helps answer your first question.

I'll try to explain "header" files later if you desire. See you tomorrow!

---

### Post by thenh813 on 2014-03-14
@[**[COLOR=#000000]JKyleOKC[/COLOR]**]("http://ubuntuforums.org/member.php?u=374258")
I knew inodes had to do with keeping track of files sizes and locations, along with some data like timestamp, but I did not know a lot of what you said. I learned how and why they exist, thank you, that always confused me. I always thought if there is a file allocation table why are inodes and trees necessary? Well, now I know why. I never knew of a 8 bit FAT and doubted that FAT12 was real or had much use. I thank you for posting that.

---

### Post by JKyleOKC on 2014-03-14
The 8-bit FAT was used only in 8-bit systems such as CP/M, and I'm not certain it lived very long even there. In those days, a LARGE disk could store only 640K bytes and standard usage was 360K (I just tossed out about 500 of those disks yesterday); by the time it became possible to put a megabyte on a disk, we had 12-bit FATs -- and they allowed up to a bit more than 8 MB to be stored!

---

### Post by thenh813 on 2014-03-14
@[**[COLOR=#000000]JKyleOKC[/COLOR]**]("http://ubuntuforums.org/member.php?u=374258")
Fascinating. I always like to learn about really old software and hardware, as well as keeping up with the current standards.

@[**[COLOR=#000000]grey1beard[/COLOR]**]("http://ubuntuforums.org/member.php?u=546578")
I just thought, if the update succeeds, make sure you still clean out so that future updates and storing of files is successful.

---

### Post by grey1beard on 2014-03-15
Jim, thanks for turning the light on. While the bulb here is pretty dim, at least I can see the picture.

I've just tried an analogy to explain(?) the problem to SWMBO - "It's like having a book with an index. When you start, the book has a list of pages in the index, but no entries against each page. As you start writing in the book, the subject appears in the index, and even though the page may only be half full, it still takes up one entry in the index. While the analogy allows the amount of data on each page to be variable, the number of entries in the index is fixed."

She has agreed to a major spring clean, so that will be done over the next few days, with me trying the *apt-get -f install* at intervals.
I'll post as soon as we get a result, but in the meantime I look forward to you thought on 'headers'.
Many thanks,

John

---

### Post by matt_symes on 2014-03-15
Hi

@OP. 

Look to delete as many of the Linux header packages as possible; all the ones you don't need.

They take up a large number of inodes as there are many header files within each package.

Open a terminal and copy and paste this into it.

```
dpkg -l | grep headers && uname -r
```

Copy and paste the results from the terminal into your next post and we'll be able to see if you can safely delete some of the Linux header packages.

Another option is to back up (move) your data to another hard drive, storage device or partition. This will free up inodes on your root partition.

Kind regards

---

### Post by grey1beard on 2014-03-15
Hi Matt,
Herewith terminal, as requested.

> pippa@pipsqueak:~$ dpkg -l | grep headers && uname -r
ii  linux-headers-3.2.0-29                 3.2.0-29.46                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-29-generic-pae     3.2.0-29.46                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-48                 3.2.0-48.74                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic-pae     3.2.0-48.74                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-49                 3.2.0-49.75                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic-pae     3.2.0-49.75                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-51                 3.2.0-51.77                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-generic-pae     3.2.0-51.77                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-52                 3.2.0-52.78                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic-pae     3.2.0-52.78                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-53                 3.2.0-53.81                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic-pae     3.2.0-53.81                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-54                 3.2.0-54.82                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic-pae     3.2.0-54.82                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-55                 3.2.0-55.85                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-55-generic-pae     3.2.0-55.85                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-56                 3.2.0-56.86                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-56-generic-pae     3.2.0-56.86                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-57                 3.2.0-57.87                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-57-generic-pae     3.2.0-57.87                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-58                 3.2.0-58.88                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-58-generic-pae     3.2.0-58.88                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-59                 3.2.0-59.90                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-59-generic-pae     3.2.0-59.90                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-60                 3.2.0-60.91                             Header files related to Linux kernel version 3.2.0
iU  linux-headers-generic-pae              3.2.0.60.71                             Generic Linux kernel headers
3.2.0-60-generic-pae

Regards
John

---

### Post by matt_symes on 2014-03-15
Hi

Blimey ! That's alot of header packages you have there.

From the package manager, delete all the header file packages that do *not* contain 

```
linux-headers-3.2.0-59
linux-headers-3.2.0-59-generic-pae
linux-headers-3.2.0-60
linux-headers-3.2.0-60-generic-pae
```

That will free up a load of inodes.

If you are not comfortable with doing this, just say so and i will give you a terminal command you can run to do the same thing.

After that, we should have a look at the kernels installed on your system that are associated with those header files.

Kind regards

---

### Post by grey1beard on 2014-03-15
Thanks Matt, I'd be grateful for the code. It will be a lot easier for me(and a lot quicker too).

Regards,
John

---

### Post by matt_symes on 2014-03-15
Hi

Open a terminal and copy and paste this command into it (less likely to introduce a typo).

```
sudo apt-get purge linux-headers-3.2.0-{29,48,49,51,52,53,54,55,56,57,58}{,-generic-pae}
```

After that has finished, post back the output of these command (copy and paste from the terminal)

```
df -i && dpkg -l | grep linux-image
```

Kind regards

---

### Post by grey1beard on 2014-03-15
The terminal for the first of your codes is
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-60-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
pippa@pipsqueak:~$ 

and to the second code is

> pippa@pipsqueak:~$ df -i && dpkg -l | grep linux-image
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda1       488640 481470    7170   99% /
udev            215806    497  215309    1% /dev
tmpfs           219460    406  219054    1% /run
none            219460      3  219457    1% /run/lock
none            219460      5  219455    1% /run/shm
/dev/sda5      4030464   6906 4023558    1% /home
ii  linux-image-3.2.0-29-generic-pae       3.2.0-29.46                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-48-generic-pae       3.2.0-48.74                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-49-generic-pae       3.2.0-49.75                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-51-generic-pae       3.2.0-51.77                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-52-generic-pae       3.2.0-52.78                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-53-generic-pae       3.2.0-53.81                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-54-generic-pae       3.2.0-54.82                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-55-generic-pae       3.2.0-55.85                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-56-generic-pae       3.2.0-56.86                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-57-generic-pae       3.2.0-57.87                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-58-generic-pae       3.2.0-58.88                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-59-generic-pae       3.2.0-59.90                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-60-generic-pae       3.2.0-60.91                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae                3.2.0.60.71                             Generic Linux kernel image

John

---

### Post by matt_symes on 2014-03-15
Hi

Did that remove the header packages ? I'm not sure from what you have posted.

To be sure, from the terminal

```
sudo dpkg -P linux-headers-3.2.0-{29,48,49,51,52,53,54,55,56,57,58}{,-generic-pae}
```

Then post the output of this command so we can be sure.

```
dpkg -l | grep headers
```

Then we'll fix the other issues.

Kind regards

---

### Post by grey1beard on 2014-03-15
It didn't seem to, as I just tried *dpkg -l | grep headers* while waiting, and the headers were the same.
Will now try the -r code, and will post result.
John

---

### Post by grey1beard on 2014-03-15
Yes, a result. I saw tyhe terminal removing then this time.

**dpkg -l | grep headers**
> 
pippa@pipsqueak:~$ dpkg -l | grep headers
ii  linux-headers-3.2.0-59                 3.2.0-59.90                             Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-59-generic-pae     3.2.0-59.90                             Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-60                 3.2.0-60.91                             Header files related to Linux kernel version 3.2.0
iU  linux-headers-generic-pae              3.2.0.60.71                             Generic Linux kernel headers
pippa@pipsqueak:~$ 

---

### Post by matt_symes on 2014-03-15
Hi

Excellent, We are making progress.

Copy and paste this into a terminal

```
sudo dpkg -P linux-image-3.2.0-{29,48,49,51,52,53,54,55,56,57,58}-generic-pae
```

Then type

```
sudo apt-get -f install
```

Finally post back the output of

```
df -i
```

Kind regards

---

### Post by grey1beard on 2014-03-15
Matt, I thought that -P (which I take to be Purge) had given it terminal diarrhea :P


> pippa@pipsqueak:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda1       488640 195855  292785   41% /
udev            215806    498  215308    1% /dev
tmpfs           219460    407  219053    1% /run
none            219460      3  219457    1% /run/lock
none            219460      5  219455    1% /run/shm
/dev/sda5      4030464   6920 4023544    1% /home
pippa@pipsqueak:~$ 

John

---

### Post by matt_symes on 2014-03-15
Hi

> **grey1beard said:**
> Matt, I thought that -P (which I take to be Purge) had given it terminal diarrhea :P

It does spit out some info :D

41% used inodes on root (/) leaves 59% free. That's plenty.

Assuming *apt-get -f install* returned successfully, you're good to go.

Kind regards

---

### Post by grey1beard on 2014-03-15
Yes, Matt, that went smoothly.
Many thanks for your guidance.
Unless I hear to the contrary, having discovered that my own laptop is in a similar state with all the linux-headers + pae entries from  0-40 to 0-60, I'm considering following the same process, starting at your #28, modifying the {numbers} where necessary.

Kindest regards from both SWMBO and myself,
John

EDIT on 2nd thoughts it doesn't seem worth it, with only 23% inodes used on mine !

---

### Post by JKyleOKC on 2014-03-15
> **grey1beard said:**
> EDIT on 2nd thoughts it doesn't seem worth it, with only 23% inodes used on mine !Good to see that Matt has steered you through the abyss! His code taught me a bit, too; I've not used the "alternating" feature with the curly braces but it certainly saves lots of typing.

As for "doesn't seem worth it" that's your call, but in my experience it's always worth it. Hitting the "inode limit" doesn't happen often, but when it does it seems always to be at the worst possible time, and under confusing circumstances. I run "Ubuntu Tweak" on my systems at least once a month just to be sure they're as clean as I can get them...

---

### Post by Odyssey1942 on 2014-03-15
I am having a somewhat similar problem. Please see thread "Firefox freezes, cannot reinstall"

Could inodes be an issue in my case?

---

### Post by thenh813 on 2014-03-15
@[**[COLOR=#000000]grey1beard[/COLOR]**]("http://ubuntuforums.org/member.php?u=546578")
Hey, you freed up a lot of inodes! Looks like it is fixed.
Wow two pages since I posted last night.
Hope you dont run into any more problems.
Well, I guess im done here, have a nice day.

@[**[COLOR=#000000]Odyssey1942[/COLOR]**]("http://ubuntuforums.org/member.php?u=85063") 	 
I would suggest not posting on others questions about your own or on solved threads you had previously nothing to do with. I will take a look at your problem, but please keep these in mind in the future.

---

### Post by grey1beard on 2014-03-15
Final words from me.
Thank you all. I finished by reducing my own inode load from 23% to 13% - 

> john@john-HP-G7000-Notebook-PC:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda6      3217536 398858 2818678   13% /
udev            215806    497  215309    1% /dev
tmpfs           219461    438  219023    1% /run
none            219461      3  219458    1% /run/lock
none            219461      4  219457    1% /run/shm
john@john-HP-G7000-Notebook-PC:~$ 

but will take Jim's advice, and keep it under review.
Over, and out.
John

---

### Post by JKyleOKC on 2014-03-15
> **grey1beard said:**
> I look forward to you thought on 'headers'.I'm a bit late with it, but here it is. Bear with me as I go back into the mists of prehistoric times...

For a starting point we must go back to the very beginnings of computing machines and note that at the lowest level, everything depends on patterns of switches that are either ON or OFF. Each switch's state is represented by a "binary digit" that's either 0 for OFF or 1 for ON, known as a "bit." Today these bits are organized into groups of 8, 16, or 32, known as "bytes," "words," and "dwords" respectively, and we routinely deal with not just millions but billions of them (a gigabyte is one billion bytes or eight billion bits). However in the earliest days their numbers were much smaller.

The first machine with which I dealt, back in 1961, had a total memory capacity of 4,096 15-bit words (the engineers had not yet learned that it's much more efficient do do everything in powers of 2, such as 2, 4, 6, 16, 32, and so on) and that was, for its time, a state-of-the-art development since it could track a rocket in flight -- which the biggest IBM monster of the day was unable to achieve.

With such small machines, it was normal to write a program -- any program -- as a single monolithic sequence of machine instructions. Originally, these instructions were simply human-readable depictions of the bit patterns, what we today know as "hexadecimal code" or "hex" represented by the digits 0-9 followed by A-F for the 16 possible patterns when bits are examined in groups of four. It's easier for we humans to deal with "43" (the bit pattern representing the character "C" in the ASCII code used almost universally now) than with "01000011" which is the actual pattern.

It didn't take long for folk to realize that they could give names to each machine instruction's pattern, and use a special program to translate the names into the actual pattern when creating a new program. That became known as "assembly language" and made life much simpler for programmers. Programs, though, were still written as single sequences of assembly language instructions.

In trhe earliest days, each different CPU design usually had its own unique assembly language. This meant that a program written to run on one type of CPU could not run on a different one. Consequently, in the late 1950s and early 1960s, a higher level of translation was introduced, in which the programmer wrote in a language more like "natural language" and the first translation (by a program called a compiler) turned the original instructions in sequences of assembly language that would accomplish the intended result. That translated sequence was, in turn, assembled into "machine language" consisting of the actual bit patterns.

This development allowed programs to be written in the language that the compiler understood, without regard to the CPU model on which they would eventually run, and by using various versions of the compilers, the instructions could output to CPU-specific intermediate files.

At the same time this was going on, people began to realize that writing each program as a self-contained full package involved horrendous amounts of duplicated effort. For instance, opening a file to read data from it was always the same sequence of instructions (for any specific type of file and of storage device) but had to be spelled out in excruciating detail. The same thing was true of every other kind of repeated action. More effort was being spent "reinventing the wheel" than was expended on creating really new applications.

By that time, decks of punched cards were the standard input mechanism, and savvy developers began keeping private decks of such routines that they could simply insert into those for a new program, where applicable. These private decks eventually got turned into "code libraries" and those are with us to this day, mostly in files whose names begin "lib," located in the /usr/lib directory.

Once libraries came into use, it became necessary to describe their content so that programmers could use them when creating new applications. Originally, such descriptions had to be typed in at the start of each program's source code. That worked, but again involved huge amounts of duplicated effort. When compilers gained the ability to include more than one file, it became possible to replace these descriptions at the head of a program with a simple text file, and then to include that file in any program that used the library.

Which brings us to "header files." They are just those simple text files that describe the contents of code libraries. We sometimes need them during the update process because certain kernel modules may have to be recompiled to achieve the update. You can find quite a few such files in the /usr/include directory -- but note that they will be quite cryptic in most cases, since they're designed to be read by a compiler program rather than by untrained humans, yet carry enough human-readable information to be maintainable!

---

### Post by grey1beard on 2014-03-16
Hi Jim,
Many thanks for another lucid explanation.
*The first machine with which I dealt, back in 1961,......*
My own experience started in 1960, when the Army(R.Sigs/UK) started to teach me the logic ccts that the machines I had to maintain/repair didn't even have ics in  them. Valves, resistors, capacitors, and diodes populated my territory, and working later in the tropics, with un-tropicalised capacitors, used to drive me crazy.

(PM on its way.)

Regards, and thanks for your help,
John

---

