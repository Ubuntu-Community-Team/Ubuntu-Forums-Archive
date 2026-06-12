---
title: "Make Ubuntu ask for password after PC idling or closing the laptop lid?"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Dani Filth on 2008-05-08
Hi folks,

I don't really know how to put this, and I did try google with "ubuntu authenticate require password after pc idling or closing the lid" but I couldn't seem to find a relevant topic. So please help me with this matter. I'm using 8.04 at work, and occasionally I have to go out to other places and leave my laptop there idling. 
The problem is my colleages like to play pranks using my laptop when I leave it there (pranks don't seriously harm, but sometimes I don't like them), in Fedora, if I leave the PC idling for a while and when I come back, it requires me to enter password to grant access, so how can I make that one in Ubuntu too?
(I don't want to log off cause perhaps I have some programs running in my PC)

Thanks in advance. :popcorn:

---

### Post by asrai on 2008-05-08
I'm not sure how to set it to do it automatically - but ctrl-alt-L locks the screen for me.  You just need to type any key to wake it up and then log back in with your password.

I'm sure someone will be by shortly to tell you how to do it automatically on idle :)

---

### Post by kpkeerthi on 2008-05-08
In the screensaver settings panel, enable a screensaver (of your choice) after certain idle time and choose the option to lock the screen when screen saver activates.

---

### Post by asrai on 2008-05-08
Brilliant, thank you kpkeerthi

---

### Post by Dani Filth on 2008-05-08
kpkeerthi : It works! Thank you! :popcorn:

asrai : Ctrl Alt L doesn't work for me as shortkey to lock the screen, but I guess I have to set up the key for that. Thanks anyway! :D

---

### Post by hob on 2008-05-09
Getting to your other question about locking the screen when the lid closes, I used this extensively in Fiesty, and it worked great. 

However, it seems to have disappeared in Hardy, and I can't seem to find the setting to activate this feature. Does anybody have any ideas about automagically locking the screen when the laptop lid closes?

---

### Post by sdennie on 2008-05-09
You can make the screen lock with the lid closing screen blank by starting gconf-editor and going to /apps/gnome-power-manager/lock and selecting blank_screen.

---

### Post by hob on 2008-05-09
Thanks vor. I opened up "gconf-editor" in a terminal and it works now!

---

### Post by forumache on 2008-05-09
Leave the gconf-editor alone, there is no need for it for this task.

You can go to menu system->preferences->power management
where you will find a dropdown box from which you can select what the OS does when the lid is closed (on AC and on battery). Select Blank Screen.

Explore other options you have in System|Preferences.

Good luck,
Dan.

Later edit: I see now that you used the gconf-editor. It does the same job, though it might scare some people. Good that you are not one of them ;)

---

### Post by sdennie on 2008-05-09
> **forumache said:**
> Leave the gconf-editor alone, there is no need for it for this task.

You can go to menu system->preferences->power management
where you will find a dropdown box from which you can select what the OS does when the lid is closed (on AC and on battery). Select Blank Screen.


That's the proper way to turn on screen *blanking* for the lid but, there is no other way to setup screen *locking* for lid other than to use gconf-editor.

---

### Post by forumache on 2008-05-09
Thanks vor, good to know. I misunderstood the question.

---

