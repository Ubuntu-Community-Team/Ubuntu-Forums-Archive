---
title: "What music player for NAS-based media folders?"
date: 2015-06-12
forum: New to Ubuntu
---

### Post by Jon_Parker on 2015-06-12
Hello,

New to Ubuntu and using 14.04 LTS (dual boot with Windows 7) which seems rather nice so far. I've set up Evolution for mail and calendar and very impressed with the Google integration.

I'd like to find a music player which can handle a large collection of music which is stored on a NAS drive. The default player Rythmbox seems to want the music collection inside the /Music/ folder which isn't viable.

I've had a go with VLC but the media library side of VLC seems pretty poor really. Ideally I'd like something that will display my albums a bit like iTunes, e.g. in a grid format with cover art visible. And I'd like to be able to point the player to multiple folders for from which to scan for tracks.

On my NAS I have 1 shared drive with two folders in the root, one named Music Almbums and one name Compilations so I need to be able to select at least two folders as the music location.

Hope that makes sense?

Thanks for any recommendations you may have.

Jon

---

### Post by Bucky Ball on 2015-06-12
Welcome. Well, one way to do what you're trying to do is to mount your NAS partition on your system using Gigolo or setting something up manually (Gigolo is in the repositories/Software Centre). 

Launch VLC> Media> Open Network Stream> Disc tab> Browse.

If the partitions are mounted on your system via Gigolo, or any other way, then you probably won't need to go through the above. You'd be able to select data from the remote partitions as if they were on a local one, regardless of player. :)

If you are looking for a way to connect directly to the server via a music player without mounting the remote partition on your local system first, this will be of no help, but is not, then hope it gives you some clues.

---

### Post by deadflowr on 2015-06-12
You can add music from outside your Music folder to your library in Rhythmbox.
You need to go to File >> Add Music.
In this toggle the Bar that says Music and select Other.
Select your nas location, which should be listed in the side bar.
When you get to your Musoic location in the nas, click open and it'll import the files.
Note import in this case does not mean copy into your Music location only that the files are accessible to rhythmbox.
The files will remain on the nas.

---

