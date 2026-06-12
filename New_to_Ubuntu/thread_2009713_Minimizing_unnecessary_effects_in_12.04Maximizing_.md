---
title: "Minimizing unnecessary effects in 12.04?/Maximizing performance"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by Xtensity on 2012-06-24
I am running Ubuntu 12.04 on my netbook, and it is by far the SLOWEST and slowest to respond out of any of the others. I have to use it because it is the only one that my wireless will work on. I wont have anything open and a simple chrome browser can take 5-10 seconds. On any other version on this same netbook, with lots of other apps open, it will open up instantly...

So basically I need to maximzie the performance of this OS, which I have no clue why it is so terribly slow to respond.

And just FYI.... there is no .compiz or .themes folder in the home folder.

I am running Gnome Shell and there is almost nothing installed, yet it is excessively slow, for no apparent reason. I have all the latest updates installed. (before and after updates, the speed never changed.)

---

### Post by NikTh on 2012-06-24
Its to slow probably cause its a netbook. What is the specs ?  
Suggestion:
Do not run gnome-shell. Just run the original Ubuntu-2d enviroment (unity without compiz) 
or 
try gnome fallback (without effects).

---

### Post by zombifier25 on 2012-06-24
Use LXDE. It's extremely light.

---

### Post by Xtensity on 2012-06-25
> **NikTh said:**
> Its to slow probably cause its a netbook. What is the specs ?  
Suggestion:
Do not run gnome-shell. Just run the original Ubuntu-2d enviroment (unity without compiz) 
or 
try gnome fallback (without effects).

It's not slow because it's a netbook, because litterely every other Ubuntu OS runs fast on it. Including unity in 11.04... Though I'm not really interested in unity. 

How do I disable compiz in Ubuntu 2d? Or gnome fall back?

I am using Gnome Classic ( No effects ).... I would be using 11.04 but my wireless on my netbook doesn't work on it and nobody here on the forum has been able to find a solution.

I seriously don't understand it. There's not any gigantic differences between 11.04 and 12.04 that would effect performance but 11.04 is a million times faster, everything I click it instant and there's practically no wait times for anything

---

### Post by cmcanulty on 2012-06-25
I would try reinstall 12.04

---

### Post by sudodus on 2012-06-25
> **zombifier25 said:**
> Use LXDE. It's extremely light.
+1

And I would suggest that you do it using Lubuntu

Download Lubuntu 12.04 and test if you like it selecting 'try Lubuntu' when booting from a USB drive. This will start a live session.

If you like Lubuntu, there are a couple of options:

- clean the system and install it

- install lubuntu-desktop

```
sudo apt-get install lubuntu-desktop
``` into your present system. This gives you the opportunity to select desktop environment at the log in screen.

---

### Post by vasa1 on 2012-06-25
> **Xtensity said:**
> ...
I seriously don't understand it. There's not any gigantic differences between 11.04 and 12.04 that would effect performance but 11.04 is a million times faster ...
Possibly it's something peculiar to your set-up? I don't think there are a significant number of reports of 12.04 being much slower than 11.04 or 11.10.

---

### Post by Xtensity on 2012-06-26
> **vasa1 said:**
> Possibly it's something peculiar to your set-up? I don't think there are a significant number of reports of 12.04 being much slower than 11.04 or 11.10.

There are actually a large number of people complaining about 12.04 being slower. A google search will show this... but everyones solutions to the problem were different from eachother.

---

