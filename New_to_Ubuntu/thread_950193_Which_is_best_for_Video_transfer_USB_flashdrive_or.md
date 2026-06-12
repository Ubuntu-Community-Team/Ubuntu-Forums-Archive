---
title: "Which is best for Video transfer? USB flashdrive or Ethernet"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Parasitesss on 2008-10-16
I want to transfer videos from my ubuntu desktop to my macbook, which is better? Ethernet crossover connection or Flashdrive?

What are the pros and cons of both?

---

### Post by GuitarRocker2562 on 2008-10-16
In my experience, ethernet. Flashdrives tend to take a LONG time to copy large amounts of data. I have never used and ethernet crossover in Ubuntu, so you may need to look that up.

---

### Post by cariboo on 2008-10-16
A crossover cable is exactly what you need to connect twp computers together with out a router, hub or switch. I would go with Ethernet to transfer large files.

Jim

---

### Post by gali98 on 2008-10-16
Definatly ethernet!
going between just two computers is really fast. 
I went between my laptop (a tx2000z) and my xbox at about 11mb/s.
Comparing that to having to transfer it tiwce beats it any day.
Before you go out and try and find a crossover cable (if you do not have one handy)
just try a normal cable. This works for me. I think newer ethernet jacks can autodetect if a crossover cable is needed and do some background work.
My laptop and xbox is a perfect example. A normal cable worked fine.
Kory

---

### Post by Parasitesss on 2008-10-16
How would I got about doing so?
just plug and start transfer immediately?

or do I have to configure the networking?

---

### Post by gali98 on 2008-10-16
you will have to configure networking.
However, I just had a thought.
If you have a router close to the desktop, just plug both the computer and the macbook into the router.
If this is not an option you will have to configure static ips for both machines.

The easiest way is to disable wireless on the laptop if it is connected.
Then make sure the computer and laptop are connected to each other and only each other.
Then go into the network manager on each one and set one ip to 192.168.0.1
and the other to 192.168.0.2
set the gateway to 192.168.0.1 on each one.
The subnet mask will autoconfigure itself usually.
I don't think you need to configure dns, but if you have problems, or just want it as a safety precation, just set it to 192.168.0.1

okay after you save that, you will probably need to restart networking.
on ubuntu just use
sudo /etc/init.d/networking restart

I'm not sure how to do it on mac, but it can't be hard.

Now the easiest way to share is to do it on ubuntu unless you know where to go from here.
Basically jst right click on a folder and go to Shareing.
Just set it to "writeable by other users" and guest access.
Then on Mac you should be able to put the ip into the explorer (I guess finder??)
and go from there.
If you need more help than this, post back and I will try and help you.
Kory

---

### Post by Parasitesss on 2008-10-21
thanks soo much, I'm going to try this out~!

---

### Post by gali98 on 2008-10-21
Yes sir...
Let me know how it goes if you will. I want to know if it works :)
Kory

---

