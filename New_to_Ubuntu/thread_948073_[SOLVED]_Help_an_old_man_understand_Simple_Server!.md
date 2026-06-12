---
title: "[SOLVED] Help an old man understand Simple Server!"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by Kellemora on 2008-10-14
Hi Gang

I posted some direct questions in the server forum where they belong.  However, Like Shultz "I KNOW NOTHING!" when it comes to Servers, but am willing to learn!

The Ubuntu Server Guide is too far over my head, and covers much more than I would ever need.
I don't need Apache, don't need POP3 Mail, etc.

Just a simple home/office LAN but instead of File and Print Sharing between the computers, I just want the computers to be dumb terminals, more or less and have all the DATA and Programs on one box, a server?.

What I understand so far is that it don't matter WHERE a hard drive resides, on Ubuntu, it's mounted on the machine it's in use on, just like it's a local drive.  And since unlike WinDoze there is no Registry.  A program also can reside on a server and be used from there by a workstation.
Or putting it another way.  The computer at the desk Knows Nothing either, nothing can be lost if it breaks down, is stolen or somebody smashes it with a hammer.  Everything is on the Server. 

This would be a total Ubuntu home/office, no Doze machines to gum up the works.

I'm of the understanding, with 8 computers networked together, using a server would virtually eliminate 900% of the problems of seeing all the other machines between each other and remembering which machine holds what files.

But in reality, the Server will only hold the location of the Hard Drives, wherever they are situated and be mounted on the Server and all other computers would then look to the server for a file and not at all the other computers to try and find it.

What I'm asking, is there a web site or document that omits all the Commercial uses of a Server and only focuses on in-house usage for file serving and possible program serving as well?

Thanks
TTUL
Gary

---

### Post by jerome1232 on 2008-10-14
Sounds like your looking for is LTSP (Linux Terminal Server Project) to me.

Basically when the computers (thin clients) boot they grab their kernel and everything over the wire from the server, they send mouse/key presses to the server, the server processes info and sends screen updates. The thin client doesn't even need a hard drive in it.

Unfortunatly I have zero experience setting this up and can only serve to point you in a good direction.

[http://ltsp.mirrors.tds.net/pub/ltsp/docs/ltsp-4.1-en.html](http://ltsp.mirrors.tds.net/pub/ltsp/docs/ltsp-4.1-en.html)

---

### Post by JoshuaRL on 2008-10-14
I think that what you are refering to is called a thin client.  A big mainframe style PC, with smaller and lighter (not to mention cheaper) PCs that get their processing muscle and files from the main server.

[https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

---

### Post by Kellemora on 2008-10-15
Thanks Jerome and Joshua

Exactly the kind of info I have been looking for, for days now!

Since I have spare computers right now, I will try all three methods and see which one I like the best.

Again, Thanks

TTUL
Gary

---

