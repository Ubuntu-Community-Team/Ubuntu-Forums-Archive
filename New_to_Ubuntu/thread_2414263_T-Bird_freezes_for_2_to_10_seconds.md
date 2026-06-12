---
title: "T-Bird freezes for 2 to 10 seconds"
date: 2019-03-07
forum: New to Ubuntu
---

### Post by chult2 on 2019-03-07
Hello,
 similar problem as described in this post: Thunderbird freezes system. Tried reinstall ([https://ubuntuforums.org/showthread.php?t=2413737](https://ubuntuforums.org/showthread.php?t=2413737))
 . Similar error message (see below).
 
 
 Dual boot Win 10/ Ubuntu 16.04
 thunderbird local folder is defined for a different partition (accessible from windows as well) with  a modified profiles.ini pointing to that directory.
 
 
 I think with the update to TB 60.something my problems started.  
 
 
 Suddenly no mails or mail boxes were shown.
 
 
 First renamed name of the profile according to:
 Moving your profile folder - Thunderbird
 ([http://kb.mozillazine.org/Moving_your_profile_folder_-_Thunderbird](http://kb.mozillazine.org/Moving_your_profile_folder_-_Thunderbird))
 
 
 problem stayed
 
 
 next step:
 
 
 Following a knowledge base article called:Recovering a profile that suddenly disappeared ([http://kb.mozillazine.org/Recovering_a_profile_that_suddenly_disappeared#Corrupt_or_empty_prefs.js](http://kb.mozillazine.org/Recovering_a_profile_that_suddenly_disappeared#Corrupt_or_empty_prefs.js))
 
 
 I eventually copied an old prefs.js from a backup before the entire mess started to my thunderbird folder and the folders were shown again.  
 
 
 But now thunderbird is sometimes (actually rather often) freezing or rather the GUI is grayed out and the GUI is not responding to any click for some two to ten seconds. In normal mode and safe mode
 
 
 Started safe mode
 thunderbird -safe-mode
 
 
 When I want to reply to a mail or select other mails from the top box thunderbird freezes.
 In the shell I get this message:
 
 
 1551986780691    addons.xpi    WARN    Can't get modified time of [/usr/lib/thunderbird/features/wetransfer@extensions.thunderbird.net]("https://ubuntuforums.org/usr/lib/thunderbird/features/wetransfer@extensions.thunderbird.net")
 
 
 But I do get this error only once, not in a repeated manner, even if the GUI of Thunderbird freezes several times.
 
 
 I just saw there is on this computer no folder called “features “ in usr/lib/thunderbird.  
 
 
 According to above suggestion, I did rename the ~/.thunderbird, started thunderbird again, stopped the creation of new accounts, ended thunderbird, copied the profiles.ini to the newly created .thunderbird folder and started thunderbird again in safe mode.  
 
 
 And in the “normal” mode  
 Problem stays the same – just the error number changes :
 ~$ thunderbird
 1551991392521    addons.xpi    WARN    Can't get modified time of [/usr/lib/thunderbird/features/wetransfer@extensions.thunderbird.net]("https://ubuntuforums.org/usr/lib/thunderbird/features/wetransfer@extensions.thunderbird.net")
 
 
 
 
 Any suggestion how to proceed ?
 Looking for constructive answers.
 Best
 Claus

---

### Post by richard378 on 2019-03-07
I no longer think it is a Thunderbird issue.  It is a more widespread issue with my firewall.  My whole system freezes when the firewall blocks any communications.  Thunderbird works 100% now that I unblocked the ports.  But my system still freezes at random times during internet access.   When I was opening a browser when running boxes and accessing internet in boxes.   Then again when I check for updates in the software center.  Everything I do points to a firewall configuration problem that the system freezes when it is blocking a port that it does not have a rule set for.  I have been getting freezes when background programs check the internet and when they access the internet on command.  It is a larger system-wide issue currently.  I turn off the firewall and the freezes stop.

---

### Post by DuckHook on 2019-03-07
@ chult2

Please do not hijack threads. Although your problem may seem like the OP's, similar problems are frequently due to different causes. Hijacking the threads of others creates confusion and errors, and diminishes the usefulness of solved threads for those who later are searching for solutions.

I have split your post off from the original thread into its own separate thread with a unique title.

---

### Post by chult2 on 2019-03-08
@DuckHook: sorry for the "hijacking" did not know/ envisage that this will increase confusion. Re-edited my post with reference to the previous post

---

### Post by DuckHook on 2019-03-08
No problem. You are new to the forums and it is understandable if you are not yet familiar with our netiquette.

Welcome to the forums and good luck!

---

