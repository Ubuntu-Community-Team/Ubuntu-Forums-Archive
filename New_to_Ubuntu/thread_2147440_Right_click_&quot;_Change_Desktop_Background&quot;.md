---
title: "Right click &quot; Change Desktop Background&quot; &amp; &quot;create new launcher&quot; not working."
date: 2013-05-22
forum: New to Ubuntu
---

### Post by joyblaze on 2013-05-22
Hi,

I'm new to ubuntu OS and I have installed ubuntu 13.04 (32 bit) yesterday (fresh installation), where i was able to chnage the desktop background even by right clicking and selecting the wallpaper.
However from "software updater" i got some message that there are some updates available (approx 144 MB) i clicked yes, and the updates were installed.

One thing i noticed this morning, is that Right clicking on desktop and selecting "chnage desktop background" or "create new launcher "is not working, i mean nothing comes out.
Though i can chnage the desktop background from systesm setings>>appearence.

Could any one guide me, do i need to tweak some thing to make right click options working.

Thank you,
BR

---

### Post by Tjkhan on 2013-05-22
I m using ubuntu 12.04 (64bit). ubuntu 13.04 isnt so good if u ask me. i tried that, not good for me.

Well, can u remember what update u have installed? 
Did you changed anything recently? 

u have time then install ubuntu again.

---

### Post by joyblaze on 2013-05-22
I'm not sure what updates are being installed, may be those are some system updates.
Before installation of these updates, all right click options were working, now "change desktop background" and "create launcher" is not working via right click (context menu)

Any clues on how to fix this.

Thanks.

---

### Post by Tjkhan on 2013-05-22
Does "Appearance" come? by using "dash home"?

---

### Post by Tjkhan on 2013-05-22
seems ur last update conflicting

---

### Post by joyblaze on 2013-05-22
Yes appearance comes up from the dash, and i use this without any issues.
The only problem is with Righ click selections.

---

### Post by deadflowr on 2013-05-22
First off, I know not how create a new launcher is available, do you mean create a document, or create a folder?

Secondly, you can post the output from the log file

```
cat /var/log/apt/history.log | tail -n 10
``` 

You can change the 10 to 20 or 30 if you want. It will grab the last ten lines of the history file which is what will show us what's been installed or removed.

Edit: If you post back the results, please you the code tags (the  # symbol in the reply box toolbar).

---

### Post by joyblaze on 2013-05-22
Hi,

I have problems only with right click options like "Change desk top background" and "Create new launcher" selecting these options from right click menu does nothing bbut other options like create new folder and create new documents works ok.

Any tweaks or clues how can i make the right click option work for above issue.

Thanks

---

### Post by monkeybrain2012 on 2013-05-22
I  never noticed that there is a "create new launcher" option in the right click menu .  Other than that is supposedly missing, --since you say it should be there,--I can change background with right click for sure (12.04 and 13.04). I think you create desktop launcher by just dragging the icon to the desktop, or the old way, drag it from /usr/share/applications. In gnome there is a thing called "main menu" with which you can create new .desktop file without using an editor, don't think it works in Unity though.

---

### Post by joyblaze on 2013-05-22
May be i got the options after yesterdays software updates, i will paste the screen shot here after i'm back to home.
I have problems only with right click options like "Change desk top background" and "Create new launcher" only.

---

### Post by joyblaze on 2013-05-22
Hi,

To be more precise, please see the below screen shots, i have highlighted in red which options of right click are not working as mentioned.
Nothing comes up when i click "create launcher" or "change desktop background."

[IMG]http://imageshack.us/a/img600/6369/rightclick.png[/IMG]

Just to confirm i'm using Ubuntu 13.04
[IMG]http://imageshack.us/a/img703/9127/ubuntuck.png[/IMG]

Any help on the way to fix is appreciated.

Thanks

---

### Post by Bladeforce on 2013-06-06
Sorry to bump this but I have the same problem with right click change desktop background from desktop too, it doesnt open appearance settings. Although my right click create launcher works

---

