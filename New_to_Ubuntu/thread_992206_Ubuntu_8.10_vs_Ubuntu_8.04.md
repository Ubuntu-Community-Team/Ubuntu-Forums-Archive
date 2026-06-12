---
title: "Ubuntu 8.10 vs Ubuntu 8.04"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by krtica on 2008-11-24
Are you having impression that Ubuntu 8.04 was more reliable than 8.10 ?
:confused:
Or is it just me...

---

### Post by Sorivenul on 2008-11-24
> **krtica said:**
> Are you having impression that Ubuntu 8.04 was more reliable than 8.10 ?
:confused:
Or is it just me...

8.04 is an LTS release, which means it will be supported longer, and by design will be somewhat more stable for many or most users.

8.10 ran just fine on my machine and was about equal to 8.04 for my purposes.  I'm running the Development Branch (Jaunty) right now, so I can't speak for the current place of either 8.04 or 8.10.  

In short, it's probably not just you.

---

### Post by LowSky on 2008-11-24
I had no issue with either

---

### Post by phidia on 2008-11-24
> **krtica said:**
> Are you having impression that Ubuntu 8.04 was more reliable than 8.10 ?
:confused:
Or is it just me...

If you're having specific issues it probably would be best to list them. Chances are people here can recommend things to try.

8.10 continued the change in xorg that was introduced in 8.04.
I and others helping here have seen various video problems as all of that change reveals itself-there are solutions so as I said just list the specifics.

---

### Post by krtica on 2008-11-24
I have some issues which I didn't had on Hardy...

- For example, I had IP locked to my MAC. Since I upgraded to 8.10 I can't go on Internet, but in local network I can reach all IPs. I can go on Internet only if I remove that option on server.

- My Remote desktop freezes when I change IP address (moving from one Access Point to another).

- Add-ons in Firefox are behaving crazy. :shock: And I can't use some embedded flash applications which was OK in 8.04.

etc.

I'm beginner and it's probably more to apps then OS, but it can be very annoying... And I really don't wanna go back to Windows, never again. :D So I'm trying to figure out what I did wrong... :-?

---

### Post by maybeway36 on 2008-11-24
Try these commands:
```
ping -c 1 4.2.2.1
ping -c 1 www.google.com
```
If the first one works but the second one doesn't, there is something wrong with resolving DNS names. 4.2.2.1 through 4.2.2.6 are all DNS servers you can use, although I'm not quite sure how to specify that in the settings.

---

### Post by kestrel1 on 2008-11-24
I had three machines running Hardy, as follows:
1) Main Desktop at home
2) Laptop Home & work
3) Secondary Desktop at Work

No.1 is still running Hardy
No.2 has been upgraded to Intrepid (only a few small problems
N0.3 was upgraded to Intrepid, but too many problems. Ended up installing Mandriva on it.
I think Intrepid works better on newer hardware, as the problems I had have been mostly down to driver incompatability.

---

### Post by mihaiv on 2008-11-24
++8.10 comes with Flash Player 10 which fixes the common crash problems of Flash 9 with Firefox 3.
++8.10 has fixed some compiz problems. Desktop effects work fine with full screen games.
--8.10 had a nasty bug with the CD-rom eject (the tray would open and close on eject). Fixed 10 days after release.
--8.10 has random system freezes, apparently related with compiz (at least on my system, but many people are complaining)
-+8.10 came with a fix for streamtuner to refer audacity instead of the burried XMMS. It also came with a bug that made audacity useles in that combination. Bug fixed a week after release.
--8.10 came with a new gcc compiler version. This is a version that breaks things and adds some rather non-conservative warnings (like warnings for not reading a return value for a function). The addition of a new libtool has its own set of problems (like not being able to compile new KDevelop projects).
--8.10 has many more bugs, like all software does. What makes 8.10 special is that its bugs look obvious to find on very simple use cases (like the default actions). The large number of regressions (things that used to work and don't anymore) shows that open source development is live and strong. Code changes at a high rate and side effects (like regressions) are almost inevitable.

---

### Post by krtica on 2008-11-24
I'm new to Linux/Ubuntu, but I have experience with network.
I still have dual boot and I test it with Windows and from Hardy Live CD - connection on Internet works.
But when I'm in 8.10 it's like all traffic is blocked by firewall or router. :-k
Also, I bought new laptop few days ago, and Interpid works out of box (except modem)...
I tried all those apt-get install options for cleaning and checking, maybe I done something wrong. :???:
What do you thing - should I reinstall 8.10, install 8.04 or something else?
:confused:

Thank you, mihaiv.

> --8.10 came with a new gcc compiler version. This is a version that breaks things and adds some rather non-conservative warnings (like warnings for not reading a return value for a function). The addition of a new libtool has its own set of problems (like not being able to compile new KDevelop projects).

That maybe can explain why I'm unable to compile driver for modem... :-k (Can it?)

---

### Post by Tomatz on 2008-11-24
> **krtica said:**
> Are you having impression that Ubuntu 8.04 was more reliable than 8.10 ?
:confused:
Or is it just me...

Arghh not another one of these. 

8.04 was buggy when it came out as was 7.10, 7.04 etc etc

Bottom line is, if you need your pc to be stable, do as i do and stay 6 months behind.

I only just upgraded to 8.04 and if i want bleeding edge software i just compile instead of using the repos.

Simple and NO complaining

;)

---

### Post by krtica on 2008-11-24
:D I'm not complaining. I'm still learning. :D
I'm just asking for opinion and advice.
Like you gave me.
:D

---

### Post by Francewhoa on 2009-05-12
Keep the 'complaints' coming krtica (joke :P). I agree that you were not complaining but asking a question :?: All questions are welcome.

To answer your question 8.04 LTS will have updates for three years after its release. LTS means _L_ong _T_erm _S_upport. In other words bug fixes and security updates for 8.04.x for 3 years after its release.

8.10 is a little different in the fact that a few new features are being introduced. Such as the new encrypted area for sensitive files. [http://fridge.ubuntu.com/node/1701](http://fridge.ubuntu.com/node/1701)

There is no big difference, and practically the same. I prefer to stick with 8.0.4.x LTS release because of the 3 years bug fixes and security updates and I don't need the new 8.10 features.

source and more info: [http://ubuntuforums.org/archive/index.php/t-961059.html](http://ubuntuforums.org/archive/index.php/t-961059.html)

---

