---
title: "Ubuntu as a firewall"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by PegMonster on 2008-06-15
Hi all

I still have a lot to learn about linux and computing in general so please excuse my lack of knowledge.

I am wanting to use Ubuntu on a spare computer to act as a firewall and server/router for 3 other computers I have, 1 desktop (ubuntu/vista), and 2 notebooks (1 kubuntu/vista, 1 xp).
Although I would like to set up a server for business later on, it is not a priority at the moment. One step at a time I guess. As I said already, I still have a lot to learn.

The problem is that I don't have enough understanding to know where to begin.
So, where do I start and what are the potential problems with my setup?

I am ready to install whatever on the spare computer but am not sure whether I need to install a server platform or whether I am better off installing a desktop platform for ease of use. If I am better off with without a GUI then so be it.
Or do I forget about using Ubuntu and use something more dedicated to being a firewall?

At the moment I just have a Xyxel modem/wireless router feeding everything. Does that now become used only as a modem, unused as a router with the new box becoming the router?

Hope this doesn't sound too confusing, I know what I am after I just don't know how to translate my vision :P

Any help is appreciated.
Cheers

PegMonster

---

### Post by tubbygweilo on 2008-06-15
A good place to start looking for information about firewalls and security in general when using Ubuntu is to be found at [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=765421") sticky. 
The firewall section should give you some information, answer a few of your questions and give you pointers for further research on the subject.
Some might suggest that firewalls and their like would be best addressed by some for of [BDS]("http://daemonforums.org/") offering but I think it is best to see what Ubuntu has to offer before exploring other areas.

---

### Post by MattBD on 2008-06-15
I'm not sure I'd want to use Ubuntu as a firewall. You might be better off using a dedicated firewall distro - there's plenty on [http://distrowatch.com/](http://distrowatch.com/) and [Smoothwall]("http://www.smoothwall.org/") is one I've heard good things about.

---

### Post by Barrucadu on 2008-06-15
OpenBSD is very secure - but is quite unlike Linux, so I would recommend going with a firewall-based distro unless you are feeling particularly adventerous.

---

### Post by PegMonster on 2008-06-15
OK, thanks for the info. I will check out the forums some more.

So far there's some negative response for Ubuntu, but no one has told me why.
What is it about Ubuntu that makes it a bad choice?

Thanks again.
J

---

### Post by MattBD on 2008-06-15
I don't think there's anything wrong with Ubuntu as a firewall, it's just that if there's dedicated firewall distros they are likely to be easier to use in that role.

---

### Post by PegMonster on 2008-06-15
No worries, that makes perfect sense!

So when I finally venture into the world of servers, am I better off using the server as a firewall also or should I have a dedicated firewall before the server on the network?

I am just thinking If the former is the way to go, then I might as well try setting up a server while I am at it.

Anyway, I will keep on researching.

Thanks again.
J

---

### Post by MattBD on 2008-06-15
Well, there's certainly no harm in trying if you're going to do a fresh install anyway - if you can't get Ubuntu working as a server and firewall then, you can have something like Smoothwall as a back up plan. Ubuntu is pretty decent as a server, and there's plenty of documentation about, so you shouldn't run into any intractable problems if you do choose to use Ubuntu to set up a server.

---

### Post by Agreken on 2008-06-20
The problem I have is that Smoothwall or IPCop don't provide any options for 3G USB modems (specifically, Sprint 595u) and their community isn't nearly as helpful as Ubuntu's. I posted a question of how to get the floppy drive to work so I could copy the Sierra drivers over and all I got 5 flame responses wanting to know why I wanted to use the floppy like I'd asked how to breach the Pentagon...

If anyone knows a firewall product that works with Wireless USB modems like the Sierra 595u please let me know.

---

### Post by hyper_ch on 2008-06-20
well, you'll need to have at least two network cards in that server if you want it to act as firewall :)

---

### Post by Agreken on 2008-06-26
So I can't route and firewall from my Sprint USB modem to an internal LAN connection?

---

### Post by hyper_ch on 2008-06-26
well, a modem has two different "port"... on uplink and one for the lan... so you have "two network cards" in there ;) but you can't just use an old desktop computer with only 1 card as firewall... you'd need to add a second one ;) you know now what I mean?

---

