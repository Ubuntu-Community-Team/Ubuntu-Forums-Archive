---
title: "CD ripping problem"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by rabbit2502 on 2008-05-16
I have a problem ripping cd's in Gutsy.i have about 95-100 m4p I-tunes song from my windows vista thta I want to convert to another format for use in Ubuntu. (i'm trying to get away from Windows totaly.) I have a dell Inspiron 531s with realtek sound card Simpron processor Nvidia Ge Force 6100 nForce430 512mb ram. The method I'm using is to burn all my i Tunes to cd and then rip them as mp3 or wav files to play in amarok. I tried ripping with sound juicer  
but all i get is static. BTW I'm dual booting with Vista on my HDD and Ubuntu on a usb Hdd. my dvd is a sata drive and cd rw is a usb extenal drive same problem ripping from both drives. Now the fun part I can rip these in Windows
to wav files reboot to Ubuntu and copy them to the Ubuntu drive and convert them with ffmpeg no problem. the static problem is not related to the cd's as this happens with all cds I have. Any Ideas? Windows is a pain I just as soon live without but for now I seem stuck.](*,)

---

### Post by .nedberg on 2008-05-16
Not sure what your problem is. I use Grip and have had no such problem. Give it a try! And remember to install lame if you want to make mp3's.

---

### Post by rabbit2502 on 2008-05-16
I have Grip and it does the same thing everything that's ripped when you try to play is just static, and the play time show as two to four time what it should be. I do have lame installed and it has no problems. I can use ffmpeg and take a flv music video and convert it to mp3 audio no problem. Can this be related to ALSA? or is it some strange  glich in my installation?

---

### Post by logos34 on 2008-05-16
Why don't you just [mount your windows partition]("http://www.psychocats.net/ubuntu/mountwindows") and read them directly? 

I just converted a lot of stuff from .m4a/alac/apple lossless and .aac to .flac and .ogg with [dBpoweramp Music Converter]("http://www.google.com/url?q=http://www.dbpoweramp.com/dmc.htm&sa=X&oi=smap&resnum=1&ct=result&cd=1&usg=AFQjCNHDMqPbwELJDkE2UMmF-PXtQrPr-w") on [Wine]("http://www.winehq.org/").  Perfect results. Even read the tags 95% correctly.  I was getting static or some problem with all of the linux tools I tried (SoundConverter, TransKode, etc.) and even Foobar2000 which everyone praises.   

dbpoweramp is also has the next best cd ripper to Exact Audio Copy (both of which can be run on wine)

---

### Post by rabbit2502 on 2008-05-17
Aye But there's the rub these are all purchased songs from I-tunes wich makes them M4P
and the only way I"ve found to access them without I-tunes is to burn them to CD and the rip them back with another program as a different file type such as mp3, ogg, flac,
ect. But the main problem is is this happens with all cd's not just one i've burned myself. Well maybe it'll go away in Hardy

---

### Post by rabbit2502 on 2008-05-17
Aye But there's the rub these are all purchased songs from I-tunes wich makes them M4P
and the only way I"ve found to access them without I-tunes is to burn them to CD and the rip them back with another program as a different file type such as mp3, ogg, flac,
ect. But the main problem is is this happens with all cd's not just one i've burned myself. Well maybe it'll go away in Hardy

---

### Post by logos34 on 2008-05-17
> **rabbit2502 said:**
> Aye But there's the rub these are all purchased songs from I-tunes wich makes them M4P

oh, missed the p...what a curse DRM is.

---

