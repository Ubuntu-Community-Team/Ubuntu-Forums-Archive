---
title: "How am I supposed to record sound?"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by venom104 on 2012-05-14
Okay here is the thing, due to problems with alsa, I had to install OSS4. 

I need to test wither or not I can record with it, and I've been having problems. I've tried using ossrecord on /dev/sdp and that didn't work. Skype reports a problem with audio output, i don't have a vent server to test it in, I can't use the sound recorder program from windows because its 64 bit and I have 32 bit wine, audacity lacks oss4 support, gnome sound recorder reports I don't have the right plugins installed.

I've been googling for hours trying to find a program that is OSS4 compatible and have found nothing.

What am I supposed to do to test this?

I'm using a 64 bit install of 10.04 LTS

---

### Post by HiImTye on 2012-05-14
I recommend installing ossxmix so you can configure OSS properly. once you get your microphone working through your speakers you can just mute it locally and it should work without issue

---

### Post by venom104 on 2012-05-14
> **HiImTye said:**
> I recommend installing ossxmix so you can configure OSS properly. once you get your microphone working through your speakers you can just mute it locally and it should work without issue


Thanks for responding, but the OSS4 packages I installed included ossxmix. I just don't really know how to use it, so I need a program to test it.

---

### Post by Baldrick_NZ on 2012-05-14
Hi there,

This might be your one-stop shop!

[http://www.omgubuntu.co.uk/2011/03/audio-recorder-for-linux-easily-record-audio-streams-to-mp3/](http://www.omgubuntu.co.uk/2011/03/audio-recorder-for-linux-easily-record-audio-streams-to-mp3/)

It even has a setting to record Skype calls.

---

### Post by venom104 on 2012-05-14
> **Baldrick_NZ said:**
> Hi there,

This might be your one-stop shop!

[http://www.omgubuntu.co.uk/2011/03/audio-recorder-for-linux-easily-record-audio-streams-to-mp3/](http://www.omgubuntu.co.uk/2011/03/audio-recorder-for-linux-easily-record-audio-streams-to-mp3/)

It even has a setting to record Skype calls.


Cool! Thanks...do you have any idea of how I can get it to work on debian testing? I have a few boxes around the house that run the same hardware, but different OSs (I'm trying to learn linux from different standpoints). I don't believe I can use a PPA on a debian system.

---

### Post by moma on 2012-05-24
Hello,
You can first try to install the .deb package on Debian.
You can get the .deb package directly from the
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)
Click the "View package details".

You can also compile audio-recorder from source. Read the INSTALL (and README) files. It's easy to do.

---

### Post by SeanIM on 2012-05-24
I'm pretty sure this is what I tried at one point and it worked.

> **moma said:**
> Hello,
You can first try to install the .deb package on Debian.
You can get the .deb package directly from the
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)
Click the "View package details".

You can also compile audio-recorder from source. Read the INSTALL (and README) files. It's easy to do.

---

