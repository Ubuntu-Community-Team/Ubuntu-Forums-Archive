---
title: "[SOLVED] how can i make hardy run faster?"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by crazypenguin2008 on 2008-09-15
is there anything i can do to make hardy run faster? IE,remove programs i dont use,strip down something? 

any advice is greatly apericated 


Jas'

---

### Post by Circus-Killer on 2008-09-15
well, one of your options is to just try [Xubuntu]("http://www.xubuntu.com/"). 
it's basically ubuntu but with the xfce desktop environment, which is far more lightweight.

---

### Post by iaculallad on 2008-09-15
Try to trim down your "unused" applications in your Sessions, and try adding more RAM to your box (Try posting your hardware specs).

---

### Post by jemate18 on 2008-09-15
> **crazypenguin2008 said:**
> is there anything i can do to make hardy run faster? IE,remove programs i dont use,strip down something? 

any advice is greatly apericated 


Jas'

So what is your Hardware specs?

CPU:
RAM:

---

### Post by crazypenguin2008 on 2008-09-15
cpu is intel pentium 3(katmia)  632.2mib ram. this is just my frankenstein box that i threw together from about 3 other boxes i had on my bench lol 

its started life as a 98 dell xpxt500. its quite a big box with lots of room to build apon

---

### Post by iaculallad on 2008-09-15
> **crazypenguin2008 said:**
> cpu is intel pentium 3(katmia)  632.2mib ram. this is just my frankenstein box that i threw together from about 3 other boxes i had on my bench lol 

its started life as a 98 dell xpxt500. its quite a big box with lots of room to build apon

With that specs you posted, Hardy would be merrier to run on it. But not to divert the topic/question you had posted, what about trying to install other distro's other than Hardy? Try Zenwalk or (x)Ubuntu at least, it could run at a better speed on that machine.

EDIT: Memories are cheap nowadays, try looking for SDRAM modules on your local SOS store and add it to your box, if you ought to run Hardy.

---

### Post by crazypenguin2008 on 2008-09-15
it might just be that ive been running my 64bit quad core AMD machine all weekend and this one is infact fast but not as fast as my newly built monster...

but anyways how do i trim down unused applications in sessions??

been using linux for 5 years and im still a noob at somthings :lolflag:

---

### Post by crazypenguin2008 on 2008-09-15
[QUOTE=iaculallad;
EDIT: Memories are cheap nowadays, try looking for SDRAM modules on your local SOS store and add it to your box, if you ought to run Hardy.[/QUOTE]

all three ram slots are filled....and ill be damned if i can rember what ram i put in here. i could pull the side panel and look i supose

---

### Post by iaculallad on 2008-09-15
> **crazypenguin2008 said:**
> it might just be that ive been running my 64bit quad core AMD machine all weekend and this one is infact fast but not as fast as my newly built monster...

but anyways how do i trim down unused applications in sessions??

been using linux for 5 years and im still a noob at somthings :lolflag:

System->Preferences->Session, and try removing apps you're not using or you don't want to auto execute at startup.

---

### Post by crazypenguin2008 on 2008-09-15
wow i didnt relize how many programs/apps i had running that i dont use/need....that might be slowing it down some lol

---

### Post by handydan918 on 2008-09-15
I just   installed Debian Lenny (KDE) on an old dell gx110 (733 mhz x 256 megs of ram) and it really is pretty snappy.

---

### Post by crazypenguin2008 on 2008-09-15
i took off some app's at startup and and took 4gb of pictures off that my girlfriend uploaded and dumped them to flashdrives and hardy is pretty damn sporty on this old cobbled toegtehr box

---

### Post by vbhide on 2009-04-06
I tried everything under the sun to make Hardy faster, until I did some simple thinking of my own. This is THE ONLY thing that worked.

1. Ubuntu installs itself on an ext3 filesystem by defualt. Change that to ext2.

2. Keep sufficient swap space. (atleast 1 gb)

If it doesn't work, then try all the fancy stuff.

---

