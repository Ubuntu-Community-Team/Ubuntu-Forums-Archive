---
title: "Weather indicator, refreshing"
date: 2012-07-29
forum: New to Ubuntu
---

### Post by rosswmcgee on 2012-07-29
The weather indicator is non stop refreshing, I tried every thing but it

is the same temperature 24hrs. a day. Never changes or stops refreshing.

I removed and re-installed it. Same problem.

---

### Post by Frogs Hair on 2012-07-29
See this post.  [http://ubuntuforums.org/showthread.php?t=2017577](http://ubuntuforums.org/showthread.php?t=2017577)

---

### Post by rosswmcgee on 2012-07-29
Hey thanks Frogs Hair. Installed and works greeat. Done with the weather indicator that
came with 12.04.. Now I my-weather-indicator won't load.

---

### Post by Frogs Hair on 2012-07-29
Under preferences > general options there is an auto start setting . If it is not enabled the indicator won't start after logout or next boot .

---

### Post by rosswmcgee on 2012-07-29
I cannot get the icon to open so that I could get to preferences. I have removed and re-installed still will not go.

When I was setting up in preferences and selected the option location is  when it crashed. 

If I knew how to get every file connected with this ppa app then I could re- install but hard to find everything, even

synaptic does not clear it completely.

Here is the problem this is what caused it. Crashes if set to auto location: how to do this fix???

Workaround: Delete ~/.config/my-weather-indicator/my-weather-indicator.conf, re-launch the app, manually set location.

---

### Post by Frogs Hair on 2012-07-29
I had not read your pm before I wrote my previous post. I trust you got my reply .

---

### Post by rosswmcgee on 2012-07-29
yes perhaps you can help here is the bug link

[https://bugs.launchpad.net/my-weather-indicator/+bug/1030648](https://bugs.launchpad.net/my-weather-indicator/+bug/1030648)


finally found the file deleted it, launches fine now. Problem solved.


This is a nice program but when you set the preference location do so manually. If you do not the program will crash

and not launch.

---

### Post by rosswmcgee on 2012-08-02
Frogs Hair! Well the my-weather-indicator crashed again. I would like to delete everything and re-install. However, I get this msg. in terminal and cannot seem to entirely wipe the computer of the program. 

 Unable to locate package _usr_share_my-weather-indicator
using the following command

sudo apt-get remove <package_name>

---

