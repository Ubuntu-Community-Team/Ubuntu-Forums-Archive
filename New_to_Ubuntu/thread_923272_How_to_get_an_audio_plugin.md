---
title: "How to get an audio plugin"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by ellalan on 2008-09-18
Hi
I am unable to get audo x/asf plugin, could someone please guide me to fix this. TIA.

---

### Post by forger on 2008-09-18
Is this for a movie, a video clip from a mobile phone.. or something else?

I think you need the medibuntu repository and the w32codecs package:
(Applications > Accessories > Terminal)
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update
sudo apt-get install medibuntu-keyring
sudo apt-get update

```

Then read:
[https://help.ubuntu.com/community/Medibuntu#Playing%20Non-Native%20Media%20Formats](https://help.ubuntu.com/community/Medibuntu#Playing%20Non-Native%20Media%20Formats)

---

### Post by ellalan on 2008-09-18
Thanks forger for the reply, I tried and couldn't get the particular MP3 file to play in VLC,Exaile,Rhythmbox or Movie player. I'll leave this post as unsolved and hope someone will come up with an answer. Thanks again.

---

