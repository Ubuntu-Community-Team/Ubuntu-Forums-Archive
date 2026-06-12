---
title: "Can't connect to wifi through my terminal."
date: 2011-11-25
forum: New to Ubuntu
---

### Post by Alexalad on 2011-11-25
I recently lost my gui due to my accidental removal of the xorg package. So I was trying to connect to my wifi through the terminal using the command:
'sudo iwconfig wlan0 essid Fishtank key s:XXXXXXXXXX'

I scanned beforehand, and I checked the spelling and capitalization twice, and I know everything is right. Unfortunately, it just output:

Error for wireless request "Set Encode" (8B2A)  :
     SET failed on device wlan0  ;  Invalid argument.


I was hoping someone could tell me what this means, or where I messed up, or if its fixable. I haven't had a gui for 4 days, now and i'm kinda desperate. Thanks in advance.

---

### Post by scarleo on 2011-11-26
Hmm, are you sure it is 'key s:your_key'? I remember it as just 'key your_key'. You could try that. Or maybe just set the router to accept connections without a password, but don't forget to change it to a secure state again when you have connected.

---

### Post by Alexalad on 2011-11-26
Well, I get the same output from either method.

---

