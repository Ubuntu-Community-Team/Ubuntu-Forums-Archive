---
title: "Delete or CTRL + Delete"
date: 2011-08-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by EgoGratis on 2011-08-29
Why did GNOME 3 developers choose this behavior for moving files to Trash? This one does have nothing to do with GNOME 3 is still young and not matured and developed enough to have support for... Why would you move Delete key to "CTRL + Delete" key for moving files to Trash?

[http://www.webupd8.org/2011/08/restore-delete-key-for-moving-files-to.html](http://www.webupd8.org/2011/08/restore-delete-key-for-moving-files-to.html)

---

### Post by pressureman on 2011-08-29
We can only hope that the Ubuntu packagers of Gnome shell will restore some of this functionality by default, so that the transition from Gnome 2 to Gnome 3 is not so jarring.

---

### Post by EgoGratis on 2011-08-29
Yes BUT why would you do that. Why would you move Delete button for moving files in to the trash to CTRL + Delete?

---

### Post by lucazade on 2011-08-29
[http://git.gnome.org/browse/nautilus/commit/?id=cce40272e35b20b4aaf5f93109a05b7bb89704d5](http://git.gnome.org/browse/nautilus/commit/?id=cce40272e35b20b4aaf5f93109a05b7bb89704d5)

> This change was made to make it harder to accidentally trigger a file
delete. We still support the trash that will let you get a trashed file
back, and we will get undo support to make this even easier. However,
that only works if you know you deleted the wrong file, not if you
accidentally hit delete while the nautilus window was focused.

has been discussed by ubuntu devs to revert the behavior.

---

### Post by pressureman on 2011-08-29
I would have thought that the trash can was sufficient protection against fat fingers.

Perhaps Gnome shell should ship with a complimentary flip up cover for the delete button, and two key locks that have to be turned simultaneously by two authorized people, just to be really sure we don't screw up.

;-)

---

### Post by cariboo on 2011-08-29
Just enable delete in Nautilus, then right-click delete.

---

### Post by EgoGratis on 2011-08-29
> **lucazade said:**
> [http://git.gnome.org/browse/nautilus/commit/?id=cce40272e35b20b4aaf5f93109a05b7bb89704d5](http://git.gnome.org/browse/nautilus/commit/?id=cce40272e35b20b4aaf5f93109a05b7bb89704d5)



has been discussed by ubuntu devs to revert the behavior.

But why would you want to "protect" users from "accidentally deleting" files and fodlers if u have Trash folder? I would understand if it would be about deleting the files permanently. So its about "protecting" 0.1% of users that have accidentally delete files and folders in to the Trash folder from where files and folders can be restored?

> **cariboo907 said:**
> Just enable delete in Nautilus, then right-click delete.

NO! There is button DELETE on the Keyboard! Not CONTROL + DELETE! User should not do anything else then press DELETE button on the keyboard to move selected files and folders in the trash folder? Why would you right click with mouse and then delete and why would you use Control + Delete? There is a button on the keyboard that does that and if u accidentally delete something you can still go to the thrash folder and restore it?

---

### Post by pressureman on 2011-08-29
What happens if/when people get confused between shift-del and ctrl-del? They think they're executing the keyboard shortcut for "move to trash", when in fact they're deleting a file permanently.

Was there really that big a problem previously, of people mistakenly deleting (moving to trash) files? I don't recall seeing the cries of anguish from thousands of users who were unable to simply go into their trash and restore a file.

---

### Post by lucazade on 2011-08-29
> **EgoGratis said:**
> But why would **you** want to "protect" users from "accidentally deleting" files and fodlers if u have Trash folder? I would understand if it would be about deleting the files permanently. So its about "protecting" 0.1% of users that have accidentally delete files and folders in to the Trash folder from where files and folders can be restored?


You should not ask me! I've only reported the original commit
If it was me I'd wipe the entire nautilus! 
anyway it doesn't seem the end of the world... :)

---

### Post by EgoGratis on 2011-08-29
> What happens if/when people get confused between shift-del and ctrl-del?  They think they're executing the keyboard shortcut for "move to trash",  when in fact they're deleting a file permanently.

Yes i was just writing this question. 

CONTROL and SHIFT keys are too close together and it is more likely users will accidentally press the wrong one on occasions!

But still why would you want to protect users in the first place when you have Trash folder by don't letting them press delete button directly?

---

### Post by EgoGratis on 2011-08-29
> **lucazade said:**
> You should not ask me! I've only reported the original commit
If it was me I'd wipe the entire nautilus! 
anyway it doesn't seem the end of the world... :)

Yes i forgot to mention i was not asking you. :D

But still in the end most of the users will have to do things like this:

[http://www.webupd8.org/2011/08/restore-delete-key-for-moving-files-to.html](http://www.webupd8.org/2011/08/restore-delete-key-for-moving-files-to.html)

This is just wrong! OK if i understand correctly Ubuntu will have this restored in time Ubuntu 11.10 is released BUT still i just can't understand why would you take delete button away from the users if u have Trash folder and say CONTROL + Delete is better. It is not?

---

### Post by lucazade on 2011-08-29
> **EgoGratis said:**
> Yes i forgot to mention i was not asking you. :D

But still in the end most of the users will have to do things like this:

[http://www.webupd8.org/2011/08/restore-delete-key-for-moving-files-to.html](http://www.webupd8.org/2011/08/restore-delete-key-for-moving-files-to.html)

This is just wrong! OK if i understand correctly Ubuntu will have this restored in time Ubuntu 11.10 is released BUT still i just can't understand why would you take delete button away from the users if u have Trash folder and say CONTROL + Delete is better. It is not?

Don't try to find a logical answer.. gnome3 is full of nonsense solutions (the shell is the first I could think of).
anyway I'd take the best and workaround the worst. :P

---

### Post by EgoGratis on 2011-08-29
To be honest i do like Nautilus and GNOME DE and Ubuntu and Unity... GnomeShell not so much at the moment...

But this one about DELETE button i just don't understand. But OK it will be "solved" and that is OK!

---

### Post by akand074 on 2011-08-30
Yeah I think it's stupid too. When I was using Gnome-shell in Natty I just set it back to just Delete.

---

### Post by coffeecat on 2011-08-31
I'm with the OP on this one. Good grief! What are the upstream gnome devs thinking about? Are they actually thinking?

I'm more likely to accidentally hit shift-delete instead of ctrl-delete and lose an important file irretrievably than hit delete accidentally and then *accidentally* empty the trash. :rolleyes:

I'm beginning to understand why Mark and co decided to go their own way with Unity rather than follow all the fevered imaginings of upstream.

---

### Post by 3rdalbum on 2011-08-31
So Shift-Delete immediately deletes a file with no notification? That's really ill-thought-out.

Control-Delete is a half-sensible idea for moving files to the trash, instead of merely the Delete key. I can definitely see users attempting to rename a file and press Delete to delete the filename, only to have the file disappear (because they weren't in the renaming mode, but they didn't know and now they think they've lost their file).

---

### Post by mc4man on 2011-08-31
> **3rdalbum said:**
> So Shift-Delete immediately deletes a file with no notification? That's really ill-thought-out.

There is by default a confirmation pop up on Shift-Delete, Ctrl-Delete does not have one

---

### Post by EgoGratis on 2011-08-31
> **3rdalbum said:**
> So Shift-Delete immediately deletes a file with no notification? That's really ill-thought-out.

Control-Delete is a half-sensible idea for moving files to the trash, instead of merely the Delete key. **I can definitely see users attempting to rename a file and press Delete to delete the filename, only to have the file disappear (because they weren't in the renaming mode, but they didn't know and now they think they've lost their file).**

Sorry but i don't "buy" that. 

If this accidentally happens to you then you go to Trash folder and restore the file or folder?

Why would you force all users to use 99.9% of the time they delete files and folders to not use Delete button and use CTRL + Delete instead, just because on rare occasion somebody will have to go in to the Trash folder and restore his file or folder?

I am not wiling to explain this to users i help using Ubuntu why they must press CTRL + Delete and not just Delete button. I don't understand it and they will not understand it too.

> I'm beginning to understand why Mark and co decided to go their own way  with Unity rather than follow all the fevered imaginings of upstream.To be honest i don't see nothing wrong in providing for example different "Shell" to you users on top of some DE BUT i don' t understand why for example GNOME, KDE... and users of this DE don't have for example "common composition manager". Why would everybody want to have it's own and solve the same hard problems and develop it in the same direction other does. Compete in other areas that are useful to users for example "Shell", but not in areas like "composition manager" where is just important that it works good and is modern. You can use all the help you can get to make it like that and you have to have it in the end. Just like your "competition" does. The "competition" that is developing THE SAME "FOSS THING" AND IN THE SAME DIRECTION!

---

### Post by pressureman on 2011-08-31
> **coffeecat said:**
> I'm beginning to understand why Mark and co decided to go their own way with Unity rather than follow all the fevered imaginings of upstream.

This particular issue is a characteristic of Nautilus 3.x, not Gnome Shell specifically, so it will also affect Unity users.

---

### Post by vpharry on 2011-08-31
> **EgoGratis said:**
> Why did GNOME 3 developers choose this behavior for moving files to Trash? This one does have nothing to do with GNOME 3 is still young and not matured and developed enough to have support for... Why would you move Delete key to "CTRL + Delete" key for moving files to Trash?

[http://www.webupd8.org/2011/08/restore-delete-key-for-moving-files-to.html](http://www.webupd8.org/2011/08/restore-delete-key-for-moving-files-to.html)
Ya this is a terrible idea..... with d amount of changs commin thick n fast it is sure 2 confuse d avg ubuntu user...... I hope it doesnt stay tat way when d final version is releasd.

---

### Post by EgoGratis on 2011-09-02
After today updates i tried pressing Delete button on group of selected files and folders and it was successfully moved to the Trash folder!

Thanks developers!

---

### Post by quids on 2011-09-02
Sweet yes that update to Nautilus has fixed things.

Now thats one change I certainly like, it was driving me mad not being able to delete files the way I've been deleting them the days of DOS Shell or was it Windows 3.1... Either way far too many years to be changing now

---

