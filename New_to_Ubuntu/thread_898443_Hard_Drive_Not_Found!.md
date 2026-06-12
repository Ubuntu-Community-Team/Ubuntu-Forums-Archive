---
title: "Hard Drive Not Found!"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by Darksci on 2008-08-23
Hi,

I tried the normal live cd and wasn't able to install it since when I did install it didn't detect a hard drive. Even though I have a dual boot Vista and XP system on that hard drive.

Then I tried the daily build DVD since I thought it qwould have the drivers to install it.

So far I tried DVD normal mode and DVD OEM mode and thus far no hard drive is found?

Oddly enough sound, USB, External DVD Drive, bluetooth and touch screen all work out of the box. WLAN and LAN don't but i can compile that on my own.

But not detectinmg Hard Drive? I can't even install ubuntu.

My system specs are:

Kohjinsha SC3

Intel CPU Z520 1.33Ghz
60GB HDD 
Built in Web Camera & Microphone
1024x600 7" Touch Screen Tablet
2GB RAM (DDR2-533)
GPS
Express Card 34 Slot
WLAN 802.11b/g
LAN
Bluetooth 2.0
3 in 1 Card Reader

FYI: Hard Drive is 1.8" Samsung Spinpoint N2 HS06THB  
ZIF Interface

If that helps at all?
Tried the same DVD with my 2.5" laptop and was fine.

---

### Post by Sef on 2008-08-23
Check to make sure your connections are tight.

---

### Post by Darksci on 2008-08-23
Connections?

Nothing is wrong hardware wise. Unless its uncompatablity.
Am currently on the same laptop, cept booted into Vista.

Some reason Ubuntu just doesn't see this Hard Drive and I don't know why?

EDIT: There is only one hard drive and that is currently dual boot into vista and xp. That is the one I want to wipe windows off and install ubuntu on.

---

### Post by bpowell2005 on 2008-08-23
You mentioned some external devices were also working? Maybe try disconnecting the External DVD and rebooting the live CD...perhaps the external drive is causing a conflict or confusing Ubuntu?

---

### Post by Darksci on 2008-08-23
Oh the problem is that i need to install the live cd via an external DVD drive. My new laptop is actually a UMPC which has no DVD drive in it.

---

### Post by egalvan on 2008-08-23
First, did you check the md5 sums on the downloaded ISO?

Or did you run the "check media" option from the liveCD boot screen?

Next:

Where exactly does the install process "not see a hard drive"?

Are you fully booting into a Live Session?

If so, then go to 

 Places

and see if the internal drive is listed

("Places" is on the top menu bar, next to "Applications")

If the drive is listed, then clicking it will mount it and open a file browser.

If this doesn't work, then others will have to chip in with help.

I installed the LiveCD onto PATA-type, and SATA-type drives, without problems. Laptop and desktop. Six installs for far...IBM, HP and Dell

Same LiveCD  8.04.1

:popcorn:

---

### Post by Darksci on 2008-08-23
> **egalvan said:**
> First, did you check the md5 sums on the downloaded ISO?

Or did you run the "check media" option from the liveCD boot screen?

Next:

Where exactly does the install process "not see a hard drive"?

Are you fully booting into a Live Session?

If so, then go to 

 Places

and see if the internal drive is listed

("Places" is on the top menu bar, next to "Applications")

If the drive is listed, then clicking it will mount it and open a file browser.

If this doesn't work, then others will have to chip in with help.

I installed the LiveCD onto PATA-type, and SATA-type drives, without problems. Laptop and desktop. Six installs for far...IBM, HP and Dell

Same LiveCD  8.04.1

:popcorn:

Checking integrity of live CD shows no problem.

I boot the live cd by pressing enter twice, once to select english language and second to tell i want to try out ubuntu.

I then enter Live CD Ubuntu, I click on places and no HDD shows up. Filesystem shows up but thats only the temporary files from the ubuntu CD.

