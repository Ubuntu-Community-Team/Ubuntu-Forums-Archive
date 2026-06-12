---
title: "Rip CD's in MP3 format @ 192 kbps CBR in Sound Juicer"
date: 2006-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by bsalt on 2006-06-04
To rip CD's in Sound Juicer in MP3 format in Sound Juicer, follow these steps below.

**This is only for Ubuntu Dapper Drake**

[COLOR="Red"]Make sure you have gstreamer0.10-ffmpeg installed:[/COLOR]

```
sudo apt-get update
sudo apt-get install gstreamer0.10-ffmpeg
```

1) Open up Sound Juicer and go to EDIT -> PREFERENCES -> Edit Profiles...

2) Click on New to create a new profile. Name it whatever you want (I chose "MP3")

3) Go ahead and select your new profile and click on "Edit"

4) Place anything you want in Profile Description

5) For Gstreamer pipeline, use this as a guideline:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=false bitrate=192 ! id3mux
```
Feel free to change 192 to a higher or lower bitrate if so desired. The tag id3mux makes it possible for a program like Rhythmbox to read the file's id3 tag.

6) Type mp3 in "File Extension" and click the "Active?" checkbox.

7) **Restart Sound Juicer**

8) Go to EDIT->Preferences and select your newly created profile on the list.


You are now ready to rip CD's at a higher-quality bitrate.

---

### Post by CronoDekar on 2006-06-05
Awesome, I was just looking for how to add mp3 support to Sound Juicer so I could compare ogg vs. mp3.  Thanks!

---

### Post by pekko on 2006-06-07
For best results regarding sound quality and compression ratio you shouldn't use CBR encoding at all but VBR (variable bitrate) instead. More info about recommended lame settings can be found here:

 [http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_Encoder_Settings](http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_Encoder_Settings)

I use and recommend following pipeline:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=4 vbr-quality=2 ! xingmux ! id3v2mux
```

This is equivalent for lame command line switch *-V 2 --vbr-new*. I have added xingmux to create xing header for vbr mp3 files. For example Ipods and xmms player use xing header to calculate vbr mp3 length, so mp3's created without xingmux won't behave as expected with those players. For some reason id3mux doesn't work with xingmux, so I use id3v2mux instead.

---

### Post by edopizza on 2006-06-08
I have a strange behaviour, the output files are about ten times bigger then normal mp3 file size and they doesn't playback. 
Could the problem come from the fact that I upgraded from a Breezy to Dapper without making a complete fresh installation?

---

### Post by OPaul on 2006-06-10
I'm having the same problem with the code **pekko** provided. Upgrading to Dapper shouldn't have any problem.

---

### Post by fast orange on 2006-06-13
same problem here too.  Any ideas?

---

### Post by Bomper on 2006-06-14
1.- System > Help > Ubuntu Book

   2.- Select Chapters > "Using Ubuntu on the Desktop"

   3.- Search:  "Ripping Songs as MP3s"

    4.- 
" You should first install the [COLOR="DarkOrange"]gstreamer-10-ugly-multiverse[/COLOR] package (from the Multiverse repository). Next, in Sound Juicer click Edit > Preferences and click the Edit Profiles button. In the dialog box that pops up, click New, call the profile MP3, and then select it from the list and click Edit.

Now fill in the settings with the following information:

     Profile Description: MP3 Encoder
     GStreamer Pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc
     File Extension: mp3

Check the Active box, and click OK. Now close the Profiles dialog box, and click Close to close the Preferences box. Restart Sound Juicer, and you can now select MP3 from the Format combo box in the Preferences box. "

---

### Post by OPaul on 2006-06-14
[QUOTE=Bomper]" You should first install the [COLOR="DarkOrange"]gstreamer-10-ugly-multiverse[/COLOR] package (from the Multiverse repository). [/QUOTE]
I don't have this package. Multiverse is enabled.

---

### Post by Bomper on 2006-06-14
Error in Ubuntu Book.

multiverse is enabled.

 sudo apt-get install [COLOR="Orange"]gstreamer0.10-plugins-ugly-multiverse
[/COLOR]

---

### Post by OPaul on 2006-06-14
[QUOTE=Bomper]Error in Ubuntu Book.

multiverse is enabled.

 sudo apt-get install [COLOR="Orange"]gstreamer0.10-plugins-ugly-multiverse
[/COLOR][/QUOTE]
Awesome that worked, thanks. Now is there anyway I can use VBR equivalent to Lames "-standard" switch?

---

### Post by chessforce on 2006-06-24
[QUOTE=OPaul]Awesome that worked, thanks. Now is there anyway I can use VBR equivalent to Lames "-standard" switch?[/QUOTE]
As indicated at [http://www.dho.ca/blog/404](http://www.dho.ca/blog/404) you could use:
```

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1001

```

---

### Post by yaztromo on 2006-06-24
[QUOTE=pekko]For best results regarding sound quality and compression ratio you shouldn't use CBR encoding at all but VBR (variable bitrate) instead. More info about recommended lame settings can be found here:

 [http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_Encoder_Settings](http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_Encoder_Settings)

I use and recommend following pipeline:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=4 vbr-quality=2 ! xingmux ! id3v2mux
```

This is equivalent for lame command line switch *-V 2 --vbr-new*. I have added xingmux to create xing header for vbr mp3 files. For example Ipods and xmms player use xing header to calculate vbr mp3 length, so mp3's created without xingmux won't behave as expected with those players. For some reason id3mux doesn't work with xingmux, so I use id3v2mux instead.[/QUOTE]

Seconding this. 192kbs CBR is inferior quality now and is only used by some die hard p2p ripping groups who are too arrogant to believe they are wrong.

For best results and lowest bitrate use the Hydrogenaudio recommended settings. Lame 3.97 -V 2 is all you need.

---

### Post by brian g on 2006-06-27
[QUOTE=pekko]For best results regarding sound quality and compression ratio you shouldn't use CBR encoding at all but VBR (variable bitrate) instead. More info about recommended lame settings can be found here:

 [http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_Encoder_Settings](http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_Encoder_Settings)

I use and recommend following pipeline:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=4 vbr-quality=2 ! xingmux ! id3v2mux
```

This is equivalent for lame command line switch *-V 2 --vbr-new*. I have added xingmux to create xing header for vbr mp3 files. For example Ipods and xmms player use xing header to calculate vbr mp3 length, so mp3's created without xingmux won't behave as expected with those players. For some reason id3mux doesn't work with xingmux, so I use id3v2mux instead.[/QUOTE]
the string in this post is wrong or something.
it leaves incorrect headers and mangled mp3s.
i just ripped a track that was a minute and a half and all player read it as being over 8 minutes long.

---

### Post by altima on 2009-03-19
hey guys, what will be the gstreamer command for an mp3 with 192 constant bit rate? there are some profiles for VBR in the rhythmbox, but I prefer CBR. thank you in advance!

---

