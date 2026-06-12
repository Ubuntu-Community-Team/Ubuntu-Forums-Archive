---
title: "New Ubuntu user trying to compile program"
date: 2016-07-26
forum: New to Ubuntu
---

### Post by asterics on 2016-07-26
Hi guys, new to Linux/Ubuntu - lifelong Windows/DOS user (sorry :/)

I have a program for mining Steem installed ([www.steemit.com](www.steemit.com)). I followed a guide to install this, it worked; but the guide didn't explain what any of the commands actually did.

They have just updated the source code and I need to upgrade to 0.12.2    [https://github.com/steemit/steem/releases](https://github.com/steemit/steem/releases)

Can anyone tell me how I install this so it actually works? xD  

Thanks!!

---

### Post by mastablasta on 2016-07-26
their source file has missing instructions for ubuntu. or rather they are incomplete. they do have a short item in build_ubuntu.md file.

otherwsie the procedure is same as you used before. you just might need to change some version data. 

Read also the comments sections: [SIZE=2]https://steemit.com/steemhelp/@proctologic/easy-install-steemd-in-ubuntu
[/SIZE]

[SIZE=2]

[/SIZE]

---

### Post by asterics on 2016-07-27
That worked really well, thanks :D

Is there somewhere where I can learn how to do this with without relying on someone making a guide???

---

### Post by mastablasta on 2016-07-27
all programs installs from osurce follow a similar method. the method is the same if oyu install form source in windows. you need dependencies first, then you compile it.

in linux the better method is:
- install preconpile dporgrams from software repositories (software center).
- use a personal repository (PPA) - less secure but should still be ok.
- the developer packaged it into a .deb file that works on all debian based distros (you have to trust that the file is form the developer)
- find a binary, unpack and run it (kind of line windows.exe - again not secure)
- new method is snap packages if the program has it. it's a sandboxed application. and there is another similar one but i forgot what it's called.

however many programs do not have these options but they do have the source. in which case one has to install from source or follow the instructions to setup some private repository to pull the updates from them. alternative in this case is to ask developers to create a PPA for Ubuntu or at least a .deb package.

---

