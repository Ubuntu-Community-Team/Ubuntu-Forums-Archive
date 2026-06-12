---
title: "conky weatherget not found"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by E87 on 2008-11-12
hi, i just installed conky this week, and its working great after countless forums for conkyrc. i just got my pop3 email working, so the last thing i need is weatherget to work. any suggestions are welcome :)
heres what im looking @

weatherget:not found

```
|  ${color} Weather: ${execo 1800 weatherget -f /home/edwin/weather.sh 33511 |
```

---

### Post by m_duck on 2008-11-12
You need to install weatherget. Presumably the script you are using in /home/edwin/weather.sh is calling weatherget to get the weather information, but as it isn't installed, gives you the error.

To install weatherget, go [here]("http://developer.berlios.de/project/showfiles.php?group_id=7174&release_id=12648") and click the top package, then "Download" on the next page. Once that has downloaded, locate it, right click it and click "Extract Here". Open up a terminal window and "cd" to the folding that has just been unzipped. So for example, if you downloaded the tar.bz2 file to your desktop, type:
```
cd ~/Desktop/weatherget-0.4.0.1
```
(depending on the name of the folder).

From the readme contained in this folder, just type:
```
sudo python setup.py install
```
and press enter, then enter your password and press enter again. This should install weatherget for you and hopefully your conky script should work.

---

