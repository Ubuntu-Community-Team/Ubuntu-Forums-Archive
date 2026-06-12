---
title: "Audiophile looking to use iTunes?"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by s0ulchicken on 2013-04-19
Hello everyone, I am a new user to Ubuntu (and linux in general) and was wondering how I would go about installing itunes so I can update my iPod.  Pardon my newbness as I literally installed Ubuntu two hours ago.  Would I need to use a program that will make an .exe compatible with linux?  Thanks for any help in advance.

BTW, I am really digging this OS!

---

### Post by DuckHook on 2013-04-19
> **s0ulchicken said:**
> ...BTW, I am really digging this OS!

Hi and welcome to the forums and Ubuntu.

As enthusiasts, we agree with you. However, one of the few holes in Ubuntu is iTunes support. There is none. There is no native iTunes app for Linux. WINE doesn't work with iTunes either, so you will have to either dual-boot with Mac/Windows or run Windows in a virtual machine (a computer within a computer) on top of Ubuntu. I'm afraid there really is no other alternative.

BTW, .exe apps are a Windows convention and generally will not run on Linux. It is possible to get them to run using WINE, but this is for more advanced users, is finicky and prickly, and only works for some programs and not others. I strongly, strongly recommend that you read the following, to get a good foundation for running Ubuntu and to understand the fundamental differences between Linux and the OS you have just come from.

Linux is not Windows intro:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

General Ubuntu Intro:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[https://sites.google.com/site/easylinuxtipsproject/Home](https://sites.google.com/site/easylinuxtipsproject/Home)

---

### Post by m4gnus on 2013-04-19
If you're feeling adventurous and simply feel like dropping new tunes into your iPod, check out this application named [gtkpod]("http://www.gtkpod.org/wiki/Home"). It connects to the database on your device allowing you to see what you currently have and transfer new music over with great ease. 

It is currently in the [universe] repository ([here]("http://packages.ubuntu.com/quantal/gtkpod")), so you should be able to do a ```
[FONT=courier new]sudo apt-get install gtkpod
```[/FONT] to get it onto your system.

Hope that helps!

---

### Post by philinux on 2013-04-19
I've tried but failed with itunes for my daughter. But look here and convince yourself. 

[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by s0ulchicken on 2013-04-19
Thanks everyone for the help!  I appreciate all the links and great information on this.  I feel a bit underwater, but I am sure I will be able to get a gulp of air soon.

---

### Post by m4gnus on 2013-04-19
> **s0ulchicken said:**
> Thanks everyone for the help!  I appreciate all the links and great information on this.  I feel a bit underwater, but I am sure I will be able to get a gulp of air soon.

My advice is to learn to enjoy that feeling of not knowing what you are doing and keep plugging away at learning new things. Eventually you'll LOVE to feel lost.

---

### Post by s0ulchicken on 2013-04-19
> **m4gnus said:**
> If you're feeling adventurous and simply feel like dropping new tunes into your iPod, check out this application named [gtkpod]("http://www.gtkpod.org/wiki/Home"). It connects to the database on your device allowing you to see what you currently have and transfer new music over with great ease. 

It is currently in the [universe] repository ([here]("http://packages.ubuntu.com/quantal/gtkpod")), so you should be able to do a ```
[FONT=courier new]sudo apt-get install gtkpod[/FONT]
``` to get it onto your system.

Hope that helps!

I was able to get gtkpod to work - THANK YOU!

---

### Post by 3rdalbum on 2013-04-19
Next time you could buy an MP3 player that uses simple drag and drop to load its music. without requiring any extra software at all. These work well with Linux or indeed any operating system.

I have a Sony Walkman MP3 player - if you are really an audiophile you would love the sound quality and premium earbuds included with the Walkman range. And of course it works fine with Linux.

---

### Post by Baldrick_NZ on 2013-04-20
After many moons of trying to get iTunes to work, I discovered Google Play Music (gMusic), which works well under Linux, iMac & Windows.

I've been so thrilled to kick iTunes into the dust where it belongs since using gMusic. IMHO it offers so much more than iTunes. Music bought is stored in the cloud and can be downloaded to your computer or Android or iPhone. Unlike iTunes, you can download the same track more than once using the web page, or unlimited times using the music manager app.
Also you can upload your music (up to 20,000 songs) to the cloud, free of charge.

All purchased music come as 320kbps mp3, making it playable on the majority of portable music players, without the need of converting.

Pricing is pretty much the same as iTunes as well.

You can also get a 'frame' built for linux to help make gMusic appear as a standalone app, called 'Nuvola'.

Give it a go, you'll be pleased you did!

---

