---
title: "Transmission won't download anything?"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by hopelessone on 2008-06-05
Hi,

What do i have to do?

thanks

---

### Post by darth_indy on 2008-06-05
Could you be a bit more specific? What have you tried so far? Have you changed any settings? Did you get any error messages?

Without more information, there's not much I can do. :)

---

### Post by hopelessone on 2008-06-05
Theres no error it always says:

Downloading from 0 out of 0 connected peers...i know there is plenty there...i can download them in windows...the port is open..no error mess..

thanks..

---

### Post by darth_indy on 2008-06-05
Did you try any other torrent programs? Deluge is the one I use most often; there's also KTorrent, and Azureus (which is pretty resource-intensive).

I'm sorry, I don't have a lot of experience with Transmission, but if you try another one it may help narrow down the problem.

---

### Post by avtolle on 2008-06-05
FWIW, it looks like no one is seeding that particular torrent right now. If I've misunderstood something, well, it won't be the last time. :-)

---

### Post by darth_indy on 2008-06-05
If they can download it now in Windows, that wouldn't be the problem. By the by, when did you try it in Windows? If it was a while ago, then Avtolle is probably right. And it wouldn't be the first time I overlooked the easy solution ;)

---

### Post by olavjunior on 2008-09-05
I'm actually having the same issue with transmission. I'm on a closed torrent network with a lot of seeders. But once in a while nothing happens in transmission, it just looks like it's off line. 

Also, when opening prefs and the port test is going, it just says "testing port" forever... and I mean forever, nothing happens! There's no output in terminal'

(I can download the same torrents in opera just fine at the same time)

EDIT: But somehow after a couple of hours, it connects and start downloading. But this takes a real long time, annoying!

---

### Post by MrWES on 2008-09-05
change the port to the next one up 51413 or whatever's next.

---

### Post by 7raTEYdCql on 2008-09-05
I think the only way is to keep trying for an open port. You can use an nmap scan on your own machine to find something like that. You will need to find an open port. That is it.

---

### Post by olavjunior on 2008-09-06
But the port's open. I don't get any message that the ports closed, it just hangs. And after a while (a long long time) it works normally again. And I've never had this problem before with Transmission. Maybe it's because I have the latest version

---

### Post by Kinetic_lord on 2008-09-06
Remove transmission and install it again... (i don't know the package name sorry!)

---

### Post by t0p on 2008-09-06
I don't trust the info you get about ports in prefs.  I've checked it before and it's come back saying ports are closed - when I'm actually downloading something!

I've also found, like the OP, it can take Transmission an awfully long time to start downloading.  But this is an intermittent issue - usually I have no problems with the app. Just the "port closed" lies.

---

### Post by olavjunior on 2008-09-06
The fact that you can download even if the port is closed isn't a bug, but a fact! You just won't be able to download from other people who have their ports closed, so you get less speed. (short - google it if you wonder)

EDIT: I've reinstalled transmission, but the bug's persistent. I guess it's just in version 1.33. Hope they fix this!

---

### Post by mixim on 2008-11-04
> **olavjunior said:**
> 
EDIT: I've reinstalled transmission, but the bug's persistent. I guess it's just in version 1.33. Hope they fix this!

Ok, so now 1.34 is out and how does it work for you?

 I have the same problem as you... No FW and no Router, just direct connection to the broadband socket in my wall.

"Testing port..." Goes on forever, no matter what port it is!
Torrents never start!

---

### Post by gandaran on 2008-11-04
install gufw firewall [http://gufw.tuxfamily.org](http://gufw.tuxfamily.org) and set up (open) transmission ports like this [http://img527.imageshack.us/my.php?image=screenshot7st4.png](http://img527.imageshack.us/my.php?image=screenshot7st4.png)

---

### Post by mixim on 2008-11-04
> **gandaran said:**
> install gufw firewall [http://gufw.tuxfamily.org](http://gufw.tuxfamily.org) and set up (open) transmission ports like this [http://img527.imageshack.us/my.php?image=screenshot7st4.png](http://img527.imageshack.us/my.php?image=screenshot7st4.png)

Many thanks, I'll try it!

But what the hell, does it mean that one HAS to have a firewall for it to work? As I said, I'm connected straight to the socket without any ports blocked.

---

### Post by philinux on 2008-11-04
I could not be bothered tinkering so I installed deluge and set it to use random ports. It works out the box.

[http://deluge-torrent.org/](http://deluge-torrent.org/)

---

### Post by mixim on 2008-11-05
> **gandaran said:**
> install gufw firewall [http://gufw.tuxfamily.org](http://gufw.tuxfamily.org) and set up (open) transmission ports like this [http://img527.imageshack.us/my.php?image=screenshot7st4.png](http://img527.imageshack.us/my.php?image=screenshot7st4.png)

Thanks man, I didn't do that but almost and it worked! Instead of downloading a Firewall I hooked up my router with a FW, it instantly worked. since UPnP is up and running, no matter what port i set up in transmission it worked.

Is this some kind of bug in Transmission? Why the hell would I need to have ports open or closed, aren't all ports open when connected straight to the socket?

---

### Post by faustus34 on 2009-05-20
I had the same issue. In my case, it was files that I had downloaded with deluge and wanted to continue with transmission. I changed the permissions on the files to full read/write and then they worked fine. I think somehow transmission needs the files to be fully read/write for all users or it won't work. I did set the user in the config file before as well. It might not solve the original problem, but perhaps someone else may find that information useful.

---

### Post by ashmew2 on 2009-05-20
Personal Opinion : I think you are FAR better off with using deluge-torrent than Transmission. And IMO , the Default should be Deluge or even rtorrent but they should remove Transmission in Karmic..

---

### Post by Astarroth on 2009-05-20
This kind of performance is the reason that I deleted it and install Deluge. Transmission is buggy at best in my dealings with it. 
Just my two coppers.:popcorn:

---

