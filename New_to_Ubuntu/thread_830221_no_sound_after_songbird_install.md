---
title: "no sound after songbird install"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by cjnkns on 2008-06-15
I recently downloaded songbird and I getting no sound when playing (trying to)play songs. Anyone have any suggestions on how to fix this?

Thanks,

---

### Post by Happy_Man on 2008-06-15
If you have something else that uses sound (eg another media player, Flash, etc.) close that and then try. For some reason, PulseAudio (Ubuntu's sound engine) doesn't like it if there are more than one application using sound at the same time.

---

### Post by cjnkns on 2008-06-15
Hi thanks for the reply - 

I did figure out that Songbird on my linux lappy does work.
It just doesn't want to play the songs I try to import from my iTunes library.
The songs load in the filter panes but no sound...
I had a NiN mp3 that was not part of the iTunes library and it works just fine?

Not sure what the deal is here.

---

### Post by waspbr on 2008-06-15
I doubt songbird has done anything significant to your computer, what you can do is go to preferences>multimedia system selector and pick the appropriate system, use the test button. 

(if that is not enables right click on the "start menu" (ubuntu logo)  and clck on edit menu, then go to preferences and enable the multimedia system selector)

Also check if anything may be muted in the sound mixer.


UPDATE...

ah itunes... try playing them and amarok (go to synaptic)  or rhythmbox

---

### Post by cjnkns on 2008-06-15
iTunes songs do work in Banshee and/or Rythmbox but I noticed on my Windows box that the m4p songs worked in Songbird so I was hoping I could get them to play on my linux box too without having to convert them. I assumed that if Songbird on Windows could play the m4p songs then so could Songbird on Linux. ...

---

### Post by waspbr on 2008-06-16
In principle they should, actually mine does...soooo, there may be something not well configure in songbird... reinstalling songbird may be an option....

---

