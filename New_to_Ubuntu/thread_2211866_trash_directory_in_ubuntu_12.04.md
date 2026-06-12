---
title: "trash directory in ubuntu 12.04"
date: 2014-03-18
forum: New to Ubuntu
---

### Post by stefabarta on 2014-03-18
hi everybody. my OS is ubuntu 12.04, and my problem is i do not know how to access the Trash. when the space on disk is getting low a pop up asks me if i want to empty the trash, but i would like to access the trash anytime i need, for example to restore files, or to definitely eliminate ones. how do i access the trash directory? thank you!

---

### Post by 3rdalbum on 2014-03-18
The Trash is the bottom icon in the panel on the left side of the screen.

---

### Post by monkeybrain20122 on 2014-03-18
Open nautilus (the file manager), under Files (at the top left corner of the screen), choose Preferences > Behaviour and check the box "Include a Delete command that bypasses Trash" then next time when you right click and choose "Delete" things really get deleted.

I find this idea of Trash annoying, it has to a most retarded design (probably "inspired" by Windows) When I delete something I want it to be deleted, not to be moved to another folder and taking up space quietly.

---

### Post by stefabarta on 2014-03-18
oh, thx, i'll check, strange if i have not noticed it yet, but i'll check.

---

### Post by stefabarta on 2014-03-18
@monkeybrain20122: in nautilus the trash icon does not show up, don't ask me why...

---

### Post by deadflowr on 2014-03-18
> **stefabarta said:**
> @monkeybrain20122: in nautilus the trash icon does not show up, don't ask me why...

?
Trash Icon?

Isn't trash listed in the side pane.
You can right click to empty trash.

As 3rdAlbum stated, there should be a trash Icon on the launcher.
You can also empty that the same way.

Ubuntu's launcher uses an added option known as quicklists.
Right click on a launcher and it should give some added options.
Some, like Firefox will give option to open new windows, or private windows.
Others like Movie Player, will give extended options like Play and Pause.

Trash is the same.

---

### Post by whitesmith on 2014-03-18
Or you could sharpen your CLI skills by opening a terminal (Ctrl+Alt+T) and```
cd ~/.local/share/Trash/files
rm *
```

---

### Post by Carlos_Moreira on 2014-04-18
I have found that by going into the root's trash (via terminal), this doesn't remove the user's trash. So say I'm user "Johnny" and I move something to the trash bin. I can't delete it via the terminal using the examples above (i.e. ~/.local...etc). You have to run the following (replacing "username" with your user's name):

shred -n 5 -zfu /home/username/.local/share/Trash/files/*

or

rm -rf /home/username/.local/share/Trash/files/*

I've placed the shred command from above into a shutdown script I use when I shutdown my computer. This is what works for me.

---

