---
title: "Update to 14.10?"
date: 2015-02-03
forum: New to Ubuntu
---

### Post by hmiersch on 2015-02-03
Hi. 
I'm on 14.04 LTS. Should I upgrade to 14.10? If so, why, and if not, why not?

---

### Post by Lars Noodén on 2015-02-03
14.04 LTS is good through to 2019.  But 14.10 is only good for 9 months so basically you'll have to update to every new 6-month release.  

[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by slickymaster on 2015-02-03
LTS stands for “long-term support” and are designed to be stable platforms that you can stick with for a long time. Ubuntu guarantees LTS releases will receive security updates and other bug fixes as well as hardware support improvements for five years.
LTS versions are released every two years. If you stick with the LTS version, you’ll still get a new Ubuntu release every two years.

In comparison, a regular release will only be supported for nine months. Considering new versions of Ubuntu are released every six months, you’ll have three months after a new version is released to upgrade to it or you won’t receive security patches anymore.

LTS versions are designed to be more polished, while the standard releases bring you the latest features that may not be completely finished yet.

---

### Post by grahammechanical on 2015-02-03
There is something else to consider.

If we are using 14.10 and we delay in upgrading to 15.04 until after 14.10 has reached End of Life then it becomes much more complicated to upgrade. It is no longer a one click action.

So, it is a life choice decision. Install an LTS and upgrade every 2 years or a little over 4 years. Or, install an Interim - Standard release and upgrade very six months for at least 2 years until the next LTS comes along.

Regards.

---

### Post by monkeybrain20122 on 2015-02-03
14.10 is buggy with multiple issues on my tested partition (my machine has run several Ubuntu releases as well as other distros.-- now 14.04 on the main partition as my work OS,--, so it is not that I have some odd hardware), plus it has short support cycle. So IMO it isn't worth the troubles if 14.04 works well for you: nothing to gain really. 

Keep in mind I am not one of those who say always stick to LTS, I would switch to a non LTS if there is a compelling reason, e.g 13.04 and 13.10 are both vastly superior to 12.04 IMO, so I switched. But not in this case.

Also as a general suggestion, never 'upgrade' with the update manager, backup your data and do a clean install (and/or make a seperate /home partition so only need to do flash install to /) 'upgrade' takes a long time and is unreliable unless you have a very pristine system. The laziness of trying to do it with one click is likely to cost you more work down the road.

---

### Post by sammiev on 2015-02-03
If 14.04 is working for you, leave it alone. 14.04 is long tern and 14.10 will be short lived.

---

### Post by Bucky Ball on 2015-02-03
All of the above. I always use LTS releases and have a few spare partitions for 'playthings', e.g. the interim releases if I want to fiddle with them, which I haven't done for a few years now. 

So, LTS, set and forget, at least for 2 or 4 years, would be my recommendation. Both 12.04 LTS (supported until April 2017) and 14.04 LTS (2019) are very stable, at least in my experience.

---

### Post by pfeiffep on 2015-02-04
> **hmiersch said:**
> Hi. 
I'm on 14.04 LTS. Should I upgrade to 14.10? If so, why, and if not, why not?You might consider both!
If you're investing time in learning Linux - specifically Ubuntu I suggest installing 14.04 LTS in onw partition for your daily tasks and data storage; into another partition install the latest (and greatest?) for your learning endeavors.
If you decide on the both options look into sharing a /home directory so you have your data available to both installed versions.

---

### Post by Bucky Ball on 2015-02-04
> **pfeiffep said:**
> 
If you decide on the both options look into sharing a /home directory so you have your data available to both installed versions.

... and the /swap. No need for two. Choose 'Something Else' at the partitioning section of the second install and make sure your /home partition is marked to use, but not to format! Definitely not the latter. ;)

---

### Post by craig10x on 2015-02-04
As far as a previous comment about upgrading with the software updater not being reliable and that a clean install is necessary, i would say that depends...if you, like me, just use a "stock" ubuntu and don't make major modifications to it (other then adding programs of course...that is no problem) or stocking up on ppas ( i only use one, Google Chrome which comes with it's install) and remember to turn off the ppas before you start the upgrade (turning them back on when the upgrade is done)...then you should have good success with upgrades...

I have been doing upgrades for several 6 month versions and they all went 100% perfect...I think there is more chance of some problems when one upgrades from LTS to LTS every 2 years....mostly because there has been a huge amount of changes over that period of time...and not so much with the 6 month version...

So, i would say that if you run a stock ubuntu, and upgrade every 6 months, then that is also a good way to go...you will always have the newest software and be covered as far as updates go...
As far as 14.10, i have found it to be very reliable and it feels like a refined and improved 14.04 and i have run both...

