---
title: "Help Please! Accidentally deleted /etc/systemd/system"
date: 2016-11-06
forum: New to Ubuntu
---

### Post by cjallaway83 on 2016-11-06
Hi all,

I have managed to accidentally "rm -r /etc/systemd/system". :( :(

Firstly, what have I gone and deleted?
Secondly, anyway to bring it back or somehow rebuild that directory?

I do have a ls-l of the folder before deleting...

Running Ubuntu 16.04 LTS


Thank you!

---

### Post by TheFu on 2016-11-06
Why? Why. Why!

Option a: Restore from backup.
Option b: reinstall the OS.
Option c: probably won't work, but ... boot off a live CD with the same  OS version, patched to the same date as your installed version, then copy over those files, being careful about permissions, ownership, groups, and ACLs.

Why would you delete anything in /etc/ without making a backup first. It is a tiny directory - daily backups of it would take less than 1-2 seconds and use next to nothing for storage.

Oh - and welcome to the forums. ;)  We've all done foolish things like this (and will continue to do it).

---

### Post by cjallaway83 on 2016-11-06
Thanks for reply TheFu and the welcome :)


I know, I'm an idiot. I was following a guide to make sure ssd trim command was going to be running and it said about copying a couple files over.
But then realised that was not for ubuntu 16.04, so when I went to delete the file I got distracted and deleted the whole dir instead of just that file!!

