---
title: "Network Manager not accepting my password for wpa 2 network"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by brianedwardjarvis on 2008-09-14
(ubuntu 8.04) I'm having trouble connecting to the wpa 2 encrypted network in my apartment. I'm trying with 2 different computers with different wireless cards (one is internal, the other is an external card). I'm using the gnome network manager to try and connect to my network and it asks me for my password (which i'm assuming is my security key that all my other computers use to connect to the network). I enter the password, then i get the animation in the panel that says it's "attempting to join the wireless network..." Then i'm asked for my password again, and it continues the process all over again. I am able to connect to networks without passwords. I've been reading through all sorts of forums and attempted multiple "solutions" but to no avail. I'm a knewbee so please don't assume much about my ability level, i'll need easy to follow instructions. Just let me know which information you want me to supply, and I'll supply it. Thanks!

brian

---

### Post by aloshbennett on 2008-09-14
Is the encrytpion for the router just wpa2 or wap2+aes or something?

---

### Post by brianedwardjarvis on 2008-09-15
Well the router's box says it supports  "wpa or wpa2", and my vista computers on the same network say it's security type is "wpa2-personal" and the encryption type is "AES". Thanks for responding so quickly too.

-brian

---

### Post by aloshbennett on 2008-09-15
So then when you connect, select AES from the 'Type' dropdown.

---

### Post by brianedwardjarvis on 2008-09-15
Both of my computers do not have an AES option. The computer i've been experimenting on has only one option which is "WPA & WPA2 Personal" and the computer i didn't mess with only has these options "WPA Personal", "WPA2 Personal", and "LEAP". 

-brian

---

### Post by aloshbennett on 2008-09-15
Thats the 'Wireless Security' thingie. There's a 'Type' thingie below with options: automatic, aes-ccmp and tkip as options.

---

### Post by brianedwardjarvis on 2008-09-15
Okay, One of the computers connected and it works great! So 20 hugs and kisses for you, not necessarily from me, but from whomever you would actually want 20 hugs and kisses from. For some reason the computer that worked only connected when i set it to TKIP, but I don't know why. The other computer doesn't have the "type" drop down menu (the picture i attached shows what it does show). The picture comes from the computer that i've been messing with, so i'm sure i made some mistake by installing wicd, which uninstalled the gnome network manager, then i uninstalled wicd and re-installed the gnome network manager. The computer that now works is using nm-applet 0.6.6 and the one that isn't working is using nm-applet 0.7.0. Do you think it's not working because of the newer version? Again thanks so much for helping get the one computer to work. Any suggestions for the non-working one??

-brian

[ATTACH]85284[/ATTACH]

---

