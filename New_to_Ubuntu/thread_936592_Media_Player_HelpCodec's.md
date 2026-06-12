---
title: "Media Player Help/Codec's"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by tictac232434 on 2008-10-02
I have tried installing and uninstalling the media player that is standard with Ubuntu 8.04 LTS. I installed both codec's at the same time and when I went to play a supported file format this error message came up. "Failed to connect to server : Invalid argument" and it does not matter which media player I try.

---

### Post by fr.theo on 2008-10-02
have you downloaded the GStreamer extra plugins codecs from you "add/remove Application" under Applications menu.

---

### Post by 3rdalbum on 2008-10-03
Are you playing a local file, or a streaming file? What file format? When you right-click on the file and go to Properties, and then look at the Audio or Video tab, what does it tell you about the codecs used?

Have you tried installing w32codecs from the Medibuntu repository? ([www.medibuntu.org](www.medibuntu.org))

Have you tried using the VLC media player that's available from within Synaptic Package Manager?

For future reference, it's easier for others to help you if you give as much information as possibile; otherwise all we can do is blindly guess what the problem might be.

---

### Post by tictac232434 on 2008-10-03
Ok, Yes I did try installing/uninstalling from the Gstreamer Codec's and even the ones that autopop up when you double click a .MP3 format song. I have tried Installing the W32codec's and still nothing. 

Under the Audio file it's information is as reads.

Codec: MPEG 1 Audio, Layer 3 (MP3)
Channels: Stereo
Sample Rate: 44100 Hz
Bitrate: 128 kbps

No I am not trying to stream music just play a local file.

and the problem is the song will play on Mplayer but not on others and eitherway an error message comes up on either players saying "Failed to connect to server: Invalid Argument" or "Failed to connect stream: Invalid Argument" and thats for Movie player which normally worked on my last install... 

Thanks all help is appreciated and I tried to give more info this time!

---

### Post by Ryadt on 2008-10-03
Have you got ubuntu-restricted-extras installed?

---

### Post by tictac232434 on 2008-10-03
> **Ryadt said:**
> Have you got ubuntu-restricted-extras installed?

I am not sure I am very new to Ubuntu.....If you can guide me through the process I will be able to tell you the answer to that question.

---

### Post by Ryadt on 2008-10-03
Type in terminal```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by tictac232434 on 2008-10-03
> **Ryadt said:**
> Type in terminal```
sudo apt-get install ubuntu-restricted-extras
```

I did exactly as you said but it still did not fix the errors and here is the message of what happened towards the end so it seems to have "worked". Thanks though I do appreciate all the help I can get. Maybe I need to Reinstall Ubuntu and make sure my hardware and everything is supported but I have not had problems like this before... My CPU is supported and Audio and Graphics and everything so I do not think that is the problem I can not figure this one out though... So any help is much appreciated !


All done, no errors.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: impact32.exe
  extracting fontinst.exe
  extracting Impact.TTF
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: times32.exe
  extracting fontinst.inf
  extracting Times.TTF
  extracting Timesbd.TTF
  extracting Timesbi.TTF
  extracting Timesi.TTF
  extracting FONTINST.EXE

All done, no errors.
Extracting cabinet: trebuc32.exe
  extracting FONTINST.EXE
  extracting trebuc.ttf
  extracting Trebucbd.ttf
  extracting trebucbi.ttf
  extracting trebucit.ttf
  extracting fontinst.inf

All done, no errors.
Extracting cabinet: verdan32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting Verdanab.TTF
  extracting Verdanai.TTF
  extracting Verdanaz.TTF
  extracting Verdana.TTF

All done, no errors.
Extracting cabinet: webdin32.exe
  extracting fontinst.exe
  extracting Webdings.TTF
  extracting fontinst.inf
  extracting Licen.TXT

All done, no errors.
All fonts downloaded and installed.
Updating fontconfig cache for /usr/share/fonts/truetype/msttcorefonts
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.

Setting up ubuntu-restricted-extras (15.2) ...
Setting up unrar (1:3.7.8-1) ...

Setting up sun-java6-bin (6-07-3ubuntu2) ...

Setting up sun-java6-jre (6-07-3ubuntu2) ...

Setting up sun-java6-plugin (6-07-3ubuntu2) ...

---

### Post by tictac232434 on 2008-10-06
I re-installed Ubuntu and it worked fine just be sure to install codec's before you update worked fine for me thanks. "Resolved"

---

