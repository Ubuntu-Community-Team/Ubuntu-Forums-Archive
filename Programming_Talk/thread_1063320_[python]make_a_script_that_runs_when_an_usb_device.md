---
title: "[python]make a script that runs when an usb device is plugged"
date: 2009-02-07
forum: Programming Talk
---

### Post by rlameiro on 2009-02-07
Hi. I messed around some time ago with python, did learn some basics, but I still have a lot ore to go.
Lets go to the real question.
I patched the alsa drivers to work with my edirol ua-4fx usb audio interface, but at the end there is a little problem, as stated in the thread, when the ua-4fx is connected, ubuntu don't load the drivers, so we need to run ```
sudo modprobe snd-usb-audio 
```
What I wanted is to know, how can I make an python script that detects this device and then load the drivers.
I also want to make an automated script that applies the patch as described at the thread, It will need to run as root (su) and also to wrap info from shell commands, like uname-r.
well all ideas are welcomed, but please, don't say that is better use bash, pearl, ruby, etc.. I don't want to learn another language, at least for now, I am a musician not a programmer;)

The Thread
[http://ubuntuforums.org/showthread.php?t=1043691]("http://ubuntuforums.org/showthread.php?t=1043691")

---

### Post by rlameiro on 2009-02-08
any idea?

---

### Post by eightmillion on 2009-02-08
> **rlameiro said:**
> any idea?

You should probably take a look at [udev.]("http://reactivated.net/writing_udev_rules.html")

---

### Post by rlameiro on 2009-02-08
> **eightmillion said:**
> You should probably take a look at [udev.]("http://reactivated.net/writing_udev_rules.html")

Thank you eightmillion. I was really this, I made it and it is working, without scripting it :)
If you go to the thread link I posted before you can see the result!
thank you!

---

