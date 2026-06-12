---
title: "[HOW-TO] Create DVD-Audio"
date: 2006-12-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Sir_Yaro on 2006-12-24
**1)**
First we have to download and compile main program for dvd authoring:
> 
[yaro][~]$ **cd /tmp**

```
wget http://dvd-audio.sourceforge.net/alpha/dvda-author-20050703.zip
```
follow the bolded lines
> 
[yaro][/tmp]$ **wget http://dvd-audio.sourceforge.net/alpha/dvda-author-20050703.zip**
--18:43:54--  http://dvd-audio.sourceforge.net/alpha/dvda-author-20050703.zip
           => `dvda-author-20050703.zip'
Translacja dvd-audio.sourceforge.net... 66.35.250.209
&#321;&#261;czenie si&#281; z dvd-audio.sourceforge.net|66.35.250.209|:80... po&#322;&#261;czono.
&#379;&#261;danie HTTP wys&#322;ano, oczekiwanie na odpowied&#378;... 200 OK
D&#322;ugo&#347;&#263;: 317,756 (310K) [application/zip]

100%[============================================>] 317,756       24.80K/s    ETA 00:00

18:44:04 (35.88 KB/s) - `dvda-author-20050703.zip' saved [317756/317756]

[yaro][/tmp]$ **unzip dvda-author-20050703.zip**
Archive:  dvda-author-20050703.zip
   creating: dvda-author-20050703/
  inflating: dvda-author-20050703/sort.txt
  inflating: dvda-author-20050703/CHANGES
  inflating: dvda-author-20050703/COPYING
[...]
  inflating: dvda-author-20050703/src/samg.c
  inflating: dvda-author-20050703/src/samg.h
 extracting: dvda-author-20050703/src/version.h
  inflating: dvda-author-20050703/dvda-author.exe
[yaro][/tmp]$ **cd dvda-author-20050703/src**
[yaro][/tmp/dvda-author-20050703/src]$ **sudo apt-get install libc6-dev libflac-dev**
[yaro][/tmp/dvda-author-20050703/src]$ **make**
gcc -Wall   -c -o dvda-author.o dvda-author.c
gcc -Wall   -c -o audio.o audio.c
gcc -Wall   -c -o ats.o ats.c
gcc -Wall   -c -o atsi.o atsi.c
[...]
gcc -Wall -lm -o dvda-author dvda-author.o audio.o ats.o atsi.o amg.o samg.o libFLAC/bitbuffer.o libFLAC/bitmath.o libFLAC/cpu.o libFLAC/crc.o libFLAC/file_decoder.o libFLAC/file_encoder.o libFLAC/fixed.o libFLAC/float.o libFLAC/format.o libFLAC/lpc.o libFLAC/md5.o libFLAC/memory.o libFLAC/metadata_iterators.o libFLAC/metadata_object.o libFLAC/seekable_stream_decoder.o libFLAC/seekable_stream_encoder.o libFLAC/stream_decoder.o libFLAC/stream_encoder.o libFLAC/stream_encoder_framing.o
[yaro][/tmp/dvda-author-20050703/src]$ **ls dvda-author**
-rwxr-xr-x 1 yaro yaro 226966 2006-08-14 18:45 dvda-author
[yaro][/tmp/dvda-author-20050703/src]$ **sudo cp ./dvda-author /usr/bin**

**2)**
now lets create an iso image. Unfortunatelly default mkisofs sort files unproperly. So here we have two options. You can recompile mkisofs and patch it using this file:
[patch](http://dvd-audio.sourceforge.net/mkisofs-dvdaudio.diff)
or use attached patched version of mkisofs. (check bellow).
There is a third way where mkisofs can sort files with a little help of external file but this way is long and unhandy, so i wont describe it here.

**3a) COMPILATION**


```
wget ftp://ftp.berlios.de/pub/cdrecord/cdrtools.tar.gz
```
> 
[yaro][/tmp]$ **wget ftp://ftp.berlios.de/pub/cdrecord/cdrtools.tar.gz**
--19:52:19--  ftp://ftp.berlios.de/pub/cdrecord/cdrtools.tar.gz
           => `cdrtools.tar.gz'
Translacja ftp.berlios.de... 195.37.77.141
&#321;&#261;czenie si&#281; z ftp.berlios.de|195.37.77.141|:21... po&#322;&#261;czono.
Logowanie si&#281; jako anonymous ... Zalogowano si&#281;!
==> SYST ... zrobiono.    ==> PWD ... zrobiono.
==> TYPE I ... zrobiono.  ==> CWD /pub/cdrecord ... zrobiono.
==> PASV ... zrobiono.    ==> RETR cdrtools.tar.gz ... zrobiono.
D&#322;ugo&#347;&#263;: 1,736,017 (1.7M) (nie autorytatywne)

100%[==========================================>] 1,736,017     39.80K/s    ETA 00:00

19:52:55 (51.82 KB/s) - `cdrtools.tar.gz' saved [1736017]

