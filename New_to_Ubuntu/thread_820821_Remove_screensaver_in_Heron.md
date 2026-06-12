---
title: "Remove screensaver in Heron?"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by ofb on 2008-06-06
I don't want a screensaver, so I don't want the daemon running.

I tried the first two steps of this post to get rid of the daemon,
[http://ubuntuforums.org/showpost.php?p=1630034&postcount=5](http://ubuntuforums.org/showpost.php?p=1630034&postcount=5)

```

sudo killall gnome-screensaver
gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false

```

That got rid of the daemon, but then I had an active blank screensaver after ten minutes. Here's my settings:

 - Screensaver preferences: Blank screen, Regard computer as idle after 10 minutes, Activate Screensaver checkbox is not checked.

 - Power management: put display to sleep at 59 minutes.

Rather than use the "less elegant" third step from the post above, I removed gnome-screensaver via Synaptic. Still got a blanked screen after ten minutes.

Searched Synaptic for 'screensaver', and found I don't have xscreensaver or kscreensaver installed either. Okay... so what's going on then?

For the moment I've replaced gnome-screensaver. In lieu of achieving removal, how do I reverse the above command so I can at least stop this ten minute activiation? Just change "false" to "true"?

---

### Post by sam_delta on 2008-06-06
check out under power management, i know you already looked at it, but there are two tabs, one for when you are on AC and other tab for when you are in battery power, you changed to 59 mins on both tabs, ac and battery power ?. 

its worth looking, just my 2 cents

sam

---

### Post by ofb on 2008-06-06
Hi Sam. Both of my Heron machines have only AC Power tabs, no battery.

---

### Post by NilsE on 2008-06-06
For the time being set the screensaver idle time in screensaver preferences to 2 hours.  At least it won't happen as often. That will also confirm it is screensaver doing the 10 minute timeout.

Also as suggested look at all the idle settings in gnome-power manager in the configuration tool and see if any of those help.

---

### Post by ofb on 2008-06-06
Set to 2 hours, and still blanks in 10. Presume that's because this line has disabled the interface?
```
gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false
```

Config Editor > apps > gnome-power-manager > etc doesn't appear to have anything causing the 10 minutes.

I'm thinking the line above has diabled the interface but not the screensaver, and without the interface it defaulted to On and 10 minutes.

I'm rather confused that removing gnome-screensaver in Synaptic doesn't get rid of screensaver either. It's only the interface then? How would I actually get rid of screensaver?

---

### Post by NilsE on 2008-06-06
> **ofb said:**
> Set to 2 hours, and still blanks in 10. Presume that's because this line has disabled the interface?
```
gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false
```

Config Editor > apps > gnome-power-manager > etc doesn't appear to have anything causing the 10 minutes.

I'm thinking the line above has diabled the interface but not the screensaver, and without the interface it defaulted to On and 10 minutes.

I'm rather confused that removing gnome-screensaver in Synaptic doesn't get rid of screensaver either. It's only the interface then? How would I actually get rid of screensaver?
You could try changing the line from false to true and run it to see if it changes the behavior.

---

### Post by ofb on 2008-06-06
I used the Config Editor to do it. It included the useful advice "Set to True to run the screensaver at login", so logout/login and we're back to normal: no screensaver activated, but a useless gnome-screensaver daemon running.

Remove gnome-screensaver via Synaptic, logout/login, and the screen blanks at ten minutes.

So back on track: How does one remove screensaver from Heron?

---

