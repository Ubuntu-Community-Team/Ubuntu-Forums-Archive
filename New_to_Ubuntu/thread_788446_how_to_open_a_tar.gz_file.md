---
title: "how to open a tar.gz file?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Andrew79 on 2008-05-09
just downloaded Joomla for buidling a website. i downloaded it as a tar.gz file? what is it and how do i make it work, when i open it from the download box, it just opens a file page? now what?

---

### Post by gali98 on 2008-05-09
tar.gz is just a compressed file that can contain many more files. you should be able to open it with archive manager then extract the files and run from there.

---

### Post by aysiu on 2008-05-09
.tar.gz just indicates it's a compressed file (much like the .zip extension in Windows).

Are you running a Ubuntu web server? Or are you running a Ubuntu home computer that's accessing a remote web server?

---

### Post by Andrew79 on 2008-05-09
Huh??? Do what with the archive manager? What am I looking for? What do you mean about the server? i have Ubuntu 8.04 only intstaled on my laptop. and have comcast for my internet provider?

---

### Post by gali98 on 2008-05-09
For Joomla you will want to extract these files to 
/var/www/Joomla (you can replace "Joomla" with whatever you want.

This is expecting you to have apache or other webserver running on your computer.
Now just open a browser and point to localhost/Joomla/install.php
Hope this helps!
Kory

---

### Post by Andrew79 on 2008-05-09
okay, i am compleatly lost now. i have absolutly now idea what your talking about.

---

### Post by gali98 on 2008-05-09
> **Andrew79 said:**
> just downloaded Joomla for buidling a website. i downloaded it as a tar.gz file? what is it and how do i make it work, when i open it from the download box, it just opens a file page? now what?

> **Andrew79 said:**
> Huh??? Do what with the archive manager? What am I looking for? What do you mean about the server? i have Ubuntu 8.04 only intstaled on my laptop. and have comcast for my internet provider?

Judging by what you say, you seem fairly new to this all. You might  want to think twice about running a web server. I'm not trying to be mean or anything, but you might test the ropes a bit before you go in deep.
Nevertheless, We need to start by installing our webserver.
First you need to start up Synaptic package manager. This is located in System(on the top menu bar) -> Administration -> Synaptic.
Once this loads go to Edit -> Mark Packages by Task
this will load a list of items.
You will want to look for "ubuntu Server" or "LAMP"
I am severly sorry, but I am not on a linux computer at this moment and cannot check. 
Hit okay or apply, then on the main screen hit okay or apply. It shoud pop up with a box just hit okay. It will start to download packages then it will install them.
Try and get this far then post back.

Hope I am helping and not harming:)
Kory

---

### Post by rscds on 2008-05-09
I am so glad that Im not the only one who gets confused with the tar.gz.  Good luck.

---

### Post by Andrew79 on 2008-05-09
Hi Kory,
 okay, just checking first, a webserver? i am just trying to make a website with pics and stories on it. the joomla is supposed to just be a way to drag and drop pics and boxes and squares and basic looking website, right?

---

### Post by aysiu on 2008-05-09
Maybe you're a bit confused as to what exactly Joomla is. Joomla is a content management system that you host on a web server (either making Ubuntu a web server or through a remote web server).

If you want a program to make websites with, try Kompozer.

---

### Post by Andrew79 on 2008-05-09
HAHA!!! Cool thanks. Sorry about all the confusion. Someone else suggested the joomla, and yes, I am very new to digging around in the guts of the computer. This is my first step of giving up on M$ and all their junk products. 
Thanks again
Andrew

---

### Post by gali98 on 2008-05-09
> **Andrew79 said:**
> Hi Kory,
 okay, just checking first, a webserver? i am just trying to make a website with pics and stories on it. the joomla is supposed to just be a way to drag and drop pics and boxes and squares and basic looking website, right?

As for what Joomla is see the other poster... If all you want to do is just test out webpages I suggest using Konqueror as said by the other poster, but you might just be interested in just making a blog.
Kory

---

### Post by aysiu on 2008-05-09
Yeah, blogs are very flexible and usually use some kind of content management system underneath.

---

