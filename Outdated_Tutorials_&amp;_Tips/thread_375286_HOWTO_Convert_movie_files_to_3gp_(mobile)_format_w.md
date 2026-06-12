---
title: "HOWTO: Convert movie files to 3gp (mobile) format with sound."
date: 2007-03-03
forum: Outdated Tutorials &amp; Tips
---

### Post by gmatt on 2007-03-03
This howto guides you through the process of setting up ffmpeg on your computer so that you can convert your avi and other movies to mobile (psp, cellphone) 3gp format. It is short, which I hope that you will appreciate. Most of the work will be done by a script.

[COLOR="SeaGreen"]You need to install SVN for this to work. To get it ```
 sudo apt-get install svn
```[/COLOR]

[COLOR="Red"]
Updated May 24 2007 6pm:
- After a little bit of testing I have found that the newer versions from SVN have broken the libraries needed by the C code to compile, it is best just to use the SVN version from the time that this worked. 
- There may have been a recent update to ffmpeg that removes the need for this howto that I am not aware of. If there is please tell me or post here!
- Thanks to dragoncow2 for showing how to download previous versions of SVN, so I don't have to look it up. The script here is updated with his change. 
- Everything should work perfect now! Have fun ;)

Updated May 24 2007 12am:
- I have fixed the links in the script so that they do not get truncated, I've noticed that has bugged people
- I am testing the svn newer versions and trying to see why they do not work with the old codec[/COLOR]

First, uinstall any ffmpeg you might have currently installed. The usual command that will do this is
 ```
sudo apt-get remove ffmpeg
```
Next, save the following into a script and make it executable and run it:
```

#!/bin/bash

# feel free to change the src directory
cd /usr/src/

#will download the newest svn ffmpeg
svn co -r '{2007-03-03}' svn://svn.mplayerhq.hu/ffmpeg trunk ffmpeg
#Install the required audio codecs for 3gp videos
cd ffmpeg/libavcodec
mkdir amr_float
cd amr_float
wget http://www.3gpp.org/ftp/Specs/archive/26_series/26.104/26104-510.zip
unzip *.zip
unzip *code.zip
cd ..
mkdir amrwb_float
cd amrwb_float
wget http://www.3gpp.org/ftp/Specs/archive/26_series/26.204/26204-510.zip
unzip *.zip
unzip *code.zip
cd ../..
#configure ffmpeg to use these audio codecs
./configure --enable-amr_nb --enable-amr_wb $@
make

#link the ffmpeg binary to somewhere in PATH so you can run it anywhere
ln -sf /usr/src/ffmpeg/ffmpeg /usr/local/bin/ffmpeg
# or somewhere else in the path!

```

To make it executable ```
chmod +x ffmpeg-install-script
```.

When you run it make sure you run it as sudo. 
When the script is finished without any errors, you can encode your videos with the following command:

```
ffmpeg -i input -acodec amr_nb -ar 8000 -ac 1 -ab 32 -vcodec h263 -s qcif -r 15 out.3gp
```

 where input is the input movie file and out.3gp is the container for the output. Note, that the settings for aspect ratio and audio bit rate and frame rate are best left alone, as chaning them may cause the video to be unplayable on your cellphone (even if it is playable on your computer.)

*****
I will be adding the simple command to do the reverse (i.e. 3gp to avi) a little later I just have to research it a little more.
[COLOR="Red"] I first need to get the other way working 100% of the time, seems svn changes quite often, makes sense. I don't think I will be adding support for this after all since who wants to conver 3gp->avi the quality would suck[/COLOR]

---

### Post by marklid on 2007-03-05
Thanks for this, I have set it up and have started to convert a file...

A couple of things to note before installation :
- you will need to have the subversion package installed (I used apt-get to install it)
- if you copy and paste the script above you will need to manually change the two 3gpp urls as they are truncated in the above code by the forum software. Right-click on the urls and select Properties to see the full path.

Cheers.

---

### Post by jamyskis on 2007-03-06
.

---

