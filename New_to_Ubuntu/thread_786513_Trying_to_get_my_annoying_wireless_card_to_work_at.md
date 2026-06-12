---
title: "Trying to get my annoying wireless card to work at boot, please help"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Darkendes on 2008-05-08
It took me forever to figure out how to get my laptop's Atheros wireless card to even work at all with Hardy. None of the methods I found would work with my Toshiba, but I finally got it running with ndiswrapper after running through a bunch of different XP drivers for it.

Only problem is, every time I switch between Windows and Ubuntu, I have to use the command line to get it to work again. I've tried looking for a bootup answer (tried rc.local and using Sessions > Start Up) to no avail. These are the commands that need to be entered in the console before my card will connect to an access point:

```
sudo modprobe ndiswrapper
sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether 001F3A8Exxxx [my MAC address]
```

I tried to make a script to run at boot, I've even tried putting the commands into /etc/network/interfaces, I just don't think I know what I'm doing.

The script I have:```
# /bin/sh


`modprobe ndiswrapper`
`/sbin/ifconfig wlan0 down`
`/sbin/ifconfig wlan0 hw ether 001F3A8Exxxx` [MAC address edited out]
```

The script doesn't work, even when I try to run it myself with sudo.

I really hate having to copy and paste those commands everytime I shutdown/reboot/suspend. Is there anywhere I can put these commands to get this to work at boot automatically? I'm sure it's something I'm doing wrong with the script, but I can't get it figured out. It's starting to drive me nuts. =\

I still have a lot to learn...

---

### Post by billgoldberg on 2008-05-08
> **Darkendes said:**
> It took me forever to figure out how to get my laptop's Atheros wireless card to even work at all with Hardy. None of the methods I found would work with my Toshiba, but I finally got it running with ndiswrapper after running through a bunch of different XP drivers for it.

Only problem is, every time I switch between Windows and Ubuntu, I have to use the command line to get it to work again. I've tried looking for a bootup answer (tried rc.local and using Sessions > Start Up) to no avail. These are the commands that need to be entered in the console before my card will connect to an access point:

```
sudo modprobe ndiswrapper
sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether 001F3A8Exxxx [my MAC address]
```

I tried to make a script to run at boot, I've even tried putting the commands into /etc/network/interfaces, I just don't think I know what I'm doing.

The script I have:```
# /bin/sh


`modprobe ndiswrapper`
`/sbin/ifconfig wlan0 down`
`/sbin/ifconfig wlan0 down [MAC address edited out]
```

The script doesn't work, even when I try to run it myself with sudo.

I really hate having to copy and paste those commands everytime I shutdown/reboot/suspend. Is there anywhere I can put these commands to get this to work at boot automatically? I'm sure it's something I'm doing wrong with the script, but I can't get it figured out. It's starting to drive me nuts. =\

I still have a lot to learn...

Have you tried adding:

```
modprobe ndiswrapper & /sbin/ifconfig wlan0 down & /sbin/ifconfig wlan0 down
```

as command in "sessions"

I don't think it will work, but it can't hurt to try.

I don't have any experience with scripting. But if you get the script working, I would image that adding the script to "sessions" would to the trick.

---

### Post by joselin on 2008-05-08
Or just add ndiswrapper to /etc/modules. This will start ndiswrapper module at boot.

Regards

---

### Post by Darkendes on 2008-05-08
> **billgoldberg said:**
> Have you tried adding:

```
modprobe ndiswrapper & /sbin/ifconfig wlan0 down & /sbin/ifconfig wlan0 down
```

as command in "sessions"

I don't think it will work, but it can't hurt to try.

I don't have any experience with scripting. But if you get the script working, I would image that adding the script to "sessions" would to the trick.

I tried this, and it still didn't work. Is it something with the "ifconfig" command itself maybe? It has to work outside of the console somehow...

> **joselin said:**
> Or just add ndiswrapper to /etc/modules. This will start ndiswrapper module at boot.

Regards

Thanks. One down, two commands to go. =)

I never thought it would be this hard to get such a simple thing to run at startup.

---

