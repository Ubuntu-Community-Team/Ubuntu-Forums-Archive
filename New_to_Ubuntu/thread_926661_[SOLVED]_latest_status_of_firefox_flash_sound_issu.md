---
title: "[SOLVED] latest status of firefox flash sound issue"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by wolfie2x on 2008-09-22
can somebody pls tell me the latest status of Hardy PulseAudio + firefox3 flash plugin sound conflict?
can I finally watch youtube (with sound) while some other media player is open?

hours of googling made me read 101 articles/tips/advice on fixing this from installing libflashsupport then n-something-wrapper blah blah.. bug tickets say they have fixed it but user comments say it doesn't work.. I'm going nuts pulling my hair..

(here's what I know so far:
Hardy introduced the *new* PulseAudio (what was wrong with the old one??); that triggers a bug in FF flash plugin n breaks it; Adobe wont fix it; Ubuntu devs say they can't do anything; )

Ubuntu 8.04.1
firefox 3.0.1
flashplugin-nonfree 9.0.124.0ubuntu2

---

### Post by kansasnoob on 2008-09-22
Look at post #7 here:

[http://ubuntuforums.org/showthread.php?t=919695](http://ubuntuforums.org/showthread.php?t=919695)

---

### Post by taqkavar on 2008-09-22
you can get libflashsupport package to fix the audio problem, but in return, you get random firefox crashes.
here is the bug report page:
[https://bugs.launchpad.net/ubuntu/+source/libflashsupport/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/libflashsupport/+bug/192888)

---

### Post by wolfie2x on 2008-09-22
> **kansasnoob said:**
> Look at post #7 here:

[http://ubuntuforums.org/showthread.php?t=919695](http://ubuntuforums.org/showthread.php?t=919695)

thanks a zillion! that worked! 

The post#7 points to [this page]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472") where I simply followed the steps and everything works perfectly!
 
On a side note, I'm surprised 4 hrs of my googling didn't take me there. Shouldn't there be a official "work-arounds" page for Hardy where the latest state of all such common bugs/solutions are listed? It'll save a lot of time for many ppl.

---

### Post by wolfie2x on 2008-09-22
There's a always recreatable crash with the new Shockwave Flash 10.0 r12 plugin: "Super Wall" in Facebook. Playing any video there will crash FF every single time.
(That's the only crash I found so far.. almost all other flash sites/vidoes work without a hitch)

---

### Post by kansasnoob on 2008-09-22
> **wolfie2x said:**
> thanks a zillion! that worked! 

The post#7 points to [this page]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472") where I simply followed the steps and everything works perfectly!
 
On a side note, I'm surprised 4 hrs of my googling didn't take me there. Shouldn't there be a official "work-arounds" page for Hardy where the latest state of all such common bugs/solutions are listed? It'll save a lot of time for many ppl.

BTW: Flash works great in Intrepid, but since Hardy is LTS they really should implement this into the updates!

---

