---
title: "Microphone Trouble"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-05-15
When I plug in my microphone i go to sound recorder and talk but i cant here anything and on Skype my friends cant here me either..any help?

---

### Post by hermes0710 on 2008-05-16
Any case you have the mic muted? (Double click the speaker icon in the system tray to see the volume levels of your devices. In case the mic is not listed then close the window, right click the same icon and select preferences. You will presented with a list of devices that are you cards components. Tick the mic in order to be shown in the mixer properties.)

---

### Post by pedro_orange on 2008-05-16
```
alsamixer
```

In terminal. Turn stuff up.
The tab key will show you more volume settings; you can also scroll along. 
Enable capture etc and then try it.

(You may need to close other audio apps like Rhythmbox)

---

