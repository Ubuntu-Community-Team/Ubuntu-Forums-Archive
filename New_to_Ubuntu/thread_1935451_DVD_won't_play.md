---
title: "DVD won't play"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by L Campbell on 2012-03-04
I have an Emprex 16X DVD player/writer and it will not play my DVD disk.

Is there some kind of driver, or software that I need to get this going?

TIA.

---

### Post by Frogs Hair on 2012-03-04
Test other types of DVDs if you have them because it may not be a driver issue , but a codec . The Ubuntu restricted extras and/or GStreamer plug-ins from the software center may solve the problem . If no DVDs play it is probably a driver issue .

---

### Post by sleepingdragon on 2012-03-05
You didn't specify if the DVD was a commercially produced disk, i.e., a shop-purchased film DVD.

If that's the case, then you need to install libdvdcss2, which enables decryption of commercial DVDs.

This software is not included by default because of certain legal questions in various countries.

However, if you wish to install it, you can go to medibuntu.org and follow the Repository How-To instructions. When they're done, you can install libdvdcss2 through the USC or just type in 

> sudo apt-get install libdvdcss2 

into a terminal. After that, you should be able to play DVDs.

---

### Post by mapes12 on 2012-03-05
As well as the above I would install ubuntu-restricted-extras from Synaptic and the VLC media player.

---

### Post by kimme on 2012-03-05
Have you tried this easy solution?

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by L Campbell on 2012-03-05
> **kimme said:**
> Have you tried this easy solution?

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Thanks, I tried this and the procedure seemed to go smoothly but the DVD disk still doesn't play.

Kind regards.

---

### Post by muppet317 on 2012-03-06
This post is pretty comprehensive and should resolve most dvd / multimedia issues:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by donkyhotay on 2012-03-06
From the sound of it, it sounds like a codec issue like everyone else has mentioned however just to elmininate the obvious it might be a good idea to make certain the computer can read discs as a whole. Can you view files on a data DVD? Basically if you put in a disc with something besides a movie (like say photo's or music) can you view/play that?

---

### Post by L Campbell on 2012-03-07
> **donkyhotay said:**
> From the sound of it, it sounds like a codec issue like everyone else has mentioned however just to elmininate the obvious it might be a good idea to make certain the computer can read discs as a whole. Can you view files on a data DVD? Basically if you put in a disc with something besides a movie (like say photo's or music) can you view/play that?

Thanks for your interest.

It will open and play a Knoppix DVD just fine.  What I'm trying to play is an exercise DVD, so I guess this must come under the 'movie' catagory?

---

### Post by sleepingdragon on 2012-03-07
> **L Campbell said:**
> What I'm trying to play is an exercise DVD, so I guess this must come under the 'movie' catagory?

Yes, it will.

---

### Post by donkyhotay on 2012-03-09
Yeah, that's going to be a movie and if a knoppix DVD plays then that means there is nothing physically wrong with drive and is a codec issue. As I mentioned I suspected that was the case but sometimes I've seen people jump straight to messing around with codecs without even checking if another type of disc plays and it ends up being something wrong with the drive itself. I've found it's always worthwhile to check the basics when doing any sort of troubleshooting.

---

