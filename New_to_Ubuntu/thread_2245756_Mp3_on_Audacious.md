---
title: "Mp3 on Audacious"
date: 2014-09-25
forum: New to Ubuntu
---

### Post by Hankbonk on 2014-09-25
How do I get mp3 CODEC for "Audacious" in "Lubuntu 14.04" ?  If i use GNOMME Mediaplayer, it accepts mp3 URL's from Radio stations, but Audacius give the error
"No decoder found for <mp3 url stream file>"

---

### Post by mc4man on 2014-09-25
Can you post a sample url or 2?

---

### Post by Hankbonk on 2014-09-25
[http://mp3.streampower.be/radio1-high.mp3]("http://mp3.streampower.be/radio1.mp3")
[http://mp3.streampower.be/ra2wvl]("http://mp3.streampower.be/ra2wvl.mp3")[1-high]("http://mp3.streampower.be/radio1.mp3")[.mp3]("http://mp3.streampower.be/ra2wvl.mp3")

---

### Post by andrew.46 on 2014-09-26
These streams 404 here....

---

### Post by Hankbonk on 2014-09-26
They were not correct : I've corrected them in the same reply, ok ?

---

### Post by coldcritter64 on 2014-09-26
> **The file you requested could not be found** Is the response I get on both those links from the site. Looks like the links are no longer valid. 

Can you play normal mp3 files in audacious, not online urls ? I'm asking just to check that you have the right codecs in your installation.

---

### Post by Hankbonk on 2014-09-26
They were not correct, these are :
 			 				[INDENT] 					[http://mp3.streampower.be/radio1-high.mp3]("http://mp3.streampower.be/radio1.mp3")
[http://mp3.streampower.be/ra2wvl]("http://mp3.streampower.be/ra2wvl.mp3")[1-high]("http://mp3.streampower.be/radio1.mp3")[.mp3]("http://mp3.streampower.be/ra2wvl.mp3") 				[/INDENT]

---

### Post by Rob Sayer on 2014-09-26
"No decoder found" sounds a wee bit like a missing codec.  If you haven't already, install the proprietary ones:

```
sudo apt-get update
sudo apt-get install lubuntu-restricted-extras
```

That's one of the first things I do in a new ubuntu install.

---

### Post by coldcritter64 on 2014-09-26
> **Hankbonk said:**
> They were not correct, these are :[INDENT]                     [http://mp3.streampower.be/radio1-high.mp3]("http://mp3.streampower.be/radio1.mp3")
[http://mp3.streampower.be/ra2wvl]("http://mp3.streampower.be/ra2wvl.mp3")[1-high]("http://mp3.streampower.be/radio1.mp3")[.mp3]("http://mp3.streampower.be/ra2wvl.mp3")                 
[/INDENT]


And again with the 2 above as you've posted them here,
> **The file you requested could not be found** 

And again from my last post...
Question:
> Can you play normal mp3 files in audacious, not online urls ?

Please try a normal mp3 in audacious to rule out codec problems. If audacious plays a normal mp3 then the above links are invalid.

You've got 2 helpers reporting dead links,
>                           These streams 404 here....         from andrew.46, and I get the bolded message shown above. Please check audacious with a normal mp3 please to help narrow down what the problem is.

---

### Post by mc4man on 2014-09-26
I'm gathering you're getting from here? - 
[http://www.online-radio-luisteren.be/radiostreams.php](http://www.online-radio-luisteren.be/radiostreams.php)
In any event works ok here, as in 
```
audacious http://mp3.streampower.be/radio1-high.mp3
```

I think the issue as far as this thread is that the posted links copy out wrong, the -high is missing, ie.
[http://mp3.streampower.be/radio1.mp3](http://mp3.streampower.be/radio1.mp3)
is supposed to be 
[http://mp3.streampower.be/radio1-high.mp3](http://mp3.streampower.be/radio1-high.mp3)
ect.

---

### Post by coldcritter64 on 2014-09-26
> **mc4man said:**
> ...
I think the issue as far as this thread is that the posted links copy out wrong, the -high is missing, ie.
[http://mp3.streampower.be/radio1.mp3](http://mp3.streampower.be/radio1.mp3)
is supposed to be 
[http://mp3.streampower.be/radio1-high.mp3](http://mp3.streampower.be/radio1-high.mp3)
ect.

OP, Clicking the second link above works now as mc4man has posted them. That could explain the 404 of andrew.46's and my previously posted errors. Your first post suggests a missing codec. Rob Sayer's suggestion may help you if that is the case. Cheers.

---

### Post by mc4man on 2014-09-26
You could try the restricted extras though by default aud should decode mp3 thru either of 2 plugins - 
madplug.so or ffaudio.so

Ex. on amd_64 install, version numbers irrelevant

```
ldd  /usr/lib/x86_64-linux-gnu/audacious/Input/madplug.so
	linux-vdso.so.1 =>  (0x00007fffcc826000)
	libaudcore.so.2 => /usr/lib/x86_64-linux-gnu/libaudcore.so.2 (0x00007f0827e80000)
	[COLOR="#FF0000"]libmpg123.so.0 [/COLOR]=> /usr/lib/x86_64-linux-gnu/libmpg123.so.0 (0x00007f0827c29000)
	libaudtag.so.1 => /usr/lib/x86_64-linux-gnu/libaudtag.so.1 (0x00007f0827a1d000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f0827657000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f0827439000)
	libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007f0827130000)
	libguess.so.1 => /usr/lib/x86_64-linux-gnu/libguess.so.1 (0x00007f0826f29000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f0826c23000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f08282bd000)
	libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f08269e4000)
	libmowgli-2.so.0 => /usr/lib/x86_64-linux-gnu/libmowgli-2.so.0 (0x00007f08267c5000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f08265c1000)
```

or 
```
ldd  /usr/lib/x86_64-linux-gnu/audacious/Input/ffaudio.so 
	linux-vdso.so.1 =>  (0x00007fff8048f000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fd6c7e41000)
	libaudcore.so.2 => /usr/lib/x86_64-linux-gnu/libaudcore.so.2 (0x00007fd6c7c30000)
	libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007fd6c7927000)
	[COLOR="#FF0000"]libavcodec.so.56[/COLOR] => /usr/lib/x86_64-linux-gnu/libavcodec.so.56 (0x00007fd6c69e3000)
	libavformat.so.56 => /usr/lib/x86_64-linux-gnu/libavformat.so.56 (0x00007fd6c66a8000)
	libavutil.so.54 => /usr/lib/x86_64-linux-gnu/libavutil.so.54 (0x00007fd6c647b000)
	libaudtag.so.1 => /usr/lib/x86_64-linux-gnu/libaudtag.so.1 (0x00007fd6c6270000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fd6c5eaa000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fd6c828d000)
	libguess.so.1 => /usr/lib/x86_64-linux-gnu/libguess.so.1 (0x00007fd6c5ca2000)
	libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007fd6c5a64000)
	libavresample.so.2 => /usr/lib/x86_64-linux-gnu/libavresample.so.2 (0x00007fd6c5846000)
	libxvidcore.so.4 => /usr/lib/x86_64-linux-gnu/libxvidcore.so.4 (0x00007fd6c5507000)
	libx264.so.142 => /usr/lib/x86_64-linux-gnu/libx264.so.142 (0x00007fd6c5171000)
	libvpx.so.1 => /usr/lib/x86_64-linux-gnu/libvpx.so.1 (0x00007fd6c4d92000)
	libvorbisenc.so.2 => /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2 (0x00007fd6c48c2000)
	libvorbis.so.0 => /usr/lib/x86_64-linux-gnu/libvorbis.so.0 (0x00007fd6c4695000)
	libvo-amrwbenc.so.0 => /usr/lib/x86_64-linux-gnu/libvo-amrwbenc.so.0 (0x00007fd6c447b000)
	libvo-aacenc.so.0 => /usr/lib/x86_64-linux-gnu/libvo-aacenc.so.0 (0x00007fd6c425d000)
	libtheoraenc.so.1 => /usr/lib/x86_64-linux-gnu/libtheoraenc.so.1 (0x00007fd6c401d000)
	libtheoradec.so.1 => /usr/lib/x86_64-linux-gnu/libtheoradec.so.1 (0x00007fd6c3e04000)
	libspeex.so.1 => /usr/lib/x86_64-linux-gnu/libspeex.so.1 (0x00007fd6c3bea000)
	libschroedinger-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libschroedinger-1.0.so.0 (0x00007fd6c3926000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007fd6c370d000)
	libopus.so.0 => /usr/lib/x86_64-linux-gnu/libopus.so.0 (0x00007fd6c34c4000)
	libopenjpeg.so.2 => /usr/lib/x86_64-linux-gnu/libopenjpeg.so.2 (0x00007fd6c32a2000)
	libopencore-amrwb.so.0 => /usr/lib/x86_64-linux-gnu/libopencore-amrwb.so.0 (0x00007fd6c308e000)
	libopencore-amrnb.so.0 => /usr/lib/x86_64-linux-gnu/libopencore-amrnb.so.0 (0x00007fd6c2e63000)
	libmp3lame.so.0 => /usr/lib/x86_64-linux-gnu/libmp3lame.so.0 (0x00007fd6c2bd6000)
	libgsm.so.1 => /usr/lib/x86_64-linux-gnu/libgsm.so.1 (0x00007fd6c29c8000)
	libfdk-aac.so.0 => /usr/lib/x86_64-linux-gnu/libfdk-aac.so.0 (0x00007fd6c271a000)
	libva.so.1 => /usr/lib/x86_64-linux-gnu/libva.so.1 (0x00007fd6c2504000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fd6c21fe000)
	librtmp.so.1 => /usr/lib/x86_64-linux-gnu/librtmp.so.1 (0x00007fd6c1fe1000)
	libgnutls.so.28 => /usr/lib/x86_64-linux-gnu/libgnutls.so.28 (0x00007fd6c1cd4000)
	libbz2.so.1.0 => /lib/x86_64-linux-gnu/libbz2.so.1.0 (0x00007fd6c1ac3000)
	libmowgli-2.so.0 => /usr/lib/x86_64-linux-gnu/libmowgli-2.so.0 (0x00007fd6c18a4000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fd6c169f000)
	libogg.so.0 => /usr/lib/x86_64-linux-gnu/libogg.so.0 (0x00007fd6c1496000)
	liborc-0.4.so.0 => /usr/lib/x86_64-linux-gnu/liborc-0.4.so.0 (0x00007fd6c1213000)
	libhogweed.so.2 => /usr/lib/x86_64-linux-gnu/libhogweed.so.2 (0x00007fd6c0fe5000)
	libnettle.so.4 => /usr/lib/x86_64-linux-gnu/libnettle.so.4 (0x00007fd6c0db5000)
	libgmp.so.10 => /usr/lib/x86_64-linux-gnu/libgmp.so.10 (0x00007fd6c0b41000)
	libp11-kit.so.0 => /usr/lib/x86_64-linux-gnu/libp11-kit.so.0 (0x00007fd6c08ff000)
	libtasn1.so.6 => /usr/lib/x86_64-linux-gnu/libtasn1.so.6 (0x00007fd6c06ea000)
	libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007fd6c04e2000)

```

---

### Post by Hankbonk on 2014-09-26
How do you explain then that, using one of the mentioned URL-streams, the GNOME Mediaplayer does play the radio station with the exact URL ?

---

### Post by mc4man on 2014-09-26
> **Hankbonk said:**
> How do you explain then that, using one of the mentioned URL-streams, the GNOME Mediaplayer does play the radio station with the exact URL ?
The url's you're using & what you have posted are not the same.
(- even though they say -high if people copy or click on them the -high is missing for some reason

Please run this in a terminal & post results

```
audacious http://mp3.streampower.be/radio1-high.mp3
```

---

### Post by Hankbonk on 2014-09-28
now audacious plays !?? thank you mc4man !

---

