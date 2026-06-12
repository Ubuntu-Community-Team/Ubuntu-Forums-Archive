---
title: "Can't get rid of Residual Config from old kernel"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by luceerose on 2008-04-26
Synaptic won't let me uninstall residual config for two older kernels.
Refer to my screenshots.
You can see from the 2.6.24-11 entry that I have been sitting on this problem for a while. I thought it would go away when the stable packages rolled around but, obviously, it hasn't.
Any ideas ???

---

### Post by warbread on 2008-04-26
Have you tried a 'sudo apt-get update', or a hitting 'refresh' in Synaptic.

---

### Post by luceerose on 2008-04-26
I've updated, auto-removed, etc.. dozens of times since this first appeared.

---

### Post by Belak on 2008-04-26
I believe you have to reinstall them and then Compleetly Remove both of them. Not just remove them. You mght not even have to install them again.

Cheers,
Belak

ps - I don't think you'll have to reboot until you're done

---

### Post by luceerose on 2008-04-26
Mark for Complete Removal fails as seen in my screenshot, 
also won't let me re-install them either.

---

### Post by Belak on 2008-04-26
Do you get the same thing when you run
sudo apt-get autoclean

---

### Post by luceerose on 2008-04-26
Yep, just ran an autoclean. The autoclean itself went off without a hitch, but I'm still getting the same error.

---

### Post by Belak on 2008-04-26
So, you get the same error with a re-install?
That's weird.

If I had the terminal output from when it was uninstalled, I could help you... geez... this is annoying.

Same thing with just an apt-get clean, I'm assuming?

Edit:
What folders are there when you run the following 2 commands:
cd /lib/modules/
ls

Edit 2:
You may be able to get rid of the residual config/files with the following 2 commands (if you got more than 1 folder). You may also want to get rid of any folders in here apart from your current kernel.
cd /lib/modules/
sudo rm -R 2.6.24-11-generic

---

### Post by frafu on 2008-04-29
Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=757336") for another solution. 

Cheers

---

### Post by luceerose on 2008-05-08
> **frafu said:**
> Have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=757336") for another solution. 

Cheers

SOLVED
&
SOLVED

The above solution worked. Thanks frafu.
I just created a "2.6.24-11-generic" & a "2.6.24-14-generic" folder
in both the /lib/linux-restricted-modules & /lib/modules folders.

Then opened Synaptic and tried complete removal again & it worked.
Then I just went back & deleted the four folders I created.

Again, Thanks frafu.

---

### Post by cambunctious on 2009-11-21
Thank you!  I had a very similar problem with an old backports package after a kernel update.  The provided link to the other thread is broken but i was able to fix the problem with larsenguitars's summarized solution.

By the way, what theme is that in your screenshot? : )

---

