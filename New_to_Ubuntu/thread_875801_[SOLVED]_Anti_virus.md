---
title: "[SOLVED] Anti virus"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by Gosling on 2008-07-31
I'm a recent migrant from Windows and am wondering how important it is to utilize anti virus programs. If so, can some programs be recommended?

Many thanks,

MikeR

---

### Post by kesman on 2008-07-31
For normal Desktop-user, no antivirus is needed, but if you are planning on hosting an e-mail server or so with your linux box, then you might consider getting one.

Search for antivirus in synaptic package manager under s**ystem->administration** menu or from **applications -> add/remove applications**

---

### Post by Trail on 2008-07-31
Not really important, unless you interact with a lot of windows machines and you don't work to pass virii to them (I wouldn't care myself, but you can be polite).

---

### Post by kesman on 2008-07-31
> **Trail said:**
> Not really important, unless you interact with a lot of windows machines and you don't work to pass virii to them (I wouldn't care myself, but you can be polite).

Sorry for going off-topic, but virii == viruses in some weird grammar?

---

### Post by sdowney717 on 2008-07-31
no virus or malware, adware for linux will run.
If you install wine, then a virus could possibly run but would be restricted to the wine installation, especially if you removed the drive link to you linux system which is z:

You can use clamAV, clamav freshclam for the updates and AVSCAN for the gui.
And you can scan windows partitions. If you dual boot, the windows partition is mounted in /media/disk.

I just cleared off a hard drive from another windows machine. avscan found 3 viruses. I manually deleted the viruses after noting the locations. And then the windows system worked again.

You can also use avast for linux. They have a .deb file for ubuntu 
gksudo avastgui is the command for running avast

---

### Post by zipperback on 2008-07-31
> **Gosling said:**
> I'm a recent migrant from Windows and am wondering how important it is to utilize anti virus programs. If so, can some programs be recommended?


clamav - anti-virus utility for Unix - command-line interface
clamtk - GUI interface for clamav

If you are dealing with Windows files, it is helpful to have these installed. 

You can install these by using Synaptic.

System -> Administration -> Synaptic Package Manager

- zipperback
- :popcorn:

---

### Post by billgoldberg on 2008-07-31
> **kesman said:**
> Sorry for going off-topic, but virii == viruses in some weird grammar?

Some people think it's the correct way to spel viruses.

It's not.

```
Hackers like to use “virii” as the plural form of “virus,” but Latin scholars object that this invented term does not follow standard patterns in that language, and that there is already a perfectly good plural in English: “viruses.” 
```

---

### Post by Gosling on 2008-07-31
> **kesman said:**
> Sorry for going off-topic, but virii == viruses in some weird grammar?

virii is the plural of virus.

Cheers,

MikeR

Sorry, just saw previous message. Learned something today. Thanks.

MikeR

---

### Post by philinux on 2008-07-31
> **kesman said:**
> Sorry for going off-topic, but virii == viruses in some weird grammar?

[http://en.wikipedia.org/wiki/Plural_of_virus](http://en.wikipedia.org/wiki/Plural_of_virus)  :lolflag:

---

### Post by aeiah on 2008-07-31
virii is just geek speak. much like the plural of box being boxen (but it not really being a correct way of pluralising box)


but yes. use anti-virus if you get and receive files from windows users, and you cant be sure whether these windows users are capable of keeping their machines virus free by themselves.

also, if you're using it for work, it looks pretty unprofessional if what you send them pops up with a virus warning at their end, even if you're just passing the data on from someone else, so id use an antivirus program in that instance.

clam-av is popular for linux i believe.

---

