---
title: "Laptop doesn't suspend by closign lid"
date: 2011-09-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ISagalaev on 2011-09-22
Hello everyone,

I'm trying to find out if this is just me… My Envy 14 laptop doesn't suspend by closing lid. Choosing Suspend from the settings menu (the thing in the upper-right corner) does work and opening lid does wake the machine up if suspended this way. The problem didn't manifest itself right after the upgrade to 11.10 beta but appeared after some subsequent update.

I've filed a bug on it[1] but it seems to be ignored. I don't know what to do with it.

[1]: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/854404](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/854404)

---

### Post by cariboo on 2011-09-22
Click the power button in the top right corner and select System Settings->Power, an check what it is set to.

---

### Post by Quackers on 2011-09-22
Some time since beta1 my laptop does the same.
It is set to suspend on shutting the lid but it doesn't now.
If I try to suspend it manually the screen shuts down but the green power light stays on. And it won't wake up (or restart). It just sits there with no action at all. I have to power off.
I seem to remember the same thing on previous development releases shortly before the actual release. It's always worked in the final release up to now :-)

---

### Post by ISagalaev on 2011-09-22
All set to Suspend.

There was an update that killed suspend from UI too: there wasn't the Suspend item in the upper-right menu, nor Suspend choice in this dialog. Now they are back and I've fiddled with them back and forth and set to Suspend but it still doesn't work. 

Also, /var/log/pm-suspend.log is quiet on closing lid but /var/log/auth.log says soemthing about successfully acquiring root (which means that at leas *something* happens in the system). Do you have any idea where to look else?

---

### Post by ISagalaev on 2011-09-22
Quackers, I don't believe it happened by magic :-). Someone went ahead and filed bugs and someone yet fixed it. That's what I'm trying to do.

---

### Post by Quackers on 2011-09-22
You could be right :-)
Or it could be one of the last things to be fixed - maybe.

---

