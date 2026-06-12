---
title: "How to activate the S-video output"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by ResumeMan on 2008-06-27
Hi, I've tried to find help on this before to no avail.

My laptop has an s-video port (the round yellow thing that links to RCA to plug into a tv). In Windows, I can hold the Fn key and press one of the function keys (F5 I think?) to scroll through the output options -- s-video, external monitor, etc.

That key combo doesn't do anything in Ubuntu.

It was recommended to use the "Screens and Graphics" dialogue, but I can't figure out what to do from there. Screen 2 is disabled, and the only apparent option with this is to set it as default.

Playing around with the settings, I don't see anywhere to select a non-internal screen ouptut.

Any help on where to get started??

---

### Post by fatality_uk on 2008-06-27
> **ResumeMan said:**
> Hi, I've tried to find help on this before to no avail.

My laptop has an s-video port (the round yellow thing that links to RCA to plug into a tv). In Windows, I can hold the Fn key and press one of the function keys (F5 I think?) to scroll through the output options -- s-video, external monitor, etc.

That key combo doesn't do anything in Ubuntu.

It was recommended to use the "Screens and Graphics" dialogue, but I can't figure out what to do from there. Screen 2 is disabled, and the only apparent option with this is to set it as default.

Playing around with the settings, I don't see anywhere to select a non-internal screen ouptut.

Any help on where to get started??

Which version of Ubuntu are you using?

---

### Post by ResumeMan on 2008-06-27
Gutsy.

At the moment I'm not planning to upgrade to Hardy, but if there's a good reason to I will -- and if Hardy will let me use this output, that's a good enough reason...

---

### Post by Duck2006 on 2008-06-27
This may help.

[http://ohioloco.ubuntuforums.org/showthread.php?t=615070](http://ohioloco.ubuntuforums.org/showthread.php?t=615070)

---

### Post by ResumeMan on 2008-06-27
Well I'm not really sure where to begin with that thread. I'm not running MythTV packages and don't have any kind of TV tuner.

Do you have a succinct summary of how I should approach this? If you do I can use that thread to provide some more details.

---

### Post by ResumeMan on 2008-06-28
So for what it's worth, [this thread]("http://ubuntuforums.org/showthread.php?t=9106") has quite a bit of information on my problem, though I haven't been able to get it solved.

I am starting to wonder, though, if it may just be that Xorg doesn't support my hardware.

---

### Post by chronographer on 2008-06-28
I could suggest an easy method (which may or may not work) is to back up your xorg.conf (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup) and then plug in the s-video and try a auto configure thing, by using "sudo dpkg-reconfigure xserver-xorg"  If that doesn't work, then it depends what graphics chip you have. Nvidia can set a second monitor up with some xorg.conf tweaking like this: [http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456) or with a ATI card like the one I'm using like this: [http://ubuntuforums.org/showthread.php?t=625435](http://ubuntuforums.org/showthread.php?t=625435) I have a script which I use to play movies on the TV on the second page there...

So its definitely doable, it just depends on your graphics chip on how hard it is to do. Once its set up you can have 2 xorg.conf files and switch between them depending on what you want to do and you can switch between them using another script which I used, which I have lost the link to, which makes a nice zenity gui and you can pick between all the xorg.conf.2screens xorg.conf.single or whatever you have in /etc/X11 

Good luck, hope you get it going!

---

### Post by ResumeMan on 2008-07-02
That didn't seem to do anything (never saw it).

I'm getting the feeling that Ubuntu just doesn't support S-video. Anyone know if Hardy is any better with this?

---

