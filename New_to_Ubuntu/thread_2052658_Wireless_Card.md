---
title: "Wireless Card?"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by TheMTtakeover on 2012-09-03
I am curious as to whether or not this computer has a wireless card in it. I attached a readout from the terminal. Any help is greatly apperciated.
 
[IMG]http://i250.photobucket.com/albums/gg261/TheMTtakeover/Screenshotfrom2012-09-0312_21_27.png[/IMG]

---

### Post by DogMatix on 2012-09-03
In a terminal 

```
ifconfig
```

look for wlan0

---

### Post by NikTh on 2012-09-03
Hello , 

usually wireless indicated from **Network Controller** . 
In your results the is not . Only Ethernet Controller is present. 

BUT , 

I have seen cases where the lspci command not showed the Network Controller cuz it was disabled in BIOS. 

So check out the BIOS config page for WiFI , or PCI Network .. etc 

Also give the results of ```
lsusb
``` 

It is not necessary to post images (screenshots) , just copy and paste the results from terminal here...
BUT
**you must put the results between ```
 brackets so can be readable .**

[noparse][code]The Results Here
```[/noparse]

Thanks

---

### Post by kostkon on 2012-09-03
Also, give
```
rfkill list
```
and post its output here.

---

### Post by TheMTtakeover on 2012-09-03
Sorry, The reason I am posting screenshots is because that computer that I am wondering about doesn't have internet connection as I have no wired connection to my room only wifi so it is easiest for me to just screenshot it and then throw it on a usb and move it to my computer.
 
ipconfig brings up this (I didn't see WLAN but maybe I missed it?)
[IMG]http://i250.photobucket.com/albums/gg261/TheMTtakeover/ipconfig.png[/IMG]
 
lsusb brings up this:
[IMG]http://i250.photobucket.com/albums/gg261/TheMTtakeover/lsusb.png[/IMG]
 
and RFkill list didn't bring up any results. I apperciate the help guys.

---

### Post by kostkon on 2012-09-03
OK.

Is this a desktop PC?

---

### Post by anewguy on 2012-09-03
None of your lists actually show a wireless network adapter.  If you think there is supposed to be a wireless adapter, post back the make, model, etc., of your PC and we can look to see what's normally included with that model.

---

### Post by TheMTtakeover on 2012-09-03
Yeah desktop pc. It's actually not my computer. But they couldn't get their computer to connect to their wifi and so I was thinking that it didn't have a wireless card. And you guys seem to agree as well. So I will let them know that is why.

---

