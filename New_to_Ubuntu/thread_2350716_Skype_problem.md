---
title: "Skype problem"
date: 2017-01-27
forum: New to Ubuntu
---

### Post by ferfykins on 2017-01-27
Skype runs fine, video works as well....i can hear other people in video chat, but they cannot hear me

anyone know how to fix this?

---

### Post by Perfect Storm on 2017-01-27
In the input tab make sure you are not muted.

---

### Post by ferfykins on 2017-01-27
No, wasn't muted.... also, it's weird, on these forums, when i quote in reply, i can't use spacebar, for some reason....

if i reply with a quote, taht is

---

### Post by Perfect Storm on 2017-01-27
Try:
```
sudo apt-get install pavucontrol
pavucontrol
```

change to built-in 'Audio Analog Stereo' inplayback and recording.

---

### Post by ferfykins on 2017-01-27
tried that, it has the right input using microphone
but people still can't hear me :'(


could it be missing drivers or some other software i need?

---

### Post by Perfect Storm on 2017-01-27
did you tried restarting pulseaudio after the change of pavucontrol:
```
killall pulseaudio
```

---

### Post by ferfykins on 2017-01-27
I tried killall pulseaudio

now i have no sound whatsoever... or video


I should of said i'm completely new to linux...
^relogged, now sound/video are ok... but still no1 can hear me on skype >_<

---

### Post by Perfect Storm on 2017-01-27
A restart should fix it, are you running 64-bit?

If so you need:
```
sudo apt-get install libpulse0:i386
```

---

### Post by ferfykins on 2017-01-27
I'm sorry when you said input tab, is taht on skype or ubuntu? cuz i don't see any tab named "input".....


also libpulse was already installed

---

### Post by ferfykins on 2017-01-27
I figured it out, thanks guys!

---

### Post by wildmanne39 on 2017-01-27
Please share with the community how you solved this issue and use thread tools at the top of the thread to mark it solved.
Thanks

---

### Post by ferfykins on 2017-01-27
Fixed it using ubuntu audio settings :)
adjusting microphone volume

---

### Post by zeca77 on 2017-01-29
how did you do it? I have the same problem as you

---

