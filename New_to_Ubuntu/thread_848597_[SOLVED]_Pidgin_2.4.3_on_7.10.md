---
title: "[SOLVED] Pidgin 2.4.3 on 7.10?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by StOoZ on 2008-07-03
is it possible? (with working ICQ of course...)
tried compiling it few weeks ago , It insisted that I dont have tons of dependencies .... is there any walk-through for installing 2.4.3 on 7.10??

---

### Post by k3lt01 on 2008-07-03
Mate, I tried installing it on 8.04 and it just kept coming back "cannot find make file". I don't know what the issue is but I'll keep trying cause I need ICQ to chat with some friends.

---

### Post by whitethorn on 2008-07-03
As far as I've read, pidgin fixed the icq in 2.4.3 .  I don't know if it's true yesterday I had to compile it and I patched it myself. It works now, but it was really annoying finding all the dependencies took me like 30 min.  Neway there are a couple work arounds you can try

Here's one

[http://ubuntuforums.org/showthread.php?t=847240](http://ubuntuforums.org/showthread.php?t=847240)

and here

[http://ubuntuforums.org/showthread.php?t=846473](http://ubuntuforums.org/showthread.php?t=846473)

Hope this helps.

---

### Post by chrisccoulson on 2008-07-03
AFAIK, there is an update to Pidgin in gutsy-proposed at the moment. I don't think it is version 2.4.3, but I think it does have the ICQ patch applied (just in case this is all you need). Have a look at [bug 244591]("https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/244591/")

For help in enabling the -proposed repository, please have a look at: [https://wiki.ubuntu.com/Testing/EnableProposed]("https://wiki.ubuntu.com/Testing/EnableProposed"). This guide will work for Gutsy as well as Hardy (remember to replace 'hardy' with 'gutsy'). Please remember that this is a testing repository, so you should normally only use it if you wish to test updated packages. There is a higher risk of broken packages in this repository.

---

### Post by sayakb on 2008-07-03
You may also get Pidgin 2.4.3 for Gutsy from here: [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

---

### Post by chrisccoulson on 2008-07-03
> **LinuxIsInnovation said:**
> You may also get Pidgin 2.4.3 for Gutsy from here: [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

Thank you LinuxIsInnovation. Unfortunately, 2.4.3 is still only available for Hardy on getdeb.net. The Gutsy version is still 2.4.1.

---

### Post by sayakb on 2008-07-03
Ahh Sorry, didn't check that.. Ive gotta cut my practice of just typing the URL I know and throwing it over here ;)

---

### Post by chrisccoulson on 2008-07-03
That's ok! I nearly did the same thing as you, but I had a quick check at getdeb.net out of curiosity, just before I hit the reply button;)

---

### Post by StOoZ on 2008-07-03
> **whitethorn said:**
> As far as I've read, pidgin fixed the icq in 2.4.3 .  I don't know if it's true yesterday I had to compile it and I patched it myself. It works now, but it was really annoying finding all the dependencies took me like 30 min.  Neway there are a couple work arounds you can try

Here's one

[http://ubuntuforums.org/showthread.php?t=847240](http://ubuntuforums.org/showthread.php?t=847240)

and here

[http://ubuntuforums.org/showthread.php?t=846473](http://ubuntuforums.org/showthread.php?t=846473)

Hope this helps.

do u have a list of all the dependencies I need to install in order for it to work?

---

### Post by whitethorn on 2008-07-03
I'd go to  [www.getdeb.net](www.getdeb.net) and download .debs there for pidgin 2.4.3  It's a lot better than compiling yourself.  I didn't write down the dependencies, so no I don't know which ones nemore, a whole bunch. lol

---

### Post by StOoZ on 2008-07-03
> **whitethorn said:**
> I'd go to  [www.getdeb.net](www.getdeb.net) and download .debs there for pidgin 2.4.3  It's a lot better than compiling yourself.  I didn't write down the dependencies, so no I don't know which ones nemore, a whole bunch. lol

but getdeb has 2.4.3 for 8.04 only... :(

---

### Post by StOoZ on 2008-07-04
thank you all , I just upgraded to 8.04 and everything is working perfect!!!

---

