---
title: "No sound after update - tried everything!"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by ghalia on 2008-07-24
Please...I am SO frustrated! New with linux, but doing my best to learn. 

Installed Feisty on my desktop in May, with minimal problems. Sound worked fine. Then I downloaded the standard updates one day...and sound is gone! When I switch to Windows, works fine, so not a speaker problem. I've gone through a zillion posts and tried every suggestion I could fine, but nothing works! Sadly, I have been at this for weeks :(

Here are the details:

Intel Pentium II 350MHz 192 MB RAM [I know...it's old!]
Sound card: NVIDIA GeForce2 
01:00.0 0300: 10de:0111 (rev b2)

I get an error: No volume control GStreamer plugins and/or devices found.

When I check Hardware Drivers, in lists: NVIDIA accelerated graphics driver: in use.

Everything else is running fine, including videos, just no sound.
I tried reinstalling the driver. The steps get REALLY confusing, but tried to follow as best I could. I didn't need to switch from "nv" to "nvidia", it was already listed.

I hate Windows, and don't want to go back to that *&#$@
Can someone PLEASE help me out?  ](*,)

---

### Post by Bucky Ball on 2008-07-24
NVIDIA driver for graphics only, nothing to do with sound. Go to a terminal and run;

> locate gstreamer

If it is not there, you should get a message something like;

'gstreamer currently not installed, you can install it by .... (instructions will be here). Also, System->Preferences->Sound. Everything is set correctly in there?

Give that a go. Feisty is getting on a bit now; why not backup and go for Hardy? Cheers and good luck.

---

### Post by OhioYJ on 2008-07-24
I wish I had some helpful advice, I too feel your pain, I'm typing this from Windows right now, while searching for a new distro.... 8.04 broke more stuff than it fixed on two of my laptops. Both worked fine in previous versions of Ubuntu (6.10, 7.04, 7.10). It's extremely frustrating.

---

### Post by Bucky Ball on 2008-07-24
Yea, that is odd, OhioYJ, as Hardy fixed a couple of things I'd been battling with for months (namely Broadcom wireless card).

---

### Post by Gibunit on 2008-07-25
> **Bucky Ball said:**
> Also, System->Preferences->Sound. Everything is set correctly in there?

What is defined as 'set correctly'?

I'm having audio problems and everything is set to Autodetect and i hear the tone when i click test. However under the 'Audio Conferencing' sub heading in the devices tab, Sou_n_d capture: *, it doesnt matter what i set for * i either get no response or a second or two of crackles then nothing, whereas i'd expect the tone to be ongoing until i click 'ok' like the other tests.

What aspects does 'audio conferencing' handle? would it have any effect on gaming through 'wine' or media in FF?

---

### Post by t0p on 2008-07-25
I also lost audio after an update. But the fix [*here*]("http://http://ubuntuforums.org/showthread.php?p=4928900") repaired it.

---

### Post by bobnutfield on 2008-07-25
You might want to take a look at this:

[http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/]("http://linux.dsplabs.com.au/no-volume-control-gstreamer-plugins-and-or-devices-found-no-sound-or-voume-control-bug-on-ubuntu-p31/")

It appears to be the same problem.

Bob

---

