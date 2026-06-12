---
title: "[SOLVED] get rid of gnome panel"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Zopiac on 2008-06-01
how do i get rid of my last gnome panel? i have made awn a complete replacement for it (well, i and a lot of help :) ) so now it is just taking up room.

---

### Post by sayakb on 2008-06-01
1. Goto System->Preferences->Sessions, click on Current Session tab
2. Select gnome-panel and change the **Style** from Restart to Trash.
3. Click on Session Options tab and **check ***Automatically remember running apps...*
4. Close the sessions window
5. Now open a terminal and issue: ```
killall gnome-panel
```6. Logout and login again.

---

### Post by Joeb454 on 2008-06-01
Can you not just right click it and choose "Delete Panel"

---

### Post by sayakb on 2008-06-01
> **Joeb454 said:**
> Can you not just right click it and choose "Delete Panel"

I think the last panel cannot be deleted.

---

### Post by Joeb454 on 2008-06-01
I still have both, so I wouldn't know ;)

---

### Post by shifty_powers on 2008-06-01
yup. i've got one left, and it won't delete ;)

---

### Post by Zopiac on 2008-06-01
> **LinuxIsInnovation said:**
> 1. Goto System->Preferences->Sessions, click on Current Session tab
2. Select gnome-panel and change the **Style** from Restart to Trash.
3. Click on Session Options tab and **check ***Automatically remember running apps...*
4. Close the sessions window
5. Now open a terminal and issue: ```
killall gnome-panel
```6. Logout and login again.

why must i remember current apps?

edit: well ok i figured it out, if you dont the gnomepanel will start up again, but i like to leave that option off because otherwise a nautilus will be open whenever i log in :/

---

### Post by olavjunior on 2008-06-02
You're only using awn? Wao, how do you manage? I just removed the last panel, but now I realized that alt-F2 won't do a thing anymore. And that one, I use a lot! Plus I liked alt-F3 as well (deskbar applet). It's a shame these doesn't work with awn!

---

### Post by Zopiac on 2008-06-04
> **olavjunior said:**
> You're only using awn? Wao, how do you manage? I just removed the last panel, but now I realized that alt-F2 won't do a thing anymore. And that one, I use a lot! Plus I liked alt-F3 as well (deskbar applet). It's a shame these doesn't work with awn!

oh so thats why alt+f2 isnt working....well the powers been out most of like the last two days, so i havent done much to figure that out anyways :P

---

### Post by Zopiac on 2008-06-06
actually, even though i disabled remember windows, it still remembers. solution?

---

### Post by Zopiac on 2008-08-07
I just made a new account, and needed to do this again, but settled for adding a startup program with the command 'killall gnome-panel'. works like a charm

Edit: hrmm...perhaps not, thought it did tho

---

### Post by paraplegicpanda on 2009-06-07
Okay, I'm running Jaunty now and I'm having issues pulling this off. I had no problem in Intrepid... Unfortunately now that the "Sessions" menu has been changed to "Startup Applications" I am having issues. Just adding an entry for "killall gnome-panel" to the Startup Applications menu doesn't do the trick... Any suggestions?

---

### Post by roadtripdave on 2009-12-30
I was able to get rid of the gnome-panel.. worked pretty easily, however I'm waiting for any potential side affects...nothing so far though.  I'm using Karmic and have Avant running and all I did was load up the recovery kernel, drop into a root shell and rename /usr/bin/gnome-panel to /usr/bin/gnome-panel-DISABLE and rebooted.  And here I am..haha  Just wanted to share, use at your own risk.. ;)

Dave

---

