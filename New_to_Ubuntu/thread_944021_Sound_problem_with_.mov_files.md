---
title: "Sound problem with *.mov files"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by braddcadd on 2008-10-10
I have several *.mov files.  The video plays but no sound.

This plays fine:
[http://www.youtube.com/watch?v=R_ixPPxqsr8&feature=dir](http://www.youtube.com/watch?v=R_ixPPxqsr8&feature=dir)

mp3's play fine too.

I have already changed all to alsa in System->Preferences->Sound but that didn't work either.  Any help?

---

### Post by entikryst on 2008-10-10
This happened to me on my mac but it seemed to work itself out.  Have you tried playing them in vlc?

---

### Post by braddcadd on 2008-10-10
Just tried it with no luck:
```

main warning: can't store message (Invalid or incomplete multibyte or wide character): found Box: 
main warning: can't store message (Invalid or incomplete multibyte or wide character): read box: "
main warning: can't store message (Invalid or incomplete multibyte or wide character): found Box: 
main warning: can't store message (Invalid or incomplete multibyte or wide character): read box: "
main warning: can't store message (Invalid or incomplete multibyte or wide character): found Box: 
main warning: can't store message (Invalid or incomplete multibyte or wide character): read box: "
[00000293] main decoder error: no suitable decoder module for fourcc `Qclp'.
VLC probably does not support this sound or video format.
[00000292] ffmpeg decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)
signal 2 received, terminating vlc - do it again in case it gets stuck
[00000280] main playlist: stopping playback

```

---

### Post by kansasnoob on 2008-10-10
If this is 8.04 (Hardy Heron) this has solved all of my sound problems:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

---

### Post by kansasnoob on 2008-10-10
> **kansasnoob said:**
> If this is 8.04 (Hardy Heron) this has solved all of my sound problems:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

I should also say that if you don't understand any part of that just ask.

I'm sure you'll notice there are 64 bit and i386 specific instructions.

---

### Post by braddcadd on 2008-10-10
No dice with that one either.  Yeah, I am running 32bit.  This one really has me stumped.

---

### Post by braddcadd on 2008-10-10
Maybe this can help someone diagnose:
```

** Message: don't know how to handle audio/x-gst-fourcc-Qclp, rate=(int)11025, channels=(int)1
** Message: Missing plugin: gstreamer|0.10|totem|audio/x-gst-fourcc-Qclp decoder|decoder-audio/x-gst-fourcc-Qclp (audio/x-gst-fourcc-Qclp decoder)
no application found
** Message: No installation candidate for missing plugins found.

```

---

### Post by kansasnoob on 2008-10-10
There's no way you ran through every step of that tutorial I posted in 10 minutes!

Are you running 8.04?

---

### Post by braddcadd on 2008-10-11
haha, well I actually not a beginner, but this problems has reduced me to the beginner forums!

Yes, 8.04.

---

### Post by Louis de Broglie on 2008-10-11
Try installing mplayer and it's codecs too. I can play .mov files ( with audio too ) in mplayer :)

---

### Post by braddcadd on 2008-10-11
No dice.

```

ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x706C6351.
Read DOCS/HTML/en/codecs.html!

