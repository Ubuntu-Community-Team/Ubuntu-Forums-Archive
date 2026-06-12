---
title: "Asus Sonicmaster Subwoofer not working"
date: 2013-10-15
forum: New to Ubuntu
---

### Post by Stephen_Gibson on 2013-10-15
Hope you do no get this question a lot, if so I can't seem to find any posts anywhere, google gave me 2-3 things to do but no luck.

I am completely new to linux but so far everything is running the way I want it besides this damn sub woofer, I am using Ubuntu for java development and if I don't have music to listen to...my coding sucks :p

Anyway, anyone know how to fix this?

---

### Post by Stephen_Gibson on 2013-10-15
Oops, yeah I followed 1-2 guides from google and now I have no sound at all :D

[http://askubuntu.com/questions/189304/no-sound-from-external-subwoofer-sonic-master-on-an-asus-n76vm](http://askubuntu.com/questions/189304/no-sound-from-external-subwoofer-sonic-master-on-an-asus-n76vm)

Nothing shows in the output box!

Save me!!

EDIT: A guide also added another desktop enviroment called GNOME Fallback, logic screen is completely different now and I don;t like it :(

---

### Post by Stephen_Gibson on 2013-10-15
Well here is some info:

```
aplay -l
```
```
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC668 Analog [ALC668 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I followed the trouble shooting guide here [https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit#heading=h.xk2h8rqfyqzt](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit#heading=h.xk2h8rqfyqzt)

I used this command as stated:

```
echo "Sound cards recognized by the system:"; lspci -nn | grep --color=none '\[04[80][13]\]';
echo "Sound cards recognized by ALSA:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel modules: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done;
echo "Sound cards recognized by ALSA, and activated:"; lspci -nn | grep '\[04[80][13]\]' | while read line; do lspci -nnk | grep -A 3 '\[04[80][13]\]' | grep -e 'Kernel drivers in use: ..*' -e '\[04[80][13]\]' | grep --color=none -F "$line"; done

```

and got the following output:

```
Sound cards recognized by the system:00:03.0 Audio device [0403]: Intel Corporation Device [8086:0a0c] (rev 09)
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
Sound cards recognized by ALSA:
00:03.0 Audio device [0403]: Intel Corporation Device [8086:0a0c] (rev 09)
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
Sound cards recognized by ALSA, and activated:
00:03.0 Audio device [0403]: Intel Corporation Device [8086:0a0c] (rev 09)
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
```

---

