---
title: "Flash crashed :( bad sound quality"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by rima on 2012-04-09
Just now, Adobe Flash crashed.
I tried playing the videos again, but the video and sound quality is really laggy. 
Reinstalled Flash using FlashAid, but the problem is still the same
Any ideas?

---

### Post by houseworkshy on 2012-04-09
If you also have gnash installed at the same time it can cause conflicts.

---

### Post by rima on 2012-04-09
The thing is, it used to work better before until that crash :( I tried Chrome and it's the same thing.
It kind of plays and stops, plays and stops, plays and stops really quickly, if you know what I mean.
Is there a solution to this?! It worked fine before

---

### Post by houseworkshy on 2012-04-09
You could try uninstalling it using "sudo apt-get purge" which will remove settings too, follow that with "sudo apt-get autoremove" to get rid of redundant dependancies.  Remove the hidden folder .macromedia when you've backed up bookmarks/passwords etc.  Then when you reinstall it should be genuinly a clean install.

When it comes to putting flash back in again try the "flash non-free...." from the repositories, go via the synaptic package manager.

If you do have gnash and want to use flash definately get rid of gnash.  You may have installed it with some sort of flash player.  

There is also a sticky thread which resolved a similar problem for me ( wasn't supposed to be fixing the flash and other video problems, it just did.  No idea why but you could try it. ) [http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)  In fact maybe try that one first.

---

### Post by lovinglinux on 2012-04-09
Please click Flash-Aid Help menu, generate a report and post here.

I am not sure if your issues are related to latest flash updates, but you could try to disable hardware acceleration.

See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

If the problem happened only after the crash and not because any updates, then clearing the cache and the cookies might solve the problem.

---

### Post by rima on 2012-04-10
All of a sudden it works now O.O I think it might be something to do with me rebooting my computer XD or the disk check XD But it does work. (At least it does on Chrome and FF.)
Thanks for your help anyway! :) Sorry for the false alarm :(

---

### Post by cmccauley on 2012-04-13
Similar problem here. Dreadful audio quality. Turning off hardware acceleration isn't a solution for this - it's for the strange colour issues that some users have reported.

---

