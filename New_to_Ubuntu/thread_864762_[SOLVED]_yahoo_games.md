---
title: "[SOLVED] yahoo games"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by SOME1ELSE1999 on 2008-07-20
i am trying to play yahoo games with this os. i am unsure how to download and install java/flash payer i need. any help would be greatly appreciated. also as far a what ver of linex i am using all i know is it says ubuntu when i start my comp. sorry if i am not much help.

---

### Post by XVII on 2008-07-20
```
sudo apt-get update && sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin flashplugin-nonfree 
```

That will install java and flash for you.

---

### Post by SOME1ELSE1999 on 2008-07-20
thank you but where do i copy paste that??

---

### Post by XVII on 2008-07-20
> **SOME1ELSE1999 said:**
> thank you but where do i copy paste that??

You put it in your terminal.

---

### Post by Sef on 2008-07-20
**Easy way to install Java:**

Applications > Add/Remove > Show: Change to 'All Available Applications' > Search: Sun Java 6 > check the top box > Apply Changes > Apply > More Applications

**Easy way to install Flash:**

Applications > Add/Remove > Show: Change to 'All Available Applications' > Search: Flash > check the top box > Apply Changes > Apply > close

---

### Post by XVII on 2008-07-20
> **Sef said:**
> **Easy way to install Java:**

Applications > Add/Remove > Show: Change to 'All Available Applications' > Search: Sun Java 6 > check the top box > Apply Changes > Apply > More Applications

**Easy way to install Flash:**

Applications > Add/Remove > Show: Change to 'All Available Applications' > Search: Flash > check the top box > Apply Changes > Apply > close

Assuming that he is using Gnome.

---

### Post by SOME1ELSE1999 on 2008-07-20
thank you. i have loaded java now it tells me yahoo games wants to load a applet. gives me the option to cancel trust applet and trust applet and add to white list. also in the y games page it tells me jjava may not be enabled on my browser or that it is not installed. i have tried to add applet to white list and tried to trust applet however both options immediately close fire fox. i also check to make sure java is enabled and that i am accepting cookies and i am. any fudther help would be appreciated.

---

### Post by alzie on 2008-07-20
At some of the game sites like yahoo and pogo java 1.6 has problems.

I used synaptic to remove java 1.6 and replace it with java5 for Pogo and I know of others doing the same for Yahoo.

You may need to remove all instances of openjdk and icedtea too.

Good Luck

---

### Post by SOME1ELSE1999 on 2008-07-20
ok through looking at previous post i think i have found a solution but this has created another problem. when i open synaptic package manager it tells me a error has occured.  

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


i tried opening terminal and entering dpkg --configure -a but then it tells me

tojo@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
tojo@ubuntu:~$ 

what does this mean and how do i fix it?

---

### Post by OldTimeTech on 2008-07-20
this has to be run as sudo
so type into terminal
sudo dpkg --configure -a
and then your password and hit enter

---

### Post by asmoore82 on 2008-07-20
As far as I can tell, Yahoo Games has been completely broken for at least the last 18 months.

---

### Post by billgoldberg on 2008-07-20
> **XVII said:**
> Assuming that he is using Gnome.

There is an [ubuntu] next to the title.

So yes he is using gnome.

---

