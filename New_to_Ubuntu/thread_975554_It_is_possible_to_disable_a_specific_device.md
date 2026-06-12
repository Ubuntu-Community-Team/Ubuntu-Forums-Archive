---
title: "It is possible to disable a specific device?"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Kosimo on 2008-11-08
There is any way to disable some specific device?
I want to disable my bluetooth as I'm not using it at all, and when using powertop it warms me that bluetooth it is waking up my system 100% of the time... And I can't suspend it.  Any idea?
Thank you

---

### Post by sdennie on 2008-11-08
In this particular case (bluetooth), you can likely disable it in BIOS.  If not, you can blacklist the bluetooth kernel module or remove it while on battery power (which is what I do).  To blacklist it, you should be able to add the following to /etc/modprobe.d/blacklist:

```

blacklist bluetooth

```

To remove it dynamically when the machine is unplugged, create a script called 99-bluetooth:

```

#!/bin/bash

if on_ac_power; then
  modprobe bluetooth
  modprobe l2cap
  modprobe rfcomm
  modprobe hci_usb

  /etc/init.d/bluetooth start
else
  /etc/init.d/bluetooth stop
  
  modprobe -r hci_usb
  modprobe -r rfcomm
  modprobe -r l2cap
  modprobe -r bluetooth
fi

```

And install it with:

```

sudo install 99-bluetooth /etc/pm/sleep.d
sudo install 99-bluetooth /etc/pm/power.d

```

(All of that was written untested but, that is the general idea).

---

### Post by Kosimo on 2008-11-08
> **vor said:**
> In this particular case (bluetooth), you can likely disable it in BIOS.  If not, you can blacklist the bluetooth kernel module or remove it while on battery power (which is what I do).  To blacklist it, you should be able to add the following to /etc/modprobe.d/blacklist:

```

blacklist bluetooth

```

To remove it dynamically when the machine is unplugged, create a script called 99-bluetooth:

```

#!/bin/bash

if on_ac_power; then
  modprobe bluetooth
  modprobe l2cap
  modprobe rfcomm
  modprobe hci_usb

  /etc/init.d/bluetooth start
else
  /etc/init.d/bluetooth stop
  
  modprobe -r hci_usb
  modprobe -r rfcomm
  modprobe -r l2cap
  modprobe -r bluetooth
fi

```

And install it with:

```

sudo install 99-bluetooth /etc/pm/sleep.d
sudo install 99-bluetooth /etc/pm/power.d

```

(All of that was written untested but, that is the general idea).

Wow, thanks for the answer. It is perfect, exactly what I was looking for. I'll test it right now.

Thank you

---

### Post by Paqman on 2008-11-08
There's an even easier solution. Go to System > Prefs > Sessions and you'll see a list of what services are running. Uncheck Bluetooth.

---

### Post by sdennie on 2008-11-08
> **Paqman said:**
> There's an even easier solution. Go to System > Prefs > Sessions and you'll see a list of what services are running. Uncheck Bluetooth.

That will disable the bluetooth service but, I believe it will leave the modules loaded.  That in turn will mean the bluetooth radio is on and you will still be using power for it.

---

### Post by Kosimo on 2008-11-08
Ok, bluetooth is now in blacklist..
But when running powertop I'm still having a wired message

[IMG]http://kosimo.googlepages.com/powertop.png[/IMG]

Hmmm... How can I know if that device that is waking up my system is bluetooth?

Another strange thing is that even if I hit U, in order to enable USB suspend, it doesn't work and it always suggest me to hit U without any effect.   

Any idea?

Thank you

---

### Post by sdennie on 2008-11-08
> **Kosimo said:**
> Ok, bluetooth is now in blacklist..
But when running powertop I'm still having a wired message

[IMG]http://kosimo.googlepages.com/powertop.png[/IMG]

Hmmm... How can I know if that device that is waking up my system is bluetooth?

Another strange thing is that even if I hit U, in order to enable USB suspend, it doesn't work and it always suggest me to hit U without any effect.   

Any idea?

Thank you

That doesn't look like bluetooth is waking up the system (just the keyboard/mouse in this case).  As for the USB thing, powertop is exceedingly useful but not without bugs.  It regularly reports inaccurate things for me.

It sounds like you are interested in power savings so I'll point you to: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773").  Likely not specific to your laptop but, it contains good information and links for general power savings information.

---

### Post by Kosimo on 2008-11-08
> **vor said:**
> That doesn't look like bluetooth is waking up the system (just the keyboard/mouse in this case).  As for the USB thing, powertop is exceedingly useful but not without bugs.  It regularly reports inaccurate things for me.

It sounds like you are interested in power savings so I'll point you to: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773").  Likely not specific to your laptop but, it contains good information and links for general power savings information.

Yes I'm trying to reduce the power consumption as much as I can :)
I'll check that link right now.
Thank you

---

