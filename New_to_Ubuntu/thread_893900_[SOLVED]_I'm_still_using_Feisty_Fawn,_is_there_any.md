---
title: "[SOLVED] I'm still using Feisty Fawn, is there any reason to upgrade?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by tahitiwibble on 2008-08-18
It does everything I want better than ever expected and I love it!

---

### Post by mikewhatever on 2008-08-18
The only reason I can suggest it Feisty's end of update cycle in October 2008.

---

### Post by tahitiwibble on 2008-08-18
> **mikewhatever said:**
> The only reason I can suggest it Feisty's end of update cycle in October 2008.

Ah ha! Thanks for teaching me something new ............ "end of update cycle" hmmmmmm.

Would this indicate that I will be running an obsolete OS at some point? What are the dangers/problems that one might encounter? One day in the future will it be like someone running Windows 95 today?

---

### Post by halitech on 2008-08-18
all of the releases have an 18 month support cycle except a few (like 6.06 and 8.04) which are what they call LTS (long term support). The install will probably still be more stable and usable in the future then win95 is as most bugs/issues should be ironed out by now.

I don't believe you can update from 7.04 so I would suggest you back up your home folder and do a fresh install of 8.04.

---

### Post by tahitiwibble on 2008-08-18
> **halitech said:**
> all of the releases have an 18 month support cycle except a few (like 6.06 and 8.04) which are what they call LTS (long term support). The install will probably still be more stable and usable in the future then win95 is as most bugs/issues should be ironed out by now.

I don't believe you can update from 7.04 so I would suggest you back up your home folder and do a fresh install of 8.04.

Wow ......... LTS hmmmm, OK. Thanks for that info Halitech. Would you **recommend** that I install 8.04?

---

### Post by halitech on 2008-08-18
if your system is the specs in your sig then I would say yes. Maybe grab a copy of the live cd and boot from it (allow for slightly slower responses due to it running from the cd) and see if everything works before installing it.

---

### Post by aysiu on 2008-08-18
> **tahitiwibble said:**
> Ah ha! Thanks for teaching me something new ............ "end of update cycle" hmmmmmm.

Would this indicate that I will be running an obsolete OS at some point? What are the dangers/problems that one might encounter? One day in the future will it be like someone running Windows 95 today? It means you'll no longer receive security updates after October 2008, so as long as you're connected to the internet, you should probably think about upgrading to 7.10, 8.04, or 8.10 after October.

---

### Post by tahitiwibble on 2008-08-18
> **halitech said:**
> if your system is the specs in your sig then I would say yes. Maybe grab a copy of the live cd and boot from it (allow for slightly slower responses due to it running from the cd) and see if everything works before installing it.

Thank you my friend, I am grateful to you for your help. I will do exactly as you suggested and test things out.

If all goes well am I safe in understanding the update procedure to be as simple as;

1/ Backup 'home' folder to external hard-drive
2/ Install 8.04
3/ Reinstall all currently used programs
4/ Overwrite newly installed 8.04 'home' folder

---

### Post by halitech on 2008-08-18
you got it :)

after you have 8.04 installed, you may want to look into remastersys and if you have a dvd burner, do a complete backup and make it a live dvd that you can use to reinstall from.

---

### Post by tahitiwibble on 2008-08-18
> **aysiu said:**
> It means you'll no longer receive security updates after October 2008, so as long as you're connected to the internet, you should probably think about upgrading to 7.10, 8.04, or 8.10 after October.

Things are becoming very clear! Thank you.

If you were in my shoes? 7.10, 8.04, or 8.10 after October?

---

### Post by ugm6hr on 2008-08-18
> **tahitiwibble said:**
> If all goes well am I safe in understanding the update procedure to be as simple as;

1/ Backup 'home' folder to external hard-drive
2/ Install 8.04
3/ Reinstall all currently used programs
4/ Overwrite newly installed 8.04 'home' folder

Yes.

However, there is one thing worth considering to make it *even* easier for the next upgrade (in about 2.5 years, or sooner if you want): a separate **/home** partition.

