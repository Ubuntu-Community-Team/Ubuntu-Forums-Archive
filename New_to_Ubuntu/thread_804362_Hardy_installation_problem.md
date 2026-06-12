---
title: "Hardy installation problem"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by sayakb on 2008-05-23
I downloaded 8.04 from ubuntu.com/get ubuntu
After booting to the CDROM and selecting language, I chose the 2nd option (To install ubuntu).. it loaded the kernel modules and the orange bar under the ubuntu logo started moving left and right. It was all fine until the bar became blank and started filling from left side. When it filled up, the screen went back to text mode to show "User not known to the underlying authentication module" about 10 times in a row. I rebooted to select "Try ubuntu without any change...", but after gdm showed, it asks me for username and password which I don't know. What to do? Is it because of the existing Gutsy lying on my HDD?

---

### Post by Skeet on 2008-05-23
Are you wanting to keep the Gutsy partition and install Hardy on a new partition or are you trying to install Hardy over Gutsy?

You might want to reinstall and select format checkbox in the Manual install mode on the LiveCD.

Not sure if it will help but if it is because of the Gutsy underneath Hardy, it could be causing conflicts.

Skeet

---

### Post by sayakb on 2008-05-23
No.. I would be removing Gutsy... So should I delete the existing partition before starting over with Hardy?

---

### Post by Skeet on 2008-05-23
You need to go into the Ubuntu installer. Go through the language selection and location selection screens, and when the Partition Editor pops up, select Manual Mode, and when your partitions pop up, select the partition with Gutsy on it and double click. A menu should pop up saying Use Partition As or something (off the top of my head). Select EXT3 or whatever file system you use. Check the Format box and put / as your mount point, click install and it should install okay.

Let me know if this helps.

---

### Post by ugm6hr on 2008-05-23
You do not need to delete Gutsy.

Did you check the Hardy CD for corruption?  There is an option at the boot menu.

This explains about md5 / 2X CD burn speed etc: [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Your LiveCD obviously doesn't work properly if it is loading GDM - the LiveCD auto-logs in as "ubuntu" (no sudo password)

---

### Post by Skeet on 2008-05-23
I must have misread, I thought it was installing fine, but wasn't booting. I didnt realise that the LiveCD wasn't booting up.

Sorry.

---

### Post by sayakb on 2008-05-23
"Checking integrity, this may take some time"
Checking the CD for defects.. I burnt it at 52x.. Anyway, is there any way to check whether the ISO is correct or not?

---

### Post by sayakb on 2008-05-23
It says:
Check finished: errors found in 1 files!
Press any key to reboot your system
 
What do I do? Burn it again on another disk at slower speed?

---

### Post by forestpixie on 2008-05-23
Yep - burn slower - check the md5 before you burn it

[http://releases.ubuntu.com/8.04/MD5SUMS](http://releases.ubuntu.com/8.04/MD5SUMS)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Dennis Beekman on 2008-05-23
When i burned my image at 52x the cd worked fine afterwards, but offcourse i have a good cd recorder aswell because i work for Plextor :lolflag:

I had the same problem however at a local school where i run edubuntu, the 8.04 version i was testing for implementation there refused to boot and also gave me a gdm screen (wich the live cd should not do offcourse).
I even used a original pressed cd wich i ordered of the website for free and it did the same.

The solution for me was to use another drive, the system was so old that the cd-drive was misreading the livecd, because the live system doesn't see a user/password file the system fails to boot or ask for a username/password wich doesn't excist (the database is empty since the file wasn't read)

Using a USB DVD-RAM drive i as able to boot and work the system just fine...

Maybe it is the actual cd in your case, but this is what i found to be the problem maybe it will help you aswell :lolflag:

---

### Post by sayakb on 2008-05-23
Gutsy live CD runs pretty well. And afterall, its a shining new Pioneer DVD-RAM drive.. just 3 months old :(

---

### Post by sayakb on 2008-05-23
I burnt it again at 4x (the slowest available). But I have the same problem. So what should I do now? How do I verify that the ISO is correct (please give exact directions since not much of an expert in this field)

---

### Post by ugm6hr on 2008-05-23
> **LinuxIsInnovation said:**
> What do I do? Burn it again on another disk at slower speed?

Check the link I gave earlier (or forestpixie's) re: MD5.

If there is a mismiatch of md5 - you may be able to correct it by using torrent rather than redownloading the whole thing again.  If you are using the 32-bit Ubuntu Hardy - the link is actually below.

And yes - burning slower, using better quality CD-R (and not RW) can make a difference.

---

### Post by sayakb on 2008-05-23
The MD5 sums are different. I am using 64-bit Hardy. Where and **how **can I fix this problem.
 
[ATTACH]71245[/ATTACH]

---

### Post by ugm6hr on 2008-05-23
> **LinuxIsInnovation said:**
> The MD5 sums are different. I am using 64-bit Hardy. Where and **how **can I fix this problem.

Options:
1. Redownload, and check MD5 before burning again!
2. Try and correct the iso file you have downloaded with this: [http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/8.04/ubuntu-8.04-desktop-amd64.iso.torrent)

In theory, you should be able to open that torrent file (assuming you have uTorrent, or something else similar), and select it to download to the same location that you have saved the corrupted iso.  BitTorrent should check the iso file, and correct the corrupted bits for you.  Once it says it is done - recheck MD5.  I have never done this - but it should work.

---

### Post by sayakb on 2008-05-23
Seems like the torrent method is working. Thanks you very much!! :D
I would post the response as the download is complete.

---

### Post by sayakb on 2008-05-23
Seems like it has been resolved. I'm burning the disk again at 4x now. Will scribble the final reply when installation would begin.
Thanks for the help
Regards 
Dave
 
[ATTACH]71251[/ATTACH]

---

### Post by ugm6hr on 2008-05-23
> **LinuxIsInnovation said:**
> Seems like it has been resolved.

I love being right :lolflag:

---

