---
title: "Convert avi/mov/ogg/etc To DVD script"
date: 2006-12-17
forum: Outdated Tutorials &amp; Tips
---

### Post by netyire on 2006-12-17
**_[SIZE="3"]Convert Any Media Mencoder Supports To DVD[/SIZE]_**

[SIZE="2"]Thanks To The Ubuntu Forum People For All Their Help And The Gentoo Wiki For The Guide Website: **[http://gentoo-wiki.com/Index:HOWTO_Create_a_DVD](http://gentoo-wiki.com/Index:HOWTO_Create_a_DVD)**
Oh yeah, and the usual "USE THIS GUIDE AT YOUR OWN RISK" thing ;) .

_[SIZE="3"]Introduction: [/SIZE]_
18/12/2006: Added support for subtitles
26/12/2006: Made a nautilus script which (if you do not like using the command prompt) allows you make a DVD from any media file which Mencoder supports. Plus, it has new features which allows you to select more than one media file, and convert it to DVD. All without opening the terminal.

[SIZE="2"]I know that when I wanted to make a DVD from a file, I wanted it to be simple and hopefully as painless as possible. I tried devede, but possibly sometimes the audio and video were a tiny bit out of sync. ](*,)  (maybe it was my hearing?) So anyway, I wrote a small python program to convert a file which mencoder supports to a DVD. And later a nautilus script too. I hope it helps you![/SIZE]

[U]
[SIZE="3"]The Python Script Howto:[/SIZE][/U]

Tested On Ubuntu Edgy Eft 6.10 32 Bit
This script takes any media which mencoder supports on your system and turns it into a DVD, along the way, you can choose whether to use NTSC or PAL and change the aspect ratios. This script does not create menus for your DVD. If you have any ideas on how to make the script better or code to contribute to it, please post so that I can merge it in and make this script even better. It is written in python. Look at the source code for interesting stuff (if you already know what the code does then maybe not for you).

Before you begin, you need to have mencoder, ffmpeg, dvdauthor and mkisofs and python installed on your system. (Only five programs!) If you are not sure if you have these programs installed on your system, type this into the terminal:
 ```
**sudo apt-get install mencoder ffmpeg dvdauthor mkisofs**
```[/SIZE]

[SIZE="2"]Using this script is very simple, just download it to the same folder as your file is in and open a terminal. Then type:
**```
python program.py
```**

It will ask you for the name of the file you want to convert, just go ahead and type it in. After which you see lots of interesting stuff on the screen for a while. (Longer if you have a bigger file). Then it will report that the AVI was created and that it is going to convert it to a mpg. Answer the questions if you know or just press enter if you don't to use the defaults (which are not bad for the media I tested). After which you will have a DVD.iso file, just right click on it and select write to disc. Simple, your DVD!


_[SIZE="3"]The Nautilus Script[/SIZE]_
1. Download the Convert to DVD.tar.gz and unzip the file inside to /home/yourusername/.gnome2/nautilus-scripts/

2. Type "killall nautilus" in a terminal. (Thanks saxaphone_man :))

3. You can now select the media files you want, right-click and select scripts->convert to DVD

4. It will merge the files you selected into a new file (temp.avi), convert it to mpg (temp.mpg) and finally using dvdauthor and mkisofs, it will create a DVD.iso which you can right-click -> write to disc.

If you like it, please drop me an email at: [email]netyire@yahoo.com[/email] or post a comment :-D .

Oh, you are free to do anything with the script, build on it and distribute it... Just please put a credit in: original script by netyire (netyire@yahoo.com). Thanks![/SIZE]

---

### Post by saxaphone_man on 2006-12-27
You wouldn't have to restart x for the nautilus scripts to work... you'd just need to restart nautilus with `killall nautilus`. It'll restart by itself.

---

### Post by starscalling on 2007-01-02
@_@
interesting! thanx for this thingie :>
giving it a try now;.. i'll holler back later to report my xperience
till then tata~~

---

### Post by bionnaki on 2007-01-02
the python script did not work for me. the resulting .iso was 0 bytes in size.

the nautilus scripted seemed to work, but how do you stop it? how long would conversion take? one hour? nine hours?

---

### Post by netyire on 2007-01-03
Thanks StarsCalling, I hope it works for you! :D Anyway, if you got any problems, just post!

