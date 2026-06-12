---
title: "Hardy Heron Update"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Brian R. on 2008-04-26
Help!!
Just downloaded Hardy Heron and updated Gusty Gibbon, but now the following System/Administration programs are not working.

Synaptic Package Manager
Software Sources
Login Window
Hardware Testing

The Starting Administrative Application tab shows at the bottom of the screen and then disappears, nothing else happens.

Also Update Manager does the same when ask to check for updates, and then will not close, only way to close it is to crash. After restarting i get the message Crash Report Detected, i click on it and Starting Administrative Application tab shows and then disappears. All else seems to work.

---

### Post by warbread on 2008-04-26
Please post the output of 

```
 :-$ gksu /usr/sbin/gdmsetup
```

from terminal.

---

### Post by Elderlygent on 2008-04-26
As far as I'm concerned the upgrade is a disaster. It has stalled at the installation of WVDIAL Now what do I do? I don't want to wreck the whole thing.

---

### Post by warbread on 2008-04-26
Yes, the upgrade is a pain, as it is every release.  Please be patient.  

What makes you think you've wrecked anything?  A stalled package installtion isn't the end of the world.

---

### Post by nina_aoki on 2008-04-26
Hitchhiker's Guide to the Galaxy: Don't Panic!

The servers have been extremely overloaded, so perhaps something has stalled.  Did you allow the install to complete before you forced a crash?  Also -- the update manager has been extremely slow as predicted - so if you can, let it sit a bit and don't freak if something doesn't happen within the first 30 seconds.  It took me close to four hours to update one machine.

The upgrade is **not** a disaster.

Please describe exactly what the problem is.

- nina

---

### Post by Brian R. on 2008-04-26
Have tried that, again the Starting Administrative Application tab shows at bottom of screen and then nothing. So tried with sudo and get the message "sudo: unable to resolve host bucky-desktop".

---

### Post by opossumjack on 2008-04-27
You should look in System>Administration>Network settings

In the "Host" tab you should look for your host and edit it to remove the ".WORKGROUP" (or anything else) that was appended to your host name. 

It worked for me... Hope it will work for you too... :)

---

### Post by rlogan on 2008-04-27
Same here, on both of my machines here that were upgraded the same thing happened. So just fixed the host bit and synaptic took off.

Mind you the new install on the laptop worked fine with wubi, had to give it a try

---

### Post by Hesperion on 2008-04-27
Whew!...That's why we love the noobie forum. LOL> I just had the very same thing happen and guess what, you were right there for me. Thanks.

---

### Post by Brian R. on 2008-04-28
Thanks wish i'd got that before i made the decision to down load the iso file and do a full new install. which went well, only have to find a way to get my windows machine to see ubuntu. Will put in a new post.

---

### Post by jmore9 on 2008-04-28
I tried the online update from 7.10 to 8.04 but it stopped about half way and never got going again .  So i waited about 45 minutes then went and downloaded the dvd and used that as a clean install .  It  works very good,  I am pleased with the way hardy is snappy it guess the word.  But i could not upgrade from 7.10 to 8.04 online -- yes this is as most of the previous ones were also.  All in all the dvd install went very well Except trying to update the mirrors.  That never happened it just stopped for about 40 minutes, i then unhooked the ethernet cable and started over and went perfectly that way , updated the sources after the install was done.

---

