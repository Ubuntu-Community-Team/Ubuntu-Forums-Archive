---
title: "installing google chrome and other soft"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by jjtech77 on 2012-03-25
[SIZE=2]Hi[/SIZE],
I have a problem installing google chrome on ubuntu 11.10 64-bit. 
I downloaded it and used:
1/ sudo apt-get install libnspr4-0d libnss3-1d libxss1

2 / sudo dpkg -i ./Downloads/google-chrome-stable_current_amd64.deb
And this is what it does: 
(Reading database ... 151389 files and directories currently installed.)
Preparing to replace google-chrome-stable 17.0.963.83-r127885 (using .../google-chrome-stable_current_amd64.deb) ...
Unpacking replacement google-chrome-stable ...
dpkg: dependency problems prevent configuration of google-chrome-stable:
 google-chrome-stable depends on libcurl3; however:
  Package libcurl3 is not installed.
dpkg: error processing google-chrome-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Errors were encountered while processing:
 google-chrome-stable


I'm using linux only for 2 days and have problems with basic stuff - like where is the best place to go to start new downloaded programs, setting TOR to work (I got pretty close but then something always goes wrong:)) I must be too used to windows and trying to follow windows logic, which doesn't work here. I'm cool with the terminal and everything, but so far dealing with linux was a bit frustrating to me. I really want to figure that out - as my plan is to use everything open source..

I haven't found videos for total linux idiots like me - there is always an assumption that I already know the basics, but I don't.

Thanks in advance,
JJ

---

### Post by idoitprone on 2012-03-25
> **jjtech77 said:**
> [SIZE=2]Hi[/SIZE],

 [B]google-chrome-stable depends on libcurl3; however:
  Package libcurl3 is not installed.[/B]

it says the problem

just do```
 sudo apt-get install libcurl3
```

---

### Post by jjtech77 on 2012-03-25
idoitprone - thank you so much, you're a star:) I've never received quicker support in my life:) 

JJ

---

### Post by idoitprone on 2012-03-25
> **jjtech77 said:**
> idoitprone - thank you so much, you're a star:) I've never received quicker support in my life:) 

JJ

well your problem is easy

i dont really need to follow up as you can see i followed up in 2 hrs

---