Hmm... Bionnaki, I think one difference between the python and nautilus scripts is that the python script converts the media file to a xvid video file while the nautilus script converts the media into a lavc file. Is there any possibility that your system does not have support for xvid? (This is just a guess, so don't stare at me ;) )

Anyway, as for how long it will take, I really can't say for sure. What the script does is that it converts the file to an avi, then to a mpg, then to the proper DVD structure and finally to a .iso file you can burn. I believe the encoding takes the most time, as for how long it takes I think that would depend on your system, what background tasks you are running, the nice value assigned to the process, and um... your media file. Anyway, if it is a long media file, then my guess would be:
Quite Long. (Maybe you want to leave it overnight if it is REALLY long).

Anyway, thanks for all the feedback, makes my day interesting!

Cheers :D .

---

### Post by bionnaki on 2007-01-03
yes, I have all codecs installed and the python script does not work for me. Running edgy with codecs installed via automatix2. Tovid, etc. all work fine.

the nautilus script seems to work great - good work. Is it possible to have some sort of minimal gui that shows an ETA and a Cancel button sort of like the audioconvert script? 

thanks

---

### Post by Bossieman on 2007-01-03
Tried it out and the result was a DVD.iso file that has size 0 bytes. I tried it out with a 2 meg sample file.
So how do I get it to work?

---

### Post by netyire on 2007-01-05
Glad the nautilus script works for you Bionnaki, though perhaps in the future it may be able to modify the python one to ensure it works. As for the ETA and cancel button, I'm open for ideas on how to implement this (though as for the exact code, well I'm not sure yet). Either way, if you absolutely must have it, I recommend that you try DeVeDe. Its a free program and I hope it will suit your needs.

Hmm... Bossieman, well could I know which options you choose when running the python script? Perhaps try again with the defaults? Either way, if that does not work try out the nautilus script.

Thanks for all the input! Makes the forum an interesting place.

---

### Post by Bossieman on 2007-01-11
> **netyire said:**
> 
Hmm... Bossieman, well could I know which options you choose when running the python script? Perhaps try again with the defaults? Either way, if that does not work try out the nautilus script.


Here is my output:

leif@Dimension-5000:~$ skapadvd
Filename:test.avi

