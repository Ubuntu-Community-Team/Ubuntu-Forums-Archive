---
title: "How to install gtalk on ubuntu for gmail chat"
date: 2008-02-12
forum: New to Ubuntu
---

### Post by anbumanij on 2008-02-12
Hi frnds,

        Is there any gtalk application to chat in ubuntu.if so pls help me out

---

### Post by lnostdal on 2008-02-12
it's already installed by default in ubuntu .. you find it in the menus: Applications -> Internet -> Pidgin Internet Messenger

also see [http://www.google.com/support/talk/bin/answer.py?hl=en&answer=24073](http://www.google.com/support/talk/bin/answer.py?hl=en&answer=24073)

---

### Post by karthikbalaji on 2008-02-12
Hi,

Using pidgin cannot do voice chat. Only gtalk supports it :(.

If u want to do voice chat use skype.

Thanks,
Karthik.

---

### Post by mozetti on 2008-02-12
For voice chat you can use Tapioca. The project appears to be dead, but I used it in the past and voice chat worked fine.

---

### Post by SOULRiDER on 2008-02-12
This thread shouldnt be here!

---

### Post by deepclutch on 2008-04-25
empathy fails!tapioca does not even react!what next??? any gtalk VOIP client which is compatible with ESD?

---

### Post by Triscuit713 on 2008-04-27
There is an updated version of the Empathy client with voice enabled for Jingle/Gtalk users. You also must be
using Hardy.

[https://launchpad.net/~telepathy/+archive](https://launchpad.net/~telepathy/+archive)

Often time, I see people make suggestions that they haven't tried themselves. Well, I have tried this. It sort of works.

I've had two talks. The first lasted about 16 minutes, and I could hear the other person loud and clear. Unfortunately, my usb webcam mic (Logitech STX) wouldn't work. This is because Pulseaudio identifies the default mic as the mic input on the motherboard. The default mic can be changed by installing paudevchooser. I didn't discover this until today, though.

In the second talk I had, I disabled pulseaudio and had gstreamer send all audio through alsa instead. Therefore my mic worked, and we could hear each other. However, this only lasted for about 30 seconds before we each became silent again. I don't know if it's due to alsa, gstreamer, or something pulseaudio related that I forgot to disable.

I will try again tonight with pulseaudio output/input and see if results change.

Get the word out that working jingle audio exists. This project needs more testers as far as I can tell.

---

