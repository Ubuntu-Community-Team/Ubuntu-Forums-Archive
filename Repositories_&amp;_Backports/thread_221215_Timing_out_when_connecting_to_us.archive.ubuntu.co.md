---
title: "Timing out when connecting to us.archive.ubuntu.com"
date: 2006-07-22
forum: Repositories &amp; Backports
---

### Post by Taiden on 2006-07-22
So I am having some problems with my audio drivers messing stuff up, and I am required to use **apt-get** to fix some things. Whenever I try to do an **apt-get install** or an **apt-get update**, it connects to all the repositories just fine, until it gets to us.archive.ubuntu.com. At this point the connection times out. ](*,)

**nmap**, and **nmap -P0** see nothing behind us.archive.ubuntu.com, but **ping us.archive.ubuntu.com** is successful. 145 ms average, 0/26 packets dropped.

Any ideas? I kinda want to get Ubuntu working again, and I need apt-get to do it as far as I know. :???:

---

### Post by Ziox on 2006-07-22
i think the us. mirror is down or something...to upgrade just edit source.list to not include the "us." part. just use archinve.ubuntu.com

---

### Post by Taiden on 2006-07-22
Thanks for the tip man. I was going to try changing **us** to **uk**. :mrgreen:

---

### Post by Taiden on 2006-07-22
So I removed the us part...

before when i tried apt-get install build-essentials, it would list off a bunch of things it was going to install (gcc etc)

Now it just gives me an error that says build-essentials was referenced by another package?

---

### Post by Ziox on 2006-07-22
did you remove all instances of "us."? and perhaps try
sudo aptitude install build-essentials

---

### Post by Taiden on 2006-07-22
Funny, I actually changed us to uk and it worked. Go figure. Now to figure out this sound driver problem... :)

---

### Post by Ziox on 2006-07-22
glad its working now :)

---

### Post by kashgar on 2006-07-22
I was having the same problem with the official repositories and I took out the "us" and changed them from http to ftp.  Those work fine now, but i am unable to access other repositories that i'm trying to download from.  i want to get amarok right now and deb [http://kubuntu.org/packages/amarok-141](http://kubuntu.org/packages/amarok-141) dapper main is timing out.  I also tried using wget to get the key from jriddell's site and that also timed out.  I've tried a few other non-ubuntu repositories and they also timed out.  This all started acting up when i made the switch to dapper a few days ago.

---

### Post by greenstar on 2006-07-23
I've also been having problems with the US repositories today. I tried changing us in "us.archive.ubuntu.com" to ca thinking there are probably Canadian repositories, but no cigar. Figured if there were Canadian repos, there would logicallly be fewer hops to those servers than to UK repos. Long story short, I had no luck trying Canadian repos, so I went with the UK repos and it worked like a charm.

So I wound up changing all occurences us in  "us.archive.ubuntu.com" to uk
so now I have "uk.archive.ubuntu.com"

I wonder if there are repos in Brazil? I'll check now. If so, then this will lighten the load on UK repos when US repos are down, while staying as close as possible to the US so as to keep hop count as low as possible.

We have a winner, folks. The Brazilian repos work also.

So to summarize, when US repos are down at:

us.archive.ubuntu.com

Then use:

uk.archive.ubuntu.com

or

br.archive.ubuntu.com

Hope this helps both repository server load and user access to the repos.

Greenstar

P.S. If my presumptions on distributing the extra load over the UK & Brazilian repos are not sound, feel free to correct me.

---

### Post by greenstar on 2006-07-23
I just found that the Brazilian repos are apparently missing some packages.

Linpopup isn't there, though the major stuff seems to be. Your mileage may vary.

Greenstar

---

### Post by ShirishAg75 on 2006-07-23
Lemme add to the confusion, the in.archive was not working yesterday but didn't try nmap as well as ping. Would try today & see.

---

### Post by Etlaesium on 2006-07-24
I was having the same issue for a couple of days.  I would have thought that the Ubuntu team would have chosen to use multiple first-stage entry points, then use the active servers to dynamically route the repo requests.  But, that's just me...

Anyway, I removed the US subdomain from all of my entries and changed from http to ftp.  Everything is working well for me.  Thanks to whomever first posted that.

---