### Post by Docter on 2007-05-13
```
Unknown option "--enable-amr_nb".
See ./configure --help for available options.
Makefile:5: config.mak: No such file or directory
/version.sh 
make: /version.sh: Command not found
make: *** No rule to make target `config.mak'. Stop.
```

I have build-essential, subversion, libc6 and libc6dev installed. Any ideas?

Thankfully it's not too difficult to remove the source your script has downloaded and reinstall ffmpeg but I'd really like to get it working.
```

/usr/src/ffmpeg$ ./configure --help
```
gives this:> 
Usage: configure [options]
Options: [defaults in brackets after descriptions]

Standard options:
  --help                   print this message
  --log[=FILE|yes|no]      log tests and output to FILE [config.err]
  --prefix=PREFIX          install in PREFIX [/usr/local]
  --libdir=DIR             install libs in DIR [PREFIX/lib]
  --shlibdir=DIR           install shared libs in DIR [PREFIX/lib]
  --incdir=DIR             install includes in DIR [PREFIX/include/ffmpeg]
  --mandir=DIR             install man page in DIR [PREFIX/man]
  --enable-static          build static libraries [default=yes]
  --disable-static         do not build static libraries [default=no]
  --enable-shared          build shared libraries [default=no]
  --disable-shared         do not build shared libraries [default=yes]
  --enable-gpl             allow use of GPL code, the resulting libav*
                           and ffmpeg will be under GPL [default=no]
  --enable-pp              enable GPLed postprocessing support [default=no]
  --enable-swscaler        software scaler support [default=no]
  --enable-beosthreads     use BeOS threads [default=no]
  --enable-os2threads      use OS/2 threads [default=no]
  --enable-pthreads        use pthreads [default=no]
  --enable-w32threads      use Win32 threads [default=no]
  --enable-x11grab         enable X11 grabbing [default=no]

External library support:
  --enable-sunmlib         use Sun medialib [default=no]
  --enable-dc1394          enable IIDC-1394 grabbing using libdc1394
                           and libraw1394 [default=no]
  --enable-liba52          enable GPLed liba52 support [default=no]
  --enable-liba52bin       open liba52.so.0 at runtime [default=no]
  --enable-avisynth        allow reading AVISynth script files [default=no]
  --enable-libamr-nb       enable libamr-nb floating point audio codec
  --enable-libamr-wb       enable libamr-wb floating point audio codec
  --enable-libdts          enable GPLed libdts support [default=no]
  --enable-libfaac         enable FAAC support via libfaac [default=no]
  --enable-libfaad         enable FAAD support via libfaad [default=no]
  --enable-libfaadbin      build FAAD support with runtime linking [default=no]
  --enable-libgsm          enable GSM support via libgsm [default=no]
  --enable-libmp3lame      enable MP3 encoding via libmp3lame [default=no]
  --enable-libnut          enable NUT (de)muxing via libnut,
                           native demuxer exists [default=no]
  --enable-libogg          enable Ogg muxing via libogg [default=no]
  --enable-libtheora       enable Theora encoding via libtheora [default=no]
  --enable-libvorbis       enable Vorbis en/decoding via libvorbis,
                           native implementations exist [default=no]
  --enable-x264            enable H.264 encoding via x264 [default=no]
  --enable-xvid            enable Xvid encoding via xvidcore,
                           native MPEG-4/Xvid encoder exists [default=no]

Advanced options (experts only):
  --source-path=PATH       path to source code [/usr/src/ffmpeg]
  --cross-prefix=PREFIX    use PREFIX for compilation tools []
  --cross-compile          assume a cross-compiler is used
  --target-os=OS           compiler targets OS [linux]
  --cc=CC                  use C compiler CC [gcc]
  --make=MAKE              use specified make [make]
  --extra-cflags=ECFLAGS   add ECFLAGS to CFLAGS []
  --extra-ldflags=ELDFLAGS add ELDFLAGS to LDFLAGS []
  --extra-libs=ELIBS       add ELIBS []
  --build-suffix=SUFFIX    suffix for application specific build []
  --arch=ARCH              select architecture  [i686]
  --cpu=CPU                selects the minimum cpu required (affects
                           instruction selection, may crash on older CPUs)
  --enable-powerpc-perf    enable performance report on PPC
                           (requires enabling PMC)
  --disable-mmx            disable MMX usage
  --disable-armv5te        disable armv5te usage
  --disable-armv6          disable armv6 usage
  --disable-iwmmxt         disable iwmmxt usage
  --disable-altivec        disable AltiVec usage
  --disable-audio-oss      disable OSS audio support [default=no]
  --disable-audio-beos     disable BeOS audio support [default=no]
  --disable-v4l            disable video4linux grabbing [default=no]
  --disable-v4l2           disable video4linux2 grabbing [default=no]
  --disable-bktr           disable bktr video grabbing [default=no]
  --disable-dv1394         disable DV1394 grabbing [default=no]
  --disable-network        disable network support [default=no]
  --disable-ipv6           disable ipv6 support [default=no]
  --disable-zlib           disable zlib [default=no]
  --disable-vhook          disable video hooking support
  --disable-debug          disable debugging symbols
  --disable-mpegaudio-hp   faster (but less accurate)
                           MPEG audio decoding [default=no]
  --disable-ffmpeg         disable ffmpeg build
  --disable-ffserver       disable ffserver build
  --disable-ffplay         disable ffplay build
  --enable-small           optimize for size instead of speed
  --enable-memalign-hack   emulate memalign, interferes with memory debuggers
  --disable-encoder=NAME   disables encoder NAME
  --enable-encoder=NAME    enables encoder NAME
  --disable-decoder=NAME   disables decoder NAME
  --enable-decoder=NAME    enables decoder NAME
  --disable-encoders       disables all encoders
  --disable-decoders       disables all decoders
  --disable-muxer=NAME     disables muxer NAME
  --enable-muxer=NAME      enables muxer NAME
  --disable-muxers         disables all muxers
  --disable-demuxer=NAME   disables demuxer NAME
  --enable-demuxer=NAME    enables demuxer NAME
  --disable-demuxers       disables all demuxers
  --enable-parser=NAME     enables parser NAME
  --disable-parser=NAME    disables parser NAME
  --disable-parsers        disables all parsers
  --enable-bsf=NAME        enables bitstream filter NAME
  --disable-bsf=NAME       disables bitstream filter NAME
  --disable-bsfs           disables all bitstream filters
  --enable-protocol=NAME   enables protocol NAME
  --disable-protocol=NAME  disables protocol NAME
  --disable-protocols      disables all protocols

Developer options (useful when working on FFmpeg itself):
  --enable-gprof           enable profiling with gprof [no]
  --disable-opts           disable compiler optimizations
  --enable-extra-warnings  enable more compiler warnings
  --disable-strip          disable stripping of executables and shared libraries

NOTE: Object files are built at the place where configure is launched.


Am I missing something here?

---

### Post by dragoncow2 on 2007-05-13
The trick is to get the svn version from March 03, since that is when these directions worked. You could figure out how to get the new one to work, but after 20 minutes of troubleshooting I decided to be lazy and just check out the older version, from the time it worked...and so, do this instead: 

#!/bin/bash

# feel free to change the src directory
cd /usr/src/

#will download the newest svn ffmpeg
svn co -r '{2007-03-03}' svn://svn.mplayerhq.hu/ffmpeg trunk ffmpeg
#Install the required audio codecs for 3gp videos
cd ffmpeg/ffmpeg/trunk/libavcodec
mkdir amr_float
cd amr_float
wget [http://www.3gpp.org/ftp/Specs/archive/26_series/26.104/26104-510.zip](http://www.3gpp.org/ftp/Specs/archive/26_series/26.104/26104-510.zip)
unzip *.zip
unzip *code.zip
cd ..
mkdir amrwb_float
cd amrwb_float
wget [http://www.3gpp.org/ftp/Specs/archive/26_series/26.204/26204-510.zip](http://www.3gpp.org/ftp/Specs/archive/26_series/26.204/26204-510.zip)
unzip *.zip
unzip *code.zip
cd ../..
#configure ffmpeg to use these audio codecs
./configure --enable-amr_nb --enable-amr_wb $@
make

#link the ffmpeg binary to somewhere in PATH so you can run it anywhere
ln -sf /usr/src/ffmpeg/ffmpeg /usr/local/bin/ffmpeg
# or somewhere else in the path!



Hope that helps! I haven't tested it all, but I got ffmpeg to compile with amr* stuff, so it's much better than using current svn :o)

---

### Post by dragoncow2 on 2007-05-13
Ok, I got it working. Get rid of the `ln` on the last line...it's not really needed. Also, I didn't uninstall the original ffmpeg because there's no conflicts with both. Just don't "install" the second one, run it from the folder where it's built, like this:

./ffmpeg -i ~/House.avi  -acodec amr_nb -ar 8000 -ac 1 -ab 32 -vcodec h263 -s qcif -r 15 ~/house.3gp


It's working just fine on my Samsung A950, here's the filetypes before and after:

# House.avi: RIFF (little-endian) data, AVI, 624 x 352, 23.98 fps, video: XviD, audio: MPEG-1 Layer 3 (stereo, 48000 Hz)

# house.3gp: ISO Media, MPEG v4 system, 3GPP


Dont' worry if the audio doesn't play with mplayer, as mplayer doesn't have the proper support built in (at least default from the multiverse), for the audio, it works just fine on the cell phone though. 

Hope this helps,

---

### Post by hexo1125 on 2007-05-13
I also got ```
Unknown option "--enable-amr_nb"
```

./configure outputs
```

