---
title: "Hardy Heron Slow, Should I downgrade to Gutsy Gibbon?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by tsunamikitsune on 2008-05-11
I recently updated to the newest version of Ubuntu and I find it rather slow.  It may have something to do with my dual monitor setup, but I remember everything running much faster in past versions.

Is there some reason for the slowdown or is my computer just not good enough to handle this update? If so, how do I go about downgrading? (And will I be missing out on any important features by doing so?)

---

### Post by jamieh on 2008-05-11
With Windows, whenever you do an Upgrade install, it makes everything MUCH slower. I don't know if Ubuntu is the same, though.

---

### Post by oarion7 on 2008-05-11
I had similar problems when I (initially) upgraded to Hardy Heron. Things ran slower, and I had a great deal of performance reduction in the video card. I ended up playing around too much with things I don't quite understand yet and reached the point where I pretty much had to reinstall everything. So I went ahead and made a Hardy Heron CD, backed up what I needed, formatted my Linux partition and did a clean install of Hardy Heron, and you know what, I no longer have any of the problems that I was having when I had simply done the upgrade. So if you upgraded from 7.10 to 8.04, try formatting and installing 8.04 from scratch instead. I have heard of at least a few other people solving similar problems with the same solution. :)

Best of luck.:guitar:

---

### Post by slimx3m on 2008-05-11
what oarion7 says it is true.  one of my friends upgraded from Gutsy to Hardy and the computer had a lot of problems.  once he did a clean install he didn't had the same problems that he had before.

---

### Post by NIT006.5 on 2008-05-11
I personally don't think it's slow just because it's an upgrade. My two PC's and laptop are all running better on Hardy than they did on Gutsy.

Run the "top" command in the terminal to see what's using up your resources. I had something similar, and in my case it was Xgl that was slowing everything down on my laptop (which isn't the newest). Since disabling Xgl however, it has been running like a dream. If this is the only issue you're having, I would advise first trying to identify exactly what's slowing you down. If you don't win there, then maybe consider going back to 7.10 - but I think its worth trying to tweak it first.

---

