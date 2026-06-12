---
title: "[SOLVED] synaptic package manager startup"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by leafy on 2008-10-10
Hi,
I've been using Xubuntu for a few days now. I was messing with Synaptic Package Manager; but from now it keeps launching everytime when I log into my account with a dialog box saying it doesn't have admin priviledges.
How can I stop it from showing up everytime?
Thanks.

---

### Post by adam_kimber on 2008-10-10
Have a look at Sessions. Its under System --> Administration IIRC. 

You probably logged out with it open and Gnome tends to save the current layout on log out. 

As for the popup Synaptic requires admin privilages to run and thus its complaint. :D

---

### Post by leafy on 2008-10-10
That didn't do the trick... The items are arranged in different order in xubuntu, nevertheless I disabled the "save session.." and restarted but I still have it pop up :(

---

### Post by adam_kimber on 2008-10-11
If you have a Sessions Preferences dialog like this one. Check for synaptic in the Startup programs, and when its running check in the second tab, Current Session for synaptic and change its style to normal. Thirdly close synaptic and click "save current session in final tab Session Options. 

If this does not work, I am a little stumped as unfortunately I do not use Xubuntu :( But you could try moving / deleting xfce-session* files in ~/.cache/sessions/

---

### Post by SunnyRabbiera on 2008-10-11
> **adam_kimber said:**
> If you have a Sessions Preferences dialog like this one. Check for synaptic in the Startup programs, and when its running check in the second tab, Current Session for synaptic and change its style to normal. Thirdly close synaptic and click "save current session in final tab Session Options. 

If this does not work, I am a little stumped as unfortunately I do not use Xubuntu :( But you could try moving / deleting xfce-session* files in ~/.cache/sessions/

he said he is using xubuntu, not ubuntu.

---

### Post by adam_kimber on 2008-10-11
> **SunnyRabbiera said:**
> he said he is using xubuntu, not ubuntu.

> **adam_kimber said:**
> If this does not work, I am a little stumped as unfortunately I do not use Xubuntu :( But you could try moving / deleting xfce-session* files in ~/.cache/sessions/

I was unsure of how much overlaps...... But I did add this bit which apparently is xfce related.

---

### Post by leafy on 2008-10-11
Finally I got it fixed...
I checked the xfce-sessions; and the "save session.." was also disabled. However in the applications > settings > settings manager >> "autostarted applications"; I saw that one of the startup applications was update-notifier.

It turned out to be update-notifier having "show notifications" enabled which caused it to popup everytime.When I disabled it the synaptic stopped showing up.*phew*
Thanks for your support ^_^

---

