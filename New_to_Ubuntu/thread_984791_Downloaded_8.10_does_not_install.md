---
title: "Downloaded 8.10 does not install"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by tobias21 on 2008-11-17
Hi:

I downloaded and burned ubuntu-8.10-desktop-i386.iso from a bittorrent site: [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/) at an awesome speed of 212kbps. But now it does not boot.

Everytime I open it with konquror, k3b launches and does a checksum. But after that i cannot launch it.

Incidentally:

When i was downloading the torrent I noticed simultaneously another download was taking place to my desktop but at a woefully slow speed of 8kbps. I promptly deleted it. Did I do something wrong?

:)

---

### Post by bennachie on 2008-11-17
Can you boot directly from the CD you have burned? It should be a LiveCD, so that you can check out the new OS without commitment. There will be a link to the installer on the desktop.

---

### Post by tobias21 on 2008-11-17
No it does not:

I downloaded and burned ubuntu-8.10-desktop-i386.iso from a bittorrent site: [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/) at an awesome speed of 212kbps. But now it does not boot.

Also:

Incidentally:

When i was downloading the torrent I noticed simultaneously another download was taking place to my desktop but at a woefully slow speed of 8kbps. I promptly deleted it. Did I do something wrong?

---

### Post by bennachie on 2008-11-17
That was quick! I assume that you tested it by restarting your system with the burned disk in the reader - that should normally lead to the machine attempting to boot from the CD. If it does not find a bootable CD, it reverts to the hard disk. I think that there must be something wrong with your downloaded image, but don't know enough about BitTorrent to say whether your action in stopping a process caused that - sounds suspicious, though.

---

### Post by tobias21 on 2008-11-17
Yep that's right. 

You mentioned an installer on the desktop. Was this the simultaneous download that i deleted. But if this is the case why in Gods name was it the same file size as the ISO - 698.XX MB with the same file name. After burnibg the k3b tool said somethging about exceeded capacity. i don't remeber howmuch. My RW CD is 700 MB also

---

### Post by tobias21 on 2008-11-17
any one know how to get my cd to work?

thanks

---

### Post by bennachie on 2008-11-17
No, the installer link on the desktop is a normal part of the LiveCD version of Ubuntu. I'm sorry, but I think that your best strategy would be to download another iso from one of the standard Ubuntu mirrors, burn a CD, and start again.

If you want to cross-check, and you have a working Windows XP or Vista system on your computer, you could fire that up, then insert the CD that you already have. That should result in your being offered the option to install Ubuntu "within Windows" (the work is actually done by a programme called Wubi). 

The arrangement works well, and, despite its having some modest impact on hard disk performance, may actually be preferable for some users to installing Ubuntu on a separate partition (on subsequent restarts, you will be offered the option of booting into either OS and, when booted into Windows, can easily uninstall Ubuntu using the standard Windows methods).

---

### Post by cariboo on 2008-11-17
Did you check the md5 hash to see if they matched, and then run the disk integrity check that is available from theinstall menu?

Jim

---

### Post by Rucas on 2008-11-17
It Could also be that your CD Drive is not set to read at start up, thus the computer will automatically boot into windows and ignore the CD.
When the Start up menu comes up, usually it shows some F key commands to get into your Bios set up and such. There you can very *easelly* (depending on how much you know about Bios and such, but if you can read English then you can find your way around* choose the order in wich the computer does the start up, by going to HDD 1st, CD/ROM, etc... Make CD 1st bootable device.
Hope this helps a bit...

---

### Post by redseventyseven on 2008-11-17
Regarding the "other file" which you deleted: I can't imagine that has anything to do with the problem.

There are a few things that could have gone wrong here (which are more common problems):

1. First thing to check - did you burn the CD properly? The .iso file is a "snapshot" of all the files and folders that belong on the disk. Check the contents of the CD you just burned. If it just contains one file with a .iso extension, then it hasn't been burned properly -- you need to burn the cd so that the files and folders contained within the snapshot get burned to the CD, not the .iso file itself. If however your CD contains several folders and files (e.g. "isolinux", "preseed" amongst others) then it's been burned correctly.

2. Check the md5sums and make sure they match the one provided on the Ubuntu website. If they don't, then there's a good chance that your download was corrupt and you'll have to download it again.

3. Check your BIOS settings to make sure that your system is looking at the CD-ROM drive before looking at the hard-disk when it starts up. Rucas's post will point you in the right direction.

Good luck!

---

### Post by tobias21 on 2008-11-18
bios is ok. in fact dvd drive is first bootable disk followed by hard disk. 

curios thing: Everytime I try opening the cd to check its contents, k3b launches and does a checksum. And thats all - i cannot open the cd..

By the way whats the command to checksum in terminal?

---

### Post by Elfy on 2008-11-18
Assuming that the file is on the desktop

```
cd Desktop
md5sum nameoffile.iso
```

You can use autocomplete rather than type whole name - type the first few characters and tab will get the rest for you.

The md5sums are here
[http://releases.ubuntu.com/8.10/MD5SUMS](http://releases.ubuntu.com/8.10/MD5SUMS)

It could be that the file you deleted wasa part of the download - when it is downloading there would be a temporary file - that would go once it was completely downloaded - but check the md5sum.

---

### Post by tarps87 on 2008-11-18
It sounds like you have copied the iso to the CD rather than burn the image. Once you have checked the check sum try 'blanking' the CD-RW and burning the iso again. As you are using k3b this should also create the check sum before it burns to the CD

---

