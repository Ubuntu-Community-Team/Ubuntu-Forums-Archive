---
title: "To record your voice to a sound file with a microphone"
date: 2011-03-10
forum: Outdated Tutorials &amp; Tips
---

### Post by shantiq on 2011-03-10
Just record your voice with a microphone to a SOUND  file and leave it on your Desktop


WAV
===
     
     ```
ffmpeg -f alsa -ac 2 -i pulse   -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0  -y  ./Desktop/myVOICE.wav 
```


ALAC  M4A
=========
     
```
      ffmpeg -f alsa -ac 2 -i pulse -acodec alac  -y ./Desktop/RecordingMYvoice.m4a 
```

FLAC
====


```
      ffmpeg -f alsa -ac 2 -i pulse -acodec flac  -y ./Desktop/RecordingMYvoice.flac 
```




MP3
===



```
ffmpeg -f alsa -ac 2 -i pulse -acodec libmp3lame  -aq 0  -y ./Desktop/RecordingMYvoice.mp3
```


or else use -ab  



```
ffmpeg -f alsa -ac 2 -i pulse -acodec libmp3lame  -ab 320k  -y ./Desktop/RecordingMYvoice.mp3
```



M4A/AAC
=======
     


     
     ```
ffmpeg -f alsa -ac 2 -i pulse -acodec aac -strict experimental -ab 399k  -y ./Desktop/RecordingMYvoice.aac
```

===


USING neroAacEnc   for better quality aac

To maximize the quality of a voice recording to m4a/aac there is yet another route


Many say that **neroAacEnc** knocks spots of the other encoders (attached)


so since ffmpeg does not process that encoder a workaround goes like this

```
  ffmpeg -f alsa -ac 2 -i pulse   -y RecordingMYvoice.wav   && neroAacEnc -cbr 499000 -if RecordingMYvoice.wav -of RecordingMYvoice.m4a  && rm RecordingMYvoice.wav 
```


it seems to go as high as 516k but many will need a lower bitrate



ps    once you have the neroAacEnc in your home folder make sure to do this first

go  1. ```
sudo cp neroAacEnc /usr/bin
```
    2. ```
cd /usr/bin
```
    3. ```
sudo chmod +x neroAacEnc 
```



This should provide one with the highest possible m4a/aac file (alledgedly)
                    ------------------




OGG
===

ogg works with libvorbis not oggenc


so if you want to record from mike to ogg



```
ffmpeg -f alsa -ac 2 -i pulse -acodec libvorbis -ab 499k  -y ./Desktop/RecordingMYvoice.ogg

```

499k is the highest in ogg    set it yo what you want most people are probably happy with 120 or even less for voice only recordings



WMA
===


 i think that is lossless but i am not sure you end up with a 1000kbps about very high sound quality




```
ffmpeg -f alsa -ac 2 -i pulse -acodec wmav2 -ab 599k  -y ./Desktop/RecordingMYvoice.wma



```


TO WAV 64-BIT
=============


and for the fun bit if you love to hear your voice in perfect reproduction  why not treat yourself to Microsoft Wav (64-bit float)




your voice will be clearer than a bell   in the 5000kbps region    only for short messages   maybe a love declaration :::)))     maybe not your memoirs in an audio version    but that is clear God it is clear


```
ffmpeg -f alsa -ac 2 -i pulse -acodec pcm_f64le  -y ./Desktop/RecordingMYvoice.wav
```



will record an acoustic guitar off a mike in astounding clarity


for you musicians who cannot be BOTHERED fire up the big guns and want a quick but quality recording this certainly works then take it to audacity for polishing

---

### Post by shantiq on 2011-03-16
**And then** one could choose to use **SoX** instead which has much more intuitive code

```
sudo apt-get install sox

```
example


```
rec -b 32 -r 192000 myvoice.wv   gain +10

```


records your voice at 32-bit 192000Hz wavpack with increased volume


but more **normally** one could opt for


```
rec -b 16 -r 44100 myvoice.flac   gain +10

```


you can even add reverb if you wish to

```
rec -b 24 -r 44100 myvoice.flac   gain +12  reverb

```


these are the formats you can directly go to

AUDIO FILE FORMATS: > 8svx aif aifc [COLOR="Red"]aiff[/COLOR] aiffc al amb amr-nb amr-wb anb au avr awb caf cdda cdr cvs cvsd cvu dat dvms f32 f4 f64 f8 fap [COLOR="Red"]flac[/COLOR] fssd gsm gsrt hcom htk ima ircam la lpc lpc10 lu mat mat4 mat5 maud nist ogg paf prc pvf raw s1 s16 s2 s24 s3 s32 s4 s8 sb sd2 sds sf sl smp snd sndfile sndr sndt sou sox sph sw txw u1 u16 u2 u24 u3 u32 u4 u8 ub ul uw vms voc [COLOR="Red"]vorbis[/COLOR] vox w64 wav wavpcm [COLOR="Red"]wv[/COLOR] wve xa xi

---

### Post by shantiq on 2011-07-16
if you want to use SoX in a more normal way you can also pick your formats and bitrate very easily




```
rec  -C 320  nameyouwant.mp3

```   change kbps to suit you

NB   for mp3 you will have to add to program first as it not there by default ```
sudo apt-get install sox libsox-fmt-all
```



```
rec  -C 10  nameyouwant.ogg
```    from 1 to 10 for size

```
rec   nameyouwant.flac
```



combine info from previous post to jazz it up....

---

### Post by Jose Catre-Vandis on 2011-07-19
Yet more nice work shantiq, thank you :)

---

### Post by shantiq on 2011-07-19
Thank you Jose; SoX is just such an amazing program, so straightforward and UNUSUALLY for command-line software easy to understand for the average user:KS

---

### Post by geazzy on 2011-07-21
nice tutorial :)

---

