---
title: "[SOLVED] Home folder has moved to my desktop"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by avanrens on 2008-09-29
Somehow my home folder has moved to my desktop how do I move it back. If I create a home folder and then copy the files into the new home folder the system won't boot.

---

### Post by lazyart on 2008-09-29
That is just a launcher (or to borrow a windows term, a "shortcut") to your home folder. Desktop is a folder within your home, so it can't be the other way around.

If you don't like seeing it there, just delete the launcher from the desktop.  It's a convenience item.

---

### Post by frankleeee on 2008-09-29
I don't think home has moved to your desktop it is just the icon to access it. I use a program called Ubuntu Tweak which can do many easy access changes, like putting several icons like home on the desktop or take them off. Somebody who knows the actual area that makes this change will probably post a solution.

---

### Post by avanrens on 2008-09-29
Thanks for the info but if I create a home folder and move all the icons on my desktop to the created home folder it won't boot. Everything works but its as if my home folder has now become the desktop

---

### Post by frankleeee on 2008-09-29
Your description is vague are you right clicking to make a folder then naming it home or have you moved icons to the built in home access icon on the desktop. If you have moved things to the access icon you can drag them from home back to the desk top or panels.

---

### Post by avanrens on 2008-09-29
I'm right clicking and then creating a home folder and copying the icons from my desk top into it , I then re-boot and the system fails to boot.If I then restore, that is all the icons back on the desktop the system boots, its as if the home folder has now become the desktop. I think this all happened when I took a Video of my desktop using Istanbul and saved the file as desktop!

---

### Post by frankleeee on 2008-09-29
> **avanrens said:**
> I'm right clicking and then creating a home folder and copying the icons from my desk top into it , I then re-boot and the system fails to boot.If I then restore, that is all the icons back on the desktop the system boots, its as if the home folder has now become the desktop.

Right clicking and calling it a the home folder is confusing, it is the home of whatever you put in it. What did you put in the made folder, and have you deleted anything, or moved it to the trash.

---

### Post by kansasnoob on 2008-09-29
Look at my screenshot:

[ATTACH]86715[/ATTACH]

Does Home Folder no longer show up at the top of the right column.

BTW, I know your menu looks different, due to poor eyesight I customize mine.

---

### Post by avanrens on 2008-09-29
When I select Places then Home folder I only get Desktop and not the whole home folder with desktop as a folder in the home folder.My home folder is on a different drive so that I can boot from different drives and use the same /home folder. I have just booted from the other system and its the same that is the home folder is on the desktop.

---

### Post by kansasnoob on 2008-09-29
> **avanrens said:**
> When I select Places then Home folder I only get Desktop and not the whole home folder with desktop as a folder in the home folder.My home folder is on a different drive so that I can boot from different drives and use the same /home folder. I have just booted from the other system and its the same that is the home folder is on the desktop.

I've never tried sharing a home partition between operating systems, so I'm clueless:confused:

---

### Post by Elfy on 2008-09-29
Have a look in /apps/nautilus/preferences and check that desktop_is_home_dir is not checked

Alt+F2 and run gconf-editor

---

### Post by avanrens on 2008-09-29
Thanks for all the help, it's not that bad the system still operates normally I just have all the icons from my home directory on my desktop.I can live with that, thanks again.

---

### Post by avanrens on 2008-09-29
> **forestpixie said:**
> Have a look in /apps/nautilus/preferences and check that desktop_is_home_dir is not checked

Alt+F2 and run gconf-editor
No its not selected thanks all the same

---

### Post by Elfy on 2008-09-29
Bit odd - you could check here 

~/.config/user-dirs.dirs

but you don't appear to be too worried :D

---

### Post by johnubu on 2008-09-29
First time post, here goes...

Can't seem to rid the desktop of folders.

When I use: 
Alt+F2 and run gconf-editor the display on the left
blinks like crazy.

Image shows the relevant stuff I hope.

Any help appreciated

---

### Post by Elfy on 2008-09-29
@johnubu - if you can't use gconf-editor to disable the value of /apps/nautilus/preferences/desktop_is_home_dir 

You could change the value in the file you have opened. Using nano as the editor (Ctrl+O, enter to save, Ctrl+X to exit)

```
nano ~/.config/user-dirs.dirs
```

Find the line which says > XDG_DESKTOP_DIR="$HOME/" change to read
> XDG_DESKTOP_DIR="$HOME/Desktop"save and logout,

---

### Post by johnubu on 2008-09-29
Thanks for your suggestion *forestpixie*

As you can see the edit gave me a johne folder in the 
/home folder (upper part of the left hand column). That's good.

But when I double click Desktop there is nothing there even
though the actual Desktop (onscreen) still contains the folders.

My goal is to empty the Desktop of my home folders.

Please excuse the images, I'm a photographer :)

---

### Post by Elfy on 2008-09-29
You should have a 'name' folder in /home - it is your users home (assumption being that johne is user), and Desktop inside /home/user.

Unedit it ```
nano ~/.config/user-dirs.dirs
``` and change it back and use gconf-editor to change it.

If you still have problems please start your own thread on it

---

### Post by johnubu on 2008-09-29
I'll try that. Thank you *forestpixie*

---

### Post by avanrens on 2008-09-29
> **forestpixie said:**
> Bit odd - you could check here 

~/.config/user-dirs.dirs

but you don't appear to be too worried :D
I can't find user-dirs.dirs

---

### Post by avanrens on 2008-09-29
> **forestpixie said:**
> Bit odd - you could check here 

~/.config/user-dirs.dirs

but you don't appear to be too worried :D
Got it to work here's the output.

---

### Post by Elfy on 2008-09-30
Ok as you can see the file is pointing at XDG_DESKTOP_DIR="$HOME/" - afaik it should be XDG_DESKTOP_DIR="$HOME/Desktop"

Try editing the file to show "$HOME/Desktop"

---

### Post by avanrens on 2008-09-30
Thank you just so much its all back to normal again.
Now how do I mark this as solved.

---

### Post by Elfy on 2008-09-30
Cool - use the thread tools at the top, there wil be an option for you to mark as solved.

---

### Post by JPeterguy on 2009-12-29
> **forestpiskie said:**
> Ok as you can see the file is pointing at XDG_DESKTOP_DIR="$HOME/" - afaik it should be XDG_DESKTOP_DIR="$HOME/Desktop"

Try editing the file to show "$HOME/Desktop"

I seem to be having this same issue, but don't know how to edit this file. Does anybody know how I can do this?

---

### Post by keef123 on 2011-10-08
Ah, thank you so much for this fix. I've been pulling my hair out over this. No idea how I managed to get my home folder on my desktop but very glad it's solved.

---

### Post by nothingspecial on 2011-10-08
Glad to here you got it sorted :)

But this thread is old and tired and needs to sleep.

Closed.

---

