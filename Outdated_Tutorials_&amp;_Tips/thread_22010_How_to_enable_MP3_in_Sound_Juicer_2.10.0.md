---
title: "How to enable MP3 in Sound Juicer 2.10.0"
date: 2005-03-25
forum: Outdated Tutorials &amp; Tips
---

### Post by ruff on 2005-03-25
Found this and thought it might be of use to some:

[http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)

It is a great little how-to on getting Sound Juicer 2.10.0 to rip mp3 - and it works  \\:D/ 

Cheers,

Ruff

---

### Post by vaskark on 2005-03-28
Thanks for the link. Would you also happen to kow how to get Sound Juicer to encode at more than 160 Kbps? I just ripped some songs using the Hoary Live CD and would like to know how to increase the encoding quality so I'll know when I install hoary to it's own partition.

Thanks!

---

### Post by jasplund on 2005-04-04
[QUOTE=vaskark]Thanks for the link. Would you also happen to kow how to get Sound Juicer to encode at more than 160 Kbps? I just ripped some songs using the Hoary Live CD and would like to know how to increase the encoding quality so I'll know when I install hoary to it's own partition.

Thanks![/QUOTE]

How did you manage to encode at 160 kbps? I can only encode at 256

---

### Post by vaskark on 2005-04-06
[QUOTE=ruff]Found this and thought it might be of use to some:

[http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html]("http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html")

It is a great little how-to on getting Sound Juicer 2.10.0 to rip mp3 - and it works  \\:D/ [/QUOTE]

I followed these instructions, but when I added 'quality=0.6' to the Gstreamer pipeline part I received this error when trying to rip in Sound Juicer:

Sound Juicer could not extract this CD
Reason: Could not create Gstreamer encoder ((null))

So is this a bug, or can we not increase the encoding rate? 128 Kbps is not enough for me.

P.S. The instructions worked fine.

---

### Post by Nis on 2005-04-06
Try adding preset=1002 to the end of the gsteamer profile line.  You can also make it preset=1003 (which is the 'Extreme' setting) or preset=1004 ('Insane' setting).  You'll also need the gstreamer0.8-mad package, which you can get from the marillat repository.

---

### Post by jasplund on 2005-04-07
[QUOTE=Nis]Try adding preset=1002 to the end of the gsteamer profile line.  You can also make it preset=1003 (which is the 'Extreme' setting) or preset=1004 ('Insane' setting).  You'll also need the gstreamer0.8-mad package, which you can get from the marillat repository.[/QUOTE]
 I get "Sound Juicer could not extract this CD
Reason: Could not create Gstreamer encoder ((null))" When I put preset=1002 at the end of the line. Yes I have the gstreamer0.8-mad package. I can however rip mp3s if I don't write preset=1002" but the bitrate is way too high

---

### Post by Nis on 2005-04-07
[QUOTE=jasplund]I get "Sound Juicer could not extract this CD
Reason: Could not create Gstreamer encoder ((null))" When I put preset=1002 at the end of the line. Yes I have the gstreamer0.8-mad package. I can however rip mp3s if I don't write preset=1002" but the bitrate is way too high[/QUOTE]
 This is what I have in my profile:
```

 audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001

```

---

### Post by jasplund on 2005-04-07
preset=1001 makes no difference

I can rip as long as it says audio/x-raw-int,rate=44100,channels=2 ! lame name=enc 
but not if it says audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001

or 1002 or whatever

---

### Post by Patrick on 2005-04-07
[QUOTE=jasplund]preset=1001 makes no difference

I can rip as long as it says audio/x-raw-int,rate=44100,channels=2 ! lame name=enc 
but not if it says audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001

or 1002 or whatever[/QUOTE]

Anybody has a link to the lame file?

---

### Post by jasplund on 2005-04-07
what lame-file?

I installed the goobox mp3 ripper. It's like sound juicer but you get to choose the bitrate. The problem is that it doesn't matter which bitrate I choose. It still encodes at 256

