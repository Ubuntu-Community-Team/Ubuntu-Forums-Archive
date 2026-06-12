---
title: "Runnin' as Root...."
date: 2009-10-03
forum: Recurring Discussions
---

### Post by kfitzenreiter on 2009-10-03
I was getting frustrated trying to delete some useless files after an unsuccessful attempt to get apache2 server working, so I hauled off and after some doing I logged into ROOT.

It's almost like rooting through my parents stuff when I was a kid.

But seriously, other than me deleting my OS by accident am I really at greater risk for viruses or system takeover?  I'm not one to just delete files willy-nilly so I'm just curious if I'm going to cause a tear in space-time or what....

Your thoughts???

P.S.  I made my desktop background for root this picture of this guy dressed up like God in white robes and the long beard.  It's great!!!

---

### Post by stwschool on 2009-10-04
Most of the security issues on Windows are due to users running admin accounts by default. It's not a great idea, and sudo/gksudo can always get you what you need anyway.

---

### Post by kfitzenreiter on 2009-10-04
Very true, very true.

I kind of play system administrator for my dad.  This past windows reinstall I gave him a limited user account.  So far he hasn't trashed windows xp yet, but give him time...give him time..  LOL

---

### Post by blueshiftoverwatch on 2009-10-04
> **kfitzenreiter said:**
> But seriously, other than me deleting my OS by accident am I really at greater risk for viruses or system takeover?
I would venture to guess that running as root on a Unix-like OS is much safer than on a Windows OS.

---

### Post by Sean Moran on 2009-10-04
One thing reckon I've learned to do a little better than before over this last month has been to stop habitually running straight for the Users and Groups config to unlock the root account like I used to, because I was in the habit of using **su** (and thought that was really tricky for an old timer), and hadn't worked out the power of **sudo nautilus** which seems about as powerful/hazardous as it ever needs to get, for the basic amateur sorts of tasks I usually get up to on a desktop client system, and probably just as versatile on a server.

It's also good to know that after the inaugural user that was given on installation has adduser'ed an alter-ego or real person in the vicinity, the **sudo]** functions aren't offered the newbie by default.

I haven't tested all this out in great detail, so just a personal opinion on the rare need for a full root session or even **su** when **sudo** seems to handle admin things fairly well.  When in Rome ...

---

### Post by stwschool on 2009-10-04
> **blueshiftoverwatch said:**
> I would venture to guess that running as root on a Unix-like OS is much safer than on a Windows OS.
Safer but still exposing yourself to unnecessary risk. Why do it when sudo and gksudo do the job?

---

### Post by blueshiftoverwatch on 2009-10-04
> **stwschool said:**
> Safer but still exposing yourself to unnecessary risk. Why do it when sudo and gksudo do the job?
I wasn't advocating running as root, Just pointing out that it would be a safer security risk to take on Linux than Windows.

---

### Post by stwschool on 2009-10-04
The obvious problem with running as root is that you run programs as root. Firefox with root permissions.. there's an accident waiting to happen. And yes I know Firefox is more secure than IE but if something manages to execute through firefox your system is owned. Basically at that point you may as well be running windows.

---

### Post by Machnikowski on 2009-10-04
As said above, don't run as root for day-to-day tasks.

---

### Post by Sean Moran on 2009-10-04
> **stwschool said:**
> The obvious problem with running as root is that you run programs as root. Firefox with root permissions.. there's an accident waiting to happen. And yes I know Firefox is more secure than IE but if something manages to execute through firefox your system is owned. Basically at that point you may as well be running windows.
That's one side of the security coin, and then on the other side, you might be lucky enough to spend the rest of the afternoon playing **sudo chmod 777** or **sudo chown self** because everything you did constructively whilst logged in as root is owned by root and it can get a little tedious when you log back in as your normal self and can't change anything you've just done.  
I've accidentally had that problem a few times. :(

---

### Post by stwschool on 2009-10-04
> **Sean Moran said:**
> That's one side of the security coin, and then on the other side, you might be lucky enough to spend the rest of the afternoon playing **sudo chmod 777** or **sudo chown self** because everything you did constructively whilst logged in as root is owned by root and it can get a little tedious when you log back in as your normal self and can't change anything you've just done.  
I've accidentally had that problem a few times. :(
Aye I've had that problem from gksudo nautilus too, it messed up my home directory permissions and caused some untidyness that took a bit of googling to fix. I've got used to CLI for that kind of job now thank god :)

---

### Post by cariboo on 2009-10-04
Instead of logging in as root, use:

```
sudo -i
```

This drops you to a root shell, so far I haven't found anything I can't do.

---

### Post by kfitzenreiter on 2009-10-04
Hello everyone and thanks for the replies.
 
While it was convenient, I probably won't run as root very often given the warnings about firefox and malicious code. I will say, however, that I did try to run nautilis as root (sudo not logon style), but I had no luck with it...
 
I was playing around with windows remote desktop and vnc server and the ubuntu versions of terminal viewers and such. I was able to take over xp from ubuntu and take over ubuntu from xp so it wouldn't be too much of a stretch, I suppose, for someone to take advantage of this from a "remote" location. On the positive side, I do have strong passwords on all my machines. As an aside, I was even able to control my xp machine from my ipod touch. Kind of scary, but I can't wait to mess around with my wife when she's on the pc. The ipod complained about memory being low--gee, I wonder why LOL--but it was still pretty cool.
 
Oh, well, sorry about the rambling.

---

### Post by starcannon on 2009-10-04
> **kfitzenreiter said:**
> I was getting frustrated trying to delete some useless files after an unsuccessful attempt to get apache2 server working, so I hauled off and after some doing I logged into ROOT.

It's almost like rooting through my parents stuff when I was a kid.

But seriously, other than me deleting my OS by accident am I really at greater risk for viruses or system takeover?  I'm not one to just delete files willy-nilly so I'm just curious if I'm going to cause a tear in space-time or what....

Your thoughts???

P.S.  I made my desktop background for root this picture of this guy dressed up like God in white robes and the long beard.  It's great!!!
Archive files before you delete them, then if they are something necessary, you can just decompress them back from whence they came.
Using root to achieve a task is perfectly normal, but running as root for everything, that is not advised. You actually don't even need to run as root to delete a pesky file:
```

sudo rm /path/to/file.ext

```will achieve the desired result, without needing to be logged in as root.
If it's a directory you need to blitz:
```

sudo rm -R /path/to/folder

```again, no need to log in as root, the folder will be removed, and desired result achieved.

GL and HF

---

### Post by aysiu on 2009-10-04
Since this thread has been pretty civil, I think it's better to just end here it before it gets ugly.

More details about root logins here:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

