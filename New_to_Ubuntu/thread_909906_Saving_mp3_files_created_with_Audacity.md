---
title: "Saving mp3 files created with Audacity"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by pkj on 2008-09-04
Hi,
Have created audio tracks using Audacity...

How do i save them in mp3 format..
Help told me to use Export option..
However, this gives me the following error..
"Audacity needs file libmp3lame.so.0 to create mp3s'
Location of libmp3lame.so.0 ---Browse

To get free copy of Lame, click here ----> Download

I downloaded Lame using Syneptic as the above download option presented by Audacity dosen't seem to work

But it did not solve my problem...

Help required urgently, as my project is stuck-up

pkj

---

### Post by Pro-reason on 2008-09-04
Click on “Find library”.

Insert the path to the library.  It is probably “/usr/lib/libmp3lame.so.0”.

---

### Post by pkj on 2008-09-04
I checked using terminal...

/usr/lib

libmp3lame.so.0 is not listed there

pkj

---

### Post by Pro-reason on 2008-09-04
> **pkj said:**
> I checked using terminal...

/usr/lib

libmp3lame.so.0 is not listed there

pkj
Do this in the terminal:

```

sudo apt-get install lame
sudo updatedb
locate mp3lame

```

What do you get?

---

### Post by pkj on 2008-09-04
Tried ...

locate mp3lame does not produce any output..

pkj

---

### Post by Pro-reason on 2008-09-04
If you can't get Audacity to save to MP3, then simply save in a lossless format (FLAC, WAV...) and then convert to MP3 later, using the command line or a conversion app.

Either install SoundConverter in Synaptic, and use that, or else use LAME on the command line:

```

lame myaudioclip.wav

```

---

### Post by lian1238 on 2008-09-04
For me, I think I had the same problem. I googled the problem and solved it, but can't remember what I installed exactly. I can now go to File->Export and choose MP3.

Edit: By the way, did you copy and pasted the three commands Pro-reason suggested? If so, try running them one by one. Maybe there was a prompt from command#1, e.g. the installation was not done.

---

### Post by Pro-reason on 2008-09-04
> **pkj said:**
> Tried ...

locate mp3lame does not produce any output..

pkj

