---
title: "HOWTO: Add quality control to Sound Juicer preferences"
date: 2005-04-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Curufir on 2005-04-25
This package adds a quality control slider for Ogg/MP3 (With lame) to the Sound Juicer preferences panel. In keeping with the Sound Juicer application it doesn't provide masses of detail. The more to the right the slider goes, the better the quality and the higher the file size.

Installing:

Download the attached file.

bunzip2 sound-juicer_2.10.1-0ubuntu1_i386.deb.bz2
sudo dpkg -i sound-juicer_2.10.1-0ubuntu1_i386.deb

Synaptic and Ubuntu's update notifier will complain that there is a new version. Fix that by apt pinning.

sudo gedit /etc/apt/preferences and add these lines:

Package: sound-juicer
Pin: release o=now
Pin-Priority: 990

The notifier will shut up next time it checks the repositories.

Notes:
If you haven't touched gnome-audio-profiles-properties everything should work fine.

If you can't see a quality setting then open gnome-audio-profiles-properties (<alt> + F2 and type gnome-audio-profiles-properties), select your Ogg/MP3 profile, choose edit and check that the GStreamer Pipeline setting looks like one of these:

audio/x-raw-int,rate=44100,channels=2 ! vorbisenc name=enc
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc

With **nothing** following after enc.

If you don't have MP3 encoding (And actually want it) follow the 4th post down in this forum thread [http://ubuntuforums.org/showthread.php?t=26416](http://ubuntuforums.org/showthread.php?t=26416).

ToDo:
I've tried to test everything thoroughly, but there may still be bugs I've missed. Please reply on this thread if you find anything.

Figure out how to send in patches for evalution, or even who to contact about it.

Unravel the mysteries of deb files and how to change version numbers.

---

### Post by rykel on 2010-10-31
I hate to edit the Gstreamer Pipeline in Sound Juicer Preferences as well, but how will your program interfere with my default Sound Juicer, especially since you did NOT specify which version of Ubuntu it is meant for?

Thank you for writing this!

---

### Post by mc4man on 2010-10-31
> but how will your program interfere with my default Sound Juicer
Don't think you have much to worry about there - this is **5 years old** so the package will not install, and if it somehow did probably wouldn't run on any current ubuntu release

---

