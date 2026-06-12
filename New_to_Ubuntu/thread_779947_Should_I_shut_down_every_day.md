---
title: "Should I shut down every day?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2008-05-03
Forgive me if this is a stupid question, but should I shut down my computer everyday and how often do I need to restart? I run Ubuntu as my only operating system now. I heard Ubuntu was stable but just how stable?

Also, does anyone know where I can get some cool desktop themes and backgrounds?

---

### Post by Exershio on 2008-05-03
You don't need to ever shut down. =D Welcome to Linux. Of course, some updates require a restart, but that's about it.

As for awesome desktop customization:
[http://gnome-look.org](http://gnome-look.org) if you have Gnome
[http://kde-look.org](http://kde-look.org) if you have KDE

---

### Post by fhmanas on 2008-05-03
Should you shutdown everyday, well, yes if you want to conserve energy and have no real use for it to be up all the time.

---

### Post by FredB on 2008-05-03
It depends on your need. If you want to save energy, yes, you can shut down every single day.

But it is not necessary. Having the biggest uptime is not a game I'm fond of.

---

### Post by iSplicer on 2008-05-03
Shut it down if you want to save power, but not shutting down has no real cons. Welcome to Linux BTW!

---

### Post by gary4gar on 2008-05-03
> **iSplicer said:**
> Shut it down if you want to save power, but not shutting down has no real cons. Welcome to Linux BTW!
No need to shutdown or reboot,

I am running my box from past 16days.

---

### Post by iSplicer on 2008-05-03
How much power does a computer use up? Please compare to a 60w bulb...

---

### Post by StOoZ on 2008-05-03
my computer is turned on for the last couple of years, some restarts here an there, maybe two small turn offs to install a new HDD and a DVD. usually I turn off the screen and thats it.

---

### Post by Paqman on 2008-05-03
> **iSplicer said:**
> How much power does a computer use up? Please compare to a 60w bulb...

About the same as 2-4 60W lightbulbs.

(Seriously though, who still uses 60W bulbs? An 11W energy saving bulb puts out the same light and lasts longer)

---

### Post by iSplicer on 2008-05-03
> **Paqman said:**
> About the same as 2-4 60W lightbulbs.

(Seriously though, who still uses 60W bulbs? An 11W energy saving bulb puts out the same light and lasts longer)

Thanks for that. 

Those white lights just arent the same :lolflag::lolflag:

---

### Post by gasansat on 2008-05-03
even if i use it as server no need to restart every 3 days i do
btw how i can make it restard every 3 days by hem self
thanks

---

### Post by jflarm on 2008-05-03
The cron should help you with that. Search more about it on the web, but here's a quick way to restarting your computer every 3 days at 00:00.
Don't just do this, learn about this cron, and then do your own customization.

sudo su
crontab -e ----> To edit the root crontab

Within the editor, add this as the last line and do Ctrl+X to exit and save

0 0 0 * 0,3 shutdown -r now

---

### Post by CREEPING DEATH on 2008-05-03
> **iSplicer said:**
> How much power does a computer use up? Please compare to a 60w bulb...

An energy-efficient power supply can actually keep usage below 60W from the wall.  I use, and highly recommend, Antec EarthWatt PSUs.

CD

---

### Post by halitech on 2008-05-03
I leave mine all on the time and not to brag but I usually get up around 30 days before an update will force me to restart or I do something stupid like hit the wrong button on my surge protector that shuts me down when I meant to turn off the monitor :(

---

### Post by fhmanas on 2008-05-11
> **iSplicer said:**
> How much power does a computer use up? Please compare to a 60w bulb...

A normal pc would probably have a 400W PSU plus your monitor.  If you don't want the white light (Daylight), there are 11W warm light (Warm) which gives a yellow glow or an in-between (Cool Daylight) which is not so yellow and not so white

---

### Post by SunnyRabbiera on 2008-05-11
Well some people claim that turning a computer on and off can use more power then just leaving it on.
Me I have no real choice but to keep my puter running as I run a network in my house :D

---

### Post by dtrot55 on 2008-05-11
Don't know if this is correct but wouldn't turning your computer on and off be worse for it?  The starting and stopping of parts would be hard on the parts.  If it is constantly running they are more efficient? I've heard of servers that have never been shut off...shut off and then have hard drive issues and stuff.  But yeah just have your monitor turn it's self off to save energy and keep your computer on

---

### Post by diablo75 on 2008-05-11
From what I was told by my class instructors, leaving a computer on is preferred, due to the gradual wear/tear caused by the act of jolting the computer when first powering up.  Though to be honest, if your computer dies as a result of that kind of wear and tear... it's probably time to build a new one anyway.

---

### Post by hufferd on 2008-05-11
> **iSplicer said:**
> Thanks for that. 

Those white lights just arent the same :lolflag::lolflag:

:lolflag:

Just reading here your right those white lights are not the same but I have learned to deal with them.  The fact that my local power companies rates have gone up 70% in the last 2 years.  Has made me put up with them.  That brings me to my next point.  

I used to leave my PC up all the time but with the cost of energy going up almost monthly.....  I to turn mine off now when Im not using it. Do you really need to leave it up all the time.  I say shut it down if your not using it.  Its like driving a BIG SUV if your only one person WHY do that if you don't need it..  But ah Thats another can of worms LOL

Have a great Sunday 

Happy mother's day to any mom's reading!

---

### Post by Joeb454 on 2008-05-11
I leave my server up and running all the time, but other than that I use a laptop, so except for the odd occasion it's downloading something, it gets turned off everyday.

My server had been on for around 17 days until yesterday, we had a power cut :(

---

