---
title: "What can and can't be done???"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by linuxrus1 on 2008-07-29
Apparently my computer is acting with dual personality.
I'm not sure what technology is available today compared to what
was claimed in the movie "Enemy of the State."

I have seen my USB drive indicate less disk space than it really has.
And none of my optical drives seem to write data.
I am running on Live CD with no hard drives connected.

It appears if I try to boot Ubuntu with my ethernet cable tethered,
sometimes the boot fails. So now I only boot without the ethernet cable connected.

Is it possible that my motherboard could have been switched out with a hacked up one which can be remotely controlled?

---

### Post by Joeb454 on 2008-07-29
No, not at all :)

You need software to be able to do that, and if you're running without a Hard Drive, that would be incredibly hard to do.

---

### Post by Het Irv on 2008-07-29
Okay, For the USB drive, how much less?

Not sure about the optical drives, but how does the boot fail with ethernet.

I highly doubt that your motherboard was replaced.

---

### Post by Bachstelze on 2008-07-29
linuxrus? Hmm, I think this might be related to your lost bukkit problum.

---

### Post by linuxrus1 on 2008-07-29
A sidebar theory, which I hope is not a possibility.

Based on info released to public so far, our phone records are in the hands of people who are trying to protect us from a war without an enemy that we know of, in advance, anyway.

What's troubling is that peoples phone records are all located in a common reserve where a computer program can do what ever with it.

Theoretically everyone is six degrees of separation from everyone else socially.

With access to ubiquitous amounts of phone records, in theory a map of social relationships can be developed, where everyone who knows someone knows someone and so on.

Lets say someone who is inside Ubuntu development is being sought after by someone who needs that person's expertise.

Theoretically that person can be reached through a chain of social influences. 

Now the thing that I'm hoping is not happening is can someone very knowledgeable in Ubuntu linux make a person's computer like mine become remotely controllable, assuming in theory?

---

### Post by Joeb454 on 2008-07-29
> **HymnToLife said:**
> linuxrus? Hmm, I think this might be related to your lost bukkit problum.

For reference, here's a collection of Lolrus pictures: [http://icanhascheezburger.com/category/lolrus/](http://icanhascheezburger.com/category/lolrus/)

---

### Post by Het Irv on 2008-07-29
What type of tin foil are you using for your hat?

Dude, I seriously doubt you are being "remotely controlled".  If you don't want to get help, don't post.

---

### Post by linuxrus1 on 2008-07-29
The USB drive has 1Gig from factory.
I put about 100 meg of data on it.

Yesterday when I tried downloading the Ubuntu iso image
the download kept failing because I did not have enough space.

So I figured that I try using the USB drive for storage.

I checked the USB drive properties and the available space was less than 400 meg. I realized here something didn't add up.

The Ubuntu iso image download failed multiple times at around 300 meg.
Furthermore I can't seem to specify the USB drive for save to disk.


I guess there can be an answer for everything.
 
But I have some reservations about the negative reflections on my postings already.
 I am looking for information here.

---

### Post by Frenske on 2008-07-29
> **linuxrus1 said:**
> I have seen my USB drive indicate less disk space than it really has.

Often this is more related to false advertisement of the producer. One gigabyte should be 1024x1024x1024 = 1073741824 bytes, but producers are telling us that is 1.07GB. So according the strange reasoning of the advertisement department my 80GB portable HDD is actually 74.5GB according the computer system. :mad:

---

### Post by Separ on 2008-07-29
Can you post the output of
```
sudo fdisk -l
```

(With the USB drive in)

---

### Post by Het Irv on 2008-07-29
> **linuxrus1 said:**
> The USB drive has 1Gig from factory.
I put about 100 meg of data on it.

Yesterday when I tried downloading the Ubuntu iso image
the download kept failing because I did not have enough space.

So I figured that I try using the USB drive for storage.

I checked the USB drive properties and the available space was less than 400 meg. I realized here something didn't add up.

The Ubuntu iso image download failed multiple times at around 300 meg.
Furthermore I can't seem to specify the USB drive for save to disk.


I guess there can be an answer for everything.
 
But I have some reservations about the negative reflections on my postings already.
 I am looking for information here.

Can't you browse the files on the USB to see what is on there?

---

