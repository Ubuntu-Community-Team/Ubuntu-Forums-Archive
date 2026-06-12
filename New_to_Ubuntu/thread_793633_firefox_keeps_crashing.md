---
title: "firefox keeps crashing"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by brokenhachi on 2008-05-13
hey guys, my firefox just keeps crashing, randomly... sometimes it does it when i view certain websites, and sometimes when i just open the tools menu, but after it crashes, i cant seem to reopen it by using the starter icon, i have to use the terminal or it wont restart (it comes up and then  immediatly closes)


here is the line i get in the terminal:

```
dave@dave-laptop-linux:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
GCJ PLUGIN: thread 0x805e130: NP_GetMIMEDescription
GCJ PLUGIN: thread 0x805e130: NP_GetMIMEDescription return
GCJ PLUGIN: thread 0x805e130: NP_GetValue
GCJ PLUGIN: thread 0x805e130: NP_GetValue: returning plugin name.
GCJ PLUGIN: thread 0x805e130: NP_GetValue return
GCJ PLUGIN: thread 0x805e130: NP_GetValue
GCJ PLUGIN: thread 0x805e130: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x805e130: NP_GetValue return
Segmentation fault

```


i'm not sure what "segmentation fault" is supposed to mean.. but thats what it ends with every time. sometimes the things above it are different but it always ends in that fault.

anyone out there give me a hand with this?


Thanks,

Dave


P.S. btw, i am using hardy heron(i think? anyways, 8.04) but the problem has been the same since after i installed gutsy

---

### Post by zenwalker on 2008-05-13
Is the FF upto date with the Hardy's def ver? Probably there was abug or some thing, try updating.

---

### Post by brokenhachi on 2008-05-13
i'm on 3.0b5 im pretty sure its the correct version because after upgrading to hardy, it updated my firefox, but like i said, the problem has been persisting since i had gutsy\



btw, i set it to reinstall through the package manager, but it didnt help

---

### Post by tjwoosta on 2008-05-13
this is a common problem people have been having with firefox3 in ubuntu (its still in beta)

i suggest trying firefox 2 or even opera

correction: i guess people have been having problems with the 32bit version of opera being slow, but if you have 64bit ubuntu you should try the new opera 9.50 beta 5 (its so fast, scores way higher than firefox3 on acid 3 test)

---

### Post by brokenhachi on 2008-05-13
is there no way to fix it?


edit: i had the same problem with firefox2. and no, i have 32bit

---

### Post by tjwoosta on 2008-05-14
i hate to say it, but i dont think there is

you should give opera 9.50b2 a try though (i just read a few more posts and others say the 32bit works fine for them)

here is the link to download

[http://www.opera.com/download/?ver=9.50b2]("http://www.opera.com/download/?ver=9.50b2")

---

### Post by brokenhachi on 2008-05-14
alright, thanks. well i'll download it as an alternative.. 


if anyone else knows how to fix this problem please speak up, i appreciate it.

---

### Post by brokenhachi on 2008-05-14
sorry for the double post, but can you also tell me how to copy my bookmarks from firefox to opera?

---

### Post by PinkFloyd102489 on 2008-05-14
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)


Scroll down to part B and do that part. Had the same problem, as does everyone I think. This fixed it.

---

### Post by nicedude on 2008-05-14
The way to fix it is to go to synaptic package manager and uninstall Firefox 3 beta and reinstall Firefox 2 (which is what you were using with earlier Ubuntu versions). Why the Ubuntu Developers decided to use a BETA in their release is beyond me as Firefox 2 is surely more stable as Firefox 3 is still a BETA release. I mean it will be way simple to upgrade to 3 when it is out of its BETA stage and is a stable release ( I guess the Firefox team needed more guinea pigs for their BETA ). Well I for one think F2 is better for now as all my favorite addons work and they don't with 3, so I will switch to 3 when they get it fully functional and the addons work.

---

