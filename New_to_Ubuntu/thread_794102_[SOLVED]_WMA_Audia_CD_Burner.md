---
title: "[SOLVED] WMA Audia CD Burner"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by Dr Small on 2008-05-14
I need an App that will burn wma files to a cd as an audio cd. I have tried recorder, which said the files needed to be wav and tried k3b which would not work.

Any suggestions?

---

### Post by TeoBigusGeekus on 2008-05-14
Couldn't you convert them to mp3 with audacity?

---

### Post by shifty_powers on 2008-05-14
[http://www.imgburn.com/](http://www.imgburn.com/) and wine?

> ImgBurn supports a wide range of image file formats - including BIN, CUE, DI, DVD, GI, IMG, ISO, MDS, NRG and PDI.

It can burn Audio CD's from any file type supported via DirectShow / ACM - including AAC, APE, FLAC, M4A, MP3, MP4, MPC, OGG, PCM, WAV, WMA and WV.

It supports Unicode folder/file names, so you shouldn't run in to any problems if you're using an international character set.

ImgBurn supports all the Windows OS's - Windows 95, 98, Me, NT4, 2000, XP, 2003, Vista and 2008 (including all the 64-bit versions). If you use Wine, it should also run on Linux and other x86-based Unixes.

It's a very flexible application with several advanced features that are often lacking in other tools, especially when it comes to burning DVD Video discs. It supports all the latest drives without the need for updates (including booktype / bitsetting / advanced settings on many of the major ones - i.e. BenQ, LiteOn, LG, NEC, Plextor, Samsung, Sony).

There is an image queue system for when you're burning several images (which you can automatically share between multiple drives if you have more than one) and an easy-to-use layer break selection screen for double layer DVD Video jobs. The Automatic Write Speed feature allows you store your favourite burn speed settings on a per 'Media ID' basis, right down to a drive by drive level. Data captured during the burn (write speed, buffer levels etc) can be displayed / analysed using DVDInfoPro.

Whilst ImgBurn is designed to work perfectly straight out of the box, advanced users will appreciate just how configurable it is.

Oh and let's not forget the best thing about it.... it's 100% FREE ;-)

---

### Post by Dr Small on 2008-05-14
> **TeoBigusGeekus said:**
> Couldn't you convert them to mp3 with audacity?
Yes, but if I did, they wouldn't play in a non-mp3 player...

---

### Post by TeoBigusGeekus on 2008-05-14
Convert them to mp3 and then burn them as audio cds with brasero,k3b,gnomebaker etc...

---

### Post by billgoldberg on 2008-05-14
> **Dr Small said:**
> Yes, but if I did, they wouldn't play in a non-mp3 player...

Did you try "brasero"?

I don't see a reason to use wma at all, but hey, that might just be me.

---

### Post by Dr Small on 2008-05-14
> **billgoldberg said:**
> Did you try "brasero"?

I don't see a reason to use wma at all, but hey, that might just be me.
Does burning the mp3's as an audio cd make them playable in a normal cd player (that is not mp3 compatible) ? If so, then I'll just convert them to mp3 and burn them.

---

### Post by avtolle on 2008-05-14
> **Dr Small said:**
> Does burning the mp3's as an audio cd make them playable in a normal cd player (that is not mp3 compatible) ? If so, then I'll just convert them to mp3 and burn them.

Yes, it does; I do it all the time using Brasero, audio project option. For example, our younger daughter is a DJ at her college radio station which streams on the internet. I set up VLC to capture the stream, which in raw form is mp3, and save it to a file with the appropriate extension. Then, I use Brasero to burn the mp3s to disk, so family members without internet can hear the program. The app converts the mp3 to wav, which is what is playable on CD players. What you need to be aware of is the time conversion from mp3 to wav; if the mp3 file is too big, the process will abort. In the example given above, her show is two hours long; I do two "saves" through VLC, each an hour, and then burn the same individually. Probably too much information.

---

### Post by NightwishFan on 2008-05-14
When you burn an audio cd it takes compatible files like mp3 and puts them into a "cd format" so to speak.

---

### Post by Dr Small on 2008-05-14
Ok. Well all else failed, so I just tried Sepentine (it was on my sister's computer) and I burnt the wma's to the disc as an audio cd and it works perfect. 

I just wish there was some other apps out there that would do the same thing, but not bring in all the gnome or kde libs with it. Stick to gtk and I'll bite the hook :)

Dr Small

---

