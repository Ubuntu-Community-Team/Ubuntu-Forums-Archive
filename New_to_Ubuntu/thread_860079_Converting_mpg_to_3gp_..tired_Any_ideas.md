---
title: "Converting mpg to 3gp ..tired Any ideas??"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Maccabee on 2008-07-15
hi,
     im a newbie in using this ffmpeg i want to convert some video files to 3gp to use in my mobile phone

I heard that default ffmpeg from ubuntu repositories lacks some thing so i added medibuntu repositories and installed ffmpeg,mencoder,etc from there.

i did ```
ffmpeg -formats
```
got this reply

```
File formats:
  E 3g2             3gp2 format
  E 3gp             3gp format
 D  4xm             4X Technologies format
 D  MTV             MTV format
 D  RoQ             Id RoQ format
 D  aac             ADTS AAC
 DE ac3             raw ac3
  E adts            ADTS AAC
 DE aiff            Audio IFF
 DE alaw            pcm A law format
 DE amr             3gpp amr file format
 DE asf             asf format
  E asf_stream      asf format
 DE au              SUN AU Format
 DE audio_device    audio grab and output
 DE avi             avi format
 D  avs             avs format
  E crc             crc testing format
 D  daud            D-Cinema audio format
 D  dc1394          dc1394 A/V grab
 D  dsicin          Delphine Software International CIN format
 D  dts             raw dts
 DE dv              DV video format
 D  dv1394          dv1394 A/V grab
  E dvd             MPEG2 PS format (DVD VOB)
 D  ea              Electronic Arts Multimedia Format
 DE ffm             ffm format
 D  film_cpk        Sega FILM/CPK format
 DE flac            raw flac
 D  flic            FLI/FLC/FLX animation format
 DE flv             flv format
  E framecrc        framecrc testing format
 DE gif             GIF Animation
 DE gxf             GXF format
 DE h261            raw h261
 DE h263            raw h263
 DE h264            raw H264 video format
 D  idcin           Id CIN format
 DE image2          image2 sequence
 DE image2pipe      piped image2 sequence
 D  ingenient       Ingenient MJPEG
 D  ipmovie         Interplay MVE format
 DE m4v             raw MPEG4 video format
 D  matroska        Matroska file format
 DE mjpeg           MJPEG video
 D  mm              American Laser Games MM format
 DE mmf             mmf format
  E mov             mov format
 D  mov,mp4,m4a,3gp,3g2,mj2 QuickTime/MPEG4/Motion JPEG 2000 format
  E mp2             MPEG audio layer 2
 DE mp3             MPEG audio layer 3
  E mp4             mp4 format
 D  mpc             musepack
 DE mpeg            MPEG1 System format
  E mpeg1video      MPEG video
  E mpeg2video      MPEG2 video
 DE mpegts          MPEG2 transport stream format
 D  mpegvideo       MPEG video
  E mpjpeg          Mime multipart JPEG format
 DE mulaw           pcm mu law format
 D  mxf             MXF format
 D  nsv             NullSoft Video format
  E null            null video format
 D  nut             nut format
 D  nuv             NuppelVideo format
 DE ogg             Ogg format
  E psp             psp mp4 format
 D  psxstr          Sony Playstation STR format
 DE rawvideo        raw video format
 D  redir           Redirector format
 DE rm              rm format
  E rtp             RTP output format
 D  rtsp            RTSP input format
 DE s16be           pcm signed 16 bit big endian format
 DE s16le           pcm signed 16 bit little endian format
 DE s8              pcm signed 8 bit format
 D  sdp             SDP
 D  shn             raw shorten
 D  smk             Smacker Video
 D  sol             Sierra SOL Format
  E svcd            MPEG2 PS format (VOB)
 DE swf             Flash format
 D  tiertexseq      Tiertex Limited SEQ format
 D  tta             true-audio
 DE u16be           pcm unsigned 16 bit big endian format
 DE u16le           pcm unsigned 16 bit little endian format
 DE u8              pcm unsigned 8 bit format
 D  vc1             raw vc1
  E vcd             MPEG1 System format (VCD)
 D  video4linux     video grab
 D  video4linux2    video grab
 D  vmd             Sierra VMD format
  E vob             MPEG2 PS format (VOB)
 DE voc             Creative Voice File format
 DE wav             wav format
 D  wc3movie        Wing Commander III movie format
 D  wsaud           Westwood Studios audio format
 D  wsvqa           Westwood Studios VQA format
 D  wv              WavPack
 DE yuv4mpegpipe    YUV4MPEG pipe format

Codecs:
 D V    4xm
 D V D  8bps
 D V    VMware video
 D V D  aasc
  EA    ac3
 DEA    adpcm_4xm
 DEA    adpcm_adx
 DEA    adpcm_ct
 DEA    adpcm_ea
 DEA    adpcm_ima_dk3
 DEA    adpcm_ima_dk4
 DEA    adpcm_ima_qt
 DEA    adpcm_ima_smjpeg
 DEA    adpcm_ima_wav
 DEA    adpcm_ima_ws
 DEA    adpcm_ms
 DEA    adpcm_sbpro_2
 DEA    adpcm_sbpro_3
 DEA    adpcm_sbpro_4
 DEA    adpcm_swf
 DEA    adpcm_xa
 DEA    adpcm_yamaha
 D A    alac
 DEV D  asv1
 DEV D  asv2
 D V D  avs
 DEV    bmp
 D V D  camstudio
 D V D  camtasia
 D V D  cavs
 D V D  cinepak
 D V D  cljr
 D A    cook
 D V D  cyuv
 D A    dca
 D A    dsicinaudio
 D V D  dsicinvideo
 DES    dvbsub
 DES    dvdsub
 DEV D  dvvideo
 DEV D  ffv1
 DEVSD  ffvhuff
 DEA    flac
 DEV D  flashsv
 D V D  flic
 DEVSD  flv
 D V D  fraps
 DEA    g726
 DEV    gif
 DEA    gsm
 D A    gsm_ms
 DEV D  h261
 DEVSDT h263
 D VSD  h263i
  EV    h263p
 D V DT h264
 DEVSD  huffyuv
 D V D  idcinvideo
 D A    imc
 D V D  indeo2
 D V    indeo3
 D A    interplay_dpcm
 D V D  interplayvideo
  EV    jpegls
 D V    kmvc
  EV    libtheora
  EV    ljpeg
 D V D  loco
 D A    mace3
 D A    mace6
 D V D  mdec
 DEV D  mjpeg
 D V D  mjpegb
 D V D  mmvideo
 DEA    mp2
 D A    mp3
 D A    mp3adu
 D A    mp3on4
 D A    mpc sv7
 DEVSDT mpeg1video
 DEVSDT mpeg2video
 DEVSDT mpeg4
 D VSDT mpegvideo
 DEVSD  msmpeg4
 DEVSD  msmpeg4v1
 DEVSD  msmpeg4v2
 D V D  msrle
 D V D  msvideo1
 D V D  mszh
 D V D  nuv
 DEV    pam
 DEV    pbm
 DEA    pcm_alaw
 DEA    pcm_mulaw
 DEA    pcm_s16be
 DEA    pcm_s16le
 DEA    pcm_s24be
 DEA    pcm_s24daud
 DEA    pcm_s24le
 DEA    pcm_s32be
 DEA    pcm_s32le
 DEA    pcm_s8
 DEA    pcm_u16be
 DEA    pcm_u16le
 DEA    pcm_u24be
 DEA    pcm_u24le
 DEA    pcm_u32be
 DEA    pcm_u32le
 DEA    pcm_u8
 DEV    pgm
 DEV    pgmyuv
 DEV    png
 DEV    ppm
 D A    qdm2
 D V D  qdraw
 D V D  qpeg
 D V D  qtrle
 DEV    rawvideo
 D A    real_144
 D A    real_288
 D A    roq_dpcm
 D V D  roqvideo
 D V D  rpza
 DEV D  rv10
 DEV D  rv20
 D A    shorten
 D A    smackaud
 D V    smackvid
 D V D  smc
 DEV    snow
 D A    sol_dpcm
 DEA    sonic
  EA    sonicls
 D V D  sp5x
 DEV D  svq1
 D VSD  svq3
 D V    targa
 D V    theora
 D V D  tiertexseqvideo
 D V    tiff
 D V D  truemotion1
 D V D  truemotion2
 D A    truespeech
 D A    tta
 D V D  ultimotion
 D V    vc1
 D V D  vcr1
 D A    vmdaudio
 D V D  vmdvideo
 DEA    vorbis
 D V    vp3
 D V    vp5
 D V    vp6
 D V    vp6f
 D V D  vqavideo
 D A    wavpack
 DEA    wmav1
 DEA    wmav2
 DEVSD  wmv1
 DEVSD  wmv2
 D V    wmv3
 D V D  wnv1
 D A    ws_snd1
 D A    xan_dpcm
 D V D  xan_wc3
 D V D  xl
 DEV D  zlib
 DEV    zmbv

Supported file protocols:
 file: pipe: udp: rtp: tcp: http:
Frame size, frame rate abbreviations:
 ntsc pal qntsc qpal sntsc spal film ntsc-film sqcif qcif cif 4cif
Motion estimation methods:
 zero(fastest) full(slowest) log phods epzs(default) x1 hex umh iter

Note, the names of encoders and decoders dont always match, so there are
several cases where the above table shows encoder only or decoder only entries
even though both encoding and decoding are supported for example, the h263
decoder corresponds to the h263 and h263p encoders, for file formats its even
worse
```