### Post by halitech on 2008-07-29
in a terminal, if you do ```
df -h
``` it should show you the main folders and how much are used and how much is available. One thing I learned is that if you delete something on a flash drive, it gets moved to the trash on the device so you may need to use Nautilus and enable viewing all files and delete the files from the .trash folder (if any are there)

---

### Post by linuxrus1 on 2008-07-29
ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ sudo fdisk -l


Not sure what this is for but I got nothing showing.

---

### Post by halitech on 2008-07-29
> **Separ said:**
> Can you post the output of
```
sudo fdisk -l
```

(With the USB drive in)

wont that just give the size and partitions on the drive?

---

### Post by halitech on 2008-07-29
> **linuxrus1 said:**
> ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ sudo fdisk -l


Not sure what this is for but I got nothing showing.

are you using an L (lowercase) or the number 1?

---

### Post by linuxrus1 on 2008-07-29
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
unionfs               1.2G  663M  476M  59% /
varrun                506M   80K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M   88K   10M   1% /proc/bus/usb
udev                   10M   88K   10M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M  7.6M  499M   2% /lib/modules/2.6.17-10-generic/volatile
tmpfs                 506M  124K  506M   1% /tmp
ubuntu@ubuntu:~$

---

### Post by linuxrus1 on 2008-07-29
I copied and pasted from your post.

ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$

---

### Post by linuxrus1 on 2008-07-29
Do you need my USB drive info?
I have not plugged that in right now.

---

### Post by halitech on 2008-07-29
> **linuxrus1 said:**
> Do you need my USB drive info?
I have not plugged that in right now.

yes, plug in the usb drive and do the dh-f again

here is a copy of mine
```

daryl@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              56G   11G   42G  20% /
varrun                443M  256K  442M   1% /var/run
varlock               443M     0  443M   0% /var/lock
procbususb            443M  104K  443M   1% /proc/bus/usb
udev                  443M  104K  443M   1% /dev
devshm                443M     0  443M   0% /dev/shm
lrm                   443M   34M  409M   8% /lib/modules/2.6.22-15-generic/volatile
/dev/sda1             228M   42M  175M  20% /boot
/dev/sda4              89G   45G   40G  54% /home
/dev/sdc1             190G   65G  126G  35% /media/New Volume
[color=red]/dev/sdb              940M  205M  736M  22% /media/DARYL[/color]
daryl@ubuntu:~$ 

```

---

### Post by Darkade on 2008-07-29
>Your USB is probably bad partitioned
>Is completely normal to boot Live CD w/o a hard drive
>You probably have enabled Network boot, and that's why if you have your ethernet cable connected you cant boot
>Your optical drivers not writing... humm... what software are you using?

---

### Post by linuxrus1 on 2008-07-29
By the way I have another computer which I have placed a lock on since purchase. And the optical drives seem to work there, along with the USB drive showing more closely the available disk space. I pretty much use Ubuntu Live CD without a hard drive.

---

### Post by halitech on 2008-07-29
is that other system windows?

---

### Post by linuxrus1 on 2008-07-29
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
unionfs               1.2G  664M  475M  59% /
varrun                506M   80K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  100K   10M   1% /proc/bus/usb
udev                   10M  100K   10M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M  7.6M  499M   2% /lib/modules/2.6.17-10-generic/volatile
tmpfs                 506M  124K  506M   1% /tmp
/dev/sda1             954M  525M  430M  55% /media/KINGSTON
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000 MB, 1000341504 bytes
16 heads, 32 sectors/track, 3816 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3816      976880    e  W95 FAT16 (LBA)

---

### Post by linuxrus1 on 2008-07-29
My other computer is a Vista packaged PC which I disconnected the hard drive.

I boot with Ubuntu on it. And I have not yet connected to the internet with it.

By the way I use Ubuntu 6.10 and the video, lan and sound drivers don't work with this PC. It seems Asus, Nvidia, and ALC has a deal with microsoft to not allow drivers to be downloaded for linux users.

Asus M2N68-LA

GeForce 6150SE nForce 430

ALC 888 chipset

---

### Post by halitech on 2008-07-29
ok, so it is being seen as a 1gig drive but after formatting it brings it down to 954 and you have used 525 meg of the available space

---

### Post by halitech on 2008-07-29
> **linuxrus1 said:**
> My other computer is a Vista packaged PC which I disconnected the hard drive.