install prefix            /usr/local
source path               /tmp/ffmpeg
C compiler                gcc
make                      make
.align is power-of-two    no
ARCH                      x86_32 (generic)
big-endian                no
MMX enabled               yes
CMOV enabled              no
CMOV is fast              no
gprof enabled             no
debug symbols             yes
strip symbols             yes
optimize                  yes
static                    yes
shared                    no
postprocessing support    no
software scaler enabled   no
video hooking             yes
Imlib2 support            no
FreeType support          yes
network support           yes
IPv6 support              yes
threading support         no
SDL support               no
Sun medialib support      no
AVISynth enabled          no
liba52 support            no
liba52 dlopened           no
libamr-nb support         no
libamr-wb support         no
libdts support            no
libfaac enabled           no
libfaad enabled           no
faadbin enabled           no
libgsm enabled            no
libmp3lame enabled        no
libnut enabled            no
libogg enabled            no
libtheora enabled         no
libvorbis enabled         no
x264 enabled              no
XviD enabled              no
zlib enabled              yes
License: LGPL
Creating config.mak and config.h...

```

I seem to be missing a lot of stuff... ???

---

### Post by Docter on 2007-05-13
Marvelous. Your clear instructions and speedy response is most appreciated. I guess I shoulda noticed the date :P

Now I can take a tai chi vid with me when I practice.

I guess if you ever need anyone killed... I'm your guy. Thanks.


(DISCLAIMER: I am not a hitman!)

---

### Post by hexo1125 on 2007-05-13
My last post, I used the latest version (as of that post).

I then tried the March 3rd revision, and get some other error
```
make[1]: *** No rule to make target `amr_float/sp_dec.o', needed by `libavcodec.a'.  Stop.
```

---

### Post by hexo1125 on 2007-05-14
anyways, it was my bad...

copy and paste the code doesn't work because the wget links are truncated...
also make sure the folder directives are right in the script...
cd into the proper directory before executing the configures and makes...
then it should work fine...

Thanks!

---

### Post by gmatt on 2007-05-24
Sorry I haven't updated this in so long guys, I'm glad you all managed to figure out the little annoying things like the truncated URLs and changes in the SVN versions that broke this method. 

I think eventually ffmpeg with come default with the amr audio codecs but until then this is a sure method to get it to work. If anyone has any info on this please message here or me.

---

### Post by vaineh on 2007-05-31
when i get to compile i get:

gcc is unable to create an executable file.

whats gone wrong??

---

### Post by gmatt on 2007-06-01
> **vaineh said:**
> when i get to compile i get:

gcc is unable to create an executable file.

whats gone wrong??

Can you be more specific? What does the error say exactly? Does the rest of the script work up to the "make" line?



I'm not sure what might have gone wrong, but did you run the script as sudo? I can't remember if /usr/ has read/write permisions to regular users.

---

### Post by gigaferz on 2007-08-08
hello, i just tried it, and as usual failed, lol, anyway.. i did the script part,  and after running the script, it told me there is  no make or install,,,

honestly, after al this time..of googling and reading to make things work, i just want to know how to get rid of this... sometimes is exhausting to  get the tyniest things to work,, dont get me wrong,, i really  got many things working but  if i want something and it requires the minimum tweaking, ill pass...

My question is how do i delete all those "inflated files, and where are they....?

i might try next month , but meanwhile where do i find the svn package,?
i didnt get it..... apt get  cannot find it

thanks

---

### Post by jasonwatkins on 2007-09-03
just wanted to jump in and say i followed the instructions and it worked like a dream for me and converted WMV to 3GP perfectly.

Played on my Motorola V3X in surprisingly good quality .. nice one :D

---

### Post by sreenidhy on 2007-09-07
I followed this tutorial...it just worked amazing for me.. :)
I was looking for this since many days...thnx everybody

---

### Post by crazygerad on 2007-09-17
THANK YOU!

I am using the latest Ubuntu Feisty and it works

I used the second code snippet that tells you to download the code versions from March. If you do that and hit make it will give a lot of warnings and pointers. I ignored them. 

The poster who modified the script also said about not using ln, he is wrong it is needed if you want to use it from the command prompt without looking for it. Still if you wish to not bother at least the name of the ffmpeg in the repos just add something like march or 3gp to the name in the ln instruction.

The latest in the repos says it encodes to 3gp but when I tried it, it says streaming error (forgot the exact phrase sorry) and when I used acode it said it didn't knew what am_... was.

The version talked about here worked to transfer an avi to 3gp and an avi to mp4.

Again thank you.

---

### Post by Mateo on 2007-10-02
doesn't work for me apparently.  at least, the sound doesn't work in mplayer.  I haven't gotten my mobile device so i can't test there, yet.

---

### Post by fortran01 on 2007-10-07
I'm on Ubuntu 7.04. Compilation and Conversion works with the revised script of dragoncow2

---

### Post by Matt Yun on 2007-10-07
Here's a related thread:  [3gp conv3rter ]("http://ubuntuforums.org/showthread.php?t=396519")

---

### Post by RooiRampokker on 2007-11-01
Hi all,

Unfortunately my internet connectivity is limited to browser only(no apt-get, svn, etc) due to a Microsoft ISA proxy issue (I'm working of fixing that), which kinda makes most of the techniques described here difficult/impossible to apply. 
I've downloaded and installed all the required packages (mplayer, mencoder, ffmpeg, lame, etc) via [https://launchpad.net/ubuntu/edgy/i386/](https://launchpad.net/ubuntu/edgy/i386/) and got  mplayer to play and encode (to flv) all the required video clips.

All I need to do now is get 3gp to play along.  
[http://www.mplayerhq.hu/design7/news.html](http://www.mplayerhq.hu/design7/news.html) claims build-in AMR support which also renders most of the posts dealing with 3gp obsolete.

My problem is I still cant get mplayer/ffmpeg/mencoder to play or encode 3gp clips. Any help would be greatly appreciated
Does anyone have any advice on how I should go about setting up 3gp support on the newest version of mplayer for Edgy?

---

### Post by Shampyon on 2007-11-03
I've started using [ConvertIt]("http://ubuntuforums.org/showthread.php?t=567016&highlight=convertit") for my video encoding needs.  If you've got all the right codecs, it's as simple to use as SUPER, which was the converter I used to use in XP. Nice clean GUI, all the options you could need to convert any type of video, audio or image into any other type of video, audio or image. 

I did find that the default ANY to 3GP conversion option in CinvertIt didn't work on my Motorola V3i, so I went into the BUILD FUNCTIONS tab and added a new option that uses this command:
ffmpeg -i INPUT -s qcif -vcodec mpeg4 -acodec aac -ac 2 -ar 16000 -r 25 -ab 32 -y OUTPUT

Hope that helps :)

---

### Post by charding on 2008-01-19
Hey, how did you know what files were amr_float and amrwv_float? The files names (like 26_series/26.104/26104-510.zip) don't help when trying to find out the most recent version of these source libraries. If you can tell me how you figured it out it might help me so I don't have to download every file and seeing if it's the correct amr_float or amrwb_float libs.

I couldn't find anything on the 3gpp website to tell me their filename naming convention.

I found this page which makes the process a lot easier.

[http://www.penguin.cz/~utx/amr](http://www.penguin.cz/~utx/amr)

Download both the amrnb and amrwb files, run configure, make and make install



> **gmatt said:**
> This howto guides you through the process of setting up ffmpeg on your computer so that you can convert your avi and other movies to mobile (psp, cellphone) 3gp format. It is short, which I hope that you will appreciate. Most of the work will be done by a script.

[COLOR="SeaGreen"]You need to install SVN for this to work. To get it ```
 sudo apt-get install svn
