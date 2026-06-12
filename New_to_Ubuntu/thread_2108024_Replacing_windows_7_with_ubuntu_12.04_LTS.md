---
title: "Replacing windows 7 with ubuntu 12.04 LTS"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by Madarox on 2013-01-23
Hello.
ok so I'm sick of windows and I'm now moving to ubuntu.I want to completely replace windows with ubuntu(not dualboot).I'm downloading the ISO image now and I will burn it to a CD then boot from that CD.At the ''installation type'' window,if I choose ''replace windows 7 with ubuntu'' will that wipe windows from drive C and replace it with ubuntu ? And will I still have access to my files in other hard drive partitions(E,D,F) ? Sorry for the noobie questions but I need to make sure everything is right as I never installed any other OS than windows:)

---

### Post by Impavidus on 2013-01-23
No, it will wipe the entire disk. All partitions.

If you want to keep some data partitions you'll have to select "something else" and select manually which partitions you want to install Ubuntu on (they will be wiped) and which you want to keep. But still, it's best to have backups in case you hit the wrong key.

Furthermore, Ubuntu doesn't know about drive letters, so you'd better take a note on the order of the partitions on your disk and the sizes, so you know which one is the windows C partition.

Edit: And welcome to the Ubuntu forums.

---

### Post by arpanaut on 2013-01-23
Be careful about your data!  Best to back up on external media.

Windows designates partitions as "Drives" even though they may be on the same hard disc, so unless you have separate hard drives installed on your computer, then those "Drives" "disks" as seen in windows (E,D,F) are actually just partitions on one hard drive.

So if you choose to overwrite the windows installation, it WILL overwrite the entire hard drive, and you WILL lose all the data on there. So I would suggest backing up all important data to another hard drive or external media, then install Ubuntu over your unwanted Windows.

Study up and pay attention to what you are doing.

---

### Post by leclerc65 on 2013-01-23
Don't forget a Swap partition.

---

### Post by collisionystm on 2013-01-23
May I offer a suggestion? Don't bother with 12.04. For an LTS it has an incredible amount of bugs and issues with compiz.

Go with 12.10. It has the later kernel, compiz patches and better Xorg drivers.

If the only thing keeping you from 12.10 is the amazon search results, just disable them.

---

### Post by arpanaut on 2013-01-23
> **collisionystm said:**
> May I offer a suggestion? Don't bother with 12.04. For an LTS it has an incredible amount of bugs and issues with compiz.

Go with 12.10. It has the later kernel, compiz patches and better Xorg drivers.

If the only thing keeping you from 12.10 is the amazon search results, just disable them.
Interesting perspective!
Personally on my hardware I find the opposite to be true.
12.10 when I tested on my this laptop was incredibly buggy, but that was a couple of months ago, so maybe it has improved. Or it could just be hardware differences.

Different strokes for different folks...
I prefer the LTS 5 year support for this machine.

---

### Post by Madarox on 2013-01-23
Wow I was just going to lose 6 years of data,lol.Good thing I asked 1st.Unfortunately,I don't have any external drives to backup my data except for a 4gig usb drive that can't hold 1% of my data. A couple of months ago,I partitioned drive F into 2 drives as I was planning on dual booting ubuntu and windows.So if I chose "something else" and chosen to install ubuntu in that drive I won't lose my data?
> May I offer a suggestion? Don't bother with 12.04. For an LTS it has an incredible amount of bugs and issues with compiz.

Go with 12.10. It has the later kernel, compiz patches and better Xorg drivers.

If the only thing keeping you from 12.10 is the amazon search results, just disable them.
Thanks for your suggestion but I already downloaded 12.04 and don't wanna wait for download again(my internet is slow) but I will think about upgrading to 12.10 if I did feel comfortable with ubuntu :)

Edit: what if I dualboot? If this won't make me lose my data,I can do it.

Sent from my GT-I9300 using tapatalk 2

---

### Post by d4m1r on 2013-01-23
> **collisionystm said:**
> May I offer a suggestion? Don't bother with 12.04. For an LTS it has an incredible amount of bugs and issues with compiz.

Go with 12.10. It has the later kernel, compiz patches and better Xorg drivers.

If the only thing keeping you from 12.10 is the amazon search results, just disable them.

Huh? This is not true at all OP...If you want stability, aim for an LTS release like 12.04.

---

### Post by GordThompson on 2013-01-23
My two cents' worth:


re: clobbering Windows 7

If someone has a working, legal copy of Windows and they are not starved for disk space then IMO completely wiping out Windows to install Ubuntu is foolish. How many times do we see people asking for help here because their Ubuntu install didn't go quite right, or something else happened to trash their network connectivity, and the only way they can fix it is by downloading stuff via their Windows network connection.


