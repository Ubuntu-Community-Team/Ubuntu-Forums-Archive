---
title: "No sound after second reboot"
date: 2014-09-10
forum: New to Ubuntu
---

### Post by mohi2 on 2014-09-10
I'm a linux newbie!
Card - [B]HDA Intel PCH
[/B]Chip - **Intel CougarPoint HDMI**

So I am having the sound problem like everyone else. There's only Dummy Output in sound settings. I've got a fix actually but it's not permanent. 
Here's what I do.

First I remove alsa-base and pulseaudio with this command
[B]
sudo apt-get remove --purge alsa-base pulseaudio


[/B]then re-install it with this command

[B]sudo apt-get install alsa-base pulseaudio

[/B]

Removal of alsa-base and pulseaudio somehow always uninstalls my Unity Control Center so I install it as well.

[B]sudo apt-get install unity-control-center

[/B]
Then force reload alsa with this

[B]sudo alsa force-reload
[/B]

Reboot the machine and voila, I get the sound back and sound setting starts showing Speakers instead of Dummy Output. 
No problem regarding internal external mic, speakers, headphones whatsoever.

But when I restart the machine once again, I'm back to square one.

Why it only works after first reboot then go back to Dummy Output. :confused: 
What am I supposed to do? It's been two days already and I haven't found a solution yet.
Please help!

---

### Post by danfreedom232 on 2015-02-08
I had the same problem!
but mine took out a lot more than unity-control-center! (I am using ubuntu 14.10)

I had to re-install all these:

sudo apt-get install
alsa-base 
indicator-sound 
libcanberra-pulse 
pulseaudio
pulseaudio-module-bluetooth 
pulseaudio-module-x11
qtdeclarative5-ubuntu-telephony0.1 
telephony-service 
tone-generator
ubuntu-desktop 
unity-control-center 
unity-control-center-signon

---

