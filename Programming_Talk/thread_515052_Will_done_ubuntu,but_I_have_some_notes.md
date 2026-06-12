---
title: "Will done ubuntu,but I have some notes"
date: 2007-08-01
forum: Programming Talk
---

### Post by yadoo86 on 2007-08-01
Dear Ubuntu team,

Will done, for this nice and amazing Linux, really I liked,  easy,strong and provide very rich packages, 

But  I have some nice notes, I hope will be useful for updating process and make Ubuntu #1 in Linux world:

1-As Java Developer, Ubuntu provide very nice packages  like Netbeans IDE, Eclipse IDE, Glassfish ...etc, But some of this package now is out of date  for example:

-Eclipse 3.2 (new version is Eclipse 3.3 called Europa).
-Netbeans 5.5(new version is Netbeans 5.5).
-Glassfish AS 1 (new version is 2 )
Note: there are lots of different between these versions.

2-I notes that Ubuntu don't provide and tool for firewall,I don't know why but I sure Firewall is very important.

3-When I tried to install  Nvidia drive for my graphic card (7200),after I restart my laptop, X window error massage will be appear. :(
,The reason for this: 7200 is not in Nvidia support list drives. I hope this drive will be add in the future. :) 

Sorry for my English grammar.
Best Regards

Yad Swdad Tahir

---

### Post by brooksbp on 2007-08-01
1) Many of those versions are only a rev behind--not as bad as you think.  Plus, you can build them all yourself.
2) There are firewalls, just take some time to do a search.
3) Yes that card is supported under nVidia drivers, just do a little research.

Ubuntu isn't a 'support everything out of the box' OS.  It's amazing, but it wont wipe your *** for you.  Just spend a little time doing research on what's available before posting like this.

---

### Post by SomethingUniqueHere on 2007-08-01
1 -  No ones stopping you from compiling from source, i use the latest and greatest version of eclipse at work.  Eventually the newer versions make their way to the repository but it takes time. 

2 - Iptables my friend.  Also, if security is a concern of yours check out Bastille (sudo apt-get install bastille).

3 - I'm optimistic theres going to be much better display drivers coming.  AMD is big on open source and they recently acquired ATI.  There has been some talk about ATI releasing some open source code.  This would pressure nvidia to do the same, although, i've ran two generations of nvidia cards on multiple linux distros and i've never had a complain, could be that i'm just lucky

Anyways, glad to hear you like the distro too.  Hope my comments were of some help

---

### Post by pmasiar on 2007-08-01
I am not from Ubuntu team, but I use Ubuntu daily, and I am glad you like it too :-)
> **yadoo86 said:**
> make Ubuntu #1 in Linux world:

According to [http://distrowatch.com/](http://distrowatch.com/), Ubuntu is still safely #1 Linux distro. Looks like many new converts don't know about that site, but users of every other distro do, and vote *their* distro up :-) hint hint :-)

> 1-As Java Developer, ...some of this package now is out of date  ...

Goal of Ubuntu is not to provide you the newest single app - you probably want gentoo for that, or just compile from sources. IIUC, goal is to provide reasonably recent apps for wide spectrum of desktop users. I like Ubuntu because I have decent apps, they work together, and it is zero bother for me to install it - It Just Works (tm) :-) 

Compared to that, on Windows, I need to research which version libraries I have, what JVM version want different apps (Tomcat, Eclipse, etc), and do it properly, and hope there would be no clash between installed libraries - I have horror stories. On ubuntu, someone made all those decisions for me, solved all dependencies. Maybe I don't have version released 2 weeks ago, but I don't need to worry that my install will break some other app I forgot to check.

> 2-I notes that Ubuntu don't provide and tool for firewall,

iptables are installed by default, thats why you did not noticed.