re: 12.04 LTS vs. 12.10

In my personal experience I have found 12.04 LTS to be considerably less "quirky" than 12.10. Frankly, 12.10 felt more like Beta software to me....

---

### Post by Madarox on 2013-01-23
> **GordThompson said:**
> My two cents' worth:


re: clobbering Windows 7

If someone has a working, legal copy of Windows and they are not starved for disk space then IMO completely wiping out Windows to install Ubuntu is foolish. How many times do we see people asking for help here because their Ubuntu install didn't go quite right, or something else happened to trash their network connectivity, and the only way they can fix it is by downloading stuff via their Windows network connection.


re: 12.04 LTS vs. 12.10

In my personal experience I have found 12.04 LTS to be considerably less "quirky" than 12.10. Frankly, 12.10 felt more like Beta software to me....
I just realized that too,lol.

Well,it seems that 12.04 is generally accepted as a stable release so I will go with that.

---

### Post by oldfred on 2013-01-23
How did you create new partitions? If you used Windows did it convert from basic  to dynamic partitions? If so that is a big issue as dynamic partitions are Windows proprietary and do not work with Linux.

Post this & if SFS then you have dynamic:

sudo fdisk -lu

---

### Post by SuperFreak on 2013-01-23
Dynamic Disks can be converted to Basic using EaseUS which is free for the Home edition. This is Windows software and must be used within Windows. It can be done nondestructively without losing the data on the Dynamic Partition [httphttp://www.partition-tool.com/easeus-partition-manager/manual.htm]("httphttp://www.partition-tool.com/easeus-partition-manager/manual.htm"). However I wouldn't recommend using this until you have backed up your data and of course first found out if you have Dynamic disks

That said I think you are probably better off with a Dual boot until you realize any limitations Ubuntu might have that you still need Windows for.

---

### Post by Frogs Hair on 2013-01-23
> If someone has a working, legal copy of Windows and they are not starved for disk space then IMO completely wiping out Windows to install Ubuntu is foolish. How many times do we see people asking for help here because their Ubuntu install didn't go quite right, or something else happened to trash their network connectivity, and the only way they can fix it is by downloading stuff via their Windows network connection.


I agree completely and dual boot even though Windows disk if I need it . Preloaded Win 7 with a recovery partition can get messy when it comes to getting Windows back.

12.04 is the best choice for a long term installation but 12.10 runs like a dream on my hardware so user experience may vary. I install the latest release every six months but that's not for everyone especially in a work situation.

---

### Post by Madarox on 2013-01-23
Sorry but how do I know if the partition is dynamic?  I don't know what you mean by "post this" @oldfred.Sorry,I'm not too techie :roll::roll:

---

### Post by SuperFreak on 2013-01-23
Using the Command OldFred gave you would have to be in terminal in Ubuntu (which you can do from the CD you burned). You would boot to CD an select try Ubuntu rather than install and open the terminal and put Old Fred's command in.
However it might be easier to simply go into Control Panel (in Windows) and in the search bar type partitons and select the "Create and Format Patitions" option. Do not perform any actions just look at the table and it should show if any or all partitions are Basic or Dynamic

---

### Post by Madarox on 2013-01-23
Hey guys,guess what...I DID IT ! ! Apparently the disk isn't dynamic.I booted the ISO image from a usb stick,created a swap partition from the F partition I Created before then created the primary partition and I got ubuntu up and running(actually posting using it now).Loving it so far,it feels like android(makes sense lol).I didn't lose any data in the process btw and windows 7 is still there ready for boot(will only use it when I need really need to):p Can't believe it...NO MORE VIRUSES AND BLUE SCREENS !:guitar: Thanks for the support guys.

---

### Post by black veils on 2013-01-24
you should still find ways to backup at least the most important data, because a hard drive can fail at any time, or a fire/flood/theif could cause you loss, so backup! there are online services like **dropbox** or** ubuntu one** which allow free backup of data on the internet as yet another storage place (dropbox 2gb free).

---

### Post by Madarox on 2013-01-24
> **black veils said:**
> you should still find ways to backup at least the most important data, because a hard drive can fail at any time, or a fire/flood/theif could cause you loss, so backup! there are online services like **dropbox** or** ubuntu one** which allow free backup of data on the internet as yet another storage place (dropbox 2gb free).

I don't really have a lot of important data.Actually the only data that I think is important are my songs,videos and pics + a few ms office documents.The majority of the hard drive is full of games that I never play anymore.All of these are either on my phone,camera or flash drive so no worries:D

---

