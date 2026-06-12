---
title: "recommended format/program to use when converting videos to keep on a ubuntu machine?"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by ijason on 2008-11-23
i'm wondering what the popular consensus would be on the best video format/codec to convert the various files i have INTO, intending to keep them on an ubuntu box hooked up to a tv. and using which program.

i've got all kinds of .wmv, .avi, and .mpg videos that i want to convert into a single format that will be lossless from the original... but run the best on a machine that will only ever be ubuntu. some of the originals are high rez, some not so much, so i'd prefer the output quality be scaled to match the original video source. 

how does ogg vorbis video compare to .mpg? mpg to mp4 etc?

---

### Post by diablo75 on 2008-11-23
> **ijason said:**
> i'm wondering what the popular consensus would be on the best video format/codec to convert the various files i have INTO, intending to keep them on an ubuntu box hooked up to a tv. and using which program.

i've got all kinds of .wmv, .avi, and .mpg videos that i want to convert into a single format that will be lossless from the original... but run the best on a machine that will only ever be ubuntu. some of the originals are high rez, some not so much, so i'd prefer the output quality be scaled to match the original video source. 

how does ogg vorbis video compare to .mpg? mpg to mp4 etc?

The first question that comes to my mind is... why not keep these files in their original format?

Second, there are codecs out there that you could convert a video into losslessly, but you'd be looking at taking up a TON of hard drive space for no practical gain (because to remain lossless, you would have to use a non-compressive codec).  Nearly all common video formats are lossless, and you'd only end up degrading the video quality even more if you tried to convert one lossy format into another lossy format for seemingly no practical reason.  Again, it would be easier to simply leave the files in their original state and play them using standard decoders.  There is nothing preventing Ubuntu from playing back mpg, mp4, wmv, avi, xvid/divx, and many many other formats, providing that you have the proper decoders installed, and that's easy to do.  (If this is what you're problem is, click Applications>Add/Remove, change the search filter to say "all available applications" and look for the word "restricted".  Click Ubuntu Restricted Extra's, then Apply to install.  You'll be able to play just about any file format out there after you do this).

Ogg Vorbis video files are quite capable of maintaining video quality, but is suprisingly not supported very well by all applications (avidemux comes to mind).  By the way, avidemux is pretty similar to VirtualDub for Windows.  You can use it to do simple edits and convert video to a few other useful formats (like xvid, mpeg2, mp4.  Although my understanding is that the ultimate video converter is mencode (a command line tool that takes some learning to use).

---

### Post by ijason on 2008-11-23
the only reason i would want to convert them is on the hopes that some format may work much better with ubuntu than .wmv does. 

i have all the codecs from the mediabuntu project, so i can play most everything, but some seem to put more strain on the cpu than others.

just seemed that if there were a format that was native to linux and would require less "work" to view, it might be worth converting. especially since i have a bunch of videos that will just live on the computer and never need to be transferred elsewhere.

---

### Post by xravexheavenx on 2008-11-23
Any format you go with will require some kind of codec.

I personally prefer AVI, MKV, or OGM formats.

---

### Post by jimmy the saint on 2008-11-23
Even WMV is not native to windows in the way you think it is.  You simply need to have the codec available and any format will work on any system.  I would focus more on the performane of the codec (ie size/performance/quality) rather than on which system you feel the format would be most at home in.

---

### Post by diablo75 on 2008-11-23
I say if they play fine now, then they'll always play fine.  Computers aren't getting any slower these days, although at some point we're all going to be watching 1080p grade HD videos and will have to upgrade no matter what codec we go with.  I know what you mean when it comes to trying to play HD WMV files back in Ubuntu; it's got a LOT of overhead to deal with.  But if you want my pick, I'd go with xvid or Divx, simply because they perform great and are the most widely supported on devices like set-top DVD players (I have a $40 Philips DVD player that will play Divx/Xvid).

---

### Post by benerivo on 2008-11-23
I know what you mean by 'less work to play'. I've always found .mpg or .mp4 to be easy formats to play and search/scan with any media player, on any platform. Plus, both are very well supported.

---

