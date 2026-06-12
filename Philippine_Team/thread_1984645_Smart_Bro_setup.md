---
title: "Smart Bro setup"
date: 2012-05-22
forum: Philippine Team
---

### Post by andydovey on 2012-05-22
Hi, I've recently moved to The Philippines and I have just bought a Smart Bro USB stick for mobile internet. I'm using Ubuntu 11.10 which recognises the stick and I have opened it using Wine. The network manager shows "Enable Mobile Network" but it won't let me check it. It also shows "Smart Bro" but when I click it, it says that I am now disconnected.
I downloaded Wammu and it says that the "phone" is connected but I can't seem to get any further than that. The Smart Bro came with 120 hours of internet so I suspect that I have to get it to text to Smart to set that up but I can't see how to do it.
I have tried all the tips on Google and on here except for one which is largely in Tagalog which I don't understand!
I seem to be going round in circles and I will probably end up doing more harm than good. I believe it is possible to use Smart Bro with 11.10 but can anyone tell me how?
I have been using Ubuntu for a couple of years and I think it's great but I am not technically minded. Any help very gratefully accepted!
Andy

---

### Post by Script Warlock on 2012-05-22
plug and play ang smartbro sa ubuntu lalo na sa bagong release na 12.04.

---

### Post by strifehart on 2012-06-01
yes, plug and play lang ang mga modem stick natin d2, just go to connection settings or "Edit connection" setup mo lang ung Mobile Internet.

---

### Post by itagomo on 2012-08-06
hi andy, i hope you're still available to read this. you don't need to use 3rd party apps to connect to the Internet. You could try to look here:
[http://askubuntu.com/questions/141452/micromax-3g-mobile-internet-modem-not-being-detected/](http://askubuntu.com/questions/141452/micromax-3g-mobile-internet-modem-not-being-detected/)

that thread talks about Longcheer WM66a modem. if you have a different modem, just post it here and let's try to configure it.

---

### Post by kstella on 2012-08-30
I'm curious; there are a lot of new Smart Bro dongles (see [http://www1.smart.com.ph/bro/products/](http://www1.smart.com.ph/bro/products/)). Can anyone give feedback on which work or don't work? Or do they all work now with 12.04?

---

### Post by reneorense on 2012-09-07
tried most of them new ones and they work perfectly...

8)

---

### Post by josephuses626 on 2012-12-06
> **itagomo said:**
> hi andy, i hope you're still available to read this. you don't need to use 3rd party apps to connect to the Internet. You could try to look here:
[http://askubuntu.com/questions/141452/micromax-3g-mobile-internet-modem-not-being-detected/](http://askubuntu.com/questions/141452/micromax-3g-mobile-internet-modem-not-being-detected/)

that thread talks about Longcheer WM66a modem. if you have a different modem, just post it here and let's try to configure it.

I tried the steps in the link for WM66E modem but Ubuntu 12.04 still does not detect it. No "New Mobile Broadband" notification pops up. I wrote a follow up question here: [http://askubuntu.com/questions/226130/mobile-internet-modem-still-not-being-detected](http://askubuntu.com/questions/226130/mobile-internet-modem-still-not-being-detected)

---

### Post by wavm on 2013-02-19
my WM66e in 10.04 and also tried 12.04 works out of the box... 

just try to unmount and it will re-mount itself and poof...

^_^ :popcorn:

---

### Post by lianne_john07 on 2013-03-01
can you post the result before and after running the command below.
```

$ lsusb

```

---

### Post by mar4 on 2013-11-21
I'm facing the same problem on 12.04.

```

# lsusb
xxxxx
ID 1c9e:98ff OMEGA TECHNOLOGY
xxxxx

# usb-devices
xxxxxxx
S:  Manufacturer=USB Modem 
S:  Product=USB Modem
xxxxxxx

```

Any idea for solution?

---

### Post by dhotrum on 2014-08-28
This is an old thread but I see that it has not been resolved. I have the same problem. I need micro doors and the only way I can get Smart Bro to work is go into Doors and start smart Bro than reboot and go into Ubuntu 14.04 and it is there. Has anyone found a work around yet?

---