```

html doc is not helping so far.

Which (mplayer) codecs did you install?

---

### Post by Louis de Broglie on 2008-10-12
I did a quick search in ubuntu repo. Seems like they are not available :(

But you can get them from here :

[http://www.archlinux.org/packages/search/?q=codecs](http://www.archlinux.org/packages/search/?q=codecs)

Download and install the "codecs" package of your architechture. Only drawback is you are not installing it via synaptic but at least it will solve the issue hopefully :)

How to install : Just extract the file in /

---

### Post by namaster on 2008-10-21
I still cant play and listen using mplayer also. Any idea how to do it? I did installed codecs and all but still no go.

---

### Post by braddcadd on 2008-10-26
bump

---

### Post by Threk on 2008-11-06
I had the exact same problem and I found an answer [here]("http://jamesreno.com/posts/20080921_1609_001.html")

I'll quote it in case the site goes away....
> 
JamesReno.com

mplayer - Cannot find codec for audio format 0x706C6351
If you are receiving errors similiar to this one, or have 'no sound in mplayer' the most likely cause is invalid codec paths.

Opening audio decoder: [qtaudio] QuickTime Audio Decoder
QuickTime6.3 DLLs found
QuickTime.qts patched!!! old entry=0x6693c3e0
theQuickTimeDispatcher catched -> 0x6693c3e0
WARNING! Invalid Ptr handle!
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x706C6351.
Read DOCS/HTML/en/codecs.html!
Audio: no sound

*** NOTE: This applies only to Linux.

After numerous hours of pure tourment I finally figured out how to play .3g2 files with mplayer.
My codecs were installed as suggested in /usr/lib/codecs and I had the symlink of /usr/local/lib/win32 -> /usr/lib/codecs however still no audio.

It seems that mplayer on various Linux Distributions does not follow the latest codec placement suggestions or they have modified mplayer to use the old paths.

Here is how i fixed it:

1. Download 'all-codecs' from mplayer download site
2. Extract these files into /usr/lib/codecs
2. Create Several Symlinks
  /usr/local/lib/codecs -> /usr/lib/codecs
  /usr/local/lib/win32 -> /usr/lib/codecs
  /usr/local/lib/w32 -> /usr/lib/codecs
  /usr/lib/win32 -> /usr/lib/codecs
  /usr/lib/w32 -> /usr/lib/codecs
 

Problem solved.


I got the "all-codecs" he mentioned from [http://www.mplayerhq.hu/design7/dload.html#binary_codecs]("http://www.mplayerhq.hu/design7/dload.html#binary_codecs")
As soon as I got it working I decided to use mencoder to convert all the files I had using qclp to something else so I won't have to hassle with this on other machines.

I hope this helps

---

### Post by braddcadd on 2008-11-07
Thanks for the hint.  I don't have a /usr/local/lib/codecs/ or /usr/lib/codecs folder.  
Would my codecs be stored somehwere else?  
Should I create these directories and follow you instructions?
How do I create a link for folders rather than files?

Thanks

---

### Post by Threk on 2008-11-08
If /usr/lib/codecs doesn't exist just create it, and then put all the extracted files from the download there.

Then just make the symlinks 

To symlink  /usr/lib/w32 -> /usr/lib/codecs ...
```
ln -s /usr/lib/codecs /usr/lib/w32
```

This way if you look in the folder /usr/lib/w32 you'll see the files in /usr/lib/codecs

Repeat that for all the locations listed in my previous post and no matter where mplayer and mencoder look they find the same codecs.

---

### Post by kansasnoob on 2008-11-08
Maybe:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by braddcadd on 2008-11-09
Thanks, but the codecs and symlinks didn't work for me.  I'm trying the comprehensive guide next.

---

### Post by wolvnmastr on 2009-01-03
> **braddcadd said:**
> Thanks, but the codecs and symlinks didn't work for me.  I'm trying the comprehensive guide next.

add the medibuntu repositories and the install the non-free codecs. works fine after that.  I had the same issue.

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free

---

### Post by wolvnmastr on 2009-01-04
> **wolvnmastr said:**
> add the medibuntu repositories and the install the non-free codecs. works fine after that.  I had the same issue.

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free

sorry ...you also have to get the key


Finally, close and save the sources file and install the Medibuntu key by copying and pasting the following command into the terminal:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by gurukatre on 2010-12-07
> **kansasnoob said:**
> If this is 8.04 (Hardy Heron) this has solved all of my sound problems:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)


hi guys 

i was also facing the same problem. in my Ubuntu karmic system.
i want to tell you there is one another option to play .mov file using browser. i used FireFox to run my .mov file 

:D

---