```[/COLOR]

[COLOR="Red"]
Updated May 24 2007 6pm:
- After a little bit of testing I have found that the newer versions from SVN have broken the libraries needed by the C code to compile, it is best just to use the SVN version from the time that this worked. 
- There may have been a recent update to ffmpeg that removes the need for this howto that I am not aware of. If there is please tell me or post here!
- Thanks to dragoncow2 for showing how to download previous versions of SVN, so I don't have to look it up. The script here is updated with his change. 
- Everything should work perfect now! Have fun ;)

Updated May 24 2007 12am:
- I have fixed the links in the script so that they do not get truncated, I've noticed that has bugged people
- I am testing the svn newer versions and trying to see why they do not work with the old codec[/COLOR]

First, uinstall any ffmpeg you might have currently installed. The usual command that will do this is
 ```
sudo apt-get remove ffmpeg
```
Next, save the following into a script and make it executable and run it:
```

#!/bin/bash

# feel free to change the src directory
cd /usr/src/

#will download the newest svn ffmpeg
svn co -r '{2007-03-03}' svn://svn.mplayerhq.hu/ffmpeg trunk ffmpeg
#Install the required audio codecs for 3gp videos
cd ffmpeg/libavcodec
mkdir amr_float
cd amr_float
wget http://www.3gpp.org/ftp/Specs/archive/26_series/26.104/26104-510.zip
unzip *.zip
unzip *code.zip
cd ..
mkdir amrwb_float
cd amrwb_float
wget http://www.3gpp.org/ftp/Specs/archive/26_series/26.204/26204-510.zip
unzip *.zip
unzip *code.zip
cd ../..
#configure ffmpeg to use these audio codecs
./configure --enable-amr_nb --enable-amr_wb $@
make

