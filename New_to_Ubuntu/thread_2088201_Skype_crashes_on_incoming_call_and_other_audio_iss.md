---
title: "Skype crashes on incoming call and other audio issues"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by anirbanghosh on 2012-11-25
I am using Xubuntu 12.10. I have installed the latest Skype. But the weird thing is that Skype takes exclusive control of the audio in the system. 

1. When I am using Skype, I cannot play any other audio in system.
2. When I am using any audio in the system, Skype audio doesn't work.
3. When someone is calling me in skype, Skype crashes when I receive it. This because I   
     think the event sound mechanism interferes with Skype audio playback.

This did not happen in Ubuntu 12.10. Any help would be greatly appreciated.

---

### Post by personalpc on 2012-11-25
> **ireneshusband said:**
> I have managed to work around the problem, at least this once, using the following procedure. Most likely some of the following steps aren't necessary, so you may be able to simplify it somewhat:

[LIST=1]
[*]Turn PulseAudio autospawn off, normally: $ echo "autospawn = no" > ~/.pulse/client.conf
[*]Kill PulseAudio: $ killall pulseaudio
[*]Shut down and restart Skype
[*]Go to the Skype sound device options, where your devices should now be exposed; Choose something.
[*]Shut down Skype
[*]Turn PulseAudio autospawn back on: $ echo "autospawn = yes" > ~/.pulse/client.conf
[*]Relaunch PulseAudio: $ pulseaudio -D
[*]Launch Skype
[*]Edit and test Skype sound device preferences
[/LIST]

that should do it

---

### Post by anirbanghosh on 2012-11-25
Tried but again it says the same thing "***Problem with audio playback***". I have set Speakers and Ringing options to ***pulse***. 

I tested this by playing a MP3 in Movie Player.

Any help please.

---

