---
title: "HOWTO: Speed Up Azureus"
date: 2005-05-19
forum: Outdated Tutorials &amp; Tips
---

### Post by thechitowncubs on 2005-05-19
I noticed that azureus was slowing down my whole computer when using it considerably. I came across the azureus faq and it said that it would be really slow if you didn't have swt installed.

Here is what i did to install SWT.

```
sudo apt-get install libswt-gtk3-java
``` 

If you have backports enabled:
```
sudo apt-get install libswt-gtk3.1-java
```

Hope it works for you too!

---

### Post by bored2k on 2005-05-19
Wow .. so I was totally unaware of this. Thanks !

---

### Post by deception on 2005-05-19
Great tip thanks!

---

### Post by ow50 on 2005-05-19
The backports Azureus 2.3.0.0 depends on libswt-gtk-3.1-java, so you'll get that automatically if you install from backports. Though, if you're looking for speed, the new Azureus is not good. All the new features in 2.3.0.0 seem to have made Azureus somewhat slow. Azureus will often freeze when quitting and it's generally slow to operate, for example just opening the preferences tab.

---

### Post by jiyuu0 on 2005-05-19
was unaware too... thanks :)

---

### Post by bored2k on 2005-05-19
It's really a bit smoother now :-O . I know longer need to arm wrestle my mouse pointer when download GB's big files ! :D

---

### Post by thechitowncubs on 2005-05-19
[QUOTE=bored2k]It's really a bit smoother now :-O . I know longer need to arm wrestle my mouse pointer when download GB's big files ! :D[/QUOTE]

Haha, thats exactly what i was doing  ;-)

---

### Post by Jad on 2005-05-20
Thank you

---

### Post by jdong on 2005-05-20
You can also install Azureus with **apt-get install azureus**, which'll pull in swt for you.

---

### Post by Gandalf on 2005-05-20
thanks for the TIP, azureus was killing my laptop before, thanks

---

### Post by dejitarob on 2005-05-20
I couldn't figure out why I couldn't find the 3.1 package. It's because its "libswt-gtk-3.1-java", a slightly different naming convention than the earlier "libswt-gtk3-java" package. "aptitude search" works great btw.

---

### Post by dejitarob on 2005-05-21
Ah too bad this isn't a remedy for the memory leak with java (1.5.0_03). It's so bad I can actually sit here and watch the java process increase it's memory usage by a a few kilobytes a second. I love azureus's features and interface but I can take java's sloppy memory usage no longer. I'm going back to trying a more lightweight client which doesn't use over 680mb of memory and increasing after 10 mins of usage. Numerous people are also [reporting](http://azureus.aelitis.com/wiki/index.php/LikelyNetworkDisconnectReconnect?version=13) this can be the culprit for slow speeds and disconnects.

---

### Post by fdoving on 2005-05-21
[QUOTE=dejitarob]Ah too bad this isn't a remedy for the memory leak with java (1.5.0_03). It's so bad I can actually sit here and watch the java process increase it's memory usage by a a few kilobytes a second. I love azureus's features and interface but I can take java's sloppy memory usage no longer. I'm going back to trying a more lightweight client which doesn't use over 680mb of memory and increasing after 10 mins of usage. Numerous people are also [reporting](http://azureus.aelitis.com/wiki/index.php/LikelyNetworkDisconnectReconnect?version=13) this can be the culprit for slow speeds and disconnects.[/QUOTE]
 I have the same problem.

---

### Post by dejitarob on 2005-05-21
I downgraded to the old 2.2.0.2 version and my memory usage has leveled off at about 450mb after an hour of use. I may try the [2.3.0.1](http://azureus.sourceforge.net/index_CVS.php) version from CVS later as it [supposedly](http://azureus.aelitis.com/wiki/index.php/ChangeLog) contains "memory usage reductions and optimizations".

---

### Post by fdoving on 2005-05-21
Maybe I'll give the CVS version a try.. thanks for the tip.

---

### Post by thechitowncubs on 2005-05-21
Here is how I upgraded to the most recent beta...

1.[B] [http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)
[/B]
2. **Backup current azureus.jar**

3. [B]Copy CVS .jar to the azureus directory (if you used the Ubuntu Guide then it would be /opt/azureus)
[/B]
4. **Rename CVS .jar to azureus.jar**
4. **Reboot azureus and have fun.**

---

### Post by dejitarob on 2005-05-21
I had about 480mb of memory usage after a few hours with the latest beta CVS version. Still microsoft-like bloated but an improvement from version 2.3.0.0.

---

### Post by bored2k on 2005-05-21
[QUOTE=dejitarob]I had about 480mb of memory usage after a few hours with the latest beta CVS version. Still microsoft-like bloated but an improvement from version 2.3.0.0.[/QUOTE]
 2. Backup current azureus.jar

Mine is azureus2.jar

Anyway thanks for the tip. I enabled AutoCVSupdater so let's hope it all goes well.

---

### Post by jdong on 2005-05-21
Hmm, I've never seen any memory leak issues with Azureus, using sun-j2re1.5/sun-j2sdk1.5 in Backports (1.5.0_update02). Is it an update03 specific problem?

---

### Post by jdong on 2005-05-21
oh WOW, nvm, I see the leak :)

