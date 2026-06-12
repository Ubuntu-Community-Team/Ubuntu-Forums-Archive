---
title: "Issue with acquring audio device names on ubuntu"
date: 2010-11-23
forum: Programming Talk
---

### Post by turc0033 on 2010-11-23
Im using java. On **Apple**, when I use the following piece of code: 
```

Mixer.Info[] mixerInfo = AudioSystem.getMixerInfo();
        for(int i = 0; i < mixerInfo.length; i++)
        {
                System.out.Println(mixerInfo[i].getName());
        }

```, I get a complete list of all of my output devices, including my bluetooth headsets. But when i use that piece of code in **Ubuntu,** it gives me:

[HTML]
PulseAudio Mixer
default [default]
Intel [plughw:0,0]
Intel [plughw:0,1]
NVidia [plughw:1,3]
NVidia [plughw:1,7]
NVidia [plughw:1,8]
NVidia [plughw:1,9]
Port Intel [hw:0]
Port NVidia [hw:1]
[/HTML]Plus, it **doesnt** list the bluetooth devices - as in i can't access them if theyre not the default output/intput sound device.

Is there anything that can be done to get a full list of the devices (incluing the bluetooth headsets) names on ubuntu just like on an apple?

Thanks in advance.

---

### Post by Zugzwang on 2010-11-23
Have you checked that your bluetooth device is usable as output device in other applications like, let's say, audacity?

---

### Post by turc0033 on 2010-11-23
> **Zugzwang said:**
> Have you checked that your bluetooth device is usable as output device in other applications like, let's say, audacity?

Yep. I can listen to music, record, playback, etc.

---

### Post by turc0033 on 2010-11-23
Also, i can get 2 headsets talking to each other (through a program that i made in java), but only if i set headset #1 as the default sound input and headset #2 as the default sound output. So its a 1 way communication line.

I would like it if both headsets could talk and hear each other, but i can't do that since i don't get a list of available devices wen using ubuntu.

---

### Post by Zugzwang on 2010-11-23
If you install the tool "pavucontrol" (using apt-get) and run it, is your bluetooth device listed?

---

### Post by turc0033 on 2010-11-23
> **Zugzwang said:**
> If you install the tool "pavucontrol" (using apt-get) and run it, is your bluetooth device listed?

Yes, both headset devices are listed.

---

### Post by Zugzwang on 2010-11-23
> **turc0033 said:**
> Yes, both headset devices are listed.

Ok, then I ran out of ideas.

---

### Post by turc0033 on 2010-11-23
> **Zugzwang said:**
> Ok, then I ran out of ideas.

:(

I only get about 10 indexes, but in the pulseaudio manager, it says that the headset devices are indexes 17 and 18. Trying to figure out a way to get to them

---

