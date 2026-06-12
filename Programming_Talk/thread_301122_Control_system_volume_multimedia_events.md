---
title: "Control system volume/ multimedia events?"
date: 2006-11-16
forum: Programming Talk
---

### Post by almahtar on 2006-11-16
I am trying to write a script that will turn up/down your system volume, mute, etc.  Anyone know if there are libraries/shell commands to do this?  I can use "dcop" to control the volume of Amarok or tell it to skip forward, etc, but I need something for the actual system volume.

As an added bonus, if anyone can tell me how to send more generic "multimedia commands" (like what would happen if you pressed a multimedia key like "next" on a multimedia keyboard), I'll mail you a cookie.  I make great cookies.  

I've recently gotten a lot better at working with infrared devices in Linux, and I'd like to create a little GUI program with which people can easily program their remotes.  The existing programs out there really didn't come through for me to get my stuff working, so I figure they could use some healthy competition.

---

### Post by engineer on 2006-11-16
i guess you're using alsa. you could change the mixer setttings simply by calling 'amixer' with the parameters you want.

the man page (call 'man amixer') shows you all settings.

---

### Post by almahtar on 2006-11-17
Thank you! That'll help a lot.  Do you know if there's a way to figure out if a system is using alsa, jack, esd, arts, etc?

---

