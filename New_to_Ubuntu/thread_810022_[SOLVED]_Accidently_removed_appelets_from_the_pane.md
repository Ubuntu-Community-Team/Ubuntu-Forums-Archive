---
title: "[SOLVED] Accidently removed appelets from the panel. Now, how to get them back?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by bhadotia on 2008-05-27
I accidently removed the   following appelets fom the panel:

Battery icon, google desktop icon , gnome network manager icon , compiz fusion icon.

After tyying a lot I am unable to restore them . Can some body help , please?
Thank you in advance.

---

### Post by iaculallad on 2008-05-27
> **bhadotia said:**
> I accidently removed the   following appelets fom the panel:

Battery icon, google desktop icon , gnome network manager icon , compiz fusion icon.

After tyying a lot I am unable to restore them . Can some body help , please?
Thank you in advance.

Right click on the panel and select "Add to Panel", from there you could select any icon you want to be included in the panel.

---

### Post by bhadotia on 2008-05-27
I have tried  that already but there are no applets for network-manager-gnome, battery indicator is there but is not the same as the one installed before, and there are no applets for google desktop and compiz fusion icon.

---

### Post by kansasnoob on 2008-05-27
If you've tried searching the menu of applets after right clicking an open space on the (or either) system tray you could install "alltray" from synaptic which will let you drag-n-drop any applet from any menu on your desktop.

---

### Post by bhadotia on 2008-05-27
But there are no menu items for these appelets , the were installed by default when I installed various software or were in the by panel by default from the very beginning.


Is there no way in which I can undo the delete operation , so that the original configuration of the panel is restored?

---

### Post by iaculallad on 2008-05-27
Let's restore them to its default setting:

Drop to your terminal:

> sudo gconftool-2 –shutdown
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel

---

### Post by bhadotia on 2008-05-27
The first command was .... --shutdown and not  .... -shutdown.

I restarted the  the computer after  giving those commands and the panel was restored to its original state.

Thank you very much:)

---

### Post by iaculallad on 2008-05-27
No problem, you're welcome. Go Ubuntu

---

### Post by LeoSolaris on 2008-05-27
The one you had before and killed was the notification area, not individual applets. I did this too and panicked. Just re-add the notification area (At least that's what I remember it being called, it's been a few months since I had the panel on my desktop at all.)

I remember missing the network manager part of the notification area too, because I have a laptop, and switched wireless spots often. I found Wifi-Radar is just as effective and fits on my AWN bar.

Resetting the panel to default would also work, but it's sorta over kill. AllTray will get your fusion-icon and google desktop icon back. I am not sure how you had them to begin with without AllTray to be honest.

Hope that helps.

Leo

---

### Post by drs305 on 2008-05-27
Once you have your panels reset to your liking, you can save/backup the settings by running this command. It will store the settings in a file on your Desktop named 'panel_settings' (or you can choose your own path/name). 
```
gconftool-2 --dump /apps/panel > ~/Desktop/panel_settings
```

Restore the saved settings and then refresh the panels:
```
gconftool-2 --load ~/Desktop/panel_settings && killall gnome-panel
```

---

### Post by bhadotia on 2008-05-28
@ LeoSolaris 

It is called the notification area and is there in the applet menu for the panel. 
Thanks for this information!

Well I don't have all tray but still the google desktop icon was installed by default on the panel when I installed google desktop  (only this evening). About the compiz fusion icon; well, I manually added it in the start up programs in the system>preferences>sessions, and it was not on the panel by default.


And I don't like AWN nor wi-fi radar:)

Still , many thanks for the information.

@drs305

Hey, thanks for that man!:)

---

### Post by LeoSolaris on 2008-05-28
@bhadotia: Nor do I blame ya, Wifi radar is a bit odd, but I have to say that the BZR version of AWN is rather nice. But to each his own. Glad to have helped out. I really freaked out the first time I accidentally lost the notification area.

For the two missing ones, try making launchers for them. There should be a launcher applet if I recall correctly. If it is anything like making a launcher on the desktop, all you have to do is name it and put in the command to start it, and maybe hunt for an icon. With Alltray, you could make those launches on the desktop and just drop them on the panel.

By the way, completely off topic, are you Buddhist by chance? Your name looks familar, but I can't place it. Almost like Bhoddivista (ok bad spelling I know, but spelling has never been my strong suit) but not quite. EDIT:After reading your location, I feel a little foolish. Hindu would have most likely been a better guess. :oops:

@drs305:  Cool! I learn new tricks ever time I log in here.

---

### Post by bhadotia on 2008-05-29
Yup! I am a hindu (Hare Krishna (ISKCON) follower ,more appropriately) and a spiritually-interested kind of a guy as can be guessed from the avatar (a monk).

---

