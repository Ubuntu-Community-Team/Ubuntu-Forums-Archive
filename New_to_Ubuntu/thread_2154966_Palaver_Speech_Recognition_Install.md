---
title: "Palaver Speech Recognition Install"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by robinduncan on 2013-06-16
Hi, I've been trying to install Palaver Speech Recognition on my laptop (which is on xubuntu 12.04, 32 bit) because I have chronic RSI and need something which will transcribe my speech so I can keep studying/working in the future. However, it's still not functioning properly.  I don't get the notification box opening once I press my hotkey, all I get is a microphone icon in the menu panel. It contains a brief menu, but I can't carry out any tasks. If I open a terminal in the Palaver folder and type ./hotkey I can do "open google.com" etc. It also responds to the vocal command "type: (whatever)", but that just makes the text appears in the terminal, in the middle of a mess of script, none of which is of much practical use.

I found out that Palaver uses notify-osd, which I believe is not included with xubuntu, so I installed it and unistalled notifyd. That didn't have any effect at all though. Does anyone have any suggestions? I know barely anything about this kind of stuff, this is the most ambitious thing I've ever done with Linux, but also probably the most important. If it doesn't work I'll probably have to get a new computer.

Thanks for any help!

---

### Post by Frogs Hair on 2013-06-16
Hi [COLOR=#000000]robinduncan.[/COLOR]

[COLOR=#000000]Getting a new computer may be a bit extreme at this point . To test the notify-osd installation copy paste and enter the following command in the terminal.  [/COLOR] ```
notify-send test


```If the installation was successful you will see notification with the word "test".

This may be of interest, but it is for Ubuntu. [http://www.muktware.com/5412/how-get-palaver-speech-recognition-work-ubuntu](http://www.muktware.com/5412/how-get-palaver-speech-recognition-work-ubuntu)

---

### Post by robinduncan on 2013-06-16
Thanks for that. The test was successful, but in terms of using Palaver, nothing seems to have changed. I'm thinking about uninstalling and re-installing to see if that changes anything...

ps. it is quite an old Toshiba I've got. My thinking was that the software just might not be up to it.

---

### Post by styxie on 2013-07-07
Same here, I also can't seem to get the notification, although I know for sure I've seen it before, on a different distro on the same box. Entering 'notify-send test' into the terminal does show me notification.

---

