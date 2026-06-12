---
title: "Newbie Questions &amp; Comments"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by WhyZeeGuy on 2008-06-01
Okay, I have to say that Ubuntu 8.04 rocks, just freakin rocks!   My 3 year old AMD Athlon 3200+ 1GB RAM, ATI X800 vid w/ SB Audigy 2 just flies and the internet in blazing fast.  I couldn't be more happy.  

I'm a long time Windows user and I had XP locked down pretty tight, but its gone now.  I fired Microsoft and have no plans of going back.  My Anti virus, Firewall and Windows Blinds subscriptions were all up for renewal and I was tired of laying out cash for product.  

I'm fairly technical and work with virtualization technologies everyday.  A shameless plug for my company, [Chip PC]("http://www.chippc.com") and our flagship product the [Jack PC]("http://www.chippc.com/thin-clients/jack-pc/") 

I enjoy tweaking systems, but unfortunately I've probably messed a few things up in Ubuntu customizing my desktop.  I installed Compiz and I think some of the KDE environment, icons and other eye candy stuff.  Now when the system boots unless I run Compiz any app that launches in stuck in the top left without its frame.  Menu is there, just no frame and I can't move the window.  I'm still trying to figure out how to auto start Compiz but the Linux file system is still a total mystery to me.  Where do I find the Compiz executable and how do I setup Compiz to automatically launch?  From the Session manager? 

One complaint, I don't care for Rhythmbox at all.  I'm a long time Winamp user and really like its functionality and find Rhythmbox lacking.  Also, occasionally Rhythmbox doesn't start the first time I try to launch it.  Always comes up the second time, so its not big deal but I hate bugs in the system.

Another issue is I can't save my desktop scheme.   I'll change  the colors and window frames but next time the system boots its back to the default scheme.  How I do I fix this?

I'm looking forward to learning this OS and getting it setup the way I want it.  I'll probably install Wine so I can run Winamp and RoboForm, other tan that I'm gonna list all my programs on eBay.  

Any input on how to correct these problems is appreciated.

---

### Post by sayakb on 2008-06-01
1. Goto System->Preferences->Sessions and Add compiz there:
Set Name as Compiz (or whaever)
Set command as [B]compiz --replace

[/B]2. Use players like Exaile, Audacity, Amarok, Banshee
3. Use emerald theme manager for more beautiful themes. Install emerald:
```
sudo apt-get install emerald
```And do:
```
emerald --replace &
```to use emerald. Goto [http://gnome-look.org/](http://gnome-look.org/) and search for *Beryl Emerald Themes* for more beautiful emerald themes.
You may also add emerald on startup in the same way you added emerald.

Plus, have you installed ccsm:
```
sudo apt-get install compizconfig-settings-manager
```
Now goto System->Preferences->Advanced desktop effects settings
and customize compiz as the way you like!

---

### Post by _zax_ on 2008-06-01
propably the jpeg [or what ever] that you choose for backround is not in a mounted place at the beggining. Make sure that the picture is for example under the home folder so is mounted from the beggining. somewhere like /home/yourusername/Pictures

---

### Post by Victormd on 2008-06-01
> **WhyZeeGuy said:**
> One complaint, I don't care for Rhythmbox at all.  I'm a long time Winamp user and really like its functionality and find Rhythmbox lacking.

Seems like all your other issues are emerald and/or compiz related and since that has already been addressed... have you tried Amarok (it's in the repos')? I was also a winamp user for a long time but find amarok to be far superior!

---

### Post by m_ad on 2008-06-01
people continue to recommend audacity but there is a huge bug in it which to me makes it unusable: you can't load m3u files!

---

### Post by markbuntu on 2008-06-01
I like rythmbox because it is simple and stupid and just plays the music without any troubles or elaborate fooling around with settings but if that is your thing then audacity is for you. I used to do a lot of sound recording and engineering and there is a time and place for that and a time and place for just playing the music.

If you need to fool around with the eq etc, and the quality of the sound is important to you, you should invest in some high quality speakers. That will do more for your sound than anything/everything else you can do.

That said, I am pretty sure that audacity will play m3us. Do you have all the plugins?

---

### Post by shifty_powers on 2008-06-01
> **WhyZeeGuy said:**
> My Anti virus, Firewall and Windows Blinds subscriptions were all up for renewal and I was tired of laying out cash for product.  


as much as i love ubuntu, it must be said that there are free versions of the first two that will be just as good, if not better, the paid for evrsions...

---

### Post by WhyZeeGuy on 2008-06-02
Okay, I've tried all the recommendations and have everything running smoothly except saving my desktop scheme/theme colors.  Every time I reboot the desktop comes back up in its default colors (But preferred wallpaper is displayed).  I've saved the scheme as My scheme so I can easily go in and select but I would prefer is starts as the default scheme.

---

### Post by hyper_ch on 2008-06-02
you normally don't need antivirus or firewall on linux (except if you're going to install server services).

---

### Post by ertrules22 on 2008-06-02
So, you have saved the theme correct?  I assume you have edited one that you downloaded right?  And you have saved everything when you edit it?

---

### Post by WhyZeeGuy on 2008-06-02
I haven't downloaded any themes, just played with and edited the default color schemes and window frames.

---

### Post by WhyZeeGuy on 2008-11-02
Well after a hefty learning curve I finally have everything working the way I want it.    System is super fast and stable. Love my desktop, check out the screen shot.

---

### Post by shifty_powers on 2008-11-02
just a quick question, where did you get that picture for your desktop?

a link would be most appreciated :D

---

### Post by Paqman on 2008-11-02
> **WhyZeeGuy said:**
> A shameless plug for my company, [Chip PC]("http://www.chippc.com") and our flagship product the [Jack PC]("http://www.chippc.com/thin-clients/jack-pc/") 


That's the coolest thin client i've ever seen. Who do you sell them to? Hotels and the like?

---

### Post by jolx on 2008-11-02
> 2. Use players like Exaile, Audacity, Amarok, Banshee

> people continue to recommend audacity

> I am pretty sure that audacity will play m3us

as far as i know, audacity is an audio manipulation program, however there is a very good audio player called audacious :D

---

