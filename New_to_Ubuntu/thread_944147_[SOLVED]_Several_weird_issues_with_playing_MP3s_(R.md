---
title: "[SOLVED] Several weird issues with playing MP3s (Rhythmbox/Banshee/Songbird)"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Bobbino on 2008-10-11
So I'm a pretty new user to Ubuntu... I've dabbled a little in the past and a few days ago i decided to make a switch from windows to this. And while i am quite enjoying the experience, and the few problems i have come across i have mostly been able to fix by myself this one is truly perplexing.

I'm having issues playing mp3s in several programs.

In Rhythm the mp3s play fine, and I can add my mp3 folder to the library... However, every time I leave the program and then access it later, the library starts to dissapear, taking quite a while to reach 0 songs, and once it has dissapeared it will reapper again, and the songs play fine. This happens every time i exit and re-enter the program.

in Banshee I managed to get my music folder to add to the library and even used it semi-successfully to add some songs to my iPod (iPod Classic). However, now it seems that no songs will play from the library.

Songbird randomly crashes, however, being in beta I half expected this when I installed it, so it's not too great of a problem.

My MP3s are stored on a different drive to the install of Ubuntu, still in a NTFS format back from when i was using windows... I wonder if this could be part of the problem? And would it be easy to reformat the drive to a linux format without losing the data... The drive is almost full, so anything that would wipe the drive would not really be an option as trasferring it all to DVDs would take a very long time.

Anyone help would be greatly appreciated.

-Bobbin.

---

### Post by eternalnewbee on 2008-10-11
I use vlc to play music and watch videos.
Have you tried it? It's in add/ remove programs

---

### Post by Bobbino on 2008-10-11
Yeah, I'm using VLC to play videos currently, and for that job it is great... However, due to the sheer number of MP3s i have (Around 20,000) for my music needs I'm looking for something with a more sophisticated library system. Something akin to iTunes in Windows. Which is why i tried those three programs as all seem to be very close to the sort of thing I would like to use... Songbird was by far my favourite, but it doesn't seem stable enough to use yet.

---

### Post by eternalnewbee on 2008-10-11
I've never used songbird (maybe I'll give it a try). How about Amarok then?
Tried that one and it worked just fine.

---

### Post by Bobbino on 2008-10-11
Thanks for the suggestion on the program, I will have a look at it.

Though it would also be nice to get to the root of the problem also... I've been looking through some posts and things... Digging around... Have read some things about drives not mounting on login.. I was wondering if this could be another source of the problem?

Sorry if I'm sounding a little noobish... Been a windows user since 3.11 and all this Linux stuff is a little confusing.. Am learning though!

---

### Post by eternalnewbee on 2008-10-11
Suppose you have two hard disks. On one of them you have your Ubuntu system. The other you use to save data (including music files).
When you start up your system The data drive isn't automatically mounted. If you go to Main menu > Computer and right click on the data drive you can choose the option mount.
Then Rhythm player can be directed to open files from that drive.
As for automatically mounting the data disk on start up: can't help you out there. You have to start a new thread, or search for it (for example: How can I mount 2nd drive).
Good luck

---

### Post by Bobbino on 2008-10-11
So i worked out the problem. My drives aren't mounting when i boot into ubuntu, so obviously, when i load a library... it doesn't see any of the files as being there!...

Gonna search around for methods of making them auto mount on boot. So Thanks to those that offered their help :)

-Bobbin

---