This allows you to reinstall Ubuntu (or install a new upgraded version) without having to backup /home - it will simply stay put each time, completely unchanged.

This may also be useful for step 3: [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by halitech on 2008-08-18
I'm using 7.10 on my desktop, 8.04 on my laptop and I guess I'm still partial to 7.04 but I would say probably go with 8.04 for now, wait a few weeks after 8.10 is released and then update to 8.10. I'll probably keep my desktop at 7.04 as long as possible but my laptop I'll probably update to 8.10 a few weeks after it comes out

---

### Post by tahitiwibble on 2008-08-18
> **halitech said:**
> you got it :)

after you have 8.04 installed, you may want to look into remastersys and if you have a dvd burner, do a complete backup and make it a live dvd that you can use to reinstall from.

Thank you halitech, for everything! Your moral and practical support is priceless to me. remastersys looks like a beauty!

Once again, thank you!

---

### Post by tahitiwibble on 2008-08-18
Thank you to one and all who have helped me out in such a gracious manner!

I get the **very firm impression** that the modern occidental world would be such a better place if it was ran by people that use Linux.

---

### Post by anjilslaire on 2008-08-18
> 
1/ Backup 'home' folder to external hard-drive
2/ Install 8.04
3/ Reinstall all currently used programs
4/ Overwrite newly installed 8.04 'home' folder


> **ugm6hr said:**
> Yes.

If I'm not mistake, shouldn't it it be:
1) Backup
2) Install 8.04
3) Overwrite newly installed 8.04 'home' folder
4) Reinstall all currently used programs
?

I would think installing your apps then replacing your /home would potentially screw up and shortcuts and/or config settings you have in place.
 Best to put your /home back on, THEN install all of your apps so as to have correct configs and shortcuts, etc.

---

### Post by halitech on 2008-08-18
glad to be of assistance and thanks is the only reason we do it :D

> I get the very firm impression that the modern occidental world would be such a better place if it was ran by people that use Linux.

I think you are right :D

---

### Post by halitech on 2008-08-18
> **anjilslaire said:**
> If I'm not mistake, shouldn't it it be:
1) Backup
2) Install 8.04
3) Overwrite newly installed 8.04 'home' folder
4) Reinstall all currently used programs
?

I would think installing your apps then replacing your /home would potentially screw up and shortcuts and/or config settings you have in place.
 Best to put your /home back on, THEN install all of your apps so as to have correct configs and shortcuts, etc.

if you put your home folder back in first, then reinstalling the programs would over write your config files

---

### Post by anjilslaire on 2008-08-19
Not entirely correct.

I have /home mounted on its own partition. When I wipe / and reinstall, using my existing /home, then reinstall all of my apps, I am essentially putting my /home back on *before* installing the new extra applications, yet my old preferences and configs are left intact. 
Mostly, this is because app config files are in the install directories, but my specific user settings are left untouched in my /home directory.

If you replaced your /home after installing your extra apps, you may be deleting some newly created shortcuts, or menu entries, etc that may have not been present in your "old" directory.

Either way, I'm glad the OP got his issues sorted, and is upgrading his system :)

---

### Post by halitech on 2008-08-19
you know, I never thought of that. It would make the seperate home folder useless if installing the apps wiped out config files during an install so having the /home folder copied in first would be the way to go.

---

### Post by tahitiwibble on 2008-08-19
Thanks to both of you for hashing that one out! I'm going to have to read everything a couple more times ............ but I'll get there :) I **will** get there! :cool:

---

### Post by MarkieB on 2008-08-20
no longer participating in ubuntuforums.org

---

### Post by tahitiwibble on 2008-08-20
> **MarkieB said:**
> for reinstalling the packages, the guide at 
[https://help.ubuntu.com/community/FeistyUpgradesFreshInstall](https://help.ubuntu.com/community/FeistyUpgradesFreshInstall)
is worth looking at


**Mark**, thanks for that.

PS Good luck with HalloIT, your credentials are very impressive.

---

### Post by MarkieB on 2008-08-21
no longer participating in ubuntuforums.org

---

