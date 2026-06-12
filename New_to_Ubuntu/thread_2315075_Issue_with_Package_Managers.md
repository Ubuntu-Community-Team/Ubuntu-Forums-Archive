---
title: "Issue with Package Managers"
date: 2016-02-26
forum: New to Ubuntu
---

### Post by ChancellorTaco on 2016-02-26
Hello community, I have a couple problems too great for my limited resources, time, and knowledge. They are as follows:
#1 Synaptic Package Manager will not boot up.
     -When I do I am prompted with an error message saying: Either **UNABLE TO GET LOCK **This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first. or some thing along the lines of(I say this because presently it won't even start, the first message is all I get) a package didn't function quite right and I have to run "dpkg --configure -a" I do this and I get the return of "dpkg status database is locked by another process"
#2 Ubuntu Software Center is gumed up
     -A long while ago I tried to delete a file, and I did, but there was one file in the back of the que, that I didn't quite know what it was. Apparently neither did Ubuntu, as to this very moment it's still "searching" for it while I wait for it to cancel. This file sitting there not cancelling itself, prevents me getting rid of both Synaptic, and the source of my issue, Dropbox.
#3 Dropbox/Nautilus don't play nicely with Ubuntu 
     -I thought I would include this merely because it was mentioned above. I was trying to install Dropbox some time ago because I have many important file on there that it would be easier to access if this application was on my machine. It installed but didn't run due to Nautilus not starting right. After trying many times in vain to remedy this issue, I gave up and vowed to deal only with the browser version on this machine. not needing the application if I wasn't going to use it, I first went to Software Center, but that was gumed up, so I instead went to Synaptic. It all was all going well, until I saw the bright shiny lure of the "reinstall" button. I fell for the bright shiny trap. I pressed it and all was going quite well, I took the bait. But not soon after the switch occurred, in configuring Nautilus the loading bar froze and refuse to move. In my frustration, fatigue, stress, as well as ignorance, I restarted my machine in an effort to stop the process and final just remove all files. that where problem #1 came into play.
#4 "sudo apt-get" doesn't work
     -Knowing as little as I do, I do know a thing or 2(I hope 2) using my knowledge learned from Raspberry Pi-like micro-computers, I used the final measure I knew: sudo apt-get --purge dropbox.
only issue, the terminal is trying to interpret "dropbox" as a command. I am mentally chalking this up to the fact that I'm most likely forgetting a crucial option to the command or something of that breed.

If you need more info; I am running Ubuntu 12.04,on a Dell Latitude 2120

---

### Post by ian-weisser on 2016-02-26
Close all applications and all terminal windows...except your web browser. 
Open a new terminal window and show us (copy-and-paste) the **complete** output of the following commands:
```
sudo apt-get update
sudo apt-get upgrade
ls /var/lock
```

---

### Post by ChancellorTaco on 2016-02-27
This is what I got as an output: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[REDACTED]@[CENSORED]:~$

Also as an update, this seems to happen to all apt-get functions.

---

### Post by carydconover on 2016-02-27
Hello Chancellor Taco,

Sounds like you have a process that is stopping all your fun and has the files the product you are trying to use already occupied.  It could be a number of things.  You may have opened many copies for the Ubuntu Software Center.  Happens.  Make sure when you are done with it you left click the X in the top left corner.  It is likely hidden now and only appears when you have your mouse hovering over the Top Bar of the User Interface.  Then the controls appear.  X (Close) - (Minimize to Back Ground) BOX (Full Screen).   Until you get used to using the User Interface it is better to totally close the windows and not put them to the back ground unless you know how to get them to come back to the fore ground.  Usually Hovering the Mouse over the Ubuntu Software Center Icon in left Apps Bar and Left click it and the app comes back to the fore ground right where you were.  Then you can continue on from there.

For the sake of discussion, what different apps have you running now?  Do you know how to list processes?  Your Jobs?  Etc...?

I am confused as to how you got the following results:

> E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[REDACTED]@[CENSORED]:~$


I did the above process and it updated, then upgraded and then showed only one process in the indicated directory.  So the suggestion is apropos.  What was suggested were normal daily basic commands.

---

### Post by cariboo on 2016-02-27
Have you tried removing the lock file from /var/lib/dpkg? in a terminal type the following commands:

```
cd /var/lib/dpkg
sudo rm lock
```

---

### Post by ChancellorTaco on 2016-02-28
That seemed to do the trick. Could you do me a favor and explain in a little more detail of what I just did so I know more of what I'm doing in the future?

---

### Post by jim_deadlock on 2016-02-29
When a package manager starts it creates that file to prevent any other package managers running at the same time. When it's finished it deletes the lock file. What's happened is you've run a package manager and it has somehow terminated without completing properly, so it has left the lock file behind which is preventing any package manager from starting.

---

