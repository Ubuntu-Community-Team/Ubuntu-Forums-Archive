---
title: "NetBEUI, Ubuntu, and a CNC controller running DOS"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by AndrewEsther on 2008-06-24
Okay, so this may be the absolute wrong spot to post this, but I figure it will get moved if it proves useful. So here I go.. *deep breath*

To start, I have an older box (still has PC100 sticks in it yay!) which will be running an, as of yet, still undetermined version of Ubuntu... probably 6.06, as this runs well on my crusty old Compaq laptop. I want to use this as a file server box for storing/calling up files to be used on one of several of my CNC boxes (I have a small machine shop and hate floppy disks with a firey passion)

Next, the box that I'm having the biggest problem with is, unfortunately, one of my oldest, but most reliable and most used machines. It has, buried somewhere deep within its bowels, a box running some type of Intel chip and DOS (I believe it to be DOS 6.x), all sandwiched under the lamest excuse for a GUI I've ever seen on a CNC box. It's a glorified MUD-wannabe interface that's very textual and monochrome-esque.

The problem: I can't just simply stick a new box in it for the simple reason that the box is part of the machine's subsystems, and houses all manner of servo controller PCI/PCMIA/wtf cards that are both expensive and proprietary and I'm pretty sure my warranty would void if I ever took the cover off. The only form of communication it has with the outside world is the floppy drive and its ethernet card.

I was given instructions as to how to set up the machine to communicate with one specific computer, which was where all the CAD/CAM programming was done from. It was running windows 95, which promptly failed (after having run for 9 years continuously). Rather then get a new windows 95 pc, I upgraded all the computers in my shop to run windows xp (needed for the CAD programs, otherwise it would have been ubuntu). Now I need a way to pull files from any computer in the shop, stick them on this would-be server box, and then call them up from the machine.

I've been told that the CNC box will ONLY accept NetBEUI as a means to communicate over ethernet, and that statement has thus far proved itself to be correct. WHY CAN'T IT JUST HAVE AN IP ADDRESS!? :cry: sorry this post is so long. Help will be gratefully appreciated.

---

### Post by jrusso2 on 2008-06-24
Unless you can run a TCP/IP stack on that DOS box your probably right being limited to netbeui.

However Windows operating systems supported this up to at least Windows 2000 I believe which is probably what I would use since its more stable then the 9x series.  Unless XP supports it which it might.

---

### Post by AndrewEsther on 2008-06-24
XP supports it, but barely. I had to rip the driver off of the deepest parts of a windows 95 hard drive. It worked once for a few days, and then the XP box, the router, or some other part of my network decided that it had had quite enough of this NetBEUI nonsense and gave me the finger. Hasn't worked since, not even directly connected to an XP box via crossover.

I never quite fully understood how to view the folder on the XP machine from the DOS box. It asks me for a username/password on boot, and I have no idea what it is asking for.

---

### Post by jrusso2 on 2008-06-24
Yes that can be a problem since XP is based on NT it will expect a password and not sure if DOS can transmit it properly.

---

### Post by AndrewEsther on 2008-06-24
So then is it possible for me to do this in ubuntu? Use the ubuntu box as a quick and easy go-between on my network? I'm hoping that if it is, it will follow the path of many other things I've done with ubuntu which tends to be harder at first and then extravigantly easier and work flawlessly.

---

### Post by AndrewEsther on 2008-07-16
thread bump on this.


maybe nobody uses netbeui anymore :*(



oh, and I've heard that NetBEUI is not route-able... is this true?

---

