---
title: "Ubuntu e17 itask-ng skype pulseaudio"
date: 2010-08-13
forum: Outdated Tutorials &amp; Tips
---

### Post by xetaprime on 2010-08-13
Hi all! Please ignore this if it's been said already.

For the last several weeks after PCLinuxOS went full KDE4 on me and I couldn't install kdenlive in 3.5+ I went exploring and found e17. I love it! I've been messing with every distro that could run e17 from elive to mint to pclinuxos to here. Today is my first day with 10.4 running e17 and if remastersys works as it did in Mint 9, I may stick with Ubuntu for a while. But I'm writing this in case anyone has had some of the same issues as I have.

1. Following the enlightenment repos you get dependency errors primarily with libecore svn stuff. I found that changing the repo to 'karmic' even though it's not listed [here]("http://packages.enlightenment.org/")- works! Worked for Mint 9 also. Make sure you get the repo key. If it doesn't work using their method try this

[http://forumubuntusoftware.info/viewtopic.php?f=7&t=2720](http://forumubuntusoftware.info/viewtopic.php?f=7&t=2720)

2. I've had problems with editing icons in itask-ng- as in they don't appear- not all- some- such as kmix or whatever. If you go to /usr/share/applications or the kde4 folder there you can change the app properties icon there and it will show up in itask-ng. That was causing me grief on every e17!!!

3. SKYPE and Pulseaudio!!! Remove pulseaudio! when you restart Skype you should have your controls back in options sound. Kmix works great!

I'm really enjoying this new system. Here's a screen shot 

[IMG]http://img826.imageshack.us/img826/5497/snapshot1q.png[/IMG]

So I'm going to try and remaster now (fingers crossed). This is the version 2.0.17  that installed no problem and worked in mint 9-

[http://linux.softpedia.com/progDownload/Remastersys-Download-26479.html](http://linux.softpedia.com/progDownload/Remastersys-Download-26479.html)

If this works I'll have 3 pre-configured e17s! PCLinuxOS, Mint 9 and Ubuntu! Cool beans!

Best wishes,
Xeta

---

### Post by xetaprime on 2010-08-14
Good Morning! 

Rematersys worked beautifully! And I want to add an issue or two. For some buggy reason gnome-screensaver would not start. In fact I couldn't find the control center or any screensaver option in my menu list. But if I go into settings/settings panel/settings/profiles and reconfigure quick launch to include control center- then the control center appears in Ibar or task-ing- but with no icon. This allowed me to access the screensaver controls but it still would not start. So I went into settings/settings panel/Apps/New Application and added: 
[FONT=monospace]
[/FONT]gnome-screensaver-command --activate 

as the executable. Then somehow I added the nuke icon and placed it on the desktop to start with one click. You know how it is when you try a million things and you can't quite remember where you went or what you did :0 And I added the control center to the desktop as well by dragging it out of /home/(yourhome)/.local/share/applications folder. You can change the icon properties there too. And made a new remaster.

[IMG]http://ubuntuforums.org/gnome-screensaver-command%20--activate[/IMG][IMG]http://img440.imageshack.us/img440/3195/snapshot2d.png[/IMG]

Best wishes,
Xeta

---