#link the ffmpeg binary to somewhere in PATH so you can run it anywhere
ln -sf /usr/src/ffmpeg/ffmpeg /usr/local/bin/ffmpeg
# or somewhere else in the path!

```

To make it executable ```
chmod +x ffmpeg-install-script
```.

When you run it make sure you run it as sudo. 
When the script is finished without any errors, you can encode your videos with the following command:

```
ffmpeg -i input -acodec amr_nb -ar 8000 -ac 1 -ab 32 -vcodec h263 -s qcif -r 15 out.3gp
```

 where input is the input movie file and out.3gp is the container for the output. Note, that the settings for aspect ratio and audio bit rate and frame rate are best left alone, as chaning them may cause the video to be unplayable on your cellphone (even if it is playable on your computer.)

*****
I will be adding the simple command to do the reverse (i.e. 3gp to avi) a little later I just have to research it a little more.
[COLOR="Red"] I first need to get the other way working 100% of the time, seems svn changes quite often, makes sense. I don't think I will be adding support for this after all since who wants to conver 3gp->avi the quality would suck[/COLOR]

---

### Post by Ketahazure on 2008-01-19
I hope that I am not posting in the wrong forum if so could I possibly get some direction to the right one. I  was trying to encode a video file using ffmpeg but unfortunatly im not getting any sound. Im using flac as my audio codec and upon playback in i get no audio. Is there a better audio codec that i sould use? Also "-acodec copy" option isnt working either.

---

### Post by ubuntu-freak on 2008-02-06
> **Ketahazure said:**
> I hope that I am not posting in the wrong forum if so could I possibly get some direction to the right one. I  was trying to encode a video file using ffmpeg but unfortunatly im not getting any sound. Im using flac as my audio codec and upon playback in i get no audio. Is there a better audio codec that i sould use? Also "-acodec copy" option isnt working either.

 
What type of video? If you want to use aac audio instead you need faac. Part 4 of [how-to](http://ubuntuforums.org/showthread.php?t=661833) deals with making vids. 
 
Nathan

---

### Post by BilliShere on 2008-07-23
Just to let everyone know.. I have tried everything...scripts, nautilus actions, winff, mobile media converter, and 3gp amr enabled self compiled ffmpeg. While some of them might work they do not work completely on my cell phone. Like moblie media converter, the 3gp results usually cannot be set to custom resolutions like 320*240 and usually the video quality is garbage..The best solution however that worked and worked 100% and all the time for me is running Freez 3gp video converter under crossover pro 7 or wine. It is flawless, easy to use, and all the videos now in 3gp are in good quality and work on my cell phone (samsung d900i) no sweat.

---

### Post by ggankhuy on 2009-06-08
> **charding said:**
> Hey, how did you know what files were amr_float and amrwv_float? The files names (like 26_series/26.104/26104-510.zip) don't help when trying to find out the most recent version of these source libraries. If you can tell me how you figured it out it might help me so I don't have to download every file and seeing if it's the correct amr_float or amrwb_float libs.

I couldn't find anything on the 3gpp website to tell me their filename naming convention.

I found this page which makes the process a lot easier.

[http://www.penguin.cz/~utx/amr](http://www.penguin.cz/~utx/amr)

Download both the amrnb and amrwb files, run configure, make and make install


THIS method is not working. I tried doing on ubuntu9.04 but at the end of checkout it says 

Checked out revision 8195.
svn: 'trunk' does not appear to be a URL <- i dont know if this is a error message and have no idea of the chkout is successfull and fully or not. 

down to the end make build fails with 

make[1]: *** [imgresample.o] Error 1
make[1]: Leaving directory `/usr/src/ffmpeg/libavcodec'
make: *** [lib] Error 2.

