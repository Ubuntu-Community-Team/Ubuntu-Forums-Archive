---
title: "Ubuntu vs Lubuntu and WiFi"
date: 2014-05-23
forum: New to Ubuntu
---

### Post by gtravis3 on 2014-05-23
Howdy,
Ubuntu appears to be working on a Dell XPS M140, but is slow as all get out. When I was using the installer USB stick and after it was installed, it detected my wireless network and all that I had to do was enter my password to connect and go netting. I wrote down all the info regarding the network: hardware address, various IP etc. addresses. 

However, based on advice given here, I gave Lubuntu a try, and it is so much faster. I was using live Lubuntu from a USB stick. I never saw anything that looked like the WiFi signal icon. I tried to enter the information mentioned above, but it would not save.  I don't know if that was because it live on a stick or not. 

I have been looking around, and have seen all sorts of scary command line fixes regarding folks having problems with WiFi. 

So is there some major difference between Ubuntu vs Lubuntu regarding WiFi ( it works on the first, but not the latter)? 
I'm using the latest downloads of both. 

Thank you you for your help.

---

### Post by Vladlenin5000 on 2014-05-23
No, there should be no difference regarding which hardware is already support and how it works and the "fixes" for others, if required, should also be exactly the same.
There is however a small detail that can make a lot of difference for newbies: Apparently there's a bug in recent Lubuntu versions preventing the network-manager and/or its applet (the "icon") to start right after the system being installed in a small percentage of systems (I've witnessed it twice).

[http://askubuntu.com/questions/451593/nm-applet-wi-fi-icon-missing](http://askubuntu.com/questions/451593/nm-applet-wi-fi-icon-missing)

---

### Post by wildmanne39 on 2014-05-23
Once you install lubuntu you should be able to enable wifi just like you did with ubuntu but it is possible as mentioned that you will have to apply the workaround for nm-applet in lubuntu but that is no big deal.

---

### Post by gtravis3 on 2014-05-23
Thank you both. I had started to wonder if there was a bug in Lubuntu, seeing as how a Ubuntu DE was working. I appreciate the help.

---

### Post by monkeybrain20122 on 2014-05-23
There should be no difference but there is. I have replaced xp on two old laptops. For one of them xubuntu and ubuntu 14.04 (live usb) immediately picks up the wifi but lubuntu 14.04 doesn't detect it at all (intel wifi). So I tried to use a dongle, lubuntu can't see it either but again Ubuntu and xubuntu detects it immediately. I am about to start a thread about it, but vladlennin5000 solved the mystery.

Since the laptop is too old for Ubuntu I ended up putting xubuntu on it. It is just as fast and wifi works out of the box.

---

### Post by gtravis3 on 2014-05-25
An update.
I decided to go ahead an install Lubuntu rather than just run the live version.  As soon as I choose INSTALL, I got a message that wireless was detected and connected and after installing, I still see no wireless applet(?), but I am connected and posting to here with no problem. 
Much happier with the improved GUI speed. 
Thanks to all who replied,
trav

---

### Post by Vladlenin5000 on 2014-05-25
Now you just need to apply to apply the workaround for nm-applet. Follow the link on post #2.

---

### Post by gtravis3 on 2014-05-25
Howdy Galiza,
I guess that I will have to give that a try. Now I have too much of a good thing.  I can't find a way to disconnect wireless, as the applet in Ubuntu DE does.
trav

---

### Post by gtravis3 on 2014-05-25
Well, after following those posted instructions for LXSessons, things appear to be working now.

---

### Post by wildmanne39 on 2014-05-25
Glad it is working, please use thread tools at the top of the page to mark the thread solved.

---

### Post by gtravis3 on 2014-05-26
Gad, I got thrown off a bit. I don't remember it happening in UDE, but if one disconnects from wireless, the applet changes into a console looking icon. I could see it if it just changed from blue to grey or red.
thanks again to everyone

---

