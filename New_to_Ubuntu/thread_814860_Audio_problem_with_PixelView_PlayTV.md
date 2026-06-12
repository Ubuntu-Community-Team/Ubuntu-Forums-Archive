---
title: "Audio problem with PixelView PlayTV"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by supta on 2008-06-01
I have Pixelview PlayTV with cx2388x chip.

I can do channel tuning and get image and sound with TVTime. The problem is when I close TVTime (Esc or Q), the sound from TV station is still on. It's like running in the background. I'm using loopback cable to get sound.

Any hint would be very appreciated. Thanks.

---

### Post by trevelyan on 2008-06-02
I have this same problem. and i use a much TV card. and that one uses the saa7134 chip. so if your card uses that same chip, as far as i know, you have two options:

1) mute "line in" in the volume control.

this is the simplest solution i found. the problem i had with this was that when i use skype.. the person i talk to hears the TV more than they can hear me. which means that the device is still on (obiously, since you only muted it). so if you use skype or something like that, this will be a problem.

2) open the terminal (applications > accessories > terminal) and type the following pressing enter after each line.

   sudo rmmod saa7134_alsa
   sudo rmmod saa7134

that takes care of the sound and if you talk on skype everything works normally..
but if you wanna watch TV again you have to open the terminal again and type:

sudo modprobe saa7134

after that you run TVtime and it works as normal.

if your card uses a different chip you can still try option 1. and maybe option 2 as well but replacing saa7134 with the correct module for your card.
i hope this helps or at least gives you a clue. :)

---

### Post by supta on 2008-06-02
As I mentioned in my first post, my card using cx2388x chip (cx88xx).

Actually, I've already muted 'Line in' to 'stop' the sound. But I think that doesn't solve my problem. There could be some way to do this properly.

I think I wouldn't do option 2. Insert/remove module everytime I want to start/stop TVTime is really not a good idea.

Anyway thanks for your sharing.

---

### Post by trevelyan on 2008-06-02
well.. it sounds like there should be a better way. and i have searched for it and found nothing. ive been doing the module thing for about a week and everything is fine. maybe there is a way to implement the commands in the TVtime program. or maybe write a script in a file or something. i dont know.. let me know if you, or anyone finds a better solution.

EDIT:
instead of:

sudo rmmod saa7134_alsa
sudo rmmod saa7134

you could just do:

sudo rmmod saa7134_alsa && sudo rmmod saa7134

in one single command. i dont know.. ill look for a better way to do this.

---

