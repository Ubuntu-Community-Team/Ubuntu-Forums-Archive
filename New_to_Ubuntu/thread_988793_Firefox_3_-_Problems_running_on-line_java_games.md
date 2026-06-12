---
title: "Firefox 3 - Problems running on-line java games"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Miljet on 2008-11-20
Is there anyone else here who plays on-line games at Pogo.com? If so, I would really like some feedback.

Computer is Toshiba Satellite P205-S6237.

I upgraded (upgraded, not reinstalled) from Gutsy to Hardy about a month ago. As a part of the upgrade, Firefox was upgraded from Firefox 2 to Firefox 3.0.3. Immediately after the upgrade, the games would no longer consistently load and run. I get wildly varying results. Sometimes the game window opens and just stalls, sometimes Firefox just closes, and occasionally the game will actually load and run. But the most common result is that the game window will open and immediately after the "game applet started" message, I get a "game applet death" message and it just sits there. Firefox is not locked up. I can close the game window or change sites or whatever. 

At first, I thought it might be a problem with some preferences left over from Firefox 2. So I created a new user with a clean /home directory, but it made no difference at all. I checked and re-installed Sun java 6 and it is working. I tried disabling all plugins except Sun java. Same problems. I disabled all Firefox extensions. Same result. A couple of days ago I received updates which included an update from Firefox 3.0.3 to Firefox 3.0.4. I hoped that would resolve the problem, but it hasn't.

I tried downloading and running Opera but, for some reason, couldn't get java plugin installed. So I went back to trying to find a fix for Firefox.

I really don't want to downgrade to Firefox 2 if I can help it. Firefox 3 seems to run much faster and smoother that Firefox 2 ever did.

I am fresh out of ideas. Any thoughts or help would be greatly apreciated.

---

### Post by wiseguy on 2008-11-21
Do a search in synaptic and search for jre. Try removing java 6 and installing java 5. Also ```
sudo apt-get install sun-java5 plugin
```

PS... you will need Java 6 for frostwire.

---

### Post by Kellemora on 2008-11-21
Hi Miljet

Been awhile since I've been over to Pogo, I play at IWON quite often though.

FWIW: I had to roll back Java all the way to version 1.6.0_07-b06 to play the Java based games at IWON, and if I remember right, I couldn't play Java based at Pogo at all, just got a gray screen where the game should be.

What are you doing about the Shockwave based games?
I have not got Shockwave to work at ANY game site yet!

TTUL
Gary

---

### Post by Miljet on 2008-11-23
Thanks for the replies. I have Shockwave Flash 9.0 r124 installed and haven't had any problems with it so far. 
Java(TM) Plug-in 1.6.0_07-b06 is the exact java plugin that I have installed. It was working with Firefox 2, but not working right with Firefox 3.
I will try the java 5 and see what happens.

---

### Post by wiseguy on 2008-12-03
> **Miljet said:**
> 
I will try the java 5 and see what happens.

Did it work?

---

### Post by Miljet on 2008-12-03
Nope.

---

### Post by binbash on 2008-12-03
with intrepid, firefox (3.0.x and 3.1b2) mostly crashes for me at java based online games also.(for me)

My solution is use opera most cases, however at some games, this even does not solve my issues (some games crashes with opera also, random mostly).This is where virtual machine is handy for me

---

### Post by Miljet on 2008-12-22
Opera was no solution for me. Every time a game attempts to load, the entire browser simply closes.

For the time being I created another partition and reinstalled Gutsy on it. Games work perfectly on Gutsy.

I am still working on getting it to work in Hardy somehow. I did read in a bug report somewhere that Firefox 3 has java problems that have not been resolved.

---

### Post by hobo on 2009-03-13
I too have had problems running POGO games in 8.04 after upgrading from 6.06. What I found was TWO JAVA plugins resident in a Firefox subdirectory. Anyways, what I did was remove all JAVA from the system and downloaded the newest JAVA from SUN and installed. Then I deleted the OLD plugin and now POGO works just fine in 8.04 for me.

---

