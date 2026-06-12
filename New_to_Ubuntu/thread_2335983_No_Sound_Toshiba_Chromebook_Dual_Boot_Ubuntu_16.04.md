---
title: "No Sound Toshiba Chromebook Dual Boot Ubuntu 16.04"
date: 2016-09-03
forum: New to Ubuntu
---

### Post by hushdie on 2016-09-03
[COLOR=#111111][FONT=Ubuntu]I have recently installed Ubuntu 16.04 on my Toshiba Chromebook 2. It is a dual boot running alongside ChromeOS. I can not get any sound on Ubuntu (chrome works fine) and I have tried following some of the instructions that I have seen on other threads but to no avail. I am getting sound if I plug in headphones, but none out of the speakers. I would really appreciate some help with this.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Many thanks[/FONT][/COLOR]

---

### Post by TheFu on 2016-09-03
Which model of CB2?  I have a C3350.
Which specific distro of Ubuntu? Running 16.04 with openbox here.

I had an issue where the audio out was defaulted to the headphone jack for a few months ... just had to plug in and remove any 2.5mm jack to make it switch to speakers.  For about 2 months, that hasn't happened, but pulse-audio has died every hour or so.  I just restart it before it is needed with this script:
```
pulseaudio -k # kill a daemon
pulseaudio -D # restart the pulse daemon

```  Check that the default audio output is analog speakers with **pavucontrol**.

I wasn't able to get Ubuntu (encrypted) and chromeOS to stay on the same SSD. Any tips you can share?

---

### Post by hushdie on 2016-09-03
I have Ubuntu running off a usb stick, got the tutorial from here 

[http://www.fascinatingcaptain.com/howto/dual-boot-chrome-os-and-linux/](http://www.fascinatingcaptain.com/howto/dual-boot-chrome-os-and-linux/)

works really well. (apart from the sound issue)

I tried the headphone trick but it didn't work. How can I check it is pavucontrol?

When I try your script this is what I get 

dingo@Dingo:~$ pulseaudio -k # kill a daemondingo@Dingo:~$ pulseaudio -D # restart the pulse daemon
E: [pulseaudio] main.c: Daemon startup failed.

---

### Post by TheFu on 2016-09-03
Did you run pavucontrol and change some settings?
If the daemon didn't start, time to check the log files. Anything there?

Running Ubuntu off a USB stick isn't an option for me. Why have a 128G SSD if I can't use it.  Would rather not have chromeos at all - really want to dual boot some other OSes without encryption, but the Ubuntu encryption wizard doesn't know how to allow that nor have I been able to manually create encrypted, LVM partitions and non-encrypted, extra partitions for another OS.

Which CB model? There are differences between the 8 models Toshiba makes, but named the same.

---

### Post by hushdie on 2016-09-03
its the CB30-b-103. 

You have lost me on the log files, how do I check them? I haven't run pavucontrol and changed any settings. 

I am bit crap once stuff starts not working!

---

### Post by TheFu on 2016-09-03
Review [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)  Google would find that with "ubuntu log files"

Hard to help if you won't experiment or run the suggested programs. ;|  To be successful, you'll have to try things.

Your CB is much older.

---

