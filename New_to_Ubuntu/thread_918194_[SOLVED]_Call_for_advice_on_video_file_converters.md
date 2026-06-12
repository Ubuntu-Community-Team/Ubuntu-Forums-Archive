---
title: "[SOLVED] Call for advice on video file converters"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by suomalainen on 2008-09-12
Ubunteros!

I would like a GUI that can convert multiple video formats like wmv, avi, mov. wmv etc... etc.. into formats I choose..

Anyone have any good/great suggestions as to what I should be using?

Thanks!!!

---

### Post by Orwell on 2008-09-12
You could try using [WinFF]("http://code.google.com/p/winff/downloads/detail?name=winff-0.42-i386.deb&can=2&q=") but you'll need to install FFmpeg through Synaptic first....I've just done this to convert .flv into wmv and it works a treat!

---

### Post by shadow-of-sin on 2008-09-12
I use AVIDemux (you can find it in the repositories).

For more info see here:
[https://help.ubuntu.com/community/Transcoding](https://help.ubuntu.com/community/Transcoding)

---

### Post by suomalainen on 2008-09-12
Shadow of sin,

Would you mind telling me step by step how to convert my mov file into avi using Avidemux?

I'm asking cause I tried but nothing is working for me...

Thank you.

---

### Post by t0p on 2008-09-12
The folk responsible for the firefox add-on **videodownloadhelper** have a vid conversion utility.  Go to [www.downloadhelper.net]("http://www.downloadhelper.net") for more info.

---

### Post by shadow-of-sin on 2008-09-12
It appears that AviDemux for converting mov files is problematic. I tested WinFF and it works well, here's how you install it:

1. Install ffmpeg by going to a terminal and typing:
```
sudo apt-get install ffmpeg
```
2. Download the winff deb binary:
[http://winff.googlecode.com/files/winff-0.42-i386.deb](http://winff.googlecode.com/files/winff-0.42-i386.deb)
3. Browse to the file you downloaded and open it to install Winff
4. Go to Applications-->Sound&Video-->WinFF to start Winff.

---

### Post by suomalainen on 2008-09-12
Shawdow!

Thanks for the advice. Howerer, I can't install the file you noted. A pic is attached noting the error message.

Can you help?

Thanks!

---

### Post by Orwell on 2008-09-12
Go [HERE]("http://code.google.com/p/winff/downloads/list")
and select the .deb package that corresponds with your system

---

