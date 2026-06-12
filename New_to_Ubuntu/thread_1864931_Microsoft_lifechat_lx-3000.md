---
title: "Microsoft lifechat lx-3000"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by ajaykumar.b on 2011-10-19
[SIZE=3]Hi

I have Microsoft lifechat [/SIZE][SIZE=3] Lx-3000.It works fine. when I add a line in a file.I got solution from the post
[http://ubuntuforums.org/showthread.php?t=1223561](http://ubuntuforums.org/showthread.php?t=1223561).
But when I add that line to /etc/modprob.d/blacklist.conf , my speakers are not working.I have to comment the line and then restart my machine to make them  work.
Can anyone help me to switch  to headset and speakers without restarting the machine.
I am using kubuntu 11.10.

Thank you 
Ajay

[/SIZE]

---

### Post by Parsley72 on 2012-03-25
The blacklist method is a bit like using a sledgehammer to crack a  walnut - it stops the snd_hda_intel module being loaded, which is why if  you unplug the headphones you won't hear anything.

I've found a better method here:
[http://superuser.com/questions/172514/alsa-usb-audio-hotplug](http://superuser.com/questions/172514/alsa-usb-audio-hotplug)

By editing the file ```
/etc/modprobe.d/alsa-base.conf
``` you can change the relative preferences of the USB audio:
```
options snd_usb_audio index=-1
options snd_hda_intel index=-2

```This works fine for me in Ubuntu 11.10 with KDE (although I had  to turn off the notifications from KDE every time I unplugged).

---

