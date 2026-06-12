---
title: "When making a backup do the File Systems Have To be the Same?"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by Wiking on 2012-01-07
Hi, I need to make a backup of my system. So far I plan on using clonezilla to makes clones/images of my system partitions. 

I would like to save it to an external hard drive that also has my Windows 7 backup images. 

Is that asking for problems? Can I save a clone of Ext4 partitions on an external drive that is using NTFS? It's the only external drive I have at the moment.

Do you guys backup the /boot partition as well?

---

### Post by 73ckn797 on 2012-01-07
If it is only a back-up and is in an image file, it seems that it would be like any other file and would just be sitting there. Restoring the back-up to a new drive for future use would have to have the same format (ext3 or ext4). There could be issues if the system is totally different (ie ... motherboard, 64 vs 32 bit and other factors).

---

### Post by bluexrider on 2012-01-07
> **Wiking said:**
> Hi, I need to make a backup of my system. So far I plan on using clonezilla to makes clones/images of my system partitions. 

I would like to save it to an external hard drive that also has my Windows 7 backup images. 

Is that asking for problems? Can I save a clone of Ext4 partitions on an external drive that is using NTFS? It's the only external drive I have at the moment.

Do you guys backup the /boot partition as well?

If that's the case I think you would be better off partitioning your external drive to accept EXT3 or EXT4

---

### Post by Wiking on 2012-01-08
Thanks guys, I went ahead and made a EXT4 partition on my external drive, just to avoid any problems. Created the backups and clonezilla said they were all restorable. 

I got an interesting message when I was checking the file system for errors before backing up:

> SuperBlock last write is in the future (by less than a day, probably due to the hardware) fix? (y/n)

Is that because I changed the time in /etc/default/rcS?
I'm not too concerned as everything went well, would just like to know.

Should I also backup the /boot drive since I have 2 distros?

Thanks again.

---

### Post by jjex22 on 2012-01-08
Hi there, to the first question, no, the formatting doesn't matter so long as your restore OS has read access to that drive - I actually recommend ntfs for any shared data storage - you can get any linux bsd or osx to read/write ntfs - Windows isn't as forgiving with other filesystems. 

The only argument for not having an ntfs file system is that you may accidentally delete the image file from windows... you are just as likely to do this from linux ie not very! keep the windows backups and linux backups in different directories and image files of backups should always have read only protection.

you may be interested in backing up your entire drive to an image file - you can do this from clonezilla or any _unix live cd_ by doing this you get a total image of the hdd - windows partitions, boot sectors, encrypted home drives, lvms you name it a restore will restore your entire machine exactly as it was at the time of the back up. As I'm a distro junkie, I have an incredibly unecessary number of OS's on my drives... and all my OS's have several partitions - 3 for windows, typically 7 for *nix systems - though sometimes they are lvms (cent) several swap partitions, shared data partition and then there's the complicated boot structure that this set up creates!

I recommend the live cd - full Hdd images take a very long period of time and by using the live CD you can keep working as usual, surf the net etc - you can install things to the live environment to make it work properly, and even store the .deb packages for problem drivers on your machine for when you do the backup - for example I have broadcom chips on 2 of my machines so I keep the necessary debs - fwcutter etc on my data partition, - boot up the live cd, go to the data partition and install the debs! job done, full support in my live environment (I could use fedora that has out of the box broadcom... but I'd prefer to be in ubuntu for a couple of hours! of course you could use a live cd with persistance!

There are a massive number of ways to do write the command, but the basics are allways the same.
1) make a note of the pathway to where you want the back-up image stored for example
```

/media/Back-up\ Drive/Ubuntu\

```2) make sure nothing is mounted - easiest way is open up gparted and have a look - it'll show you in the table where things are mounted (you unmount them by right clicking and "unmount"), as well as the name for each device - /dev/sda, /dev/sdb, /dev/sdc, in the top right corner - being graphical it's very easy to work out where everything is and if it's mounted.

3)now re-mount the backup drive - why did we unmount? just to reduce the risk of errors!

4)Step one of the back-up is to create the hdd image:
```

sudo dd if=dev/sd[COLOR=Red]a[/COLOR] conv=sync,noerror bs=64k of =/[COLOR=Red]pathtobackup[/COLOR][COLOR=Black].img[/COLOR]

```This will copy the entire drive into an img file in the destination you specify in [COLOR=Red]pathtobackup[/COLOR]. Take care - never get if and of the wrong way round, when using 'dd' always remember "I comes before O" or "you must go In before you can go Out" the letter [COLOR=Red]a [/COLOR]should be the letter of your primary drive you found in gparted.

5) you may want to shrink the image file so you can store more backups on your drive? to do this the command is.
```

sudo tar cjfv [COLOR=Red]name-you'd-like-for-compressed-image[COLOR=Black].tar.bz2[/COLOR][/COLOR] /[COLOR=Green]path/to/image/to/compress[/COLOR]

```You may see many guides that use gzip to compress images, you really should use tar for backups as it preserves ownership and bzip compresses further than gzip anyways :)

6) If you wanted to store the image on a cloud server such as Adrive, or burn it to disks, you'll need to spilt it up using split:
```

split --bytes[COLOR=Green]1G[/COLOR] -d [COLOR=Red]imagefile.tar.bz2[/COLOR][COLOR=DarkOrange] /directory/for/split/files[/COLOR]

```This splits the image into [COLOR=Green]1G[/COLOR] bits that are easy to upload. if you wanted to burn cds, you'd change it to [COLOR=Green]690M

[COLOR=Black]Hope this is useful?
To go in the other direction and rebuild a system or failed hdd:

1)restore split
```

cat [COLOR=Green]split-file-name[COLOR=Black]* > [COLOR=Red]new-file-name.tar.bz2
[/COLOR][/COLOR][/COLOR]
```[COLOR=Green][COLOR=Black][COLOR=Red][COLOR=Black]

2) decompress
```

tar xjfv [COLOR=Red]image-filename.tar.bz2
[/COLOR]
```[COLOR=Red]
[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]
3) Restore drive
```

sudo dd if=/[COLOR=Green]path/to/image/file.img[/COLOR] of=/dev/sd[COLOR=Red]a[/COLOR][COLOR=Black]
[/COLOR]
```This is the most important part - never issue this command before you've double checked that /dev/sd[COLOR=Red]a[/COLOR] is the right device - afterall you're about to destroy everything on it and replace it with you're image.

Hope this is usefull - you can combine these in a number of ways using 
```

&&

```or
```

|

```The easiest way is just to add && between each command - that way it will do all of the steps ina row one after the other without you needing to be there, but there are much more effienct ways of typing that massively long command!

---

### Post by jjex22 on 2012-01-08
> **Wiking said:**
> 
Is that because I changed the time in /etc/default/rcS?

Thanks again.
yup :) it's not really a problem - may as well hit Y if you see that again!

---