Strange.  Did LAME install properly?  (Type &#8220;lame --help&#8221; to check.)

It should pull in *liblame0* as a dependency.  Let's install it manually.

```

sudo apt-get install --reinstall **liblame0**
dpkg -L **liblame0**

```

The second command should list all the files installed by that package, and they should include */usr/lib/libmp3lame.so.0*.

---

### Post by pkj on 2008-09-04
Tried saving in wav format..

But getting this error

Cannot export audio to /home/pradeep/Desktop/music on the floor/temp1.wav

Really don,t undersatand where am i going wrong..

pkj

---

### Post by pkj on 2008-09-04
lame --help produces this output

LAME 32bits version 3.97 ([http://www.mp3dev.org/](http://www.mp3dev.org/))

usage: lame [options] <infile> [outfile]

    <infile> and/or <outfile> can be "-", which means stdin/stdout.

RECOMMENDED:
    lame -V2 input.wav output.mp3

OPTIONS:
    -b bitrate      set the bitrate, default 128 kbps
    -h              higher quality, but a little slower.  Recommended.
    -f              fast mode (lower quality)
    -V n            quality setting for VBR.  default n=4
                    0=high quality,bigger files. 9=smaller files
    --preset type   type must be "medium", "standard", "extreme", "insane",
                    or a value for an average desired bitrate and depending
                    on the value specified, appropriate quality settings will
                    be used.
                    "--preset help" gives more info on these

    --longhelp      full list of options
pkj

---

### Post by Pro-reason on 2008-09-04
> **pkj said:**
> lame --help produces this output


It looks like LAME is installed OK.  Does it actually work?  Try it on any WAV file.  (You can find a file by typing “locate .wav”.)

---

### Post by Pro-reason on 2008-09-04
> **pkj said:**
> Tried saving in wav format..

But getting this error

Cannot export audio to /home/pradeep/Desktop/music on the floor/temp1.wav

Really don,t undersatand where am i going wrong..

pkj

And you definitely chose “WAV, AIFF, and other compressed types” when exporting (rather than just putting .wav on the end)?

Perhaps you could try clicking on “Options” in the export dialogue.

---

### Post by pkj on 2008-09-04
Tried lame on a wav file

program appeared to run with the following output..
pradeep@pradeep-desktop:~/Desktop$ lame temp11.wav 
LAME 3.97 32bits ([http://www.mp3dev.org/](http://www.mp3dev.org/))
CPU features: MMX (ASM used), 3DNow! (ASM used), SSE
Using polyphase lowpass filter, transition band: 16538 Hz - 17071 Hz
Encoding temp11.wav to temp11.wav.mp3
Encoding as 44.1 kHz 128 kbps j-stereo MPEG-1 Layer III (11x) qval=3
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
 15947/15947 (100%)|    1:22/    1:22|    1:40/    1:40|   5.0196x|    0:00 
----------------------------------------------------------------------------------------------------------------------------
   kbps        LR    MS  %     long switch short %
  128.0        1.2  98.8        85.8   8.3   5.9
Writing LAME Tag...done
ReplayGain: +5.3dB
pradeep@pradeep-desktop:~/Desktop$ 

However there was no sound...

pkj

---

### Post by pkj on 2008-09-04
Yes i definitely chose WAV, AIFF, and other compressed types&#8221; option

pkj

---

### Post by Pro-reason on 2008-09-04
> **pkj said:**
> 

However there was no sound...

pkj

Why were you expecting sound?  Did you try to play it after converting it?  It looks like it converted correctly.

---

### Post by pkj on 2008-09-04
Totem is not playing .wav.mp3 file which has been created..

Says suitable codecs not found..

Anyway the original problem is un-answered as to how to save the Audacity file..

pkj

---

### Post by Pro-reason on 2008-09-04
> **pkj said:**
> Totem is not playing .wav.mp3 file which has been created..

Says suitable codecs not found..

Anyway the original problem is un-answered as to how to save the Audacity file..

pkj

This problem may be related.

In any case, you haven't mentioned whether you tried the other step I mentioned.

---

### Post by pkj on 2008-09-04
Using add/remove programs, i re-installed Lame using multiverse repo...

Now i can save the files in mp3 format..

wav is still not happening

also, the quality of sound of the saved file in mp3 format is very inferior to the original quality when heard via audacity..any suggestions to improve the quality of sound

pkj

---

### Post by Pro-reason on 2008-09-04
Do this in a terminal:

```

gksu gedit /etc/apt/sources.list

```

Then add this to the end of the file:

```

deb http://packages.medibuntu.org/ hardy free non-free
#deb-src http://packages.medibuntu.org/ hardy free non-free

```

Save and close.

Then do this in the terminal:

```

sudo apt-get update
sudo apt-get install medibuntu-keyring non-free-codecs

```

That should enable MP3 codecs for Totem.

---

### Post by pkj on 2008-09-04
The problem may not be with Totem as even when i am importing this file back to audacity and playing, the quality of sound is inferior.

Does it has anything to do with the sample/bit rate using which i am saving the file.

I am however trying the suggestion of yours  of enabling codecs for totem
pkj

---

### Post by pkj on 2008-09-04
Also i have not understood why files are not being saved in wav format
pkj

---

### Post by pkj on 2008-09-04
Why wav files are not being saved via audacity also is not clear

pkj

---

### Post by Bucky Ball on 2008-09-04
In Audacity, from memory, you need to tweak the settings in preferences or some such and up the quality of your mp3 export file (doesn't give you an option on the fly, you need to set that first then export). Have you actually used this powerful, flexible, lightweight audio manipulation program before? Don't be fooled by the meagre gui - it is common in studios from home to high-end. If not, you might find this of interest:

[http://www.wikieducator.org/Using_Audacity](http://www.wikieducator.org/Using_Audacity)

There is a lot of info out there regarding this popular audio tool. (incidentally, flac is the go unless there is really a need for mp3 and wav is a microsoft creation so always going to be a little buggy in linux ... unless some miracle happens at their end) :)

---

### Post by Pro-reason on 2008-09-04
> **pkj said:**
> Using add/remove programs, i re-installed Lame using multiverse repo...

Ah yes, you should definitely make sure that all the repos are enabled.

> **pkj said:**
> 
Now i can save the files in mp3 format..

also, the quality of sound of the saved file in mp3 format is very inferior to the original quality when heard via audacity..any suggestions to improve the quality of sound

pkj

That is normal.  MP3 is a lossy compression codec.  The results are always worse than the original.  It is very much like JPEG.

You can choose different bitrates in Audacity.  Just click on &#8220;Options&#8221; in the export dialogue.  At high levels, the MP3 will be large, but the quality will be almost as good as the original.  At low levels, the file will be small, but the quality will be noticeably bad.  Choose the level you want.

All this raises the question of why you want to export as MP3 anyway.  MP3 is a proprietary codec, and is inferior in quality to OGG Vorbis.  Unless you intend to play the files on an MP3 player which doesn't support other formats, you should almost certainly reject MP3 and instead use OGG Vorbis (lossy) or FLAC (lossless) compression.

I never use MP3 myself.  I have FLAC files on my computer and FLAC or OGG Vorbis on my iRiver E100 personal audio player.

If you intend to ever do any further work on these files (edit them again, or burn them to an audio CD), then you should definitely use lossless compression.

I don't know why you are having trouble exporting uncompressed files.  Try choosing &#8220;WAV, AIFF, and other uncompressed types&#8221; and then clicking on &#8220;options&#8221;.  Fiddle with the settings until it works.

See also the [Audacity documentation regarding LAME]("http://audacityteam.org/wiki/index.php?title=Lame_Installation").

---

### Post by Bucky Ball on 2008-09-04
[QUOTE=Pro-reason]You can choose different bitrates in Audacity.  Just click on &#8220;Options&#8221; in the export dialogue.[/QUOTE]

Exactly what I was trying to say! Haven't used Audacity in awhile. :)

Pro-reason, is your nick a hybrid of two audio softwares that don't work in Linux? Wish they would. ;( Then I wouldn't be using my XP box at all (except of course for Sibelius).

---

### Post by pkj on 2008-09-04
Saving files as FLAC was good...
I then converted to wav (to play in my audio system) using k3b..

Thanks to all of u...It did really help,,,,

pkj

---

### Post by Bucky Ball on 2008-09-04
Cool, glad to hear it and be of help. You can mark your thread as 'solved' in 'Thread Tools' so others can surf here for a fix. :)

---

### Post by snkr on 2008-11-13
thankyou verymuch proreason... i had the same problem and now it got fixed...

---

