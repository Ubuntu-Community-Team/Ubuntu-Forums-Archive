---
title: "Is there actually a program called &quot;Network Manager&quot;?"
date: 2014-04-14
forum: New to Ubuntu
---

### Post by mattw1 on 2014-04-14
Ok, incredibly frustrated.  It is a serious question, is there a program  called Network Manager, and if so, where is it?  Not "Network" or  "Network Connections", both of which I can find and open and both of  which are pretty much useless, to me anyway.  My problem is that I  cannot find a way to see the broadcasting, available wireless networks in my area with  a program that will actually allow me to connect to one of them.
  
Now, because I know the SSID I can use Network Connections to manually enter  the info to get connected to a  network and that part of it works quickly and fine.   The problem is that  I run two routers for a variety of reasons and those routers are  within 40 ft of each other.  As I  said, Network Connections allows me to connect to either network, but  in order to do so, particulary if I move from one room to another, I  then I have to literally DELETE the one connection in Network  Connections in order to connect to the stronger signal of the other  network rather than just choosing from a list of available networks.   Today I tried two other programs to see if they could get the job done,  WICD and WIFI Radar.  They both looked like excellent possibilities  because when I loaded them they immediately found all available wireless  networks in the area (not just mine, but 16 of them - I live in a condo) and presented them in a list with connection options.  The problem  is that after entering the correct password and encryption method(s) (WPA,  WEP etc) and double checking them, they couldn't connect.  Neither program.  So the bottom line  is that the one program that allows me to connect is such a pain in the  neck to use - Network Connections - that it is barely worth having, and  the two that have an interface that looks like exactly what I am looking  for, will find all of the networks but won't connect. Btw, before trying to connect with WICD and WIFI Radar, I did delete the networks I had entered in Network Connections, so there was no conflict.  

Sorry for the length.  Didn't see any other way to do it.  Can anyone help?  Thx.  Matt.

Matt W
Lubuntu 14.04
IBM Thinkpad T42
Pentium M
1.70 Ghz
768mb RAM
60gb HD

---

### Post by ian-weisser on 2014-04-14
There is indeed a program called Network Manager, and it's very handy.
It's included with the default install of Lubuntu, the network-manager-gnome package.
It supposed to autostart when you login, and put an applet icon in your system tray.

Apparently it's running (since you can use wireless at all), but the systray applet has some kind of problem with your system. 
Open a terminal and try the command **nm-connection-editor** to open the window where you can add multiple networks instead of deleting every time.

Open a terminal and try the command **nm-applet** to establish a new applet in your systray. If it works, then you know how to get the applet working.  If it fails, post the *entire* terminal output here.

---

### Post by mattw1 on 2014-04-14
Thanks so much for your willingness to help.  I did use the nm-applet command and it did bring up the list of networks (which was great to see, I feel like I'm getting close!).  Unfortunately, when I close the terminal window, it goes away again.  Here is what was shown:

tpad@tpad-ThinkPad-T42:~$ nm-applet
nm-applet-Message: using fallback from indicator to GtkStatusIcon

---

### Post by mattw1 on 2014-04-14
Alright, now this is bizarre - but in a good way.  So, following up on your good information which, as I said, I knew was getting us close, I opened up the "Default Applications for LX Session" program.  I remembered seeing a listing of autostart programs when I went in there earlier today and I even remember checking the "Network" box, which was unchecked at the time.  Now earlier today, that had no effect as I still could not see the applet in the panel tray (or whatever linux calls it), even after I rebooted.  Anyway, I just went back in there and did it again (I had put it back the way I found it earlier today), and now the nm-applet opens at startup.  I'm not sure how, or why, it's working now when it wasn't working earlier, but I'll take it.  Thanks again for your help.

---

### Post by grahammechanical on 2014-04-15
We interact with Network Manager using utilities like Network Connections. But two or more Network Managers cause conflict. By installing those other Network Managers you caused a conflict with Network Manager used in Ubuntu/Lubuntu. That is the most likely reason Network Manager was removed as a start up application.

Furthermore, once we make a network connection with a wireless access point then Network Manager locks on to it to maintain contact. This is why you need to disconnect from one wireless access point and connect to another.

Each wireless access point will have its own pass phrase that is needed to authenticate the connection. This is another reason why we cannot "roam" in the way you would like.

Regards.

---

### Post by HermanAB on 2014-04-15
Yes, the program is called 'NetworkManager'.

---

