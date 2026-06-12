---
title: "Newbie Thinking of Creating a Server"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by benjam4 on 2008-08-22
I am new to Ubuntu and have the most recent version installed on my laptop.  I also have a fairly new 80G Desktop that I am thinking on making into a server so that I can play around with some of the great applications in the Ubuntu world... specifically with some of the wikis such as PMWiki for project management solutions.  

I have created websites in the past and manage 3 companies sites through a public content management system. I am knowledgeable about many software applications but limited experience and understanding with command codes so it is taking some time as I make the adjustments with Linux.   

My question is any suggestions on making my desktop into a server (I know that I can download Ubuntu Server) but not sure if I might be getting in over my head...what are some advantages of doing this with Ubuntu and what challenges might I encounter before I start down this path???

Thanks a bunch for any suggestions...

---

### Post by neurostu on 2008-08-22
One thing I would do is install the package **ubuntu-desktop** on the server after you install the OS for a newbie I think this is essential unless you are really familiar with the command line

---

### Post by DFord425 on 2008-08-22
[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html) 
That has some very good guides on how to turn your computer into a server using ubuntu.

---

### Post by benjam4 on 2008-08-22
Thanks, I did see this and reviewd the information beforehand and this is why I was then wondering if I was getting involved with something more than I bargained for... is it important to already have a very good knowledge of Ubuntu BEFORE taking the next step and creating a server or learning both at the same time my pose some advantages???

---

### Post by Old_Grey_Wolf on 2008-08-22
I built a server on my LAN. I have never had a server before. I was concerned that I was not up to the task; however, I was surprised how easy it was. The Ubuntu package manager and the Help or How-To posts on this site made it go a lot faster than I ever imagined.

Go for it!

---

### Post by jerome1232 on 2008-08-22
Personally if your out to learn about linux, I would install a cli only server, there are plenty of guides out there and lots of help in the forums if you find yourself lost.

Knowing the command line comes in handy, it's powerful and faster/preferred for certain tasks. (dare I say a good majority of tasks once you learn it)

Plus you'll start figuring out how you can make scripts to simplify everyday tasks.

Yes the learning curve is steep, but worth it I think.

---

### Post by benjam4 on 2008-08-22
> **jerome1232 said:**
> Personally if your out to learn about linux, I would install a cli only server


I'm sorry, but if I am not that familiar with commands, would it be wise to install a cli (command-line only server???)

---

### Post by jerome1232 on 2008-08-22
Think about it this way, if you install (pick any random service here)
guess how 99% of guides will walk you through configuring it. The command-line. Most services are either configured by editing text files, or through a web interface, both of which having a gui doesn't make it any easier.

It also depends on what your trying to do with the server, maybe in your case a gui is very beneficial.

I have a little 400 mhz celeron computer with 110 Mbs of ram, it serves as a dns cacher/forwarder, apt-cacher, dhcp server and teamspeak voice chat server. It can even serve a game of NeverWinter Nights (that puts it under heavy load though with a game of 4). Does this all with 400 mhz and very little ram (it only uses like 44 mb) After initial configuration was done, I ssh in once a day to update, and once a week to check my logs, other than that I don't have to do anything with it.

Of course this is my personal preference I'm not saying don't install a gui, I just think it's a great way to learn how to do more in linux, being forced to use a command line.

---

### Post by iansane on 2008-08-22
You might use command line to install webmin for a web based admin page to access from another computer. It makes a lot of stuff easy and some stuff complicated. I know it's probably frowned upon by some and you need to learn the commands but it is fairly widely used for server admin. Also there's phpMyadmin for setting up mysql databases for your site. I think they both tell on there websites how to enable the nessesary repos and use wget command to download them in terminal.

howtoforge.org has some good how to's for setting up the server

---

