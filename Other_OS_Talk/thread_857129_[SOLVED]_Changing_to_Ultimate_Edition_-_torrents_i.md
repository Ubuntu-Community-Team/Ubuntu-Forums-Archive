---
title: "[SOLVED] Changing to Ultimate Edition - torrents in progress"
date: 2008-07-12
forum: Other OS Talk
---

### Post by SeanLor on 2008-07-12
Greetings, folks!

So, after spending some time with the Ubuntu Ultimate Edition live dvd, I most definitely want to make the switch from Hardy to U.E., but I've got a couple questions before I take the proverbial plunge. 

(Quick background: I switched to Hardy about 6 weeks ago, and have no prior Linux experience; I'm now comfortable with the basics, but have no programming experience or other excessive techy know-how. Smarter than the average bear, but no Mensa for me.)

I've got Hardy & Vista basic both installed on my laptop, and I use an external HD for all of my music, movies, etc. I want to upgrade to Ubuntu Ultimate Edition, but I've got some large torrents on the go in Ktorrent that I really don't want to sacrifice. (most of them I don't mind restarting, but a few full seasons/full series are 80% complete after many many moons of downloading.) 

Ktorrent is currently set to download torrents to a folder on my desktop (ubuntu partition), and then move completed downloads to my external HD. 

Is there any possible way that I can install Ultimate Edition without losing the torrents in progress? In a perfect world, I could move the 'torrents in progress' folder to my external HD, change from Hardy to Ultimate Edition, and then have my torrents pick up where they left off. (Some of them could be many weeks to complete, and I'd rather not wait to upgrade.)

I'm probably SOL, but any suggestions would be greatly appreciated!

---

### Post by atomkarinca on 2008-07-12
You can backup your .ktorrent folder in your home directory. KTorrent should save its data in that folder.

---

### Post by SeanLor on 2008-07-12
Are you referring to the folder that partial downloads are going into, or another ktorrent folder? Searching for '.ktorrent' returned no results, but searching for 'ktorrent' brings up 2 folders - one in /usr/share/docs & one in /usr/share/apps, as well as several text files, shared libraries, shell scripts, and png images.

---

### Post by atomkarinca on 2008-07-12
.ktorrent folder should be in your home folder, from view select "Show Hidden Files" or hit Ctrl+h on keyboard and you should see that folder.

---

### Post by SeanLor on 2008-07-12
It would seem that i have no .ktorrent folder in my home folder, after enabling hidden files. Humph.

---

### Post by atomkarinca on 2008-07-12
What about ~/.kde/ktorrent ? Does such a folder exist?

---

### Post by maybeway36 on 2008-07-12
How about:
~/.kde/share/apps/ktorrent
That has all your KTorrent settings in it.
But that shouldn't be necessary, because if you start a torrent and the folder has a partially completed file in it, it will use the parts that are already there.
So actually, just move that partially completed folder over, then tell the torrent client on U.E. to download to that folder.

---

### Post by SeanLor on 2008-07-12
~/.kde/share/apps/ktorrent I've got, and it has multiple folders (tor0, tor1, etc) with info on the partially completed torrents. I'll back up that folder & the 'partially completed' folder, and that should have me covered, right? Even if another client won't recognize the partial torrents, I'd be able to reinstall Ktorrent & replace the new ~/.kde/share/apps/ktorrent with the old folder. Sounds logical to me; any reason why that wouldn't work?

---

### Post by Sand &amp; Mercury on 2008-07-12
> **maybeway36 said:**
> So actually, just move that partially completed folder over, then tell the torrent client on U.E. to download to that folder.
It really should be that easy. :D Just make sure you've got the actual .torrent file too.

---

### Post by SeanLor on 2008-07-12
Sounds good. Um, where are torrent files stored? I've never specified a folder for the torrent itself to go to.

---

### Post by wolfen69 on 2008-07-12
it's a good idea to keep the original .torrent files. that way, no matter what you do. all you have to do is right click .torrent file>open with ktorrent, it will ask where to save it to, tell it to save where the partial torrent file is, and it will re-check what you have and continue downloading.

---

### Post by SeanLor on 2008-07-14
Yup, in future I'm definitely hanging on to them. Changeover went smoothly, all is right and and well in the universe, and the peasants rejoice!

---

### Post by estyles on 2008-07-15
Well, since your issue is solved, mind if I threadjack a little?  How is Ultimate Edition?  My Hardy installation is effed up right now - pretty sure it's my own fault, I'm good at breaking stuff that is working fine by tweaking it too much - and I was thinking about installing something else instead of Hardy, just to try out something new.

I have no problem with Hardy, but do you think I should try UUE or something else?

---

### Post by Zero Prime on 2008-07-15
Ultimate Edition is a great distro.  I'm running Ultimate Edition 1.8 Gamers Edition right now.

---

