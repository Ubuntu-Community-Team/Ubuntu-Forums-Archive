---
title: "rythmnbox, clementine won't play cds"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by stiggowitz on 2012-06-22
Hi. Now that I have sound I can play wav files but while the cds will load on R/box and clementine, when I mouse click the track or press the play arrow the track does nothing. what's up?
 
s:)

---

### Post by jmfal on 2012-06-22
Start rhythnbox and play a wav or something that you know works
Then click on the speaker icon (top toolbar right side)> sound settings > Applications
 
You should see rhythmbox listed
try to play a cd  rhythmbox may disappear or become muted, try to unmute it
If its not working opena terminal an try these
```
sudo apt-get  --purge rhythmbox
             sudo apt-get autoclean
             sudo apt-get install rhythmbox
```

Enter each command separately  and make sure rhythmbox is spelled correctly

---

### Post by stiggowitz on 2012-06-23
Jmfal wrote this solution.
"sudo apt-get  --purge rhythmbox
             sudo apt-get autoclean
             sudo apt-get install rhythmbox"
 
I figured out the code and managed to purge rhythmbox.
How do I get it back as I can't find it in software?
 
s:)

---

### Post by jmfal on 2012-06-23
open a terminal and type:

```
  rythmbox 
```
and press enter

---

### Post by jmfal on 2012-06-23
I'm sorry Mr. Stiggowitz I meant to add this to my last post:

If rythmbox does not open try this in a terminal:

```
sudo apt-get install rythmbox     
```

If you still cannot play CD's  ina terminal tyoe:
```
 alsamixer      
```

Press F5 and use the left/right arrows on your keyboard an navigate to CD  volume control,  if it is muted you will see "MM" in the small box below the volume meter.
Press "M" or  "m"  to unmute it and use the up arrow to increase the volume

---

