---
title: "HOW TO: Fully functional Toshiba A215-S7422 in Hardy 8.04"
date: 2008-08-13
forum: Outdated Tutorials &amp; Tips
---

### Post by etchnstketch on 2008-08-13
First of all I am relatively new to linux and Ubuntu, but I've manage to get my laptop up and running with the help of these forums. I have compiled a list of what I did here in case anyone else may find this useful.

List of problems I had:

1. Graphics card driver not loaded
2. Wireless not functional
3. Suspend freezes after fixing wireless

1. Easiest to solve. Go to Menu > System > Administration > Hardware Drivers
Tick the enable check box and it will automate the installation process. 

[optional] 
Menu > Add/Remove : search for "ATI Catalyst Control Center" and install it. Make sure the show drop down has "all available" selected.

Menu > System > Administration > Update Manager to get the updates afterwards

2. There is already a terrific step by step guide here: 
[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

3. This one I hacked together myself, so I'm sure there is plenty of room for improvement, but it gets the job done. This assumes you followed step 2 and have your wifi files in the directory /wifi/ otherwise replace all instances of /wifi/ below with where ever you put the wifi files from step 2.

open a terminal

```
sudo gedit /etc/pm/sleep.d/01_wifi
```

paste this in and save the file.

```
#!/bin/bash
case $1 in
    hibernate)
        /wifi/wlan0down
        ;;
    suspend)
        /wifi/wlan0down
        ;;
    thaw)
        /wifi/wlan0up
        ;;
    resume)
        /wifi/wlan0up
        ;;
    *)  echo "Something is wrong."
        ;;
esac
```

then make it executable

```
sudo chmod +x /etc/pm/sleep.d/01_wifi 
```

That should do it. This hook calls wlan0down before the system suspends and then calls wlan0up after the system resumes.

That's all I have so far.

---

