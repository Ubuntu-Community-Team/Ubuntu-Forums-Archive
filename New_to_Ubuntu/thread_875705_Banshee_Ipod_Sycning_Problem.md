---
title: "Banshee Ipod Sycning Problem"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by samlockart on 2008-07-31
Hello, my first post here!
I have switched from XP to Ubuntu and I am loving it, just a few things I need sorted out, one of them is my Ipod Nano 3g Black.

After hours of confusion because of Banshee being extremely outdated in the default respiratory for some reason, I downloaded the source and compiled it (my first compile too!). I added all of my music and a few videos, also subscribed to a podcast. But when I tried syncing the iPod all hell broke loose. It seems I can sync a small portion of my library and it can be read on my ipod, but album art goes distorted or just shows up as a black box. If I try sync the whole lot of my music, it says it's all synced, so I eject it and find it to have 0 Music and 0 Videos and 0 Podcasts, so I'm guessing it has corrupted the itunesdatabase file. What do I do!?

Also how do I get video and podcasts synced up?

This is quite urgent, so any help would be great, thanks for your time, Sam.

---

### Post by nothingspecial on 2008-07-31
> **samlockart said:**
> 

This is quite urgent, so any help would be great, thanks for your time, Sam.

Use gtkpod to drag and drop the missing files on to your ipod.

I too have not found anything (banshee, gtkpod, rhythmbox, amarok, songbird) that will load my entire collection and sync it with my ipod easily,

---

### Post by samlockart on 2008-07-31
Ok, I did the same with GTKpod, same problem as above with the no music thing.

Sam.

---

### Post by nothingspecial on 2008-07-31
Are your tunes in apple`s m4a format?
Are you using plain old gtkpod or gtkpod-aac?

---

### Post by samlockart on 2008-07-31
Ok, well I was running GTKpod, just downloaded -aac now. Most of my library is .MP3, but some are .M4A

---

### Post by cozmicharlie on 2008-07-31
A couple items to check along with the suggestions from nothingspecial.

For Gtkpod
[LIST=1]
[*]Make sure you set the mount point in gtkpod correctly
[*]Make sure you select the correct model number on the first line of the file Ipod_control/Device/Sysinfo.
[*]Add your music by dragging to the local window
[*]Click save changes
[*]Importantly, update the Ipods database
[*]Make sure and wait until the actions are complete on the ipod before yu disconnect.
[/LIST]

Banshee
[LIST=1]
[*]Again, make sure you have the correct mount point and model selected.
[*]Move the music files into ipod (drag tracks from the library)
[*]To copy the files and update the ipods database, right click on the ipods name in the left hand pane and select synchronize ipod and Save Manual Changes to copy over the files you dropped in the device.  
[*]Again, make sure you don't disconnect before the actions are all complete.
[/LIST]
As per the video - this is a good source of info for your ipod and should help [https://help.ubuntu.com/community/PortableDevices/iPod?action=show&redirect=IPodHowto](https://help.ubuntu.com/community/PortableDevices/iPod?action=show&redirect=IPodHowto).  

Do post back though if you are still having problems.

Enjoy

---

### Post by cozmicharlie on 2008-07-31
Also, make sure you have podsleuth installed (available in Synaptic).

---

### Post by nothingspecial on 2008-07-31
> **cozmicharlie said:**
> Also, make sure you have podsleuth installed (available in Synaptic).

I can`t find it. What does it do?

---

