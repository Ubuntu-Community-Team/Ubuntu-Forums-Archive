---
title: "updates fail - DNS error"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by skintner on 2012-01-12
Ubuntu 10.04 desktop
 
It shows a list of udates that need to be installed.  I say ok, give my password, update starts and then errors out:
 
unable to resolve security.ubuntu.com
 
Other than upgrade to 11.0?, what can I do to solve this? Other names are being successfully resolved (msn, yahoo, etc), so I think my dns settings are ok (dhcp).
 
thanks
steve

---

### Post by spacecheck on 2012-01-12
What are the contents of your /etc/apt/sources.list file?

Post them here, so we can see if anything is amiss.

Good luck!

---

### Post by skintner on 2012-01-12
Hi there spacecheck... uhm, I don't have the first clue about that file... I will look into it and post what I can.
 
I just tried: sudo apt-get install openssh-server on my server box.  The install starts and gives a report of disc space it will use.  After that it is giving out similar error, unable to connect to the source files... I would be it is same problem having to do with urls and dns resolution...
 
steve

---

### Post by spacecheck on 2012-01-12
How about first trying the solution cited in this link:

[http://ubuntuforums.org/showthread.php?t=1480604&highlight=signatures+invalid&page=3](http://ubuntuforums.org/showthread.php?t=1480604&highlight=signatures+invalid&page=3)

Let me know the results. IF it works, you can use the thread tools to mark this thread Solved.

Then you could try installing the additional software. If it doesn't work, you can use the file manager to go to the folder /etc/apt and open the file sources.list and copy the data from that and paste it into a response.

Good luck!

---

### Post by skintner on 2012-01-13
The first line ran fine, but the cd line returned "no such command"...  I am assuming that is similar to dos change directory command.  This was on server... I haven't run it on the desktop box, but will try on it and let you know.
 
steve

---

### Post by skintner on 2012-01-13
same error on the desktop box -- sudo: cd: command not found
 
so what now?

---

### Post by skintner on 2012-01-13
Ok, so I double clicked the sources.list and it opened in an application that said the sources had changed and should it update from the internet... it updated the list and now the update program is updating the operating system... hmmm...
 
I'm learning...

---

### Post by skintner on 2012-01-13
So the updates finished and now it's throwing a Gnome power manager default configuration failed to install... consult your administrator. When it's idle for a few minutes the monitor gives an unsupported frequency error...  I have changed the refresh rate to 60hz, no screen saver, power options OFF and still it goes haywire.
 
this is way more hassle than it should be.

---

### Post by spacecheck on 2012-01-13
> **skintner said:**
> So the updates finished and now it's throwing a Gnome power manager default configuration failed to install... consult your administrator. When it's idle for a few minutes the monitor gives an unsupported frequency error...  I have changed the refresh rate to 60hz, no screen saver, power options OFF and still it goes haywire.
 
this is way more hassle than it should be.
Hi Steve,

I'm glad you were finally able to update the system! Since the cited problem has been resolved and updating now works, please use the thread tools to mark this thread as [Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

If you are now experiencing other, different problems, please open a new thread for it/them, so that others will also be able to pay attention to them and get a chance to assist you.

Good luck!

---