Even if I just do ./configure without the switch it is same build error message.

any help would be appreciated.

Oh yeah, I also tried the latest ffmpeg source code and it builds fine without --enable-amr_nb --enable-amr_wb switch but once those switch is turned on, the switch is not recognized-> dug into configure file and found they are changed to 

--enable-libamr-nb --enable-libamr-wb 
also had supply --enable-nonfree switch. 

and once again i do run configure i am stuck following message: 

ERROR: libamrnb not found
any help would be appreciated.

---

### Post by siongz on 2009-06-25
Hi guys, i managed to get it installed. but i cant seem to convert my files to 3GP format. 
some other fuctions work still, like i can convert from .flv to .mpeg but not to .3GP.

please help. :(

when i clicked "Convert", it immediately shows "Conversion Complete. What to do?" 
but there is no file.

---

### Post by RomanIvanov on 2009-08-02
I use WinFF from Ubuntu repository.

```
sudo apt-get install winff
```

Run winff, select file to convert and select:
Convert to = Mobile Phones
Device Preset = 3g2

works like a charm :)

Need more ? look as WinFF forum for more presets [http://www.biggmatt.com/forums/index.php?topic=358.0](http://www.biggmatt.com/forums/index.php?topic=358.0)

---

### Post by andrew.46 on 2009-08-03
Hi gmatt,

Looks like the svn FFmpeg no longer compiles against these amr libraries and now the opencore-amr libraries are required. These libraries can be found [here]("http://sourceforge.net/projects/opencore-amr/").

All the best,

Andrew.

---

