---
title: "More Torrent/Music Issues...."
date: 2008-09-12
forum: New to Ubuntu
---

### Post by rideburton56 on 2008-09-12
Hi All, After all the great help I recieved in regards to how to get torrents set up, I have a few follow up questions.  First of all, being that I am a big fan of the commmunity set up, I want to make sure that I have all my DLed files available for others to get from me.  I have gotten 3 files, and my ratio is .4, how do i rectify this?  Is it literally getting files that many other people are interested in, or are there some setting that can be tweaked (for example,I have yet to open a port, and I was perfectly happy with the downstream speed).  

Also, when I select a torrent, and it starts to DL, do I have to keep the files in a specific place to make sure that they are available?  I thought I read something about Linux that it doesnt matter what folder the file is in, the resource is always available.  I am kind of anal about my file organization, so traditionally when I recieve files, I rename them how I want and then I put them in  specific subfolder.

Also, is there a reccommended program that can retag file info for music files?  It seems that rhythmbox does not offer this, and like I said, I am kind of anal about organization.

Last but not least, while browsing the repositories, I added a program called streamtuner.  Sounded like a great idea, compiling all my favorite webcasts and putting them in one box, but I cant get it to work!  It opens, I pick a file, click on tune in, and it says it cannot tune in.  Is there some sort of extra configuration that is required?  I am away from my ubuntu box until probably sunday (at work/girlfriends), so I wont be able to recreate the problem till then, although I will be checking in from other places.  Thanks!

---

### Post by barney385 on 2008-09-12
Which torrent client are you using?

Deluge? Transmission? Etc.?

---

### Post by rideburton56 on 2008-09-12
Transmission

---

### Post by barney385 on 2008-09-12
Though the edit button on transmission you can set your preferences.

---

### Post by t0p on 2008-09-12
> **rideburton56 said:**
> 
Also, is there a reccommended program that can retag file info for music files?

**Audio Tag Tool**

```
sudo apt-get install tagtool
```

---

### Post by rideburton56 on 2008-09-12
I have gone through transmission settings I am just trying to figure out how to make sure everything is available to everyone else.  In a perfect world, on transmission, what would a poweruser do, starting from going to a website and clicking on DL torrent, and finishing with enjoying file and making sure others can to.

---

### Post by lovinglinux on 2008-09-12
> **rideburton56 said:**
> Hi All, After all the great help I recieved in regards to how to get torrents set up, I have a few follow up questions.  First of all, being that I am a big fan of the commmunity set up, I want to make sure that I have all my DLed files available for others to get from me.  I have gotten 3 files, and my ratio is .4, how do i rectify this?  Is it literally getting files that many other people are interested in, or are there some setting that can be tweaked (for example,I have yet to open a port, and I was perfectly happy with the downstream speed).  

Just seed the torrent you download at least until you reach 1.0 ratio. You might want to prioritize seeding torrents with fewer seeders. For example if a torrent has 500 seeders and 20 leechers, you probably won't make much difference on the swarm. But if a torrent has 20 seeders and 500 leechers than your bandwidth will be much appreciated. 

> **rideburton56 said:**
> Also, when I select a torrent, and it starts to DL, do I have to keep the files in a specific place to make sure that they are available?  I thought I read something about Linux that it doesnt matter what folder the file is in, the resource is always available.  I am kind of anal about my file organization, so traditionally when I recieve files, I rename them how I want and then I put them in  specific subfolder.

As long as you rename or move the file using the torrent client interface it will remain available, no matter what name or directory you choose (if you don't stop it in the client). If you rename or move the file using other software like Nautilus, then the torrent will give you an error if you try to seed it.

---

### Post by rideburton56 on 2008-09-14
I have worked out all of the kinks with my torrent/DL questions (thanks again to all of those who worked with me on that one), I just have yet to get streamtuner to work yet, does anyone have any input in regards to this particular package?

---

