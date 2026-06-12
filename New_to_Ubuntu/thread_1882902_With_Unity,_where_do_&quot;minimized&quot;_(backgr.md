---
title: "With Unity, where do &quot;minimized&quot; (background process) icons go to now?"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by diablo75 on 2011-11-18
I just upgraded an old computer I use as a server of sorts to 11.10 and am pleased to see the 2D version of Unity running quite well on it.  However, a question I've had in the back of my mind for a while but didn't really care to ask until now is:  Where do all the little extra icons for background processes go to now?

One of the things I run on this system is PS3 Media Server (edit to add:  I also used Transmission in a "start minimized" fashion), which used to add it's own icon to the upper task bar in GNOME by the clock, so even if you "closed" the program it was still actually running in the background, not taking up space on the task bar panel at the bottom like most applications do, and you could double-click it to bring the interface back up.  Now, with 11.10, I have confirmed that when I click the close button, the icon that's on the Unity Panel for the window itself completely disappears yet the program is still running, because I'm able to access it from my PS3. 

Another example of stuff I used to have in the upper panel was my system monitor widget for monitoring CPU, RAM and Network bandwidth usage.  With this fresh install all that stuff is gone now and it would be nice to have it all back.  Is there anyway to get this stuff to come back up without switching back to GNOME?  I rather like the clean look of Unity, save for the little rough edges like what I'm describing here.

---

### Post by dave0109 on 2011-11-18
I believe you're referring to the Notification Area, aka System Tray on Windows.  You might be able to add the Notification Applet to the top panel, but I recall reading that the panel isn't so configurable with Gnome 3.  I'm not using Unity much at the moment, it's only on my seldom used netbook, so can't say for sure.

---

### Post by Mark Phelps on 2011-11-18
As far as I know, they don't go anywhere now. Instead, you get a button added to the launchbar and some marks to the right and left of it indicating that it has been minimized.

---

### Post by grahammechanical on 2011-11-18
As for your final request, they are called app indicators - application Indicators. They need to be modified to work with Unity and many are being modified. Here are two links.

[http://www.ubuntu-corner.com/2011/06/application-indicators-for-ubuntu-11-04/]("http://www.ubuntu-corner.com/2011/06/application-indicators-for-ubuntu-11-04/")

[http://news.softpedia.com/news/Top-10-Ubuntu-11-04-Unity-Panel-Applets-208034.shtml]("http://news.softpedia.com/news/Top-10-Ubuntu-11-04-Unity-Panel-Applets-208034.shtml")

I can vouch for Radio tray working in 11.10. There may be other sites that list other app indicators for Unity.

Regards.

---

### Post by 3rdalbum on 2011-11-18
The old-school "notification area" icons are depreciated now - they have been since 2009 - and won't appear by default. Application developers are expected to use the Indicators API now, which is what the current icons use.

You can cause notification area icons to appear again by making a simple modification, mentioned here: [http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/](http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/)

It should work for 11.10 as well as 11.04. The notification area icons will appear at the left of the indicators on the top panel.

---

### Post by koolkatkiwi on 2011-11-19
All I can say is, whatever happened to "If it ain't broke, don't fix it."? Why on earth wouldn't we want a notification area to see what programs are running? :confused:

---

