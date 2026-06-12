---
title: "Windows Share"
date: 2014-03-05
forum: New to Ubuntu
---

### Post by docJ on 2014-03-05
Hi,
its been a while since my last visit where you helped me build a system from the ground up.
It has worked out exceedingly well for the most part. Recently I was running low on storage space and added a 5th hard drive, and since the original setup was a while back, a friend helped me with partitioning, auto mounting and sharing the drive for my home network. Once we were done, I rebooted the system and there were no issues at all.

A couple of days ago, I had a short power failure and had to start the system, and that's when I noticed, from my windows network, that the last share drive had disappeared. From the network page, it's gone (but all 4 other ubuntu drives are ok).

From Ubuntu, If I go ```
**smbclient -L localhost**
```, I only see the 4 "old" drives
I have a workaround for now, tru Nautilus, I have right clicked the 5th drive and enabled sharing. Its icon then changes (showing an arrow confirming its shared) What puzzles me is the 4 previous drive icons do not show this extra arrow on them; right-clicking them & going to the share tab, no share options are checked, yet from windows network, they're fully visible.

If I right click and enable sharing on any of the 4 drives I can already share, they will appear in duplicate from windows.
I am at a loss to explain this behavior, and while my Nautilus sharing is a working solution, I am wondering what cause this difference

---

### Post by docJ on 2014-03-07
Bump:P

---

### Post by docJ on 2014-03-10
Oddly enough, I just went a moment ago gksudo nautilus, then to Media foler, and to my astonishment, my 4 "original" drives showed the share symbol, and the latest 5th drive didn't.
That's the exact opposite of what I was seeing the last week; 4 original drive "not shared" and the latest shared. What the ????

So my problem seems solved, but I have no clue how it happenned nor how it fiexed itself

---

### Post by docJ on 2014-03-10
Actually, I can still reproduce it.
If I open "regular" Nautilus, then Media folder, my "a" drive show the share symbol, but the 4 other drives "b", "c", "d" and "e" don't.
If I go gksudo Nautilus, then the Media folder, my "a" drive doesn't show the share symbol, and you guessed it, the 4 other drives are displayed as shared.

---

