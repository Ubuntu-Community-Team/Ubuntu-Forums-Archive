---
title: "Apps Bar disappered after installing Compiz Settings Manager"
date: 2012-12-21
forum: New to Ubuntu
---

### Post by Fuser77 on 2012-12-21
Hi There,

I think I already posted it but am not able to retrieve the thread...

After installing Compiz and playing a little bit around with the Settings Manager, the Apps Bar disappeared.
This happened on the main profile user, which happens to be the admin of the PC.
I can't (or I don't know how to) access any of the applications with that profile and don't have a clue o how to solve the problem.

Please help!!!

(Please be patient, I am REALLY new to Ubuntu and am running on 10.12)

---

### Post by superDave972 on 2012-12-21
Try opening a terminal (CTRL-ALT-T) and then type the command 'unity --reset' (without the quotes)

---

### Post by Fuser77 on 2012-12-21
Thank you, SuperDave!
That did not work...

---

### Post by Fuser77 on 2012-12-21
Ok, apparently it is still trying to do something... This is taking long time!!!!

---

### Post by deadflowr on 2012-12-21
Do remember what you were trying to muck about with?

On using the compizconfig-settings-manager, note that changes can take a moment to take effect.
If something like this happens, and you end up with a blank desktop, use the ctrl+t terminal keyboard shortcut and type ccsm.
You can try reseting it from here by going to the sidepane entry 'preferences' and in the profile section is a tab marked 'reset to defaults'.(The profile will most likely be marked Unity).
Another thing is to open up and look to see if the unity shell plugin(Or Ubuntu Unity Plugin)is checked for enabled.(Unlike other setting in the compizconfig-settings-manager the unity plugin doen't have a checkbox on the main page, so it'll need to be opened to check it).

---

### Post by Fuser77 on 2012-12-21
Thank you, DeadFlowr!
The ccsm command did work.
Apparently I had accidentally unchecked the "Enable Plug In" option, desktop did come back to normal after re-checking this option, but...
In the Profile Section there was no Unity marked, when I selected it and restored to defaults the problem came back again. The only Default that gets the desktop working correctly is Default # 2 (not differentiated by numbers, both are named Default...!)
While CCSM was coming back to normal it triggered a couple of messages asking me to confirm changes in the key settings that could conflict with the already established key settings... I think I declined the offer but am not too sure of what I did.

I sense that something is wrongly configured...
Any other suggestion?
I really appreciate your help!

---

### Post by deadflowr on 2012-12-21
It's not overly odd to not see a unity profile( the defaults should suffice).
In terms of re-enabling the unity plugin, I usually check 'resolve conflicts' and in the second issue it usually brings up something about the run dialog, with this I usually pick the first option which should say 'set something something anyway'.

Of course this is all based on my own experience and I have found circumstances vary system to system.

---

### Post by Fuser77 on 2012-12-21
Great!
Thanks a lot for the piece of advice!

---

### Post by deadflowr on 2012-12-21
> **Fuser77 said:**
> Great!
Thanks a lot for the piece of advice!

If it works it works.

When I started using Ubuntu, if I felt the system was slightly off or I encountered problems I couldn't fix upon seeing it, I just reinstalled(I must have reinstalled a half-dozen times in the first few weeks.) I did this because the installation process was and still is a breeze. Plus all my files and data are always backed up.(Always back up your stuff).

I guess what I'm saying is, when in doubt there is nothing wrong with cleaning house and reinstalling if you feel either that something is wrong or the fix isn't up to snuff.

---

### Post by Fuser77 on 2012-12-21
It's a little bit of a hassle having to reinstall when you start feeling comfortable with the settings, but I'll keep that in mind!

---

### Post by Fuser77 on 2012-12-21
Hey, I am noticing that, in order for Compiz to take effect, I need to "unity - reset" after re-booting every time.
Also, sometimes it works partially.

I tried installing Compiz Fusion Icon, clicked on it, nothing happened...

Can I fix this without re-installing?

Thank you!

---

