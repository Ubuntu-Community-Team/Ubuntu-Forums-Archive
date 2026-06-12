---
title: "Compiz keeps crashing"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by upsla on 2012-07-21
Hi
I am using Ubuntu 12.04 along with windows 7. Recently Compiz  has started to crash very frequently. Usually a error dialog pops up saying 'Compiz has stopped working unexpectedly' with options to close or re launch.  Choosing Re launch option leads to different suggestions like submitting error to Ubuntu forums or ask Ubuntu etc etc. Please note I am novice user. So kindly suggest help as simple as possible.

---

### Post by Kopkins on 2012-07-21
> **upsla said:**
> Hi
I am using Ubuntu 12.04 along with windows 7. Recently compiz  has started to crash very frequently. Usually a error dialog pops up saying 'compiz has stopped working unexpectedly' with options to close or re launch.  Choosing Re launch option leads to different suggestions like submitting error to ubuntu forums or ask Ubuntu etc etc. please note I am novice user. So kindly suggest help as simple as possible.

Are you doing anything specific at the time of the crashes? For example, are you always switching workspaces or some other compiz related function when you get a crash?

Kopkins

---

### Post by ranger1021994 on 2012-07-21
> **upsla said:**
> Hi
I am using Ubuntu 12.04 along with windows 7. Recently compiz  has started to crash very frequently. Usually a error dialog pops up saying 'compiz has stopped working unexpectedly' with options to close or re launch.  Choosing Re launch option leads to different suggestions like submitting error to ubuntu forums or ask Ubuntu etc etc. please note I am novice user. So kindly suggest help as simple as possible.

As Kopkins said..watch out for actions causing compiz to shut down
Disable the conflicting plugin and compiz wont restart :)
>>If that doesnt help them update your video drivers.. :)

---

### Post by upsla on 2012-07-23
To my knowledge it happens when I watch videos over the Internet.

---

### Post by upsla on 2012-07-23
How to watch out for the plugins?. How do I know which plugins cause problems ?. Please do explain explain about that.

---

### Post by NikTh on 2012-07-23
Hi , 

if you want , you can delete ALL your configuration files . 

First do a backup 
```
gconftool --shutdown
killall -r -I gconf
killall -r -I dconf
tar czf confbackup.tar.gz .compiz* .gconf* .config/dconf/ .config/compiz*
```Then copy-paste this command (from here to your terminal) 
```

rm -rf .compiz* .gconf* .config/dconf/ .config/compiz*
```Reboot your system to see if everything its ok now.



**In case**  you cannot login or some other problem(relative to compiz or Desktop Environment)  

you can restore your previous settings like this
```
gconftool --shutdown
killall -r -I gconf
killall -r -I dconf
rm -rf .compiz* .gconf* .config/dconf/ .config/compiz*
tar xzvf confbackup.tar.gz
```

THanks

---

