---
title: "Concerned About Spyware/ Python Symbol?"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by candyshimmer7 on 2014-04-25
Every time I log onto my computer and several times while I'm using it, an update message will pop up telling me to upgrade to 14.04. This makes sense since the update was just released. However, the image that comes up looked weird, so I Ctrl-Alt-Delete and end the update gtk process or whatever it's called from there so I don't click on it. 

Then when I searched under the other people's images for their update messages, their messages always say something like, "your computer is up to date, but you can download 14.04." my computer is not up to date b/c it's just a little EEE machines computer and I'm afraid updates will over tax it, so that might be why my update wording is different.

However, when it asks me to update the computer for 14.04, it shows a fuzzy pixelated version of the python symbol ([http://i.stack.imgur.com/jBli3.png](http://i.stack.imgur.com/jBli3.png)) on the left side where all my launcher programs are. This concerns me since the symbol I see most often for 14.04 is something like a mountain goat or something. I've seen a few articles that python is a part of 14.04, but why would python be the overall symbol? Is this what everyone is seeing or is this some kind of spyware trick?

---

### Post by coldcritter64 on 2014-04-25
> ...I'm afraid updates will over tax it...
Not allowing updates is a security concern and you will _*not*_ likely "tax" your system _*with them*_, only with applications/services etc you install and start up additional to your base system. I'd advise turning security updates on if they've been turned off at the very least, preferably normal application (recommended) updates as well. 

You can turn off the LTS update notice in update manager (on by default iirc). Opening "settings" in Update Manager should give you "Software Sources", look at the bottom of the Updates tab in  "Notify me of a new Ubuntu version" and set it to your needs; setting to "Never" will get rid of the 14.04 LTS notices. Interim releases come out every 6 months, LTS come out every 2 years, this setting can be turned off if you know that.

Python is used by many applications, I suspect update-manager is using it if the icon is showing. Doesn't appear to be anything to worry about spyware wise with this i.m.o. Cheers.

---

### Post by deadflowr on 2014-04-25
1) the python symbol is what shows up for a release upgrade, so that's normal.

2)I don't know what, or why you think ctrl_alt+del opens system monitor in Ubuntu, but that key sequence is used to log you out.
I believe it's hard-coded.

3)Unless you only have a very tiny amount of disk space( like 10GB or less) install all updates you get.
Updates aren't going to slow down the system, normally.

---

### Post by coldcritter64 on 2014-04-25
> **deadflowr said:**
> ...2)I don't know what, or why you think ctrl_alt+del opens system monitor in Ubuntu, but that key sequence is used to log you out.
I believe it's hard-coded...

That can usually be changed in System Settings > Keyboard > Shortcuts (titles may be slightly off, like that though), Under the system shortcuts section. I always use that to use ctrl + alt + del to bring up the command gnome-system-monitor; but only after first deleting the shortcut for the logout sequence, the one you mention, then setting a custom entry using the ctrl + alt + del combination for system monitor (unless this has changed since 12.04 that _*can*_ be set up). Cheers.

---

### Post by deadflowr on 2014-04-25
> **coldcritter64 said:**
> That can usually be changed in System Settings > Keyboard > Shortcuts (titles may be slightly off, like that though), Under the system shortcuts section. I always use that to use ctrl + alt + del to bring up the command gnome-system-monitor; but only after first deleting the shortcut for the logout sequence, the one you mention, then setting a custom entry using the ctrl + alt + del combination for system monitor (unless this has changed since 12.04 that _*can*_ be set up). Cheers.

I stand, somewhat, corrected.;)

---

### Post by candyshimmer7 on 2014-04-25
Thank you so much for all your help. I feel much better. Thank you also for your advice. My system says it has a little over 18 GB, so I'm going to download the updates now. :)

---

