---
title: "Moving My Documents from Windows to Ubuntu"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by anonymoustache on 2008-08-19
I've decided that I'm going to make the full switch to Ubuntu. I want to completely remove everything about Windows, except for the "My Documents" folder. Can someone direct me to a tutorial explaining how to do this?

---

### Post by DR583V3 on 2008-08-19
You can backup the My Documents folder. You can use a blank DVD, large enough flash drive, external hard drive, or any other storage media.

---

### Post by billgoldberg on 2008-08-19
> **anonymoustache said:**
> I've decided that I'm going to make the full switch to Ubuntu. I want to completely remove everything about Windows, except for the "My Documents" folder. Can someone direct me to a tutorial explaining how to do this?

Just copy the contents of the folder to a external hdd or dvd. 

Once Ubuntu is installed, just copy them into the Ubuntu home folder in the right folders.

This is a very, very basic task.

I'm sorry to say, but I don't think Ubuntu will be for you.

---

### Post by LowSky on 2008-08-19
well you just need access to your Windows files, you might have to mount the partition.
the partition should be right on your desktop
just copy and paste the folder where you want it

---

### Post by anonymoustache on 2008-08-19
Ah, yes, I forgot to mention that i do not have any sort of removable storage devices or any DVDs or anything. I contemplated compressing all of my documents, but can't find a website that will let you upload more than 5GB at a time.

---

### Post by anonymoustache on 2008-08-19
> well you just need access to your Windows files, you might have to mount the partition.
the partition should be right on your desktop
just copy and paste the folder where you want it

How do I go about doing this? I've booted up form the Ubuntu CD and am on the step concerning partitioning the disk. I haven't got a clue what to do here...

---

### Post by DR583V3 on 2008-08-19
Have you tried adrive? [http://www.adrive.com/](http://www.adrive.com/)

---

### Post by LowSky on 2008-08-19
If you have not install ubuntu yet your in luck. Ubuntu will auto move your windows docutment and your wallpaper automatically to your ubuntu install

As for Partitioning, I would leave windows on there for a little while, so you can swithc between while getting used to ubuntu more. choose guided install for disk partitioning. it will do all the work

---

### Post by linuxguymarshall on 2008-08-19
I think the ubuntu installer has a "Migration Assistant" but I recommend a flash drive

---

### Post by DR583V3 on 2008-08-19
I would still try to backup the data. You never know what may go wrong.

---

### Post by anonymoustache on 2008-08-19
> Have you tried adrive? [http://www.adrive.com/](http://www.adrive.com/)

I'd rather not use that method to get my documents to ubuntu. Is there not a simpler way to get your stuff from one OS to another?

---

### Post by shizakapayou on 2008-08-19
Do you have a DVD burner?  Writable media is cheap these days, and should be available in small packs.  Even 4GB flash drives can be found for under $20.

Personally, I'd recommend setting up a dual-boot for now till you're completely comfortable.  You can always format the Windows partition later and reclaim the space for Ubuntu.

---

### Post by linuxguymarshall on 2008-08-19
Dude, just use usb media like a flash drive or external HDD or dvds. 

Or if you have multiple hard drives format one (If you recently bought your computer it is probably a windows recovery drive) and place all your files on it. Install Ubuntu to your primary hard drive and then copy files from your (probably) slave drive

---

### Post by fuhrysteve on 2008-08-19
You could create a 5gb Fat32 partition on your harddisk now, then put all the files there. 

When you install ubuntu, have it format all the NTFS space, then install there. After you install, mount the FAT32 partition (if Ubuntu didn't do it automatically), copy the files to your /home/user/Documents folder (or wherever) and then use the partition editor
```
sudo apt-get install gparted
```
to remove the FAT32 partition.

---

### Post by Rolcol on 2008-08-19
If you're going to use ubuntu for compression, you can compress your documents and then use the split command to separate it into 5GB chunks.

```
tar -cvzf My-Documents.tar.gz /media/ntfs-drive/Documents\ and\ Settings/User/My\ Documents/
split -b 5000m My-Documents.tar.gz docs
```
That will compress and then split the file (but leave the original) into 5GB chunks.  If you want to split as it's compressing (haven't tested this so don't know if it'll work):```
tar -cvzf - /media/ntfs-drive/Documents\ and\ Settings/User/My\ Documents/ | split -b 5000m - docs
```
Both split methods will create files labeled docsaa, docsab,docsac, etc. To join them:```
cat docs* > My-Documents.tar.gz
```

---

