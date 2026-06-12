---
title: "Problem with Wireless card RT2790 on fresh install of Xubuntu 12.04"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by Aycco on 2012-12-18
Hello, this is my first post here and it's about a problem I've run into upon installation of the 12.04 version of the Xubuntu distribution, it's my first time with an open OS and so far I haven't run into any major problems, with the exception of this one:

The problem is that I can't connect to my wireless network, I can connect to my router via an ethernet cable just fine, and I can even detect wireless networks as usual, but I can't connect to mine, even if I leave my network open without any protection/encription. It's (probably) not a problem with my router, as I can still connect to it using another computer or even this one when running Windows

My wireless card is a "Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe", I tried dowloading the newest linux-compatible official driver on the Ralink official site,  but after the download of the file, wich appears to be "2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2", I can't seem to be able to extract it,  it gives me a message saying that it isn't a valid bzip2 file:
```

$ tar -xjf 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now

```
I don't know if my problem would be solved upon installation of the new driver, but I'm not sure of what else I could do to try to fix it

I thank anyone who could spare his time to assist me

As a side note, english is not my native language, so please give me some feedback on my spelling and point out any mistakes I may end up doing

---

### Post by audiomick on 2012-12-18
Have you tried letting the additional drivers utility install proprietary drivers for your wireless card?

I am not sure where that is on xubuntu, but it will be there somewhere. Up until the unity desktop, it was in system> administration on the gnome desktop.

You should try and find that and give it a chance before you try and install something from a .tar file. If you do, it means your package manager will know the packages are there and take care of updates and what have you.

Your computer needs to be connected to the internet (i.e. on the cable) when you do this.

---

### Post by Aycco on 2012-12-18
> **audiomick said:**
> Have you tried letting the additional drivers utility install proprietary drivers for your wireless card?

I did, but no additional drivers were found  with the exception of a few NVIDIA graphic drivers, wich I honestly don't think I'll need anytime soon

---

### Post by audiomick on 2012-12-18
Have you tried unpacking it from the file manager? I think you should be offered that option if your right click on it.

---

### Post by Aycco on 2012-12-18
Upon selecting "Extract Here" with the Archive Manager I just get the message "An error occurred while loading the archive."
"bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error is not recoverable: exiting now"
Basically the same error message as when I try to do it manually
For the record, I already have tried redownloading the file

---

### Post by audiomick on 2012-12-18
Hmm, I'm stumped, then. I hope someone else can help you. Sorry.

---

