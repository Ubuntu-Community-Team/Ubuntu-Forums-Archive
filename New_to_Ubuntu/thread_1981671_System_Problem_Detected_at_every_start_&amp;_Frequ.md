---
title: "System Problem Detected at every start &amp; Frequent Powering down experienced"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by TooRight on 2012-05-17
Am getting seriously fed up with Ubuntu....after a year of it going downhill with the 11 releases, we have now been given this 12.04 pos! arghhh

Upon EVERY boot/login, i get notification that a System Problem has been detected...forget about reporting the error, because trying to triggers another error!!

Have gone through my power settings as well, to try to stop the "powering down" issue that oocurs everytime I get going doing anything...it STILL happens n there's no recovering from it either. All that can be done is to reboot the comp n hold my breath, saving everything I do every 15-30 while i wait for it to happen again.

WTFFF have they done to my ubuntu???

*sighs, anyways, has anyone found any solutions for the two issues i mentioned?

---

### Post by jtarin on 2012-05-17
If you could post the details of the notification it would be a place to start.
How many versions have you installed on the same computer?

---

### Post by prshah on 2012-05-17
> **TooRight said:**
> Upon EVERY boot/login, i get notification that a System Problem has been detected...forget about reporting the error, because trying to triggers another error!!

Heh, I had the same problem, see [http://ubuntuforums.org/showthread.php?t=1971928](http://ubuntuforums.org/showthread.php?t=1971928) 

However, it seems to have solved itself with recent updates. I am now up-to-date.

It still comes, but infrequently. (Maybe 3-4 times a week).

However, I have no issues with shutting down randomly...

---

### Post by GreenWhite on 2012-05-17
You may have a far less problem than imagined.

  Open terminal and type this;


  sudo rm /var/crash/*

  At times this may happen when you have error while updating which cannot be resolved or something else.

---

