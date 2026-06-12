---
title: "Question about audio files for IPod on Linux..."
date: 2008-07-03
forum: New to Ubuntu
---

### Post by bertlacy on 2008-07-03
The one thing that I love about itunes is that is will convert you mp3's, etc to aac files...  Is there an app for Linux that will do the same?  Or, is there another file format that is like an aac file that will play on ipods???

---

### Post by kostkon on 2008-07-03
You can try [*Floola*]("http://www.floola.com/"). It is a very good iPod management application, although it's closed source (if you care about this).

It can convert on the fly to various formats, including *aac* using *FFMPEG* as its backend. But you'll need to install the version of *FFMPEG* that is in the [*Medibuntu*]("http://medibuntu.org/") repository and has support for restricted formats.

Add this repo to your software sources list, install *Floola* and try it.

---

### Post by bertlacy on 2008-07-03
Cool, thanks.
I will have to check that out.  I'm on my blackberry so I will have to install it later tonight but I will let you know how it works out. 

Thanks again!

---

### Post by kostkon on 2008-07-03
> **kostkon said:**
> Add this repo to your software sources list, install *Floola* and try it.
Oops, I forgot to say that you'll obviously need to install *FFMPEG* too.

---

### Post by bertlacy on 2008-07-03
Right on, I figured that.  Good looking out!

---

### Post by moore.bryan on 2008-07-03
gtkpod (in the repos, i think) syncs everything very nicely... i'm sure it converts. if not, soundkonverter is nice as a front to ffmpeg/mencoder.

---

### Post by bertlacy on 2008-07-03
Would you recommend sound convertor over foola?

---

### Post by moore.bryan on 2008-07-03
> **bertlacy said:**
> Would you recommend sound convertor over foola?
"soundkonverter" ;-)
never heard of/used foola, so go with whichever seems to fit your needs best; god i love linux.

---

### Post by ChameleonDave on 2008-07-03
> **bertlacy said:**
> The one thing that I love about itunes is that is will convert you mp3's, etc to aac files...  Is there an app for Linux that will do the same?  Or, is there another file format that is like an aac file that will play on ipods???

But why would you want to do that?  You will lose quality by converting to one lossy format from another.  And surely iPods are capable of playing MP3s?

If you really need to do the conversion, I personally would do it on the command line.

```

**sudo apt-get install** sox aacplusenc  *# This installs what we need.*
**sox** Yellow.mp3 Yellow.wav            *# This decodes the MP3*
**aacplusenc** Yellow.wav Yellow.aac 32  *# This encodes it as AAC, 32 bitrate*
**rm** Yellow.wav                        *# This deletes the temporary file*

```

When you run graphical utilities, they are actually just running these commands behind the scenes.

P.S. aacplusenc is in the Medibuntu repository, so you will have to add the following line to your* /etc/apt/sources.list* file if it's not there already:

```
deb http://packages.medibuntu.org/ hardy free non-free
```

---

### Post by bertlacy on 2008-07-03
Ok, first of all thank everyone for the replys but...  From what I understand, aac is a better quality sound file and smaller. I only have an ipod nano so space is a concern to me so if I could help it, I would like all my files to be in aac.

So... do I not want to convert my files to aac or something similar?

---

### Post by ChameleonDave on 2008-07-03
> **bertlacy said:**
> Ok, first of all thank everyone for the replys but...  From what I understand, aac is a better quality sound file and smaller. I only have an ipod nano so space is a concern to me so if I could help it, I would like all my files to be in aac.

So... do I not want to convert my files to aac or something similar?

Totally wrong.  You cannot increase the quality of a file by transcoding it.  A photograph of a person is a higher-quality reproduction than a quick pencil sketch of a person; but if you take a photograph of a pencil sketch, will it magically increase its quality so that it looks just like you took a photo of the person?

The size of the file depends on bitrate.  If your MP3 are big, the best option is to reencode them at a lower bitrate (but still as MP3s).  You will still lose quality though.

---

### Post by bertlacy on 2008-07-04
> **ChameleonDave said:**
> But why would you want to do that?  You will lose quality by converting to one lossy format from another.  And surely iPods are capable of playing MP3s?

If you really need to do the conversion, I personally would do it on the command line.

```

**sudo apt-get install** sox aacplusenc  *# This installs what we need.*
**sox** Yellow.mp3 Yellow.wav            *# This decodes the MP3*
**aacplusenc** Yellow.wav Yellow.aac 32  *# This encodes it as AAC, 32 bitrate*
**rm** Yellow.wav                        *# This deletes the temporary file*

```When you run graphical utilities, they are actually just running these commands behind the scenes.

P.S. aacplusenc is in the Medibuntu repository, so you will have to add the following line to your* /etc/apt/sources.list* file if it's not there already:

```
deb http://packages.medibuntu.org/ hardy free non-free
```


From what I see you have to make a temporary .wav file to convert it to aac.  Why can't you just encode the mp3 file straight to aac?

---

### Post by ChameleonDave on 2008-07-04
> **bertlacy said:**
> From what I see you have to make a temporary .wav file to convert it to aac.  Why can't you just encode the mp3 file straight to aac?

Why can't you directly convert a marble sculpture to a photocopy?  You just can't.  You have to take a photograph of the sculpture and then photocopy the photograph.

Audio files must be decoded before they can be re-encoded.  If you find a program that seems to do it in one step, it will actually be performing the two steps behind the scenes and deleting the temporary file without you seeing.  The only other way to do it would be to do it in chunks and hold the temporary chunks in RAM during the process, but juggling data like that can be inefficient.

The sox command is a good "Swiss army knife" tool than can handle many formats, so you can actually do stuff like "sox Music.mp3 Music.ogg" (with it deleting a temp file behind the scenes), but we can't do that in this case because Ubuntu's sox cannot output to patent-encumbered formats.

---

