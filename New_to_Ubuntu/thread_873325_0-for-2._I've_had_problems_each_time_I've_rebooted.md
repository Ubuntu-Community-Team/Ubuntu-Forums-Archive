---
title: "0-for-2. I've had problems each time I've rebooted or shut down my system."
date: 2008-07-28
forum: New to Ubuntu
---

### Post by ready4thebreak on 2008-07-28
This is the second time I've rebooted Ubuntu since I've got it, both times, I've had some kind of problem.  Last time is unimportant because I just did a fresh install, but I shut down my comp last night and now today, when I restarted, the top panel was missing. Luckily I had the trash bin on my desktop, so I can search for the programs I'm looking for, but I have got to get that panel back! I feel like such a loser, but I'm so Windows trained that I don't know how to do this. lol.

Thankfully I have you guys to save me!

---

### Post by UbuntuNerd on 2008-07-28
click on the panel you got and click new panel

---

### Post by ready4thebreak on 2008-07-28
no that's the problem I have NO panels!(I was using AWN)

---

### Post by UbuntuNerd on 2008-07-28
also if the panel you added is empty click on it and press add to panel and from there find the things you used to have in your panel before hope this helps

---

### Post by ready4thebreak on 2008-07-28
It's literally just my background and desktop!(Sorry I should have said all of this in my first post)  I tried Right-Clicking everywhere on the screen, on both workspaces, and no luck!

---

### Post by UbuntuNerd on 2008-07-28
press ALT+F2 and in the run dialog box, type gnome-terminal then click on Run.


Once the Terminal window opens, enter the following command at the prompt:

gconftool-2 - -shutdown

(Note: There should be no spaces between the two dashes before shutdown.)

Then enter the next command:

rm -rf ~/.gconf/apps/panel

And enter one more command:

pkill gnome-panel

That's it! 


you should see the panels and if only one appears then use it to get the other

---

### Post by ready4thebreak on 2008-07-28
hmm wtf! My run command isn't working! I just can't win! I've used run a few times, so I know it's worked in the past. 

I gotta get that fixed somehow. but I searched Terminal and got to it that way.

---

### Post by ready4thebreak on 2008-07-28
I tried the gconftool-2 - -shutdown(yes I deleted the spaces) and it keeps saying command unavailable. 


rm -rf ~/.gconf/apps/panel

I could have swore I've heard people say not to do rm -rf command before?

---

### Post by ready4thebreak on 2008-07-28
Any help from anyone? This has to be a simple fix.

---

### Post by ready4thebreak on 2008-07-28
Please this is the biggest hassle not having the taskbar!

---

### Post by hubie on 2008-07-29
> **ready4thebreak said:**
> I tried the gconftool-2 - -shutdown(yes I deleted the spaces) and it keeps saying command unavailable. 


rm -rf ~/.gconf/apps/panel

I could have swore I've heard people say not to do rm -rf command before?

rm is the remove command, which is how you remove files or directories.  The option "r" is recursive, which means it will traverse down all the directories from where it is told to start.  The "f" option is force, which means it will force the remove by not prompting you if you really want to do that.  Here you would be telling it to recursively delete down from the .gconf/apps/panel directory in your home directory.

Where you get into big trouble is if you run rm -rf from the root directory, or from the top of your home directory.  Every now and again someone who thinks they are funny will tell a newbie to run a version of that to wipe out their system (there are all sorts of variants on that).

---

### Post by ready4thebreak on 2008-07-29
I did what he said and no panel appeared, do you have any help or suggestions?

---

### Post by hubie on 2008-07-29
I'm sorry to say that I cannot be of much help with your problem.

---

### Post by pi.boy.travis on 2008-07-29
When I first installed Ubuntu 7.10 I had this problem.  I had errors on my install disk, and I was surprized that it installed at all.  As long as you don't have any important information on your computer (assuming you don't because it is a fresh install) I would recommend trying again with a new CD that you have checked for errors.  *A clean install fixes all. . .*

---

