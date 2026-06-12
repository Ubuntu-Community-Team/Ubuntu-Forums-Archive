---
title: "pidgin and songbird"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by anemptygun on 2008-11-13
I want to have my status in pidgin updated with what i am playing so I downloaded [DbusBird]("http://addons.songbirdnest.com/addon/181") for songbird, and [pidgin-musictracker]("http://code.google.com/p/musictracker/") for pidgin. So, supposedly if I put getTitle in my status message it will update with what I am playing, but it's not working. I feel like I'm missing something very simple. Anyone who has used this have any pointers, I would be very grateful!:)

---

### Post by raycosm on 2008-11-15
Musictracker hasn't been updated in more than a year, I don't even think it works with Songbird in Windows. [pidgin-musictracker]("http://code.google.com/p/pidgin-musictracker/") is the continuation of musictracker after it was abandoned, you might have some luck with it. I know it works with Songbird in Windows. I'm using it right now, but it doesn't seem to be working with Linux.

---

### Post by anemptygun on 2008-11-15
Is this the same package that is in the repositiories?

---

### Post by LinLux451 on 2008-11-30
I agree. I'm running Songbird with LiveTweeter, and Pidgin with pidgin-musictracker. Apparently it works in Windows but i need a hand with ubuntu. Livetweeter with "current track" on pidgin is supposed to work in linux, but i got to many ./configure errors. any help would be awesome!

---

### Post by Band B on 2009-01-02
try:
sudo apt-get remove pidgin-musictracker
sudo apt-get build-dep pidgin-musictracker
en then building from source ([http://code.google.com/p/pidgin-musictracker/](http://code.google.com/p/pidgin-musictracker/))

---

### Post by flaminigo on 2009-03-26
I have displayed my track info from songbird in pidgin with musictracker successfully. 
Here are the steps.
1. Install the latest addon of songbird [DBusBird]("http://addons.songbirdnest.com/addon/181"). 
2. Build the latest [pidgin-musictracker]("http://code.google.com/p/pidgin-musictracker/") by:
               ./configure --prefix=/usr
               ./make
               ./sudo make install
    A deb package for Ubuntu 8.10 on x86 is also available in the attachment. You can install it by 'sudo dpkg -i pidgin-musictracker_0.4.16-1_i386.deb'. 

Enable the musictracker plugin in your pidgin and enjoy it. 

[ATTACH]107719[/ATTACH]

---

