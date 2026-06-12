---
title: "generic USB-phone not recognised ?"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by palloy on 2012-08-05
Lubuntu 12.04 doesn't seem to recognise my USB-phone.
I don't know whether these tests are any help:

QasMixer > Mixer Device > hw : card , shows 
Card 0: HDA Intel, VIA VT1708BCE
Card 1: C-Media USB Headphone, USB Mixer
which both look correct, but Mixer Device > shm : Socket, CTL shows
"Mixer device couldn't be opened"
Function: snd_hctl_open
Address: shm
Error: Invalid argument

GMerlin Alsamixer only displays VIA VT1708BCE
GMerlin Recorder allows me to select the input device USB Audio, but then stops responding.

Yate Client connects to my SIP service, but when I make a call I get
"Failed to open media channel(s)".

The device has been working correctly in Win 7.
Is there something in Lubuntu like Win's Device Manager where I can sort this out ?

---

### Post by levlaz on 2012-08-05
What are you trying to do with this phone? 

What kind of phone is it?

---

### Post by palloy on 2012-08-05
I am trying to use the USB-phone to make VoIP calls with Yate Client.

In Win 7 the device calls itself C-media USB Headphone Set and uses standard M$ drivers. It is a simple device, having no display and no keyboard.

---

### Post by anewguy on 2012-08-05
A simple search on the net turned this up - yes, it's for 9.xx, and yes it's for kubuntu, but it won't matter.

[http://ubuntuforums.org/showthread.php?t=1184923&highlight=C-Media]("http://ubuntuforums.org/showthread.php?t=1184923&highlight=C-Media")

The only difference I can see in the first post of that thread is that you need to change the lines that start with:

sudo kate ........

to:

gksudo gedit ........

for the standard download of Ubuntu.

If you have questions, please post back.

Also, please let us know if this does work and then mark the thread as solved.

Of course, if by chance it doesn't work, post back.

---

### Post by palloy on 2012-08-05
That looked promising - the line in /etc/modprobe.d/alsa-base.conf was there, so I commented it out and rebooted. Started Yate, registered with SIP server OK, made a call, it connected, but got the same "Failed to open media channel(s)" twice and automatically hung up. No sounds on punching in the numbers, no ringing out sounds.

GMerlin Mixer now sees VIA and the USB Mixer with PCM Play and Mic Rec sliders, which is a step forward.
I also have QasMixer and PulseAudio Volume Control installed (is that OK?)
I don't pretend to understand all the settings, but I think I have tried everything.

Ideally I would like the following arrangement, (written in an invented language). Is it going to be possible to arrange this, or shouldn't I bother ?

```
System-Sounds off ;
while (true) 
{ if (USB-phone is plugged in) 
    { speakers(mute) ; 
      line-in(mute) ; 
      Yate.in(USB-phone.mic(50%)) ; 
      Yate.out(USB-phone.speaker(50%) ; 
    }
  else
    if (Sound application running)
      { line-in(mute) ; 
        application.out(speakers(50%)) ; 
      }
    else 
      { auto.in(line-in(50%)) ; # carries sound from external satellite decoder box
        auto.out(speakers(50%)) ;
      }
}
```

---

### Post by anewguy on 2012-08-06
I believe the first can be done via writing a new rule in the udev rules specifying a shell script and/or program to run when the given USB vendor:product id is plugged in.  I don't know if there is a way to detect that the device was unplugged and reverse it - the udev rules execute in this case when the device is plugged in, not when it is unplugged.

The last 2?  I'm not positive, but I think that would require a program running as a daemon to detect and make the changes. I won't go into a more detailed outline of what you want to do until I do more research and/or someone else comes up with something.

---

### Post by palloy on 2012-08-06
I decided to stick with Gmerlin Mixer and to uninstall PulseAudio and QasMixer, and reboot, to see if that made any difference. It didn't. 

Nowhere in Yate VoIP Client does it give you the opportunity to choose the devices (unlike X-lite in Win7), so I thought I would try Ekiga. That does allow that, (Edit > Preferences > Audio > Devices) and C-media headset mic and speaker was on the list (not the default). Filled in the account details and it registered OK. Made a call out and it works ! :P

So the problem was probably with Yate - I suppose it couldn't pick up a default microphone, because there wasn't one, and that's as far as it got.

Ekiga +1

Thank you everybody for your help.

---

