---
title: "Last thread on my wireless...."
date: 2008-08-05
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-08-05
This is going to be my last thread on trying to get my wireless sorted before i just give up and get over the fact that I'm going to have to put up with cables running up and down the stairs:lolflag:

Ok here goes....

I Have a Linksys WUSB54G which wouldn't work with Ubuntu out of the box, well I'll rephrase that Ubuntu could tell that it was connected but it wouldn't display any wireless networks which were available.

So on the recommendation of a couple of users i installed Ndiswrapper and tried using that with my wireless adapter at which point i managed to connect with my router once! and only once, at this time i was able to input my pass phrase but unfortunately i was unable to connect. The green wireless connection icon in the top right just continued to spin and it went on like this for a good 4-5 days every time i tried to connect:( eventually i gave up and i am now using a wired connection. 
Just recently i thought i might have another go at getting the Damn thing working so i plugged it in and checked on the nidiswrapper "Windows Wireless Devices" bit at which point it all looked good saying that it was connected and working properly but again i cant seem to be able to find any wireless networks! and the box is no more than a ruler's length away!


_List of blatantly obvious thing which i haven't missed!_
[LIST]
[*]The button on the side of the router was pressed to allow a connection
[*]everything is plugged in correctly
[*]My wireless adapter works fine in xp and vista so it's not broken
[*]My mum manages to connect to the router via her laptop ok so the router is perfectly fine
[/LIST]


Thanks in advance!

---

### Post by tamoneya on 2008-08-05
first of all for trouble shooting purposes try disabling any wireless encryption you have.  If we can get it working like that we can then try getting things locked down.  Also have you looked into wicd?

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by kamitsukai on 2008-08-05
> **tamoneya said:**
> first of all for trouble shooting purposes try disabling any wireless encryption you have.  If we can get it working like that we can then try getting things locked down.  Also have you looked into wicd?

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

:guitar:OK it looks like the problem was my WPA encryption as turning it off enables me to connect:KS but unfortunately this isn't an option for me as i live in a built up area with a main road close by (wardrivers...) I've tried wicd before but to me it just seemed like an extra hassle as i didn't like it as much as the standard Ubuntu connection thingy lol

---

### Post by tamoneya on 2008-08-05
i was never advocating for going without encryption.  Now we know more about the problem and we know more specifically what needs to be fixed.

EDIT: Ive been researching so now lets turn WPA back on and try these two suggestions: 
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
[http://www.fam.tuwien.ac.at/~schamane/_/blog:080512_wusb54g_wpa_on_ubuntu_8.04](http://www.fam.tuwien.ac.at/~schamane/_/blog:080512_wusb54g_wpa_on_ubuntu_8.04)

Lets start with the first one.  By doing it through command line I hope to get a more detailed error message.

---

