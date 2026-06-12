---
title: "[SOLVED] Sopcast TV Player - how do I play it?"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by t0p on 2008-08-19
I've installed the app **gtk-sopcast**, aka **gsopcast**, **Sopcast TV Player**.  I've looked for documentation, but the little I've found is extremely poor.

When I launch the app, it searches for then displays a list of "channels".  I select one - lots of network activity goes on, which indicates to me that it is receiving (and sending) the channel. (It's a P2P TV streaming app.)  But I don't know how to actually *play*.

From what I've read, I get the idea that I should use vlc to play the network stream.  But there's no indication of *how* to do this.

If anyone here knows how to use this app, please enlighten me!!

---

### Post by gn2 on 2008-08-19
The answer might be in here: [http://ubuntuforums.org/showthread.php?t=258049](http://ubuntuforums.org/showthread.php?t=258049)

---

### Post by t0p on 2008-08-19
Ok... reading the thread linked to by gn2 has just confused and frustrated me all the more!!

 The stuff I just read goes on about changing configuration to choose player - but the config button is greyed out!  In fact, *all* the buttons across the top are greyed out - sopcast, config and about.   What gives?!!

If anyone can help me (please please let someone be able to help me!!)... I'm using **gtk-sopcast 0.2.8.1**, which I got as a .deb.

How can I get to the configuration, when the config button's greyed-out?  How do I get an actual player to launch? How do I make this flaming thing work??  :confused:  In that thread g2 linked to, people go on about how great this app is... SO HOW DO I GET TO USE IT???  :(

**EDIT:**  I've attached a screenshot of what my "gsopcast" window looks like, if that's of any use.

---

### Post by pauper on 2008-08-19
Try this one:

[http://www.linux.ryukent.co.uk/show.php?id=36](http://www.linux.ryukent.co.uk/show.php?id=36)

---

### Post by t0p on 2008-08-20
Okay, so I finally got a working version of sopcast.  I installed it from a .deb [that I've linked to here]("http://linuxtoy.org/files/deb/gtk-sopcast_0.2.8-1_i386.deb").

Then I set sopcast to use vlc as its player: click on **config** - the buttons at the top of the sopcast window, **sopcast**, **config** and **about** appear to be greyed-out but still work nevertheless; in the player field type vlc.  Save and close window. 

*But* most of the channels it lists are from China.  There are 1 or 2 from France and Italy too - there are few/no English language channels. :(  So that's what I've got to do now - find a list of English language channels.  And figure out how to put the info into Sopcast.  But I feel like I'm getting somwhere with it now.  At last!

---

