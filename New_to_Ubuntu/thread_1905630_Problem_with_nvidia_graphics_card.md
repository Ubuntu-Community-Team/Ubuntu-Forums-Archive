---
title: "Problem with nvidia graphics card"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by CalFs on 2012-01-07
New to ubuntu.

Opened up menu of programs that open on startup. There were two -- startup noise and nvidia settings. Opened the nvidia settings and it said that I needed to run nvidia xconfig in the terminal and then reset. Ran it in terminal, but the same message appeared every time I opened nvidia settings.

When I closed my notebook over the system didn't turn off and the screen was subsequently blank, ended up having to hold the power button.

When I then turned it on, ubuntu wouldn't run normally. It is dual boot, so from grub I launch ubuntu 3.0.0-14-generic. It then launches a screen saying modem manager for various things and starts various things -- one of which fails: 'automatic crash report generation'. Can't do anything from here, but when I press power button (not holding it) it continues where 'checking for running unattended upgrades' -- 'terminating programs' fails and the computer shuts down.

Starting it in recovery mode I was able to get to command line input.

Not sure what I need to do from here, but guess its to do with graphics card.

Your help would be greatly appreciated

Calum.

---

### Post by 2F4U on 2012-01-07
Did it work before you installed the nVidia drivers? If yes, I would remove the nVidia drivers and use the open source drivers. The problem with those drivers is that they are not open source and so only nVidia is able to change them, which can take a long time.

---

### Post by Basher101 on 2012-01-07
> **2F4U said:**
> Did it work before you installed the nVidia drivers? If yes, I would remove the nVidia drivers and use the open source drivers. The problem with those drivers is that they are not open source and so only nVidia is able to change them, which can take a long time.

probably

if you do not know how to uninstall them in recovery mode, simply make a fresh reinstall, it should be faster to get all your settings and programs again instead of fiddling around with the drivers for hours..

---

### Post by CalFs on 2012-01-07
It was working fine .. I assumed I was already using the nvidia driver. Perhaps I changed it.

Do you know what I did when I ran 'nvidia xconfig' in terminal?

---