Then i issued the command
```
ffmpeg -i test.mpg -s qcif -vcodec h263 -acodec mp3 -ac 1 -ar 8000 -ab 32 -y clip.3gp

```

but the result is

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 23 2008 22:28:54, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
Input #0, mpeg, from 'test.mpg':
  Duration: 00:01:14.9, start: 0.446211, bitrate: 626 kb/s
  Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 384x288, 104857 kb/s, 25.00 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 44100 Hz, stereo, 128 kb/s
Output #0, 3gp, to 'clip.3gp':
  Stream #0.0: Video: h263, yuv420p, 176x144, q=2-31, 200 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: 0x0000, 8000 Hz, mono, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1

```
can somebody please help me...

---

### Post by philinux on 2008-07-15
[http://goinggnu.wordpress.com/2007/02/13/convert-avi-to-3gp-using-ffmpeg/](http://goinggnu.wordpress.com/2007/02/13/convert-avi-to-3gp-using-ffmpeg/)

---

### Post by Maccabee on 2008-07-15
Hi i ve read the page but i ve already installed all the multimedia codecs
as far as i know

i found they reply offered there is to install
```

sudo apt-get install ubuntu-restricted-extras
sudo apt-get install w32codecs
sudo apt-get install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll

```
All these are alredy installed and is the newest versions
but in the last item i vent installed thelibxine extra codecs as i vent installed xine..is that the problem ??

Is there any other codecs i needs to install??
..Can sombody help me?? :(

---

### Post by philinux on 2008-07-15
Well I just tried that command, had to install ffmpeg first, and it worked.

Mine is a clean install 3 days ago, 64 bit.

I've installed ubuntu-restricted-extras and w64codecs but nothing else.

---