[yaro][/tmp]$

```
wget http://dvd-audio.sourceforge.net/mkisofs-dvdaudio.diff
```
> [yaro][/tmp]$ **wget http://dvd-audio.sourceforge.net/mkisofs-dvdaudio.diff**
--19:54:01--  http://dvd-audio.sourceforge.net/mkisofs-dvdaudio.diff
           => `mkisofs-dvdaudio.diff.1'
Translacja dvd-audio.sourceforge.net... 66.35.250.209
&#321;&#261;czenie si&#281; z dvd-audio.sourceforge.net|66.35.250.209|:80... po&#322;&#261;czono.
&#379;&#261;danie HTTP wys&#322;ano, oczekiwanie na odpowied&#378;... 200 OK
D&#322;ugo&#347;&#263;: 5,972 (5.8K) [text/plain]

100%[===========================================>]  5,972         26.11K/s

19:54:03 (26.02 KB/s) - `mkisofs-dvdaudio.diff' saved [5972/5972]

[yaro][/tmp]$
[yaro][/tmp]$ **tar -xzvf cdrtools.tar.gz  **
cdrtools-2.01/
cdrtools-2.01/RULES/
cdrtools-2.01/RULES/9000-725-hp-ux-cc.rul
cdrtools-2.01/RULES/9000-725-hp-ux-gcc.rul
cdrtools-2.01/RULES/MKLINKS
cdrtools-2.01/RULES/README
cdrtools-2.01/RULES/alpha-linux-cc.rul
cdrtools-2.01/RULES/alpha-linux-gcc.rul
cdrtools-2.01/RULES/aviion-dgux3-cc.rul
[...]
cdrtools-2.01/build_all.com
cdrtools-2.01/scgskeleton/
cdrtools-2.01/scgskeleton/skel.c
cdrtools-2.01/scgskeleton/Makefile
cdrtools-2.01/scgskeleton/scsi_scan.h
cdrtools-2.01/scgskeleton/scsi_scan.c
cdrtools-2.01/scgskeleton/cdrecord.h
cdrtools-2.01/scgskeleton/defaults.h
cdrtools-2.01/scgskeleton/io.c
cdrtools-2.01/scgskeleton/cd_misc.c
cdrtools-2.01/scgskeleton/scsi_cdr.c
cdrtools-2.01/scgskeleton/scsimmc.h
cdrtools-2.01/scgskeleton/modes.c
cdrtools-2.01/scgskeleton/misc.c
cdrtools-2.01/scgskeleton/getnum.c
cdrtools-2.01/scgskeleton/defaults.c
cdrtools-2.01/README.mingw32
cdrtools-2.01/AN-2.01
[yaro][/tmp]$ **mv cdrtools-2.01 cdrtools-2.01.01**
[yaro][/tmp]$ **patch -p0 < mkisofs-dvdaudio.diff**
patching file cdrtools-2.01.01/mkisofs/mkisofs.c
Hunk #4 succeeded at 1814 (offset -4 lines).
Hunk #5 succeeded at 2300 (offset -5 lines).
patching file cdrtools-2.01.01/mkisofs/mkisofs.h
patching file cdrtools-2.01.01/mkisofs/tree.c
patching file cdrtools-2.01.01/mkisofs/udf.c
patching file cdrtools-2.01.01/mkisofs/write.c
[yaro][/tmp]$ **cd cdrtools-2.01.01/**
[yaro][/tmp/cdrtools-2.01.01/]$ **make**
[...]
        ==> LINKING "OBJ/i686-linux-cc/isoinfo"
make[2]: Opuszczenie katalogu `/tmp/cdrtools-2.01.01/mkisofs/diag'
        ==> MAKING "all" ON SUBCOMPONENT "SRCROOT/mkisofs/diag/isovfy.mk"
make[2]: Wej&#347;cie do katalogu `/tmp/cdrtools-2.01.01/mkisofs/diag'
../../RULES/r-gmake.dep:76: OBJ/i686-linux-cc/isovfy.d: Nie ma takiego pliku ani katalogu
        ==> MAKING DEPENDENCIES "OBJ/i686-linux-cc/isovfy.d"
make[2]: Opuszczenie katalogu `/tmp/cdrtools-2.01.01/mkisofs/diag'
make[2]: Wej&#347;cie do katalogu `/tmp/cdrtools-2.01.01/mkisofs/diag'
        ==> COMPILING "OBJ/i686-linux-cc/isovfy.o"
        ==> LINKING "OBJ/i686-linux-cc/isovfy"
[...]
        ==> LOCALIZING "OBJ/i686-linux-cc/man/makerules.5"
make[3]: Opuszczenie katalogu `/tmp/cdrtools-2.01.01/man/man4'
make[2]: Opuszczenie katalogu `/tmp/cdrtools-2.01.01/man/man4'
make[1]: Opuszczenie katalogu `/tmp/cdrtools-2.01.01/man'
[yaro][/tmp/cdrtools-2.01.01]$
[yaro][/tmp/cdrtools-2.01.01]$ **cp /tmp/cdrtools-2.01.01/mkisofs/OBJ/i686-linux-cc/mkisofs ~/bin/mkisofs-dvd-audio **
[yaro][/tmp/cdrtools-2.01.01]$


**3b) COMPILED VERSION**
unzip downloaded attachment and copy it into a bin directory
> [yaro][/tmp]$ **unzip mkisofs-dvd-audio.zip**
Archive:  mkisofs-dvd-audio.zip
  inflating: mkisofs-dvd-audio
[yaro][/tmp]$ **chmod +x mkisofs-dvd-audio**
[yaro][/tmp]$ **cp mkisofs-dvd-audio ~/bin**


**4) Create DVD structure**

change directory to the directory with wav files and execute:
> [yaro][/tmp]$ **cd /tmp/dvd-audio-test/**
[yaro][/tmp/dvd-audio-test]$ **ls**
razem 436704
-rw-r--r-- 1 yaro yaro 49497064 2006-08-14 18:55 0.wav
-rw-r--r-- 1 yaro yaro 54464488 2006-08-14 18:55 1.wav
-rw-r--r-- 1 yaro yaro 43082728 2006-08-14 18:55 2.wav
-rw-r--r-- 1 yaro yaro 52847080 2006-08-14 18:54 3.wav
-rw-r--r-- 1 yaro yaro 38649832 2006-08-14 18:55 4.wav
-rw-r--r-- 1 yaro yaro 42456040 2006-08-14 18:55 5.wav
-rw-r--r-- 1 yaro yaro 63417832 2006-08-14 18:55 6.wav
-rw-r--r-- 1 yaro yaro 53773288 2006-08-14 18:55 7.wav
-rw-r--r-- 1 yaro yaro 48543208 2006-08-14 18:55 8.wav
[yaro][/tmp/dvd-audio-test]$ **dvda-author -o DVD -g *.wav**
dvda-author v0.1-cvs - Copyright (C) 2005 Dave Chapman
Latest version available from [http://dvd-audio.sourceforge.net/](http://dvd-audio.sourceforge.net/)

This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

DVD Layout:

Group  Track    Rate Bits  Ch       Length  Filename
    1     01   44100   16   2     12374255   0.wav
    1     02   44100   16   2     13616111   1.wav
    1     03   44100   16   2     10770671   2.wav
    1     04   44100   16   2     13211759   3.wav
    1     05   44100   16   2      9662447   4.wav
    1     06   44100   16   2     10613999   5.wav
    1     07   44100   16   2     15854447   6.wav
    1     08   44100   16   2     13443311   7.wav
    1     09   44100   16   2     12135791   8.wav

Size of raw PCM data: -5191019945699583212 bytes (12641643646249MB)

INFO: Processing 0.wav
INFO: Processing 1.wav
INFO: Processing 2.wav
INFO: Processing 3.wav
INFO: Processing 4.wav
INFO: Processing 5.wav
INFO: Processing 6.wav
INFO: Processing 7.wav
INFO: Processing 8.wav
INFO: Writing last packet - pack=223365, bytesinbuffer=1180

Group  Track    First Sect   Last Sect  First PTS   PTS length
    1     01           0       24748         585    25253581
    1     02       24749       51980    25254658    27787981
    1     03       51981       73522    53042413    21980961
    1     04       73523       99945    75024046    26962773
    1     05       99946      119270   101986291    19719279
    1     06      119271      140498   121705678    21661222
    1     07      140499      172207   143366903    32356014
    1     08      172208      199094   175723025    27435328
    1     09      199095      223365   203158740    24766920

[yaro][/tmp/dvd-audio-test]$


Notice new *DVD* directory contains correct AUDIO_TS directory and empty VIDEO_TS directory.
**5) CREATE ISO IMAGE**
> 
[yaro][/tmp/dvd-audio-test]$ **mkisofs-dvd-audio -o image.iso -dvd-audio DVD**
  2.24% done, estimate finish Mon Aug 14 19:13:35 2006
  4.47% done, estimate finish Mon Aug 14 19:13:35 2006
  6.70% done, estimate finish Mon Aug 14 19:13:35 2006
  8.94% done, estimate finish Mon Aug 14 19:13:46 2006
[...]
 93.81% done, estimate finish Mon Aug 14 19:13:50 2006
 96.04% done, estimate finish Mon Aug 14 19:13:50 2006
 98.28% done, estimate finish Mon Aug 14 19:13:50 2006
Total translation table size: 0
Total rockridge attributes bytes: 0
Total directory bytes: 4096
Path table size(bytes): 42
Max brk space used 42000
223871 extents written (437 MB)
[yaro][/tmp/dvd-audio-test]$ **ls *iso**
-rw-r--r-- 1 yaro yaro 458487808 2006-08-14 19:13 image.iso
[yaro][/tmp/dvd-audio-test]$


So, thats how we got ready to burn dvd image. Of course you should use much more tracks in a real project to occupy the whole dvd.



[http://yaro.gdi.pl/art/mkisofs-dvdaudio.diff.zip](http://yaro.gdi.pl/art/mkisofs-dvdaudio.diff.zip)
[http://yaro.gdi.pl/art/mkisofs-dvd-audio.zip](http://yaro.gdi.pl/art/mkisofs-dvd-audio.zip)

---

### Post by dude87 on 2007-06-10
I've tried following your instructions and run into all sorts of issues when I issue the make command.  Output below:

gcc -Wall   -c -o dvda-author.o dvda-author.c
dvda-author.c:25:19: error: stdio.h: No such file or directory
dvda-author.c:26:20: error: stdlib.h: No such file or directory
dvda-author.c:27:20: error: string.h: No such file or directory
dvda-author.c:28:20: error: stdint.h: No such file or directory
dvda-author.c:29:22: error: sys/stat.h: No such file or directory
dvda-author.c:30:23: error: sys/types.h: No such file or directory
In file included from libFLAC/include/FLAC/format.h:36,
                 from libFLAC/include/FLAC/stream_decoder.h:36,
                 from libFLAC/include/FLAC/seekable_stream_decoder.h:36,
                 from libFLAC/include/FLAC/file_decoder.h:36,
                 from audio.h:33,
                 from dvda-author.c:37:
libFLAC/include/FLAC/ordinals.h:36:22: error: inttypes.h: No such file or directory
In file included from libFLAC/include/FLAC/format.h:36,
                 from libFLAC/include/FLAC/stream_decoder.h:36,
                 from libFLAC/include/FLAC/seekable_stream_decoder.h:36,
                 from libFLAC/include/FLAC/file_decoder.h:36,
                 from audio.h:33,
                 from dvda-author.c:37:
libFLAC/include/FLAC/ordinals.h:50: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘FLAC__int16’
libFLAC/include/FLAC/ordinals.h:51: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘FLAC__int32’
libFLAC/include/FLAC/ordinals.h:52: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘FLAC__int64’
libFLAC/include/FLAC/ordinals.h:53: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘FLAC__uint16’
libFLAC/include/FLAC/ordinals.h:54: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘FLAC__uint32’
libFLAC/include/FLAC/ordinals.h:55: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘FLAC__uint64’
In file included from libFLAC/include/FLAC/stream_decoder.h:36,
                 from libFLAC/include/FLAC/seekable_stream_decoder.h:36,
                 from libFLAC/include/FLAC/file_decoder.h:36,
                 from audio.h:33,
                 from dvda-author.c:37:
libFLAC/include/FLAC/format.h:267: error: expected specifier-qualifier-list before ‘FLAC__int32’
libFLAC/include/FLAC/format.h:274: error: expected ‘:’, ‘,’, ‘;’, ‘}’ or ‘__attribute__’ before ‘*’ token
libFLAC/include/FLAC/format.h:287: error: expected specifier-qualifier-list before ‘FLAC__int32’
libFLAC/include/FLAC/format.h:310: error: expected specifier-qualifier-list before ‘FLAC__int32’
libFLAC/include/FLAC/format.h:406: error: expected specifier-qualifier-list before ‘FLAC__uint32’
libFLAC/include/FLAC/format.h:433: error: expected specifier-qualifier-list before ‘FLAC__uint16’
libFLAC/include/FLAC/format.h:502: error: expected specifier-qualifier-list before ‘FLAC__uint64’
libFLAC/include/FLAC/format.h:542: error: expected specifier-qualifier-list before ‘FLAC__uint64’
libFLAC/include/FLAC/format.h:564: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘FLAC__STREAM_METADATA_SEEKPOINT_PLACEHOLDER’
libFLAC/include/FLAC/format.h:592: error: expected specifier-qualifier-list before ‘FLAC__uint32’
libFLAC/include/FLAC/format.h:603: error: expected specifier-qualifier-list before ‘FLAC__uint32’
libFLAC/include/FLAC/format.h:615: error: expected specifier-qualifier-list before ‘FLAC__uint64’
libFLAC/include/FLAC/format.h:634: error: expected specifier-qualifier-list before ‘FLAC__uint64’
libFLAC/include/FLAC/format.h:677: error: expected specifier-qualifier-list before ‘FLAC__uint64’
In file included from libFLAC/include/FLAC/seekable_stream_decoder.h:36,
                 from libFLAC/include/FLAC/file_decoder.h:36,
                 from audio.h:33,
                 from dvda-author.c:37:
libFLAC/include/FLAC/stream_decoder.h:363: warning: type defaults to ‘int’ in declaration of ‘FLAC__int32’
libFLAC/include/FLAC/stream_decoder.h:363: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
libFLAC/include/FLAC/stream_decoder.h:456: error: expected declaration specifiers or ‘...’ before ‘FLAC__StreamDecoderWriteCallback’
In file included from libFLAC/include/FLAC/file_decoder.h:36,
                 from audio.h:33,
                 from dvda-author.c:37:
libFLAC/include/FLAC/seekable_stream_decoder.h:305: error: expected declaration specifiers or ‘...’ before ‘FLAC__uint64’
libFLAC/include/FLAC/seekable_stream_decoder.h:318: error: expected declaration specifiers or ‘...’ before ‘FLAC__uint64’
libFLAC/include/FLAC/seekable_stream_decoder.h:331: error: expected declaration specifiers or ‘...’ before ‘FLAC__uint64’
libFLAC/include/FLAC/seekable_stream_decoder.h:356: warning: type defaults to ‘int’ in declaration of ‘FLAC__int32’
libFLAC/include/FLAC/seekable_stream_decoder.h:356: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
libFLAC/include/FLAC/seekable_stream_decoder.h:539: error: expected declaration specifiers or ‘...’ before ‘FLAC__SeekableStreamDecoderWriteCallback’
libFLAC/include/FLAC/seekable_stream_decoder.h:796: error: expected declaration specifiers or ‘...’ before ‘FLAC__uint64’
libFLAC/include/FLAC/seekable_stream_decoder.h:923: error: expected declaration specifiers or ‘...’ before ‘FLAC__uint64’
In file included from audio.h:33,
                 from dvda-author.c:37:
libFLAC/include/FLAC/file_decoder.h:194: warning: type defaults to ‘int’ in declaration of ‘FLAC__int32’
libFLAC/include/FLAC/file_decoder.h:194: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
libFLAC/include/FLAC/file_decoder.h:293: error: expected declaration specifiers or ‘...’ before ‘FLAC__FileDecoderWriteCallback’
libFLAC/include/FLAC/file_decoder.h:558: error: expected declaration specifiers or ‘...’ before ‘FLAC__uint64’
libFLAC/include/FLAC/file_decoder.h:652: error: expected declaration specifiers or ‘...’ before ‘FLAC__uint64’
In file included from dvda-author.c:37:
audio.h:39: error: expected specifier-qualifier-list before ‘FILE’
audio.h:54: error: expected specifier-qualifier-list before ‘uint32_t’
audio.h:69: error: expected ‘)’ before ‘*’ token
audio.h:70: error: expected ‘)’ before ‘*’ token
audio.h:72: error: expected declaration specifiers or ‘...’ before ‘uint8_t’
dvda-author.c: In function ‘main’:
dvda-author.c:55: error: ‘uint64_t’ undeclared (first use in this function)
dvda-author.c:55: error: (Each undeclared identifier is reported only once
dvda-author.c:55: error: for each function it appears in.)
dvda-author.c:55: error: expected ‘;’ before ‘totalsize’
dvda-author.c:57: warning: implicit declaration of function ‘fprintf’
dvda-author.c:57: warning: incompatible implicit declaration of built-in function ‘fprintf’
dvda-author.c:57: error: ‘stderr’ undeclared (first use in this function)
dvda-author.c:71: warning: implicit declaration of function ‘memset’
dvda-author.c:71: warning: incompatible implicit declaration of built-in function ‘memset’
dvda-author.c:76: warning: implicit declaration of function ‘strcmp’
dvda-author.c:79: warning: implicit declaration of function ‘strncpy’
dvda-author.c:79: warning: incompatible implicit declaration of built-in function ‘strncpy’
dvda-author.c:84: warning: implicit declaration of function ‘atoi’
dvda-author.c:127: warning: implicit declaration of function ‘mkdir’
dvda-author.c:133: warning: implicit declaration of function ‘snprintf’
dvda-author.c:133: warning: incompatible implicit declaration of built-in function ‘snprintf’
dvda-author.c:156: error: ‘struct <anonymous>’ has no member named ‘samplerate’
dvda-author.c:156: error: ‘struct <anonymous>’ has no member named ‘numsamples’
dvda-author.c:158: error: ‘totalsize’ undeclared (first use in this function)
dvda-author.c:158: error: ‘struct <anonymous>’ has no member named ‘numbytes’
dvda-author.c:177: error: ‘struct <anonymous>’ has no member named ‘first_sector’
dvda-author.c:177: error: ‘struct <anonymous>’ has no member named ‘last_sector’
dvda-author.c:177: error: ‘struct <anonymous>’ has no member named ‘first_PTS’
dvda-author.c:178: error: ‘struct <anonymous>’ has no member named ‘PTS_length’
make: *** [dvda-author.o] Error 1

---

### Post by Sir_Yaro on 2007-06-11
first:
```
sudo apt-get install libc6-dev libflac-dev
```
and then try again

---

### Post by dude87 on 2007-06-11
Much happier, thanks.  I'll test this out tonight, but at least now I'm compiling properly.

---

### Post by MetalMusicAddict on 2007-06-11
I havnt tried this yet but as a audio guy I have to say thanx. :)

---

### Post by dude87 on 2007-06-11
Cool, this worked fine, including starting with FLAC files instead of WAVs.

thanks!:D

---

### Post by Sir_Yaro on 2007-06-13
You're very welcome

---

### Post by dwasifar on 2008-01-17
Thanks!  I was already making DVD-A discs using mkisofs, but I didn't know about the patched version, so I had to go through the authoring process twice, once to find the AUDIO_PP.IFO start sector, and again using it as a parameter.  This shaves some time off the process for sure.

It looks like the patched mkisofs is using mplayer for something, if I'm reading the process monitor correctly!

---

### Post by robertrej on 2009-05-07
Thats looks really cool I was wondering if it works with a
ac3 audio file instead of wav ?


                      any ideas
                      good day
                      Bob

---

### Post by pprjack on 2009-06-20
wget [http://dvd-audio.sourceforge.net/alpha/dvda-author-20050703.zip](http://dvd-audio.sourceforge.net/alpha/dvda-author-20050703.zip)
Resolving dvd-audio.sourceforge.net... 216.34.181.96
Connecting to dvd-audio.sourceforge.net|216.34.181.96|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-06-20 18:04:20 ERROR 404: Not Found.

This does not seem to work any more.

---

### Post by Sir_Yaro on 2009-06-22
[http://sourceforge.net/project/showfiles.php?group_id=131997&package_id=144979](http://sourceforge.net/project/showfiles.php?group_id=131997&package_id=144979)

was it that hard ?

---

### Post by jonohull on 2010-04-25
I keep getting a segmentation fault every time I run this command:

```
dvda-author -o DVD -g *.wav
```

Any ideas? The gui for this program also does not work.

---

### Post by finite9 on 2010-06-01
Has anyone managed to compile a later version of dvda-author?  Im using Ubuntu 9.10 amd64 and trying to compile dvda-author 9.09 and it keeps failing to make correctly.

I'm trying to burn FLAC24 albums and don't want to convert them to WAV first, and this early version that is described in the first post cannot--as far as I have understood--handle FLAC as input?

---

