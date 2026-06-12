---
title: "2nd problem with ubuntu"
date: 2013-09-17
forum: New to Ubuntu
---

### Post by hilario2 on 2013-09-17
Ok following my road to ubuntu I have now the following problem:

My sound card is : Realtek High definition audio and I have a creative 5.1 speakers system.

Sound is working but not all the speakers have sound and when I try to check the system ont the test there's only the right and the left speaker.

Is there any chance to use the full 5.1 system inside my ubuntu 13.04 ??

---

### Post by Bubba_Jackson on 2013-09-17
It may seem a stupid question to ask, but first of all, does your sound card support surround sound? 

Have you tried checking the "System Settings > Sound" menu for the configured sound output? You're obviously using stereo output, so there might be a surround option to check. Happened to me once, wondered why there wasn't any sound on my TV while connected via HDMI on a Linux Mint distro. Had to choose HDMI digital output in that menu.

Also, it could be a driver issue, maybe your current driver has no surround sound support.

---

### Post by hilario2 on 2013-09-17
On windows all speakers have sound.

On ubuntu I only get left and right speaker.

I have installed last drivers I found for Ubuntu !!!

---

### Post by pbpersson on 2013-09-17
Did you get the Linux drivers from the Realtek web site?  I see they have a new driver there but I have not looked at the instructions to see how involved the installation might be.

[http://www.realtek.com.tw/downloads/downloadsview.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false]("http://www.realtek.com.tw/downloads/downloadsview.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false")

---

### Post by hilario2 on 2013-09-17
> **pbpersson said:**
> Did you get the Linux drivers from the Realtek web site?  I see they have a new driver there but I have not looked at the instructions to see how involved the installation might be.

[http://www.realtek.com.tw/downloads/downloadsview.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsview.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)


Yes that's where I got the drivers.

Version installed was 5.18.

But to be honest I don't know if I did instalation  right.

It's still a bit confusing the instalation on ubuntu.
Sometimes it's so easy to install, another times it's confusing.

---

### Post by newb85 on 2013-09-18
On the left side of the Output tab in the Sound dialog, what options are listed under "Play sound through"?

---

### Post by hilario2 on 2013-09-18
> **newb85 said:**
> On the left side of the Output tab in the Sound dialog, what options are listed under "Play sound through"?


I have only: analogic entry 
                  internal audio

---

### Post by Bubba_Jackson on 2013-09-18
Take a look at these links, you may find more info there:

[http://ubuntuforums.org/showthread.php?t=783222](http://ubuntuforums.org/showthread.php?t=783222)
[https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)

---

### Post by hilario2 on 2013-09-18
Now I did some kind of mistake as I don't have sound at all.

When I select "sound" there's nothing neither  in the output nor in the input !!!

How can I restore the sound ??

---

### Post by newb85 on 2013-09-19
Okay, please give us the output of 
```
sudo lshw -C sound
```

---

