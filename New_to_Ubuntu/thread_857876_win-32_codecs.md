---
title: "win-32 codecs"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by DarinB on 2008-07-12
i installed the w32 codecs from the medbuntu site 
then got an update > now how do i make it work???
it did say not authenticated not sure what that means???
i tried opening the wma and it still won't play with vlc or rhythm box either
after i install is there something else i need to do????

---

### Post by phidia on 2008-07-13
Take a look at the section titled *Manual Method* from [this thread]("http://ubuntuforums.org/showthread.php?t=766683&highlight=codec"). Hopefully you can use that to get the repo enabled.

---

### Post by DarinB on 2008-07-13
i have the codec installed i simply don't know what to do next???
or is it automatic????
is there a preference in rhythmbox or vlc player i have to check????

---

### Post by aktiwers on 2008-07-13
```
sudo apt-get install ubuntu-restricted-extras 
```

Always install almost everything for me..  Using medubuntu or this should make the codecs work automatically.

---

### Post by DarinB on 2008-07-13
with what player???
i have the codecs installed i checked synaptic the w32 codec is there i added the non free w32 codec as well but that didn't do anything...i hate to ask but do i need to reboot or is that M$ BS that is still in my head??????

---

### Post by aktiwers on 2008-07-13
There should be no need to reboot..  only on kernel updates and stuff with the kernel.

Have you tested if it works? And did you install the package I suggested above? It has all the needed stuff to play movies and sound

---

### Post by DarinB on 2008-07-13
i wonder i checked it is installed so i tried to convert it to mp3 with audiacity and i get the error can't open patented music????
is that the DRM thing????

---

### Post by SunnyRabbiera on 2008-07-13
> **DarinB said:**
> i wonder i checked it is installed so i tried to convert it to mp3 with audiacity and i get the error can't open patented music????
is that the DRM thing????

might be, unless you still need the mp3 codec

---

### Post by 3rdalbum on 2008-07-13
I don't think Audacity opens WMAs directly. Is this audio file from a music store? If so, it's encrypted. Try using a real music store :-)

---

### Post by Sef on 2008-07-13
> Is this audio file from a music store? If so, it's encrypted.

Not necessarily encrypted.  But if it is encrypted, then it won't play on Ubnuntu.

---

### Post by DarinB on 2008-07-13
i have them and have mainly mp3's and M4A or AAC just one or two ogg's
i simply had a wma and wanted to play it.
i checked i have the medibuntu repos and Win32 codec binaries
This package contains Win32 codec binaries, required for the
decompression of video formats that have no open source
alternative.
This package is in Medibuntu because of its non-free license.
it updated after i installed it 
then i added the Non-free codecs
This package depends on the binaries codecs package matching your architecture
(w32codecs for i386, w64codecs for amd64 and ppc-codecs for powerpc systems).
so really dumb shouldn't i be able to open song with my vlc player or with rhythm box i get errors "the Gstreamer needed to decode not found"

---

### Post by DarinB on 2008-07-13
hum thats good information i will try a diferent wma file
thank you that one is probably encrypted.

---

### Post by mc4man on 2008-07-13
Vlc can play back some .wma files, i don't use them anymore so I may have some of this wrong. I know it will playback plain .wma (cbr) and won't play the lossless type. As I remember there's 2 other types, windows media pro, and windows media vbr. Those I don't know about.

Amarok and mplayer will play the lossless, cbr, and probably the other 2.
The latest smplayer now has an equalizer if that's a factor and will obviously play anything mplayer can.

I believe other common players (banshee, audacious, rhythm box  are similar to vlc in wma support.

The sound files preview  (with totem-xine as default totem player) should also work with the lossless, ect. (quick way to ck. on drm which won't play)

---

