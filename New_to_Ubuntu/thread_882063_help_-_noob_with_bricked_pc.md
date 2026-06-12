---
title: "help - noob with bricked pc"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by erutufon on 2008-08-06
hello
I have just managed to brick my pc running ubuntu, and am not sure how to sort it out.  the pc boots up, I log in as normal then my desktop comes up, all fine.  however, no buttons work (applications, system, places).  

if I try to open a folder on the desktop I get to see inside, but if i try to look in the file system the pc freezes and has to be manually turned off.
Pressing keys does not do anything.  

I tried escape when grub was loading, and got to recovery mode, however this has no effect.

I am running ubuntu 8.04, and a noob with a little experience of terminal, enough knowledge to get me into trouble, but not enough to get me out again:(
many thanks for any help!

---

### Post by Blutack on 2008-08-06
Boot into recovery mode.
Create a new user by typing
adduser (new user name)
and follow through the wizard.  
Then reboot and try logging in as your new temp user, and see if that user account works.

---

### Post by billgoldberg on 2008-08-06
If the above didn't work, boot into the livecd, back up your data to an external hdd and reinstall Ubuntu.

Your problems will be fixed in under 30 minutes.

For future reference:

It's a good idea to have /home on a different parition. Then you don't need to back up your data before install an OS.

And be carefull when you are root (through sudo).

---

### Post by erutufon on 2008-08-06
thanks, will give it a try

---

### Post by erutufon on 2008-08-06
billgoldberg - thanks, didn't know you could get into the files by using a live cd.  do you know if there is a thread/wiki for morons such as myself who break their computers, then don't know how to sort themselves out?  :)

---

### Post by billgoldberg on 2008-08-06
> **erutufon said:**
> billgoldberg - thanks, didn't know you could get into the files by using a live cd.  do you know if there is a thread/wiki for morons such as myself who break their computers, then don't know how to sort themselves out?  :)

No.

You could always start one in the community cafe.

lol

---

### Post by Blutack on 2008-08-06
It's a rite of passage, I wouldn't worry about it!
We've all done it once (or twice, or about 13 times...)

---

### Post by erutufon on 2008-08-06
ok I have followed Blutacs advice, and created a new user.  that user now has the same problem.  I reckon I could use the live cd and then boot off that, recover files etc but I would prefer to fix whatevers broken (and hopefully learn a bit).  any ideas?

ps how do you thank people for helping? is there an icon or something?

---

### Post by billgoldberg on 2008-08-06
> **erutufon said:**
> ok I have followed Blutacs advice, and created a new user.  that user now has the same problem.  I reckon I could use the live cd and then boot off that, recover files etc but I would prefer to fix whatevers broken (and hopefully learn a bit).  any ideas?

ps how do you thank people for helping? is there an icon or something?

Yes, the little medal next to the quote button.

--

It's not a big deal to reinstall your ubuntu isntall.

If done it a few dozen times.

I think most people here have.

(note: not because ubuntu is unstable, but because we bricked the system ourselfs)

---

### Post by Blutack on 2008-08-06
Well, what was the last thing you were poking with before it all broke :-) ?
You can boot into recovery mode and then look through the logs:-
dmesg is normally a good place to start.  If there is nothing obviously wrong there, try the other logs.  You can make them easier to read by using less like this.

dmesg | less
or
cat /var/log/whatever | less

That sounds like a rather serious problem and if you are not comfortable with the command line you may save yourself a lot of time, frustration and annoyance by simply backing up and reinstalling - it's much less hassle than with that 'other' operating system.  The exception to this is if dmesg says anything obviously hardwary - lots of things related to disks (ignore cd's) and IO errors are normally not a very good sign at all.

---

### Post by erutufon on 2008-08-06
and now to dig out the boot cd......

cheers for your help. this is one of the reasons I love linux (despite ending  banging my pc with a hammer every so often, due to ignorance) - the community is ace

---

### Post by steveneddy on 2008-08-06
Yeah - I'd reinstall, too.

---

### Post by wolfen69 on 2008-08-06
> **Blutack said:**
> It's a rite of passage, I wouldn't worry about it!
We've all done it once (or twice, or about 13 times...)

yup. i've installed linux probably over 70 times with different computers and different distros. that's how i learned. now nothing scares me, as i can fix just about anything. dont be impatient, and dont worry about screwing up. anyone who knows linux well, probably has made millions of mistakes. but someday the light goes on and you get it. 

it's not about having the perfect computer, it's about having fun and learning. if you can do that, your computer *will* be perfect. :wink:

---

### Post by pi.boy.travis on 2008-08-06
When you first booted into the CD you used to install, did you try "Check CD for Defects"?  That is always a good idea before installing.

---

