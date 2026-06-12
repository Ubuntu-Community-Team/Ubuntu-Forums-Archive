---
title: "You Tube And Playing DVDs, How Is it Done?"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Breandean on 2008-09-04
So I have Ubuntu, but how do I get it to play You Tube videos and DVDs?

---

### Post by lowstand on 2008-09-04
fire fox  is what i am running an all i had to do today was run the plug ins

---

### Post by Bakon Jarser on 2008-09-04
[https://help.ubuntu.com/8.04/musicvideophotos/C/video.html](https://help.ubuntu.com/8.04/musicvideophotos/C/video.html)

---

### Post by crjackson on 2008-09-04
> **Breandean said:**
> So I have Ubuntu, but how do I get it to play You Tube videos and DVDs?

Assuming you are running 32-bit 8.04 (Hardy), this will fix your DVD & You Tube issues as well as many others.  Open up a terminal screen and paste the following code:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2 libdvdnav4 gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 libdvdread3
```

If you are running 64-bit Hardy, then paste the following:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w64codecs totem-mozilla libdvdcss2 libdvdnav4 gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 libdvdread3
```

---

### Post by Breandean on 2008-09-06
Thanks, this was very hlpful, but dpkg was interupted and I am instructed to run it manually. "-a". Is there a wiki for this?

---

### Post by Bradtek on 2008-09-06
Comprehensive Multimedia & Video Howto

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by t0p on 2008-09-06
> **Breandean said:**
> Thanks, this was very hlpful, but dpkg was interupted and I am instructed to run it manually. "-a". Is there a wiki for this?

I take it you got a message telling you to run **dpkg --configure -a**?  If so, type this into the terminal:

```
sudo dpkg --configure -a
```

---

### Post by billgoldberg on 2008-09-06
Open up a terminal and copy/paste this


```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

--

If you are afraid of the terminal, you can do that also in synaptic. But it's going to take a lot longer to do so.

---