I boot with Ubuntu on it. And I have not yet connected to the internet with it.

By the way I use Ubuntu 6.10 and the video, lan and sound drivers don't work with this PC. It seems Asus, Nvidia, and ALC has a deal with microsoft to not allow drivers to be downloaded for linux users.

Asus M2N68-LA

GeForce 6150SE nForce 430

ALC 888 chipset

you may want to consider updating to 7.10 or 8.04 as they will have better support then 6.10 does as it is an older (almost to the non supported state by Canocal) which hopefully will allow you to get all those devices working.

far as your video card, Nvidia has always been the card of choice for linux users as it has always been supportive of open source.

---

### Post by linuxrus1 on 2008-07-29
According to data on my USB drive I have 62.8 meg of files.
On a 1 Gig drive I would expect a little bit more free space.
I checked on my other computer as well and now the free space is the same at 430 meg.

Something still does not add up.

Did someone put data on my USB that I can't see?

---

### Post by linuxrus1 on 2008-07-29
I appreciate your recommendation to upgrade to newer version.
But I can't seem to get the download to work.
I have submitted a request for a free CD.

---

### Post by linuxrus1 on 2008-07-29
Name: KINGSTON

Type: folder

Contents: 87 items, totaling 62.9 MB

Location: on the desktop

Volume: KINGSTON

Free space: 429.2 MB

Modified: Thu Jan 1970 12:00:00 AM UTC



Interestingly my other computer had 62.8 MB.

---

### Post by halitech on 2008-07-29
> **linuxrus1 said:**
> According to data on my USB drive I have 62.8 meg of files.
On a 1 Gig drive I would expect a little bit more free space.
I checked on my other computer as well and now the free space is the same at 430 meg.

Something still does not add up.

Did someone put data on my USB that I can't see?

open the drive with Nautilus and press ```
CTRL H
```that will show you the hidden files. look for a folder called .Trash (the . is important) and see if you have files in there. If you do, they are hidden and thats why they don't show up and make it look like only 62.8meg is used. Depending on the ownership of the files, you may be able to delete them from there (press down the shift key and it will delete them completely). If not, you will need to open Nautilus as sudo

```
gksu nautilus
``` 
and then you can delete them

---

### Post by linuxrus1 on 2008-07-29
I found .Trash-ubuntu folder with a couple of files.

I removed them via rm -r .Trash-ubuntu.

I still have a lot of missing free space.

I can't find any hidden files.

I do remember copying the partial download of the Ubuntu iso file on to the USB drive, but I had deleted that file.

---

### Post by halitech on 2008-07-29
what does dh -f give you for a reading now?

---

### Post by linuxrus1 on 2008-07-29
I tried to eject the USB drive from my other PC and now I get an error.

Unable to eject media.

Additional message state something like /media/KINGSTON device is busy.

---

### Post by linuxrus1 on 2008-07-29
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
unionfs               1.2G  667M  472M  59% /
varrun                506M   80K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  100K   10M   1% /proc/bus/usb
udev                   10M  100K   10M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M  7.6M  499M   2% /lib/modules/2.6.17-10-generic/volatile
tmpfs                 506M  124K  506M   1% /tmp
/dev/sda1             954M  525M  430M  55% /media/KINGSTON


I realized with a terminal open to the /media/KINGSTON folder that 
the USB drive is busy and I can not eject.

---

### Post by linuxrus1 on 2008-07-29
As for the USB drive mysterious free space loss,
I just decided to remove the visible files off the USB drive and then
reformat the USB drive and then reinsert the visible files back onto the USB drive. I think the formatting got rid of the unkown or missing free space.

---

### Post by halitech on 2008-07-29
it may have been corrupted files that for wahtever reason were not showing. So you've done the format and everything is fine now?

---

### Post by linuxrus1 on 2008-07-29
Yes.

Thank you.

I have to figure out how to points to people who help me.

---

### Post by halitech on 2008-07-29
very welcome :)

points? not sure what you mean. If you want to thank them, you can click on the little star below one of their posts

---

### Post by Het Irv on 2008-07-30
> **linuxrus1 said:**
> Yes.

Thank you.

I have to figure out how to points to people who help me.

Please also mark your thread as solved so that others can benifit from this thread.

---

