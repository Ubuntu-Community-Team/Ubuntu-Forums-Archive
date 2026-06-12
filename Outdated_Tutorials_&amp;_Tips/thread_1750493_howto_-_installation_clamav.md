---
title: "howto - installation clamav"
date: 2011-05-05
forum: Outdated Tutorials &amp; Tips
---

### Post by TheBelgian on 2011-05-05
Hi, I had a problem problem installing KlamAV. Being a total noob to Ubuntu, I was looking for a virus scanner and started my search in the software center.

Sure enough i found Klamav, downloaded it and tried to install it. But apparently you need to have clamav installed first. OK, one step forward, two steps back.

Clamav was not found via the software center so i dl'd it from the web, and tried to install it. But during installation it said: permission denied in folder /usr/local/lib. 

Via #ubuntu-beginners i got instant help, and the next steps took me to a solution:

1) install sudo first (./configure)

With me it failed since 'cannot find -lpam'. So I installed the missing lib using: # sudo apt-get install libpam-dev

2) try to install sudo again (./configure)

Again it failed since 'permission denied /usr/local/libexec'

3) So apparently, I just needed to use the magical command # sudo apt-get install clamav to get clamav installed
4) Installation ended on 'ldconfig deferred processing now taking place'
5) Run clamav typing #clamscan
6) It worked!
7) Nice, but can be better with a GUI. So i installed clamtk again using the magical command # sudo apt-get install clamtk
8) Simple but effective GUI. scan process is running in the background as I'm typing this

I still don't understand everything that happened, but it works!

Hope this helped for you.

wij

PS: thx <atari314>

---

