---
title: "Microphone issue"
date: 2018-04-27
forum: New to Ubuntu
---

### Post by cthunter24 on 2018-04-27
Hi any tutorial on how to make the audio line-in work? the speakers are working but I can't record anything. It started when I'm using Lubuntu 17.10 but even after I upgrade, it still doesn't work. I tried to check it using pavucontrol and it shows that it can detect it.

---

### Post by leunam12 on 2018-04-28
While this does not address your question specifically, you can use audio-recorder to record anything that is playing through the speakers.

```
sudo add-apt-repository ppa:audio-recorder/ppa
sudo apt update
sudo apt install audio-recorder
```

If you don't want to do this via ppa you may download the .deb file for your particular Ubuntu version and double-click to install.

[http://ppa.launchpad.net/audio-recorder/ppa/ubuntu/pool/main/a/audio-recorder/](http://ppa.launchpad.net/audio-recorder/ppa/ubuntu/pool/main/a/audio-recorder/)

---

### Post by oldrocker99 on 2018-04-28
Audio-recorder works fine. Personally, I use Audacity, which allows editing of the recording after it is made.

---

