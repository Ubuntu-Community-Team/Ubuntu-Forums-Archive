---
title: "random log out ubuntu 11.10 (64bit)"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by shevin on 2011-10-30
I upgraded from 11.04 , I have 64 bit ubuntu .
I randomly get Log Out-ed . I see a black screen with some text for a moment then it goes to GDM log in page.and when I login , all of my works are lost .

I also get my curssor to jump sometimes when I am writing inside a text box , it is not doing it right now, but it happens randomly too .
I tried unchecking , "disable touchpad while typing" as it was suggested in similar forums but no help.


P.S : I have toshiba sattelite laptop , intel graphic card.

---

### Post by shevin on 2011-10-31
no one ?

---

### Post by hailtothethief on 2011-10-31
This is just a shot in the dark, but perhaps you're experiencing the same problem as in this thread?

[http://ubuntuforums.org/showthread.php?t=1872430](http://ubuntuforums.org/showthread.php?t=1872430)

Running
```
cat /var/log/syslog
```

at a terminal will output the file to your terminal. If it has something like

```
CRON[7832]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)
```

this may very well be your issue.

If not, is there anything you can tell us as far as when this occurs? Very few issues like this are truly random in occurrence.

Also, perhaps next time after this happens you could log back in and run 

```
cat /var/log/Xorg.0.log.old
```

and paste the output. The output of the first command may be useful, too.

---

### Post by shevin on 2011-11-01
it appears I have that in my system log ,

```
 cat /var/log/syslog | grep "cd / && run-parts --report /etc/cron.hourly)"
Oct 31 02:17:01 medya-Satellite-P745 CRON[12196]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 03:17:01 medya-Satellite-P745 CRON[12648]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 04:17:01 medya-Satellite-P745 CRON[13554]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 16:17:01 medya-Satellite-P745 CRON[2686]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 17:17:01 medya-Satellite-P745 CRON[4077]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 18:17:01 medya-Satellite-P745 CRON[4955]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 19:17:01 medya-Satellite-P745 CRON[5556]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 21:17:01 medya-Satellite-P745 CRON[6849]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 31 22:17:01 medya-Satellite-P745 CRON[7626]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```

what do u suggest ? just removing killer in the bin folder? 
isnt that killer there for a security reason or something ?

---

### Post by hailtothethief on 2011-11-01
Oops, my mistake. That line isn't necessarily what you're looking for, the actual line to check for is something like

```
killer[3353]: kill(15, 2053)
```

using, perhaps

```
cat /var/log/syslog | grep "killer.*kill"
```

"sudo apt-get remove killer" would solve this if it is your problem.

As far as I can tell killer is a sort of housekeeping script to kill processes belonging to users who aren't logged in. My 11.10 install doesn't have this package and runs fine so far.

---

### Post by shevin on 2011-11-02
it happend just one minute ago , [mine doesnt happen every hour , it happens like twice a day]

here are the sys logs : (it is long ubuntu forums wouldnt let me post it )

[http://www.copypastecode.com/93460/](http://www.copypastecode.com/93460/)


and here is the log for the /var/log/Xorg.0.log.old

[http://www.copypastecode.com/93464/](http://www.copypastecode.com/93464/)

---

### Post by shevin on 2011-11-02
> **hailtothethief said:**
> Oops, my mistake. That line isn't necessarily what you're looking for, the actual line to check for is something like

```
killer[3353]: kill(15, 2053)
```

using, perhaps

```
cat /var/log/syslog | grep "killer.*kill"
```

"sudo apt-get remove killer" would solve this if it is your problem.

As far as I can tell killer is a sort of housekeeping script to kill processes belonging to users who aren't logged in. My 11.10 install doesn't have this package and runs fine so far.

it  has no kill in the log
```
$ cat /var/log/syslog | grep "killer.*kill"
$ 

```

---

### Post by hailtothethief on 2011-11-02
Well, you're not going to like this:

After reading your Xorg.0.log I can see that X is experiencing a segmentation fault (crash) which is causing you to 'log out' (in reality X is dying in a fiery blaze, and like a pheonix, rising from its ashes over again, bringing you to the login screen)

Your backtrace doesn't provide anything strikingly useful, lacking debug symbols.

There are many bugs on [https://bugs.launchpad.net/ubuntu/+source/xorg-server/](https://bugs.launchpad.net/ubuntu/+source/xorg-server/) describing the same behavior (sporadic crashes due to a segfault)

I couldn't find any that match your exact setup, but that doesn't mean there isn't one. Your best bet is likely to follow the steps at [https://wiki.ubuntu.com/X/Backtracing](https://wiki.ubuntu.com/X/Backtracing) to obtain a useful backtrace and report it to the xorg-xserver launchpad (linked above). Once your bug is triaged the guys there will either point you to a solved bug or use your information to fix this one. They might even have a proper solution for you in the interim.

Sorry I couldn't be of more help.

---

### Post by breek on 2011-11-04
same here but no xorg segfault.
killer is not installed and no kill in syslog.
the problem happens twice today and a couple of times in the last week.

ubuntustudio 11.10

---

### Post by shevin on 2011-11-04
> **breek said:**
> same here but no xorg segfault.
killer is not installed and no kill in syslog.
the problem happens twice today and a couple of times in the last week.

ubuntustudio 11.10

do u also have microsoft wireless mouse & keyboard ? I suspect it could be the problem

---

### Post by breek on 2011-11-05
me? microsoft??? no no... :D mine is logitech mk 300 set.
the video card is different too as it seems you have an intel and mine is nvidia (nouveau driver).
in common we have a 64 bit os.

---

### Post by shevin on 2011-11-05
> **breek said:**
> me? microsoft??? no no... :D mine is logitech mk 300 set.
the video card is different too as it seems you have an intel and mine is nvidia (nouveau driver).
in common we have a 64 bit os.

yeah it seems like a 64bit bug . I should have never installed 64bit, there is no benefit but lots of headache in 64bit.

---

### Post by marty331 on 2011-12-14
> **breek said:**
> same here but no xorg segfault.
killer is not installed and no kill in syslog.
the problem happens twice today and a couple of times in the last week.

ubuntustudio 11.10


I am having the same issue.  I'm on 11.10 and I have a Logitech wireless mouse.  No wireless keyboard though.  I'm using a Samsung PC.

---

### Post by shevin on 2012-01-19
I reported this as a bug , in launchpad.net
[https://bugs.launchpad.net/ubuntu/+bug/918842](https://bugs.launchpad.net/ubuntu/+bug/918842)

---

### Post by gfte on 2012-01-21
Just wanted to add that I'm experiencing the exact same problem as you are shevin. Including Xorg Segmentation Fault:

[http://pastebin.com/XUJ4j9Ze](http://pastebin.com/XUJ4j9Ze)

Also that link you provided to the bug on launchpad is returning a 'Page Not Found'?

---

### Post by shevin on 2012-01-21
> **gfte said:**
> Just wanted to add that I'm experiencing the exact same problem as you are shevin. Including Xorg Segmentation Fault:

[http://pastebin.com/XUJ4j9Ze](http://pastebin.com/XUJ4j9Ze)

Also that link you provided to the bug on launchpad is returning a 'Page Not Found'?

oh sorry i had posted the bug as private, now it is public.

could you tell me the specification on your computer?

for example :
- I have Toshiba Laptop
- ubuntu 11.10 64bit (are you 64bit too?)
- having a Microsoft wireless keyboard mouse
- using compiz and unity
- installed non-free flash plugin

---

### Post by gfte on 2012-01-21
Thanks for making that public.

> **shevin said:**
> 
could you tell me the specification on your computer?


My spec:
Novatech Laptop (obscure brand from the UK)
11.10 64 bit
No external laptop or keyboard 
using compiz and unity
installed non-free flash plugin 

After more searching on Launchpad I found some more similar issues including this one, which is one of the only resolved:
 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/774978](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/774978)

and on this bug the resolution is within [comment 25]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/774978/comments/25").

I have added the repository suggest in the fix and updated. So far I haven't experienced the problem but that could just be a coincidence. 

I also found some suggestions that turning off certain compiz effects would remove the issue however this is kinda unsatisfactory because I'd rather not sacrifice some of the functionality that this offers:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/780358](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/780358)

---

### Post by DimasMM on 2012-06-16
I own 3 computers (one notebook, two desktops) all ubuntu 12.04, all x86_64. 

The problem is happening only in one desktop. Coincidentally, it is the only computer in which I made an upgrade from 11.10. I made a fresh install in the other two. 

So my question is: Is this happening only when upgrading?

PS: The same problem was happening in 11.10.

---

