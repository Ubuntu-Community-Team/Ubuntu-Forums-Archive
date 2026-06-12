---
title: "HOWTO: Setting up a computer lab with Ubuntu 6.06"
date: 2006-07-20
forum: Outdated Tutorials &amp; Tips
---

### Post by pclancy on 2006-07-20
This summer I worked in a computer science lab, and my job was to build 10 clients and a server.  I documented everything thoroughly, but it's too long to post on the message boards, so here are the links.

HTML:  [http://students.haverford.edu/pclancy/howto/howto.htm](http://students.haverford.edu/pclancy/howto/howto.htm)

PDF:   [http://students.haverford.edu/pclancy/howto/howto.pdf](http://students.haverford.edu/pclancy/howto/howto.pdf)

There was some discussion about this in another thread: [http://www.ubuntuforums.org/showthread.php?t=186357](http://www.ubuntuforums.org/showthread.php?t=186357)

---

### Post by kele on 2006-08-22
Can't seem to be able to get to the links you have above.


##EDITED

Sorry I was able to connect to one link

---

### Post by pclancy on 2006-08-22
I'm not sure what the problem is, if you want the PDF I can email it to you.  I didn't post the HTML directly, because it's over the character limit of these forums.

---

### Post by TNBY963 on 2006-08-22
Thanks for this HowTo.

I'm a teacher myself, so this is very usefull.

Greetz

---

### Post by helmet on 2006-08-23
some good points but the best way is systemimager.

i'm working for the department of electrical and computer eng at the university of alberta right now, and i setup a lab of 68 machines, a lab of 30, and am the contact person for 3 other individuals customizing ubuntu for their labs with cross-compilers, etc. we are using systemimager to do everything and it's amazing. setup one golden client, hack some scripts, add some users for automation, and go drink coffee :D

---

### Post by egoldtech on 2006-08-30
THANKS helmet for your info.
we have to setup Ubuntu on several laptops, all the time, and if the hardware is the same -->boot it [http://www.terabyteunlimited.com/](http://www.terabyteunlimited.com/)   ,  but what to do
if I want to have the "same configuration", dvd codecs, wifi radar, extra app,  firefox tuneups, etc .... all the work again and again ?????
what the people recomend, ????

Eze

---

### Post by pclancy on 2006-08-30
> **egoldtech said:**
> what to do if I want to have the "same configuration", dvd codecs, wifi radar, extra app,  firefox tuneups, etc .... all the work again and again ????? what the people recomend, ????

Well, Helmet was suggesting you use SystemImager to do exactly that.  I chose PartImage because I was not allowed touch the existing DHCP server or create a new one.  SystemImager seems like the most complete solution, but if you don't have that many computers to set up, PartImage is acceptable.  What I did was set up one computer exactly the way I want it, and then made an image of it, and put that on the server.  Once it was on the server I just wrote a script to extract it onto each computer.  All I had to do was run the script on each computer.  So after that I had the same image on each computer, and I just had to change a couple configuration files on each computer.

---

