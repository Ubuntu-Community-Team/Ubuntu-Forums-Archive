---
title: "bad sound control"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by c4jjm on 2008-10-27
I have an acer aspire 6920 notebook, when I first installed ubuntu, i had no sound at all. after about an hour, I got sound....but now i don't have a volume control. It basically made the sound set to max, unchangeable, (pandora volume works) just not the system volume. Also, Skype doesn't work, also comes up with not finding volume control

This is the message I receive when I click on volume control;

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured."

I'm not sure if I should just remove all sound components then reconfigure. if any one has a suggestion please let me know.

---

### Post by billgoldberg on 2008-10-27
Remove pulse audio using synaptic.

Then in system -> preferences -> sound select ALSA for everything.

Install "gnome-alsamixer" and use that to configure your sound preferences.

Should you not have the right card selected, install asoundconf-gtk and use that to select the card.

---

### Post by c4jjm on 2008-10-27
I tried that approach but when I open alsa mixer and select Edit > sound card properties .... it just disappears. The last thing I couldn't find it after installation.


new error:

No volume control GStreamer plugins and/or devices found.

---

