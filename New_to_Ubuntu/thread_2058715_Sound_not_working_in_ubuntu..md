---
title: "Sound not working in ubuntu."
date: 2012-09-16
forum: New to Ubuntu
---

### Post by Luigi2012SM64DS on 2012-09-16
I can't get sound to work! my laptop has an ATI IXP SND-400 sound card and no matter what i try i can't get it to work. if i have to do other things to make it work please let me know. and btw i can't get it to work in any other linux distro.

---

### Post by Luigi2012SM64DS on 2012-09-16
Bump?

---

### Post by Shadius on 2012-09-16
What have you tried?

I don't know if this will work for you but it did for me. 

Do this in Terminal:
```
sudo alsa force-reload
```

---

### Post by Luigi2012SM64DS on 2012-09-16
> **Shadius said:**
> What have you tried?

I don't know if this will work for you but it did for me. 

Do this in Terminal:
```
sudo alsa force-reload
```
that didn't work
i also tried blacklisting the modem (following another thread) and that didn't work either

---

### Post by Hadaka on 2012-09-16
Hi, at terminal enter alsamixer

in the upper left hand corner it will display your sound chip,
post back what you find please.

also have you clicked ..system...sound...and selected your sound card??

thanks.

---

### Post by Luigi2012SM64DS on 2012-09-16
> **Hadaka said:**
> Hi, at terminal enter alsamixer

in the upper left hand corner it will display your sound chip,
post back what you find please.

also have you clicked ..system...sound...and selected your sound card??

thanks.
Card: ATI IXP                                        F1:  Help               &#9474;
&#9474; Chip: Conexant Cx20468-31

---

### Post by Hadaka on 2012-09-16
Hi, ok, might have a possible fix, is your computer a desktop or laptop?
and what model...dell,hp,asus???

---

### Post by Luigi2012SM64DS on 2012-09-16
> **Hadaka said:**
> Hi, ok, might have a possible fix, is your computer a desktop or laptop?
and what model...dell,hp,asus???
Laptop
Emachines MX4624 (Unknown Laptop)

---

### Post by Hadaka on 2012-09-16
Hi, try this option;

```
 gedit /etc/modprobe.d/alsa-base.conf
#add this line to the end of the file

options snd-hda-intel model=laptop

```

---

### Post by Steve R. on 2012-09-16
I have NO knowledge as to whether this will help, but in my "*No Sound*" case, the issue was resolved by installing the GNOME ASLA Mixer from the Synaptic Program Manager. [Click on this link to see my post]("http://ubuntuforums.org/showpost.php?p=11416859&postcount=5").  [Post #7]("http://ubuntuforums.org/showpost.php?p=11419600&postcount=7") has a screen shot. My post is two years old now, and my "*No Sound*" issue has not reappeared when updating UBUNTU.

---

### Post by Luigi2012SM64DS on 2012-09-16
> **Steve R. said:**
> I have NO knowledge as to whether this will help, but in my "*No Sound*" case, the issue was resolved by installing the GNOME ASLA Mixer from the Synaptic Program Manager. [Click on this link to see my post]("http://ubuntuforums.org/showpost.php?p=11416859&postcount=5").  [Post #7]("http://ubuntuforums.org/showpost.php?p=11419600&postcount=7") has a screen shot. My post is two years old now, and my "*No Sound*" issue has not reappeared when updating UBUNTU.
I saw something saying external amplifier was enabled. i enabled it and it worked:lolflag:
THANK YOU SO MUCH!!!!!!!!!!!!!!!!!!

---