=====================
Encoding To AVI...   
Current Pass 1/2     
=====================
MEncoder 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU:               Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x660800
AVI file format detected.
VIDEO:  [XVID]  576x304  12bpp  25.000 fps  755.4 kbps (92.2 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:576x304  fps:25.00  ftime:=0.0400
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 120.8 kbit/7.86% (ratio: 15099->192000)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================
xvid: using library version 1.1.0 (build xvid-1.1.0)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
MP3 audio selected.
VDec: vo config request - 576 x 304 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.89:1 - prescaling to correct movie aspect.
videocodec: XviD (576x304 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=576x304, sampled=576x304
xvid: 2Pass Rate Control -- 1st pass
Writing header...1f ( 0%)  0.00fps Trem:   3min   0mb  A-V:0.000 [0:0]
ODML: vprp aspect is 16384:8647.
Setting audio delay to 0.024s.
Writing header...
ODML: vprp aspect is 16384:8647.
Setting audio delay to 0.024s.
Pos:   1.0s     28f ( 1%) 20.54fps Trem:   1min   6mb  A-V:0.081 [0:126]
Skipping frame!
Pos:  59.8s   1500f (100%) 40.88fps Trem:   0min   8mb  A-V:0.049 [1106:125]
Flushing video frames
Writing index...
Writing header...
ODML: vprp aspect is 16384:8647.
Setting audio delay to 0.024s.

Video stream: 1105.865 kbit/s  (138233 B/s)  size: 8282926 bytes  59.920 secs  1500 frames

Audio stream:  125.182 kbit/s  (15647 B/s)  size: 938112 bytes  59.952 secs

=====================
Encoding To AVI...   
Current Pass 2/2     
Takes More Time Than 
Pass 1               
=====================
Do you want subtitles [Y/N] (Default: N):
MEncoder 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU:               Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x660800
AVI file format detected.
VIDEO:  [XVID]  576x304  12bpp  25.000 fps  755.4 kbps (92.2 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:576x304  fps:25.00  ftime:=0.0400
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 120.8 kbit/7.86% (ratio: 15099->192000)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================
xvid: using library version 1.1.0 (build xvid-1.1.0)
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
MP3 audio selected.
VDec: vo config request - 576 x 304 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.89:1 - prescaling to correct movie aspect.
videocodec: XviD (576x304 fourcc=44495658 [XVID])
xvid: par=0/0 (vga11), displayed=576x304, sampled=576x304
xvid: 2Pass Rate Control -- 2nd pass -- bitrate=1000kbit/s
Writing header...1f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
ODML: vprp aspect is 16384:8647.
Setting audio delay to 0.024s.
Writing header...
ODML: vprp aspect is 16384:8647.
Setting audio delay to 0.024s.
Pos:   1.0s     28f ( 1%)  0.00fps Trem:   0min   6mb  A-V:0.081 [0:126]
Skipping frame!
Pos:  59.8s   1500f (100%) 22.78fps Trem:   0min   7mb  A-V:0.049 [970:125]
Flushing video frames
Writing index...
Writing header...
ODML: vprp aspect is 16384:8647.
Setting audio delay to 0.024s.

Video stream:  969.989 kbit/s  (121248 B/s)  size: 7265220 bytes  59.920 secs  1500 frames

Audio stream:  125.182 kbit/s  (15647 B/s)  size: 938112 bytes  59.952 secs

===============================================================
Conversion To AVI Completed(Transcoding Step 1/2 Is A Success)
Please Answer The Following Questions Regarding Your Media
If You Do Not Know, Pressing Enter Uses The Defaults
================================================================
Do you want it PAL or NTSC [PAL/NTSC] (Default:NTSC):
Do you want to specify an aspect ratio [Y/N] (Default:N):
==================
Encoding To MPG...
Wait... :D        
==================
ffmpeg: error while loading shared libraries: libavformat.so.51: cannot open shared object file: No such file or directory
================================================
Conversion To MPG Complete (Transcoding Success)
================================================
Press Enter To Continue
DVDAuthor::dvdauthor, version 0.6.11.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing mpg.mpg...
ERR:  Error opening mpg.mpg: No such file or directory
DVDAuthor::dvdauthor, version 0.6.11.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: dvdauthor creating table of contents
ERR:  No .IFO files to process
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs 2.01.01a03-unofficial-iconv (i686-pc-linux-gnu)
Scanning DVD
Scanning DVD/VIDEO_TS
Scanning DVD/AUDIO_TS
mkisofs: No such file or directory. Faild to open DVD//VIDEO_TS/VIDEO_TS.IFO
mkisofs: Can't open VMG info for 'DVD/'.
mkisofs: Unable to parse DVD-Video structures.
mkisofs: Unable to make a DVD-Video image.

=========================================
All Operations Complete, DVD ISO Created!
Netyire 18/12/06                       
Feel Free To Distribute And Build Upon   
=========================================
Do You Want To Delete Temporary Files [Y/N] (Default:Y):
rm: kan inte ta bort "mpg.mpg": Filen eller katalogen finns inte
================================
If it worked for you, please drop
me an email at: [email]netyire@yahoo.com[/email]
Please :)                        
=================================
Right Click The ISO & Click Write To Disc :D
leif@Dimension-5000:~$ 




So there is a problem there, how can I fix it?

---

### Post by Bossieman on 2007-01-11
It works now!!

---

### Post by i3dmaster on 2007-01-13
First of all, thanks for the initial tools! Mod a little bit of the nautilus script and now it has a little pretty GUI and Cancel handling. Let's call it a Rev1.

---

### Post by netyire on 2007-01-20
WOW! Could you recommend any links to tutorials on this? Thanks for contributing, can't wait till I can improve the script.

---

### Post by kurlee daddee on 2007-01-25
> **Bossieman said:**
> Tried it out and the result was a DVD.iso file that has size 0 bytes. I tried it out with a 2 meg sample file.
So how do I get it to work?

I have only been using Ubuntu for a week now. I love it.

I get the same output as you. 0 bytes. 

Also when I run killall nautilus, I never get the option to select scripts. It isn't in the menu that comes up. So I have been trying to open the video file (I tried one .wmv file and one .avi file) with the Convert to DVD file. It makes a iso file, but it is only 0 bytes.

Can anyone help a newb? Please.

---

### Post by aeiah on 2007-01-29
the reason your script isnt showing up on your right-click menu may be because it isnt set to execute. open your script folder, right click your dvd script and go to properties>permissions and tick the execute box.

as for it spitting 0byte .iso files at you, well, its doing the same to me :p ill be sure to post back if i manage to fix it

---

### Post by aeiah on 2007-01-29
..

---

### Post by picklesmagee on 2008-01-06
.

---

