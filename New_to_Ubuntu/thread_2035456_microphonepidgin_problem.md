---
title: "microphone/pidgin problem"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by bekirs on 2012-07-30
Hi,

I have xubuntu 12.04, installed on my HP 635.
Normally the built-in microphone works fine with **Skype 4.0** but in **Pidgin Internet Messenger**, the audio call option is not activated. Then if I make an audio call by logging in **imo.im** webpage, I hear the other person but he doesn't hear me. And if I go back to **Skype** for a test call, the microphone is not functioning properly there as well. To recover it, I have to reboot the system each time.

Do you have any recommendation for that problem?

Bekir

---

### Post by levlaz on 2012-07-30
> **bekirs said:**
> Hi,

I have xubuntu 12.04, installed on my HP 635.
Normally the built-in microphone works fine with **Skype 4.0** but in **Pidgin Internet Messenger**, the audio call option is not activated. Then if I make an audio call by logging in **imo.im** webpage, I hear the other person but he doesn't hear me. And if I go back to **Skype** for a test call, the microphone is not functioning properly there as well. To recover it, I have to reboot the system each time.

Do you have any recommendation for that problem?

Bekir

Have you tried playin around with ALSA when pidgin is running? 

just open a terminal and type ```
alsamixer
```

You can adjust a bunch of different settings, maybe somehow they are being changed when you try to use this program?

---

### Post by bekirs on 2012-08-02
I did some trial-and-errors but couldn't be successful with alsamixer... any other suggestion?

---

