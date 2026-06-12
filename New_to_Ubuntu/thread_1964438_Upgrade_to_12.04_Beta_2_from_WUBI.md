---
title: "Upgrade to 12.04 Beta 2 from WUBI?"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by ACuriousGuy on 2012-04-24
I installed Ubuntu 11.10 on my Vista laptop using WUBI. If I run the "update-manager -d" command will that update my installed version or will it want to install the whole thing on my system. I set up 15 GBs of space when I used WUBI because I need to have Winblows installed also for work. 

Any help is greatly appreciated.

---

### Post by 3rdalbum on 2012-04-24
> **ACuriousGuy said:**
> I installed Ubuntu 11.10 on my Vista laptop using WUBI. If I run the "update-manager -d" command will that update my installed version or will it want to install the whole thing on my system. I set up 15 GBs of space when I used WUBI because I need to have Winblows installed also for work. 

Any help is greatly appreciated.

It will update the installed version. Instead of having 11.10 inside the Wubi file, you'll have 12.04. I hope that clarifies things for you.

I can't comment on how well an in-place dist-upgrade works with Wubi... anyone got any thoughts?

---

### Post by grahammechanical on 2012-04-24
This kind of operation is being tested throughout this week. This is a link to the test case:

[http://testcases.qa.ubuntu.com/Testing/Cases/WubiUpgrade]("http://testcases.qa.ubuntu.com/Testing/Cases/WubiUpgrade")

This is what others have found when running this test:

upgrade i386

[http://iso.qa.ubuntu.com/qatracker/milestones/214/builds/15904/testcases/1291/results]("http://iso.qa.ubuntu.com/qatracker/milestones/214/builds/15904/testcases/1291/results")

upgrade amd64

[http://iso.qa.ubuntu.com/qatracker/milestones/214/builds/15904/testcases/553/results]("http://iso.qa.ubuntu.com/qatracker/milestones/214/builds/15904/testcases/553/results")

Have you thought about joining in the testing program? Your real life experience is valuable.

[https://wiki.ubuntu.com/U+1/DeployedProjects/rc-iso-testing-main]("https://wiki.ubuntu.com/U+1/DeployedProjects/rc-iso-testing-main")

Regards.

---

### Post by Frogs Hair on 2012-04-24
Back before beginning ! Although Wubi Upgrades work for some they can be problematic. The nice part it is easy to reinstall . At the moment there are only test versions of Wubi available for 12.04 and Wubi will not be included with the ISO.

---

### Post by Frogs Hair on 2012-04-24
Here are the test versions of Wubi in case the upgrade goes wrong . 

[http://people.canonical.com/~evand/wubi/precise/](http://people.canonical.com/~evand/wubi/precise/)

---

### Post by bcbc on 2012-04-24
The upgrade worked flawlessly when I tested it (earlier this week). Note that it doesn't estimate the required space correctly (bug [lpbug]986272[/lpbug]) so make sure you have plenty of free space (I'd guess a minimum of 3GB, preferable more)

Just back up the \ubuntu\disks folder before running the upgrade - then you can copy it back over if it fails.

---

### Post by ACuriousGuy on 2012-04-27
Hey everyone. Just wanted to let anyone reading this know that the upgrade went fine. Just one issue. Not a bug but something I didn't know or expect. Maybe posting this will help someone else. After the downloading was done and the installing had started, it seemed to stop on something like the debconf??? (something like that). It spent an hour or so there. I eventually went to bed. In the morning it was still stuck on that (in the terminal window view of the upgrade manager?). Anyway, I was about to consider just shutting down the computer and starting from scratch with a new WUBI install when I decided to click on "Details." That showed me a window in which I had to hit the tab key (I think it was the tab key) once or twice to have "OK" highlighted. Hit "Enter" and it started moving again. I *think* there were two more windows where I had to hit "OK." However, if I hadn't clicked "Details" I wouldn't have know that.

This might be a situation where Ubuntu automatically shows the window you see after you click "Details." New users (or users who haven't used it in a long time and are re-investigating) might not think about clicking on "Details" and therefore assume that something got broken in the upgrade. That was my first thought (again, typical Windows user who is used to stuff breaking when the OS is updating/upgrading itself). :-k   :-k

Simply show the details by default whenever something is going to require some interaction from the user. I think that might be a good idea. 

I would have posted this on the testers page but wasn't really sure how to join it. :redface:    :oops:

---

