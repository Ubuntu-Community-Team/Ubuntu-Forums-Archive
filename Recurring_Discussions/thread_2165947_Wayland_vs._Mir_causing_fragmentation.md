---
title: "Wayland vs. Mir causing fragmentation??"
date: 2013-08-07
forum: Recurring Discussions
---

### Post by inte2 on 2013-08-07
Hey,

I got some questions regarding Canonical implementing Mir in Ubuntu, instead of Wayland (as all other distributions).
As far as I understand, both (Mir and Wayland) can run X-Windows-programs through a nested X-server.
However, since all Linux distribution except for Ubuntu have chosen Wayland as successor for X (even Kubuntu!!!) - will programs compiled against Wayland still run on Mir?
If not, who is going to port all the famous Linux tools to Mir? Or will Canoncical encourage the developers to stay with X-Windows, since both, Mir and Wayland, feature a nested X-server?
What about commercial apps, e.g. Steam? Will Steam support Wayland, Mir or even both?
How will Ubuntu support commercial apps when they were built against Wayland and even Canonical can't grep the code? A nested Wayland-server?
What about the other way round? It is feasible that Steam will be released for Mir, since there is already a close collaboration between Valve and Canonical. Will Canonical develop a nested-Mir-server that Wayland users will still be able to use Steam?
Both, Mir and Wayland, can address Android binary graphics drivers. Does that meand binary divers are interchangeable between Mir and Wayland in general?
Or, in brief: Why has Canonical chosen Mir at all, since things might become more complicated with forking the whole display environment, possibly ending in Ubuntu being as incompatible to Linux/LSB as Android - and who really needs a second Android?

Thanks for your comments,

 Chris

---

### Post by 3rdalbum on 2013-08-07
Programs are not compiled against X, Mir or Wayland.

Programs are compiled against GUI toolkits like GTK and QT. The toolkits handle the task of communicating with the window manager and the display server. As long as the toolkits support all three display servers, and you are running an appropriate window manager, everything will be interoperable.

Games don't use toolkits, but they do use LibSDL. As long as LibSDL supports Mir, Wayland and X everything will be interoperable.

I think this thread will get sent to Recurring very shortly.

---

### Post by grahammechanical on 2013-08-07
Fragmentation is in the genetic make-up of Free and Open Source Software. We would not have FOSS if Richard Stallman did not disagree with his employers as to how software should be developed and distributed. That was the beginning of fragmentation. Whenever developers of FOSS disagree the FOSS universe fragments. "Fork the code" is a basic human right of FOSS programmers. Weyland is fragmentation. Have you complained about that? No of course not.

Did Mark Shuttleworth complain of fragmentation when people took Ubuntu and turned it into Kubuntu, Xububtu, Lubuntu as well as other Linux distributions that have moved the Ubuntu code too far away from Ubuntu to be part of the Ubuntu family? Fragmentation is an accepted price that is paid when code is licensed as open source.

The reasons for developing MIR are publicly available. All you have to do is read the blogs of Mark Shuttleworth, Jono Bacon and others directly involved in coding MIR. As today is the day when I play at being Mr. Nice, I give you one link.

[http://www.markshuttleworth.com/](http://www.markshuttleworth.com/)

It is not for Ubuntu to support commercial applications. The owners of commercial applications are responsible for making sure their code is compatible with Ubuntu. Otherwise they lose customers. And they lose profits.

I have Saucy Salamander running with Xmir in Ubuntu, Kubuntu, Xubuntu, Lubuntu and Ubuntu Studio. And there is no issue with applications at all. Right now I am posting from Saucy Salamander Ubuntu+Xmir. Yesterday I tested a Xubuntu-Xmir ISO image. The live session runs on Xmir. The installed Xubuntu runs on Xmir. The platform is stable. And if the OS is unable to run on Xmir for any reason, it falls back to Xserver and the user does not notice a thing. And that is as it should be.

Regards.

---

### Post by inte2 on 2013-08-07
> **3rdalbum said:**
> Programs are not compiled against X, Mir or Wayland.

Programs are compiled against GUI toolkits like GTK and QT. The toolkits handle the task of communicating with the window manager and the display server. As long as the toolkits support all three display servers, and you are running an appropriate window manager, everything will be interoperable.


Thank you both for your fast reply!
Since Unity is switching to Qt, and Qt is supported by Wayland, does that mean it will be possible to install a basic Ubuntu/Mir-release, uninstall Mir and install Wayland instead and everything keeps working?
That would be amazing!

Thank you in advance!

---

### Post by 1clue on 2013-08-07
+1 on what 3rdalbum said.

I would call it competition, not disagreement.  When several teams have specific ideas about which way to solve a problem, you get several different products.  Sometimes one is very obviously better in the real world, and the others fall away because nobody uses them, and sooner or later the developers find something better to do.  Sometimes you get two or more good tools, each of which has a specific use case where it excels but none comes out as a clear winner in every case.  Then you have 'competing' products, or as users would call it, several choices in a list, which can be used to solve a certain problem as best fits your needs.

Think of mail servers.  There are a bunch of them, and some are just a simple tool to mail warnings on a server to the admin, and others are able to handle thousands of accounts with lots of extras.  Which one is better?  Depends on what you want to do.

Or, for a more mainstream comparison, how about web browsers?  Firefox, Internet Explorer, Chrome, Opera, and a few dozen others.  Ask a thousand nerds which one is better and you'll get a lot of the mainstream ones and probably a couple you hadn't heard of before.

This mir/wayland thing is not bad.  Two teams have envisioned solutions to a problem that needs to be solved, and both will be implemented so as to be more or less seamless across the network, and either one will reign supreme or both will coexist smoothly.  I expect lots of bumps on the road along the way, but it will get there.

---

### Post by cariboo on 2013-08-08
Moved to recurring, as this has been discussed to many times to count.

---

