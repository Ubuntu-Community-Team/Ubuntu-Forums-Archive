---
title: "Adobe Flash keeps crashing"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by crs501 on 2011-10-11
Hi Folks: I presently have the Ubuntu 10.04 LTS Operating System with Firefox 3.6.23. I've been operating fine for about 6 mos and then all of a sudden within the past 5-6 days the Adobe Flash plug-in has started crashing. Every time I go to YouTube or any other site that requires Adobe Flash I get the message that it has crashed, I may reload and/or send a crash report. I have now sent several dozen crash reports and I have also uninstalled and re-installed the Adobe Flash plugin more than half a dozen times. The problem remained unchanged so I decided to completely re-install Ubuntu 10.04 and The Adobe Flash once again crashed. Am I missing something here? Am I the only person on the planet this is happening to? How do I solve this. And who ever tries to help me - - I am not a programmer or developer, just a PC user so I'm somewhat limited in what I know how to do. Please help!!!

---

### Post by dolphin194 on 2011-10-11
Have you considered trying Ubuntu 11.04?

---

### Post by BlinkinCat on 2011-10-11
Have you considered Flash-Aid?

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by thatguruguy on 2011-10-11
Actually, updating to 11.04 may be unnecessary, but I would strongly suggest updating your firefox to a more recent version.  To do so, you'll first want to install the official ppa (personal package archive) of the Mozilla Team.  To do so, open a terminal and type:
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
```
You will be prompted for your password, and then the package manager will install the keys for the repository.

When that's done, type:
```
sudo apt-get update && sudo apt-get upgrade
```
It will ask if you want to upgrade certain packages; firefox will be among them.  Choose "y".

Then, install the Flash-Aid plugin, as suggested in your other thread.

---

### Post by crs501 on 2011-10-12
Typing the code exactly as suggested did not yeild the indicated outcome-Thanks anyway!

---

### Post by crs501 on 2011-10-12
Have tried to acquire Flash Aid several times with no success - I have no idea what I'm doing wrong! Thanks anyway!

---

### Post by crs501 on 2011-10-12
Didn't re4alize it was available, will check it out! Thanks!

---

### Post by crs501 on 2011-10-12
Thanks to all who tried to help - I just downloaded & installed the newest Mozilla Firefox and my Flash problem appears to have gone away. Thanks again to all who responded - much appreciated!!!

---

### Post by thatguruguy on 2011-10-12
Happy to help.  You may want to mark this thread as solved.

---