---

### Post by Patrick on 2005-04-07
[QUOTE=jasplund]what lame-file?

I installed the goobox mp3 ripper. It's like sound juicer but you get to choose the bitrate. The problem is that it doesn't matter which bitrate I choose. It still encodes at 256[/QUOTE]

gstreamer8.0-lame

---

### Post by jasplund on 2005-04-07
[http://henrik.synth.no/deb/gstreamer0.8-lame_0.8.2-2_i386.deb](http://henrik.synth.no/deb/gstreamer0.8-lame_0.8.2-2_i386.deb)

that's the one that I use but maybe there's a newer one since I can't change the bitrate.

---

### Post by Nis on 2005-04-07
[QUOTE=jasplund][http://henrik.synth.no/deb/gstreamer0.8-lame_0.8.2-2_i386.deb](http://henrik.synth.no/deb/gstreamer0.8-lame_0.8.2-2_i386.deb)

that's the one that I use but maybe there's a newer one since I can't change the bitrate.[/QUOTE]
 Try the one for the marillat repository.  I was able to change the bitrate so maybe the deb you're using is not working correctly.  The only problem I noticed with it is some of my mp3s appear to be encoded at a very low bitrate (32) when in actuallity they sound fine and are the same size ratio as the ones reporting the correct ratio.

---

### Post by vaskark on 2005-04-07
Is preset 1001 = 192 Kbps? I just ripped an mp3 and in XMMS the bitrate indicator is fluctuating all over the place.

---

### Post by Nis on 2005-04-07
[QUOTE=vaskark]Is preset 1001 = 192 Kbps? I just ripped an mp3 and in XMMS the bitrate indicator is fluctuating all over the place.[/QUOTE]
 I'm not exactly sure what bitrate preset 1001 is (or any of the other presets for that matter), but it sounds like the mp3 was encoded at a variable bitrate.

---

### Post by vaskark on 2005-04-07
[QUOTE=Nis]I'm not exactly sure what bitrate preset 1001 is (or any of the other presets for that matter), but it sounds like the mp3 was encoded at a variable bitrate.[/QUOTE]
Ah. Does anyone know how to encode at a constant bitrate then?

---

### Post by alexp on 2005-04-10
vaskark,

 >  Ah. Does anyone know how to encode at a constant bitrate then?

you can examine the available configuration options for the gstreamer-lame encoder by running ```
gst-inspect-0.8
``` in a terminal.

So, if you want to set your profile to CBR encoding, using 192 kBit/s, you would add "vbr=false bitrate=192" to your encoding profile. The "quality" setting, however, does the same thing; the default value (5) corresponds to 160 kBit/s.

ruff, maybe you can add this to the first post, so that it can be found easily.

Regards,
Alexander

---

### Post by vaskark on 2005-04-10
[QUOTE=alexp]vaskark,

you can examine the available configuration options for the gstreamer-lame encoder by running ```
gst-inspect-0.8
``` in a terminal.

So, if you want to set your profile to CBR encoding, using 192 kBit/s, you would add "vbr=false bitrate=192" to your encoding profile. The "quality" setting, however, does the same thing; the default value (5) corresponds to 160 kBit/s.

ruff, maybe you can add this to the first post, so that it can be found easily.

Regards,
Alexander[/QUOTE]
Alexander,

Here is my current pipeline for encoding in MP3:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001

So are you saying that I replace "preset=1001" with "vbr=false bitrate=192" ? I tried that and received the same error.

---

### Post by alexp on 2005-04-11
vaskark,

according to the gstreamer developer documentation and various web sites, this is the way to configure gstreamer pipelines.

However, I posted yesterday without trying it out :-\". It seems that gstreamer and/or gnome-audio-profiles-properties (and God knows what else) frankly ignore those settings -- but I don't know why.

IMHO, the appropriate thing to do now is to [file a bug]("https://bugzilla.ubuntu.com/enter_bug.cgi?product=Ubuntu").

Regards,
Alexander

---

### Post by dabeej on 2005-04-11
Anyone have the default settings for the ogg one? I accidentally deleted mines.

---

### Post by titus1950 on 2005-04-11
Get  "Grip",and you can adjust everything including Rip Bitrate.
You need  "Lame"  and "Liblame" to encode to MP3 (Synaptic for them)

---

### Post by alexp on 2005-04-11
vaskark,

[QUOTE=vaskark]
Here is my current pipeline for encoding in MP3:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001

So are you saying that I replace "preset=1001" with "vbr=false bitrate=192" ? I tried that and received the same error.[/QUOTE]

I tried it out now. You can test the impact of the various settings by executing a gstreamer pipeline on your command prompt:
 ```
gst-launch-0.8 filesrc location=music.wav ! wavparse ! lame ! filesink location=music.mp3
```
This obviously assumes a "music.wav" input file in the current working directory. By adding options to the lame pipeline part, you can control the behaviour of the encoder, e.g. changing it to "lame vbr=0 bitrate=192" results in 192kBit/s CBR-encoded files. A short ```
gst-inspect-0.8 lame
``` will tell the tale about all available settings, along with nice descriptions of what they do -- for me, the default is CBR/128.

Note that this *ONLY* works with the .deb from [marillat]("ftp://ftp.nerim.net/debian-marillat/dists/unstable/main/binary-i386/gstreamer0.8-lame_0.8.8-0.1_i386.deb"); I tried with several other packages, and every single one wets its pants. Furthermore, after installing the package via dpkg, you have to run ```
sudo gst-register-0.8
``` once; else the encoder will **crash hard** and without hope for recovery.

After that, the code snippet from above will work. Please drop a short note when having it up and running.

Besides that, I found some [documentation]("http://www.ubuntulinux.org/wiki/RestrictedFormats#head-d6f3a3ededfdd1a9bdbdec06d029bd976622bd9b") in the Ubuntu Wiki which explains the whole process, too -- obviously, this was completely overlooked by everyone.

Regards,
Alexander

---

### Post by alexp on 2005-04-11
[QUOTE=titus1950]Get  "Grip",and you can adjust everything including Rip Bitrate.
You need  "Lame"  and "Liblame" to encode to MP3 (Synaptic for them)[/QUOTE]
 titus (and all others who seem to qualify as yet another apt-cache frontend),

<rant mode="on">
we *know* that there are several other gnome cd ripper tools, but obviously this thread is about sound-juicer and MP3 -- so please (with sugar on top) stop telling us about one or the other oh-so-wonderful program that does everything much better than sound-juicer.
</rant>

Regards,
Alexander

---

### Post by vaskark on 2005-04-11
Thanks, Alexander. I got it finally the way I want with this gstreamer pipeline for mp3:

 ```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192
```

Hats off to ya!

---

### Post by alexp on 2005-04-12
vaskark,

[QUOTE=vaskark]Thanks, Alexander. I got it finally the way I want with this gstreamer pipeline for mp3:

 ```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192
```

Hats off to ya![/QUOTE]

Glad to hear that, finally, it works. I'll PM ruff to edit his first message. If he doesn't reply, I'll have to open yet another "Sound Juicer with MP3 support" thread :roll:.

Regards,
Alexander

---

### Post by Raptor Ramjet on 2005-04-24
This all looks good but does anyone know where gstreamer8.0-lame can be found for 5.04 (Hoary ?) ? (i.e. which repository do I ned to add to synaptic ?)

Cheers.

---

### Post by cvmostert on 2005-09-06
HI all... i am also a newbie... and the thing that helped me with lame was to change the audio profile properties with the same user who uses sound ripper...

duh... 

but that was my problem

take care,
c

---

### Post by Mosey on 2005-11-14
I'm trying to be able to rip to mp3...so i'll resurect this thread.

When I attempt to run the extracter in soundjuicer with the new profile I recieve this error:

Sound Juicer could not extract this CD.
Reason: Could not create GStreamer encoders for CD Quality, Lossy mp3

So I looked back and found out that you need the gstreamer8.0-lame plugin/add on thing...

I apt-cache searched for it...but no...nothing. It's not there. I install gnome-media and all the gstreamer plugins...but one for lame is not listed.

WHERE IS IT?!?! WHY ME?

---

### Post by lessthanjake on 2005-12-04
This thread helped me ripping mp3's with Sound-Juicer, but do anyone know how to choose the text-encoding(UTF8/ISOxxxx) for the files created? I'm usually good at reading manuals, but I do not find any manual for this gstreamer pipelining, neither with "man" nor "google". So if anyone know where to find the manual it would be even better!!

---

### Post by MetalMusicAddict on 2006-05-25
Does anyone have a link to the arguments?

If someone can help me get this I would be thrilled. I might be able to get rid of WINE and Audiograbber.

In Audiograbber I rip @ these settings:
Stereo, High Quality and VBR quality level 3.

Does Sound Juicer add Id3 tags? Doesnt look to. :-k 

Does anyone use Grip?

---

### Post by dpm on 2006-06-10
[quote=MetalMusicAddict]Does anyone have a link to the arguments?

If someone can help me get this I would be thrilled. I might be able to get rid of WINE and Audiograbber.

In Audiograbber I rip @ these settings:
Stereo, High Quality and VBR quality level 3.

Does Sound Juicer add Id3 tags? Doesnt look to. :-k 

Does anyone use Grip?[/quote] 
I'm not sure whether this is what you are asking for, but here it goes:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=128 ! id3v2mux
``` 
I pasted this from: [https://wiki.ubuntu.com/CDRipping]("https://wiki.ubuntu.com/CDRipping"), which gives you detailed instructions on how to rip mp3 songs from soundjuicer. You'll have to install **gstreamer0.10-plugins-ugly-multiverse** as indicated.

It seems that Soundjuicer does not add id3 tags, but I'll look into it.

I've been using Grip, and although it works fine, I find it overly unintuitive and too much bloated with options. I don't find the soundjuicer interface especially groundbreaking, but at least it is simple and intuitive. The only advantage I find in Grip is that it generates the id3 tags.

Cheers.

---

### Post by MetalMusicAddict on 2006-06-10
Desp. I sat down a tackled Grip. See my sig for the HOWTO.

---

### Post by Fred Doolie on 2006-06-16
Jasplud said:
The problem is that it doesn't matter which bitrate I choose. It still encodes at 256

Then I said:
Forgive my stupidity but why would you want anything less than 256?  That's CD quality isn't it? Maybe it's just me but I want my MP3 files to be indistinguishable from the original CDs.

---

### Post by Fred Doolie on 2006-06-16
[QUOTE=ruff]Found this and thought it might be of use to some:

[http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)

It is a great little how-to on getting Sound Juicer 2.10.0 to rip mp3 - and it works  \\:D/ 

Cheers,

Ruff[/QUOTE]

Yes it does. Thanks.
Now, how to get it to rip to wma? The files are smaller and my player supports it.

---

### Post by abbot on 2006-06-17
[QUOTE=desp]
I've been using Grip, and although it works fine, I find it overly unintuitive and too much bloated with options. I don't find the soundjuicer interface especially groundbreaking, but at least it is simple and intuitive. The only advantage I find in Grip is that it generates the id3 tags.[/QUOTE]

Bloated with options? Unintuitive? Changing options by gstreamer pipeline entries is intuitive for you?  I only use Grip to rip music just because you can set every single thing to how you want it, instead of having to conform to how your ripping program wants to organize your music.  All you have to do is click check boxes and fill in some paths to where you want to files to go.  The most difficult part is the %n - %a - %t.mp3 type stuff for file name formatting, but that's explained very clearly in the programs help section.  It's better than having to choose from the 5 or 6 available settings in sound juicer, none of which I use.  Plus it doesn't write ID3's which is ridiculous.  I only wish Grip was incorporated into Rhythmbox instead of Sound Juicer.  I wish I could use it, but it just wants to choose too many of my options for me.

---

### Post by rossp on 2006-06-19
I'm a newbie, as you can see.   What I'm trying to do is create small low-quality mp3 files, so I can fit as many as possible on my (small, cheap) portable mp3 player.   My assumption was that I could do that by encoding at a low bitrate.      (When I record internet radio at 24 kb/sec, I get files that are about 1 MB per minute).  

So I'm trying to encode mp3 files using this gstreamer pipeline:

Code:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=24 ! id3v2mux

But this gives me an mp3 file of about 10MB per minute of music, which is the same as I get when I use bitrate=128.

So what am I doing wrong?   Any suggestions would be gratefully received...

Thanks
Ross
:confused:

---

### Post by rossp on 2006-06-22
I fixed it!   I found that for some reason I had gstreamer-0.8 as well as gstreamer-0.10 installed.   I used synaptic to remove gstreamer-0.8.   Unfortunately that also got rid of gstreamer-0.8-lame.   I found gstreamer-0.10-lame in gstreamer-plugins-ugly-multiverse, installed it, and everything started working.

I do prefer Sound Juicer to grip (sorry!)


Ross.

---

### Post by sandpaperback on 2006-06-25
When I tried the above pipelines, Sound Juicer was just ripping things to WAV and using mp3 as the extension.  Not very useful.  So here's what I ended up with to do VBR files that average 192kpbs:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=4 vbr-mean-bitrate=192 preset=1001 ! id3v2mux

However, I've again run into the problem that ripping to VBR on linux (I think I was using PCLOS before) creates incorrect play times.  I just ripped a 4 minute song, and Nautilus and amaroK are both telling me it's 30 minutes long.  Is there a fix to this?

**Edit:**
I guess the incorrect track length must be a problem with the Gstreamer Lame.  Using lame in Grip produces accurate times.

---

### Post by Ndlovu on 2006-06-26
> [http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html](http://www.emcken.dk/weblog/archives/99-MP3-encoding-with-Sound-Juicer.html)

I got a 504 Gateway Timeout when I tried the above link. If anyone else has the same problem, I found similar information here:
[http://jimmac.musichall.cz/weblog.php/2006/Feb/24]("http://jimmac.musichall.cz/weblog.php/2006/Feb/24")

There should be enough information there for you to figure things out.

---

### Post by maubp on 2006-06-27
[QUOTE=desp]I'm not sure whether this is what you are asking for, but here it goes:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=128 ! id3v2mux
``` 
I pasted this from: [https://wiki.ubuntu.com/CDRipping]("https://wiki.ubuntu.com/CDRipping"), which gives you detailed instructions on how to rip mp3 songs from soundjuicer. You'll have to install **gstreamer0.10-plugins-ugly-multiverse** as indicated.

It seems that Soundjuicer does not add id3 tags, but I'll look into it.[/QUOTE]

I think it DOES make the tags, but [tags written are ID3 version 2.4.0 tags](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-id3v2mux.html), which some players can't read :(

---

### Post by dpm on 2006-06-28
[quote=maubp]I think it DOES make the tags, but [tags written are ID3 version 2.4.0 tags]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-id3v2mux.html"), which some players can't read :([/quote]

You are completely right. I noticed this a couple of days ago after someone pointed this out in another thread.

After that, I decided to write a mini guide on the current ID3 tag situation in Ubuntu. It's here:

[http://www.ubuntuforums.org/showpost.php?p=1184248&postcount=16](http://www.ubuntuforums.org/showpost.php?p=1184248&postcount=16)

I hope it's useful.

Cheers.

---

### Post by Alienhunter2010 on 2006-07-10
I'm experience a strange problem with Sound Juicer on Ubuntu Dapper for PPC.

I Intall all additional software i need to rip on mp3 format: lame, gstreamer0.8-lame.

I set up the profile as described, I've reloaded Sound Juicer choosing the right profile and rip a track but I found a file, with mp3 extension that is truely a wav file!

Anybody could help me about this?

Tnx to all, Alex.

---

### Post by Alienhunter2010 on 2006-07-10
I found the solution myself. Dapper's version of Sound Juicer uses gstreamer0.10 instead of gstreamer0.8.

BTW 0.10 packages's structure is really different from 0.8 one. So you need to install following packages:

[LIST]
[*]gstreamer0.10-plugins-ugly (to play)
[*]gstreamer0.10-plugins-ugly-multiverse (to encode with LAME)
[/LIST]

With them your Sound Juicer turn back to work fine! \\:D/

Bye, Alex.

---

### Post by ronoc on 2006-07-20
Hi guys anyone ...
I have major problems trying to encode mp3. Gstreamer0.10 are installed with dependancies (as long as apt-get did its job correctly). With sound juicer I have made all the changes necessary to encode the mp3. Everything looks fine but when I attempt to extract I get a "File not found " error.
With GooBox I again can see all the mp3 options and everything seems fine until I actually extract I get this :
[B]
[FONT="Courier New"](goobox:6084): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(goobox:6084): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed[/FONT][/B]

Anybody have any idea what is going on ?

Cheers,
Conor

---

### Post by jamaas on 2006-07-21
Thanks Ross, that got mine sorted as well after many attempts!

Jim
> **rossp said:**
> I fixed it!   I found that for some reason I had gstreamer-0.8 as well as gstreamer-0.10 installed.   I used synaptic to remove gstreamer-0.8.   Unfortunately that also got rid of gstreamer-0.8-lame.   I found gstreamer-0.10-lame in gstreamer-plugins-ugly-multiverse, installed it, and everything started working.

I do prefer Sound Juicer to grip (sorry!)


Ross.

---

### Post by rasfahan on 2006-08-05
For those of you who have problems with wrong track lengths using VBR encoding, the following line works for me:

[PHP]audio/x-raw-int,rate=44100,channels=2 ! lame name=enc, preset=1001, xingheader ! id3v2mux[/PHP]

Notice the use of the xingheader option. The help on the lame gstreamer plugin mentions it's broken and that xingmux should be used instead, but quite contrary it seems that xingmux does not result in a correct XING-header.
I had no success to combine the id3mux plugin with anything that writes a xing header - it segfaults.

---

### Post by JackandJohn on 2006-08-09
The way I combatted this whole thing was to rip a cd with a gstreamer pipeline of:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=2 vbr=4
``` (I have to have separate stereo, which mode=2 does)

THEN, the magic: Scanned the mp3s with Musicbrainz Picard; this reads the audio files, then tags them properly based on the musicbrainz.org database (it sounds geeky and annoying, but it's *very* easy once Picard is installed ( [http://musicbrainz.org/doc/PicardLinuxInstall](http://musicbrainz.org/doc/PicardLinuxInstall) )


[SIZE="3"][B]Basically (once it's set up):

Pop cd in > rip > process mp3s > Play through mp3 player[/B][/SIZE]


Hope this helps.


p.s. Quick encoding tip; to find your options for the gstreamer pipeline, run ```
gst-inspect-0.10 lame
``` in a terminal (some options may not work, or I'm not sure how to use them)

---

### Post by browneyedgirl65 on 2006-09-17
> **ronoc said:**
> Hi guys anyone ...
I have major problems trying to encode mp3. Gstreamer0.10 are installed with dependancies (as long as apt-get did its job correctly). With sound juicer I have made all the changes necessary to encode the mp3. Everything looks fine but when I attempt to extract I get a "File not found " error.
With GooBox I again can see all the mp3 options and everything seems fine until I actually extract I get this :
[B]
[FONT="Courier New"](goobox:6084): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(goobox:6084): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed[/FONT][/B]

Anybody have any idea what is going on ?

Cheers,
Conor

bumping this... i've got the same problem, file not found

trying to rip mp3 for the new ipod #-o

---

### Post by browneyedgirl65 on 2006-09-18
OK, solved the no file issue (misspelled "channels"...sigh)

Now, I've successfully ripped MP3 files from audio cd's using Sound Juicer.  But..but...but...No tagging info!  Not even as basic as artist/album!  I got this just fine when using SJ to rip FLAC files.  Is there some other setting I need, here??  ](*,) 

Help!

Thx,
BEG

---

### Post by henderb on 2006-09-18
add: 
```
 ! id3mux
```
to the end

---

### Post by student3191 on 2006-11-19
Hey Guys, check out this link : [http://www.pizon.org/adding-mp3-support-to-gnome.html]("http://www.pizon.org/adding-mp3-support-to-gnome.html")

In your mp3 sound profile a command like this: 

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 bitrate=160

would set the bit rate to 160kbps

And for VBR encoding:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6

Hope this helps

---

### Post by PhoenixAndy on 2006-11-28
> **henderb said:**
> add: 
```
 ! id3mux
```
to the end

That doesn't give tags that EasyTAG or tagtool can read.

It identifies the tag as existing, but reads every field as blank.

Amarok, on the other hand, reads the tag just fine.

---

### Post by ElroyJetson on 2007-01-13
I am having problems encoding MP3 format. ](*,) 

I have tried the above encoding suggestions, but my mp3 files are "silent" when I play them. (No sound except a short music blip after about 30 seconds.) I successfully encode and play as ogg, so it seems the hardware and sound systems are working properly.

Does anyone have a suggestion? Could Lame having a hard time with the input, and is there anything I need to check? 

Thanks! ;)

---

### Post by te5torx on 2007-01-25
Hmmm.  I've done all these things.  I have gstreamer0.8-lame.  I've set up gnome-audio-profiles-properties as:

--------------------------
CD Quality, Lossy

mp3 audio

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc
 
mp3
-------------------------

When I try to use this setting in sound-juicer, it does not complain and creates a file that is not an MP3 and is big enough to be a WAV file.

---

### Post by te5torx on 2007-01-25
Doh!

Figured it out.

I needed gstreamer0.10-plugins-ugly-multiverse!

---

### Post by Shadoglare on 2007-03-12
> **te5torx said:**
> Doh!

Figured it out.

I needed gstreamer0.10-plugins-ugly-multiverse!

Yup, that fixed it for me too!

---

### Post by TimJBart on 2007-04-23
> **te5torx said:**
> Doh!

Figured it out.

I needed gstreamer0.10-plugins-ugly-multiverse!


and me!  I'd enabled practically everything but that!  Thanks!

---

### Post by iamah on 2007-09-13
I'm switching to Grip, altough is more complicated there's a thread here explaing it... I counldn't  select the MP3 profile in Juicer... tried many things but the profile doesn't list there...

---

### Post by axel112 on 2007-12-15
> **alexp said:**
> vaskark,

 

you can examine the available configuration options for the gstreamer-lame encoder by running ```
gst-inspect-0.8
``` in a terminal.

So, if you want to set your profile to CBR encoding, using 192 kBit/s, you would add "vbr=false bitrate=192" to your encoding profile. The "quality" setting, however, does the same thing; the default value (5) corresponds to 160 kBit/s.

ruff, maybe you can add this to the first post, so that it can be found easily.

Regards,
Alexander

Thank you! I have been googling and googling.

---

### Post by spesheled1 on 2008-01-05
Thanks for the info on configuring Sound Juicer for mp3, it was just what I needed.

---

