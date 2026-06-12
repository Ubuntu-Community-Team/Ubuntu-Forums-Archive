---
title: "First Install: How, What, Where do install my wifi driver"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by leotemp on 2008-04-29
Ok, my first linux install and its booting just fine, now i want to get wifi going (that makes sense to do first right?) and I cant for the life of me figure out how i even install the drivers to my card . I typed the command in the terminal to get my cards info but it wasn't listed. But my card is in the list of supported hardware, im such a newb thats its entirely possible that Im looking in the wrong place or just don't understand the process. Coming from a windows background i would normally download a driver go to hardware manager and then update the driver but when I look at the hardware manager in ubuntu it just says that I dont have any proprietary hardware installed.

Any help would be awesome.

---

### Post by Monicker on 2008-04-29
Please give us the results of this terminal command:

lspci -v

---

### Post by joshrobinson on 2008-04-29
> **leotemp said:**
> Ok, my first linux install and its booting just fine, now i want to get wifi going (that makes sense to do first right?) and I cant for the life of me figure out how i even install the drivers to my card . I typed the command in the terminal to get my cards info but it wasn't listed. But my card is in the list of supported hardware, im such a newb thats its entirely possible that Im looking in the wrong place or just don't understand the process. Coming from a windows background i would normally download a driver go to hardware manager and then update the driver but when I look at the hardware manager in ubuntu it just says that I dont have any proprietary hardware installed.

Any help would be awesome.

could you post the model of your card? or the output of
```
lspci
```

---

### Post by leotemp on 2008-04-29
It is a Trendnet TEW-421PC or 423PI i cant remember which, output of the command is to much to type but the part that pertains to my card is:

04:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

---

### Post by kesman on 2008-04-29
Have you checked system -> administration -> hardware drivers? Maybe it's there, hopefully.

---

### Post by leotemp on 2008-04-29
You know i think your right, everything i am reading tells me it is in there it just isnt apparent to my windows trained eyes, upon clicking everywhere on the screen i have found a dialog that is actually asking me for wifi info so i think im just lame, sorry all..

---

### Post by hyper_ch on 2008-04-29
either hardware runs out-of-the-box or it won't... if the later is the case, you normally will have quite some issues getting it to work ;) good that wifi works for you out of the box.

---

### Post by leotemp on 2008-04-29
yeah, its working as im getting rejected by my access point, i think i need some clarification if anyone wants to help, i have my WEP key but i don't understand the connect to wireless network dialog in ubuntu, on my AP im just using standard WEP security with an alpha numerical WEP key. under EAP method im not sure what to select as i don't need any of these options such as identity and password or anonymous identity.. i don't see where i would put the wep and everything im trying is telling me to F off which is awkward as normally my AP treats me with kindness and respect.

And FYI this is still easier then Windows as I had to spend the better part of a day pulling this card in and out of my machine like robot sex just to get XP to detect it, was brutal.

---

### Post by hyper_ch on 2008-04-29
well, just to make sure it works, disable WEP on the router... then try to connect with your wifi... if that works, then protect the router again... however if you want protection, don't use WEP... it can be cracked in a matter of minutes.

---

### Post by leotemp on 2008-04-29
I will do that now as i am not sure it is working now since i can put anything in the dialog with the same results, i only have WEP going to keep my one neighbors Xbox of my network just because i am mean >:)

---

### Post by leotemp on 2008-04-29
arrrg.. all i did was restart ubuntu and now it doesnt load the UI i just get terminal prompt "Build-shell (ash) 'help' for a list of built in commands." how the hell did this happen?

---

### Post by hyper_ch on 2008-04-29
no clue, but enter:

```

startx

```

---

### Post by leotemp on 2008-04-29
Weird, i restarted, booted to windows and then restarted again and now it is loading the ui... whatever.

I just tried to connect to my open network and it is still telling me i need a passphrase, maybe im clicking in the wrong area to properly connect to a wifi network, i am clicking right next to my user name in the upper right on the two monitors icon and then selecting "connect to 802.1x protected wired network" which seems kind of fishy. Is there a more appropriate place in the ui that perhaps lists available networks like in windows?

---

