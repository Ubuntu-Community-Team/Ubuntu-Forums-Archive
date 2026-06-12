---
title: "Thunderbird and Lighting versions"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by Denver Dave on 2011-11-04
I'm running ununtu 11.04 and the Thunderbird email version 3.1.15 installed by the software center.  I gather that the current version of Thunderbird is 7.0.1.  I just tried to install the Thunderbird addon for Lightning Calendar, however, the versions are not compatible.  Is there an easy way to update ?  I'm thinking there should be something in the update manager Thunderbird, but if is there, I'm missing it.  I can't check again, because I seem to have hung the update manage window. and don't want to lose this post.

Ironically Thunderbird and Lightning are running just fine on my XP PC.   I'll try on Windows 7 and report back.

Easiest way to upgrade Thunderbird 3.1.15 to 7.0.1 in ubuntu?

... also if I'm not on the right track, please let me know.

Thanks
= = = == 
Just found this thread so maybe I should get a new ubuntu disk, but still curious about the upgrade
[http://ubuntuforums.org/showthread.php?t=1859876&highlight=lightning](http://ubuntuforums.org/showthread.php?t=1859876&highlight=lightning)

> Recently updated to 11.10 and one change is that thunderbird has replaced evolution (a good thing), but how do you get the same integration with gnome's calendar with thunderbird as evolution had? Where stored tasks/meetings in thunderbird's lightning extension show up in gnome's drop down calendar (upper right corner)

---

### Post by wolfen69 on 2011-11-04
```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
```
then
```
sudo apt-get update
```
then
```
sudo apt-get upgrade thunderbird
```

---

### Post by Denver Dave on 2011-11-05
wolfen69 - I'd like to thank you so much for the 3 commands.

I was really bummed out that I couldn't figure out how to upgrade Thunderbird in ubuntu and was starting to question my interest in ubuntu.  I wated until this morning to install, but I went to bed with a smile instead of a frown.

Even I was able to copy 3 commands to the terminal editor, especially, now that I know how to copy and paste to the terminal (ctl+shift+p)

Ran for a fairly long time and looked like it updated quite a few things other than Thunderbird.  Interesting.   But maybe some of the things in the update manager may have cleared out.  I was not able to run them all before using update manager, trying again ... yep, most cleared out and update managered the rest, except for new 11.10 version (which I ordered).

... So thanks and this raises the question of how to improve my understanding.   It is not like I didn't look on how to update Thunderbird, with internet searches, Thunderbird site.  Found several ways to update, but all seemed complicated and also out of date.

Is there an old way to update that some are listing that might be more specific and a new way that is more simple for mere mortals?   Can you suggest a documentation resource to study?

Thanks again !

= = = == = = 

The reason that Thunderbird is important to me, is that I'm searching for a contact management tool to replace my windows Time & Chaos application that I love and use every day - no plans for Linux version.    

Strangely, Thunderbird with the syncing to google contacts, Lightning calendar to pull down and sort of sync with google calendar and ReminderFox which sort of duplicates events and tasks is starting to approach what I have with Time and Chaos under windows.  The features in Thunderbird are not integrated and there doesn't seem to be note taking addon, but I'm getting close.   Looking at Tomboy for notes, pretty neat, but don't like the 3rd party need to sync across computers (Like reminder fox better).   Maybe Google or Yahoo will come up with a notes application that has a local client and syncs?

Thanks again !!!!

---

### Post by Denver Dave on 2011-11-08
I guess things change fast.

I checked the Mozilla website and the linux versions of Thunderbird 8.0 and FireFox 8.0 are available.  So would we just do the same commands for thunderbird:

sudo add-apt-repository ppa:mozillateam/thunderbird-stable
sudo apt-get update
sudo apt-get upgrade thunderbird

and I'm just making this up, but maybe do the same firefox changing the word thunderbird to firefox ?

Or does firefox work differently since it is the default browser in ubuntu?

Where can we read up on these techniques?

Thanks.

---

### Post by wolfen69 on 2011-11-08
You already have the ppa needed, so you will just have to wait until the ppa team updates the releases.
```
sudo apt-get upgrade thunderbird
```
is all you will need to do. Just wait until they add the latest versions.

---

### Post by audiomick on 2011-11-08
Have a look here. I think the advice there should work.

[http://openubuntu.com/index.php/topic,1686.msg67373.html#msg67373](http://openubuntu.com/index.php/topic,1686.msg67373.html#msg67373)

---

### Post by Denver Dave on 2011-11-08
> s all you will need to do. Just wait until they add the latest versions.

so other than just keep running the command
sudo apt-get upgrade thunderbird
.... ran and updated a few things - started thunderbird - still 7.0.1.   But I did have thunderbird open, probably not such a bright idea.  Closed and updated again says 0 to install - start thunderbird again - still 7.0.1 - will wait and keep trying.

is there a list somewhere that we can see what new versions are available? ... or maybe a notification list to sign up for.  But wait, my windows thunderbird tells me there is an upgrade and unbuntu is not telling me that yet - so maybe that's my answer?

= = = = = 
wonder if the ubuntu update manager has the thunderbird and firefox upgrades?  - let's check
see 6 updates to 11.04 and also the 11.10 upgrade, but no thunderbird or firefox.   Not sure if they will be in the upgrade manager anyway, I haven't seen much that I recognize there.

Also there is the notion of resource.list or something like that.  Is this a way to register for updates?

Thanks - this is exciting.

---

### Post by Denver Dave on 2011-11-16
Checking back to see if FF and TB updates are available for ubuntu 11.10.  I think the linux versions have been available for a week.  Aren't TB and FF default applications for ubuntu?  How long does it usually take for them to be available for upgrade?

Thanks.

---

### Post by jaddi27 on 2011-11-16
Firefox 8 and Thunderbird 8 have been released for all platforms, but the  Ubuntu Developers have not put the new versions into the main repositories yet. There are a couple of issues that need to be resolved before they put them in there, but it should not be too long from now. Take  a look at the Sticky thread [Firefox 8 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247") for updates on this.

Joel

---

### Post by SheaMan on 2011-11-16
completely uneducated comment, but ..while.. FF and TB are default apps for Ubuntu that does not mean that the developers put Ubuntu users at a their first priority. In fact, ( if they are business minded ) they will put their priorities to Windows, then Mac, then Ubuntu. Right? Were I a betting man I would say that FF/TB updates for ubuntu are ..prolly monthly? Thinking from their CFO's perspective :P

---

### Post by alphacrucis2 on 2011-11-16
> **Denver Dave said:**
> 

Even I was able to copy 3 commands to the terminal editor, especially, now that I know how to copy and paste to the terminal (ctl+shift+p)



You can also paste into the terminal using the mouse. Right click anywhere in the terminal window and select paste from the context menu or edit - paste from the terminal main menu.

---

### Post by vanhenryjr on 2011-11-16
Thanx for this thread. I really have not been able to get thunderbird working my my 11.04 ubuntu laptop-I have been happy w evolution, but if the next LTS is going thunderbird I thought I would switch sooner rather than later.

---

### Post by Denver Dave on 2011-11-25
Found this link about Thunderbird 8 and ubuntu that contains a link for what versions are available.

= = = = 
hmmmm - looks like I didn't post the link - will look for it.

Previously updated to Firefox and  just a few minutes ago, updated to Thunderbird 8 through the ubuntu update manager.  Had to wait for a while, but worked slick and don't mind waiting for things to work right - impressive thanks.

... so I guess my Q was answered, there was an alert on the ubuntu top menu bar that updates were available.

---

