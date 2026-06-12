---
title: "Problem playing .mkv formats on Ubuntu 10.04.3"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by mschooler93 on 2011-09-16
I just installed Ubuntu 10.04.3 LTS yesterday, so I am exteremely new to Ubuntu. I installed it over my Windows XP. 
So, I am having troubles playing .mkv formats, it plays for a short time (1-5 min) then suddenly quits. It has no problem with .avi, or .mp3 so it is just this one format. I have tried the movie player that comes with Ubuntu, and VLC, and MPlayer, because I saw other threads with those working. I saw a couple of other thread about using a terminal, and I don't know how to do this. So, if anyone could help me fix this, if you could spell it out for me that would be great.

---

### Post by FormatSeize on 2011-09-16
Open an terminal and try the following:
```
sudo apt-get install ubuntu-restricted-extras
```
 
The files that you are trying to play require pieces of software that, while free, are illegal in some countries to be packaged with the OS.

---

### Post by mschooler93 on 2011-09-16
ubuntu-restricted-extras is already the latest version.

I guess I already installed that one.

---

### Post by ajgreeny on 2011-09-16
In a terminal try the command ```
mplayer <*filename*>.mkv
``` from the folder containing the movie file and note any error messages that appear, after the few minutes of playing properly, if that is when you see them.

---

### Post by mschooler93 on 2011-09-16
> **ajgreeny said:**
> In a terminal try the command ```
mplayer <*filename*>.mkv
``` from the folder containing the movie file and note any error messages that appear, after the few minutes of playing properly, if that is when you see them.

How do I say what folder it is in? The terminal just says it cannot find it.

---

### Post by doas777 on 2011-09-16
op:

here is my advice on Video:
1) install the mediubuntu repositories
2) install ubuntu-restricted-extras
3) install vlc
4) mplayer/smplayer or umplayer from PPAs (not the repos).
[https://help.ubuntu.com/community/SMPlayer](https://help.ubuntu.com/community/SMPlayer)

ok, in terms of players, Totem (the built in movie player) is the best integrated into the desktop so it is a good solid player for general use. 

SMPplayer/UMPlayer are good front--ends for mplayer. mplayer backend is teh best available, and will deal well (as well as possible) with dense or HD content.

VLC is your player of last resort. it plays almost anything, but plays almost nothing well. it will not help you with lag from HD processing.

vid card driver also has a big impact on performance. if you have an NVIDIA card, then look into VDPAU, to force high-res processing to take place on your GPU not your CPU.

---

### Post by ajgreeny on 2011-09-16
> **mschooler93 said:**
> How do I say what folder it is in? The terminal just says it cannot find it.
As an example, if the .mkv file is on your desktop use command ```
cd Desktop
``` and then ```
mplayer <*filename*>.mkv
``` The first command navigates to your Desktop folder (note upper case D, Linux is case sensitive) and then you can play the movie with the second command.

Alternatively you can use the pathway to the file in a single command ```
mplayer Desktop/<*filename*>.mkv
```

---

### Post by mschooler93 on 2011-09-16
OK, I did everything you said (I think)
I don't know whether or not the mediubuntu things are installed, but it was saying stuff on the terminal for awhile, so I think it is. I downloaded the SMplayer thing, it is a tar.gz, but I don't know how to install it. It is just a folder to extract, with a bunch of text files, and other stuff in it. Once again, I am a total beginner.

---

### Post by abnordude on 2011-09-16
> **mschooler93 said:**
> OK, I did everything you said (I think)
I don't know whether or not the mediubuntu things are installed, but it was saying stuff on the terminal for awhile, so I think it is. I downloaded the SMplayer thing, it is a tar.gz, but I don't know how to install it. It is just a folder to extract, with a bunch of text files, and other stuff in it. Once again, I am a total beginner.

Why dont u install it from the software centre and do like [ajgreeny]("http://ubuntuforums.org/member.php?u=27747") says.

Tis' more easier.

---

### Post by mschooler93 on 2011-09-16
OK, when i posted the last reply, I must not have been refreshed, because I didn't see yours, ajgreeny. I have to copy the files over to my computer from my external HD, so I will do that in a sec.

Okay, I opened it in Mplayer, after installing the SMplayer thing from the software center, and it works now. Haven't watched the whole thing, but it went for over 15 minutes, and no problems. There are no options, like file, edit, or skipping to a part of the movie, but I will figure that out on my own.
Thank you all so much! This Ubuntu forums are much faster to answer my questions than any windows forums I have ever been on, and you were much more helpful.

---

### Post by Lisiano on 2011-09-16
Tip. You can always drag-n-drop stuff on the terminal ```
mplayer Drag-N-Drop_Video.here
``` do put a space after mplayer before drag and dropping.
You can use the Software Center to install "almost everything", use Synaptic for "the near rest of everything" and googling for "the last part of the rest of everything".
Also MKV is just a container, it can contain any codec inside it, be it Xvid, DivX, H.264, etc. Although the usual combo is MKV+H.264.
Also what are you trying to play? For example most TV shows are in Xvid, Anime in H.264, Movies in both.
A example to see what codec is used using mplayer
```
lisiano@Lisiano-Ubuntu:~/Videos$ mplayer "Bath Rhymes.mp4"
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Bath Rhymes.mp4.
libavformat file format detected.
[lavf] stream 0: video (**h264**), -vid 0
[lavf] stream 1: audio (**aac**), -aid 0, -alang und
VIDEO:  [H264]  1920x1080  24bpp  23.976 fps  2006.3 kbps (244.9 kbyte/s)
Clip info:
 major_brand: isom
 minor_version: 512
 compatible_brands: isomiso2avc1mp41
 title: Bath Rhymes_edited
 encoder: Lavf52.78.3
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (**FFmpeg H.264**)
==========================================================================
==========================================================================
Opening audio decoder: [faad] **AAC (MPEG2/4 Advanced Audio Coding)**
AUDIO: 44100 Hz, 2 ch, s16le, 127.9 kbit/9.07% (ratio: 15992->176400)
Selected audio codec: [faad] afm: faad (FAAD **AAC (MPEG-2/MPEG-4 Audio)**)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vdpau] 1920x1080 => 1920x1080 Planar YV12 
A:   2.3 V:   2.3 A-V: -0.001 ct:  0.024   0/  0 59%  9%  0.9% 4 0 
Exiting... (Quit)
lisiano@Lisiano-Ubuntu:~/Videos$
``` Everything in bold is either a video or a audio codec. Or just open with the default video player (Totem) and under Properties (Click on Playlist then Properties) you can see the codec.
And I shall end with this. Try playing your video file in mplayer and post everything mplayer tells you (Left-click & Hold on the terminal to select then Right-click and press Copy or if you like Ctrl+C,V then use Ctrl+Shift+C,V)


EDIT: Great to hear that it's working. You can skip using arrows, close with Q, pause/unpause with space. Just press random buttons on the keyboard and you'll find more controls. Numbers also do stuff.

---

### Post by el_koraco on 2011-09-16
> **mschooler93 said:**
> OK, when i posted the last reply, I must not have been refreshed, because I didn't see yours, ajgreeny. I have to copy the files over to my computer from my external HD, so I will do that in a sec.

Okay, I opened it in Mplayer, after installing the SMplayer thing from the software center, and it works now. Haven't watched the whole thing, but it went for over 15 minutes, and no problems. There are no options, like file, edit, or skipping to a part of the movie, but I will figure that out on my own.
Thank you all so much! This Ubuntu forums are much faster to answer my questions than any windows forums I have ever been on, and you were much more helpful.

that's all done with keyboard shortcuts. Type "man mplayer" without the quotes in the terminal, and you'll get a detailed description (the man pages are there for every program).

---

