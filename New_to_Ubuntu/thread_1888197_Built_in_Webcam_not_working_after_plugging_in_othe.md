---
title: "Built in Webcam not working after plugging in other Webcam"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by androssofer on 2011-11-28
so i hav a webcam built into my laptop, and it worked fine with ubuntu.

then i got a new webcam for my other ubuntu box, and tested it on the laptop to check it worked wit ubuntu and it did fine. so i unplugged it and turned the laptop off. 

then when i turned the laptop on again the built in webcam doesnt work anymore :-(

---

### Post by homemadejam on 2011-11-28
What program are you testing your webcam out in?
I had this same problem in the past, and I found out that when I plugged in my new web cam, it became the default.

If you're using Cheese, go to the preferences tab, and there's an option to select which camera. I don't know if this helps at all?

---

### Post by bluexrider on 2011-11-28
its going to look for the last web cam used. change the default settings you'll be fine

---

### Post by no2498 on 2011-11-29
if you have the fn key you may need to restart the cam with the keys

---

### Post by androssofer on 2011-11-30
i used cheese yeah, but it just says 'no device found' and i cant see a preference option anywer..

> if you have the fn key you may need to restart the cam with the keys

could you explain how to go about this?

---

### Post by no2498 on 2011-12-01
i do not have a lap top but i think its the fn+f4 keys at the same time
the light should come on
also open a terminal type dmesg click enter
after it stops click close now try cheese
for the settings open system/preferences multimedia systems selector now click video
is that the cam you use ?

---

### Post by androssofer on 2011-12-01
> **no2498 said:**
> i do not have a lap top but i think its the fn+f4 keys at the same time
the light should come on
also open a terminal type dmesg click enter
after it stops click close now try cheese
for the settings open system/preferences multimedia systems selector now click video
is that the cam you use ?

i ran dmesg then rebooted, and it works! Thanks no2498!

fn+f4 puts my laptop into hibernate... a scary thing to happen when ur pressing random keys... haha.

---

### Post by no2498 on 2011-12-02
glad it helped

---

