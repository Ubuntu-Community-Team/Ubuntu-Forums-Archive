---
title: "Audio Problems / Offline CD?"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by enrapture on 2008-08-30
Two questions, one thread! Twice the fun.

First: My audio through my Creative Sound Blaster X-Fi works great through  the LiveCD but after installing Ubuntu it doesn't work properly anymore (as in no sound at all). I'm really new to Ubuntu so I can't figure out where the device manager equivilent is to figure out what's wrong with it. What steps should I follow to get it working? Do I need to download a driver to get it working? If so, can I have a link to it? (No internet access on this pc, which leads me to my next question...)

SEcond: Is there a community created CD with a lot of the programs/codecs/etc that Ubuntu can support and are needed for basic use like MP3 playback provided in the community? Like a CD with a bunch of general installation packages? I don't have the internet on this ubuntu cd for the next week and was hoping to toy with it. If there is one, I'd love to get a link :)

---

### Post by gmxgeek on 2008-08-30
For your first question, please open a terminal, and post the output of
```

lspci

```

we'll see if ubuntu detects your card

second, what you are looking for is the Repository. You can access it using Synaptic, which is under System, Administration, Synaptic

It contains every package that is supported by ubuntu, as well as several that are nonfree

[http://www.ubuntugeek.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html](http://www.ubuntugeek.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html)

that link should help you get started with it


as for an offline thing, i don't think there would be one cd, as there are hundreds of GB of applications
you could try downloading packages from another computer if you have no internet on this one

---

### Post by enrapture on 2008-08-30
> **gmxgeek said:**
> For your first question, please open a terminal, and post the output of
```

lspci

```

we'll see if ubuntu detects your card


I will try this as soon as I get home tonight and post results tomorrow. Thanks :D

Any tips for if it does detect/doesn't?

> 
It contains every package that is supported by ubuntu, as well as several that are nonfree

[http://www.ubuntugeek.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html](http://www.ubuntugeek.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html)

that link should help you get started with it


as for an offline thing, i don't think there would be one cd, as there are hundreds of GB of applications
you could try downloading packages from another computer if you have no internet on this one


Ah, I was hoping there was a starter kit ISO or something for programs that see a lot of downloads.

---

### Post by gmxgeek on 2008-08-30
If it detects, its probably a driver issue, if not, it's something more.

No CD exists to the best of my knowledge, but you could make one from another computer that internet access if you really want to.

---

