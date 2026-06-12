---
title: "Atheros 5007 wifi"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by surfoutsider on 2008-08-17
Ok I think this a common problem that happens to the new laptop owners attempting to dual boot but here it goes again.  My atheros 5007eg doesn't work and I need to install the linux drivers.  Easy enough, I have the madwifi link and I have read lots of code about getting the drivers on 32 bit hardy ubuntu.  But I don't have a wired connection to the internet to download the drivers through the terminal.  Do I have to download the drivers before and then extract them?  I am total rookie bent on eliminating microsoft from my life so the easier the answer the more appreciated.  Quick side note:  What is this I hear about Hardy crashing all the time with video on VLC.  I watch lots of movies on VLC Windows and that sounds like dangerous territory if Hardy can't support VLC. Are things resolved with Hardy or the problems for real?  No hair pulling in this debate.

---

### Post by fahadsadah on 2008-08-17
Download the drivers from Windows

I use hardy and VLC - no crashes.

Then again, I don't get any of the other common Hardy problems (overheating cpu, totally not working box, slowness, etc)

---

### Post by erickghint on 2008-08-17
> **fahadsadah said:**
> 
I use hardy and VLC - no crashes.



  +1 on the VLC usage. As to your WiFi problem, check this out. Although since you don't have IC on the Linux box, it may be a problem. [http://it.dennyhalim.com/2008/08/atheros-5007-wifi-ar2425-chips-linux.html](http://it.dennyhalim.com/2008/08/atheros-5007-wifi-ar2425-chips-linux.html)

   Is there any way that you may be able to go to a friend's house and plug into their router for a few minutes to get this taken care of? Or maybe a local cyber cafe?

---

### Post by nicedude on 2008-08-17
-1 for ndiswrapper there are better ways to utilize this adapter. I wrote a guide on how to install it correctly and have aircrack patched Madwifi drivers that are current linked on post#1 of my guide. I enjoy full wireless capability with the AR5007EG chipset including MONITOR mode and RAW PACKET INJECTION 2 things that Ndiswrapper can never provide nor will any Ubuntu standard drivers support Injection.

Heres a link to my guide

[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

If you do choose to follow it though, please read the whole thing and try to grasp what will be required of you. If you get stuck you can PM me and I will help you out :-)

At least 20 people have PM'ed me to say it worked for them so it can work for you too.

Ndiswrapper is the last choice in my book not the first. Also my driver linked there is also confirmed to work with both WEP & WPA and at high speed ( in my speed tests I get the same speed to the internet as I do with Ethernet connection ). And I wanted to be able to use Kismet & Aircrack so Ndiswrapper is not even an option if you want to use those as well.

And VLC works just fine in Hardy I am watching Batman The Dark Knight right now in VLC, so peace out to all as I have to get back to my movie :-)

Hope this helps you get it figured out.

---

### Post by erickghint on 2008-08-18
Who suggested ndiswrapper?

---

### Post by nicedude on 2008-08-18
sorry I guess I got confused about what you guys were suggesting for this fellow but I have a 100% guide to getting this adapter working and he can feel free to use it. Or listen to you, his choice.

---

### Post by surfoutsider on 2008-08-19
Hmmm ok thanks for the response but I'm still a little stuck.  It isn't possible for me to connect to someone's wired internet.  I just moved to Germany from CA. and I share my neighbors wireless.   I don't know anyone, yet, with wired internet and I can't German so internet cafes will be very confusing.  I don't need anything complicated on the internet usage, just WEP wireless internet.  Is it possible to download the packages on vista and then install them on hardy?  
About hardy issues, are the overheating problems common?  I have an AMD 64 laptop.

---

