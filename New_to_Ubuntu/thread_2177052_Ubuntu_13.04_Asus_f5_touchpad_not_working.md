---
title: "Ubuntu 13.04 Asus f5 touchpad not working"
date: 2013-09-27
forum: New to Ubuntu
---

### Post by jonesbri on 2013-09-27
Hello
 I have a asus F5, the touchpad is not working correctly on a recently 13.04 install. It was working on version 12.04. I enter the following command in terminal sudo modprobe -r psmouse && sudo modprobe psmouse proto=imps  and touchpad works. The problem is when I reboot I have to open terminal and enter the command again, this is not very practical. I have tried opening startup application and pasteing the same command in the additional startup program proceedure that is provided for you, this does not work. I have also tried entering the following command in the additional startup application proceedure . Etc/rc.local/modprobe -r psmouse && etc/rc.local modprobe psmouse. With no joy can anyone help  please.

---

### Post by andreazzz on 2013-09-27
What exactly does not work? Are you able to use the touchpad as cursor and is tapping and scrolling disabled?
[this](http://www.upubuntu.com/2011/11/is-your-laptop-touchpad-not-working.html) might work for you.

Good luck!

---

### Post by jonesbri on 2013-09-27
dconf

---

### Post by jonesbri on 2013-09-27
Hello
Dconf editor does not seem to work. Their is a blank screen next to org and the rest of the items . The touch pad is erratic, tapping and scrolling is disabled.
Regards.

---

### Post by andreazzz on 2013-09-29
Are you sure you cannot alter the settings in "System > Preferences > Mouse > Touchpad" ? Make sure to uncheck 'Disable touchpad while typing' and 'Enable mouse clicks with touchpad'.

---

### Post by jonesbri on 2013-09-29
Hello.
Their does not seem to be any system preferences in ubuntu 13.04. Only system settings, and in this under under touchpad are limited touchpad changes.
Regards

---

### Post by andreazzz on 2013-09-30
Paste this command in a terminal:
```

synclient TapButton1=1

```

On some systems/distro's it might be reset after a reboot. Let me know and I supply you with more info;)

More info:  [http://handytutorial.com/disableenable-touchpad-in-ubuntu-13-04-12-10/](http://handytutorial.com/disableenable-touchpad-in-ubuntu-13-04-12-10/)

---

### Post by jonesbri on 2013-09-30
hello 
I have tried the command and I get the followin message. Couldn't find synaptics properties. No synaptics driver loaded?.

---

### Post by andreazzz on 2013-10-01
In that case, paste this in terminal first to install synaptic.

```

sudo apt-get install synaptic

```

---

### Post by jonesbri on 2013-10-01
Hello
I entered the synoptics command. It looked like it loaded o.k. I then entered the command you asked and i still get the following statement.Couldn't find synaptics properties. No synaptics driver loaded?

An update. I have just loaded some updates to the system and now everything seems to be working. I would like to thank you for your help and patience.
Kind regards

---

