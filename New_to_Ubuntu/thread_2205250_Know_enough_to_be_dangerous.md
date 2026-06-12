---
title: "Know enough to be dangerous"
date: 2014-02-12
forum: New to Ubuntu
---

### Post by eborghi1 on 2014-02-12
Hi people! I'm new here. I have been selling, servicing and supporting PC systems since 1985. I've played with Ubuntu since version 5.04 I believe it was but was never really serious about it.  At this point in my business I have scaled down to wanting to support only businesses with 10 or fewer seats and a server if they have one. With all the upheaval in the economy many of my competitors have gone under so busines for me is not bad. The only problem is I'm stuck with Windows servers in a few places and I must say I wholly dislike them!  How many different screen and dialogs can they possibly come up with for something as simple as setting permissions or taking ownership of a file???!!! Not to mention a plethora of other issues.  I really liked Netware until version 4.01 and had no problem supporting it. Soooooooo........ I took the plunge and installed 13.04 server on an old Dell system I had hanging around the shop. I've been beating it up pretty good for a week or so and it seems to perform beautifully. I installed Webmin because it's easy but I configured the server on the command line where I must say I feel at home to this day. Webmin is just kind of nice for quick additions especially if I'm too lazy to get up off my backside and walk over to the server. I think I'm on to something here since many of my clients don't need anything but a file server to keep data centralized, easy to backup, secure and so forth. At some point if they need a mail or web server it can be added so Ubuntu Server seems to be the way to fly. Most have balked at a server because of the cost of a Windows server and all the ongoing licensing issues and such.  So, my questions are: Should I be somewhere else in the community since I really need to talk about servers but am still a beginner to Ubuntu pretty much?  I have a server running on my shop network and at home and all seems well. Can it be this easy to set up? Do I dare drop 12.04 LTS into a business environment as a pure file server with little Ubuntu (Linux) experience?

---

### Post by TheFu on 2014-02-12
Asking on the server forum would get better replies.

I don't run any non-LTS releases. Too much instability and the support period is too short for any server.

I think you'd be doing your client a disservice pushing Ubuntu (or any Linux) with very little server admin experience. OTOH, we all had to start somewhere. You are at the point where you don't know what you don't know.  Very dangerous. 80% of Windows Admin knowledge does NOT translate to Linux. The techniques used are very different.  Netware doen't help much either - I did that for file, print and NFS services - nothing like UNIX really. 
* Do you eat your own dogfood?
* Do you have backup religion?
* Do you have any Linux Certifications - RHCE?
I'm confused - why would you need to walk over to any Linux server when there is ssh? I admin servers on different continents and 2ft away via ssh.  Also, please tell me you've locked down webmin with extremely restrictive firewall rules ... or better, only access it through an ssh tunnel.

Over the last few years, a few questions have been asked about becoming a Linux Admin on these forums. I recall some really smart answers.

---

### Post by Iowan on 2014-02-12
> **TheFu said:**
> Asking on the server forum would get better replies.
Remember, you can request to have a thread moved by using the Report Post button

---

### Post by mastablasta on 2014-02-13
have a look at Zentyal project (ubuntu based).

and yes it really is that easy. and free and customzable and...

well as mentioned use SSH. who want to keep geting up just to adjust a small thing :-)

---