Clicking on install I get:
1) English, forward
2) London, forward
3) Japan, Japan, forward
4) "Starting Partition" is displayed, but nothing shows up!


From my other laptop which uses a SATA 2.5" the partition of my HDD has always shown up. I think the ZIF interface of this 1.8" is ATA or something? I also heard its the type of HDD used in musicplayers 0.o

---

### Post by Darksci on 2008-08-23
So does anyone hav any info about this problem? Whether Ubuntu will support this kind of HDD?

---

### Post by thebigbluecan on 2008-08-23
I had the same problem with a desktop computer about 6 months ago. Windows worked fine on it (or so I thought) and Ubuntu couldn't find it. A week later the drive failed and died. It's possible you have a bad disk and don't know about it. To be on the safe side I would backup important stuff on the computer to cd or dvd's. Got another hard drive and put Ubuntu on it. Fine ever since.

Edit: I did have Ubuntu installed on it previously and it worked. so it wasn't compatibility issues I was having... It was just a bad drive.

---

### Post by Darksci on 2008-08-23
I hope its not a bad disk :S

This is a jap laptop from while i was over there ^^;

Was talking to the guy i got this from and he said he couldnt install ubuntu this type of machine since it didnt detect the HDD. So im assuming its a compatability issue.

Fingers crossed anyway. Hope thers some kind of fix for it ^^;

---

### Post by thebigbluecan on 2008-08-23
Does the drive show up in Partition editor on the Live cd? 
Or is this what you see when your trying to install?
[IMG]http://i210.photobucket.com/albums/bb5/thebigbluecan/Screenshot-2.png[/IMG]

---

### Post by Darksci on 2008-08-23
> **thebigbluecan said:**
> Does the drive show up in Partition editor on the Live cd? 
Or is this what you see when your trying to install?
[IMG]http://i210.photobucket.com/albums/bb5/thebigbluecan/Screenshot-2.png[/IMG]

Yep! Thats exactly what I see.

When did you hav  that problem 0.o?

---

### Post by thebigbluecan on 2008-08-23
> **Darksci said:**
> Yep! Thats exactly what I see.

When did you hav  that problem 0.o?

I guess 4 and a half months ago... It was with 7.10 not 8.04.

---

### Post by Darksci on 2008-08-23
Oh you had the problem with 7.10, but fixed at 8.04 ^^;

Maybe ill download 7.10 and see what results i get :O

---

### Post by thebigbluecan on 2008-08-23
> **Darksci said:**
> Oh you had the problem with 7.10, but fixed at 8.04 ^^;

Maybe ill download 7.10 and see what results i get :O

No it was a bad drive. Give it a try tho.

---

### Post by bumanie on 2008-08-24
As long as there is nothing wrong with the hard drive, a 'no disk found' often indicates that the partition table has been corrupted. It can usually be retrieved and re-written by testdisk. You can get a live cd version of testdisk from [here]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by Darksci on 2008-08-24
omg!

so ubuntu 7.10 detects my ZIF HDD but 8.04 doesn't...

I dunno what to think about this ^^;

---

### Post by Darksci on 2008-08-24
Well ok problem after problem...

So installed 7.10, then tried to boot into it.

Does absolutely nothing when I try all three ubuntu boots options. Even safe mode doesnt work.

Didnt think id ever see a laptop completely unable to use ubuntu 0.o

---

### Post by Steveire on 2008-08-29
> **bumanie said:**
> As long as there is nothing wrong with the hard drive, a 'no disk found' often indicates that the partition table has been corrupted. It can usually be retrieved and re-written by testdisk. You can get a live cd version of testdisk from [here]("http://www.cgsecurity.org/wiki/TestDisk")

Hi.

Can you post how to actually use testdisk? Here's my attempt:

[http://ubuntuforums.org/showthread.php?p=5689025#post5689025](http://ubuntuforums.org/showthread.php?p=5689025#post5689025)

---

