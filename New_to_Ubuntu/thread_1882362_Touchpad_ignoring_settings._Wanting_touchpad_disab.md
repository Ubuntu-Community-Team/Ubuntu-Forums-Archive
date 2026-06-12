---
title: "Touchpad ignoring settings. Wanting touchpad disabled during typing"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by wanabegeek on 2011-11-17
I'm brand new to any operating system other than Windows so please excuse my naivety.
 
Had issues with my touchpad initial when using Windows 7 however changed the settings and worked perfectly. Have now partioned the harddrive and installed Ubuntu 11.10. 
 
Have used System Settings, Mouse and Touchpad to disable the touchpad while typing.  Which had no effect. 
 
Used the following commands within a terminal to disable the touchpad complete as a drastic means of getting around my problem. 
 
Synclient -l (to list the settings)
synclient touchpadoff=1 (to turn it off)
Synclient -l (to confirm that the setting had indeed be changed)
 
Closed the terminal window and it had no effect
 
Installed pointing devices
and this stated that the touchpad was already disabled (probably because of my previous command to synclient (!!!)
 
Now wondering what else I can do
 
Its most annoying as I'll be touchtyping and my hand will accidentally brush across the touchpad and cause my text to be deleted or to type in the wrong place etc. Please help!!!

---

### Post by fishexe on 2011-11-18
I have the same problem.  It appears to be a bug in the newest version.  My Ubuntu was respecting my settings up until yesterday, then it suddenly stopped.  This is a BIG problem for usability because the default is to allow "tapping" on the touchpad to constitute a click, but my touchpad is very sensitive and often registers a tap when all I was doing was moving my finger across, not actually tapping it...so I get lots of random clicks when I didn't actually click on anything at all.

It appears to be fixed on a reboot, but broken again as soon as I suspend and resume.  A description of why and a kludgey fix can be found here:
[http://tombuntu.com/index.php/2011/11/06/persistent-touchpad-configuration-in-ubuntu-11-10/](http://tombuntu.com/index.php/2011/11/06/persistent-touchpad-configuration-in-ubuntu-11-10/)

I haven't gotten around to trying the fix because I would have to look up the right variables for synclient corresponding to the setting I want, but it sounds plausible.  I'll try it out later today and report back.

I'm a little bit disappointed in both gnome and Ubuntu for breaking usability like this. Seriously, there should be rigorous tests for usability before rolling out new versions of packages that are the most likely to be seen by new FOSS users.  I'm also increasingly disenchanted with Shuttleworth, who has stated that anyone criticizing Ubuntu is merely a tech-snob who doesn't like attractive user interfaces, when really our complaint is, "No, you guys just keep BREAKING your interface!"  This is not the first (or second or third) time I've had some major aspect of the user interface inexplicably stop working on Ubuntu, a problem I've never had with Debian.  Yes, Ubuntu is easier to set up without wading through config files, but that benefit is lost when it repeatedly breaks as a result.  Newbies should not have to learn various formats formats of config file just to use an OS, and they should not have to learn various formats just to fix problems that had no business arising, either.

---

### Post by wanabegeek on 2011-11-19
Thanks for your response. I read and attempted the fix proposed in the article you proposed. It had no effect. Unfortunately I don't think my issue is the same. In the article Tom is losing his settings after the computer is suspended.  I can't change mine to begin with. 

[http://tombuntu.com/index.php/2011/11/06/persistent-touchpad-configuration-in-ubuntu-11-10/](http://tombuntu.com/index.php/2011/11/06/persistent-touchpad-configuration-in-ubuntu-11-10/)

"It didn’t take long before I noticed that some changes would revert  after I suspended and woke the system. Even adding the changes to my  Xorg configuration didn’t make them stick. "

This issue is really starting to bug me, but unfortunately I can't revert to an older and more stable version of Ubuntu as so many items on my computer were not recognized whereas with 11.10 they nearly all worked immediately.  Think I'm just going to have to revert to one finger typing!!!

---

### Post by roger_1960 on 2011-11-19
Hi
  
> Installed pointing devices
and this stated that the touchpad was already disabled (probably because of my previous command to synclient (!!!)
 
Did you mean gpointing-device-settings available in synaptic package manager?  This usually works.

Also, forgive me if its too obvious, but every laptop/netbook I have seen has a hardware keyboard shortcut for disabling the touchpad (FN+F?) - have you tried it?

---

### Post by wanabegeek on 2011-11-21
> **roger_1960 said:**
> Hi
  
Did you mean gpointing-device-settings available in synaptic package manager?  This usually works.

Also, forgive me if its too obvious, but every laptop/netbook I have seen has a hardware keyboard shortcut for disabling the touchpad (FN+F?) - have you tried it?

Thanks for your response.  Believe me I know that quite often it is the obvious things that get missed.  Unfortunately in Windows the Fn+F9 button does disable the keypad but not in Ubuntu. 

I'm using "gpointing-device-settings 1.5.1-5ubuntu1", and it hasn't worked. I set "Disable touchpad" and it still has full functionality.

---

