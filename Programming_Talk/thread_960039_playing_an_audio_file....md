---
title: "playing an audio file..."
date: 2008-10-27
forum: Programming Talk
---

### Post by kcode on 2008-10-27
Im learning how to make an audio player using gstreamer, im getting what it says.But i would first like to know more clearly how an audio file is played by my computer.I cant find any tut for that. can someone just tell(briefly) || link me to some good source.

thanks

---

### Post by Xavieran on 2008-10-27
[http://pygstdocs.berlios.de/](http://pygstdocs.berlios.de/)

That's for python, but it is fairly good anyway...

---

### Post by kcode on 2008-10-27
thats looks like a gst documentation. But I would like to know first, how my computer plays an audio file.

thanks

---

### Post by DrMelon on 2008-10-27
Your computer decodes the compressed audio via a codec. Then, the decompressed digital audio signal is sent to the sound card, where it is changed into an analogue electricity signal. This is sent to the magnet in the back of the speaker cone, where the speaker vibrates, and voila! Music!

---

### Post by kcode on 2008-10-27
> **DrMelon said:**
> Your computer decodes the compressed audio via a codec. Then, the decompressed digital audio signal is sent to the sound card, where it is changed into an analogue electricity signal. This is sent to the magnet in the back of the speaker cone, where the speaker vibrates, and voila! Music!

thanks...that satisfied.

---

### Post by kcode on 2008-11-11
From the sound card decoded data is sent to an audio device,
how inside, speakers are distinguished from head-phones? ie
to where the data should be sent if i need to use headphones???

thanks

---

### Post by Zugzwang on 2008-11-11
> **kcode said:**
> From the sound card decoded data is sent to an audio device,
how inside, speakers are distinguished from head-phones? ie
to where should the data should be sent if i need to use headphones???

thsnks

There is no difference in using headphones or speakers. The sound card just outputs an analog signal. This is strong enough to drive head-phones directly. On the other hand, if you connect an amplifier, it amplifies this signal before driving the speakers with it.

Note that this part of the "playing" process is not digital and there is no "back-channel", so the sound-card just "fires and forgets" about the analog signal outputted. It cannot detect how the signal is being used. Likewise, the sound-card normally cannot detect situations in which all output devices are unplugged (although such a functionality could be added easily).

If you have so-called "USB speakers", things are a little bit different. These are -so to speak- however sound-cards on its own.

Summary: You do not need to worry about how the signal the sound-card produces is being used. It does not make a difference.

---

### Post by kcode on 2008-11-12
> **Zugzwang said:**
> There is no difference in using headphones or speakers. The sound card just outputs an analog signal. This is strong enough to drive head-phones directly. On the other hand, if you connect an amplifier, it amplifies this signal before driving the speakers with it.

Note that this part of the "playing" process is not digital and there is no "back-channel", so the sound-card just "fires and forgets" about the analog signal outputted. It cannot detect how the signal is being used. Likewise, the sound-card normally cannot detect situations in which all output devices are unplugged (although such a functionality could be added easily).

If you have so-called "USB speakers", things are a little bit different. These are -so to speak- however sound-cards on its own.

Summary: You do not need to worry about how the signal the sound-card produces is being used. It does not make a difference.

Actually the problem i am facing is that i'm unable to use headphones in my laptop, while speakers are working quite well. So i wanted to point out where the problem is.

thanks

---

### Post by Zugzwang on 2008-11-12
> **kcode said:**
> Actually the problem i am facing is that i'm unable to use headphones in my laptop, while speakers are working quite well. So i wanted to point out where the problem is.


If you just plug a 3,5mm headphone into the respective jack, then it's not too unlikely that you have a defective piece of hardware.

---

