---
title: "Lubuntu booted up into Ubuntu 12.04 commandline"
date: 2014-07-23
forum: New to Ubuntu
---

### Post by seal308 on 2014-07-23
Hi,

I have been using lubuntu for a few months. 
Then I stopped using it for a while then logged back on which was fine. 
Apparently there was a ton of updates so I pressed install. 
When I pressed shut down and tried to boot the next day instead of lubuntu it booted up into ubuntu command line.
I did have ubuntu 12.04 before but then I switched to lubuntu, before this crash I would see the GRUB menu and see both lubuntu and ubuntu but it would always automatically log into lubuntu.
Now there is no GRUB. When I boot is see the friendly blue lubuntu symbol and then it flickers to black and goes to the ubuntu 12.04 command line. 
I am able to log into the ubuntu command line but would like to get back to lubuntu. What should I do?

Thanks

---

### Post by Bucky Ball on 2014-07-23
A simple approach that might at least change the scenery would be to log out when you are in Ubuntu and change the session to Lubuntu at the login screen (should be in a pop up 'Sessions' list somewhere, depending on what login GUI you have). Log back in and reboot and see what happens. It should boot into the last used session, which would then be Lubuntu.

If it doesn't boot to Lubuntu or the command line that will give us some clue as to what might be amiss. :-k

---

### Post by seal308 on 2014-07-23
When I boot it doesn't auto log me in. 
It has my machine name login: 
When I log in it logs me into ubuntu.
I tried pressing "logout" but it sends be back to the same prompt mentioned

---

### Post by Bucky Ball on 2014-07-23
Ah. Try installing lightdm:

```
sudo apt-get install lightdm
```

Reboot and see if that gets you to a login screen with selectable sessions.

---

### Post by seal308 on 2014-07-23
Hi, 
This seems to have worked.
What is lightdm?

---

### Post by Bucky Ball on 2014-07-23
Open Synaptics Package Manager, have a search for it and it will give a description. 

> LightDM is _*a X display manager *_that:
 * Has a lightweight codebase
 * Is standards compliant (PAM, ConsoleKit, etc)
 * Has a well defined interface between the server and user interface
 * Cross-desktop (greeters can be written in any toolkit)

Is everything back to normal as far as booting and getting into Lubuntu goes?

---

### Post by seal308 on 2014-07-26
yes seems so, but there is no GRUB menu it goes straight to lubuntu

---

### Post by Bucky Ball on 2014-07-26
Hit shift at boot and that should get you to a list. If you want that list every boot:

```
sudo nano /etc/default/grub
```

... and the first four lines should look something like this:
```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

Once you've made any changes:

```
sudo update-grub
```

Good luck.

---

### Post by ibjsb4 on 2014-07-26
You realize Lubuntu 12.04 was not an LTS release and has reached end of life.

---

