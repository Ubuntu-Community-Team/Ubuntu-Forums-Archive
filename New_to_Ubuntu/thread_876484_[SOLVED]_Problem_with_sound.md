---
title: "[SOLVED] Problem with sound"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by AnonUK on 2008-07-31
Hey, sometimes i hear no sound on ubuntu

example: sometimes i can hear the sound on youtube videos, and other internet streaming sites however i cannot hear any sound on  movie maker and vlc player.

then, other times i can hear music on movie maker and vlc player and not youtube.. the vids either stop after 2 seconds or i hear no sound at all

any help is greatly appreciated thanks

awesome thanks it worked!

---

### Post by scragar on 2008-07-31
pulse audio is a bit annoying, while it's running it only supports 1 stream, however it is being slowly upgraded and should in future support more than 1 things using audio at the same time.```
killall pulseaudio
```
will act as a temp solution, but pulseaudio starts up again at every restart.

---

### Post by RomeReactor on 2008-07-31
Hi. Try installing **libflashsupport**; you can find it in Synaptic, or to install it form the terminal:
```
sudo aptitude install libflashsupport
```

Also, go to 'System->Preferences->Sound' and on the 'Devices' tab set all the dropdown menus to 'PulseAudio Sound Server'.

---

