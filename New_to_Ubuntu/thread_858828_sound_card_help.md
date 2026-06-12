---
title: "sound card help"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by coolman121 on 2008-07-13
i have an laptop (acer extensa 3000) and sound card which is great but with drivers from ubuntu makes it less than its potential i was wondering if there is any way to get driver working or get a better one????

---

### Post by tuxxy on 2008-07-14
Did you try the sound options like ALSA mixer to increase the volume?  my sound is better in Ubuntu!

---

### Post by coolman121 on 2008-07-14
yes kinda obvious .... but driver is barely sustainable and sound level .. is fine but quality is poor ........ UBUNTU Rules

---

### Post by vikramaditya on 2008-07-14
Did you install a sound card yourself?  If so, any onboard sound on your mobo may have to be disabled in the bios before the linux drivers can work properly.

---

### Post by Canis familiaris on 2008-07-14
Which model of Sound card you use?

```
lspci | grep Audio
```

Also which player do you use or rather which engine? 
In my experience Xine performs much better than gstreamer.

---

### Post by coolman121 on 2008-07-14
and no i didnt install my own sound card ... it is stock intel and i use internet plyers to vlc ect.......

---

