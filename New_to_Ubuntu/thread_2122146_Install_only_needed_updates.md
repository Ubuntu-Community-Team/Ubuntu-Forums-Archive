---
title: "Install only needed updates?"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by Apurvam on 2013-03-04
Hi, I'm new to forums and Linux world. Yesterday I installed Xubuntu 12.10 64-bit.

I like to have my computer clean and organized. Which leads to my question do I really need to install all updates which are available for my system?!

For example, I have bunch of *Common UNIX Printing System* updates, but I don't have any printers.
(when I used Windows, I din't see any reasong to install some random update for particular software / service etc which I don't have installed or use.)

Any comments?

---

### Post by Cheesemill on 2013-03-04
Updates are only offered for programs that you have installed on your system. You should install all the updates you are offered as they are all to patch security issues and bug fixes.

If you don't want the program then just uninstall it.

However, I would be careful when trying to uninstall system utilities such as CUPS as a lot of other applications on your system will need it to be installed as a dependency. Forcing the removal of CUPS will probably force the uninstallation of programs that you do want to keep so I would advise you to just keep it. You wouldn't gain any performance benefits by removing it anyway, all you would do is free up a couple of MB of hard disk space.

---

### Post by schragge on 2013-03-04
To some extent, you can choose which updates to get by enabling only appropriate repositories. See description at [uhelp]community/Repositories#A_Quick.2C_Tongue-in-cheek_Description_of_the_Ubuntu_Repositories[/uhelp]

---

### Post by Apurvam on 2013-03-04
Goods posts. Thanks.

But is there a significant reason to install updates if everything is working fine? (don't fix what isn't broke!?) Or is there really a point of installing some update fixing some bug which I'm not having or experiencing yet? And install it when I'm starting to have some issues with that software or function?

I want to note, I'm not expecting any performance gains from not installing updates, but I do believe OS would slow down with time by installing every and all updates available.

---

### Post by QIII on 2013-03-04
What would lead you to believe that the OS would slow down?

---

### Post by Apurvam on 2013-03-04
I think good analogy would be codecs in Windows, if you install mega codec pack (which has like 100+ codecs, filters etc) there is much greater risk of some conflicts arising between those codecs, wheras if you install only those codec which you use there is almost none risk of having some wierd issue, or slow (buggy) playback. 
Not sure, if I expressed myself understandable... ;)

---

### Post by QIII on 2013-03-04
There is some risk, both in Windows and Linux, that conflicts will arise.  

Updates generally make things better in Windows, just as in Linux.

---

### Post by fantab on 2013-03-04
> **Apurvam said:**
> Hi, I'm new to forums and Linux world. Yesterday I installed Xubuntu 12.10 64-bit.

I like to have my computer clean and organized. Which leads to my question do I really need to install all updates which are available for my system?!

For example, I have bunch of *Common UNIX Printing System* updates, but I don't have any printers.
(when I used Windows, I din't see any reasong to install some random update for particular software / service etc which I don't have installed or use.)

Any comments?

If you haven't already installed "**Synaptic Package Manager**" then install it. IMO it is far better than "Ubuntu Software Center".

From Synaptic choose to uninstall CUPS and see what all 'other' packages is wants to uninstall... this way YOU can figure out what to remove and what not to. 

After each Ubuntu install I REMOVE a bunch of unneeded packages myself. Some packages I am forced to keep because they are needed as dependency for another package which I want to keep. If you CAREFULLY remove unwanted applications then you won't get updates for those applications. Anything that is installed on your machine should always be updated. Don't skip updates.

---

### Post by grahammechanical on 2013-03-04
Remember, one of the main differences between Linux and Linux distributions to Windows is that Linux is under constant development and improvement as well as continued fixing of bugs and security issues as they are reported. We do not get a Linux release followed by Service Pack 1 a year later, which is then followed by Service Pack 2. By which time everyone is waiting for the next version to come out. Actually, a distribution is made up of many components that are under continue development. And we can set Update Manager not to notify us of updates if we so choose. I am not sure how Xubuntu lets you do this but in standard Ubuntu 12.10 we go to System Settings>Software Sources>Updates tab and we can set the frequency to never.

By the way Update Manager is being developed to present an interface that will help ordinary users better understand what is being updated and we get the option to uncheck each item for download. It is like this in 13.04. Regards.

---

### Post by aspergerian on 2013-03-04
My Xubuntu 12.04 computer gets offered updates related to Unity, which I removed from my computer several months ago. Ought I allow updating of Unity-related whatevers or can I safely uncheck them on the update-manager window?

---

### Post by Nr90 on 2013-03-04
You only get updates for installed programs, so you haven't successfully uninstalled them.If they are never used you can probably uncheck them.However why bother?It seems to me that the time spend unchecking stuff like that is not worth the extra couple of seconds your computer would spend updating them. Unless you're on a limited internet connection, I suppose.

---

