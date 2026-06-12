---
title: "Kill apps Lubuntu"
date: 2014-03-02
forum: New to Ubuntu
---

### Post by sdvf on 2014-03-02
Hi. I usually use XBMC and as you guys know, the app is allways crashing. So i need something like ctrl+alt+del to kill that process.

Lubuntu 13.10.

Tks

---

### Post by Lars Noodén on 2014-03-02
In Lubuntu there is the Task Manager, which can be used to kill processes.  It is found via the LXDE Menu->System Tools->Task Manager

---

### Post by sdvf on 2014-03-02
> **Lars Noodén said:**
> In Lubuntu there is the Task Manager, which can be used to kill processes.  It is found via the LXDE Menu->System Tools->Task Manager
Ok. The situation is: in this moment my screen is locke with a crashed XBMC. How can i go to task manager? IS there a key combination?

---

### Post by Lars Noodén on 2014-03-02
ctrl-alt-del is *supposed* to bring up the Task Manager in LXDE but in 14.04beta, it does not.  

Alternately, can you bring up a text console with ctrl-alt-f1?  That migt not be as convenient but you could then use [pkill](http://manpages.ubuntu.com/manpages/saucy/en/man1/pkill.1.html).

---

### Post by Lars Noodén on 2014-03-02
Actually it turns out that I had lubuntu-core installed, with a full lubuntu-desktop, then ctrl-alt-del does bring up the Task Manager.

---

### Post by sdvf on 2014-03-02
I've got Lubuntu 13.10 and nothing happens when i go with ctrl+alt+del. Nothing happens in this specific situation when i've got a xbmc crash. Whem i'm on desktop environment it works perfect.

I'm a huge noob in linux distributions and this forum will be my "home" in the next few weeks.

---

### Post by rburkartjo on 2014-03-02
open terminal type in xkill and then hit the enter key. middle mouse button will kill whatever you want and you will get a skull with cross bones. left mouse button will exit xkill.

---

### Post by ajgreeny on 2014-03-02
I have set up a keyboard combination of **Winkey+Del** for the xkill command.  It can be useful on the (very unusual) occasion of an application locking itself solid.

---

### Post by walterorlin on 2014-03-02
Also if this keeps happening a task manager that can be run in a tty that even if can't get back you could use htop.

---

