---
title: "Video Trusty vpx_codec_vp9_dx_algo"
date: 2015-04-16
forum: New to Ubuntu
---

### Post by jpvrlau on 2015-04-16
**PROBLEM:**

 Recently, not sure at what point, my video players started failing except for mplayer located in the /usr/local/bin directory and it's kinda shaky.   I have tested different formats and  browsers (Firefox, Chrome, Midori) they basically get the same errors or just provide a frame with blank video.  In fact, I have the same video issues on a cloned 14.04 that is 3 months removed.  It's sad to say I do not have this problem  on my Windows 7 server (dual boot drive) where I can view MLBtv and Amazon Prime as expected.   Apparently there is something amiss with libavcodec.so.54.   Several attempts were made to correct this but things just got worse.   Had high hopes for installing ffmpeg-2.6.1 but the errors continue. How do I get things straightened out or get to a base line without having to do a complete reinstall of Trusty? Is there trouble shooting doc that Ubuntu addresses with software video issues?  Anyone else experiencing this broad of a problem with video players?  THANKS!!!
                        

**GIVEN:**

  **Trusty 14.04**
 Linux version 3.13.0-49-generic (buildd@akateko) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #83-Ubuntu SMP Fri Apr 10 20:11:33 UTC 2015 (Ubuntu 3.13.0-49.83-generic 3.13.11-ckt17)
 Memory 3.7 Gb

 Processor Intel Core I5 CPU650@320GHzx4

 Graphics Intel Ironlake Desktop
 OS type 64-bit

  


  $ ls -ald /usr/local/bin/mplayer /usr/bin/mplayer  
 -rwxr-xr-x 1 root root  2328144 Mar 27  2014 /usr/bin/mplayer  SEE ERROR BELOW

 -rwxr-xr-x 1 root root 12041024 Aug  5  2014 /usr/local/bin/mplayer  WORKS ON ALL FORMATS (includes mlbviewer but is not full-featured as last season)

 
 
 $ **/usr/bin/mplayer** testing.mov
 /usr/bin/mplayer: symbol lookup error: /usr/lib/x86_64-linux-gnu/libavcodec.so.54: undefined symbol: vpx_codec_vp9_dx_algo

 
 
 $ **/usr/bin/mpv **testing.mov
 /usr/bin/mpv: symbol lookup error: /usr/bin/mpv: undefined symbol: vpx_codec_vp9_dx_algo
 
 
 $ **/usr/bin/xbmc** testing.mov
 /usr/lib/xbmc/xbmc.bin: symbol lookup error: /usr/lib/x86_64-linux-gnu/libavcodec.so.54: undefined symbol: vpx_codec_vp9_dx_algo
 
 
 $ **/usr/bin/vlc **vlc-record-2015-03-06-16h39m21s-fd___0-.mp4  
 VLC media player 2.2.0-rc2 Weatherwax (revision 2.2.0+ppa3.2)
 [000000000148ba98] skins2 interface: skin: Debian Red Coast  author: Mateusz Jagiello
 [000000000148ba98] skins2 interface error: pls, check bitmap sizes for id: button_ff
 [000000000148ba98] skins2 interface error: pls, check bitmap sizes for id: button_ff
 [000000000148ba98] skins2 interface error: pls, check bitmap sizes for id: button_d_ff
 [000000000148ba98] skins2 interface error: pls, check bitmap sizes for id: button_d_ff
 [000000000148ba98] skins2 interface error: cannot resolve boolean variable: vlc.hasVout(false
 [000000000148ba98] skins2 interface error: unknown bitmap id: pl.png.controls.bg.resizeS
 [000000000148ba98] skins2 interface error: pls, provide a valid size for the video control id: video_design (dropping the video control)
 [00007f5b2cce8388] core decoder error: Codec `h264' (H264 - MPEG-4 AVC (part 10)) is not supported.\

**smplayer **was tried earlier with same libavcodec.so.54 error but was uninstalled

---

### Post by mc4man on 2015-04-16
What do these show?
```
ldd /usr/lib/vlc/plugins/codec/libavcodec_plugin.so |grep libavcodec
```
```
apt-cache policy mpv 
```

And provide sample of testing.mov if possible

---

### Post by jpvrlau on 2015-04-16
pc:~/Tests$ ldd /usr/lib/vlc/plugins/codec/libavcodec_plugin.so |grep libavcodec
ldd: /usr/lib/vlc/plugins/codec/libavcodec_plugin.so: No such file or directory
pc:~/Tests$ apt-cache policy mpv
mpv:
  Installed: 2:0.8.3+git3
  Candidate: 2:0.8.3+git3
  Version table:
 *** 2:0.8.3+git3 0
        500 [http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu/](http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     2:0.8.0+git1.1 0
        500 [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/) trusty/main amd64 Packages
     0.3.4-1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages

---

### Post by mc4man on 2015-04-16
Re: mpv
That's the package I use & have never seen such an error with vp8/9 files of all sorts. So if you can provide a sample will take a look.

Re: vlc 
No clue what you're up to. The vlc-nox package would have installed that plugin to where I posted. 
Do you have vlc-nox installed? Do you have a vlc self-build in /usr/local/ ?

---

### Post by jpvrlau on 2015-04-17
Subsequent to your follow up I tried specifying  libvacodec54 via synaptic which deleted vlc.  I reloaded vlc using synaptic and it now works on all video tests with a few minor errors.  Have yet to check other video players.
  	 	 	 	   ```
$ vlc TEST.avi
 VLC media player 2.2.0-rc2 Weatherwax (revision 2.2.0+ppa3.2)
 [0000000001b93ff8] skins2 interface: skin: Debian Red Coast  author: Mateusz Jagiello
 [0000000001b93ff8] skins2 interface error: pls, check bitmap sizes for id: button_ff
 [0000000001b93ff8] skins2 interface error: pls, check bitmap sizes for id: button_ff
 [0000000001b93ff8] skins2 interface error: pls, check bitmap sizes for id: button_d_ff
 [0000000001b93ff8] skins2 interface error: pls, check bitmap sizes for id: button_d_ff
 [0000000001b93ff8] skins2 interface error: cannot resolve boolean variable: vlc.hasVout(false
 [0000000001b93ff8] skins2 interface error: unknown bitmap id: pl.png.controls.bg.resizeS
 [0000000001b93ff8] skins2 interface error: pls, provide a valid size for the video control id: video_design (dropping the video control)
 TESTing.wma
 VLC media player 2.2.0-rc2 Weatherwax (revision 2.2.0+ppa3.2)
 [0000000001654e48] skins2 interface: skin: Debian Red Coast  author: Mateusz Jagiello
 [0000000001654e48] skins2 interface error: pls, check bitmap sizes for id: button_ff
 [0000000001654e48] skins2 interface error: pls, check bitmap sizes for id: button_ff
 [0000000001654e48] skins2 interface error: pls, check bitmap sizes for id: button_d_ff
 [0000000001654e48] skins2 interface error: pls, check bitmap sizes for id: button_d_ff
 [0000000001654e48] skins2 interface error: cannot resolve boolean variable: vlc.hasVout(false
 [0000000001654e48] skins2 interface error: unknown bitmap id: pl.png.controls.bg.resizeS
 [0000000001654e48] skins2 interface error: pls, provide a valid size for the video control id: video_design (dropping the video control)
 TEST.mov
 VLC media player 2.2.0-rc2 Weatherwax (revision 2.2.0+ppa3.2)
 [0000000002457008] skins2 interface: skin: Debian Red Coast  author: Mateusz Jagiello
 [0000000002457008] skins2 interface error: pls, check bitmap sizes for id: button_ff
 [0000000002457008] skins2 interface error: pls, check bitmap sizes for id: button_ff
 [0000000002457008] skins2 interface error: pls, check bitmap sizes for id: button_d_ff
 [0000000002457008] skins2 interface error: pls, check bitmap sizes for id: button_d_ff
 [0000000002457008] skins2 interface error: cannot resolve boolean variable: vlc.hasVout(false
 [0000000002457008] skins2 interface error: unknown bitmap id: pl.png.controls.bg.resizeS
 [0000000002457008] skins2 interface error: pls, provide a valid size for the video control id: video_design (dropping the video control)
 TEST.mpg
 VLC media player 2.2.0-rc2 Weatherwax (revision 2.2.0+ppa3.2)
 [00000000021fcff8] skins2 interface: skin: Debian Red Coast  author: Mateusz Jagiello
 [00000000021fcff8] skins2 interface error: pls, check bitmap sizes for id: button_ff
 [00000000021fcff8] skins2 interface error: pls, check bitmap sizes for id: button_ff
 [00000000021fcff8] skins2 interface error: pls, check bitmap sizes for id: button_d_ff
 [00000000021fcff8] skins2 interface error: pls, check bitmap sizes for id: button_d_ff
 [00000000021fcff8] skins2 interface error: cannot resolve boolean variable: vlc.hasVout(false
 [00000000021fcff8] skins2 interface error: unknown bitmap id: pl.png.controls.bg.resizeS
 [00000000021fcff8] skins2 interface error: pls, provide a valid size for the video control id: video_design (dropping the video control)
 TEST.swf
 VLC media player 2.2.0-rc2 Weatherwax (revision 2.2.0+ppa3.2)
 [0000000001208008] skins2 interface: skin: Debian Red Coast  author: Mateusz Jagiello
 [0000000001208008] skins2 interface error: pls, check bitmap sizes for id: button_ff
 [0000000001208008] skins2 interface error: pls, check bitmap sizes for id: button_ff
 [0000000001208008] skins2 interface error: pls, check bitmap sizes for id: button_d_ff
 [0000000001208008] skins2 interface error: pls, check bitmap sizes for id: button_d_ff
 [0000000001208008] skins2 interface error: cannot resolve boolean variable: vlc.hasVout(false
 [0000000001208008] skins2 interface error: unknown bitmap id: pl.png.controls.bg.resizeS
 [0000000001208008] skins2 interface error: pls, provide a valid size for the video control id: video_design (dropping the video control)
 TEST.wmv
 VLC media player 2.2.0-rc2 Weatherwax (revision 2.2.0+ppa3.2)
 [0000000001330ff8] skins2 interface: skin: Debian Red Coast  author: Mateusz Jagiello
 [0000000001330ff8] skins2 interface error: pls, check bitmap sizes for id: button_ff
 [0000000001330ff8] skins2 interface error: pls, check bitmap sizes for id: button_ff
 [0000000001330ff8] skins2 interface error: pls, check bitmap sizes for id: button_d_ff
 [0000000001330ff8] skins2 interface error: pls, check bitmap sizes for id: button_d_ff
 [0000000001330ff8] skins2 interface error: cannot resolve boolean variable: vlc.hasVout(false
 [0000000001330ff8] skins2 interface error: unknown bitmap id: pl.png.controls.bg.resizeS
 [0000000001330ff8] skins2 interface error: pls, provide a valid size for the video control id: video_design (dropping the video control)
 vlc-record-2015-03-06-16h39m21s-fd___0-.mp4
 VLC media player 2.2.0-rc2 Weatherwax (revision 2.2.0+ppa3.2)
 [000000000250a068] skins2 interface: skin: Debian Red Coast  author: Mateusz Jagiello
 [000000000250a068] skins2 interface error: pls, check bitmap sizes for id: button_ff
 [000000000250a068] skins2 interface error: pls, check bitmap sizes for id: button_ff
 [000000000250a068] skins2 interface error: pls, check bitmap sizes for id: button_d_ff
 [000000000250a068] skins2 interface error: pls, check bitmap sizes for id: button_d_ff
 [000000000250a068] skins2 interface error: cannot resolve boolean variable: vlc.hasVout(false
 [000000000250a068] skins2 interface error: unknown bitmap id: pl.png.controls.bg.resizeS
 [000000000250a068] skins2 interface error: pls, provide a valid size for the video control id: video_design (dropping the video control)
 [00007f1680161038] freetype spu text error: Breaking unbreakable line
```

---

### Post by mc4man on 2015-04-17
Re: vlc
Using  skins is prone to errors as many aren't that well done or currently compatible.
This should open vlc without any such errors
 ```
vlc -Iqt4
```

---

### Post by jpvrlau on 2015-04-17
After resinstalling vlc and mplayer(mplayer2) via synaptic all tests were good excepting tons of errors on the command  line for the swf test (   	 	 	 	   [mjpeg @ 0x7f9d2568daa0]Found EOI before any SOF, ignoring V:   3.6   0/  0  2%  0%  0.0% 0 0) which still had visilble video.

That's the good news but mpv continues to report    	 	 	 	   

/usr/bin/mpv: symbol lookup error: /usr/bin/mpv: undefined symbol: vpx_codec_vp9_dx_algo

  
Below are notes taken while trouble-shooting ffmpeg.  I find it rather confusing and I feel like there should be some policy statement or authority to resolve ffmpeg issues once and for all.
Maybe I should just be happy vlc, mplayer, and even smplayer are working.  Thanks to all who have helped and are helping.
  	 	 	 	   

```
pc:~/Tests$ sudo apt-get -f install
 [sudo] password for   

 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 The following packages were automatically installed and are no longer required:
   gstreamer1.0-plugins-bad-faad gstreamer1.0-plugins-bad-videoparsers
   libfluidsynth1 libgavl1 libgstreamer-plugins-bad1.0-0 libgtkglext1
   libmicrohttpd10 libnfs1 libopencv-calib3d2.4 libopencv-core2.4
   libopencv-features2d2.4 libopencv-flann2.4 libopencv-imgproc2.4
   libopencv-ml2.4 libopencv-video2.4 librcc0 librcd0 libshairport1
   libsidutils0 libsrtp0 libtagc0 libtbb2 moc
 Use 'apt-get autoremove' to remove them.
 0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
 Lpc:~/Tests$ apt-cache policy ffmpeg  
 ffmpeg:
   Installed: (none)
   Candidate: 7:2.6.2~trusty
   Version table:
      7:2.6.2~trusty 0
         500 [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/) trusty/main amd64 Packages
 
```
 
 
 
 ```
pc:~/Tests$ apt-cache policy libavcodec54
 libavcodec54:
   Installed: 6:9.18-0ubuntu0.14.04.1+fdkaac
   Candidate: 6:9.18-0ubuntu0.14.04.1+fdkaac
   Version table:
  *** 6:9.18-0ubuntu0.14.04.1+fdkaac 0
         500 [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/) trusty/main amd64 Packages
         100 /var/lib/dpkg/status
      6:9.18-0ubuntu0.14.04.1 0
         500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/universe amd64 Packages
         500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe amd64 Packages
  	 	 	 	   
sudo apt-get install ffmpeg  
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 Some packages could not be installed. This may mean that you have
 requested an impossible situation or if you are using the unstable
 distribution that some required packages have not yet been created
 or been moved out of Incoming.
 The following information may help to resolve the situation:
 
 
 The following packages have unmet dependencies:
  ffmpeg : Depends: libx265-49 but it is not going to be installed
 E: Unable to correct problems, you have held broken packages.
 
```
 
 
 
```
 $ sudo dpkg --get-selections  |grep ffmpeg  
 chromium-codecs-ffmpeg-extra			install
 ffmpeg-opti					install
 ffmpeg-real					install
 gstreamer0.10-ffmpeg:amd64			install
 libavcodec56-ffmpeg				install
 libavdevice56-ffmpeg				install
 libavfilter5-ffmpeg				install
 libavformat56-ffmpeg				install
 libavresample2-ffmpeg				install
 libavutil54-ffmpeg				install
 libpostproc53-ffmpeg				install
 libswresample1-ffmpeg				install
 libswscale3-ffmpeg				install
 
 
 
 
 E: Unable to correct problems, you have held broken packages.
 E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
 E: Unable to correct dependencies
 E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
 E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
 E: Unable to correct dependencies
 E: Unable to correct problems, you have held broken packages.
 E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
 E: Unable to correct dependencies
 E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
 E: Unable to correct dependencies
```
 
 
 
 
 
 
 MPV is a versatile CLI movie player, based on mplayer and mplayer2.
 This build uses latest git FFmpeg & libass with some encoding support
 
 
 
 

```
/usr/bin/mplayer -noquiet -slave -identify -nofs -sub-fuzziness 1 -vo xv, -ao pulse -nodr -double -stop-xscreensaver -nomouseinput -input nodefault-bindings:conf=/dev/null -nokeepaspect -wid 65011756 -monitorpixelaspect 1 -subfont-osd-scale 3 -ass -embeddedfonts -ass-line-spacing 0 -ass-font-scale 1 -noflip-hebrew -ass-styles /home/XXXX/.config/smplayer/styles.ass -subcp ISO-8859-1 -vid 0 -subpos 100 -volume 50 -cache 2048 -osdlevel 0 -vf-add screenshot -noslices -channels 2 -af-add scaletempo -af-add equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/XXX/Tests/test2.avi

 

 
 Unknown option on the command line: --noflip-hebrew
 Error parsing option on the command line: -noflip-hebrew
 MPlayer2 2.0-701-gd4c5b7f-2ubuntu2 (C) 2000-2012 MPlayer Team
 ID_EXIT=NONE
```

---

### Post by mc4man on 2015-04-17
> That's the good news but mpv continues to report

/usr/bin/mpv: symbol lookup error: /usr/bin/mpv: undefined symbol: vpx_codec_vp9_dx_algo
As mentioned you need to put this into some context & if ocurring on specific files provide a sample. Otherwise nothing to be done to help you..

As far as ffmpeg 
> ffmpeg:
Installed: (none)
Candidate: 7:2.6.2~trusty
This ^ is a static only build, only provides the ffmpeg binaries, nothing that's used by any player so likely you have no use for it...
> ffmpeg-opti install
ffmpeg-real install
gstreamer0.10-ffmpeg:amd64 install
libavcodec56-ffmpeg install
libavdevice56-ffmpeg install
libavfilter5-ffmpeg install
libavformat56-ffmpeg install
libavresample2-ffmpeg install
libavutil54-ffmpeg install
libpostproc53-ffmpeg install
libswresample1-ffmpeg install
libswscale3-ffmpeg install
These ^  are from Sam Rog ppa.  If you have issue with them I can't help you but they have nothing to do with mpv. I'm somewhat at a loss as to the value of those shared ffmpeg libs from rog ppa as virtually nothing is provided that uses them (maybe kaffeine & some thumbnailer. What did you hope to gain by using them??

---

### Post by mc4man on 2015-04-17
The reason you can't install ffmpeg from the trusty multimedia ppa is the the libx265 package in the Rog ppa sets a Conflicts: & Replaces: on any other version of libx265-XX
This is not needed or proper by any means. 
You already have the equivalent installed in the ffmpeg-opti package so nothing to be gained by trying to install ffmpeg package.

edit - rog libx265-XX control file - 
> Package: libx265-55
Architecture: any
Multi-Arch: same
Depends: ${misc:Depends}, ${shlibs:Depends}
Conflicts: libx265-44, 
 libx265-45, 
 libx265-46, 
 libx265-47, 
 libx265-48, 
 libx265-49, 
 libx265-50, 
 libx265-51,
 libx265-52,
 libx265-53,
 libx265-54
Replaces: libx265-44, 
 libx265-45, 
 libx265-46, 
 libx265-47, 
 libx265-48, 
 libx265-49, 
 libx265-50, 
 libx265-51,
 libx265-52,
 libx265-53,
 libx265-54

---

### Post by jpvrlau on 2015-04-18
Evidently I have been barking up the wrong tree due to my over-googling.
I just need to reduce my problems to why the following do not work:
---mpv, error noted previously, never got off the ground on this one
---amazon prime instant video:  worked fine for months, does not work on any browser(firefox,chrome,midori), works on windows 7, suspect flash issues (another can of worms)
COMMENT:  I've been a unix/linux user, an OK admin, for 20 years and the hallmark of an OS is it's consistency and reliability especially one classified as an LTS.  
I just hate the fact that I find myself having to turn to my Windows 7 for trouble-free viewing these days.

---

### Post by wildmanne39 on 2015-04-18
@jpvrlau, please follow the directions in my signature for how to use code tags and edit your posts using code tags to make  the posts easily readable.
Thanks

---

### Post by mc4man on 2015-04-18
My final comment on this - 
if you can't provide a sample problem file or even  put the error into context then there is nothing to be done, at least from me.
this - "usr/bin/mpv: symbol lookup error: /usr/bin/mpv: undefined symbol: vpx_codec_vp9_dx_algo"  is practically worthless for troubleshooting
At a min complete output from - 
mpv -v --no-config /path/to/file

---

### Post by jpvrlau on 2015-05-11
I cannot provide anything if the  mpv command  errors immediately.  I cannot even get a response to help.  Note that I have seen 3 updates for mpv in recent weeks and the same error occurs.
  $ mpv --help
mpv: symbol lookup error: mpv: undefined symbol: vpx_codec_vp9_dx_algo

---

### Post by SeijiSensei on 2015-05-11
Watching Amazon Instant requires installing the now-deprecated HAL package or pipelight: [http://www.howtogeek.com/204319/how-to-watch-amazon-instant-video-on-linux/](http://www.howtogeek.com/204319/how-to-watch-amazon-instant-video-on-linux/)

---

### Post by mc4man on 2015-05-11
Post results

ldd /usr/bin/mpv |grep libvpx
apt-cache policy libvpx1

Note: this post will self-destruct in 14 days..

---

### Post by jpvrlau on 2015-05-25
Requested results below:
PS There was another mpv software update(05.25.2015) and the vpx_codec_vp9_dx_algo error continues.

$ ldd /usr/bin/mpv |grep libvpx
    libvpx.so.1 => /usr/local/lib/libvpx.so.1 (0x00007ff7107cf000)
xxxxxxx:~/Tests$ apt-cache policy libvpx1
libvpx1:
  Installed: 1.3.0-3~trusty
  Candidate: 1.3.0-3~trusty
  Version table:
 *** 1.3.0-3~trusty 0
        500 [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     1.3.0-2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages

---

### Post by mc4man on 2015-05-25
```
$ ldd /usr/bin/mpv |grep libvpx
libvpx.so.1 => /usr/local/lib/libvpx.so.1
```
That version of libvpx is not from Installed: 1.3.0-3~trusty which installs to /usr/lib/*

Ex. here & *what you should see* - 
> ldd /usr/bin/mpv |grep libvpx
	libvpx.so.1 => /usr/lib/x86_64-linux-gnu/libvpx.so.1 
You installed some version of libvpx yourself to /usr/local/lib/
So remove it & mpv will work properly, as your libvpx isn't   package managed you'll need to do so manually as root. 
After removing /usr/local/lib/libvpx*, there will be more than 1 file,   you may need to run - 

sudo ldconfig

Then rerun the ldd command, it should look  as I've posted above.

Until you do that mpv will not start up, you should also remove any & all  traces of libvpx from /usr/local/*

Edit: if after the above mpv fails on something else then run this, it it returns anything at all  then you may  need to remove those libs also. I'd run even if mpv is ok to see if you've installed other libs that you've apparently 'forgotten' about to /usr/local/
```
ldd /usr/bin/mpv |grep /usr/local/
```

---

### Post by jpvrlau on 2015-06-19
Thanks! mc4man.  Removing /usr/local/lib/libvpx* files allowed mpv to run correctly. :p

---

