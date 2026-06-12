---
title: "HOW TO: Install Nicotine 1.0.8c"
date: 2005-01-26
forum: Outdated Tutorials &amp; Tips
---

### Post by clparker on 2005-01-26
**N**icotine is a Linux P2P file sharing client that logs into the soulseek network. It's ability to 'Download Containing Folder(s)' is amazing as the program with simple ease allows you to download entire albums, or even an artist's complete discography. It's features are geared towards music, and it lets you set up a buddy list so you can begin trading your favorite music who share your interests. It's fair to say that the soulseek network with it's privlidged user status makes the Napster of days ago look like a baby's toy. 
Now many have used:
```
	sudo apt-get install nicotine
``` 
to get the 1.0.7 version default with Ubuntu 4.10 'Warty Warthog'
However if you follow these steps you *should *be able to get the latest version running on your system.
(right click > copy link locataion)
```
sudo wget [http://archive.ubuntu.com/ubuntu/pool/universe/n/nicotine/nicotine_1.0.8rc1-1.1.diff.gz]("http://archive.ubuntu.com/ubuntu/pool/universe/n/nicotine/nicotine_1.0.8rc1-1.1.diff.gz") 

``` 
(right click > copy link locataion)
```
sudo wget [http://archive.ubuntu.com/ubuntu/pool/universe/n/nicotine/nicotine_1.0.8rc1-1.1.dsc]("http://archive.ubuntu.com/ubuntu/pool/universe/n/nicotine/nicotine_1.0.8rc1-1.1.dsc") 

``` 
(right click > copy link locataion)
```
sudo wget [http://archive.ubuntu.com/ubuntu/pool/universe/n/nicotine/nicotine_1.0.8rc1.orig.tar.gz]("http://archive.ubuntu.com/ubuntu/pool/universe/n/nicotine/nicotine_1.0.8rc1.orig.tar.gz") 

``` 
```
	dpkg-source -x nicotine_1.0.8rc1-1.1.dsc
``` 
```
	cd nicotin*
``` 
```
	sudo dpkg-buildpackage -d
``` 
```
	cd ..
``` 
```
	sudo dpkg -i nicotine*.deb
``` 
You should see Nicotine in your Applications > Internet. If not reboot. Your gonna need to simply just make up a user name and password under File > Settings.
Once you run a search and find something you like, download the whole album, and once you get a good reputation on the network, you can download whole discographies.
For more information see [http://nicotine.thegraveyard.org/]("http://nicotine.thegraveyard.org/")

---

### Post by az on 2005-01-26
You do not need to sudo to wget the packages.  You should just wget them normally, or just click on the links in your HOWto.

Also, what ports does one need to open from behind a firewall?

Thanks!

---

### Post by keyshawn on 2005-01-26
I'm confused why it requires 3 different packages to be downloaded. A .deb in the backports project would be much appreciated and easier for the casual user :)

---

### Post by clparker on 2005-01-26
Ask the backports people for a nicotine backport. but see there is a catch, see nicotine 1.0.8c needs the new python, and well it's complicated, this is the best way to FORCE it to do the new nicotine.

---

### Post by az on 2005-01-26
"I'm confused why it requires 3 different packages to be downloaded"

That is a good question.

These are free software projects distributed by source code.  You must always be able to get the source for the binary package you use.

The original source is the orig.tar.gz file.  The different additions and/or changes made to make it work in Ubunt are in the .diff.gz file and the .dsc is the description in the package database (Packages.gz)

Please go ahead and ask the backport people if they want this package.  It seems easy to maintain.

---

### Post by keyshawn on 2005-01-26
[QUOTE=clparker]Ask the backports people for a nicotine backport. but see there is a catch, see nicotine 1.0.8c needs the new python, and well it's complicated, this is the best way to FORCE it to do the new nicotine.[/QUOTE]

On the official site - [http://nicotine.thegraveyard.org/changelog.php](http://nicotine.thegraveyard.org/changelog.php) - The changelog states the last update was all the back in may 2004...Am I missing some news/info [ref: the new nicotine] ?

thanks,
keyshawn

---

### Post by keyshawn on 2005-02-12
Well, I installed it, according to the directions and no problems during the installation. 
However, I'm unable to connect to the server....The status in the lower left-hand corner just says "Listening on port 2234"

Any help would be appreciated,
keyshawn

PS - thanks to parker for the directions !

---

### Post by paul cooke on 2005-02-12
[QUOTE=keyshawn]Well, I installed it, according to the directions and no problems during the installation. 
However, I'm unable to connect to the server....The status in the lower left-hand corner just says "Listening on port 2234"

Any help would be appreciated,
keyshawn

PS - thanks to parker for the directions ![/QUOTE]

have you opened port 2234 on your firewall to incoming connections???

---

### Post by bored2k on 2005-02-24
[QUOTE=paul cooke]have you opened port 2234 on your firewall to incoming connections???[/QUOTE]


Soulseek has 2 servers working on 2234 and 2240 occasionally [sometimes sseek 2234 crashes] .

But it has a nack for  sometimes listening on 2236 server .

So yall should forward 2234, 2236 and 2240 .

---

### Post by paretooptimum on 2005-03-09
I've put a page on the wiki on filesharing. Can you all please contibute to it and make it better.

[http://www.ubuntulinux.org/wiki/FileSharing](http://www.ubuntulinux.org/wiki/FileSharing)

Add How-To's to the page, etc

---

### Post by xNight Wraithx on 2005-03-29
I have it all downloaded and it says listening on port 2234 but then next to it it says offline and I can't connect. Also, I don't have a firewall. any advice? Thanks in advance.

---

### Post by bored2k on 2005-03-29
[QUOTE=xNight Wraithx]I have it all downloaded and it says listening on port 2234 but then next to it it says offline and I can't connect. Also, I don't have a firewall. any advice? Thanks in advance.[/QUOTE]
 xDSL ? Be sure you port forward 2234 -not really needed to connect-.
Also , go to the options menu and select the 2nd server [the one working on port 2240 and retry -- sometimes crappy Soulseek servers won't work ] .

---

### Post by xNight Wraithx on 2005-03-29
all that i know is that I have SBC/Yahoo DSL not sure the difference. This is what I did:
File-->Settings--->Server-->

I only have two choices here:

server.slsknet.org;2240

and

server.slsk.org;2240

I chose the second one as suggested.

Character encoding: utf-8

Ports: Set to 2234


You know what...nevermind, it started working but it still suggested that I update. can I just 

$ sudo apt-get autoupdate to get it  or upgrade?

---

### Post by jeffblack on 2005-06-01
Actually, going back to this thread...

Nicotine was previously working for me, except that occaisionally it would go all freezy-freezy on me. Reopening it, it would have this problem. Then if I closed it and reopened again, it would erase all my previous settings, and upon filling them out again, it would miraculously work again. Very odd.
However, the erasing of the fields and miraculous reworking part no longer occurs. Nothing to do with servers has been changed. Perhaps nicotine is just experiencing a little bug?

---

### Post by misfito on 2007-04-18
How to upgrade from 1.0.8rc1 to 1.0.8 (I'm not sure if they're the same) I already download the nicotine-1.0.8.tar.gz, what should I do next?

---

### Post by gyyug78fg87ogguiioioioioi on 2011-03-26
how to connect?? i typed in username and password but i am not getting connected, how do i do it

---

