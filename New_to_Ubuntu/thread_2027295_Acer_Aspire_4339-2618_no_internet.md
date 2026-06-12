---
title: "Acer Aspire 4339-2618 no internet"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by kbmike64 on 2012-07-16
Hi, I'm still pretty new to ubuntu and linux in general and I am having A LOT of trouble gettting my Acer 4339 to connect to the internet. I know that it is probably my wirless card ( atheros ar5b95) but i am lost on how to fix it because I cant connect to the internet at all to get to the software store. Any help would be much appreciated. Thank You

---

### Post by mike555 on 2012-07-16
Go to a friends house and connect to wired internet then check "additional Drivers" in your menu.

---

### Post by techvish81 on 2012-07-16
or, connect through a phone via usb tethering.

---

### Post by sanderj on 2012-07-16
> **mike555 said:**
> go to a friends house and connect to wired internet then check "additional drivers" in your menu.

+1

---

### Post by kbmike64 on 2012-07-16
> **mike555 said:**
> Go to a friends house and connect to wired internet then check "additional Drivers" in your menu.

Well I tried to connect to my wired internet at home but every time I try to download something it tells me that it cant and to check my internet connection... I'm sorry I know I'm a novice but I really want to get into Linux and this is the only thing holding me back. Thanks

---

### Post by kbmike64 on 2012-07-16
> **techvish81 said:**
> or, connect through a phone via usb tethering.

Thanks that's one thing I never even thought of I'll try it and post back if it worked or not tonight

---

### Post by sanderj on 2012-07-16
> **kbmike64 said:**
> Well I tried to connect to my wired internet at home but every time I try to download something it tells me that it cant and to check my internet connection... I'm sorry I know I'm a novice but I really want to get into Linux and this is the only thing holding me back. Thanks

Is there any Internet connectivity when you have a wire connected?
For example: can you browse Internet?

---

### Post by kbmike64 on 2012-07-16
> **sanderj said:**
> Is there any Internet connectivity when you have a wire connected?
For example: can you browse Internet?

No not at all...

---

### Post by sanderj on 2012-07-16
> **kbmike64 said:**
> No not at all...

And do you want to solve that?

If so:

If there is no Internet at all, how are you using this forum?
On what kind of network are you? At home? At work? Hotspot?
Open a terminal, and type

```
ifconfig
nm-tool
```

and post the output here.

---

### Post by kbmike64 on 2012-07-16
> **sanderj said:**
> And do you want to solve that?

If so:

If there is no Internet at all, how are you using this forum?
On what kind of network are you? At home? At work? Hotspot?
Open a terminal, and type

```
ifconfig
nm-tool
```

and post the output here.

I'm sorry if I wasn't clear enough in my last post... I have Ubuntu duel booted with Windows 7 and my wireless and everything still works on Windows. Oh ya, and I am currently at home.

---

### Post by kbmike64 on 2012-07-17
> **kbmike64 said:**
> Thanks that's one thing I never even thought of I'll try it and post back if it worked or not tonight

Ok, so I tried this and it worked to get me connected to the internet!! However, when i click on "additional drivers" it says that none are in use on my computer.....?

---

### Post by techvish81 on 2012-07-17
how are you connecting through wireless? does the connection icon in the right side of panel show connected? can you determine your card? 

following link can be helpful to you.
[https://help.ubuntu.com/11.04/ubuntu-help/net-wireless-troubleshooting-hardware-check.html]("https://help.ubuntu.com/11.04/ubuntu-help/net-wireless-troubleshooting-hardware-check.html")

---

### Post by kbmike64 on 2012-07-19
Ok so, now my wifi works for the first couple of minutes and then I lose internet access but am still connected. Thank you by the way the link was VERY helpful in getting me this far. I'm excited for this to actually work! Any ideas on why i would lose internet access after having it for a few minutes?

---

### Post by techvish81 on 2012-07-19
what version of ubuntu are you using.?  

see the link below if not helpful try to search related threads in forum.

[http://ubuntuforums.org/showthread.php?t=1460535]("http://ubuntuforums.org/showthread.php?t=1460535")

you can also search in google.

---

### Post by kbmike64 on 2012-07-22
> **techvish81 said:**
> what version of ubuntu are you using.?  

see the link below if not helpful try to search related threads in forum.

[http://ubuntuforums.org/showthread.php?t=1460535]("http://ubuntuforums.org/showthread.php?t=1460535")

you can also search in google.

Im using 12.04 LTS 64Bit. Do different versions support different drivers??

---

### Post by techvish81 on 2012-07-22
yes, wireless modules are updated with every new release and may be drivers to some legacy devices are removed to conserve space.

---

### Post by kbmike64 on 2012-07-23
> **techvish81 said:**
> yes, wireless modules are updated with every new release and may be drivers to some legacy devices are removed to conserve space.
Ok so do you have any advice on what version might support my drivers better?

---

### Post by techvish81 on 2012-07-23
> **kbmike64 said:**
> Ok so do you have any advice on what version might support my drivers better?

actually,  i've no idea about your particular card, but in general,  older hardware will work with older versions of ubuntu and newer with newer.

one more link to try.
[http://ubuntuforums.org/showthread.php?t=1230823]("http://ubuntuforums.org/showthread.php?t=1230823")

---

### Post by kbmike64 on 2012-07-23
> **techvish81 said:**
> actually,  i've no idea about your particular card, but in general,  older hardware will work with older versions of ubuntu and newer with newer.

one more link to try.
[http://ubuntuforums.org/showthread.php?t=1230823]("http://ubuntuforums.org/showthread.php?t=1230823")
Ok Thank You VERY much you have been really helpful n Ill be sure to post back if it works. One more question though, Should I try running a 32-Bit version just to see if it works?

---

### Post by techvish81 on 2012-07-23
> **kbmike64 said:**
> Ok Thank You VERY much you have been really helpful n Ill be sure to post back if it works. One more question though, Should I try running a 32-Bit version just to see if it works?

no, 32bit will not make any difference.  
it was my pleasure to help you, 

good luck!

---

### Post by kbmike64 on 2012-07-25
> **techvish81 said:**
> no, 32bit will not make any difference.  
it was my pleasure to help you, 

good luck!

Well, Im now running 11.10 and my wifi works right away! However, once i get a few feet from my router it drops signal...

---

### Post by techvish81 on 2012-07-25
have you tried 11.04? which versions you have tried out?

---

