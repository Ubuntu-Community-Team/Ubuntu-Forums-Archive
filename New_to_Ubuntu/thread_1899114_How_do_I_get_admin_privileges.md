---
title: "How do I get admin privileges?"
date: 2011-12-22
forum: New to Ubuntu
---

### Post by avg_joe on 2011-12-22
Hi, all.  First off, sorry if this has been discussed to death...I did a bunch of searching, and reading, and couldn't find my particular answer.

Second....I don't know nuthin' bout no kubuntu voodoo stuff.  I do pretty good on winxp at getting around.  I don't do any technical work type stuff on my computer...just the basics.  E-mail, forums, pictures, some simple home video editing, general internet surfing, and auction sites.:lol:

Which leads me into my particular problem.

I purchased at auction, a computer that is running kubuntu.  I didn't set it up, I didn't install it...I didn't do anything but plug it in, and turn it on.
There is no user log in prompt to start the computer, but I am unable to upgrade, or install anything, because everything requires administrative privileges.
How do I get administrative privileges?  I have no way to find the original admin.  I don't know anything about programming.  Very frustrating....The journey of a thousand miles begins with a single step....but some bastard tied my shoes to each other, and I need administrative privileges to untie them.

Any suggestions?(about the computer...the shoes thing was just metaphoric...I got a knife in my pocket that gives me admin privileges in that situation)

Thanks,
avg_joe

---

### Post by pbpersson on 2011-12-22
I know there is a way to do that.  I think you need to download and burn the latest Kubuntu CD, then boot from CD, get into the admin stuff and reconfigure the root account.  I have never done it.

However, while you are at it, why don't you just blow away what is on the hard drive now and setup a new modern Kubuntu machine?  I bet what is on that machine is old.  Do you care about any data on the machine?

Just a thought....

---

### Post by wildmanne39 on 2011-12-22
Hi, here is a link for resetting the password.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Thanks

---

### Post by avg_joe on 2011-12-22
> **pbpersson said:**
> I know there is a way to do that.  I think you need to download and burn the latest Kubuntu CD, then boot from CD, get into the admin stuff and reconfigure the root account.  I have never done it.

However, while you are at it, why don't you just blow away what is on the hard drive now and setup a new modern Kubuntu machine?  I bet what is on that machine is old.  Do you care about any data on the machine?

Just a thought....

I think I will have the latest, greatest if I can get through this admin privilege thing.  The first thing it did when I connected it to the internet was download all the updates, and whatnots...just can't install.

As far as the data on the machine...as far as I can tell, there is none.  It seems to be a fresh install.  Everything I started up, started with the welcome screen.

avg_joe

---

### Post by avg_joe on 2011-12-22
Wildmanne39, Thanks, that link looks like something I can figure out.

avg_joe

---

### Post by wildmanne39 on 2011-12-22
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following command into it then paste the output here so we can see if it is a new enough version to keep.
```
cat /etc/lsb-release; uname -a
```
Thanks

---

### Post by avg_joe on 2011-12-23
I got my privileges.  Thank you.
It seems that the only user in the system is a user called 'user'.  Another clue pointing towards fresh install?

I will fire that machine up in a little while, and do your copy/paste thingy.  That computer is set up out in garage.  It's pretty chilly out there right away in the morning.  I'll go get a fire going.

avg_joe

---

### Post by wildmanne39 on 2011-12-23
Hi, in ubuntu user is the only account that gets setup for security here is a link that explains it.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Thanks

---

### Post by avg_joe on 2011-12-23
Here's what I get when I did that.
user@user:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux user 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux
user@user:~$

Bear in mind, that the username avg_joe is as much descriptor as moniker......Break it down simple like for me.

I have read the linked page a couple of times, and some of it might be starting to sink in.  It all seems pretty complex for an avg_joe to jump into, with terminal commands, and such.  Seems to be going well enough so far, once I got past that whole password thing.
The machine also has a winxp pro license attached to it.  It doesn't ask me to choose which to load, just goes straight to kubuntu.  I haven't gone to bios screen on startup or anything like that yet, but there might be xp pro on here as well.

avg_joe

---

### Post by wildmanne39 on 2011-12-23
Hi, you are using a good release that is supported until April 2013 so I would keep it.

Are you able to install updates now? if so then I would leave it as it is, you do not need to setup an admin account like in windows.

You can install software with synaptic package manager, when the window opens for your password does it except it? if so you are good.
Thanks

---

### Post by avg_joe on 2011-12-23
Yes.  I am able to install updates, and it accepts my password.
Still trying to learn how to do stuff.
I was able to download and install pyscrabble.  I haven't tried to play yet, as I don't like scrabble.  But my wife LOVES to play.  I went and got it for the winxp machine for her as well.

I have been doing quite a bit of reading, so there is a certain degree of information overload right now.  But I think I might start to like this, if I can get past the cross-eyed dumbstruck stage.

Thank you for your help.
I'm sure I will figure out some more questions as I go along, but as it stands, I don't even know enough to know what to ask.

avg_joe

---

### Post by audiomick on 2011-12-23
> **avg_joe said:**
> The machine also has a winxp pro license attached to it.  It doesn't ask me to choose which to load, just goes straight to kubuntu.  I haven't gone to bios screen on startup or anything like that yet, but there might be xp pro on here as well.
Hi. I don't have a kbuntu install, mine is Ubuntu, however there should be a hard drive administration tool on there, I think. On Ubuntu 10.04 it is in the menu system> administration> 

Look for that, and then look at your drive with it. If you can see a partition that is ntfs, you may have an XP install on there. If there is no ntfs partition, but rather only ext4 and swap, then the windows has been wiped.

---

### Post by wildmanne39 on 2011-12-23
Hi, your welcome! when you have another question start a new thread for it and use thread tools at the top of the page to mark the thread solved please.
Thanks

---

### Post by avg_joe on 2011-12-24
Audiomick, I don't see a hard drive administration tool.  Although it's hard to tell what I'm looking at, due to the goofy names that stuff has.  That part is going to take some getting used to.
Once the holidays are over, I will have some more time to read about what the heck I'm doing.

Thanks, 
avg_joe

---

