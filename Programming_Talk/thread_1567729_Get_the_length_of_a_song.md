---
title: "Get the length of a song?"
date: 2010-09-04
forum: Programming Talk
---

### Post by hakermania on 2010-09-04
Is there any way to do this with a programming language?
Can this be done in C++,unix scripting, perl or python somehow?
Thx for any help.

---

### Post by Bachstelze on 2010-09-04
The most straightforward way would be to use [font=monospace]ffmpeg -i foo.mp3[/font], and parse the output with some regexp magic.

---

### Post by lykeion on 2010-09-04
ffmpeg will work (although there's a lot of extra output that you'll have to regexp away)

you can also try ecasound:
```
sudo apt-get install ecasound
ecalength foo.mp3
```

ecasound also have C, Python, and Ruby bindings

---

### Post by StephenF on 2010-09-04
Mutagen in Python.

---

### Post by hakermania on 2010-09-04
ffmpeg has a lot of output :P
ecasound is very big (3MB)
Mutagen is only 85K but how do I use it? Can you explain me a bit?

---

### Post by lykeion on 2010-09-04
> **hakermania said:**
> ecasound is very big (3MB)
Big for what? What do you intend to do?
For a personal bash script 3MB wouldn't matter.

> **hakermania said:**
> Mutagen is only 85K but how do I use it? Can you explain me a bit?
```
sudo apt-get install python-mutagen
python
>>> from mutagen.mp3 import MP3
>>> audio = MP3("/full/path/to/foo.mp3")
>>> print audio.info.length
```

---

### Post by StephenF on 2010-09-04
Well, the python method is only 85K if you overlook the overhead of loading the Python interpreter. Not an issue if you are writing your script in same.

For personal scripts ease of writing and reliability should be the only concern.

---

### Post by hakermania on 2010-09-04
It is a program, so i don't want large dependencies. Is python support pre-installed in ubuntu?

---

