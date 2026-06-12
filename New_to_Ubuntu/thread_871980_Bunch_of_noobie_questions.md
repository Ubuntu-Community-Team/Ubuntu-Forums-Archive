---
title: "Bunch of noobie questions"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by foy1der on 2008-07-27
Hi,
I have been using Ubuntu on and off for a couple of months now (more off than on). So I know a little bit about what I would like to do but I am having trouble getting the OS to do what I would like. 
Let me get the real easy question out of the way first. Where would I go to find a glossary of sorts for common terminal commands like making directories, deleting files, etc.
My second question, I think is not as straight forward. I installed the latest version of Ubuntu this morning. After the install, I when and got all the latest updates then turned it off and installed a hard drive. It was formatted for NTFS although nothing was on it. So I try to mount the thing and it doesn't all me to mount it. Citing "Unable to mount volume" I search for a solution for the problem and it gets me nowhere. Finally, I stumble upon [[COLOR="RoyalBlue"]this[/COLOR]](https://help.ubuntu.com/community/InstallingANewHardDrive#Create%20a%20Mount%20Point) page and start to follow along. When I get down to the mounting portion, it give me a command not found error.

---

### Post by L Campbell on 2008-07-27
> **foy1der said:**
> Hi,
I have been using Ubuntu on and off for a couple of months now (more off than on). So I know a little bit about what I would like to do but I am having trouble getting the OS to do what I would like. 
Let me get the real easy question out of the way first. Where would I go to find a glossary of sorts for common terminal commands like making directories, deleting files, etc.
My second question, I think is not as straight forward. I installed the latest version of Ubuntu this morning. After the install, I when and got all the latest updates then turned it off and installed a hard drive. It was formatted for NTFS although nothing was on it. So I try to mount the thing and it doesn't all me to mount it. Citing "Unable to mount volume" I search for a solution for the problem and it gets me nowhere. Finally, I stumble upon [[COLOR="RoyalBlue"]this[/COLOR]](https://help.ubuntu.com/community/InstallingANewHardDrive#Create%20a%20Mount%20Point) page and start to follow along. When I get down to the mounting portion, it give me a command not found error.

This might help you for a 'glossary of terms'.

[http://ubuntulinuxhelp.com/friday-fun-useful-linux-terminal-commands-for-new-users/](http://ubuntulinuxhelp.com/friday-fun-useful-linux-terminal-commands-for-new-users/)

---

### Post by rockerphil on 2008-07-27
ok, the first thing you want to do really is to enable all your repos, this can be easily done through editing the /etc/apt/sources.list file as superuser (you can't change anything beyond your own home folder without being superuser) so my best suggestion is to run this in terminal:

sudo gedit /etc/apt/source.list

what you want to do is look closely, i repeat, closely, and delete the # next to anything that says deb or deb-src and then a URL. these are the repositories from which you'll be installing a lot of your software. once that is done save and exit gedit and run:

sudo apt-get update

to update your system. as far as a list of the commands i'm sorry, not sure as where to find one. now, to mounting your NTFS partition. simply run:

sudo fdisk -l

(l is a lower case L)

and that will give you your partition table, take a look and see which one is formatted to NTFS. the name at the beginning of that line is going to be the drive label of the partition you want to mount. for example my NTFS partition shows up as /dev/sdb2. so once you've got that figured out i'd suggest making a mount point somewhere in your home folder. this can be easily done by creating a new folder. i use the name Media since all of my multimedia is stored there. once you've got that done simply run this in terminal

sudo mount /dev/sdb2 ~/Media

of course you'll have to adjust the partition label to fit your system, and be sure to have the NTFS driver called ntfs-3g installed, it should be installed with Ubuntu by default, but just in case you can install it with:

sudo apt-get install ntfs-3g

i hope this information helps,

Phil

---

### Post by ibuclaw on 2008-07-27
There are lots of places where you can find out about the most basic Linux Commands.

One small google search brought me here.
[http://people.ischool.berkeley.edu/~kevin/unix-tutorial/toc.html](http://people.ischool.berkeley.edu/~kevin/unix-tutorial/toc.html)

I've checked it out and 99.99% of it is usable with Ubuntu.

Regards
Iain

---

### Post by foy1der on 2008-07-27
Thanks for the quick replys.
rockerphil,
As for mounting the drive, it is no longer formatted in NTFS. The guide that I was referencing in my OP was a how to on installing a new harddrive. As there was nothing of value on the drive I went along with that.

Here is the output of the fdisk
```


Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabc8abc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2365    18996831   83  Linux
/dev/sda2            2366        2434      554242+   5  Extended
/dev/sda5            2366        2434      554211   82  Linux swap / Solaris

Disk /dev/sdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```
The last line is what has me worried, as I said, there is nothing of value on the drive, but I think I may have my the problem worse. 
Additionally, let me point out what my end goal is, I would like this ubuntu machine as a file server for other windows computers on my network. Should this drive be formatted in NTFS in order to so this?

EDIT:
OK out of curiosity, I went back to the web page describing how to install a new hard drive and tried again. I used the following command to set up the partition
```

  sudo mke2fs -j /dev/hdd1

```

After that, mounting when off without a hitch.
If anyone has any advice as to the choice I made in file systems considering this drive will be serving Windows PC's, I would be more than happy to hear it.

Thanks again for the help.

---

### Post by Zimmer on 2008-07-27
> **foy1der said:**
> Thanks for the quick replys.
rockerphil,
As for mounting the drive, it is no longer formatted in NTFS. The guide that I was referencing in my OP was a how to on installing a new harddrive. As there was nothing of value on the drive I went along with that.

Here is the output of the fdisk
```


Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabc8abc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2365    18996831   83  Linux
/dev/sda2            2366        2434      554242+   5  Extended
/dev/sda5            2366        2434      554211   82  Linux swap / Solaris

Disk /dev/sdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```
The last line is what has me worried, as I said, there is nothing of value on the drive, but I think I may have my the problem worse. 
Additionally, let me point out what my end goal is, I would like this ubuntu machine as a file server for other windows computers on my network. Should this drive be formatted in NTFS in order to so this?

Looks like it needs formatting/partitioning  ..
Have a read at 
[http://www.ginad.org.uk/Frameset.html](http://www.ginad.org.uk/Frameset.html)
and planning partitions at
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by halitech on 2008-07-27
Ubuntu and writing to NTFS *can* be flaky (although I've been using an external 200gig with NTFS for a few months with no problem) so I would suggest using FAT32 to format it

---

### Post by nicfallenangel on 2008-07-27
> **foy1der said:**
> If anyone has any advice as to the choice I made in file systems considering this drive will be serving Windows PC's, I would be more than happy to hear it.

As already mentioned, NTFS can be flaky in Linux in general, I'm trying to remember but I think I had an Ubuntu load that used Samba to share folders on an ext3 hard drive. (Samba is the protocol that windows uses to share files/folders.) You can install it through the add/remove programs window or synaptic. I'm in the process of reinstalling Samba now to test but as far as I remember as long as the protocol was supported on the other computers, the host OS is the only real determining factor on whether or not shares or file systems can be read on the network. Hope this helps, and I'll post back with my results.

---

