---
title: "Minecraft server with port forwarding on Ubuntu 12.10"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by Clothbox on 2013-04-13
Hey, I literally just started using ubuntu 12.10 yesterday, and I've been trying to make a minecraft server on it so me and other people could play on. I tried following the instuctions on the minecraft wiki site, but I keep having this problem where other people cannot connect to the server. I can connect to it on any computer on the same network as the host, but no one else can connect. I've tried external ip, changing the settings on the router page, checking the ports, etc. Would much appreciate it someone can tell me what I did wrong, or even a step by step tutorial on how to put up a minecraft server. Thanks!

---

### Post by [::AP::] on 2013-04-13
Is port forwarding necessary, or would you be willing to use something like Hamachi? ([https://secure.logmein.com/labs/#HamachiforLinux](https://secure.logmein.com/labs/#HamachiforLinux))

I'll be honest, I know very little when it comes to port forwarding (although I'm sure I could figure it out), but I do run a small time Minecraft server for some friends, through hamachi.

You did say that you started using Ubuntu *yesterday*...so I assume you are brand new to Linux? I'm kind of approaching this like you're a total newbie, so, forgive me if not.

I can write a little guide for you (hamachi specific), but it may be a bit later (as late as Wednesday...). For now, try either Googling around for videos/guides, or just playing around with Ubuntu, so you become familiar. 

Before that, I do have a few questions...
-technical experience? Like...are you moderately tech savvy?
-What are the specs (specifically RAM) of the computer that you will be running the server on?
-Is the computer to be used ONLY as a server? And are there any other operating systems installed?

Personally, and I know this might be hard to hear, but I'd scrap Ubuntu and use Debian for a server. Or at least, Lubuntu or Xubuntu, anything which is lighter weight.

Get back to me...I'll help, but it may not be immediate. Also...if you're completely lost, just let me know, and I'll explain things more in depth.

---

### Post by Clothbox on 2013-04-13
I'm more interested in doing it with port forwarding, tbh. I am brand new to linux, but I've been learning a bit about the terminal, installing stuff etc, and I've followed all the instructions on the wiki. About tech savvy, I don't really know how to measure that. but I'm willing to learn and try. The computer is seperate, and is only for a server, no other OSes installed. The RAM is 4GB atm, since I had a mishap with the other RAM sticks I ordered, so I'm using some from my main computer.

---

### Post by [::AP::] on 2013-04-13
Okay. I'll look into port forwarding, but I'm sure someone else will pipe in before I get a chance to get back to you. Look around the Minecraft Forums and other Linux forums. 

How many people do you expect to have on your server? I'm only asking because you mentioned that you have 4GB of RAM. I know the more RAM the merrier, especially with a Minecraft server, but my Debian based Minecraft server runs on a "meager" 1GB RAM and a Core Duo in circa 2006 laptop! Granted, there are never more than 3 or 4 people playing at one time...

---

### Post by Clothbox on 2013-04-13
No idea how many people, but like I said, I had a mishap with the RAM so I'm definitely going to be replacing that sometime.

---

### Post by [::AP::] on 2013-04-13
Am I correct in saying that the only issue which you've come across is the port forwarding? Does the actual server work (can you log on to it?) ?

Here is a poorly written guide that I found. [http://www.planetminecraft.com/blog/ubuntu-server-minecraft-installsetup/](http://www.planetminecraft.com/blog/ubuntu-server-minecraft-installsetup/) Jump to the bottom section.

What is your router model?

---

### Post by Clothbox on 2013-04-13
Yeah, I can log onto it on any computer on the same network (It seems). Router is a WRT54G2 Linkysis v1.0 firmware.

---

### Post by Horbo on 2013-04-13
A full guide: [https://help.ubuntu.com/community/InstallMinecraft147](https://help.ubuntu.com/community/InstallMinecraft147)

Use Hamachi (trivial), and then if WAN clients still can't connect look at port forwarding Hamachi ports.

---

### Post by Clothbox on 2013-04-14
Anyone else have any ideas? Trying to do it with port fowarding

---

