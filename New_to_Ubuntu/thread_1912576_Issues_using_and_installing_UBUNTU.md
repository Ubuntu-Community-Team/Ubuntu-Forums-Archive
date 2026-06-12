---
title: "Issues using and installing UBUNTU"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by archangel2003 on 2012-01-20
Lets see.
It said to get the universal USB installer and put UBUNTU on it, then start from the flash drive.
I hit F-12 and tell it to boot from the flash drive, the flash drive light flashes once and Windows boots up.
Started over from scratch 2 more times with nothing new.

Funny that every step of the way they keep referring to a CD even when fallowing the steps intended for using a flash drive.:confused:

Then I try the CD boot, so I load it to a CD.
I restart, hit F-12, tell it to boot from the CD Drive.
Well it looks like it's booting, logo there, dots flashing back and forth, then after a long while, the caps lock button starts flashing.....FOREVER going no further, no UBUNTU, nothing but the start up logo.

All I want is to get one copy of the UBUNTU on the partition I put aside for it keeping the Windows 7 where it is!

---

### Post by Double.J on 2012-01-20
Hi there! sorry to hear you're having difficulties!

Don't give up - it really is worth the wait.. 
If you've had troubles both ways, it could be the downloaded image - best try redownloading.

for your USB stick try this

in windows go to computer, right click on the stick and then format. Choose format to fat32.

Then go to the usb installer and try again - select ubuntu 11.10, locate the 11.10 oneiric iso image, select the letter of the USB device and then create a persistence file if you'll need one (if you're just installing, you dont - that's just to save things if you run it off the stick like a normal OS). once it's all done use the safely remove hard drive feature.

For the cd - make sure that it burns the Iso image to the disk, not copies it to the disk (it should have folders such as "boot" and "casper" on the disk post burn. Also make sure you burn at the slowest speed possible.

Really hope it helps :)

---

### Post by Double.J on 2012-01-20
Oh I almost forgot - don't forget to check you've got everything backed up ;)


also if you've created a seperate partition for ubuntu in windows, I'd advise clicking "try" not "install" once you get the installer working. Once it loads, press the "windows" key on your keyboard and type "gparted" -without the quotes- and hit return - this partitioner will allow you to check that the partition you want to use is empty. I advice using this tool to delete the partition so you just have free space in the place you want ubuntu then clicking apply, closing and running the installer from the desktop icon - now you just have to choose "use free space" and there's no need to do any more partitioning :)

---

### Post by archangel2003 on 2012-01-20
I'll give it a try.
My daughter set up my last laptop with a flash drive (10.04) and as for surfing the web it seems bullet proof!

I never even used the Windows partition on that one!

I would have preferred to just copy what I had, with the way it was set up, and install it on this one, but my "kom-pu-tor" skills are lacking.:D

Now I need to take with me several CADD programs that require Windows, so I am stuck.

---

### Post by archangel2003 on 2012-01-20
Questions. I have a Toshiba **(LAPTOP) **Satellite P775 with the i7-2670QM 64 bit system and 6 GIG's of ram.
The program I'm attempting to use says it's
[B]
UBUNTU 10.04.3-desktop-amd64[/B]
[B]
They are all desktop I assume?[/B]
**UBUNTU 10.??**** is the one I have on my other laptop but in the 32 bit format and I like it the way it is.**

But the installer had **(the first one was the one I was using and also burned again to my last unused disc)**

UBUNTU 10.04-desktop
 
UBUNTU 10.04.X-desktop

UBUNTU SERVER 10.04.X-desktop-amd64-Istaller (this is the one I am going to try tonight)

So, they all are missing the .3 and the first two are missing the AMD64
the second has an additional X
and the third has the amd64 but says server and installer

This is the one I am going to install on the flash drive tonight UBUNTU SERVER 10.04.X-desktop-amd64-Istaller.

Can you clarify what I should try to install?

---

### Post by archangel2003 on 2012-01-21
Well, I found the windows installer and I can got it to work with no disc or flash drive needed.
It seems limited to 30 GIG even though I allocated 100 GIG on that partition, and there was no option to go with the 10 version, only the 11 version.

It's loading right now.

Assuming my "KOM-PU-TOR" survives, I'll post my result.

---

### Post by archangel2003 on 2012-01-21
Well, windows is still there and there is an UBUNTU, the wrong version, but at least a version of UBUNTU none the less.

Is there any way to get my Firefox passwords to transfer over in a file like the bookmarks do?

It's such a PITA as I now have to take screen shots to save them for my records.

---

### Post by mastablasta on 2012-01-21
i think you installed it in Wubi which is creates virtual file inside windows. Thi sis ment only for trying and not for serious use. 

Ubuntu server uses command line interface. you should go with 64 bit (amd64) desktop verison. as fo rhwich one you can go with latest or the stable version. i would go with latest sicne oyu have new hardware.

instead of USB creator there are also a couple of other easy to use programmes that make a live USB such as unetbootin and linuxliveUSB. i liek the last one since it has a nice interface, but unetbootin is also good.

once you donwload the image you need to check if it has all the bit s and make sure that nothing got lost during transmission ( a small missing packet can make a huge difference when we are talking about OS). the easiest way to make sure you get exactly the same file is to use torrents (as they check for consistency during the time the file is shared). if you use normal download here is how you check the file: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

oh and guide to install dual partition: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
and the latest Ubutnu desktop guide: [https://help.ubuntu.com/11.10/ubuntu-help/index.html](https://help.ubuntu.com/11.10/ubuntu-help/index.html)

for the older version (10.04 LTS) see my signature.

hope this helps.

---

### Post by varunendra on 2012-01-22
> **archangel2003 said:**
> Is there any way to get my Firefox passwords to transfer over in a file like the bookmarks do?
Try copying these files over to the firefox profile folder in your new computer:
For older versions of firefox:

[LIST=1]
[*]key3.db
[*]signons.txt
[*]signons2.txt
[/LIST]
 For newer versions:

[LIST=1]
[*]key3.db
[*]signons.sqlite
[/LIST]
(I'm not sure how it would behave if you copy the three files from an older version to a newer version'r profile folder. Probably updating - then transferring would be required)




 > **archangel2003 said:**
> It's such a PITA as I now have to take screen shots to save them for my records.
What kind of records? Maybe we could suggest a better way if we knew your objective.


**_PS_:**
As a side note, given how modern your new laptop's hardware is, I would recommend to install 11.10 64bit on it (and use torrent to download its iso, as *mastablasta* suggested).

With 10.04, you may experience graphics problems with Intel HD graphics embedded in the sandy bridge processor (which the lappy has), and even if you manage to use backported kernel/drivers from newer releases, they may not be stable with 10.04 (my personal experience of last two days).

---

