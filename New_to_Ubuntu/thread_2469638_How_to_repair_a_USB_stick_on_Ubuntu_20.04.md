---
title: "How to repair a USB stick on Ubuntu 20.04?"
date: 2021-12-04
forum: New to Ubuntu
---

### Post by bhubunt on 2021-12-04
Hi All,
The USB stick I used on my laptop, running Ubuntu 20.04, is no longer recognized after I copied some files on it from the hard drive. It does not show up when I stick it into the USB port and it also wasn't recognized on a Windows computer.

On another forum, I came across the following recommendation:

-try repairing the stick using [COLOR=#000000][FONT=&amp]ntfsfix in linux
and/or
-try repairing the stick using the [/FONT][/COLOR][COLOR=#000000][FONT=&amp]ntfs filesystem of a Windows computer.

Do any of you have any experience with this?

Thanks.[/FONT][/COLOR]

---

### Post by sudodus on 2021-12-04
You can analyze the problem according to [this link](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035), and if you are lucky, find a solution.

---

### Post by bhubunt on 2021-12-04
Hi Sudodus,
Thanks very much for the link, which is very helpful.

I am a real newbie, so pls allow me to ask a follow-up question: 

is there anything I need to watch out for if I wan't to make sure not to lose the current data on the USB stick (assuming the stick is not totally corrupted)?

---

### Post by tea for one on 2021-12-04
> **bhubunt said:**
> The USB stick I used on my laptop, running Ubuntu 20.04, is no longer recognized after I copied some files on it from the hard drive. It does not show up when I stick it into the USB port and it also wasn't recognized on a Windows computer.

> **bhubunt said:**
> is there anything I need to watch out for if I wan't to make sure not to lose the current data on the USB stick (assuming the stick is not totally corrupted)? 

If the USB stick is not recognised in both Ubuntu and Windows, that is probably an indication that the device is damaged?

Boot up your Ubuntu OS, plug in the USB device, open a terminal and enter:-
```
sudo parted -l
```

Please post the output in code tags via **Adv Reply**

---

### Post by bhubunt on 2021-12-04
Hi Tea for One,
Thanks very much for the helpful hint. I will try to do that and post the results later. It may be a little while. 
Regards

---

### Post by sudodus on 2021-12-04
If the USB stick is (or seems to be) read-only, yes, **backup** the files that you want to keep to another drive before it is too late.

The repair actions might fix the drive, but wipe its content, so again, **backup** the files that you want to keep to another drive.

---

### Post by bhubunt on 2021-12-04
Hi Sudodus,
Can I get the data off the USB stick if it is in read-only mode and not totally damaged? I used this stick on the Ubuntu laptop about which I have questions in my other thread: 

[https://ubuntuforums.org/showthread.php?t=2469611](https://ubuntuforums.org/showthread.php?t=2469611)

Regards

---

### Post by sudodus on 2021-12-04
If the drive is read-only you can read the data on it. If you cannot read, it is in a worse condition. Please notice that I am talking about the drive hardware.

The file system might be damaged, and might be possible to repair, if the drive hardware can still be written to. And in this case it might also be possible to recover some files or all files (depending on the damage).

---

### Post by yancek on 2021-12-05
In your initial post, you mention suggestions from elsewhere to use a windows operating system to attempt to repair the usb drive but you do not indicate what type of filesystem you have on the usb.  Using ntfsfix or a windows computer assumes a windows ntfs filesystem.  Do you in fact have an ntfs filesystem on the drive?  What exactly was on the usb stick before you copied 'some file' to it?  Being 'read-only' means it can be read but not written to.  Your initial post states that you could write to it as that was the beginning of the problem, copying/writing files to the usb.

What was on the usb prior to copying these files to it, what had it been used for?  Did you have some iso file copied to it to boot, just data files?
Have you tried the usb in different ports?
With the usb plugged in, run the "sudo parted -l "command suggested above and post the output.

---

### Post by bhubunt on 2021-12-05
Yancek, thanks for the clarification. Yes, I tried the stick in different ports on the Ubuntu laptop and on a Windows computer, but it was not recognized. The stick simply contains LibreOffice docs and PDFs, nothing else, so no windows ntfs filesystem. Thanks for warning me against trying that one out. I will try and post the output using sudo parted -l some time in the next few days.
Regards

---

### Post by Autodave on 2021-12-05
USB sticks die all the time.....and without warning.  NEVER trust and single means to backup anything important!  Myself, I have 2 backups at home and a third one offsite at my mother's place.

As for your USB stick, there is probably nothing that you can do at this point to save anything on it.  I have heard people say that if you put them in a freezer for an hour or two, you may be able to get it to work briefly.  If that works for you, and I sincerely doubt that it will, get your stuff off of it quickly, buy a new USB stick, and bury that one.

---

### Post by yancek on 2021-12-06
>   The USB stick I used on my laptop, running Ubuntu 20.04, is no longer  recognized after I copied some files on it from the hard drive. It does  not show up when I stick it into the USB port and it also wasn't  recognized on a Windows computer.


USB drives fail all the time without warning.  Since it was previously working on Ubuntu anyhow as you were able to write those files to it, it doesn't seem likely that there is any relationship between writing files from your hard drive to the USB from Ubuntu.  If you have tried using different usb ports on both Ubuntu and windows and get no response, that is a pretty good sign of failure.  If you don't get any positive response from the following commands relating to the usb, it is a pretty sure sign the drive is dead. 

>   sudo fdisk -l
sudo blkid
sudo lsblk

Also, the parted command suggested above.

---

### Post by bhubunt on 2021-12-06
The USB stick has indeed given up the ghost. I just cannot get it to be recognized. The USB stick only had data files on it, light stuff (PDFs and LibreOffice docs). I have back ups, except for a few paragraphs in a current doc I am working on but I shall be more careful now that you all have confirmed the fragile nature of such sticks. Are those small metal jet flash sticks any sturdier?

---

### Post by sudodus on 2021-12-06
SSDs are sturdier, and there are USB SSDs, but the cheapest way to use an SSD via USB is probably to buy a 'small' SATA SSD (or two) and a USB 3 to SATA adapter.

There are also sturdier USB pendrives, but they are very expensive.

---

### Post by bhubunt on 2021-12-06
Thanks for the info. I just found this Wired article about good USB pendrives, but it does not explain how to format them for Ubuntu, for some reason...

[https://www.wired.com/gallery/best-usb-flash-drives/](https://www.wired.com/gallery/best-usb-flash-drives/)

---

### Post by ActionParsnip on 2021-12-06
Does the device show up if you run
```

sudo fdisk -l

```

---

### Post by sudodus on 2021-12-07
How do you want to format them for Ubuntu? It depends on how you intend to use the drive.

- As Ubuntu-only data storage?
- As Ubuntu-and-Windows data storage?
- As Ubuntu-and-Windows-and-MacOS data storage?

- As Ubuntu live drive or Ubuntu installer drive?
- As Ubuntu persistent live drive?
- As Ubuntu installed system in USB drive?

---

### Post by bhubunt on 2021-12-07
Primarily to store PDFs, LibreOffice docs, word docs and jpegs on. 

> **sudodus said:**
> How do you want to format them for Ubuntu? It depends on how you intend to use the drive.

- As Ubuntu-only data storage?
- As Ubuntu-and-Windows data storage?
- As Ubuntu-and-Windows-and-MacOS data storage?

- As Ubuntu live drive or Ubuntu installer drive?
- As Ubuntu persistent live drive?
- As Ubuntu installed system in USB drive?

---

### Post by sudodus on 2021-12-07
If you want Windows access, it should be OK with the old-style FAT32 file system (max file size 4 GB should be no problem with such files), or if you want a better file system, NTFS.

If you need only Linux access, you can use the ext4 file system.

You can [install and] use **gparted** to create a partition table if necessary, a partition and the file system you want in the partition.

---

### Post by bhubunt on 2021-12-07
> **sudodus said:**
> If you want Windows access, it should be OK with the old-style FAT32 file system (max file size 4 GB should be no problem with such files), or if you want a better file system, NTFS.

If you need only Linux access, you can use the ext4 file system.

You can [install and] use **gparted** to create a partition table if necessary, a partition and the file system you want in the partition.

Pardon the uninformed question, but if I buy a pendrive then do I need to always format it, unlike a regular USB stick?

---

### Post by tea for one on 2021-12-07
Pendrive = USB stick = Thumb dirve = Flash stick etc

They are all the same yet English has an excessive variety of descriptive phrases.

Generally, USB sticks are pre-formatted with FAT32 for Windows users.

Luckily (or by design), Linux users have the applications and knowledge to format our devices to a myriad of file systems.

Your device , your choice ;)

Have a play (carefully) with [COLOR="#0000FF"]gparte[/COLOR]d mentioned in post 19

---

### Post by bhubunt on 2021-12-07
> **tea for one said:**
> Pendrive = USB stick = Thumb dirve = Flash stick etc

They are all the same yet English has an excessive variety of descriptive phrases.

Generally, USB sticks are pre-formatted with FAT32 for Windows users.

Luckily (or by design), Linux users have the applications and knowledge to format our devices to a myriad of file systems.

Your device , your choice ;)

Have a play (carefully) with [COLOR=#0000FF]gparte[/COLOR]d mentioned in post 19

Thanks for the explantion about the synonyms for USB stick. Then I guess my next question is: is a [COLOR=#000000]USB SSD, like a Sandisk Cruzer Extreme any safer or sturdier than a regular USB stick?[/COLOR]

And what exactly is the purpose of gparted?

---

### Post by yancek on 2021-12-07
>  And what exactly is the purpose of gparted? 		 

It is a partition manager to create partition tables, partitions of various types and filesystems.  The link below is to the GParted manual.

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by sudodus on 2021-12-08
> **bhubunt said:**
> Thanks for the explantion about the synonyms for USB stick. Then I guess my next question is: is a [COLOR=#000000]USB SSD, like a Sandisk Cruzer Extreme any safer or sturdier than a regular USB stick?[/COLOR]


If I remember correctly, Sandisk Cruzer is a group of pendrives and Sandisk Extreme is another group of pendrives. I would not say that these are SSDs, but *maybe* some of the newest and most expensive Sandisk Extreme pendrives have the same kind of memory hardware as SSDs.

Edit: See [this link that is listing Sandisk's SSDs](https://kb.sandisk.com/app/ssd/a_id/23553)

---

### Post by bhubunt on 2021-12-08
> **sudodus said:**
> 

Edit: See [this link that is listing Sandisk's SSDs]("https://kb.sandisk.com/app/ssd/a_id/23553")

Thanks for the link. So I gather then that it is better not to use a USB stick but to buy a small Sandisk SSD.

---

### Post by bhubunt on 2021-12-08
> **yancek said:**
> It is a partition manager to create partition tables, partitions of various types and filesystems.  The link below is to the GParted manual.

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

Hi Yancek, Thanks so much for the info and the link. I must admit, though, that I am a newbie and don't understand what the purpose of partitioning is or why I would have to apply it. What does it have to do with security?

---

### Post by yancek on 2021-12-08
>  I am a newbie and don't understand what the purpose of partitioning is or why I would have to apply i 

A good reason to read the link to learn what it is and does.  For one thing, you could not install windows and Linux on the same computer without partitions,   I posted the link because you specifically asked what it was.

---

### Post by bhubunt on 2021-12-09
Hi Yancek,
Yes, thanks for the link but to a newbie like me the text on that link is too technical and jumps right into the problem, without explaining what partitioning is and what it does in non-technical language. 

By contrast, the comment you just made, that I need partitions, for example, to install windows and linux on the same computer, is totally clear and helps me understand the purpose of partitioning.

---

