---
title: "[SOLVED] root login"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by philk949 on 2008-07-25
Hi
I understand that logging in as root is a black subject, but I simply want to check the capacity of my printer's ink tanks, and for this, my turbo print configuration window informs me I need to be logged in as root. In fact, I get this message when I try to perform other functions as well. If logging in as root is such a heinous crime, why does Hardy offer the prompt?
And another thing: the message "you are not owner" or words to that effect when trying to perform some functions. How do I convince Hardy that I am?
Thank you
Phil

---

### Post by DGortze380 on 2008-07-25
For most day to day tasks you can use the sudo command to gain root privileges. There are very few cases where you actually need to be logged in as root. Being logged in as root makes it more likely to cause damage to your system, so use sudo whenever possible. (IMO there are times that are appropriate to log in as root, but as per forum guidelines I'll leave that subject alone). Sudo should work fine for what you need.

---

### Post by RequinB4 on 2008-07-25
See my signature for an explination of sudo and root.

It's not using root PRIVILAGES that is the problem, it's having EVERYTHING be running from a root user, ie "logging in as root."  It's much better to run specific APPLICATIONS as root then give any old program access to your machine.  Simply run your app in the terminal and add a sudo in the front.

---

### Post by Joeb454 on 2008-07-25
To get a temporary root terminal, run ```
sudo -i
```

To get a nautilus (file browser) root window, hit Alt+F2 and enter ```
gksudo nautilus
```

Though do be careful when you have the root session running ;)

---

### Post by stevoo on 2008-07-25
running like sudo isnt really that bad. 
Its just not adviced especially if you do not know what you are doing.
A wrong command and you may end up on the wrong side.

Instead use like everyone else said 
sudo 
infornt to temporarily gain root and access what you want to do.

---

### Post by philk949 on 2008-07-25
Thank you for your replies, but I still don't know how I can perform the simple task of checking my ink tank capacity. The terminal commands you provided do give me temporary and safe root access, but not to the Control Centre, from which I'm trying to configure my printer's toolbox options.

phil

---

### Post by Joeb454 on 2008-07-25
How do you normally run the control center?

---

### Post by philk949 on 2008-07-25
System>Control Centre<select function>

---

### Post by mc4100 on 2008-07-25
> **philk949 said:**
> Thank you for your replies, but I still don't know how I can perform the simple task of checking my ink tank capacity. The terminal commands you provided do give me temporary and safe root access, but not to the Control Centre, from which I'm trying to configure my printer's toolbox options.

phil

Have you tried ALT+F2 and then,
```
gksudo gnome-control-center
```

---

### Post by philk949 on 2008-07-25
No. Boy, am I embarrassed! Thank you.

---

### Post by Joeb454 on 2008-07-25
It's easy enough to make mistakes :)

You can mark your thread solved from thread tools at the top of the page.

See - [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by sdowney717 on 2008-07-25
> 
System>Control Center<select function>


How come I don't have that in my system menu?
gksudo gnome-control-center
gives me an app I have not seen before.

---

### Post by philk949 on 2008-07-25
syd,

Right click on the Ubuntu icon top left. Select Edit Menus>System<tick box for Control Centre>

Phil

---

### Post by arpanaut on 2008-07-25
Right click on Applications>edit menu>System> add check mark to Control Center>close
Now it be there:biggrin:

---

