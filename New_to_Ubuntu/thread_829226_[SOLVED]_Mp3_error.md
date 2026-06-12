---
title: "[SOLVED] Mp3 error"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-06-14
I receive an error when I try to plat a Mp3 file. Audio codec 'Windows Media Audio Lossless' is not handled. You might need to install additional plugins to be able to play some types of movies. I tried to locate additional files in both, the Add & Delete as well as System/Admin/SynPkgMgr with out any luck. Any ideas ??? Thanks

---

### Post by halitech on 2008-06-14
you probably need to install the Win32 codecs which aren;t standard so you will need to enable additional repos to get them.

---

### Post by SunnyRabbiera on 2008-06-14
yeh you need the codecs, but they are easy to get.

---

### Post by CoCoKnots on 2008-06-14
Great... Now, How do I go about getting them ?

---

### Post by avtolle on 2008-06-14
You need to add the Medibuntu repository for that, IIRC. [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) is a how-to to do it. Good luck.

---

### Post by CoCoKnots on 2008-06-14
Well, Not sure why... I added a bunch of stuff as indicated in the links noted. Looks like things are happening on my termonal page... Still doesn't make any difference in playing the Mp3 files.

---

### Post by avtolle on 2008-06-14
Just a thought; after installing all the software from Medibuntu, were there any updates that have appeared that you've not downloaded? Or, another thought, after installing the Medibuntu stuff, did you restart your system?

---

### Post by CoCoKnots on 2008-06-14
Good Point Avtolle, I did receive a message about new updates... I am downloading them now. I haven't rebooted my system... It sounds like I should do that after my downloads are complete ???

---

### Post by CoCoKnots on 2008-06-14
OK... I'm back. I finished the downloads & re-booted the system. I tried to run a Mp3 file & still received the same error. Anything else I should try ?

---

### Post by ad_267 on 2008-06-14
Read this: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

If you've enabled the universe and multiverse repositories you can just install the ubuntu-restricted-extras package.

---

### Post by CoCoKnots on 2008-06-14
Thanks, I had already tried this. I did it again just to make certain everything took. It came back with -0- updated & 'already exist. I'm still not sure where I'm suppose to find these 'codecs' & how to install them... Or was this it ?

---

### Post by avtolle on 2008-06-14
That message indicates that the codecs are installed. I'm wondering if the problem you are having involves some recent new Windows app that uses a method for which no reverse-engineered codecs exist as of yet?

---

### Post by ad_267 on 2008-06-14
Yeah where did this mp3 file come from? Are you sure it's actually an mp3 and not using some other codec?

---

### Post by CoCoKnots on 2008-06-14
I had not considered that as a possibility. How can I test it to find out... Is there a source for a 'true, clean mp3' file to check this out ?

---

### Post by ad_267 on 2008-06-14
You can browse to the file in a terminal and run 

```
file "name of mp3.mp3"
```

There's probably a more specific way but that should tell you something.

Edit: Also just right click on the file in Nautilus and go to Properties - Audio and see what it tells you about the codec.

---

### Post by cozmicharlie on 2008-06-14
> **CoCoKnots said:**
> I receive an error when I try to plat a Mp3 file. Audio codec 'Windows Media Audio Lossless' is not handled. You might need to install additional plugins to be able to play some types of movies. I tried to locate additional files in both, the Add & Delete as well as System/Admin/SynPkgMgr with out any luck. Any ideas ??? Thanks

I think ad_267 is correct.  The error message states "Windows Media Audio Lossless" is not handled.  Mp3 is not lossless so the file is most likely not an mp3.  You can find an mp3 to download here "http://www.archive.org/details/etree" or just browse the internet and find one.

---

### Post by avtolle on 2008-06-14
[http://en.wikipedia.org/wiki/Windows_Media_Audio](http://en.wikipedia.org/wiki/Windows_Media_Audio) It looks like that file is most definitely **not** an mp3, but a WMA type file.

---

### Post by cariboo on 2008-06-14
Again, look at the error message **Windows Media Audio Lossless** that isn't an mp3 files it is a misnamed wma file. Maybe just change the extension to **wma** and see what happens. I doubt there are any codecs to play this type of media file.

Jim

---

### Post by CoCoKnots on 2008-06-14
BINGO... You were right on. I tried looking in the Terminal page & it came back with errors... I then downloaded another Mp3 file & it works fine... Thanks All, Cal

---

### Post by ad_267 on 2008-06-14
You could try renaming it and change the file extension to .wma and it may help. It may be that that file is corrupted too.

---

### Post by ferdaus98 on 2008-10-05
The following is error message while trying to run Totem Movie Player Xine **¨Audio codec 'Windows Media Audio Lossless' is not handled. You might need to install additional plugins to be able to play some types of movies**

---

