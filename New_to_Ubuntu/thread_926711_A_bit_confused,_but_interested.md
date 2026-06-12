---
title: "A bit confused, but interested"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by NintendoTogepi on 2008-09-22
I'm very interested in trying out Ubuntu, but I'm a tad confused about one issue.

I've got Windows XP. As much as I'd like to change that permanently, I'd rather not as I have too many programs that require it.

Anyway, so I know people do this, but how do I install Ubuntu without uninstalling XP? Will it hurt my computer? :confused:

I know, I probably sound like a total moron. I'm not computer illiterate by any means though, I've been using them since I was 4! (which is seriously not a joke).

---

### Post by jemate18 on 2008-09-22
> **NintendoTogepi said:**
> I'm very interested in trying out Ubuntu, but I'm a tad confused about one issue.

I've got Windows XP. As much as I'd like to change that permanently, I'd rather not as I have too many programs that require it.

Anyway, so I know people do this, but how do I install Ubuntu without uninstalling XP? Will it hurt my computer? :confused:

I know, I probably sound like a total moron. I'm not computer illiterate by any means though, I've been using them since I was 4! (which is seriously not a joke).


You can do virtualization

download xVM from 

[www.sun.com](www.sun.com)

then once you have installed xVM

you can now use it to install Ubuntu without wiping your Windows.. Then ubuntu will run under windows, and you can switch to either by just, clicking the other window

---

### Post by jemate18 on 2008-09-22
or you can use wubi..

search this this forum (Absolute Beginners Talk) and use the keyword wubi

---

### Post by philinux on 2008-09-22
This does do a nice job but you have to reboot to each OS.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by bumanie on 2008-09-22
Not a stupid/moronic question at all. To answer your question, there are a couple of ways to install ubuntu without affecting windows. 
A) Use the wubi installer to install ubuntu within windows. Wubi has hooks etc. that make windows think it is a regular .exe program. It can be uninstalled via add/remove. If you like it, you can later move it to its own partition.
B) Do a dual boot where ubuntu has its own partitions and ubuntu's bootloader, grub, will give the choice of booting into ubuntu or windows.
C) You can extensively test ubuntu for compatibility with your system by using the live cd and making sure everything works OK, before doing either installation.
D) You could run ubuntu in a virtual machine.
There are many tutorials on the internet. Read a few and decide how you want to do things. Once decided, ask questions here if you need any help. Pre-reading is always a good idea.

---

### Post by tangibleorange on 2008-09-22
there is very good advice given above. all i would suggest is that if you are editing partitions, you back up your important data first to an external hard drive or DVD. you never know what might go wrong...

---

### Post by freesitebuilder on 2008-09-22
I've used Ubuntu for almost two years now - I started by dual booting with XP. I could do my "work" in XP and then play with Ubuntu when I had free time. That way the learning curve was easy, and I didn't have to panic about not knowing how to do things that I needed to get done quickly.

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) has lots of help - I second the comment from tangibleorange on backing up first. Also you'll need to defrag at least twice before partitioning your drive to make sure all XP clusters are moved out of the way.

Enjoy yourself - I have!

---

### Post by NintendoTogepi on 2008-09-22
Also really quick, do I have to order the DVD or BitTorrent or can I just download it normally?

And I don't think I'll be doing any partitioning any time soon. :-D

Sun and Wubi look promising...

*goes off to read links*

---

### Post by jrothwell97 on 2008-09-22
> **NintendoTogepi said:**
> Also really quick, do I have to order the DVD or BitTorrent or can I just download it normally?

Download away. You can just burn it to a blank DVD as you would with a CD ISO - however, BitTorrent might be a better option for two reasons:

[list][*]It's slightly faster
[*]Once you've finished downloading, it'll 'seed' the file to other downloaders, reducing the strain on the servers and making the idle time while your computer burns the DVD 'useful'. It's not compulsory, but it helps.[/list]

---

### Post by aparigraha on 2008-09-22
Fastest way would be to download it through BitTorrent

---

### Post by tangibleorange on 2008-09-23
there is a really good guide here explaining how to burn your image to a CD using a freely available Windows tool. you can ignore the bit about verifying the MD5sum because BitTorrent does this for you - it is only necessary for HTTP/FTP.

[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by MockY on 2008-09-23
Installing it using Wubi is probably the most painless way you can install Ubuntu. The Wubi installer is very small and it will automatically download the latest image for you.

---

### Post by waspbr on 2008-09-23
wubi already comes in ubuntu's (desktop) liveCD, so all you need to do is download it, burn it onto a CD, and pop it in while you are running windows, a dialogue should open which should allow u to install wubi.

---

### Post by Bucky Ball on 2008-09-23
Problem with wubi is not as fast as hard drive 'real' install as running on a virtual disk within windoze. But for some, not a problem at all. And I agree with other posters, torrent fastest, safest, most reliable way incidentally.:)

---

### Post by philinux on 2008-09-24
Just to de-mistify some info.

[http://www.foogazi.com/2008/04/22/hands-on-with-wubi/](http://www.foogazi.com/2008/04/22/hands-on-with-wubi/)

---

### Post by Paqman on 2008-09-24
> **Bucky Ball said:**
> Problem with wubi is not as fast as hard drive 'real' install as running on a virtual disk within windoze. But for some, not a problem at all.

I'd say "for the vast majority, not a problem at all". In fact i'd say most users would have a really hard time noticing any difference.

---

