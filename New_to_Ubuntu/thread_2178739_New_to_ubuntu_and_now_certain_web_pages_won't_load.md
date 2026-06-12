---
title: "New to ubuntu and now certain web pages won't load."
date: 2013-10-04
forum: New to Ubuntu
---

### Post by eric32 on 2013-10-04
So i just installed Ubuntu and a game my roommates plays straight off the internet will no longer load. With my lack of experience, I can't seem to figure out why not. It won't display an error, it just stops loading halfway through and the screen turns black. It loads other pages from the same website but simply stops when it comes to the log in for the game. The website is empire.goodgamestudios.com. 

When i access the browser console during the error it states this about the current page and i don't understand what it means, "--
[21:52:03.756] Use of getPreventDefault() is deprecated.  Use defaultPrevented instead. @ http://empire.goodgamestudios.com/"

If anyone can explain this to me or tell me what to adjust in order to get this website to load my roommate would greatly appreciate it and I would like to learn what the problem is for informational purposes.

Thanks everyone in advance,
Dr013lunt
Ubuntu 12.04 LTS

---

### Post by jewisharific on 2013-10-04
I can get to the site, but I don't have a login.  It appears to use flash, and loads for me in Chromium and Firefox.

Have you installed flash?  Do a search in the Ubuntu Software Center, it will show up as "Adobe Flash plugin".
Alternatively you could type this in the terminal: ```
sudo apt-get install flashplugin-installer
```

Then try again.  You'll need to restart the browser after installation.

---

### Post by asifnaz on 2013-10-05
Do you have Flash player installed ..?

---

### Post by craig10x on 2013-10-05
Have you installed ubuntu restricted extras?  It is the first thing to do after installing ubuntu...gives you all the codecs and flash that you need...

---

