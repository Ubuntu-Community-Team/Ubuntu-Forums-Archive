---
title: "[SOLVED] wlan dies arfter a couple hours"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by trigsenior on 2008-08-10
hello ,

I am having problems with wlan , i can connect fine but after about an hour or two it dies however still connected to modem and i can only reconnect if i un-plug cable  and plug back in. 

I tried asked for help on irc and people suggested disabling acpi on boot. 
Is this a good idea , as it sound a bit radical =) 

many thanks as usual and hope you can help

ps : wireless works fine

FIX =

The problem had nothing to do with ubuntu as same thing happened in m$.
I did a bit , well quite a bit of searching Turns out its a problem with the orange box i had to go to 198.168.1.1 and disable UPnP.

now works great , touch wood

---

### Post by Mytth on 2008-08-10
If its a wireless problem why do you have it connected to a modem?Does the wifi die in a couple of hours or the connection from the router?

---

### Post by trigsenior on 2008-08-10
sorry was not clear enough.

I can connect to wireless Without any problems.

However i want to connect to the modem though a cable as it is faster but every few hours the internet stops working. And to make the internet work again i have to un plug the cable from the modem and replug it in. The internet is still working on the modem i believe it is a problem with Ubuntu. 

i hope this made a bit more sense :)

---

### Post by Crafty Kisses on 2008-08-10
When the internet drops, try pinging a website:
```
ping www.whatever.com
```
See if you get a reply.

---

### Post by lisati on 2008-08-10
There might be a conflict with another wireless network in your area. Does changing the channel your wlan uses help? (how to do this will depend on your hardware)

---

### Post by Victormd on 2008-08-10
> **trigsenior said:**
> sorry was not clear enough.

I can connect to wireless Without any problems.

However i want to connect to the modem though a cable as it is faster but every few hours the internet stops working. And to make the internet work again i have to un plug the cable from the modem and replug it in. The internet is still working on the modem i believe it is a problem with Ubuntu. 

i hope this made a bit more sense :)

What router do you use? I have a similar problem with a cheap belkin router that I have. My laptop (wireless) goes out but my desktop (wired) stays connected. I have to reset the router every time this happens. In my case, it's not ubuntu because the same thing happens when I'm using windows...

---

### Post by trigsenior on 2008-08-10
thanks for all you reply s, 

>  When the internet drops, try pinging a website: 

i tried that i get host not found

> here might be a conflict with another wireless network in your area. Does changing the channel your wlan uses help? (how to do this will depend on your hardware)

There is only one wireless connection where i am ( i live in the middle of no where). The wireless is fine  , however wired drops every couple hours.

> What router do you use? I have a similar problem with a cheap belkin router that I have. My laptop (wireless) goes out but my desktop (wired) stays connected. I have to reset the router every time this happens. In my case, it's not ubuntu because the same thing happens when I'm using windows...

Im using an orange live box [http://en.wikipedia.org/wiki/Orange_Livebox](http://en.wikipedia.org/wiki/Orange_Livebox). (the old ugly one ;) )
I will have to boot up in to windows and brave the pop ups  and see if this happens in m$.

---

### Post by Victormd on 2008-08-10
> **trigsenior said:**
> There is only one wireless connection where i am ( i live in the middle of no where). The wireless is fine  , however wired drops every couple hours.

Well, your network behavior is different from mine, my wireless is what craps out... but it's worth a shot checking it out under windows as well...

---

### Post by trigsenior on 2008-08-11
sorry for delayed post but just wanted to make sure it was fixed.

The problem had nothing to do with ubuntu as same thing happened in m$.
I did a bit  , well quite a bit of searching ;)  Turns out its a problem with the orange box i had to go to 198.168.1.1 and disable UPnP.

now works great , touch wood 

thanxs as usual. :)

---