### Post by lykeion on 2010-09-04
Python is preinstalled in Ubuntu, but mutagen is not.
You do a check and prompt user to install it if not found.
Something like this (bear in mind that I'm a Java programmer, and just a n00b in Python):
[PHP]#!/usr/bin/env python
# _*_ coding: utf-8 _*_
import os, sys
try:
	from mutagen.mp3 import MP3
except ImportError, e:
	pass # module doesn't exist, deal with it.
	print "Please install python-mutagen package"
	sys.exit(1)

if len(sys.argv) > 1:
    inputfile = sys.argv[1]
else:
	print "Usage:"
	print "\tgetMp3dur.py <audiofile>"
	sys.exit(1)	

if os.path.exists(inputfile):
	mp3file = MP3(inputfile)
	print mp3file.info.length
else:
	print inputfile + " is not a valid file"[/PHP]

---

### Post by FakeOutdoorsman on 2010-09-04
An FFmpeg example:
```
$ ffmpeg -i '20 Honky Tonk Women.mp3' 2>&1 | awk '/Duration/{print $2}'
00:02:55.33,
```
The trailing comma might be annoying for you but I ran out of time and didn't get to experiment with it more.

---

### Post by SledgeHammer_999 on 2010-09-04
Since you're going to develop for ubuntu then I suggest using gstreamer. Use the "playbin2" element to automatically decode ANY file. Then do a [gst_element_query_duration()](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gstreamer/html/GstElement.html#gst-element-query-duration) on it and you'll have an answer. There are python bindings for it if your not comfortable with C or C++.

Upside: gstreamer is installed in every GNOME installation.
Downside: Most distros don't install by default the extra codecs for some formats. eg for mp3 decoding you need to install the gstreamer-plugins-ugly package.

---

### Post by Some Penguin on 2010-09-04
> **hakermania said:**
> ffmpeg has a lot of output :P
ecasound is very big (3MB)
Mutagen is only 85K but how do I use it? Can you explain me a bit?

*shrug*  You're a hacker, right?  Be curious and take a look.  For instance, it's a pretty safe bet that ffmpeg is not a statically linked binary which had everything written from scratch, because that'd be a mind-bogglingly pointless waste of time when there are many perfectly good formats and when it would make sense to have a pluggable architecture, at least at compilation time, so that one can support different formats pretty reasonably.

```

myuser@myhost /usr/lib $  ldd /usr/bin/ffmpeg
        linux-vdso.so.1 =>  (0x00007ffff5fff000)
        libavfilter.so.1 => /usr/lib/libavfilter.so.1 (0x00007f86ec504000)
        libpostproc.so.51 => /usr/lib/libpostproc.so.51 (0x00007f86ec2f7000)
        libavdevice.so.52 => /usr/lib/libavdevice.so.52 (0x00007f86ec0f1000)
        libavformat.so.52 => /usr/lib/libavformat.so.52 (0x00007f86ebe4e000)
        libavcodec.so.52 => /usr/lib/libavcodec.so.52 (0x00007f86eb295000)
        libavutil.so.50 => /usr/lib/libavutil.so.50 (0x00007f86eb085000)
        libswscale.so.0 => /usr/lib/libswscale.so.0 (0x00007f86eae52000)
        libm.so.6 => /lib/libm.so.6 (0x00007f86eabd1000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x00007f86ea9b5000)
        libc.so.6 => /lib/libc.so.6 (0x00007f86ea65c000)
        libasound.so.2 => /usr/lib/libasound.so.2 (0x00007f86ea38b000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0x00007f86ea04f000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0x00007f86e9e3c000)
        libz.so.1 => /lib/libz.so.1 (0x00007f86e9c26000)
        libbz2.so.1 => /lib/libbz2.so.1 (0x00007f86e9a15000)
        libmp3lame.so.0 => /usr/lib/libmp3lame.so.0 (0x00007f86e979b000)
        libvorbisenc.so.2 => /usr/lib/libvorbisenc.so.2 (0x00007f86e92cc000)
        libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0x00007f86e90a0000)
        libx264.so.78 => /usr/lib/libx264.so.78 (0x00007f86e8e0e000)
        libxvidcore.so.4 => /usr/lib/libxvidcore.so.4 (0x00007f86e8b00000)
        /lib64/ld-linux-x86-64.so.2 (0x00007f86ec70a000)
        libdl.so.2 => /lib/libdl.so.2 (0x00007f86e88fc000)
        librt.so.1 => /lib/librt.so.1 (0x00007f86e86f3000)
        libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007f86e84d5000)
        libogg.so.0 => /usr/lib/libogg.so.0 (0x00007f86e82ce000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0x00007f86e80ca000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007f86e7ec4000)

```

Pick your format, then pick your library.  Or pick a multi-format library. 

For instance... libavcodec sounds promising.  I'll poke at the statically linked version because it's easier.

```

myuser@myhost /usr/lib $ nm /usr/lib/libavcodec.a | grep header
                 U imx_dump_header_bsf
                 U mjpega_dump_header_bsf
                 U mp3_header_compress_bsf
                 U mp3_header_decompress_bsf
                 U ff_aac_parse_header
0000000000000000 T ff_aac_parse_header
                 U ff_ac3_parse_header
                 U ff_eac3_parse_header
0000000000000000 T ff_ac3_parse_header
0000000000000560 T ff_ac3_parse_header_full
0000000000000160 t write_frame_header
0000000000000000 r header_prefix.7280
                 U ff_flv_encode_picture_header
                 U ff_h261_encode_picture_header
                 U ff_mjpeg_encode_picture_header
                 U ff_mpeg1_encode_slice_header
                 U ff_mpeg4_encode_video_packet_header
                 U ff_wmv2_encode_picture_header
                 U h263_encode_gob_header
                 U h263_encode_picture_header
                 U mpeg1_encode_picture_header
                 U mpeg4_encode_picture_header
                 U msmpeg4_encode_ext_header
                 U msmpeg4_encode_picture_header
                 U rv10_encode_picture_header
                 U rv20_encode_picture_header
0000000000000e60 T ff_eac3_parse_header
0000000000000000 T ff_flac_parse_block_header
...

```

See all those 'U' bits?  Those are undefined symbols -- as in references to other libraries.   It would be reasonable to guess that this is a wrapper of sorts that provides a common interface.  There's probably code for identifying which formats to try first somewhere in it.  You'll want to do the same.

Should be obvious that e.g. libmp3lame is highly likely to be able to parse the headers of MP3 files, that libvorbis would be aimed at Ogg Vorbis, and so forth.

---

### Post by hakermania on 2010-09-04
but ffmpeg supports mp3,wav and ogg. The 3 formats that I am interested in. My usual question is: What dependencies are required to decode all these files? I mean, what codecs must be installed for this?

---

### Post by hakermania on 2010-09-04
As for the comma, it is easily removed:
ffmpeg -i 'track.ogg' 2>&1 | awk '/Duration/{print $2}' | sed 's/,//g'

---

### Post by hakermania on 2010-09-04
and, as you show me ffmpeg has a lot of dependencies, but I want only them which can be used with ogg mp3 and wav...

---

### Post by andrew.46 on 2010-09-04
A bit cumbersome, as I suspect MPlayer is not really the tool for the job, is this:

```

$ mplayer -vo null -ao null -frames 0 -identify 4last_songs.ogg 2>&1 | grep 'ID_LENGTH' | cut -d "=" -f 2
1334.17

```

But the possibilities with scripting are endless if you really want to go this way...

Andrew

---

### Post by Some Penguin on 2010-09-04
> **hakermania said:**
> and, as you show me ffmpeg has a lot of dependencies, but I want only them which can be used with ogg mp3 and wav...

If you're too lazy to even read filenames, make some educated guesses, and run a few cursory searches, I don't think there's any reason to help you.

---

### Post by soltanis on 2010-09-04
> **hakermania said:**
> As for the comma, it is easily removed:
ffmpeg -i 'track.ogg' 2>&1 | awk '/Duration/{print $2}' | sed 's/,//g'

I'll save you a sed call, even:

```

ffmpeg -i 'track.ogg' 2>&1 | awk '/Duration/{gsub(/,$/,"");print $2}'

```

---

### Post by ghostdog74 on 2010-09-04
> **soltanis said:**
> I'll save you a sed call, even:

```

ffmpeg -i 'track.ogg' 2>&1 | awk '/Duration/{gsub(/,$/,"");print $2}'

```

i will save you one less process call :)

```

var=$(ffmpeg -i track.ogg 2>&1)
var=${var##*Duration: }
echo ${var%%, *}

```

---

### Post by d3v1150m471c on 2010-09-04
```

ffmpeg -i song.mp3 >~/output 2>&1
sed -n '/Duration:/, /s*/p' ~/output | head -1 | tail -1 | sed 's/Duration: //g' | grep -o -s ..:..:..

```

---

### Post by d3v1150m471c on 2010-09-05
> **ghostdog74 said:**
> i will save you one less process call :)

```

var=$(ffmpeg -i track.ogg 2>&1)
var=${var##*Duration: }
echo ${var%%, *}

```

my hero

---

