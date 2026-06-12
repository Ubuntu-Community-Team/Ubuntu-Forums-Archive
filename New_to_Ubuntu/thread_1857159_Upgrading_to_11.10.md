---
title: "Upgrading to 11.10?"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by d4m1r on 2011-10-09
Hi, so I hear a final version of this will be released soon...I am running 11.04 and I am not sure how updating versions works on Ubuntu yet, will it show up in update manager? I am guessing all my files/programs will be saved, but will my customized settings as well (NTFS partitions to mount at boot, keyboard shortcuts, firefox bookmarks, etc)?

Also, what is the next scheduled LTS version? Let me know please, thanks :D

---

### Post by zhogan85 on 2011-10-09
Yes, an option will show up in the update manager, and yes your files/settings/etc should stay. But be forewarned, some people encounters problems with upgrading, so be sure to back up your info in case you need to do a clean reinstall. But that being said, it should be fine.

And the next LTS release should be in April.

---

### Post by d4m1r on 2011-10-09
> **zhogan85 said:**
> Yes, an option will show up in the update manager, and yes your files/settings/etc should stay. But be forewarned, some people encounters problems with upgrading, so be sure to back up your info in case you need to do a clean reinstall. But that being said, it should be fine.

And the next LTS release should be in April.

Leads me to a few more questions :lol:

1)What is currently the latest LTS version?

2)What "problems" do they encounter?

3)How should I backup my Ubuntu partition? Is there an option to burn a recovery CD that would save all my settings and programs? On Windows, I do that or just burn a clone to DVD...

---

### Post by BlinkinCat on 2011-10-09
You could also read this - :)

[URL="https://help.ubuntu.com/community/NattyUpgrades"]Edit wrong answer
[/URL]

---

### Post by Frogs Hair on 2011-10-09
1. 10.04 is the latest LTS and 12.04 is the next .(April 2012) 

2. Do you mean problems with upgrades ? If so do a forum search .

3. I do a clean installations every 6 months and backup only my home folder . Some programs may change and will be removed and replaced during upgrade if you choose to go that route . I have some PPA'S  , which are never compatible with the new version in my experience .

---

### Post by dFlyer on 2011-10-09
I've only done an upgrade once to try it out and never had a problem. On the other hand I've burned an iso every 6 months and do a fresh install and haven't had any problem with that either. You might want to download deja dup and backup your home directory regardless if you do an upgrade or reinstall to be on the safe side. Deja Dup is the default backup program in 11.10. FYI, synaptic is not in 11.10 so if you use that program you will have to install it from the archives either using Ubuntu Software Center or 

sudo apt-get install synaptic

---

### Post by alphacrucis2 on 2011-10-09
> **Frogs Hair said:**
> 1. 10.04 is the latest LTS and 12.04 is the next .(April 2012) 

2. Do you mean problems with upgrades ? If so do a forum search .

3. I do a clean installations every 6 months and backup only my home folder . Some programs may change and will be removed and replaced during upgrade if you choose to go that route . I have some PPA'S  , which are never compatible with the new version in my experience .


The upgrade process automatically disables all PPA's but you can re-enable them afterwards. You may need to check if the PPA offers packages for the new release version before doing that. If not, the ppa packages for the older release may or may not work depending on library version compatibility.

---

### Post by CarlosFerreira on 2011-10-10
> **dFlyer said:**
> I've only done an upgrade once to try it out and never had a problem. On the other hand I've burned an iso every 6 months and do a fresh install and haven't had any problem with that either. You might want to download deja dup and backup your home directory regardless if you do an upgrade or reinstall to be on the safe side. 

I've never had any problems with updating myself; on the other hand I've had serious problems with LiveCD/USB, which was much less fun. Either way, backing up with Deja Dup is probably the best advice that can be given right now.

---

