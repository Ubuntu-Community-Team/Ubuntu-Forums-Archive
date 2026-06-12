---
title: "[SOLVED] python pop-up box"
date: 2008-11-07
forum: Programming Talk
---

### Post by roquefilipe on 2008-11-07
Hi, I have done a small python script that follows changes in a webpage. Now I would like to present a small pop-up indicating that a change was made. What is the best way? 

For pop-up box I mean those small pop-ups that show up when there are updates available or the way rhythmbox presents song information. 

I have tried zenity, but I don't seem to get what I want.

So, any ideias?

---

### Post by LaRoza on 2008-11-07
easygui is the easiest and most simple solution. [http://ubuntuforums.org/showthread.php?t=772507](http://ubuntuforums.org/showthread.php?t=772507)

---

### Post by Dirty Ole on 2008-11-07
python-libnotify

---

### Post by roquefilipe on 2008-11-08
I checked easygui. It doesn't feet my needs beacause they require user interaction, such as pressing OK or similar. My goal was just to display a message and fade way. 

Python-notify seems to do that, thank you. But there seems to be a big lack of documentation. I managed to find some examples out there such as [http://whijo.net/blog/brad/2007/06/24/python-and-cybersmart-caps.html](http://whijo.net/blog/brad/2007/06/24/python-and-cybersmart-caps.html) and [http://roscidus.com/desktop/node/336](http://roscidus.com/desktop/node/336). 

So my script is done. thank you both. I will mark this thread as solved.

---

