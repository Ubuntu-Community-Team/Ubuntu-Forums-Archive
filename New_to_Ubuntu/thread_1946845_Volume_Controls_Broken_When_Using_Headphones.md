---
title: "Volume Controls Broken When Using Headphones"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by Raynman37 on 2012-03-25
I am having issues with my audio using the headphone jack and I am looking to see if anyone has a workaround.  I have searched online a lot and found [_[COLOR="Blue"]this bug report[/COLOR]_]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/410948"), which looks to have gone nowhere, and [_[COLOR="Blue"]this workaround[/COLOR]_]("http://dragly.org/2011/10/13/fixing-the-volume-treshold-and-intervals-in-ubuntu-on-dell-xps-m1330/"), which freezes the headphone and PCM channels completely.  The problem with this workaround is that my volume coming from the headphones seems completely unaffected by the master volume channel.

Here are pictures of what happens in alsamixer when I try to use the keyboard commands for the volume.

**Muted:**
[IMG]http://i291.photobucket.com/albums/ll320/ramalan37/audio1.png[/IMG]

**+1 Volume:**
[IMG]http://i291.photobucket.com/albums/ll320/ramalan37/audio2.png[/IMG]

**+1 Volume Again:**
[IMG]http://i291.photobucket.com/albums/ll320/ramalan37/audio3.png[/IMG]

**+1 Volume:**
[IMG]http://i291.photobucket.com/albums/ll320/ramalan37/audio4.png[/IMG]

As you can see, the PCM and headphone channels increase drastically when you press the volume button the first couple times.  When wearing headphones, this means it goes from mute to bleeding eardrums quickly.  Seeing as I almost blew out expensive headphones and someone in the Launchpad thread said they *did* blow out a speaker, I don't understand why this is filed as "won't fix".  Does anyone understand the workaround posted above enough to maybe freeze the master and PCM channels but leave the headphone channel working?  Thanks in advance for your help!

---