[http://www.google.com/search?q=ubuntu+firewall](http://www.google.com/search?q=ubuntu+firewall) has many more options

Of course it is additional work - security is not about the convenience, right?

> 3-When I tried to install  Nvidia drive for my graphic card (7200)

Nvidia is non-free driver, and as such will always have a problems (we don't have sources, see? :-) ) There are many options: install better drivers, or use video cards from manufacturers who work better with free software community.

[http://www.google.com/search?q=ubuntu+nvidia](http://www.google.com/search?q=ubuntu+nvidia)

> Sorry for my English grammar.

Your grammar is OK enough, you don't need to apologize for it. Many forum members (including me) learned English as second (or 3rd :-) ) language. You probably know more other (non-english) languages than half of the forum participants :-)

---

### Post by vexorian on 2007-08-01
1. for up to date packages you might wish to use backports, download updated .deb or source packages

2- By default ubuntu doesn't have open ports so firewall is not needed until you open a port, in reality the linux kernel has some internal firewall, you can configure it using **firestarter** look for that package in synaptic.

3. Hopefully, some recent upgrades to the Linux kernel might make things easier for third party drivers.

---

### Post by yadoo86 on 2007-08-02
Thanks for kind replay,

> No ones stopping you from compiling from source, i use the latest and greatest version of eclipse at work. Eventually the newer versions make their way to the repository but it takes time.
Sure,

> There are firewalls, just take some time to do a search.
But my question why ubuntu not contain built-in firewall.I think this will be better, Isn't it???

> 
By default ubuntu doesn't have open ports so firewall is not needed until you open a port
This is good news,

> Yes that card is supported under nVidia drivers, just do a little research.
Can u give some resource so much, but Always I got error message

Best Regards

---

### Post by yadoo86 on 2007-08-02
> 
Hopefully, some recent upgrades to the Linux kernel might make things easier for third party drivers.

Thank so much vexorian, After I install new kernel, Nvidia drive card has been installed successfully,

Thank u sooooooooooo much.:KS

---

### Post by Selage on 2007-08-02
Cant "envy" solve your issue with your NIVIA drivers?

Edit:

Already fixed, sorry for the trouble

---

### Post by sliwowitz on 2007-08-08
If you are looking for a simple and easy to use firewall GUI, check out firestarter.
```
sudo apt-get install firestarter
```

---

### Post by AlexThomson_NZ on 2007-08-08
> **yadoo86 said:**
> 1-As Java Developer, Ubuntu provide very nice packages  like Netbeans IDE, Eclipse IDE, Glassfish ...etc, But some of this package now is out of date  for example:

-Eclipse 3.2 (new version is Eclipse 3.3 called Europa).
-Netbeans 5.5(new version is Netbeans 5.5).
-Glassfish AS 1 (new version is 2 )
Note: there are lots of different between these versions.

2-I notes that Ubuntu don't provide and tool for firewall,I don't know why but I sure Firewall is very important.



1. If you need the very latest versions of these apps, you will have to download them and install them yourself, rather than use Synaptic (I would probably recommend doing this with ANY Java app anyway, and avoid the gcj-compatibility fluff altogther).  You won't need to compile from source

2. I agree.  Any distro should be shipping with an activated firewall (even if it is set to be very permissive by default).  The fact that you have to pay for this essential feature in Windows makes this an attractive point of difference in Ubuntu (and all other distros, obviously)

---

### Post by slavik on 2007-08-09
> **AlexThomson_NZ said:**
> 1. If you need the very latest versions of these apps, you will have to download them and install them yourself, rather than use Synaptic (I would probably recommend doing this with ANY Java app anyway, and avoid the gcj-compatibility fluff altogther).  You won't need to compile from source

2. I agree.  Any distro should be shipping with an activated firewall (even if it is set to be very permissive by default).  The fact that you have to pay for this essential feature in Windows makes this an attractive point of difference in Ubuntu (and all other distros, obviously)
about #2, windows has a built in firewall (how good/effective it is, is not the point of this discussion :P)

by default (in ubuntu), there are no ports open, why do you need a firewall? (in the case with windows, it has some ports open by default)

---

### Post by Chilongola on 2007-08-09
I have been dealing with Ubuntu for about 6 weeks now.  I have found it to be very stable.  Need to add 512 more memory though.  Personally i am into Lotus smart suite, Word Perfect x3 etc.  The only thing for Microsoft is the operating system Win XP.  As soon as I get everything to work on this rig with Ubuntu I will then install it on my main PC.  I firmly agreee with all the comments above.  The author may have had a certain "Tone" but I am sure he was trying to say "well done Ubuntu"
I love the part about no "real" need for firewall.  I use "firestarter" .  Just for a measure "added security".  I have not installed any device driver other than the one than the ones I am working on right now which is Pctell and or Agere.  No other device giving me one ounce of trouble.
So, I join all and also say "Well done Guys!!  Ubuntu from now on....:guitar:
Cheers!!:popcorn:

---

### Post by ubuntu27 on 2007-08-09
Guys/gals. There is a built-in Firewall in Ubuntu. It's called iptables. 
Do a search in this forum about iptables :)

---

### Post by AlexThomson_NZ on 2007-08-09
> **slavik said:**
> about #2, windows has a built in firewall (how good/effective it is, is not the point of this discussion :P)

by default (in Ubuntu), there are no ports open, why do you need a firewall? (in the case with windows, it has some ports open by default)

Hey, you are right, I did a Google, and windows does indeed come with a firewall- don't know where I got the idea it didn't (I thought it was part of a pack with AV tools you have to pay extra for! doh!)

Is that true that by default most ports are blocked?  I haven't been using Ubuntu that long, but I haven't had any issue with blocked ports using various web apps, DBs, etc.

While using iptables may do the job, let's face it, it's a black art for many and not something maybe the average Linux user would spend time configuring, whereas a nice GUI app in the menu would be so much more accessible.

---

### Post by slavik on 2007-08-09
> **AlexThomson_NZ said:**
> Hey, you are right, I did a Google, and windows does indeed come with a firewall- don't know where I got the idea it didn't (I thought it was part of a pack with AV tools you have to pay extra for! doh!)

Is that true that by default most ports are blocked?  I haven't been using Ubuntu that long, but I haven't had any issue with blocked ports using various web apps, DBs, etc.

While using iptables may do the job, let's face it, it's a black art for many and not something maybe the average Linux user would spend time configuring, whereas a nice GUI app in the menu would be so much more accessible.
```
sudo apt-get install firestarter
```

nice enough for ya? :)

---

### Post by AlexThomson_NZ on 2007-08-09
Thanks Slavik.

I'm actually aware of this great app, my point is that it should be installed by default in Ubuntu.  Although iptables may be offer more advanced functionality, a very simple frontend (even if it is a little more limited) would make firewalls more accessable to the average user, who might not otherwise bother.

---

### Post by slavik on 2007-08-10
how is fire starter limited?

---

### Post by ubuntu27 on 2007-08-11
> **AlexThomson_NZ said:**
> Hey, you are right, I did a Google, and windows does indeed come with a firewall- don't know where I got the idea it didn't (I thought it was part of a pack with AV tools you have to pay extra for! doh!)

Is that true that by default most ports are blocked?  I haven't been using Ubuntu that long, but I haven't had any issue with blocked ports using various web apps, DBs, etc.

While using iptables may do the job, let's face it, it's a black art for many and not something maybe the average Linux user would spend time configuring, whereas a nice GUI app in the menu would be so much more accessible.

Windows' Firewall is the worst firewall. It actually doesn't block anything. Windows users should use other software firewall like ZoneAlarm or a hardware firewall. 
PS. Windows Firewall comes with Windows XP SP2 (There is also in SP1, but much more useless)

---

