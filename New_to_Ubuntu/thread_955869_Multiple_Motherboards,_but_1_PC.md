---
title: "Multiple Motherboards, but 1 PC?"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by D3M0L1$H3® on 2008-10-22
Here; [http://helmer.sfe.se/](http://helmer.sfe.se/) is the story of a Swiss 3D artist who needed the processing speed for rendering.
She put 6 motherboard with 2.4GHZ processing speed, 4GB RAM each into one big IKEA file cabinet computer and used Dr. Queue to distribute the jobs on all the motherboards.
How would one connect them in order to use them as one PC?
Yes, I know it would be expensive, but as an everyday Linux box, it would be blazing fast with even, say, 2-5 Motherboards/processers/rams.
Eh?
Advice?
Ideas?
Thoughts?
Please?

---

### Post by y@w on 2008-10-22
That's awesome. I want to build one now..

As far as Linux clustering software goes, it all depends upon the applications you want ot run. Obviously she used Dr. Queue and it works well for her but there are tons of options around. A good place to start would be here: [http://lcic.org/computational.html](http://lcic.org/computational.html) and at the wikipedia page for clustering: [http://en.wikipedia.org/wiki/Computer_cluster](http://en.wikipedia.org/wiki/Computer_cluster)

It's not going to be something you'll want to use for a desktop per say but if you do a lot of jobs that require a ton of processing time, then clustering is the way to go.

---

### Post by Sarmacid on 2008-10-22
I saw the site a while ago, and got me interested, but I don't really need that kind of power, so a desktop will suffice for me now(Hopefully not for long). He states that they are connected through gigabit ethernet

> All connected to a 8 port 3 com gigabit switch.

If you're gonna try that, keep us posted and maybe we can help :)

---

### Post by Kellemora on 2008-10-23
Hi D3

You can study [this]("http://www.scl.ameslab.gov/Projects/old/ClusterCookbook/") if you would like...

It's the SCL Cluster Cookbook site.

I've also heard of LinkLock, but couldn't find anything about it online.

TTUL
Gary

---

### Post by markbuntu on 2008-10-23
All the big renderfarm clusters run linux, some with over 2,000 processors. It is the cluster os of choice.

---

### Post by D3M0L1$H3® on 2008-10-29
Thanks guys. I might try it, but i was just wondering how it would do as a desktop PC, with things like burning CDs, copying files, etc., if they were spread out with Dr. Queue, or whatever, or if that would even work that way.

I'll definitely keep you posted if i try it!

---

### Post by LowSky on 2008-10-29
Burning CD's is limited to the rate that the CD-ROM can operate at. Same applies to moving of files over hard drives.
What this kind of technology is great for is processing huge amounts of data at one time by splitting it up. One great exapmle is [Folding@Home]("http://folding.stanford.edu/") where information is sent to a bunch of home computers globaly and the information is rendered and sent back. Its basically  a global server over countless home desktops... Whats cool is my Playstation 3 can even attribute.

---

### Post by D3M0L1$H3® on 2008-10-29
> **LowSky said:**
> Burning CD's is limited to the rate that the CD-ROM can operate at. Same applies to moving of files over hard drives.

Yes, true for optimum PCs, but if the computer is not processing at max speed at the time, it goes much slower. Me burning a DVD or CD goes much faster on my 2GB ram computer with same speed burner than the same burner of my 512mb ram pc. and burning on one computer goes faster than burning on the same computer with stuff going on.
so i figured doing it on a separate set of RAM and processor, but on same general PC would go faster even with other things running and such.
yes, my friend has a PS3 and we looked at the Stanford prog, it locked up, he was impatient, but it seemed like a missle launc prog lol.
but thanks.

---

### Post by taqkavar on 2008-10-29
These kinds of setups would not help with general purpose computing. For 3d rendering and some advanced graphical software for video compositing they would be useful.
If you want to put money in a system for fast personal computing you are  better off with investing in the best components for a single PC.

A simple thing you can do with a number of low quality computers is to install Linux on all of them, and connect them to a hub/router. then ssh using the -X tag to all the machines from one to run graphical programs in any of them you want. I have three old computers, one is dedicated to runing azureus, other I use to run open office on it while the main one is dedicated to firefox. All of their storage spaces are mounted as nfs. Its pretty easy to setup and hassle free.

---

### Post by robert shearer on 2008-10-29
> A simple thing you can do with a number of low quality computers is to install Linux on all of them, and connect them to a hub/router. then ssh using the -X tag to all the machines from one to run graphical programs in any of them you want. I have three old computers, one is dedicated to runing azureus, other I use to run open office on it while the main one is dedicated to firefox. All of their storage spaces are mounted as nfs. Its pretty easy to setup and hassle free.



How about posting a tutorial about how you did it?.
I'd sure like to give it a try. :)

---

### Post by D3M0L1$H3® on 2008-10-29
> **robert shearer said:**
> How about posting a tutorial about how you did it?.
I'd sure like to give it a try. :)

yes pleasE? lol.
nfs? do you mean ntfs? or is that like 'network file system' so they're all saving to oe?

---

### Post by taqkavar on 2008-10-29
Umm, I'm a newb myself but I remember using this tutorial to setup the nfs shares which allows you to mount your hard drives:
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

And then I open a terminal and just do:
ssh -X <username on remote computer>@<ip of remote computer>

It prompts you for the password. you login and anything you run will be done on the remote computer, you can use the Network File System (nfs) to access files on the computer you are using.

---

