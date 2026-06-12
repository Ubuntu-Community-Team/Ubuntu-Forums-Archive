---
title: "Thumbnail music using embedded cover art metadata"
date: 2008-01-01
forum: Outdated Tutorials &amp; Tips
---

### Post by jmillikin on 2008-01-01
The below instructions are for pre-Intrepid versions of Ubuntu. Beginning in Intrepid, thumbnails of audio files are supported by Totem. They may be optionally enabled by opening gconf-editor and setting the following keys to "true":

/desktop/gnome/thumbnailers/audio@mpeg/enabled
/desktop/gnome/thumbnailers/audio@ogg/enabled
/desktop/gnome/thumbnailers/audio@x-flac/enabled
/desktop/gnome/thumbnailers/audio@x-m4a/enabled
/desktop/gnome/thumbnailers/audio@x-mp3/enabled
/desktop/gnome/thumbnailers/audio@x-mpeg/enabled
/desktop/gnome/thumbnailers/audio@x-vorbis/enabled
/desktop/gnome/thumbnailers/audio@x-vorbis@ogg/enabled


I repeat: if you are using Intrepid (8.10) or later, there is no need to follow the rest of this post.

========================================================

Note: this is different from [Howto: Music album covers in Thunar Nautilus and everywhere!](http://ubuntuforums.org/showthread.php?t=486359). This is for thumbnails of individual audio files, rather than entire directories.

[[img]http://img136.imageshack.us/img136/8908/thumbnailsvn9.th.png[/img]](http://img136.imageshack.us/img136/8908/thumbnailsvn9.png)

[SIZE="5"]What is it?[/SIZE]
I got tired of the default audio file icon in Nautilus appearing for all my music, so I wrote a GNOME thumbnailer to liven things up. If an audio file contains metadata describing cover art, that art will now be displayed as a thumbnail for that picture.

[SIZE="5"]Capabilities[/SIZE]
Can handle FLAC, Ogg/Vorbis, and MP3 files currently.

[SIZE="5"]Installation[/SIZE]
Add the following source lines in Synaptic to use my PPA for these:
```
deb http://ppa.launchpad.net/jmillikin/ubuntu gutsy main
deb-src http://ppa.launchpad.net/jmillikin/ubuntu gutsy main
```

You'll want to install/upgrade the following packages:
[list]
[*]**audio-thumbnailers** - The thumbnail programs themselves.
[*]**libgnomeui** (and etc) - Allow multiple thumbnailers to be registered for each MIME-type. See [GNOME bug #497264](http://bugzilla.gnome.org/show_bug.cgi?id=497264)
[*]**vorbis-tools** - If you want to use my script for adding art to Ogg/Vorbis files. The vorbis-tools in Ubuntu's repository has a [bug with long comments](https://trac.xiph.org/ticket/1259).
[/list]

Restart nautilus at a terminal with **nautilus -q && nautilus &**, or just log out and back in.

[SIZE="5"]Tagging your music[/SIZE]
[LIST]
[*]**FLAC**: Use **metaflac** --import-picture-from=cover.jpg file1.flac file2.flac ...
[*]**Ogg/Vorbis**: I couldn't find any taggers that support Ogg/Vorbis, so I made a simple command-line one. You'll need the patched vorbis-tools in my PPA. My script can be found in [http://pastebin.com/f7835ed27](http://pastebin.com/f7835ed27).
[*]**Ogg/FLAC**: Not supported, since libFLAC's metadata reading seems to choke. Advise and patches eagerly accepted.
[*]**MP3**: I've had the best luck using iTunes. Easytag seems to generate invalid metadata. [EyeD3 has been reported to work.](http://bugzilla.gnome.org/show_bug.cgi?id=345975#c25)
[*]**Other**: If you have another format you'd like to see supported, upload a test file and post the link. Best luck will be for formats with C-accessible open-source parsing libraries.
[/LIST]

[SIZE="5"]How broken is it?[/SIZE]

Maybe broken, this is the first time anybody other than me has used this. If you have any problems (Nautilus hanging, incorrect thumbnails, etc) please post.

If you find that thumbnailing .ogg files is intolerably slow, try renaming them to **.oga**. If files are named .ogg, Nautilus will run Totem's video thumbnailer on them before mine.

---

### Post by toppavak on 2008-01-03
Hey, pretty good work on this- tried it today with mixed results. Some files display album art perfectly, but it seems most just render the top tenth of the image and then it goes to crap, just shows random colors and blocky noise. Not sure what else to give you to help diagnose the problem. Good luck!

---

### Post by jmillikin on 2008-01-04
> **toppavak said:**
> Hey, pretty good work on this- tried it today with mixed results. Some files display album art perfectly, but it seems most just render the top tenth of the image and then it goes to crap, just shows random colors and blocky noise. Not sure what else to give you to help diagnose the problem. Good luck!

Were the files MP3 files, with art added using EasyTag?

> **jmillikin said:**
> **MP3**: I've had the best luck using iTunes. Easytag seems to generate invalid metadata if you use it to store JPEG covers, but perhaps it works with PNG?

EDIT: A user on the GNOME bugzilla mentioned that [EyeD3 generates correct tags](http://bugzilla.gnome.org/show_bug.cgi?id=345975#c25).

---

### Post by Aetherius on 2008-01-09
Anyone wishing to get album art easily quickly and (relatively) accurately embedded into the id3 tags should look no further than [Album Cover Art Downloader]("http://www.unrealvoodoo.org/hiteck/projects/albumart/") ([http://www.unrealvoodoo.org/hiteck/projects/albumart/](http://www.unrealvoodoo.org/hiteck/projects/albumart/)) .

The .deb works brilliantly on gusty and fesity but.....one small problem ails this app in ubuntu (its to do with incorrect text encoding) easily fixed with the tip in[ this post]("http://ubuntuforums.org/showpost.php?p=2335946&postcount=10").

Aeth

EDIT: Ahh, this will also tag Ogg, even tho the ogg album art tagging isn't really any kind of standard

EDIT 2: THANKS ! this a great little addition to nautilus :)

---

### Post by kebajonathan on 2008-03-26
Hi jmillikin,

I'm just trying to tag an ogg vorbis file with a jpeg I have extracted from the MP3 I have converted it from. Your script doesn't work for me, even though I have the last version of oggenc (where your bugfix was included). Can you please help me? How does it work? Thank you

Keba

---

### Post by grana on 2008-05-11
Hi, I really like the functionality of your thumbnailer but... I couldn't get it to work! I have Hardy Heron, and the thumbnails are simply not generated. I checked more and more and, the mp3 have embedded image, and I tried both on a mounted NTFS device or ext3 (does it make any change?).

Please, can you help me?

thanks!!
grana

---

### Post by jmillikin on 2008-05-17
> **kebajonathan said:**
> Hi jmillikin,

I'm just trying to tag an ogg vorbis file with a jpeg I have extracted from the MP3 I have converted it from. Your script doesn't work for me, even though I have the last version of oggenc (where your bugfix was included). Can you please help me? How does it work? Thank you

Keba

Does the script give an error? If you open the file with a tagger like Ex Falso ([FONT="Courier New"]exfalso[/FONT]), are the "coverart" and "coverartmime" tags there?

It works by reading in the image with PIL ([FONT="Courier New"]python-imaging[/FONT]), base64-encoding it, then writing it to the file with vorbiscomment ([FONT="Courier New"]vorbis-tools[/FONT]).

> **grana said:**
> Hi, I really like the functionality of your thumbnailer but... I couldn't get it to work! I have Hardy Heron, and the thumbnails are simply not generated. I checked more and more and, the mp3 have embedded image, and I tried both on a mounted NTFS device or ext3 (does it make any change?).

Please, can you help me?

thanks!!
grana

Have you installed the patched [FONT="Courier New"]libgnomeui-0[/FONT]? Without it, Nautilus will not detect the additional thumbnailers.

Try running "[FONT="Courier New"]audio-thumbnailer-gst -i <path to mp3> -o ~/Desktop/temp.png[/FONT]",  and see if the image is created. If not, could you upload a sample mp3 somewhere for me to examine? If the image was created, you probably need to apply the libgnomeui patch.

---

### Post by grana on 2008-05-17
> Have you installed the patched [FONT="Courier New"]libgnomeui-0[/FONT]? Without it, Nautilus will not detect the additional thumbnailers.

Try running "[FONT="Courier New"]audio-thumbnailer-gst -i <path to mp3> -o ~/Desktop/temp.png[/FONT]",  and see if the image is created. If not, could you upload a sample mp3 somewhere for me to examine? If the image was created, you probably need to apply the libgnomeui patch.
My noob-ish error: I used gutsy apt sources instead of the hardy ones: go on with the great job!! =D> =D> =D>

---

### Post by tretle on 2008-09-12
Any chance you could upload packages for intrepid please?

---

### Post by jmillikin on 2008-09-12
> **tretle said:**
> Any chance you could upload packages for intrepid please?

I don't have any systems running Intrepid yet, so no. However, I believe that in Intrepid Totem's thumbnailer is now able to thumbnail audio files. You may need to dig into the GConf thumbnailer keys at /desktop/gnome/thumbnailers/<mimetype> and enable them.

---

### Post by tretle on 2008-09-12
Hmmmm.... I enabled the video thumbnail support for mp3s and ogg audio files but that didnt seem to do the trick either.. Here is what I get when I try and manually grab the album art from the file :

tretle@tretle-desktop:~$ audio-thumbnailer-gst -i /home/tretle/Music/metallica - death magnetic/Cyanide.mp3 -o ~/Desktop/temp.png
Error thumbnailing "/home/tretle/Music/metallica": Failed to enter GST_STATE_PAUSED
tretle@tretle-desktop:~$ 


Also, have you discussed this thumbnailer with the nautilus guys, it should clearly be included with nautilus as default.

---

### Post by tretle on 2008-09-12
Well.... I enabled every audiofile not just the .mp3 and ogg and that seemed to do the trick... even though it was an .mp3 :D

---

### Post by jmillikin on 2008-09-12
> **tretle said:**
> Hmmmm.... I enabled the video thumbnail support for mp3s and ogg audio files but that didnt seem to do the trick either.. Here is what I get when I try and manually grab the album art from the file :

tretle@tretle-desktop:~$ audio-thumbnailer-gst -i /home/tretle/Music/metallica - death magnetic/Cyanide.mp3 -o ~/Desktop/temp.png
Error thumbnailing "/home/tretle/Music/metallica": Failed to enter GST_STATE_PAUSED
tretle@tretle-desktop:~$ 


You need to use quotes around the filename:

```
audio-thumbnailer-gst -i "/home/tretle/Music/metallica - death magnetic/Cyanide.mp3"
```

> Also, have you discussed this thumbnailer with the nautilus guys, it should clearly be included with nautilus as default.

The thumbnailer requires a patch to libgnomeui to work properly, and there's been zero interest in the GNOME camp in getting that patch in. As mentioned, Totem's thumbnailer will be getting support for this in the next version of GNOME, but even then it's not enabled by default. I've tried to get this accepted into Ubuntu's patchset for Hardy and Intrepid, but there wasn't much interest there either. I guess most devs just don't care about album art.

---

### Post by tretle on 2008-09-12
Well I used your hardy repo to install the thumbnailer, I used the stock libgnomeui that came with intrepid and it works now... Seems the only think I needed to do was enable the video thumbnails for audio files... Its a pity that no-one has shown interest in including it yet.. I will be sure to spread the word about this nautilus goodness and hopefully people will wake up to how great this is.
One thing that I could see as something that would go against the script is the fact that the two most commonly used audio players in gnome based distro's banshee, and rhythmbox do not support writing album art to the metadtata but I will spread the word about this script on #rhythmbox and #banshee to show them that including album art metadata support is clearly beneficial.. Well in terms of ease of use if this script is included in distros like suse and ubuntu in the future. 
Thanks for the great work.

---

### Post by jmillikin on 2008-09-12
> **tretle said:**
> Well I used your hardy repo to install the thumbnailer, I used the stock libgnomeui that came with intrepid and it works now... Seems the only think I needed to do was enable the video thumbnails for audio files... Its a pity that no-one has shown interest in including it yet.. I will be sure to spread the word about this nautilus goodness and hopefully people will wake up to how great this is.

I think there is a misunderstanding, here. Intrepid comes with audio thumbnailers that are disabled by default. My package is for pre-Intrepid systems (which do not have built-in thumbnailers).

There is no way for my package to function on a stock libgnomeui. If you are using a stock libgnomeui and your thumbnails are working, you are using the built-in thumbnailers. Go ahead and uninstall my package, because it serves no purpose in Intrpid -- it just wastes disk space.

> **tretle said:**
> One thing that I could see as something that would go against the script is the fact that the two most commonly used audio players in gnome based distro's banshee, and rhythmbox do not support writing album art to the metadtata but I will spread the word about this script on #rhythmbox and #banshee to show them that including album art metadata support is clearly beneficial.

I've already tried to get a patch for reading embedded album art into Rhythmbox, but with no luck. I believe there's also a patch floating around for writing album art to files somewhere on GNOME bugzilla, but again, no interest.

I would also like to see more interest in embedded album art from upstream. I think it adds style and polish to the desktop. But there's no way to *force* upstream to accept patches.

---

### Post by tretle on 2008-09-13
Hi, enjoying the new thumbnailer thus far but  thought of a nice feature for it. It currently uses the picture thumbnail_frame which is ok but when you have music and pictures in the same folders then it can get a bit confusing as to what files are music files and what aren't.
The thumbnail_frame is located here /usr/share/pixmaps/nautilus . It seems that you can assign different frames to different mimetypes. Like video, I'm not sure where that frame is located but it obviously uses a different frame to differentiate videos from pictures. 
Might be cool to have a specialized thumbnail_frame for music. It could be just like the current one except the left side has extra padding with "Music" written on it. The extra padding on the left would sort of make it look like a cd case too :D
If a thumbnail_frame like this was implemented then it would be easy to take a quick glance at a directory and see which files are music files and which files are images without having to hover over the files individually.

---

### Post by elektronaut on 2009-06-01
Just to clarify, as I didn't know myself what jmillikin meant: 

In the newer Ubuntu versions (Intrepid, Jaunty,...) you start
```
$ gconf-editor
```
and traverse the tree to the left to /desktop/gnome/thumbnailers. There you see a lot of 'audio@xyz' entries. I simply enabled all of them. Restart Nautilus and you will see the cover art.

---

