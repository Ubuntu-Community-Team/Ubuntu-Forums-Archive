---
title: "unable to hear songs even when bluetooth headset connected"
date: 2012-09-20
forum: New to Ubuntu
---

### Post by Harsh Beria on 2012-09-20
I had paired my bluetooth headset(BH-503) and it shows paired and whenever I wanted to listen songs through the headset, I used to go to sound settings and chose BH-503 to listen. But just for fun I switched off the settings in BH-503(there were three options there regarding the sound quality and the third was switch off) and now its gone from the sound settings and I'm unable to get it back. Plz help as I am very new to ubuntu

---

### Post by daslinkard on 2012-09-21
Try this and see if you are able to get your bluetooth working again....

[LIST=1]
[*]Fire up Ubuntu as normal.
[*] Plug in or enable your Bluetooth adapter. Your Bluetooth adapter  will be automatically detected and drivers loaded - there is nothing for  you to do manually here.
[*]Turn on your Bluetooth headset.
[*]Switch your headset into pairing mode (refer to your headset's manual).
[*]While the headset is in pairing mode, left click the Bluetooth icon  in your system tray and choose "Setup new device" from the menu. Follow  the wizard prompts to seek out and pair your headset.
[*]Once paried, open a terminal, and type in the following:
 	Code:
 	$ hcitool scan
[*]Your PC will now scan for local Bluetooth devices and your headset  should appear in the resulting list after a few seconds (along with  anyone's Bluetooth-enabled mobile phones that are in range).
[/LIST]

---

### Post by Harsh Beria on 2012-10-04
The solution is not working. After pairing when I typed hcitool scan in terminal, it didn't list my bluetooth device(BH-503).

I am pasting a screenshot of the actual problem. Below Speakers earlier BH-503 also used to appear and whenever I had to play a song using my bluetooth BH-503, I used to connect to it and then in the sounds setting used to choose BH-503. But now it no longer appears and even when I pair my device it gets paired and shows "connected" in bluetooth panel but still I am not able to hear songs through it. Please help!

---

### Post by Harsh Beria on 2012-10-06
Please someone help me out!

---

