---
title: "A problem with certain applications..."
date: 2008-10-15
forum: New to Ubuntu
---

### Post by amc6987 on 2008-10-15
Hey guys,

Im using 8.04, and am having a problem with some online applications. For some reason, I cant sign into Pidgin, use Transmission Bittorrent Client, Limewire, or assign my ClearWeather widget a zip code. There seems to be a problem with these programs/applications connecting to my internet. My internet works fine with firefox and browsing, though.

Any ideas as to what is wrong? Thanks

---

### Post by Tatty on 2008-10-15
It could be a firewall problem.  Try temporarily turning off any firewalls you may have in your router, etc.  If that solves the problem then you will need to find out the port numbers these applications use and set up port forwarding in your router.

If not then try running these apps from the terminal to see if you get any clues from the terminal output.

---

### Post by patrickballeux on 2008-10-15
Feels like you are using a proxy to reach the internet.


Is this your home network or are you on a corporate network?  Often a proxy will be used to connect to the internet on corporate network.  If you are not sure, see the Firefox setup in "Preferences" to validate if any proxy was setup.

Or maybe in "System - Preferences - Proxy Settings"?

If this is the case, some software support the use of a proxy server like Pidgin.

Good luck!

---

### Post by amc6987 on 2008-10-15
Thanks tatty, it is a firewall problem.

I have found the ports under the preferences tabs for each of the programs, but am unsure of which to use. I was told by a friend that I should look for a UDP or a TCP port number. Transmission has a number labeled TCP, but 
Pidgin has two different numbers for a start and end port. And Limewire has a Manual Port Forward number. Which numbers should I use?

---

### Post by trikster_x on 2008-10-15
If you can get into the settings of your router, then you should be able to open ports manually and assign a port to each program.  Remember that you can only have one program per port.  And this thread should address your clearweather problem:
[http://ubuntuforums.org/showthread.php?t=784053&highlight=clearweather](http://ubuntuforums.org/showthread.php?t=784053&highlight=clearweather)

---

### Post by amc6987 on 2008-10-15
Thanks trickster. I found Screenlets 0.1.1 in that thread and that fixed the clearweather problem.

---

