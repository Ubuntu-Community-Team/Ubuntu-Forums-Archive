---
title: "SanDisk Connect Wireless Media Drive not connecting"
date: 2013-12-23
forum: New to Ubuntu
---

### Post by paulwillliamkoehn on 2013-12-23
thank you for reading this

I received a [COLOR=#000000][FONT=verdana]SanDisk Connect Wireless Media Drive from a contest online and would like to connect it to my laptop/desktops.

I tried to install the .exe version of the wmd from [/FONT][/COLOR][http://www.sandisk.com/products/software/media-manager/](http://www.sandisk.com/products/software/media-manager/)[COLOR=#000000][FONT=verdana]  through wine but kept getting a 'sandbox' error

I have spent the last 4 hours researching it and have come up with nothing

Does anyone have a clue what i can do to get the drive working?

i am using Ubuntu 12.04 LTS

Thank You!

(btw, i am a semi-beginner, i know basics, but not much beyond that...)[/FONT][/COLOR]

---

### Post by sanderj on 2013-12-23
Can you describe what the device should do? Is it like this:

Connect it to a PC via USB to put content on it.
Then disconnect it and use a mobile device to view the content on the device.

Right?

If so: on Ubuntu open a terminal, then type "lsusb". Then connect the device via USB to your Ubuntu system and type "lsusb" again. There must be one line extra. Copy that into this thread and google it.

---

### Post by paulwillliamkoehn on 2013-12-23
when i do that i get:
paul@Computer:~$ lsusb
Bus 002 Device 002: ID 064e:a219 Suyin Corp. 1.3M WebCam (notebook emachines E730, Acer sub-brand)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
paul@Computer:~$ lsusb
Bus 001 Device 002: ID 0781:7600 SanDisk Corp. 
Bus 002 Device 002: ID 064e:a219 Suyin Corp. 1.3M WebCam (notebook emachines E730, Acer sub-brand)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

when i search the line that is different i get [FONT=arial]Your search - [/FONT][FONT=arial]**Bus 001 Device 002: ID 0781:7600 SanDisk Corp.**[/FONT][FONT=arial] - did not match any documents.[/FONT]

---

### Post by paulwillliamkoehn on 2013-12-23
i got the connection to usb working with this post(the only linux post i could find:
[http://www.blairkennedy.com/node/207](http://www.blairkennedy.com/node/207)
want the wireless working now..

---

### Post by paulwillliamkoehn on 2013-12-23
> **sanderj said:**
> Can you describe what the device should do? Is it like this:

Connect it to a PC via USB to put content on it.
Then disconnect it and use a mobile device to view the content on the device.

Right?

If so: on Ubuntu open a terminal, then type "lsusb". Then connect the device via USB to your Ubuntu system and type "lsusb" again. There must be one line extra. Copy that into this thread and google it.

forgot you asked, the answer is yes to "Can you describe what the device should do? Is it like this:

Connect it to a PC via USB to put content on it.
Then disconnect it and use a mobile device to view the content on the device."

---

### Post by sanderj on 2013-12-23
Based on the info [http://www.sandisk.com/products/wireless/media-drive/](http://www.sandisk.com/products/wireless/media-drive/) I think the device is only meant to watch content on mobile devices, and only after installing the  special app on it. Maybe you can check that with your mobile device?

BUT ... as the content watching works via Wifi, maybe you can do some reverse engineering against the SanDisk Connect Wireless Media Drive? Use nmap to scan for open ports? Maybe it's just DLNA?

---

### Post by paulwillliamkoehn on 2013-12-23
you do know this is the beginners section- right? i have no idea what '[COLOR=#000000]Use nmap to scan for open ports? Maybe it's just DLNA?' is
and my original question was how to install the app. i posted both links to desktop and the other one with android and ipad..[/COLOR]

---

### Post by sanderj on 2013-12-23
> **paulwillliamkoehn said:**
> you do know this is the beginners section- right? i have no idea what '[COLOR=#000000]Use nmap to scan for open ports? Maybe it's just DLNA?' is
and my original question was how to install the app. i posted both links to desktop and the other one with android and ipad..[/COLOR]

Ah, OK. Well, my advice to a beginner: don't expect Windows software to run on Linux, certainly not if it has to do with hardware and/or encryption.

---

### Post by paulwillliamkoehn on 2013-12-25
I was not "expecting it" to connect right away, but i figured with the features it has that someone had got it working with ubuntu by now..
Maybe a suggestion of steps to take.. or a repository that will have an effect.
i am posting here because everyone does not speak 'technical jargon'

---

### Post by paulwillliamkoehn on 2013-12-25
would this work?
[http://www.itsplayingapp.com/helperapp.html](http://www.itsplayingapp.com/helperapp.html)
and if so, in "for dummies" language, how do i install the .jar (i take it i need java and repository for it)

(i know enough to use terminal and paste commands)

---

