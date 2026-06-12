---
title: "scrambled screen b4 logging"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by aravind4j on 2012-04-30
[LEFT][B][FONT="Comic Sans MS"]i'm fairly new to kubuntu but i've installed too many updates without fully understanding their concepts so i don't know which update caused the following error

Hence i'm faced with a scrambled screen b4 the logging in i.e loading screen (the log in screen has no problems) and after i log into the computer a KDE daemon update notification appears showing a black space in the middle of computer

Though i can close it , its pretty much annoying to see it every time i log in !!

Need HELP:confused: !![/FONT][/B][/LEFT]

---

### Post by jtarin on 2012-04-30
The black strip is an issue with bad data in the update notifier:

[http://www.kubuntuforums.net/showthread.php?58340-Yellow-light-bulb-icon-Bug-](http://www.kubuntuforums.net/showthread.php?58340-Yellow-light-bulb-icon-Bug-)
light&p=295264&viewfull=1#post295264


To clear it:

```
sudo rm /var/lib/update-notifier/user.d/data-downloads-failed
sudo rm /var/lib/update-notifier/user.d/data-downloads-failed-permanently
```

---

### Post by aravind4j on 2012-12-21
Thank you !! i'm using ubuntu now but solved that issue :P

---

