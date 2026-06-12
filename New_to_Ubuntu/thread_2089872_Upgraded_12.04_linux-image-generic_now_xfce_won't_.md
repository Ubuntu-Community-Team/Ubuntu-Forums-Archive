---
title: "Upgraded 12.04 linux-image-generic now xfce won't start"
date: 2012-11-30
forum: New to Ubuntu
---

### Post by thepreacherswife on 2012-11-30
Update manager had several updates for my Xubuntu 12.04 this morning but when I tried to install all of them I got some sort of failure message like "the daemon dies" or something similar. So I upgraded a few items on the list to see if it would take. Per var/log/apt/history.log:
 
perl (to 5.14.2-6ubuntu2.2)
dh-apparmor (to 2.7.102-0ubuntu3.5)
perl-base (to 5.14.2-6ubuntu2.2)
perl-modules (to 5.14.2-6ubuntu2.2)
libperl5.14 (to 5.14.2-6ubuntu2.2)
apparmor (to 2.7.102-0ubuntu3.5)
 
So far, so good. Next I installed:
linux-image-3.2.0-34-generic (3.2.0-34.53)
 
and upgraded:
linux-image-generic (3.2.0.34.37)
linux-generic (3.2.0.34.37)
 
Then I rebooted as instructed. After grub, I got the xubuntu splash screen for an instant, then it went to a shell and asked me to login.
 
Tried to execute thunar and got an error "Cannot open display"
I tried to execute startx and got a bunch of errors, maybe related to the nvidia drivers?
 
Suggestions?
 
Update: I was able to get into xfce by selecting 3.2.0.33 in grub.  Then finished the rest of the 3.2.0.34 installs/upgrades and rebooted.  All better now.

---