---

### Post by bored2k on 2005-05-21
[QUOTE=jdong]oh WOW, nvm, I see the leak :)[/QUOTE]
 Lol .

I hope bittornado releases a version with the new BT 4.0.2 features ASAP. Azureus+PC-usage reminds me so of another OS..

---

### Post by thechitowncubs on 2005-05-26
Azureus 2.3.0.2 is out  :)

---

### Post by ubuntu_demon on 2005-05-26
[QUOTE=thechitowncubs]Azureus 2.3.0.2 is out  :)[/QUOTE]
 I just copied the new jar file over the old one (I use azureus from the backports) :)

---

### Post by brdweb on 2005-05-27
One thing that affects the newer versions of Azureus is that fact that they are now supporting the decentralized tracker code. I mean if every client is helping to maintain a tracker it WILL decrease performance a bit. However, this vastly improves reliability of a swarm and ensures that if there are seeders, people can complete their downloads even if the original tracker goes down.

---

### Post by jdong on 2005-05-27
[QUOTE=brdweb]One thing that affects the newer versions of Azureus is that fact that they are now supporting the decentralized tracker code. I mean if every client is helping to maintain a tracker it WILL decrease performance a bit. However, this vastly improves reliability of a swarm and ensures that if there are seeders, people can complete their downloads even if the original tracker goes down.[/QUOTE]


Yeah, but there's no reason for DHT to use 2.3GB RAM after 3 days... Besides, Bittorrent 4.1.x beta supports DHT too, but doesn't suffer from RAM mania...

---

### Post by miscz on 2005-05-29
I don't know how do you do this. 2.3 gb of memory? This is impossible, you're propably using Gnome process list displaying proggie which I find VERY unreliable. Good old *ps aux* shows me that Azureus is using about 40% of my 256mb of ram and I'm downloading 3 big torrents that are over 8 gb big. I've got every possible memory eating feature enabled, decentralized trackers etc.

Back to the topic: installing libswt-gtk3-java packages made my Azureus CRAWL and die in 5 minutes. When I removed them it started to work again.

---

### Post by dejitarob on 2005-05-30
Doesn't the proc list use ps? Anyways the new 2.3.0.2 handles memory a bit better but it still is consistently taking over 500mb for 2-4 torrents, reaching upwards of 100% of my total ram usage.

---

### Post by pdk001 on 2005-05-30
i will try it later thank for tip

---

### Post by bored2k on 2005-05-31
For some sick reason, I removed this package and the others azureus from the repositories installs. I tried the official .bz2 this way, and so far I haven't feel any sluggishness at all (download two files simultaneously: one 3.6GB and 140MB one!).

---

### Post by Jesus Franco on 2005-05-31
Please add them back. Please. Azurues uses about 300 megs on my computer. I think these packages can decrease the amount of memory it uses.

---

### Post by Tad030 on 2005-07-11
whenever I run apt-get install azureus I receive the following error 

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package azureus


I'm new to linux, so I'm sorry if this is a real boneheaded question, but I have no idea how to fix the problem.  Any detailed help would be very appreciated.  


Tad

---

### Post by SFN on 2005-07-11
Frea

Kin

Sweet.

---

### Post by markmark on 2005-07-12
Tad030: I'm guessing this is because Azureus is in the "Universe" repositories which aren't enabled by default in Ubuntu. Try following the guide here: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories) to enable universe and give it another go.

---

### Post by bored2k on 2005-07-12
[QUOTE=markmark]Tad030: I'm guessing this is because Azureus is in the "Universe" repositories which aren't enabled by default in Ubuntu. Try following the guide here: [http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories) to enable universe and give it another go.[/QUOTE]
 Actually, it's in the backports ;).

---

### Post by liamhef2002 on 2006-02-25
i am downloading a file that is 1.50gb 
it is taking me days to download what speed should i have it set at or is there something i am missing?:(

---

### Post by specialboy on 2006-03-06
I had loads of problems with azureus 2.4.0.0.  It would connect but then not start transfers, give me loads of red line error codes and generally be anoying, so I downgraded to 2.2.0.2 and installed loads of other java pakages with synaptic (can't remember wich ones, I was ruthless) and now it's all good.  YAY! :D

---

