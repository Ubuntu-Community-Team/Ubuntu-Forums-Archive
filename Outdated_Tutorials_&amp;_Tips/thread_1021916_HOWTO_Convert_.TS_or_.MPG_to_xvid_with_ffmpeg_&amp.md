---
title: "HOWTO: Convert .TS or .MPG to xvid with ffmpeg &amp; winff in ubuntu 8.10"
date: 2008-12-26
forum: Outdated Tutorials &amp; Tips
---

### Post by art2003 on 2008-12-26
In short we need a customize ffmpeg to do the conversions and winff to provide a friendly GUI and batch processing of files. This is very usefull if for example you have lots of Dreambox recordings in .TS format and want to convert them to xvid typically shrinking the file size by 66%. I have borrowed from other tutorials plus my own experience 

This tutorial will explain how to compile our custom ffmpeg with xvid support and how to install AND CONFIGURE winff to work with our custom ffmpeg.

*Special thanks to FakeOutdoorsman* for his ffmpeg tutorial and helpfull posts.


**1. Make sure the Ubuntu universe and multiverse repositories are enabled.** For help doing this, refer to[ Adding the Universe and Multiverse Repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096") on the Ubuntu Wiki.


**2. Uninstall x264, libx264-dev, and ffmpeg** if they are already installed. Open a terminal and run the following:
```
sudo apt-get purge ffmpeg x264 libx264-dev
sudo apt-get update
```

**3. Install the necessary packages:** 
```
sudo apt-get install build-essential subversion git-core checkinstall yasm texi2html libfaad-dev libfaac-dev libmp3lame-dev libtheora-dev libxvidcore4-dev libsdl1.2-dev libvorbis-dev
```

**4. **(*Optional*) **Install X264**
```
cd ~/
git clone git://git.videolan.org/x264.git
cd x264
./configure --enable-shared
make
sudo checkinstall --fstrans=no --install=yes --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`-0.0ubuntu1"
sudo ldconfig
```

**5. Install ffmpeg**

```
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
cd ffmpeg
./configure --prefix=/usr --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
make
sudo checkinstall --fstrans=no --install=yes --pkgname=ffmpeg --pkgversion "3:0.svn`date +%Y%m%d`-12ubuntu3"
```

**6. Lock** your **ffmpeg **package to prevent Ubuntu from automatically updating and replacing your custom software with versions from the repository.

If you use apt-get or Synaptic:
System -> Administration -> Synaptic Package Manager -> Choose the ffmpeg package -> Package -> Lock Version
(and do the same with x264 if you followed optional step 4)
[B]
7. Copy default presets to ~/.ffmpeg[/B] (This step may not be necessary as I believe winff comes with its own presets) 
```
mkdir ~/.ffmpeg
cp ~/ffmpeg/ffpresets/* ~/.ffmpeg 

```

At this point we should have a funcional (yet intimidating) command line ffmpeg. To verify this open a Terminal and type
```
ffmpeg -formats |grep xvid
```
The last line should show something like:
EV    libxvid         libxvidcore MPEG-4 part 2

Now comes winff -> The GUI 
[WinFF]("http://winff.org/html/") is a GUI for the command line video converter, FFMPEG. It will convert most any video file that FFmpeg will convert. WinFF does multiple files in multiple formats at one time.


**8. Add the official winff repository** (for Ubuntu 8.10 intrepid only!) and corresponding key

```
wget --quiet --output-document=- "http://winff.org/ubuntu/AAFE086A.gpg" | sudo apt-key add -

```
```
echo "deb http://winff.org/ubuntu intrepid universe" | sudo tee /etc/apt/sources.list.d/winff.list

```

**9. Install winff** and supporting packages
```
sudo apt-get update && sudo apt-get install winff libavcodec-unstripped-51

```

**10. Open winff**, click on **Edit**, **Presets**, **Select AVI**,** XVid in AVI 16:9 anamorphic** and make sure the line is like this:
-r 29.97 -croptop 58 -cropbottom 62 -vcodec libxvid -vtag XVID -s 640x272 -aspect 2.35 -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2

Note: This last step may not be necessary anymore but I was getting a fatal error with +4mv-trell so I replaced with +4mv and now is working (but I have winff 0.43, newer versions may come with correct presets for xvid)

I hope this tutorial is usefull to somebody, I certainly wished there was one around yesterday!

---

### Post by aashay on 2008-12-30
Bumping this well written Howto. Thanks.

---

### Post by v.mazzotta on 2009-01-14
Very very very good.

Work fine.

Be sure after installation to verify string in preset command line. Remove this string "+trell -aic 2 " or copy exactly string in this article:
-r 29.97 -croptop 58 -cropbottom 62 -vcodec libxvid -vtag XVID -s 640x272 -aspect 2.35 -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2
for preset command line and work fine.

Good work man!

Kind Regargs.:-({|=:lolflag:\\:D/

---

### Post by FakeOutdoorsman on 2009-01-14
> **v.mazzotta said:**
> Very very very good.

Work fine.

Be sure after installation to verify string in preset command line. Remove this string "+trell -aic 2 " or copy exactly string in this article:
-r 29.97 -croptop 58 -cropbottom 62 -vcodec libxvid -vtag XVID -s 640x272 -aspect 2.35 -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2
for preset command line and work fine.

Good work man!

Kind Regargs.:-({|=:lolflag:\\:D/
This should preserve aic and trellis:
```
-r 29.97 -croptop 58 -cropbottom 62 -vcodec libxvid -vtag XVID -s 640x272 -aspect 2.35 -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv+aic -trellis 1 -cmp 2 -subcmp 2 -g 300 -acodec libmp3lame -ar 48000 -ab 128k -ac 2
```

---

### Post by blazini on 2009-01-20
When I get to step 5 "5. Install ffmpeg", I run the command:
```
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
```
.......and nothing happens. command line in the terminal just stays blank

---

### Post by Sharepointengine on 2009-01-20
I really don't know  
HOWTO: Convert .TS or .MPG to xvid with ffmpeg & winff in ubuntu 8.10
Great Advice **art2003**
;)

---

