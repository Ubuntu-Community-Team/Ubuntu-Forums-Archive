---
title: "My Sound just died..."
date: 2008-07-11
forum: New to Ubuntu
---

### Post by parakeets11 on 2008-07-11
Ok, so yesterday I spent about 2 hours trying to get Youtube videos to play with sound and that failed miserably.  I was listening to music and talking to friends untill i turn it off.  I turn it on the next day, and i'm greeted with the drums and I log in.  Once in, there is no sound.  My music will not play either.  I remember that i downloaded alsa-oss drivers and created some new config files according to the how tos.  I need a lot of help and I'm linux stupid.

---

### Post by ChameleonDave on 2008-07-11
Give this page a try: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by parakeets11 on 2008-07-12
I managed to get music to play, but my alsa sound is broken.
As to the troubleshooting, I get this when typing aplay -l
```
**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:1589:(snd_config_load1) _toplevel_:52:61:Unexpected char
ALSA lib conf.c:2850:(snd_config_hook_load) /home/daniel/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2714:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3079:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:214: control open (0): Invalid argument

```

Any help?

---

### Post by parakeets11 on 2008-07-12
Never Mind, I fixed it. Thanks for the help though =P

---

### Post by ChameleonDave on 2008-07-12
Have you continued running through the troubleshooting guide?

---

### Post by parakeets11 on 2008-07-16
I restarted, it all works now. Thanks for your help! A+ for you.

---

