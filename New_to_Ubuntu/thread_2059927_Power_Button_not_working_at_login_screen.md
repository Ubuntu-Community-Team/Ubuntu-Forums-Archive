---
title: "Power Button not working at login screen"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by fmueller01 on 2012-09-19
Hi there,

being quite new to Ubuntu I encountered the following  issue:

On Ubuntu 12.04.1 pressing the physical power button on the machine shuts down the pc. However, this only works if a user is logged in, i.e. there's no effect of power button presses at the login screen.

Is this the intended behavior? If yes, any way to make it shutdown at the login screen after power button press also?

Any hints are greatly appreciated. Thanks.

---

### Post by androssofer on 2012-09-19
> **fmueller01 said:**
> Hi there,

being quite new to Ubuntu I encountered the following  issue:

On Ubuntu 12.04.1 pressing the physical power button on the machine shuts down the pc. However, this only works if a user is logged in, i.e. there's no effect of power button presses at the login screen.

Is this the intended behavior? If yes, any way to make it shutdown at the login screen after power button press also?

Any hints are greatly appreciated. Thanks.

someone else posted something similar and got not answer.. :-(

they key would be the power settings.. and settings them for the login..

so if we could run 

```
gnome-control-center
```

on login, change the settings. it would probably work..

a similar technique was used to change the login screen background on old ubuntu versions. but now it uses a different login screen managed called 'lightdm'.  so the method doesnt work anymore..

---

### Post by fmueller01 on 2012-09-20
Okay, so looking into lightdm might be worthwhile. Thanks for the tip.

---

### Post by fmueller01 on 2012-09-20
A quick Google search led me to "http://mjg59.dreamwidth.org/2414.html", from there I get the impression that lightdm is completely separate from the desktop environment, i.e. any setting made concerning power management do not apply at the login screen (because no user session has been started yet).

So there seems to be no easy solution to this problem. That's disappointing, because my Ubuntu box runs headless and powering off with no login would be great.

Any suggestions for a workaround are greatly appreciated. Thanks.

---

### Post by androssofer on 2012-09-20
> **fmueller01 said:**
> 

So there seems to be no easy solution to this problem. That's disappointing, because my Ubuntu box runs headless and powering off with no login would be great.

Any suggestions for a workaround are greatly appreciated. Thanks.

is it ubuntu server? 

may i ask why you are trying to achieve this?

---

### Post by cogier on 2012-09-20
I looked into this and tried [Ctrl]+[Alt]+[Del] and that allows you to log out - but as you have already logged out it does nothing?!

I presume you are aware of the ability to shut down with the menu at the top right of the login screen.

---

### Post by fmueller01 on 2012-09-20
@androssofer
I'm running the standard desktop version of Ubuntu 12.04.1. However, because I use the machine only for smb shares, I have no need for keyboard, monitor etc, thus it runs headless. I opted for the desktop version because I find it convenient to have a full desktop environment if I need to do something else on the machine.


@cogier
Thanks for the suggestion, but because I'm logged out already that doesn't help. The power down icon works fine, but I need the machine to shut down by pressing the physical power button.

---

### Post by fmueller01 on 2012-09-20
Just found something that I'll try tomorrow:

"http://ubuntuforums.org/showthread.php?t=1669946&highlight=login+shutdown+power+button"

Similar issue, power button not working if screen is locked. They suggest adding a shutdown command to "/etc/acpi/powerbtn.sh".

---

### Post by fmueller01 on 2012-09-21
Ok, it worked. From what I understand the "/etc/acpi/powerbtn.sh" checks  if some daemon is managing powering down. If not it just initiates a  shutdown via:

# If all else failed, just initiate a plain shutdown.
/sbin/shutdown -h now "Power button pressed"

However,  the skript never seems to get to this place (after all, the machine  should shut down if it would), and instead seems to call one of the  daemon options in the if-then part.

By inserting "/sbin/shutdown -h now" before the if-then part this is avoided.

Doesn't seem very elegant to me, but it works.

Thanks for your help and suggestions.

---

### Post by lptr on 2012-10-09
> **fmueller01 said:**
> Ok, it worked. From what I understand the "/etc/acpi/powerbtn.sh" checks  if some daemon is managing powering down. If not it just initiates a  shutdown via:

# If all else failed, just initiate a plain shutdown.
/sbin/shutdown -h now "Power button pressed"

However,  the skript never seems to get to this place...
By inserting "/sbin/shutdown -h now" before the if-then part this is avoided.

Doesn't seem very elegant to me, but it works.


Usually this machine acts as smb server. But sometimes it is used as desktop, too. The users in the past (older Ubuntu version) were used to just pressing power to boot it up and when done they again pressing power to shutdown. Upper mentioned method worked here in this case, too. 

I am wondering if **dconf** could be tweaked to manipulate the 'system' similar to something likewise, that when a user is logged into system. This power-button behaviour can be modified with entry: gnome, settings-daemon, plugins, power and changing power-button from hibernate to shutdown.

Where to find the sources of this tool?

---

