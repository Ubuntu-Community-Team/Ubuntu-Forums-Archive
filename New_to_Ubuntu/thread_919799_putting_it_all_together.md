---
title: "putting it all together"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by mdraicch on 2008-09-14
Hi to all,

I'm having alot of trouble following forum posts because I do not know how ubuntu is structured.  For example, I read conversations about xorg and mesa and what seem to be components of these or other parts of ubuntu, but I cannot follow the conversation because I don't know how it goes together, what talks to what and how.

Is there some documentation somewhere that visually puts these and other parts of the system together, providing an aerial view and whatever other detail?

Many Thanks
Muzza

---

### Post by markbuntu on 2008-09-14
If you find one, come back here and tell us.

---

### Post by k33bz on 2008-09-14
WOW, 

there is loads of information, litterally thousands. Any where from Linux books, to pages on the internet.

---

### Post by R_T_H on 2008-09-14
I doubt it; there's so much, and it all changes so fast. Best just to learn by doing with Linux, I find.

---

### Post by SunnyRabbiera on 2008-09-14
[http://en.wikipedia.org/wiki/X.Org_Server](http://en.wikipedia.org/wiki/X.Org_Server)

[http://en.wikipedia.org/wiki/Mesa_3D](http://en.wikipedia.org/wiki/Mesa_3D)

---

### Post by mdraicch on 2008-09-15
[LEFT][/LEFT]
Hi to all,

Thankyou for your replies, I can see that this sort of doco is not readily available. 

This sort of doco needs to come from the developers, in particular, someone who has been with the project from the beginning, but I suppose that they are all to busy developing to be bothered with producing this type of doco.

Never mind I'll just keep looking.

Regards
Muzza

---

### Post by northern lights on 2008-09-15
[https://help.ubuntu.com/community/]("https://help.ubuntu.com/community/")

[psychocats.net]("http://psychocats.net/ubuntu/index.php")

[linuxcommand.org - learning the shell]("http://www.linuxcommand.org/learning_the_shell.php")

---

### Post by bab1 on 2008-09-15
> ...I can see that this sort of doco is not readily available.

This sort of doco needs to come from the developers, in particular, someone who has been with the project from the beginning, but I suppose that they are all to busy developing to be bothered with producing this type of doco.

The biggest problem for new users of any technology is understanding that most technology is not monolithic, but rather, that it is layered and many times fragmented.  It is the nature of the beast.  By that I mean a developer of a "recording application" (Audicity comes to mind) does not have to know anything about networking.  A developer working for a hardware manufacturer does not need to know anything about network security.

So when you say "they are all to busy developing to be bothered"; a pejorative comment to say the least, you are wrong!

The Ubuntu product itself is not run by or controlled by any single entity.  There are upstream OS Kernel developers, X-server and Windows managers (X-org, Gnome and KDE ) Mail servers and clients, Web servers and browsers, file servers and all manner specialized applications.  All independent and available for you  to research and tinker with.  

Most of use have our areas of expertise.  The general subject is just too big to understand completely, let alone, keep up with the latest developments in the individual areas.

Find an area that interests you and dig in!

---

### Post by t0p on 2008-09-15
> **bab1 said:**
> 
Find an area that interests you and dig in!

Alternatively, don't!  I know very little about how anything in linux works.   I've learnt some bash, but mostly I get by clicking menus to see what happens and struggling through man pages.  Exploring is good.

---

### Post by markbuntu on 2008-09-15
You should find an old copy of Running Linux and read it. It is old and a lot of it is outdated for specifics but it will give you a very solid grounding in basic linux structure and operation.

---

### Post by mdraicch on 2008-09-15
Thanks t0p

For the most part thats all I do, is just point and click and most of the time it works OK.  What dosen't work I ignore and if I can't ignore I change linux until I find one that runs the required application. But, the nature of the beast is that from time to time you need to get into the guts and dig, without some idea of whats going on its difficult to do anything successfully. 


Thanks bab1

Yes, I have already discerned that the complete package called UBUNTU is a mass of many smaller sub-systems put together and that no one person can understand it all.  This is also the reason why LINUX isn't advancing as it should, don't get me wrong, its going along well, buts its not that good yet.

If I was to say to myself that I want to create application A and I don't want to develop all the sub-systems to create application A I would pull together a lot of pre-written smaller applications and put them together and most probably just write something to run each smaller app at the required time, you would recognize that there are lots of apps written this way, for example DEVEDE.

Before I could write this app I would have to design it and plan how to use all the smaller apps and also how the apps would pass data, etc...   To do this I would draw diagrams, first a helicopter view of the complete system and then I would start to break down the sub-systems into smaller sub-systems and applications and just keep going until the job was done.  If I can't do it on paper then I can't do it for real.

I just want to see some of this documentation, if it is available and of course if it is not confidential.


Regards
Muzza

---

### Post by Mornedhel on 2008-09-15
> **mdraicch said:**
> Before I could write this app I would have to design it and plan how to use all the smaller apps and also how the apps would pass data, etc...   To do this I would draw diagrams, first a helicopter view of the complete system and then I would start to break down the sub-systems into smaller sub-systems and applications and just keep going until the job was done.  If I can't do it on paper then I can't do it for real.

No *serious* dev team doesn't do this. It certainly happens in Free Software communities, but it happens in professionnal environments as well.

Also, all documentation, API or whatever, for all Free Software applications, is freely available when present. If it is not, ask the dev team.

---

