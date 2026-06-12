---
title: "How Can I Convert .flac to .mp3?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by FreewareFan on 2008-05-11
I know how to do this in Windows, but not in Ubuntu.  Is there a good program that will convert my .flac files to .mp3 format?

Doing a search in Synaptic only shows me programs that will play .flac, not convert them.

Thanks!

---

### Post by shifty_powers on 2008-05-11
soundconverter. find it in synaptic or:

```
sudo apt-get install soundconverter
```

---

### Post by FakeOutdoorsman on 2008-05-11
I beleive sound juicer can do this.  Soundconverter can as well if you enable the multiverse repo.
```
sudo aptitude install soundconverter gstreamer0.10-plugins-ugly-multiverse
```

If you like command-line you can use ffmpeg:
```
ffmpeg -i input.flac -ab 196k -ac 2 -ar 48000 output.mp3
```

However, ffmpeg in the repos has not been compiled with mp3 support due to legal reasons.  You can either use ffmpeg from the [Medibuntu repository]("https://help.ubuntu.com/community/iPodVideoEncoding?highlight=%28ipod%29#head-718248d42e047c1bdeda6e7e26665b1103b6b00f") or [build it from source]("http://ubuntuforums.org/showthread.php?t=786095") (tutorial).

---

### Post by disturbedite on 2008-05-11
it isn't a good idea to do this unless you really have to.  if you convert flac (a lossless format, which doesn't throw away any quality) to mp3 (a lossy format that *does* throw away quality) you will get audio degradation.
better explanation:
[http://en.wikipedia.org/wiki/FLAC#Comparisons](http://en.wikipedia.org/wiki/FLAC#Comparisons)

btw, it is ironic that your username is 'freewarefan' & you want to convert free audio format to a proprietary format.

---

### Post by shifty_powers on 2008-05-11
maybe flac into ogg?

syaing what you've said is all very well, but not all of us have the space to store all of our music as flac...

---

### Post by FreewareFan on 2008-05-11
Thank you ALL for your input and suggestions!  I truly appreciate the help!

FwF

---

### Post by FreewareFan on 2008-05-11
> **disturbedite said:**
> 

btw, it is ironic that your username is 'freewarefan' & you want to convert free audio format to a proprietary format.

Not so ironic when you stop to consider that my portable mp3 player does not handle .flac files....  Who would have thunk, eh?

---

### Post by zvacet on 2008-05-11
[Here]("http://www.arsgeek.com/?p=1044") After installing right click on nautilus-script-audio-convert and you will see what you can add.Second option is [pacpl]("http://pacpl.sourceforge.net/").It is text based but if you have Amarok installed you will have GUI.

---

### Post by Tom--d on 2008-05-11
Do:
```
sudo apt-get isntall liblame0
```
Thats the encoder for mp3.

then do, 
```
sudo apt-get install soundconverter
```

Open soundconverter, then, on settings.. change it to MP3. You will see.

Then drop your audio file in there and convert it :)

There :D
Its done.

---

### Post by Tintazul on 2008-06-06
soundconverter -- very nice tip, thanks! ;)

---

### Post by ian_hawdon on 2008-12-07
> **disturbedite said:**
> it isn't a good idea to do this unless you really have to.  if you convert flac (a lossless format, which doesn't throw away any quality) to mp3 (a lossy format that *does* throw away quality) you will get audio degradation.
better explanation:
[http://en.wikipedia.org/wiki/FLAC#Comparisons](http://en.wikipedia.org/wiki/FLAC#Comparisons)

Yeah, personally I use FLAC for backing up CDs, but either OGG (Preferred) or MP3 for iPodding. For the casual listening, I don't need superior quality, but I need a small format to fit on the iPod's "tiny" 60Gb hard drive!

Out of the lossies, I prefer OGG Vorbis, for it's better quality, and freeness :-) (and to play them on iPod, I use rockbox :-) )

---

### Post by mattlach on 2009-12-12
> **disturbedite said:**
> it isn't a good idea to do this unless you really have to.  if you convert flac (a lossless format, which doesn't throw away any quality) to mp3 (a lossy format that *does* throw away quality) you will get audio degradation.
better explanation:
[http://en.wikipedia.org/wiki/FLAC#Comparisons](http://en.wikipedia.org/wiki/FLAC#Comparisons)

btw, it is ironic that your username is 'freewarefan' & you want to convert free audio format to a proprietary format.

FLAC is really just a waste of disk space.

Hydrogenaudio.org did a double blinded study a few years ago, and found that even some of the biggest audiophiles, with expensive gear who claimed they could tell the difference, could not when comparing raw CD audio and a lame encoded mp3 with the alt-preset standard setting of the time.

Personally - since I don't have a disk space limitation, I prefer converting to mp3's for compatibility's sake.   Same reason I don't use ogg.

---

### Post by kelvin spratt on 2009-12-12
Perhaps they forgot to turn their hearing aids on.

---

### Post by mattlach on 2009-12-12
> **kelvin spratt said:**
> Perhaps they forgot to turn their hearing aids on.

Nah,
these guys are the real deal.

I once even read a hilarious thread on their forums about some dude who had poured a dewaxing agent in his ears so he could enjoy his $1000 headphones better, and was screaming with pain and posting about rushing to the emergency room :lol: :lol: :lol:

Audiophile forums are some of the best unintentional humor you can find out there :p

I fully support using flac or raw wav files for audio you intend to process, as you don't want to compound compression artifacts to the point where they really distort sound, but for stuff you just plan on listening to a VBR compressed mp3, with good settings (these days that alt-preset is gone, -V2 -Q2 ought to suffice)

---

### Post by kelvin spratt on 2009-12-12
Nah,
these guys are the real deal.

It was actually a paid publicity stunt to promote mp3, I remember it well.

---

### Post by Cheesemill on 2009-12-12
That's odd. I can definitely tell the difference between mp3 and flac, and my mp3's are ripped straight from the original source at 256 kB/s.

And it's a **big** difference as well.

---

### Post by mattlach on 2009-12-12
> **Cheesemill said:**
> 
And it's a **big** difference as well.

Placebo effect ;)

---

### Post by Cheesemill on 2009-12-12
> **mattlach said:**
> Placebo effect ;)

Nope, I've just tried again. Definitely more bass and crisper treble.

And none of the mp3 hiss either.

---

### Post by hgbso on 2009-12-15
does soundkonverter split the tracks of a flac image when it encodes to mp3

---

### Post by jessebean on 2010-01-28
Worked like a charm for me 
```
ffmpeg -i input.flac -ab 196k -ac 2 -ar 48000 output.mp3
```

---

### Post by cloyd on 2010-01-28
I'm new to Ubuntu, but have been messing with music files since I got a computer that would do it. I've never noticed degradation from mp3, ogg or even WMA's _except_ when there is a chain of conversions. (I believe you when you say there is degradation, I just don't hear it.) I remember making a  regular audio cd from wma that had been converted from  the original mp3 because I couldn't locate the original mp3. The difference was noticeable, but not drastic. It was noticeable enough that I didn't want to do it again.  I have avoided making more than one conversion of a file (mp3 to wma or ogg to conserve disc space). Don't use second generation files for audio cd's. Find your earliest copy of the file.

By the way, to join the conversation, I tried soundconverter just a few days ago. I think it works great.

---

### Post by kgr132 on 2010-05-19
Ditto the soundconverter. I used to use ffmpeg via command line but I lost the syntax I was using during my last upgrade via clean install (the only way). I made a few Preferences setting changes in soundconverter and I was off and running w/o the need to remember the command line options. In the words of more than a few Ubuntu fans: "it just worked"

---

