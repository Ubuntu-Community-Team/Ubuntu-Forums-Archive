---
title: "windows antivirus for linux"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by melrokz on 2008-07-15
[FONT="Comic Sans MS"][SIZE="3"]I need a good antivirus solution for Windows viruses in Linux, comparable 2 Symantec corporate edition 10 in windows. Please suggest an appropriate one - shareware and freeware best.
Also, whenever i search for real-time virus scanning, i have to install 'dazuko' and compile my Linux kernel 4 that! How should i do that? I'm a babe in linux, so plz tell me step-by-step.[/SIZE][/FONT]

---

### Post by Canis familiaris on 2008-07-15
I think you need ClamAV.
Just search ClamAV in Add/Remove and install

---

### Post by OutOfReach on 2008-07-15
I second ClamAV its a very good tool.

---

### Post by lisati on 2008-07-15
I use the free version of AVG. The catch is that you have to add your user name to the avg group for the gui-based update to work. (It's in the manuals but who bothers to read them?)

---

### Post by Sef on 2008-07-15
Check out [Avast]("http://www.avast.com/eng/avast-for-linux-workstation.html").

---

### Post by gandaran on 2008-07-15
> **melrokz said:**
> [FONT="Comic Sans MS"][SIZE="3"]I need a good antivirus solution for Windows viruses in Linux, comparable 2 Symantec corporate edition 10 in windows. Please suggest an appropriate one - shareware and freeware best.
Also, whenever i search for real-time virus scanning, i have to install 'dazuko' and compile my Linux kernel 4 that! How should i do that? I'm a babe in linux, so plz tell me step-by-step.[/SIZE][/FONT]

real-time virus scanning in ubuntu is a bit tricky, dazuko conflicts with some security applications in ubuntu that won't let dazuko work, you'll have to remove them.
you just have to compile dazuko and load the module.
about the best **free** linux antivirus, I would say BitDefender, it's just a command line scanner, (no real time scanning, but there's no need for this in linux) it's the only linux antivirus with ad-aware,spyware and antivirus scanner all in one package with hourly updates.

edit:
most linux antivirus scanners use the dazuko engine for real-time scanning, but there's one or two paid commercial antivirus that have their own scanning engine, I don't remember which brand, check panda software and karspensky antivirus.

---