### Post by cozmicharlie on 2008-07-31
> **nothingspecial said:**
> I can`t find it. What does it do?

It is in the Universe repository - make sure it is enabled in Synaptic.  It helps Banshee communicate with the ipod.

---

### Post by samlockart on 2008-07-31
Ok, all my settings are fine than. I synced a few and the album art is working, but still if I sync the whole lot at once, it corrupts the file. What would cause that? (in banshee)

Sam.

---

### Post by nothingspecial on 2008-07-31
> **cozmicharlie said:**
> It is in the Universe repository - make sure it is enabled in Synaptic.  It helps Banshee communicate with the ipod.

I`ve got universe enabled, is it because I`m still on Gutsy?

---

### Post by cozmicharlie on 2008-07-31
> **nothingspecial said:**
> I`ve got universe enabled, is it because I`m still on Gutsy?

Might be - I am in Hardy.  You could try a search on the forums and see if there is a method for installing it from source or maybe a deb is available.

---

### Post by cozmicharlie on 2008-07-31
> **samlockart said:**
> Ok, all my settings are fine than. I synced a few and the album art is working, but still if I sync the whole lot at once, it corrupts the file. What would cause that? (in banshee)

Sam.

Glad it is at least working.  It could be a bug in Banshee.  To me it still seems that their are a lot of bugs in Banshee related to iopds.  You could try browsing the Banshee forums and see if their are any posts on their forum that might suggest it is a bug.

How does it work in gtkpod? I find gtkpod very reliable.

Also, FYI, there is a new Amarok coming out ([http://lifehacker.com/399160/an-early-look-at-amarok-2](http://lifehacker.com/399160/an-early-look-at-amarok-2)).  It's still in alpha but it should have better ipod support (hopefully).

---

### Post by nothingspecial on 2008-07-31
> **samlockart said:**
> Ok, all my settings are fine than. I synced a few and the album art is working, but still if I sync the whole lot at once, it corrupts the file. What would cause that? (in banshee)

Sam.

Sorry, hijacked your thread for a bit.
To transfer all your music using gtkpod, just drag your music folder (wherever it is on your system) into the thing that says sam`s ipod (or whatever you have called it) in the left hand column. Click save changes and that`s it.

---

### Post by samlockart on 2008-07-31
Ok, I'm first going to try uploading chunk by chunk to my iPod using banshee and if that doesn't work, GTKpod-aac it is.

BTW. Is it normal for some album art to be a little distorted and placed on wrong albums in Banshee?

Sam.

---

### Post by cozmicharlie on 2008-07-31
> **samlockart said:**
> Ok, I'm first going to try uploading chunk by chunk to my iPod using banshee and if that doesn't work, GTKpod-aac it is.

BTW. Is it normal for some album art to be a little distorted and placed on wrong albums in Banshee?

Sam.

Not sure if that is normal but like I said, I think Banshee is still fairly buggy when it comes to ipod support.

---

### Post by samlockart on 2008-08-01
Ok, I am using itunes through virtualbox so I can sync perfectly now. But I did do a complete sync on an older iPod mini and found it syncs 100% with Banshee. Time will solve the bugs with the new models.

---

### Post by thundercles on 2008-09-16
> **samlockart said:**
> If I try sync the whole lot of my music, it says it's all synced, so I eject it and find it to have 0 Music and 0 Videos and 0 Podcasts, so I'm guessing it has corrupted the itunesdatabase file. What do I do!?

Also how do I get video and podcasts synced up?

This is quite urgent, so any help would be great, thanks for your time, Sam.

Go to someone's house running windows XP and use their Itunes to restore your ipod, I beat my head against the wall for a while trying to save a already f'ed off itunes database that gtkpod or banshee screwed up. They both use libgpod to write to the ipod so it doesn't matter which one you use, the solution should be the same. Now once you've restored the ipod, the FIRST thing you do is take it back home and plug it in to your linux computer, when gnome or kde try and automatically launch something when you plug in the ipod, tell it not to and go straightaway into a terminal. type in 
```
sudo ipod-read-sysinfo-extended <device> <mount>
```
where <device> is a full path to your ipod in the /dev directory, and <mount> is a full path to the mount point, so for instance when I did this I typed in:
```
sudo ipod-read-sysinfo-extended /dev/hdd1 /media/#1\ Stunna
```

This will generate the extended system info for your ipod, open up your ipod in nautilus/konqueror and go to the folder iPod_Control/Device and open up SysInfo with gedit or kedit. it should have a second line which says FirewireGUID: <#> where the <#> is a 12 or so digit number. If that is there, you should be able to use gtkpod or banshee fine. This solution is tested and works with
ipod nano 4g (silver) 3rd gen. - firmware 1.1.3PC 
Fedora Core 9 (yeah, it shouldn't make a difference in this case at all, this isn't a ubuntu-specific issue, it's a libgpod specific issue)
libgpod 0.6.0 (Must be version 0.6 or greater for this to work)
gtkpod 0.99.12
iTunes 8 -
I plugged the iPod back into iTunes 8 on XP to get two songs and two games I bought off iTunes with a gift card and iTunes credit from ticketmaster stuck the crap on there, plugged it back into my linux box and gtkpod whined about the checksums being off but I put another song on the iPod from gtkpod and ejected it and now both songs from iTunes8 and gtkpod show up, although I used the manual way to add songs, you'll have to test out whether or not syncing in itunes will screw things up on your own. One last interesting note is that gtkpod and itunes8 had different albumn covers for Unk - Beatin Down the Block, which was my test albumn, and itunes stuck its new cover on my old cover for the Unk albumn even though I didn't ask it to do anything to the UNK albumn, I was adding an E40 albumn in itunes, so be careful plugging your ipod back into itunes, it will replace your albumn covers if it doesn't think they are right! -

Probably works with, but not sure:
Banshee 1.2.1
-Banshee can't deal with itunes8 formatted ipods and is wanting to redo the database, I'm not tempting fate quite yet but feel free to try it yourselves and report back, they both use libgpod to my knowledge and both caused the same problem before I did the fix right.

Closing notes-
The issue is due to Apple trying to force everyone to use iTunes who has an Ipod, where they went wrong is not releasing a version for linux so the excellent developers at libgpod managed to figure out how to replicate the checksum that is required in the ipod's database for it to work, without that checksum the ipod knows it's been "tampered with" and CHOOSES not to work right thanks to Apple's nazi-ism. What is needed to make it work right is that "FirewireGUID:" line to be correct. It would not write my FirewireGUID: line with the tool I mentioned at the beginning AFTER you let a program screw up the ipod but works fine on a freshly restored one. Now correctly adding the FirewireGUID: line manually may work after the ipod gets screwed up, but I doubt it, didn't work for me although I didn't enter the line in the file correctly either. I suggest just restoring the ipod personally.
Lastly this guide is ONLY for the third generation ipod nanos (the first ipod nanos with video capability) and apperently it is also a fix for iPod Classics too, but I don't have one, so I can't say I personally had the issue with one and fixed the issue this way.

---

### Post by betterhands on 2009-02-03
i've had similar trouble as well.  

Windows system died, installed ubuntu.  read that Banshee would be a good app to manage my ipod (5th gen)

The ipod had 3600 songs.  created a Banshee music library from it.  

added an album to the banshee library, attempted to sync the ipod, now the ipod reads as if it's completely empty.  

scared the crap out of me--the above post sounds helpful, except i have no f'in windows machine at home.  not sure what to do.  hate to think banshee just wiped everything out.

i have the content on the intrepid system, now just an empty ipod (says it's syncing, takes 30 minutes, then still reads it's empty).  hope i can get it to go without an xp system handy.

---

### Post by betterhands on 2009-02-03
been reading a ton before and after my post immediately above.  what i've gathered is:

Fix your ipod with the GTKpod utility
After that, sounds like Songbird is the way to go.

I'll try that tonight and post my results.

---

### Post by betterhands on 2009-02-04
> **betterhands said:**
> been reading a ton before and after my post immediately above.  what i've gathered is:

Fix your ipod with the GTKpod utility
After that, sounds like Songbird is the way to go.

I'll try that tonight and post my results.

well this is exactly what i did last night and i am satisfied with the results.  i needed both apps:

[LIST=1]
[*]GTKpod - to extract songs from device to filesystem
[*]Songbird - to manage syncing ipod with library created from files exported with GTKpod
[/LIST]
being quite a newbie, perhaps there was a way to get the songs from the ipod onto the filesystem from Songbird, but i couldn't find it.  Songbird is pretty slick and 'felt' more like itunes than Banshee--whether that's good/bad/indifferent for you...

---

