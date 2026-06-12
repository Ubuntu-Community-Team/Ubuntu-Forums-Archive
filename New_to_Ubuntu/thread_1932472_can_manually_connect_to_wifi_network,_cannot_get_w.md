---
title: "can manually connect to wifi network, cannot get wireless network list to popup"
date: 2012-02-27
forum: New to Ubuntu
---

### Post by smkatz on 2012-02-27
Hi. I can connect to wireless networks manually, but unclear how to get the list of wireless networks to appear. When I insert my dongle, it says wireless networks are available but I click the popup and it doesn't show them. There must be a way to manually pop up that list but I don't know what it is. My dongle is made by netgear in case that matters.

--Sam

---

### Post by Ms. Daisy on 2012-02-28
Are you sure the available networks aren't simply hidden?

---

### Post by audiomick on 2012-02-28
> **smkatz said:**
> When I insert my dongle, it says wireless networks are available but I click the popup and it doesn't show them.

You mean the pop up thing that appears on the desktop a little bit below the top bar? That's not the way, as you have noticed. ;) 
Look for the network symbol at the top right of the screen and left click on that. The screen shot shows what it looks like on 10.04. I believe it is similar on 11.04 and 11.10, but I am not sure.

> 
My dongle is made by netgear in case that matters.

If you want to know exactly what it is, open a terminal whilst it is plugged in and do

```
lsusb
```

You can see mine, the Hauwei device.
```
mick@mick-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by smkatz on 2012-02-29
Hey Guys.

I'm running lubuntu in case that changes your instructions any. If you intended to attach a screenshot, please do.

--Sam

---

### Post by Ms. Daisy on 2012-02-29
Did you find the network applet and click on it?

edit: sorry- I failed to notice you're using Lubuntu.  I've got no idea what the desktop looks like in Lubuntu.

---

### Post by smkatz on 2012-02-29
Got it.   For the record, on lbuntu it is next to the clock, and right-clicking on it pops up the network list. Double clicking does nothing. And the pop up does say, "click this icon to connect to a wireless network" so it is slightly misleading.

Is there a way to turn off the pop up? Also, double clicking should ideally work, although I'm sorry for not thinking of right-clicking earlier. I did go into the network connections control panel, but that only works for manual connections, and works quite well.

--Sam

---

### Post by audiomick on 2012-02-29
> **smkatz said:**
> Hey Guys.
  If you intended to attach a screenshot, please do.

--Sam

Ooops, sorry. It was late at night ;)

I wont bother now, as you seem to have things sorted.

---

