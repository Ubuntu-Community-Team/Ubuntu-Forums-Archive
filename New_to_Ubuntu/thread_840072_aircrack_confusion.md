---
title: "aircrack confusion"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by UIIIU on 2008-06-25
Im new to ubuntu in fact the first time i used it was yesterday.  I was just googling different linux apps and aircrack really caught my eye, i thought it would be fun to fool around with, but i cant figure out how to use it.  I downloaded "aircrack-ng_1.0~beta1-1_i386.deb" and it said i successfully installed it but i have no clue how to go about running it

---

### Post by gtdaqua on 2008-06-25
If ever in doubt about the app installed, goto terminal and type "air" and press tab button. That will try to autocomplete the ambiguous command. Or open the start menu and browse through "the folders to find them.

---

### Post by UIIIU on 2008-06-25
i tried that out and it did nothing does that mean the app is not installed?

---

### Post by Fedz on 2008-06-25
Not sure myself how to work it but, I found their website: [Aircrack - ng](http://www.aircrack-ng.org) a good read :-)

---

### Post by plucky on 2008-06-25
Try this thread for [howto Aircrack](http://ubuntuforums.org/showthread.php?t=528276&highlight=aircrack)

This worked very well to crack my WEP encryption and made me change to WPA very quickly.That was on 7.10,haven't tried it on 8.04.

Enjoy.

---

### Post by whitethorn on 2008-06-25
I tried it out b4 in 7.10, and it worked pretty well.  Can't get into monitor mode in Hardy. 
If I remember correctly, you first have to set your wireless card to monitor using

sudo airmon-ng start [wireless card notation eth0, wlan0*]   

* you can find out what your network card is called by running ifconfig

Next you have to start capturing packets using aerodump.  Don't remember how that went, just type aerodump --help and it'll give you the options you need. You can set it to listen on a specific channel or listen to a certain router. There's also another tool with the aircrack suite that'll let you inject captured packages into the stream to force more traffic. Just can't remember what's it's called

Once you've collected enough IVs (for WEP encryption)  or for WPA you need to capture a handshake or two. WPA2 is pretty much impossible. 

and then you need to use aircrack-ng to deencrypt either the file where you stored the IVs, or for WPA you need to use a dictionary file to decrypt the key (brute force) you can find dictionary files on the net.  

don't forget to turn your network back from monitor mode using

airmon-ng stop [interface]

This should only be used to test your own network.

---

