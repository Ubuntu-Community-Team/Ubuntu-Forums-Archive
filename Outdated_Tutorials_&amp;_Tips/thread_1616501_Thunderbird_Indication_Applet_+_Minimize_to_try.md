---
title: "Thunderbird: Indication Applet + Minimize to try"
date: 2010-11-08
forum: Outdated Tutorials &amp; Tips
---

### Post by mr.interested on 2010-11-08
The best solution that I've found. Works for Thunderbird 3.1.6 in Ubuntu 10.10. New message arrives:

[IMG]http://img213.imageshack.us/img213/241/screenshotxl.png[/IMG]

A moment later, Ubuntu notifies about this:

[IMG]http://img193.imageshack.us/img193/4238/screenshot1bf.png[/IMG]

Thunderbird is in the notification applet:

[IMG]http://img560.imageshack.us/img560/8400/screenshot2y.png[/IMG]

OK, so here's what you need:


[LIST=1]
[*]Download [Indicators for Thunderbird]("https://addons.mozilla.org/en-US/thunderbird/addon/223374/") which integrates the software with Indicator Applet. Go to Thunderbird and install in Tools --> Add-ons.
[*]Install another extension called FireTray, just search for "firetray" in Tools --> Add-ons.
[*]Install libnotify-bin in Synaptic Manager.
[/LIST]
After that you need to "fix" two things:

4. Go to Tools --> Add-ons in Thunderbird, and go to preferences of the FireTray extention. Unselect "Show number of unread mail" as below, so that the tray will have Thunderbird's icon, instead of the original ugly icon with numbers--unless you like it.

[IMG]http://img600.imageshack.us/img600/1162/screenshot5z.png[/IMG]

5. Go to Edit --> Preferences in Thunderbird, and in "General" tab unselect "Show an alert". The alert will be show by Ubuntu instead (this is the libnotify-bin you installed).

Hope this helps.

---

### Post by Zookalicious on 2010-11-16
Hey fantastic guide! Very easy to follow and it's everything I needed all in one place. 

I have no clue why Thunderbird isn't the default mail app in Ubuntu. I just installed it and it's great, especially with these add ons.

The only thing I would add to this though is a way around Firefox (if that's what your using to download the add ons) trying to install the add on onto itself instead of saving them for use with Thunderbird.  I had to use another browser to save it to my drive. 

Thanks again for the walkthrough!

---

