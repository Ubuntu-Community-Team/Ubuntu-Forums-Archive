---
title: "[xubuntu] Can't Uninstall (manlly instld) pkgs due to 'getdeb.list.bck' inval file"
date: 2014-09-10
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2014-09-10
Hey "Guys", brand new. Very happy to leave the world of WinX behind me (course Android 18-months-learning to root,etc.delicately delivered me here!) ;-)

Question, (random example) I'm trying to remove CrashPlan
(I did install in "correct"/ directory per CPP instructions which *is* a root directory, but  read on here say "NO" to install into root as it causes problems later in logs,etc. 
Makes sense, thus trying to uninstall that particular location, to then reinstall. 

Uninstall CrashPlanPlus, using the following:
______________________________________________
```

bender@DAWG:/usr/local$ sudo apt-get remove crashplan
[sudo] password for bender: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Unable to locate package crashplan
bender@DAWG:/usr/local$ 

```

______________________________________________

I don't think the 

```
Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' 
```

  is unique to CPP as I get this error with other packages as well. 

Browning /sources.list.d/ looks like those files under the tree are PPA-List based. 
However, those PPA's appear to be installing just fine (aka installed XBMC that way). 

Thank YOU!! in Advance!
E.


________________
PS-A quick primer please. What is forum protocol if I have (what I think) are all same ballpark questions (6-7) of them 
(I think) 101-Grade School answers (not much to gain for a KB) thus permissible to roll into one question? 
I don't want to "blow up" the board with academic/101 that 98% probably find no value in. But if that's the rule, pls let me know. 

___________
ex-o.k. to flash Bios through wine? (or better way?)-AKA-since Flashing is less fault tolerant that most, want to make sure. 
is the "host" same as "host" in Windows? The "loopback?" If so, I used a great program called "HostMan"[http://www.abelhadigital.com/hostsman](http://www.abelhadigital.com/hostsman) that created 60,000ish lines of 127.0.0.1 loop back when an ad server tries to hit. makes computer faster too, can I use same in X/Ubuntu

---

### Post by deadflowr on 2014-09-10
Rename the extension
```
sudo mv /etc/apt/sources.list.d/getdeb.list.bck /etc/apt/sources.list.d/getdeb.list.save
```
It doesn't know what a bck extension is suppose to be.
See if that helps, at least with the apt-get error.
Don't know about crashplan...

Edit: I changed the extension from old to save, which seems to be what it wants.

---

### Post by whereismymindat2 on 2014-09-10
Thannk you kindly! Think this works/worked. Is there a "Thanks" button around (a la AndroidForums)--*laff*--sorry for the "junior" question, but where is "solved"--it's 5:35pm here low on the glucose. *grin*

---

### Post by deadflowr on 2014-09-10
> **whereismymindat2 said:**
> Thannk you kindly! Think this works/worked. Is there a "Thanks" button around (a la AndroidForums)--*laff*--**sorry for the "junior" question, but where is "solved"**--it's 5:35pm here low on the glucose. *grin*

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

