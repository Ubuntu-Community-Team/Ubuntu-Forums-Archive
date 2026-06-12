---
title: "USB Headphones"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by bkwraith on 2008-06-09
Hi There!  I am a bit new to Linux, so please be patient and bear with me.  I have a set of [eDemensional]("http://www.newegg.com/Product/Product.aspx?Item=N82E16826504004") USB headphones and was curious if it's possible to use them in ubuntu.  Thanks for the help!

---

### Post by ajmorris on 2008-06-10
> **bkwraith said:**
> Hi There!  I am a bit new to Linux, so please be patient and bear with me.  I have a set of [eDemensional]("http://www.newegg.com/Product/Product.aspx?Item=N82E16826504004") USB headphones and was curious if it's possible to use them in ubuntu.  Thanks for the help!


I take it when you plug them in, they dont work?

When they are plugged in, can you please post the output of ```
sudo lsusb
```

AJ

---

### Post by Xiong Chiamiov on 2008-06-10
Heh, USB headphones can be a bit of work sometimes, but rest assured, they will mostly likely work.

I had to compile my sound drivers (I always have to do that, actually) with support for both my audio card and the headphones.  The ./configure line looked like this:
```

./configure --with-sequencer=yes --with-cards=usb-audio,ca0106 --with-oss=yes

```
and then set the headphones to be default with
```

asoundconf

```

Now then, I'm sure that this is all gibberish to you.  I'm more posting it incase you need it later on (or someone else searching does).

---

### Post by bkwraith on 2008-06-11
> **ajmorris said:**
> I take it when you plug them in, they dont work?

When they are plugged in, can you please post the output of ```
sudo lsusb
```

AJ
it displays this.
```
Bus 005 Device 012: ID 056a:0017 Wacom Co., Ltd 
Bus 005 Device 011: ID 046d:08d7 Logitech, Inc. 
Bus 005 Device 010: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 1532:0109  
Bus 003 Device 002: ID 1532:000c  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 001 Device 001: ID 0000:0000  
```

The Logitech is a webcam, the C-Media are the headphones.

Thanks for the fast response

---

### Post by bkwraith on 2008-06-11
What would the command be through the terminal be to access the /config file?  I also need to get my Creative X-fi to play nicely with the rest of the system

---

### Post by Xiong Chiamiov on 2008-06-11
I'm not quite sure how things go when they work like they're supposed to (I haven't had that happen yet), but I had to compile ALSA.  In general, compiling takes the form
```

./configure
sudo make
sudo make install

```
inside a source folder.

I'd start out by trying the things in [this guide]("http://ubuntuforums.org/showthread.php?t=205449").  If that fails, I can give you the directions I followed to get things working for me.

---

### Post by PAFin on 2008-06-14
I am having the same usb audio issues and I tried the guide earlier.  I have not experienced any success.  I tried to set my usb audio to the primary but it always reverts back to secondary.  I saved the usb to be 0 and the hda to be 1.  

 1 snd_hda_intel
 2 snd_usb_audio

Is it not possible to have the usb device be your primary speakers?

---

### Post by bkwraith on 2008-06-14
I used [this guide]("http://ubuntuforums.org/showthread.php?t=205449") and got the creative card to work, still no usb headphones.  When I plug them in, the headphones will play the ubuntu login theme, even if the computer is playing music through amarok.

---

### Post by Xiong Chiamiov on 2008-06-14
If amarok is started before your headphones are plugged in, then it will continue to play music through your speakers; you'll have to restart it.  The same should apply to any other apps - they'll use the default soundcard if it's available, and if not, fall back to whatever they can.

@PAFin:
How did you change which one was default?  For me, I run
```

asoundconf list

```
to get a list of my soundcards names (with the headphones plugged in), then
```

asoundconf set-default-card [name]

```
to set the card I want as default.

You may have to play around with some of the other options, which you can see by entering
```

asoundconf

```

Hmm, noticed that I put a space in there in my first post.  Have to go back and fix that.

---