---

### Post by monkeybrain20122 on 2015-02-04
> **craig10x said:**
> As far as a previous comment about upgrading  with the software updater not being reliable and that a clean install is  necessary, i would say that depends...if you, like me, just use a  "stock" ubuntu and don't make major modifications to it (other then  adding programs of course...that is no problem) or stocking up on ppas (  i only use one, Google Chrome which comes with it's install) and  remember to turn off the ppas before you start the upgrade (turning them  back on when the upgrade is done)...then you should have good success  with upgrades...

I have been doing upgrades for several 6 month versions and they all  went 100% perfect...I think there is more chance of some problems when  one upgrades from LTS to LTS every 2 years....mostly because there has  been a huge amount of changes over that period of time...and not so much  with the 6 month version...

So, i would say that if you run a stock ubuntu, and upgrade every 6  months, then that is also a good way to go...you will always have the  newest software and be covered as far as updates go...
As far as 14.10, i have found it to be very reliable and it feels like a  refined and improved 14.04 and i have run both...

Well if you do anything other than using stock Ubuntu for basic  stuffs then there are many things that work well in 14.04 but broken in  14.10. e.g just found out even ppa-purge doesn't work properly (chose  'abort' but it went ahead to purge anyway) The more I test 14.10 the  more I find it unsatisfactory. So the question relevant to OP is whether  there is any compelling adbvantage to gamble away a working system with  5 year support for something at best unknown, and at worst rather  broken (for my use case e.g) I can't see any (getting newest software is  not true, the software is just not so old,--so something that has to change rapidly like smtube most definitely is already too old to work,-- to get newest software in a  much safer and less invasive way would be to use ppas, that way you  don't need to basically nuke the whole system)

As for upgrade,  even under best case scenario it takes hours during which a lot can happen,--wifi dies, cat/kid kicks the cable...--and leave you with a partially upgraded = broken system . Maybe it is just me, I  would rather have more control and get the whole thing over with in  about 30 min (reinstall system + software,--excluding recompiling software but you need to do that anyway  however you update the system and probably most users don't compile from  source)

---

### Post by craig10x on 2015-02-05
Hours? Well, i must admit that i have a pretty high speed cable connection (50 mbps according to the cable provider but it is actually more like 54 mpbs most of the time). All the files download in about 5 minutes...
The actual install time (through software updater) once the files are downloaded, is roughly 60 minutes (or about 30 minutes more then a clean install takes)...

So, other then the file downloading time (which would vary according to your internet speed of course) figure on about an hour for the actual install...
At least on my hardware ( a 2 year old toshiba laptop with intel graphics) 14.10 has been very reliable so it probably depends on your hardware and what you use...

When my upgrades were completed, other then re-checking the Google Chrome ppa in "software sources" that was the extent of the work i needed to do after re-booting...all programs, settings, etc were exactly in place...It even cleaned up the no longer needed stuff for me (like old kernels, for example) like a clean up janitor... all i had to do was to tell it to remove that stuff at the end of the upgrade...

14.04 ran well for me...however that 3.13 kernel was "cursed" for me (caused multimedia instability) so i needed to get away from it, and 14.10 provided a quick answer to get the ubuntu native "patched" 3.16 kernel which is rock solid for me...

Of course, 14.04 will be getting the utopic kernel tomorrow ;) (if you install the hardware enablement stack, that is)...

---

### Post by monkeybrain20122 on 2015-02-05
> **craig10x said:**
> 

Of course, 14.04 will be getting the utopic kernel tomorrow ;) (if you install the hardware enablement stack, that is)...

Of course I don't install the HES. I am already running mesa 1.5 (better performance) and kernel 3.19 rc7, which solves a long standing problem of vlc freezing with vaapi enabled. ;)

 I am sure the Ubuntu kernel patch does something, but I have not noticed any advantage on my machines. I am using 14.04 but most of the software I use is newer than 14.10's stock offer (ppa + self compiled) so for me there is no reason to upgrade unless there is something compelling like switching from Unity 5 to 7 between 12.04 and 13.04. But with Ubuntu moving to unity 8, major improvements in Unity 7 are unlikely, minor tweaks and  bug fixes will be backported to 14.04. 14.10 is just neither here nor there even if it weren't so buggy.

---

### Post by craig10x on 2015-02-05
All good points...i would say, at least on my hardware, that the main advantage of using the native (ubuntu "patched" kernel) has been that it seems to run a lot cooler then when i install from outside...

---

