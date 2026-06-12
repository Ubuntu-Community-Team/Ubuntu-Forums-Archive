---
title: "[SOLVED] Firetray Icon gone"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by lariosa42 on 2008-10-31
OK, so I tried to move my Firetray icon (extension for thunderbird) and I accidentally removed it from the panel.  It does not show up in the "add to panel menu."  I tried reinstalling the add-ono with no luck.  I use this icon all the time.  How do I get it back?  Please help!

---

### Post by talsemgeest on 2008-10-31
Have you tried using the complete uninstall from the synaptic package manager, then installing it again?

Hope it helps :)

---

### Post by lariosa42 on 2008-11-02
I tried uninstalling and re-installing Firetray, but since it is an add-on to Thunderbird, it doesn't show up in Synaptic.  I would try to uninstall/reinstall Thunderbird, Firefox, and Lighning, and then install Firetray, but I had a hard time finding a way to save all my preferences, e-mails, calendars, etc.  (I found some vague hints on the forums after much searching.)  

Is the information that keeps it from showing up in the panel somehow stored in the files related to the panel rather than in Thunderbird/Firetray's files?

---

### Post by lariosa42 on 2008-11-16
Not having the Firetray icon is starting to seriously affect my work habits.  I get important e-mails all the time, and if I'm not at my desk to see the quick Thunderbird message, I sometimes miss the message and my advisor gets one step closer to killing me. 

I have uninstalled Firetray, downloaded a new version, reinstalled, and restarted a few times.  I tired searching through my ~/.mozilla-thunderbird directory to see if there were any left-over files after I uninstalled, but no luck.

Can somebody please help, and soon?!  I want to remain alive.

---

### Post by ugm6hr on 2008-11-16
> **lariosa42 said:**
> OK, so I tried to move my Firetray icon (extension for thunderbird) and I accidentally removed it from the panel.  It does not show up in the "add to panel menu."  I tried reinstalling the add-ono with no luck.  I use this icon all the time.  How do I get it back?  Please help!

You can't move a System Tray icon.  Did you delete the whole system tray - do you still have the network manager icon?

Is Firetray enabled in the Firefox Addons.

---

### Post by lariosa42 on 2008-11-16
Actually yes, this was my original mistake.  My Network Manager disappeared at the same time.  I guess I must have deleted the system tray <slaps forehead>.  How can I restore this?

Oh, and Firetray is enabled in the Thunderbird Addons, but wasn't installed in Firefox, so it doesn't show up in the Firefox Addons.

---

### Post by lariosa42 on 2008-11-16
I got it!  I found the answer in [this]("http://ubuntuforums.org/showthread.php?t=486328") post.

All I had to do was right-click on the main panel/menubar thing, and add "Notification Area" (which seems oddly named).

Thanks for your help!  You saved my life! =)

---

### Post by talsemgeest on 2008-11-16
Right-click the panel and click "Add to panel...", select "notification area", and click "Add".

---