So annoyed as I do not have any backup as I am only a few days in to setting this up, but have put about 10 hours work into config! :(

So my only option is B or C.... I dont think if I can face B..... lol

Heeelp :(((( So C might work?


(edit) Just trying to get my head around this mess....so If I do end up doing B is there any point saving my configs? 
And also, whats the best way to backup in future? :D

So I gotta find a live CD... can you point me in right direction?

---

### Post by TheFu on 2016-11-06
> **cjallaway83 said:**
>  I know, I'm an idiot. I was following a guide to make sure ssd trim command was going to be running and it said about copying a couple files over.
But then realised that was not for ubuntu 16.04, so when I went to delete the file I got distracted and deleted the whole dir instead of just that file!!

A few things are distro specific. I only use LTS releases, so my first experience is with 16.04. Don't like it. Don't want it. Don't need it.  It fixes issues that I don't have. Too bad there isn't any option and still use Ubuntu.

> **cjallaway83 said:**
> 
So annoyed as I do not have any backup as I am only a few days in to setting this up, but have put about 10 hours work into config! :(

10 hours!!!?    Really?   You are really new I take it.  I can install a new system and get all my programs, settings, configs installed in about 45 min. Lots of automation, of course.  Plus, if I have a backup, 45 min to a complete restore from 2am's backup total.

> **cjallaway83 said:**
> 
So my only option is B or C.... I dont think if I can face B..... lol Get thee some backup religion. Please.  Like anything, practice makes you better.  A base install takes about 15 min for me these days.  It isn't a big deal. If I have another system that is similar, getting to that level takes about 15-30 minutes more - automation.

> **cjallaway83 said:**
> 
Heeelp :(((( So C might work?  Pigs might fly too, without an aircraft.

> **cjallaway83 said:**
> 
(edit) Just trying to get my head around this mess....so If I do end up doing B is there any point saving my configs? 
And also, whats the best way to backup in future? :D
10 hours in?  I wouldn't bother.  
Backups are a very personal thing. "Best" is highly subjective. I mostly work on servers and have 20+ yrs of experience, so the way I backup probably isn't useful to you.  I've posted about backups in these forums enough. Search and read. My signature has lots and lots of links for backup information too. A backup is only 10% of the problem.  The other 90% is to actually restore it. If you do backups and don't test the restore, you've only done 10%.  Took me about 5 times to restore before I had a backup that actually worked.  Just sayin.  I wasn't getting enough and I didn't want EVERYTHING - which is very storage and time wasteful.  For about the last 7 yrs, I've been backing up "just enough" to restore and have a system almost exactly like what I had at the backup point.  I do not backup the base OS or any packages installed through the package manager. That saves about 4G per system.

> **cjallaway83 said:**
> 
So I gotta find a live CD... can you point me in right direction?

Errr. I hate to say this, but if you don't know that already, I can't help. I have doubts you'll be able to complete C too. How did you install Ubuntu to start?

---

### Post by cjallaway83 on 2016-11-06
> **TheFu said:**
> A few things are distro specific. I only use LTS releases, so my first experience is with 16.04. Don't like it. Don't want it. Don't need it.  It fixes issues that I don't have. Too bad there isn't any option and still use Ubuntu. 

Not sure I quite understand what you mean.... I am using LTS.


> **TheFu said:**
> 10 hours!!!?    Really?   You are really new I take it.  I can install a new system and get all my programs, settings, configs installed in about 45 min. Lots of automation, of course.  Plus, if I have a backup, 45 min to a complete restore from 2am's backup total.

 Get thee some backup religion. Please.  Like anything, practice makes you better.  A base install takes about 15 min for me these days.  It isn't a big deal. If I have another system that is similar, getting to that level takes about 15-30 minutes more - automation.

  Pigs might fly too, without an aircraft.

Yeah it's my first time with Linux since I was about 17/18 and messing around with it then. Complete newbie! Is 10 hours bad? haha! Well it included me reading guides, finding out what I needed to put into confs etc. I had setup SSH, Apache, SSL, Mail, DKIM, TLS, SPF, Squid, SARG, Firewall etc. (I think that was all) Oh and trying Xubuntu 16.10 which kept crashing.



> **TheFu said:**
> 
10 hours in?  I wouldn't bother.  
Backups are a very personal thing. "Best" is highly subjective. I mostly work on servers and have 20+ yrs of experience, so the way I backup probably isn't useful to you.  I've posted about backups in these forums enough. Search and read. My signature has lots and lots of links for backup information too. A backup is only 10% of the problem.  The other 90% is to actually restore it. If you do backups and don't test the restore, you've only done 10%.  Took me about 5 times to restore before I had a backup that actually worked.  Just sayin.  I wasn't getting enough and I didn't want EVERYTHING - which is very storage and time wasteful.  For about the last 7 yrs, I've been backing up "just enough" to restore and have a system almost exactly like what I had at the backup point.  I do not backup the base OS or any packages installed through the package manager. That saves about 4G per system.


Ok thank you. I have alot of experience in hardware and windows based machines rather than linux. Will read up. I see there is a backup system already built in to desktop version (deja dup?) so will give that a go.

> **TheFu said:**
> 
Errr. I hate to say this, but if you don't know that already, I can't help. I have doubts you'll be able to complete C too. How did you install Ubuntu to start?

Installed from USB (ubuntu iso). Sorry, didn't know what it was, just looked it up, its just the test ubuntu on the iso which doesnt install?


I think I will just have to bite the bullet and do it all again. Is there anything I can do to make my life easier? Like saving all my confs somehow?

---

### Post by RobGoss on 2016-11-06
> So annoyed as I do not have any backup as I am only a few days in to setting this up, but have put about 10 hours work into config!

 The one good thing we learned from this is we know better next time right!

One good thing about Linux once you get the hang on it is really simple especially installing different distributions I make it a habit to have anything that's really important on a external drive. Setting up any Ubuntu desktops will get easier with time don't rush things because it's a learning curve and you'll get better with time

---

### Post by TheFu on 2016-11-06
Putting important things in at least 3 differerent locations is important.  Don't be one of the people we've all heard about who think an external "backup drive" is the only place to keep important stuff. It needs to be both on the internal disk AND external backup disk AND 1 other place - a disconnected HDD, inside encrypted cloud storage, at a friend's house, on an encrypted disk you take into work weekly ... somewhere else.  Need at least 3 copies, on 3 different storage devices, on 3 different computers (not the same 1) in at least 2 different physical locations.

The point about LTS and different releases was that systemd is new in 16.04 (at least to me), since I came from 14.04.  Personally, I think it is alpha-level code and shouldn't have been put into an LTS release.  Perhaps in 2-3 more years, it will be ready for production. Perhaps.

Deja Dup tends to have issues. Be certain to do some research before committing to any backup tool.  Look for issues and problems BEFORE. Learn from the mistakes of others so you can avoid them.  My impression (probably wrong) is that GUI backup tools shouldn't be used for system/server backups, period.  If you just want to backup your personal HOME, great, then use a GUI tool.  Otherwise, the backup tool needs to run with elevated privileges and automatically, which means it cannot be a GUI. There are problems running GUI tools with elevated privileges without some care.  Backups on Unix systems need more than just the files. The owner, group, permissions, xattrs and ACLs need to be captured with each saved version too.

A live-CD is the same as a live-Flash drive or an "Test Ubuntu" option from any media.  The point is NOT to be running the installed OS. This is like a super-restore disk and extremely handy to correct bonehead mistakes.  Personally, I keep a flash drive setup with about 10 different Linux distros just to have the tools I need available from a single, tiny, storage device.

"Anything" - sure.  Are you able to do these things with minimal knowledge ... probably after 40 hrs of research, so only you can decide if learning that stuff is worthwhile now or not.  Making a backup or $HOME and /etc/ is just smart - always, daily, have a versioned, backup of those things.  

To get a system back completely, you'll need much more. What you need depends on what you install, where you install it, how and where the configs are placed, etc ... every Linux system is a little different unless you use DevOps techniques and script the configuration.  We call this "infrastructure as code."  If you have 20 servers that are nearly identical, it makes much more sense than if you have 1 system or 5 systems that are different.  DevOps is a hot skill to know - experienced devops Linux people are in extremely high demand. Same for OpenStack folks.  Put those two skills on a resume - and employment really isn't an issue.

---

### Post by oldfred on 2016-11-07
I do not know servers as TheFu.

Another alternative may be to just create another 10 to 20GB partition and do another Ubuntu install. Then you may be able to just copy /etc/systemd/system back into your system.

But I would fully backup everything. I do not have a server configuration which has a lot more in /etc. The few files I do manually edit in /etc, I also copy into /home so my backup of /home includes those. And I also can install Ubuntu in just a few minutes, now have scripts to do probably 80% of configuration. But I typically install each new version several times, but keep current LTS as main working install, so I have lots of practice installing.

There is also "dirty" install where you do not reformat / partition. But it would also reset all configuration files back to defaults and it would seem you edited a lot. Only advantage is where you have added a lot of files as they would then not be erased.

---

### Post by TheFu on 2016-11-07
I love the idea of another small install to get the files needed.  Be certain the exact same version of the distro is used and that fresh install is patched to the same level.  
I only fear that doing it on the same machine will risk other parts of the install for someone not well-versed in partitioning. It is easy to accidentally wipe a system. 

If you are good with partitioning, this is a no-brainer. "Server" shouldn't need anywhere near 10G ... I did a minimal install into a VM yesterday as part of a show-n-tell exercise. It used a little over 3G of storage.  If you use a VM technique, the risk of accidentally wiping the current data is almost zero.  How comfortable with virtual machines are you?  And are you positive that only the systemd directory was removed?  Any reason to think other locations were impacted too?

---

