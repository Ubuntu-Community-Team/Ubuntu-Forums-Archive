---
title: "Virus Scanner for ubuntu"
date: 2009-08-18
forum: Recurring Discussions
---

### Post by schalich11 on 2009-08-18
I have dual booted computer with windows and ubuntu. Sometimes i torrent programs and other things from my ubuntu but they only work for windows. So i just wanted to get a virus scanner for my ubuntu so i can scan the programs before i move them into windows. Any suggestions on which is the best program to use? I dont really need a firewall and all that other stuff. I just want a scanner. Thanks!

---

### Post by credobyte on 2009-08-18
BitDefender: [https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

---

### Post by doas777 on 2009-08-18
I've used bitdefender and clam. bitdefender is definitely the winner for GUI and ease of use. clam-tk never worked right for me anyway.
I've also heard that there is an AVast version for linux as well.

---

### Post by ajgreeny on 2009-08-18
clamav is the best in my opinion.  Run ```
clamscan -ri
```to check your home folder or ```
clamscan /path/to/file
```to check a single file.

---

### Post by hoppipolla on 2009-08-18
Wow these virus scanner threads DO come along often! And yeah I would say Clam, but I haven't used many others for Lin I have to admit.

Grab a good front-end for it though if you want ease of use :)

---

### Post by juancarlospaco on 2009-08-18
Clam extension for Nautilus is nice.
:)

---

### Post by bodhi.zazen on 2009-08-19
> **hoppipolla said:**
> Wow these virus scanner threads DO come along often! And yeah I would say Clam, but I haven't used many others for Lin I have to admit.

Grab a good front-end for it though if you want ease of use :)

Yes and it is nice to see one stay on topic (ie answer the question without all the cruft).

---

### Post by paok4 on 2009-08-19
I use AVG 7.5 for Linux. download it from [HERE]("http://rapidshare.com/files/263702704/avg75fld-r51-a1243.i386.deb") to give a try. You can update it from internet easily ...   For downloading  the updates change the command in the AVG launcher from "avggui" to"gksudo avggui" ... :KS:KS:KS

---

### Post by brij on 2009-08-19
Use clam it works well

---

### Post by credobyte on 2009-08-19
> **brij said:**
> Use clam it works well

*Works well* doesn't mean the same what *protects well* :p

---

### Post by MikeTheC on 2009-08-20
[center][img]http://img200.imageshack.us/img200/6096/ubuntuvirusscanner01.png[/img][/center]

---

### Post by Cloggsy on 2009-08-20
> **doas777 said:**
> 
I've also heard that there is an AVast version for linux as well.

...which I have just downloaded onto both my machines as I wasn't convinced Clam was doing the job - couldn't find any virus signatures or download updates. However, avast! seems to be working and has already unearthed a couple of Windows viruses with Clam missed.

---

### Post by running_rabbit07 on 2009-08-20
> **MikeTheC said:**
> [CENTER][IMG]http://img200.imageshack.us/img200/6096/ubuntuvirusscanner01.png[/IMG][/CENTER]

That's awesome!

---

### Post by Spencer Caplan on 2009-08-20
Just to throw in my two cents, I recently switched from dual booting with Windows XP and I find that both Avast and AVG anti-virus work well. AVG doesn't have a GUI though so you might prefer Avast. Firestarter is a good GUI for the built-in firewall on Jaunty.

---

### Post by running_rabbit07 on 2009-08-20
> **doas777 said:**
> I've used bitdefender and clam. bitdefender is definitely the winner for GUI and ease of use. clam-tk never worked right for me anyway.
I've also heard that there is an AVast version for linux as well.

I am running Hardy, how do I get bitdefender so that I can give it a spin? I can't find it in Synaptic.

> **doas777 said:**
> unfourtunatly it is not quite that easy (but not hard, just a few more steps).
this should get you started: [https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

Cool, thanks.

---

### Post by doas777 on 2009-08-20
> **running_rabbit07 said:**
> I am running Hardy, how do I get bitdefender so that I can give it a spin? I can't find it in Synaptic.


unfourtunatly it is not quite that easy (but not hard, just a few more steps).
this should get you started: [https://help.ubuntu.com/community/BitDefender](https://help.ubuntu.com/community/BitDefender)

---

