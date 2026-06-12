---
title: "Play IMG-files with mplayer"
date: 2005-11-24
forum: Outdated Tutorials &amp; Tips
---

### Post by monotux on 2005-11-24
This isn't very hard once one has it figured out, but they way there might be a bit tricky... :)

Since I haven't any DVD-burner nor any DVD-player (for my TV), I'm have to watch my movies on my computer, and getting it working in Linux hasn't been very easy, in my experience, but nothing is impossible. :)

Before I continue - if you've had problems playing *real* dvds with mplayer, you can use this method as well.

If your DVD is either a .img or .iso, you don't have to convert it to anything, you can simply mount it, but othervise:
[LIST]
[*]For bin/cue, you need **bchunk** (I believe it's in universe)
[*]For nrg, you need **nrg2iso**, also in universe
[/LIST]

Using these tools isn't difficult, but as long as you end up with a iso you'll be fine :P

Mounting a iso in Linux is quite simple:
```
mount -t iso9660 -o loop /path/to/file.iso /mnt
```

But if you run some custom kernel without support for loopback, this wont work :)

A quick'n'dirty way to test this, without subtitles nor menus, follows:
```
mplayer -dvd-device /mnt dvd://
```
In theory, you can choose what subtitle you want in the film with "-slang", but I couldn't make it work with the DVD I tested it on :(

Now - I like GUIs for everything, and making this work with gmplayer isn't very hard either - 
[LIST=1]
[*]Start mplayer
[*]Open the preferences
[*]Go to the Misc-tab
[*]Change the DVD device to /mnt
[/LIST]
Now, right click in the player window, and DVD -> Open Disc.
This is also where you easily can choose what subtitle you want.

Have fun - and remember, the manpage contains enough candy for all of you! :)

---

### Post by trash on 2006-01-09
converting the nrg with nrg2iso worked great but the 'mount -t iso9660 -o loop /path/to/file.iso /mnt' gave me something about the iso not being in a known format but right clicking on the iso and playing with VLC(in my case) worked like a charm.

thanks:)

---

### Post by josethemute on 2007-08-16
> **trash said:**
> converting the nrg with nrg2iso worked great but the 'mount -t iso9660 -o loop /path/to/file.iso /mnt' gave me something about the iso not being in a known format but right clicking on the iso and playing with VLC(in my case) worked like a charm.

thanks:)

I am having the same problem.  I have converted various .nrg files to .iso using nrg2iso, and I use the following commands to mount the created .iso files.

```

sudo modprobe loop
sudo mount -t iso9660 -o loop /directory/of/iso/isofile.iso /mount/folder/of/isofile

```

The mount command returns the following error when I try to do this:  
> 
mount: wrong fs type, bad option, bad superblock on /dev/loop0, missing codepage or other error
In some cases useful info is found in syslog- try dmesg | tail or so


I can post the output of  dmesg | tail if it would help, but I have no idea what dmesg does or whether the information in the output is better kept personal.  

I don't have the luxury of opening my converted iso's in VLC.  They are largely installation disks or backups of my PlayStation games.  I have tried opening them with gisomount, burning them with cdrecord, and opening them on Windows; nothing recognizes them as .iso files.  Has anyone else ran into this problem or can offer some advice on getting around this (I stupidly deleted all of my .nrg files after conversion)?

---

### Post by KryoFrk on 2008-04-03
got:

[HTML]Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...

FATAL: Could not initialize video filters (-vf) or video output (-vo).


Exiting... (End of file)[/HTML]

I've been trying to find an easy way to do this for some time now, I have close to 100 dvd's, and would love to just have them on my computer. 

VLC sorta works, the image is filled with square noise, mostly green.

Am I missing something simple?

---

### Post by KryoFrk on 2008-04-03
got VLC to read ISO.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

there are some horizontal lines though.

Mplayer works as well, and it comes in nice and clear.

---

### Post by mothis on 2009-07-23
Gmount-iso is a simple GUI tool to automatically mount ISO/IMG files. To install it go to Applications ->Add/Remove. Make sure "show" is set to "All open source applications". Search for gmount-iso, click the check box next to it, then click apply changes.

---

