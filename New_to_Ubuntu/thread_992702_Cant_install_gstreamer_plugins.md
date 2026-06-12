---
title: "Cant install gstreamer plugins"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by dileepdinesh on 2008-11-25
I made a fresh install of ubuntu 8.10 yesterday in my dell lap,,,
when i try to install gstreamer plugins ,it says mine is x386 architecture and its not supported,,,any help?

---

### Post by spawn. on 2008-11-25
What kind of gstreamer plugin is it? "Good" "Bad" "Ugly" "Base" etc...

Added: You're not the only one whose having issues with this on Dell. I would try adding a new repository like medibuntu so you can try other alternatives. I never owned a Dell so I can't solve your problem but there's a ton of folks here who will check out your post.

Medibuntu Link:  > [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) 

---

### Post by jimreynold2nd on 2008-11-25
uhh... what are your steps of installing gstreamer plugins? Can you be a lil more specific about the steps that you did to install it?

Meanwhile, can you try this one liner: 
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install libdvdcss2 w64codecs

```

---

### Post by dileepdinesh on 2008-11-25
sorry guys,,,i try to install these things from add or remove
there the gstreamer plugins for xvid,faac etc is what i tried
then i get that message

---

### Post by jimreynold2nd on 2008-11-25
uhh.. that is weird. I would open Synaptic and do a search on 'gstreamer' and install the gstreamer-plugins-bad (-good and -ugly too)

---

