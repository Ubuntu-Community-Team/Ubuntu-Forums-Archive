---
title: "HOWTO: Download YouTube Stereo MP3s"
date: 2006-12-30
forum: Outdated Tutorials &amp; Tips
---

### Post by SuperMike on 2006-12-30
**I'm editing this on Jan 3 2009. YouTube basically broke the API discussed here. Thread can be closed.**

YouTube provides videos for practically every band you've ever heard of, even obscure ones or one-hit-wonders on some TV show you saw. The video quality is moderate but effective, and works on most browsers without having to do anything special. In all your excitement of finding that favorite song of yours, you might not have noticed that it was in mono. You might not have also known that you can extract the sound from it. Unlike P2P networks like Limewire, these YouTube videos are often complete, often not fake, and 99.5% of them download properly on to your computer for playback in your browser.

[SIZE="3"]Well I'm about to change your perspective on YouTube. You are in for a treat.[/SIZE]

The following script makes an "mp3" folder in your home directory, downloads a YouTube video to it, extracts out a mono MP3 file, then feeds it through a sophisticated simulated stereo filter to create a fairly high quality stereo MP3 file.

The simulated stereo filter puts an 8 microsecond delay on the right channel and then differs the EQ slightly in each channel. If the delay is increased, the first thing that happens is distortion. Then, it becomes a hollow or tinny sound, and then becomes just pure echo. But with an 8 microsecond delay, plus some EQ modification, it creates a cool stereo effect and no distortion or echo is present.

I also noticed that some music videos are made up, such as with Asian Anime or kids goofing off in front of it, but the soundtrack is the real thing in some cases. By throwing away the video part, the MP3 sound, especially when converted to fake stereo, sounds great.

**[SIZE="4"]REQUIREMENTS[/SIZE]**

You first need to do this:

```
$ sudo su
# apt-get update
# apt-get install xulrunner
# apt-get install ffmpeg
# apt-get install lame
# apt-get install mpg123
# apt-get ecasound
# exit
```

Now surf with your browser to YouTube and try to play a video. If it asks to install
Flash, do so because I think it updates your video codecs on your PC.

Now surf with your browser to find an MPG file on the Internet and download it. Now
try to open it. Ubuntu will ask you to choose some codecs to download and install.
Do so.

**[SIZE="4"]SCRIPT[/SIZE]**

The following script can be placed as "ytr" in your /usr/bin folder and then made into an executable file with "sudo chmod a+x /usr/bin/ytr". In my case, I made a launcher for it, created my own YouTube icon, and then set the launcher to require a Terminal Window.

```
#!/bin/bash
#
# Bash script to convert YouTube Video to Simulated Stereo MP3
#
# Public Domain
# Contributors: Supermike, Crouse, Kai Vehmanen, Chriss.Hi
#
bu="http://rd.cache.l.google.com/get_video?video_id="
mkdir -p ~/mp3;cd ~/mp3
read -p "YouTube url? " ur
read -p "Name? " nv
echo;echo;
uf=`echo $ur | cut -d = -f 2`
wget "${bu}${uf}" -O /tmp/y.flv
ffmpeg -i /tmp/y.flv -f mp3 -vn -acodec copy "/tmp/${nv}.mp3"
ecasound -i "/tmp/${nv}.mp3" -etf:8 -o "${nv}.mp3"
echo;echo;
rm -f "/tmp/${nv}.mp3"
echo "File is saved in your home directory in the 'mp3' folder."
read
```

**[SIZE="4"]IF YOU WANT A GUI VERSION[/SIZE]**
I also whipped up a GUI version at:

[http://code.google.com/p/yt2mp3/](http://code.google.com/p/yt2mp3/)

**[SIZE="4"]UNINSTALLATION:[/SIZE]**
```
$ sudo apt-get --purge remove ecasound
$ sudo rm -f /usr/bin/ytr
```

Anything else that is removed could potentially disturb your ability to use MPEG audio and video on your PC, but this is what it would look like....

```
$ sudo apt-get --purge remove ffmpeg
```


[SIZE="4"]**SOURCES: **[/SIZE]
[**[COLOR="Red"]Crouse, admin from BashScripts.org[/COLOR]**]("http://bashscripts.org/viewtopic.php?t=210")
[**[COLOR="Red"]Kai Vehmanen, one of the developers of the Ecasound tool[/COLOR]**]("http://eca.cx/ecasound/Documentation/ecasound_manpage.html")
[**[COLOR="Red"]Chriss.Hi, who showed me an interesting Google hack[/COLOR]**]("http://ubuntuforums.org/member.php?u=239974")

[SIZE="4"]**TESTED:**[/SIZE]
Ubuntu Breezy Badger
Ubuntu Feisty Fawn

---

### Post by OrganicPanda on 2007-01-14
WOW this is incredible, very good work. This is seriously very cool

---

### Post by SuperMike on 2007-01-14
Glad you like it. My Sansa MP3 player is filled to the hilt with this stuff.

Right now I've got another project I'm working on -- a large web-based CRM project -- but I do plan to knock out some time to use this technique...

[http://www.ubuntuforums.org/showthread.php?t=333862](http://www.ubuntuforums.org/showthread.php?t=333862)

...to build a GUI to do what this script does. Perhaps someone could knock it out faster in Python and PyGTK if they are eager.

---

### Post by SuperMike on 2007-01-28
[SIZE="4"]**GUI Available Now**[/SIZE]

Get it here:

[http://code.google.com/p/yt2mp3/](http://code.google.com/p/yt2mp3/)

I wrote it in XUL. See requirements on the project page.

[IMG]http://yt2mp3.googlecode.com/files/Screenshot.png[/IMG]

---

### Post by tonofclay on 2007-01-28
Pretty cool, I'd love to have it working but right now when I do 

$ xulrunner yt2mp3/yt2mp3.xulrun

I get the error message "Gecko MinVersion requirement not met." I did some googling and I think it has something to do with applications.ini but I haven't really been able to figure out exactly what to do...any ideas?

---

### Post by SuperMike on 2007-01-28
Upgrade your xulrunner with the latest from Mozilla.com?

---

### Post by tonofclay on 2007-01-28
I'm running 1.8.0.5-4.2, thats the latest as far as I know.

---

### Post by tonofclay on 2007-01-28
Hmm well I didn't do anything at all and it seems to be working now, so I dunno what the problem was before :)

Time to try it out now!


OK just got a song! This is great, thanks for sharing!

---

### Post by SuperMike on 2007-01-28
Hmm. That's strange. Let me know if the problem comes back. Perhaps it has to do with Firefox being open and that Gecko engine in RAM, or perhaps not. Another possibility is that xulrunner might be running in memory from a hung job or something, and a 'sudo killall xulrunner' a couple times might kill it.

---

### Post by SuperMike on 2007-01-28
Perhaps it was a typo. For instance, try this:

$ xulrunner typocity

It generates the same error that you see. This can possibly explain why the intermittent results. I'll admit that typing yt2mp3 is not the easiest thing in the world -- I was mistyping that a lot when working with the project. Note I also provide a binary you can download instead of the source. It was compiled with the 'makeself' tool, which is pretty darn cool.

---

### Post by Tom B on 2007-02-05
Really nice script. You might want to include a note somewhere that if there is a "/" in the name of the mp3, it won't work (I think). I tried save an mp3 and it downloaded fine but then couldn't open the file to encode it. I'm pretty sure it was because of the / because I tried the same video again with a different name and it worked fine. Thanks for making this; it's incredible.

---

### Post by SuperMike on 2007-02-06
Glad you liked it. I guess that's why they call me "Super".

Yeah, my daughter gets a kick out of it too. She uses the XUL version now. I'm taking suggestions for updating it like what you mention here if you go to the website for it, or here is fine too, I guess.

I think what I should do is prevent certain keystrokes on the field in the XUL application. Did you run this by script or by XUL application? If you haven't tried the XUL app, it's cool.

---

### Post by tonofclay on 2007-02-06
Hehe OK I'm back...haven't used this in awhile but I went to use it today and got this error:

XML Parsing Error: undefined entity
Location: chrome://mozapps/content/profile/profileSelection.xul
Line Number 53, Column 1:<dialog

I haven't done anything explicitly to mess with this program but perhaps something I did inadvertently messed it up.
Any suggestions?

---

### Post by SuperMike on 2007-02-07
Hmmm. That's not even my chrome. That's a chrome for something else and looks like a profile selection for the browser.

Did you download and install xulrunner from Mozilla? The XUL app I wrote runs through that.

If you have xulrunner installed on the system and in the system path ($PATH) properly, then the thing should load properly. I also provide two versions. One is the XUL app and the other is a binary. Both, however, assume you have xulrunner installed on Ubuntu and in the system path.

---

### Post by pencilpoint on 2007-02-13
I love this!


I'm going to learn XUL myself :)

---

### Post by SuperMike on 2007-02-13
Good for you. XUL isn't bad at all. It's like what HTML wishes it could be when on steroids. It has clear logic. Javascript, also, is a rockingly cool language too -- nice and simple, lots of people know it, and so on. It's the bad implementation of DHTML, and the browser differences, that has drug Javascript into the muck and made it look bad. Plus, when Javascript is enabled to go outside the sandbox in certain conditions, it's a wonderful little language.

In fact, I'm looking at ngs-js right now and I'm amazed at what it can do.

---

### Post by Athanasius on 2007-05-12
Ooh, just what I was looking for and it works in Kubuntu too

---

### Post by kaede on 2007-05-14
is the audio quality really good?

---

### Post by SuperMike on 2007-05-15
Good enough. My daughter and I listen to it on our MP3 players and in our car stereos. We're pleased with it. See for yourself.

---

### Post by Polygon on 2007-05-15
hmm, i tried it and the program works except when it "finishes" it doesnt save the mp3 file....

here is the console output:

> mark@ubuntu:~$ ./yt2mp3 
bash: ./yt2mp3: No such file or directory
mark@ubuntu:~$ cd Desktop
mark@ubuntu:~/Desktop$ clear

mark@ubuntu:~/Desktop$ ./yt2mp3 
Verifying archive integrity... All good.
Uncompressing .......................
--18:00:14--  [http://youtube.com/watch?v=h7RcqRmBlIQ](http://youtube.com/watch?v=h7RcqRmBlIQ)
           => `/tmp/y1'
Resolving youtube.com... 208.65.153.253, 208.65.153.251
Connecting to youtube.com|208.65.153.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 94,586 (92K) [text/html]

100%[====================================>] 94,586       190.01K/s             

18:00:15 (189.68 KB/s) - `/tmp/y1' saved [94586/94586]

--18:00:15--  [http://youtube.com/get_video.php?video_id=h7RcqRmBlIQ&l=257&t=OEgsToPDskK16UdAHj5ijXZYEUiodv8d&soff=1&sk=h9nOpYHt-zXs8q97ICCk4QC&sw=0.1](http://youtube.com/get_video.php?video_id=h7RcqRmBlIQ&l=257&t=OEgsToPDskK16UdAHj5ijXZYEUiodv8d&soff=1&sk=h9nOpYHt-zXs8q97ICCk4QC&sw=0.1)
           => `/tmp/y.flv'
Resolving youtube.com... 208.65.153.251, 208.65.153.253
Connecting to youtube.com|208.65.153.251|:80... connected.
HTTP request sent, awaiting response... 303 See Other
Location: [http://ash-v13.ash.youtube.com/get_video?video_id=h7RcqRmBlIQ](http://ash-v13.ash.youtube.com/get_video?video_id=h7RcqRmBlIQ) [following]
--18:00:15--  [http://ash-v13.ash.youtube.com/get_video?video_id=h7RcqRmBlIQ](http://ash-v13.ash.youtube.com/get_video?video_id=h7RcqRmBlIQ)
           => `/tmp/y.flv'
Resolving ash-v13.ash.youtube.com... 64.15.118.82
Connecting to ash-v13.ash.youtube.com|64.15.118.82|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,484,993 (10.0M) [video/flv]

100%[====================================>] 10,484,993    56.80K/s    ETA 00:00

18:03:06 (60.11 KB/s) - `/tmp/y.flv' saved [10484993/10484993]

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)

Seems that stream 1 comes from film source: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, flv, from '/tmp/y.flv':
  Duration: 00:04:16.3, bitrate: N/A
  Stream #0.0: Audio: mp3, 22050 Hz, mono
  Stream #0.1: Video: flv, yuv420p, 320x240, 25.00 fps(r)
Output #0, mp3, to '/tmp/7-11.mp3':
  Stream #0.0: Audio: 0x0000, 22050 Hz, mono
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    1993kB time=256.4 bitrate=  63.7kbits/s    
video:0kB audio:1993kB global headers:0kB muxing overhead 0.000000%




The GUI says that it finished, but i still dont see the mp3 file...

---

### Post by Neilguy on 2007-05-15
I too have the same problem. The GUI says that it finished, but i still dont see the mp3 file...

---

### Post by Skylara on 2007-05-16
> **Neilguy said:**
> I too have the same problem. The GUI says that it finished, but i still dont see the mp3 file...

Same for me as well.  Seems to run beautifully, but then no MP3.  Here's my code:

```
--17:21:02--  http://www.youtube.com/watch?v=v9C831c5WVQ
           => `/tmp/y1'
Resolving www.youtube.com... 208.65.153.251, 208.65.153.253
Connecting to www.youtube.com|208.65.153.251|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 90,118 (88K) [text/html]

100%[====================================>] 90,118       208.22K/s             

17:21:03 (207.88 KB/s) - `/tmp/y1' saved [90118/90118]

--17:21:03--  http://youtube.com/get_video.php?video_id=v9C831c5WVQ&l=247&t=OEgsToPDskIjM8ldNUw7bITIwzQvMSdE&soff=1&sk=B3NjhjelcIKQD1ZQFFlJGAC
           => `/tmp/y.flv'
Resolving youtube.com... 208.65.153.253, 208.65.153.251
Connecting to youtube.com|208.65.153.253|:80... connected.
HTTP request sent, awaiting response... 303 See Other
Location: http://sjl-v53.sjl.youtube.com/get_video?video_id=v9C831c5WVQ [following]
--17:21:03--  http://sjl-v53.sjl.youtube.com/get_video?video_id=v9C831c5WVQ
           => `/tmp/y.flv'
Resolving sjl-v53.sjl.youtube.com... 208.65.153.90
Connecting to sjl-v53.sjl.youtube.com|208.65.153.90|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10,204,103 (9.7M) [video/flv]

100%[====================================>] 10,204,103    79.82K/s    ETA 00:00

17:24:10 (53.34 KB/s) - `/tmp/y.flv' saved [10204103/10204103]

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)

Seems that stream 1 comes from film source: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, flv, from '/tmp/y.flv':
  Duration: 00:04:07.7, bitrate: N/A
  Stream #0.0: Audio: mp3, 22050 Hz, mono
  Stream #0.1: Video: flv, yuv420p, 320x239, 25.00 fps(r)
Output #0, mp3, to '/tmp/oomph-gottisteinPpopstar.mp3':
  Stream #0.0: Audio: 0x0000, 22050 Hz, mono
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=    1985kB time=247.8 bitrate=  65.6kbits/s    
video:0kB audio:1985kB global headers:0kB muxing overhead 0.000000%

kitten@green-desktop:~$ 
```

Thanks so much!

Edit: Also, I did a full HD search for the saved mp3 file, in case it just didn't resave it in the MP3 folder after having it in the tmp folder and my search turned up nothing.

---

### Post by boneyjellyfish on 2007-05-16
Same problem here, too. It makes the mp3 directory, but no mp3!

---

### Post by boneyjellyfish on 2007-06-09
Bumping to say that I fixed all of my ecasound problems by compiling v2.4.5 from source.

---

### Post by SuperMike on 2007-06-19
Strange. It worked for me. The files are dropped in $HOME/mp3. However, I wrote and tested the thing on Breezy Badger -- haven't had the time to upgrade the home PC because of how busy I am.

Make certain not to run the thing under root or it will end up in /root/mp3.

---

### Post by SuperMike on 2007-06-26
On a fresh install of Feisty Fawn, I had to do things a little differently:

apt-get install xulrunner
apt-get install ffmpeg*
apt-get install ecasound*
apt-get install mpg123*
apt-get install lame*
# to tell you the truth, I think I only installed with asterisk (*) on ecasound, but don't fully recall at this point

...and then downloaded:

[http://code.google.com/p/yt2mp3/](http://code.google.com/p/yt2mp3/)

---

### Post by rlorenzo on 2007-06-29
> **SuperMike said:**
> On a fresh install of Feisty Fawn, I had to do things a little differently:

apt-get install xulrunner
apt-get install ffmpeg*
apt-get install ecasound*
apt-get install mpg123*
apt-get install lame*
# to tell you the truth, I think I only installed with asterisk (*) on ecasound, but don't fully recall at this point

...and then downloaded:

[http://code.google.com/p/yt2mp3/](http://code.google.com/p/yt2mp3/)

Hello,

Just installed Feisty Fawn on my MacBook Pro using Parallels and followed your instructions. I can get the program to run and downloaded and converted a YouTube into a mp3, but the sound is horrid.

Link to video: [http://www.youtube.com/watch?v=7PoJv4N1Too](http://www.youtube.com/watch?v=7PoJv4N1Too) (Great band I recently heard)
Link to produced mp3: [http://senduit.com/8f2b4e](http://senduit.com/8f2b4e) (link expires in a week)

The horrible sound is an ever present static noise.

---

### Post by SuperMike on 2007-06-29
Ah, that's either something up with the Macbook, ALSA driver, or the fact that it's running through a VM. The static is probably time-slicing in the sound driver. My daughter and our friends don't have this problem on our systems or in our MP3 players.

What happens if you run this on a system that's not using Linux in a VM?

What happens if you turn off the sound on your Mac OS speaker but leave it on inside Feisty?

What happens if you turn off the sound recorder feature in your Mac OS and inside Feisty so that it can rule that out as being a factor?

---

### Post by zweiundzwei on 2007-08-26
This used to work for me, but now I keep getting errors.

```
--13:26:29--  http://youtube.com/watch?v=5BgAdfe4GFc
           => `/tmp/y1'
Resolving youtube.com... 208.65.153.251
Connecting to youtube.com|208.65.153.251|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 129,676 (127K) [text/html]

100%[====================================>] 129,676       53.02K/s             

13:26:32 (52.93 KB/s) - `/tmp/y1' saved [129676/129676]

--13:26:32--  http://youtube.com/get_video.php?v=1';
           => `/tmp/y.flv'
Resolving youtube.com... 208.65.153.251
Connecting to youtube.com|208.65.153.251|:80... connected.[B]
HTTP request sent, awaiting response... 404 Not Found
13:26:32 ERROR 404: Not Found.[/B]

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 21 2007 14:14:05, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
/tmp/y.flv: Unknown format
********************************************************************************
*        ecasound v2.4.4 (C) 1997-2005 Kai Vehmanen and others    
********************************************************************************
- [ Session created ] ----------------------------------------------------------
- [ Chainsetup created (cmdline) ] ---------------------------------------------
- [ Connecting chainsetup ] ----------------------------------------------------
(eca-chainsetup) 'nonrt' buffering mode selected.
(audioio-mp3) Unable to open file /tmp/guitar_hero.mp3.
(eca-chainsetup) Audio object "/tmp/guitar_hero.mp3", mode 
... "read".
(audio-io) Format: s16_le, channels 2, srate 44100, interleaved.
(eca-chainsetup) Audio object "guitar_hero.mp3", mode "write".
(audio-io) Format: s16_le, channels 2, srate 44100, interleaved.
- [ Chainsetup connected ] -----------------------------------------------------
(eca-control-objects) Connected chainsetup: "command-line-setup".
- [ Controller/Starting batch processing ] -------------------------------------
- [ Engine init - Driver start ] -----------------------------------------------
/usr/bin/ytr: line 12: 19493 Segmentation fault      (core dumped) ecasound -i "/tmp/${nv}.mp3" -etf:8 -o "${nv}.mp3"


File is saved in your home directory in the 'mp3' folder. Press Enter to exit.
```

---

### Post by Tom B on 2007-08-27
This also used to work for me, but on another computer. Now I get these errors. The GUI says it's done, but it doesn't actually save it.
```

Verifying archive integrity... All good.
Uncompressing .......................
--11:58:18--  http://www.youtube.com/watch?v=P842Tmi6lrc
           => `/tmp/y1'
Resolving www.youtube.com... 208.65.153.251, 208.65.153.253, 208.65.153.238
Connecting to www.youtube.com|208.65.153.251|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 157,030 (153K) [text/html]

100%[====================================>] 157,030      117.46K/s             

11:58:20 (117.06 KB/s) - `/tmp/y1' saved [157030/157030]

--11:58:20--  http://youtube.com/get_video.php?v=1';
           => `/tmp/y.flv'
Resolving youtube.com... 208.65.153.253, 208.65.153.238, 208.65.153.251
Connecting to youtube.com|208.65.153.253|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
11:58:20 ERROR 404: Not Found.

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 21 2007 14:14:05, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
/tmp/y.flv: Unknown format


```

---

### Post by Yes on 2007-09-05
Unfortunately, neither of the programs work, the GUI or the text-based program.  When I run the GUI, I get the same output as Tom B, and when I run the text-based program, it says that it saved correctly, but there's no file in the mp3 directory it created.

---

### Post by SuperMike on 2007-09-05
Yeah, but you and I are close. You see, on Aug 20, 2007, Google changed their scripts and I must adjust both the Bash script and the GUI so that they use the new method to capture the FLV file. I have another request in the forums here to see if anyone can assist because I think I can get it, and I know some websites can snag the FLV, but I haven't had the time to adjust my script. I was hoping to leverage some Bash script help from someone who's already figured this out for the new technique.

---

### Post by embeemb on 2007-09-06
I also encounter errors when using both the terminal and the GUI. It says it's done and saved but the mp3 directory is still empty.

> Verifying archive integrity... All good.
Uncompressing .......................
--14:22:34--  [http://youtube.com/watch?v=mcDAWie5LSI&v2](http://youtube.com/watch?v=mcDAWie5LSI&v2)
           => `/tmp/y1'
Resolving youtube.com... 208.65.153.253, 208.65.153.238, 208.65.153.251
Connecting to youtube.com|208.65.153.253|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100,196 (98K) [text/html]

100%[==================================================================>] 100,196       28.54K/s    ETA 00:00

14:22:39 (28.48 KB/s) - `/tmp/y1' saved [100196/100196]

--14:22:39--  [http://youtube.com/get_video.php?v=1';](http://youtube.com/get_video.php?v=1';)
           => `/tmp/y.flv'
Resolving youtube.com... 208.65.153.251, 208.65.153.253, 208.65.153.238
Connecting to youtube.com|208.65.153.251|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
14:22:39 ERROR 404: Not Found.

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)
/tmp/y.flv: Unknown format
/tmp/selfgz322837101/chrome/content/yt2mp3/convert.sh: line 4: 32401 Segmentation fault      (core dumped) /usr/bin/ecasound -i "/tmp/$1.mp3" -C -q -etf:8 -o "$HOME/mp3/$1.mp3"



Any ideas ?

---

### Post by SuperMike on 2007-09-06
> **embeemb said:**
> I also encounter errors when using both the terminal and the GUI. It says it's done and saved but the mp3 directory is still empty.

Any ideas ?

embeemb, note that Google changed their scripts on Aug 20, 2007 and so I'm not as easily able to extract the FLV file. However, I've skimmed around in the Javascript and HTML of the pages and I might have it fixed in a few days when I get the time. The problem is that we're not downloading the FLV file. When we have that, and if you have ffmpeg, ecasound, xulrunner, and mpg123 installed, it should convert it to a simulated stereo MP3.

---

### Post by Chriss.Hi on 2007-09-09
I've a fix!!!!!
Instead of youtube.com/get_video?v=YOURID use that
[http://rd.cache.l.google.com/get_video?video_id=YOURID](http://rd.cache.l.google.com/get_video?video_id=YOURID)
I don't know how to change the shell-script but this url works
if you enter this one manually in firefox with the id you can download it...
Example: [http://rd.cache.l.google.com/get_video?video_id=Ke-kel9zOFo](http://rd.cache.l.google.com/get_video?video_id=Ke-kel9zOFo)

---

### Post by SuperMike on 2007-09-10
> **Chriss.Hi said:**
> I've a fix!!!!!
Instead of youtube.com/get_video?v=YOURID use that
[http://rd.cache.l.google.com/get_video?video_id=YOURID](http://rd.cache.l.google.com/get_video?video_id=YOURID)
I don't know how to change the shell-script but this url works
if you enter it manually in firefox with the id.
It gives an error 400 bad request but you can download the video...
Example: [http://rd.cache.l.google.com/get_video?video_id=Ke-kel9zOFo](http://rd.cache.l.google.com/get_video?video_id=Ke-kel9zOFo)

You are like sooooo awesome. I'm at work, but I'll give this a try when I get home tonight pretty late.

---

### Post by SuperMike on 2007-09-11
Here's the latest release!

```
#!/bin/bash
#
# Bash script to convert YouTube Video to Simulated Stereo MP3
#
# Public Domain
# Contributors: Supermike, Crouse, Kai Vehmanen, Chriss.Hi
#
bu="http://rd.cache.l.google.com/get_video?video_id="
mkdir -p ~/mp3;cd ~/mp3
read -p "YouTube url? " ur
read -p "Name? " nv
echo;echo;
uf=`echo $ur | cut -d = -f 2`
wget "${bu}${uf}" -O /tmp/y.flv
ffmpeg -i /tmp/y.flv -f mp3 -vn -acodec copy "/tmp/${nv}.mp3"
ecasound -i "/tmp/${nv}.mp3" -etf:8 -o "${nv}.mp3"
echo;echo;
rm -f "/tmp/${nv}.mp3"
echo "File is saved in your home directory in the 'mp3' folder."
read
```

---

### Post by Tom B on 2007-09-11
Yes! Works perfectly. Thank you so much.

---

### Post by SuperMike on 2007-09-11
Glad someone noticed. No problem. Enjoy, please! And I thank Chriss.Hi for the big help he gave me!

---

### Post by SuperMike on 2007-09-11
I've updated the GUI version now that the command line one works. It's here:

[http://code.google.com/p/yt2mp3/](http://code.google.com/p/yt2mp3/)

---

### Post by jamaas on 2007-09-27
Thanks, works great.

J

---

### Post by Nooreazy on 2007-09-27
Well...i couldn't get this thing to work so i found an alternate :guitar:.
Programs called "Sound Recorder".It records what ever sound your computer is outputting here is the code to install it 

```
sudo apt-get install sound-recorder
``` 
after you done installing it go to (did mine with 7.04) 
Applications>>>Sound&Audio>>> Sound Recorder

go to youtube.com,stream a video with sound 

Open up sound Recorder 

Record from input: MIX 
Record As:CD quality, lossless .OGG 

hit record as soon as the video starts playing or or record 3 secs earlier before the video starts to play once your done  recording.
File>>Save as>> <name>.ogg 

have fun :D :popcorn:

---

### Post by SuperMike on 2007-09-29
> **Nooreazy said:**
> Well...i couldn't get this thing to work so i found an alternate

Why don't you explain why it didn't work. I bet I can unstick you. Also, note that the audio you download from YouTube is mono, not stereo, and that my script used a tool to simulate stereo as well from the sound file.

---

### Post by Yes on 2007-09-29
I just can't seem to get it to work.  I tried running the latest version, and it just crashes when I try downloading anything.  Any ideas?

---

### Post by SuperMike on 2007-09-30
> **Yes said:**
> I just can't seem to get it to work.  I tried running the latest version, and it just crashes when I try downloading anything.  Any ideas?

Okay, try this:

* Are you using the script version or the version with the GUI? Try the version with the script, first, and that way we can see the error result.

* Have you installed the requirements as mentioned for the script?

* I had this problem, previously, when we were using an alternative means to capture that FLV file. We fixed that and now we have a line that points to rd.cache.l.google.com for the FLV. That seems to work.

* When I see your error result from the script, I'll be able to suggest the fix. It might be a requirements or permission problem.

---

### Post by Yes on 2007-09-30
Well, I got it to download the mp3, but all it is weird beeping and static noises.  I have all the requirments installed.

Thanks.

---

### Post by SuperMike on 2007-09-30
> **Yes said:**
> Well, I got it to download the mp3, but all it is weird beeping and static noises.  I have all the requirments installed.
Thanks.

Perhaps it's the video. Does this happen with all the YouTube videos you try? If so, then tell me what version of Ubuntu you have. If not, then shoot me the URL for the YouTube video and I'll see what happens on my system. Also, how do other MP3 files play on your system -- do they work okay or have static and beeping too?

Are you using a 64bit version of Ubuntu?

Do you have a multi-processor or non-Intel kind of processor?

What kind of sound card do you have?

---

### Post by Yes on 2007-10-01
Yeah, this happens with all the videos I try, I'm running the standard (Not 64 bit) Feisty Fawn. Here's the URL for the video: [http://www.youtube.com/watch?v=uWvrtA-UV0c](http://www.youtube.com/watch?v=uWvrtA-UV0c).  Other mp3s play fine.

I have an Intel Pentium 4.  It's not multi-core, but it's got hyperthreading, so Ubuntu treats it as if it has two cores.

My sound card is SB Audigy2, by Creative Labs.

Thanks.

---

### Post by SuperMike on 2007-10-02
I tried your URL and with non-64 Feisty on a P4 system just like yours except that I have a sound from the Dell motherboard. I used the project from here...

[http://code.google.com/p/yt2mp3/](http://code.google.com/p/yt2mp3/)

...and made certain I followed the requirements instructions:

    * xulrunner - retrieve from Mozilla.com
    * ffmpeg
    * lame
    * mpg123
    * mpeg codecs++
    * ecasound 
++ = get this simply by viewing the video in Firefox on YouTube's site and then get the mpeg codec for MP3 playback.

I did this on 3 different kinds of PCs and the result was all the same. It always converted it into a simulated stereo MP3 and not chirps, whistles, and static, but real sound. Sounds like something's still not right in your OS or perhaps with a funky setting in the BIOS. Try another comparable (or perhaps not comparable) PC and see if that helps.

BTW, are you overclocking?

Perhaps your sound card has an IRQ or DMA issue?

---

### Post by Yes on 2007-10-03
What do you mean by "viewing the video in Firefox on YouTube's site"?  I think that might be what I'm doing wrong.  Am I supposed to be viewing the video while the program is running?

---

### Post by SuperMike on 2007-10-05
No. You just view the video, copy the URL, paste it into the app I wrote, give it a name, and click download. Whether you're still watching that video, or on another video, is of no consequence except that it slows down the download.

---

### Post by Yes on 2007-10-10
Sorry for not replying sooner, but it's still not working =/.

---

### Post by Re1lly on 2007-10-16
Thanks for this program! the other day i found out about a similiar program in windows and being able to do the same  thing in ubuntu is great!!

---

### Post by SuperMike on 2007-10-16
> **Re1lly said:**
> Thanks for this program! the other day i found out about a similiar program in windows and being able to do the same  thing in ubuntu is great!!

Glad to hear it.

Well, this goes to show that it looks like when one follows the directions and uses a regular Ubuntu Breezy, Dapper, or Feisty workstation, it works great. So far I've followed the exact install instructions and was able to install it on 3 new Ubuntu workstations without trouble.

---

### Post by Yes on 2007-10-21
I don't know what was wrong in Feisty, but I upgraded to Gusty and it works great.

---

### Post by SuperMike on 2007-10-21
> **Yes said:**
> I don't know what was wrong in Feisty, but I upgraded to Gusty and it works great.

Hey, fantastic! I'm thinking either the Feisty install was botched (or a scratch CDR or something like that), or perhaps Feisty couldn't recognize your sound hardware properly and created the issue.

---

### Post by novus721 on 2007-10-22
Just wondering - is there any way to maintain the mono from youtube, if not just to maintain the same quality from the website? I don't know if it makes sense, but when I wear headphones it sounds like the sound is actually coming from behind me...so just wondering

and it also works great in 7.10 if anyone was wondering, at least with the GUI

Thanks!

---

### Post by SuperMike on 2007-10-23
> **novus721 said:**
> Just wondering - is there any way to maintain the mono from youtube, if not just to maintain the same quality from the website? I don't know if it makes sense, but when I wear headphones it sounds like the sound is actually coming from behind me...so just wondering

The install directory of the GUI version (yt2mp3) has a file called convert.sh in one of the directories. It drives the ecasound program which splits mono to stereo. I have been dying to know what the switches are, or perhaps another command to run, which would make the sound have a little reverb in it such that it broadens it and doesn't give the "from behind me" feeling. So feel free to experiment, and if you find the fix, please let me know.

You can also try the quicker route with the ytr Bash script version so that you can actually see what's going on a little better and can play with the script a bit faster.

In my truck, I found I have to play with the EQ a little to make it sound better, but I'm okay with that for now. But it would be great to play with the EQ in the ecasound program a little bit more to see what else I could do to make the simulated stereo even more realistic than it already is.

Note also that some songs are worse than others with this "from behind me" feeling.

Anyway, if anyone improves this, I'll include you in the credits on the next release and we can all benefit.

---

### Post by Tech Provider on 2007-11-11
I made the mistake of using a NTFS mounted partition for the GUI.

The scripts on NTFS are not running the bash file because the partition is not set right in fstab ! 

To test that your bash script is executed the right way use a test file and see if the default execution mode : ./test.sh in terminal window is ok.

If not you get a :/bin/sh: bad interpreter: Permission denied

After moving to the ext3 partition everything worked like a charm.

PS : it interesting to see how You can create an interface like the one Firefox uses, using xulrunner from Mozzila and run shell scripts. ( check out the js/sh files)

---

### Post by SuperMike on 2007-11-11
> **Tech Provider said:**
> 
PS : it interesting to see how You can create an interface like the one Firefox uses, using xulrunner from Mozzila and run shell scripts. ( check out the js/sh files)

Yeah, it's a fantastic development environment for rich client, rich client + webserver, and webserver-based situations although I think there are a few problems with xulrunner that I'd like to see fixed:

* Having a requirement of a forced set of directories and paths gets a little silly, in my opinion. Had they not realized that someone might want something simpler for smaller projects?

* It's still too slow to boot. Perhaps they could survey all the xulrunner developers they can find for two years and see which features they actually use, then propose an xulrunner-lite kind of standard that slims the thing down to only the most essential items that people actually use.

* The GUI from xulrunner apps needs to be a slight bit snappier. It's fast, but could stand to be even faster.

* GUI multithreading with a callback timer is necessary. I mean, what if I have a Bash script that's running in the background that's taking quite a long time, and I want to make the GUI update a progress bar without freezing the whole window? I have yet to figure this out.

---

### Post by SuperMike on 2007-11-18
Okay, it broke again. Evidently in yt2mp3/chrome/content/yt2mp3 of the GUI version of this script, in download.sh, the 'bu' parameter points to:

[http://rd.cache.l.google.com/get_video?video_id=](http://rd.cache.l.google.com/get_video?video_id=)

Evidently Google changed this yet again. So I'll have to reverse engineer the way to get the video again.

---

### Post by SuperMike on 2007-11-18
Fixed. Version 1.3 is now available here:

[http://code.google.com/p/yt2mp3/downloads/list](http://code.google.com/p/yt2mp3/downloads/list)

I'd like to acknowledge this user on Nuxified who helped make this possible:

[http://www.nuxified.org/user/bashist](http://www.nuxified.org/user/bashist)

...from this post:

[http://www.nuxified.org/blog/download_youtube_video_files_with_youtube_dl#comment-10289](http://www.nuxified.org/blog/download_youtube_video_files_with_youtube_dl#comment-10289)

---

### Post by kewlman1945 on 2007-11-23
Hey,
     What was the fix and what is the new format that youtube is using. Anyways this is awesome work :lolflag:

---

### Post by Caffeine_Junky on 2007-11-23
Nice work, this is very handy

---

### Post by LusciousChunks on 2008-01-24
Just installed Gutsy yesterday, still new to everything. Program worked fine last night and I got two songs with the GUI version and the sound is awesome.  Tried it today and when it said that the video was downloading it did it much quicker than normal and went through the rest leaving a 1.2 kb mp3 file with the name I designated which doesn't open.  I tried the non-gui version and this is what I get: 
************************
root@charles-desktop:/usr/bin# ./ytr
YouTube url? [http://www.youtube.com/watch?v=EX24QOFbNWk](http://www.youtube.com/watch?v=EX24QOFbNWk)
Name? davematthewsband graceisgone


--11:24:53--  [http://rd.cache.l.google.com/get_video?video_id=EX24QOFbNWk](http://rd.cache.l.google.com/get_video?video_id=EX24QOFbNWk)
           => `/tmp/y.flv'
Resolving rd.cache.l.google.com... 64.233.179.99, 64.233.179.104
Connecting to rd.cache.l.google.com|64.233.179.99|:80... connected.
HTTP request sent, awaiting response... 502 Bad Gateway
11:24:54 ERROR 502: Bad Gateway.

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
/tmp/y.flv: Unknown format
********************************************************************************
*        ecasound v2.4.5 (C) 1997-2006 Kai Vehmanen and others    
********************************************************************************
- [ Session created ] ----------------------------------------------------------
- [ Chainsetup created (cmdline) ] ---------------------------------------------
- [ Connecting chainsetup ] ----------------------------------------------------
(eca-chainsetup) 'nonrt' buffering mode selected.
(audioio-mp3) Unable to open file /tmp/davematthewsband graceisgone.mp3.
(eca-chainsetup) Audio object "/tmp/davematthewsband graceisgone.mp3", mode 
... "read".
(audio-io) Format: s16_le, channels 2, srate 44100, interleaved.
(eca-chainsetup) Audio object "davematthewsband graceisgone.mp3", mode 
... "write".
(audio-io) Format: s16_le, channels 2, srate 44100, interleaved.
- [ Chainsetup connected ] -----------------------------------------------------
(eca-control-objects) Connected chainsetup: "command-line-setup".
- [ Controller/Starting batch processing ] -------------------------------------
- [ Engine init - Driver start ] -----------------------------------------------
./ytr: line 16:  6187 Segmentation fault      (core dumped) ecasound -i "/tmp/${nv}.mp3" -etf:8 -o "${nv}.mp3"


File is saved in your home directory in the 'mp3' folder.
******************

I keep getting the 502 Bad Gateway error no matter which file I try. Any help would be appreciated as when the program was working it was a great resource.

---

### Post by SuperMike on 2008-01-26
They broke the API again. I'm giving up. I think what I'm going to do from here on out is just create an FLV to simulated stereo MP3 Bash script, keeping it simple and easy, and people can use one of two methods to get that FLV from YT:

1. Just play the YT vid all the way through and then copy the file from /tmp/Flash* to ~/Desktop/Flash.flv.

2. Use a downloader site from the web (which hopefully is up to date) that downloads that FLV file.

Sorry gang -- just not enough time in the day to dedicate my life to this. If you want to make it better, please feel free to fork the yt2mp3 project and edit the Bash script yourself. It's inside the zip file a few directories deep.

---

### Post by AnonCat on 2008-01-27
Wow, I love this program and can finally convert my millions of youtube music videos to mp3 files.  For those who had an empty mp3 folder, I found that rebooting my computer after installing the requirements fixed that problem on the GUI version (I also closed my browser after pasting the youtube address into the GUI just to be on the safe side).

---

### Post by SuperMike on 2008-01-29
[COLOR="Red"]**ANNOUNCEMENT**[/COLOR]

I had to keep updating ytr and yt2mp3 all the time. It got tiring and I didn't have a lot of time. Things have to keep being updated because all those free video sites change their web pathing API for how the video is loaded. So if you use a script or bookmark a site that can extract the video, chances are it's broke within 30 days.

So, if you have let the video download all the way through, and not necessarily played it, you can do:

```
$ cp /tmp/Flash* ~/mymovie.flv
$ ffmpeg -i mymovie.flv mymovie.wmv
$ rm -i /tmp/Flash*
```

This gives you the video in FLV and WMV formats. The second step is only necessary if you want to copy it over to a Windows workstation to view it. Of course, you must know how to properly install ffmpeg and add the right codec, but this is described here at ubuntuforums.org.

Now, if you want to extract the mono MP3 out of the YouTube FLV and convert it to simulated stereo, do it with:

```
$ ffmpeg -i ~/mymovie.flv -f mp3 -vn -acodec copy /tmp/temp.mp3
$ ecasound -i /tmp/temp.mp3 -etf:8 -o ~/mysong.mp3
$ rm -i /tmp/temp.mp3
```

Of course, this requires that you install ecasound, the mp3 codec, and ffmpeg, and that you reboot your computer before using them after installation. Again, this is described in ubuntuforums.org and on many Ubuntu blogs on the web.

In order to add an ID3 tag in the MP3 file, just run it through Beep Media Player, which you can install easily, doubleclick the title once it appears during play, fill out the ID3 form, and click Save.

All I can say is that with this technique, the bad guys (RIAA, MPAA, ODEX) can't stop us unless they force vendors to switch from Flash to some other kind of medium.

---

### Post by Muscar on 2008-01-29
Sweet, thanks

---

### Post by durand on 2008-02-01
Yeah, I realised that that's the problem with the youtube scripts. Anyway, just found this site that links you to the flv. [http://keepvid.com/](http://keepvid.com/)

Using that, I changed the download.sh file a bit:

```

#!/bin/bash

ur="$1"
#old way bu="http://rd.cache.l.google.com/get_video?video_id="
#old way bu="http://cache.googlevideo.com/get_video?video_id="
bu="http://sjl-v124.sjl.youtube.com/get_video.flv?video_id=" # CHANGE THIS IF THE LINKING URL CHANGES
mkdir -p ~/mp3
rm -f /tmp/y.flv
uf=`echo $ur | cut -d = -f 2`
wget "${bu}${uf}" -O /tmp/y.flv
#t=$(wget -O- "http://www.youtube.com/watch?v=${uf}" | grep -o
#"t:'[^']\+")
#wget -O /tmp/y.flv "${bu}${uf}&t=${t##*\'}"

exit 0

```

IE: went back to the old way as it seemed simpler and then just modified the url. Oh and thanks a lot for the awesome script :)

---

### Post by SuperMike on 2008-02-02
Hey, thanks for this. I'm sure a lot of other readers will appreciate what you discovered. Feel free to fork the project, Durand, and own it. Google will even give you the free project space on code.google.com.

---

### Post by GamingMazter on 2008-02-02
Cheers...Been thinking about stuff like this for ages. Thanks!

---

### Post by durand on 2008-02-02
Thought about that but there's not much point in changing the code everytime if google's going to keep doing this. It may be easier to just download the latest url from [http://code.google.com/p/yt2mp3/examplecode](http://code.google.com/p/yt2mp3/examplecode). example code being a plain text file that just contains the ever changing url. Then you can just use

```
wget http://code.google.com/p/yt2mp3/examplecode
bu=`cat examplecode` 
```

---

### Post by SuperMike on 2008-02-02
Aha, durand. That might be an option there. Unfortunately I'm mired in debt right now, don't have any options to work around here, and have been doing PHP freelancing like a banshee in order make ends meet and keep from getting evicted from my home. So, if anyone out there wants to own this, please, more power to them. I'm swamped, unfortunately.

---

### Post by durand on 2008-02-03
okay, good luck.

---

### Post by picpak on 2008-02-18
Has anyone tried this?

[http://www.flv2mp3.com/](http://www.flv2mp3.com/)

I just found it.

---

### Post by vista on 2008-02-19
But if you have a mono mp3 file on your desktop and you want to convert that file to "fake stereo"using ecasound, what command lines do you use for this? Command line for locating the mp3 file on my desktop and then command line for conversion to stereo? Step by step instructions please.;)

I would really love to try this out and hear the result. Or is this also possible to do in ffmpg? 

Should I install this to? No?
libecasound16-devel
python-ecasound
ruby-ecasound

Thanks :)

---

### Post by durand on 2008-02-19
> **vista said:**
> But if you have a mono mp3 file on your desktop and you want to convert that file to "fake stereo"using ecasound, what command lines do you use for this? Command line for locating the mp3 file on my desktop and then command line for conversion to stereo? Step by step instructions please.;)

I would really love to try this out and hear the result. Or is this also possible to do in ffmpg? 

Should I install this to? No?
libecasound16-devel
python-ecasound
ruby-ecasound

Thanks :)

```
/usr/bin/ecasound -i "input.mp3" -C -q -etf:8 -o "output.mp3"
```
Just replace input.mp3 with your file and output.mp3 with the new filename.

> Has anyone tried this?

[http://www.flv2mp3.com/](http://www.flv2mp3.com/)

I just found it.

That will create mono mp3's and you have to give it the actual flv url as opposed to this script which takes the youtube url.

They seemed to have changed the linking url again and added encryption? Anyway, use this site to get your flv: [http://keepvid.com/](http://keepvid.com/) and then you can upload it to [http://www.flv2mp3.com/](http://www.flv2mp3.com/) and then use the above code!

---

### Post by vista on 2008-02-19
> **durand said:**
> ```
/usr/bin/ecasound -i "input.mp3" -C -q -etf:8 -o "output.mp3"
```
Just replace input.mp3 with your file and output.mp3 with the new filename.


I get this error: ecasound v2.4.5 (C) 1997-2006 Kai Vehmanen and others
********************************************************************************
- [ Session created ] ----------------------------------------------------------
- [ Chainsetup created (cmdline) ] ---------------------------------------------
- [ Connecting chainsetup ] ----------------------------------------------------
(eca-chainsetup) 'nonrt' buffering mode selected.
(audioio-mp3) Unable to open file 123.mp3
ERROR: Connecting chainsetup failed: "Enabling chainsetup: AUDIOIO-MP3: Can't open... 123.mp3 for reading."

:(  i tried other mp3 files aswell but same error.

---

### Post by vista on 2008-02-20
Also, is there a way to check if ecasound is properly installed on my system? 

:-s

---

### Post by durand on 2008-02-20
ecasound is working properly because it showed you that message. I don't think [http://www.flv2mp3.com/](http://www.flv2mp3.com/) works....correct me if I'm wrong but I just got a blank file. I don;t have any mono mp3's to test so....not sure here. When I used the yt3mp3 script, it worked fine.
Maybe your file is corrupt.

---

### Post by Jackelope on 2008-05-22
Does this work on Hardy? I've been trying to make it work for almost 2 hours and have accomplished nothing :( ....then again, I'm still a noob when it comes to linux, so it might just be my own lack of knowledge. Still....it'd be nice to know its at least possible to make it work.

---

### Post by SuperMike on 2008-05-23
1) Works on hardy just fine, but the script and the GUI are broke (thanks to Google) and you have to know how to use ffmpeg and ecasound.

2) Go visit a YouTube video and then do this repeatedly in your command window while the video is downloading into the YT video control:

```
$ ls -al /tmp/Flash*
```

See that file getting bigger and bigger (byte count) and then it finally stops? That's an FLV file -- it just doesn't have the extension on it.

3) So, once that stops filling up with bytes, I can then do:

```
$ sudo su
# cp /tmp/Flash* /tmp/movie.flv
# ffmpeg -i /tmp/movie.flv /tmp/monosong.mp3
# ecasound -i /tmp/monosong.mp3 -etf:8 -o /home/yourloginid/yoursong.mp3
# exit
$ exit
```

On the above, if it asks to overwrite, say yes except on the ecasound line -- where you might want to change the song name.

And this sticks a file called yoursong.mp3 in my /home/yourloginid directory that is a simulated stereo file.

4) To add a genre, song title, band name, and album info, that's called ID3. There's a handy ID3 editor you get when you install something called "Beep Media Player" (in add/remove programs). You just play the song and then doubleclick the scrolling title of it when it appears. An ID3 dialog will pop open. You fill out the form and click Save. It will save the update even while the song is playing. You can then drag this to your MP3 player's MUSIC folder or whatever and listen to it on your MP3 player.

5) Note that you can also watch YouTube videos on your MP3 player if it has video support. I have one for Rockbox that's posted [here]("http://ubuntuforums.org/showthread.php?t=705899"). (My son converted his iPod to a Rockbox iPod in order to play videos.)

---

### Post by tromort on 2008-05-23
wow, i havn't tried this since im on school atm but when i get home I surely will.

looking awesome so far!:popcorn:

---

### Post by starcannon on 2008-05-23
the DownloadHelper Firefox extension makes it easy as well, click on a nice little gui icon in your browser, save the movie like you would any other download.

either way, its not to hard.

---

### Post by durand on 2008-05-23
Probably easier to use [http://keepvid.com/](http://keepvid.com/) to download the flv first, then apply step 3.

---

### Post by Bobbafett on 2008-05-28
You could probably use youtube-dl to download the youtube video to a place other than then /tmp folder:
[http://www.arrakis.es/~rggi3/youtube-dl/](http://www.arrakis.es/~rggi3/youtube-dl/)

I have a Groovy script that uses this to batch download the YT videos, it is very simple, I can post it here if anyone needs it.

---

### Post by fuzzyl0g1c on 2008-05-29
Thanks for the guide, works great!

---

### Post by Bobbafett on 2008-05-29
Maybe a dumb question, but here I go anyway: Do I absolutelly need to install mpg123 in order to make the conversion?

---

### Post by SuperMike on 2008-05-30
> **Bobbafett said:**
> Maybe a dumb question, but here I go anyway: Do I absolutelly need to install mpg123 in order to make the conversion?

I wouldn't know without taking a virgin machine and experimenting. Since I don't have the time or the spare machine, I can't help you there.

---

### Post by durand on 2008-05-30
> **Bobbafett said:**
> Maybe a dumb question, but here I go anyway: Do I absolutelly need to install mpg123 in order to make the conversion?

You probably don't.

---

### Post by Bobbafett on 2008-05-30
Ok I  think I am missing somethng here :(
I have downloaded a bunch of YouTube videos using youtube-dl, these FLV files play with no problem in MPlayer.
When I run ffmpeg as:
ffmpeg -i 'My Music Video.flv' -f mp3 -vn -acodec copy 'My Music File.mp3'

I get a MP3 file generated, but XMMS cannot play it :(

However if I run:
mplayer -ao pcm:waveheader -vc dummy -vo null 'My Music Video.flv'

I have no problem playing the generated audiodump.wav file with XMMS.

So, I think I probably have a mp3 codec missing or something? If anyone have any advice on this one I'd be happy to hear :)

Thanks

---

### Post by Bobbafett on 2008-05-31
Never mind my previous post :P
I realized I needed to run first:
sudo apt-get install ubuntu-restricted-extras

Then using this command:
ffmpeg -i 'My Music Video.flv' -f mp3 -ab 128k -vn -acodec mp3 'My Music File.mp3'

And then applying the ecasound command works perfectly :)


Thanks a lot anyway and sorry about wasting your time :P

---

### Post by Gripp on 2008-05-31
That pretty cool.  hopefully before you started this project that you can use VLC player to do what you just did...

get the vid using DownLoadHelper in firefox, then run the .flv file through VLC and transcode it to mp3|mpeg1, then run that through transcode as a mp3|raw ... done..

but otherwise, great work!  much easier than my method i'm guessing

edit for clarity

---

### Post by malinna on 2008-06-01
Very easy for u with [E.M. Youtube video downlad tool]("http://www.effectmatrix.com/Youtube_video_download_tool/").
It works very well and easy to use.

It can download video from youtube , myspace, veoh, yahoo or any other video websites autoamtically.

It can also convert flv video to  any audio include MP3, wma,wav,ac3,mmf,amr,ogg,aac..., to any video formats include 3gp,avi,wmv, mpg,mpg4,asf,swf,h264,mov,jpg, that can be support by PSP,iPod,iPhone,Apple TV video,iTune,MP3,MP4,Zune,Cellphone,Digital camera,DV,CD/DVD/VCD/SVCD.

[http://www.effectmatrix.com/Youtube_video_download_tool/index.htm](http://www.effectmatrix.com/Youtube_video_download_tool/index.htm)

:):):):lolflag:
[IMG]http://www.effectmatrix.com/Youtube_video_download_tool/Youtube_video_download_tool_s.jpg[/IMG]

---

### Post by durand on 2008-06-01
I hope that is not spam. That tool is for windows only and its not open source.

---

### Post by Hackbert's Celine on 2008-06-20
Thats really anoying, even if you find a way to get your .flv file, my ubuntu wont convert it, i tried audacity ffmpeg mplayer (->mencoder) NOTHING works. I'm almost upset - the first time since i use linux - because that issue mustnt be as hard to do as it actually is. 

ITS A REAL PROBLEM!!!!

---

### Post by SuperMike on 2008-06-20
> **Hackbert's Celine said:**
> Thats really anoying, even if you find a way to get your .flv file, my ubuntu wont convert it, i tried audacity ffmpeg mplayer (->mencoder) NOTHING works. I'm almost upset - the first time since i use linux - because that issue mustnt be as hard to do as it actually is. 

ITS A REAL PROBLEM!!!!

First things first -- just how new are you to Linux and to command-line interaction with Linux?

Second, this is an intermediate hack, not really made for novices.

Third, have you installed all the multimedia doodads onto Ubuntu from this link? Perhaps that's what's blocking the conversion.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Note that this link above is a bit long to go through -- I remember it being far shorter. It also may have you install way more than you need.

---

### Post by fallen seraph on 2008-06-20
I get the following message:

exception... "component returned failure code 0x80520006
(NS_ERROR_FILE_TARGET_DOES_NOT_EXIST)[nslProcess.init]" nsresult: "0x80520006 (NS_ERROR_FILE_TARGET_DOES_NOT_EXIST)" location: "JS frame ::chrome://yt2mp3/content/yt2mp3.js :: RunCommand :: line 65" data:no]


..Any ideas?

---

### Post by SuperMike on 2008-06-21
> **fallen seraph said:**
> I get the following message:

exception... "component returned failure code 0x80520006
(NS_ERROR_FILE_TARGET_DOES_NOT_EXIST)[nslProcess.init]" nsresult: "0x80520006 (NS_ERROR_FILE_TARGET_DOES_NOT_EXIST)" location: "JS frame ::chrome://yt2mp3/content/yt2mp3.js :: RunCommand :: line 65" data:no]


..Any ideas?

Yeah. I wrote the code. Go back and read this entire thread from top to bottom. You'll discover something we all discovered. That Google changed YT to block us. You'll notice if you look through my logic in my code (which isn't very exotic, by the way) that I shell out and call a few bash scripts. One of those is broken because it fails to download a file from YT.

The way I got around this was a process, as I explain in this thread, where I wait for the file to fill up in /tmp as Flash* (wildcard is the *), and then created another Bash script to copy the FLV file out and process it with ffmpeg and ecasound.

I wish I could have the time to revisit the yt2mp3.js code, but I just don't have the time right now. I'm open to anyone who wants to fork it. Please do and share. :)

---

### Post by Gripp on 2008-06-24
hmm
i just tried my method of ripping sound from .flv files with VLC on linux for the first time.. oddly it didn't work!

works fine in winblows though.. i wouldn't expect there to a difference(?!)


edit: yeah, i just tried with the same flv file from last.fm first on ubuntu, then on windows XP pro.  it works on XP, but not ubuntu.

the steps are:
1. open VLC player
2. File>Wizard...
3. Select "Transcode/Save to file" - next
4. "Choose..." then select the .flv file that you got using DownloadHelper - next
5. Check the box for Transcode Audio, set it to MP3 and set the bitrate to 192 - next
6. IMPORTANT - select MPEG 1 as your encapsulation method - next
7. save the file as <name> .mpg

now, repeat all of those steps on the mpg file that you just created, only this time select RAW as your encapsulating method and save the file with an MP3 extension. 

done. from internet video to your car stereo. 
it seems like a lot of steps but its actually not so bad once you get a flow going. 

BUT... for some dumb reason this isn't working on linux... it must have something to do with the method that the linux version of VLC player is creating the MP3 file..

so hopefully someone here figures it out...

---

### Post by macmasterxiv on 2008-08-09
Script fixed for hardy/8.04 and the latest YouTube setup.

[SIZE="4"]Requirements[/SIZE]

First do this:

```
$ sudo apt-get update
$ sudo apt-get install xulrunner ffmpeg lame mpg123 ecasound youtube-dl
```

Then restart the system to make sure ecasound starts correctly.


[SIZE="4"]Script[/SIZE]

```
#!/bin/bash
#
# Bash script to convert YouTube Video to Simulated Stereo MP3
#
# Public Domain
# Contributors: Supermike, Crouse, Kai Vehmanen, Chriss.Hi, John-Michael Mulesa
#
mkdir -p ~/mp3;cd ~/mp3
read -p "YouTube URL: " ur
read -p "Filename: " nv
echo;echo;
youtube-dl "${ur}" -o /tmp/y.flv
ffmpeg -i /tmp/y.flv -f mp3 -vn -acodec copy "/tmp/${nv}.mp3"
ecasound -i "/tmp/${nv}.mp3" -etf:8 -o "${nv}.mp3"
echo;echo;
rm -f "/tmp/${nv}.mp3"
echo "File is saved in your home directory in the 'mp3' folder."
read
```

---

### Post by SuperMike on 2008-08-10
Thanks so much, macmasterxiv

---

### Post by TCSnyder on 2008-09-10
It Doesnt work for me. it says it is saved but nothing is in the folder.
 i am using the mediaconverter.org plugin for firefox but i only lets you do 10 downloads a day. so i was looking for something else

---

### Post by TCSnyder on 2008-09-10
I Got It Working. but can we change the code to just keep the audio the exact same as from the youtube file. i can tell the slight change when the volume is all the way up. can i just comment out a few lines? if so which ones

---

### Post by SuperMike on 2008-09-11
> **TCSnyder said:**
> I Got It Working. but can we change the code to just keep the audio the exact same as from the youtube file. i can tell the slight change when the volume is all the way up. can i just comment out a few lines? if so which ones

The audio you get from YT is mono. The command line that uses ecasound converts from mono to a simulated stereo (which sometimes is not so perfect). This is the one you'll want to comment out with a # symbol on the first line. However, what you get then is just mono.

Now, if you're creative, and you interact with the community that maintains the ecasound community on the web (Google that) and you'll find ways to improve the ecasound command in certain cases, even doing better than the work I have done with it. For instance, do you hear a hum when you turn it up? If so, then perhaps you can use the ecasound command to isolate it and pull it out. Or, do you hear bass gets clipped after so many decibels and you want to prevent that? These are two examples that I've made up, but where ecasound can be used to craft that sound.

---

### Post by mixmadmen on 2008-12-06
:D Hey there. Just thought I would pop in and report how this all worked out for me. (glad to finally have it working now)

Im running Hardy, and the initial program here:
[http://code.google.com/p/yt2mp3/](http://code.google.com/p/yt2mp3/)
had that same issue repeatedly mentioned earlier by others where it would say the video was downloaded and the file should be in the mp3 folder, however it was nowhere to be found.

This was tried on my first install of hardy, and I eventually gave up on it and left the project on the back burner. Then after upgrading to Intrepid I tested this out again but the same problem. Though, Intrepid has horrible sound issues, so even if the program worked fine, I'd suspect additional issues caused by it anyway. XD

Since then I've wiped and made a completely fresh install of Hardy and had the same trouble.

However, I read through all the posts to try every suggestion the first time and this time as well (so many posts lol!) but no luck-- until I got to the one posted by macmasterxiv.

:) Now it works like a charm.

Thanks so much for working so hard on this project, guys. I'm so glad to have this working now. :D

---

### Post by mixmadmen on 2008-12-06
Oh-- sorry, and one last note if it helps any, I tried [http://code.google.com/p/yt2mp3/](http://code.google.com/p/yt2mp3/) with both the US and UK YouTube links 
(like [http://uk.youtube.com/watch?v=6y1CLxxraxE](http://uk.youtube.com/watch?v=6y1CLxxraxE) versus [http://youtube.com/watch?v=6y1CLxxraxE](http://youtube.com/watch?v=6y1CLxxraxE) )
just to see if it made any difference. This made no difference in any of my tests. :) The current working suggestion has no trouble with either and the problematic initial tests wouldn't work with either.

---

### Post by SuperMike on 2008-12-07
BTW, if you want to switch your YouTube videos to stereo, if they were uploaded in stereo in the first place, just go to your address line of the video and tack on the following option:

&fmt=18

Again, this doesn't work with all videos because some were uploaded in mono. Meanwhile, if you do use this option, then yt2mp3 will still not grab the stereo version because yt2mp3 ALWAYS runs this through the 'ecasound' command to convert mono to simulated stereo.

So, for me, I go back to command line for now because I don't have the time right now to update yt2mp3 everytime YouTube wants to change things. So, what I do is:

$ sudo su
# cd /tmp
# rm -i /tmp/Flash*

...now go to YouTube and click on the video you want. Next, tack on &fmt=18 on the end and hit enter on the address line in your browser. Wait until the red tube fills up to indicate the video completely downloaded.

# cp   Flash*   song.flv
# ffmpeg  -i  song.flv  song.mp3

...and now I move song.mp3 to whatever and use chown on it to give me the proper permissions to that file.

Now, if the song ends up being mono, you can see in this thread how I use ecasound to convert into simulated stereo. If it's already in stereo, then you can use an ID3 editor to put in the genre, album name, song title, artist name, etc. For me, I use an older copy of Beep Media Player (not the latest version because I think the overhaul they did completely sucks -- I use bmp from the Hardy distro).

BTW, this technique also works with Pandora and many other video and song sites on the web.

---

### Post by telemah on 2008-12-07
I saw about the code earlier but I dont seem do know how to work with it pls explain ( i am new...)

---

### Post by TorqueyPete on 2009-01-02
Hi SuperMike.
 I appreciate your efforts. and am looking forward to grabbing some sound files. But I'm geting an error in the terminal, and ecasound isnt installing.
 Every thing else on the list went ok. Any ideas? Have I done something wrong?

-desktop:~$ sudo apt-get ecasound
E: Invalid operation ecasound


Cheers, Pete.

---

### Post by SuperMike on 2009-01-03
> **TorqueyPete said:**
> Hi SuperMike.
 I appreciate your efforts. and am looking forward to grabbing some sound files. But I'm geting an error in the terminal, and ecasound isnt installing.
 Every thing else on the list went ok. Any ideas? Have I done something wrong?

-desktop:~$ sudo apt-get ecasound
E: Invalid operation ecasound


Cheers, Pete.

Oh, it's:

-desktop:~$ sudo apt-get update; apt-get **install** ecasound

..or...

-desktop:~$ sudo su
# apt-get update
# apt-get **install** ecasound
# exit
-desktop:~$

---

### Post by Neostar2119 on 2009-01-03
I tried this, but I can't seem to make it work.

First tried the XUL app, and got this...

> Details: Failed to execute child process "/home/neostar/yt2mp3/yt2mp3.xulrun" (Permission denied)

Ten I tried to operate it from the terminal (I'm a recently converted Windows user that loves to work in the Terminal, am I strange?)

Here's a copy of my input and output...

```
neostar@DreathusMain:~$ ytr
YouTube url? http://www.youtube.com/watch?v=QBYxCFCk3GQ
Name? whenyouleave.mp3


--2009-01-03 10:49:23--  http://rd.cache.l.google.com/get_video?video_id=QBYxCFCk3GQ
Resolving rd.cache.l.google.com... 64.233.189.99, 64.233.189.104, 64.233.189.147, ...
Connecting to rd.cache.l.google.com|64.233.189.99|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-01-03 10:49:31 ERROR 404: Not Found.

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
/tmp/y.flv: Unknown format
********************************************************************************
*        ecasound v2.4.6.1 (C) 1997-2007 Kai Vehmanen and others    
********************************************************************************
- [ Session created ] ----------------------------------------------------------
- [ Chainsetup created (cmdline) ] ---------------------------------------------
- [ Connecting chainsetup ] ----------------------------------------------------
(eca-chainsetup) 'nonrt' buffering mode selected.
(audioio-mp3) Unable to open file /tmp/whenyouleave.mp3.mp3.
(eca-chainsetup) Audio object "/tmp/whenyouleave.mp3.mp3", mode 
... "read".
(audio-io) Format: s16_le, channels 2, srate 44100, interleaved.
(eca-chainsetup) Audio object "whenyouleave.mp3.mp3", mode 
... "write".
(audio-io) Format: s16_le, channels 2, srate 44100, interleaved.
- [ Chainsetup connected ] -----------------------------------------------------
(eca-control-objects) Connected chainsetup: "command-line-setup".
- [ Controller/Starting batch processing ] -------------------------------------
- [ Engine init - Driver start ] -----------------------------------------------
(audioio-mp3) Can't start process "mpg123 --stereo -r %s -b 0 -q -s -k %o %f". Please 
... check your ~/.ecasound/ecasoundrc.
(audioio-mp3) Starting to encode whenyouleave.mp3.mp3 with lame.
(audioio-mp3) Can't start process "lame -b %B -s %S -x -S - %f". Please check your 
... ~/.ecasound/ecasoundrc.
(eca-engine) WARNING: An output object has raised an error! Possible causes: Out 
... of disk space, permission denied, unable to launch external applications needed in 
... processing, etc.
- [ Controller/Batch processing finished (-3) ] --------------------------------
ecasound: Warning! Errors detected during processing.
(eca-control-objects) Disconnecting chainsetup: "command-line-setup".
- [ Chainsetup disconnected ] --------------------------------------------------


File is saved in your home directory in the 'mp3' folder.

```

Obviously, no mp3 file to speak of.

Where did I go wrong here?

---

### Post by TorqueyPete on 2009-01-03
Thanks Mike
 ecasound installed, but now my Totem movie player is very slow. Moving at about 1 frame per second. :D
I reinstalled Totem in Synaptic, but no change.

I'll do some checking in the Multimedia how to thread.

---

### Post by ithanium on 2009-01-03
it doesn't work anymore :(

---

### Post by SuperSonic4 on 2009-01-03
Yeah, the OP edited the first post to highlight this

---

### Post by Neostar2119 on 2009-01-03
Thanks for the update Mike, I left the programs involved and removed the ytr and xul app. Maybe i'll find a use for them somewhere down the line.

---

### Post by SuperMike on 2009-01-16
I started to think some RIAA trolls were here, so I decided not to continue it. I do have my ways of making the scripts work still, though. I just won't be sharing that here for the RIAA or YT engineers to shut down.

---

### Post by andrew.46 on 2009-01-19
Hi SuperMike,

> **SuperMike said:**
> BTW, if you want to switch your YouTube videos to stereo, if they were uploaded in stereo in the first place, just go to your address line of the video and tack on the following option:

&fmt=18

Just saw the note on the beginning of your guide about the changes that Google have made. Remember the old saying:

'Nil Bastardum Carborundum'

which is as much as to say 'Don't let the b***rds grind you down!

Now I am not sure if it is of any use to you at all in your script but the newest version of youtube-dl has a few commandline switches for the high quality option you speak of. There are some details [here]("http://ubuntuforums.org/showthread.php?t=1037760") in a post that has received absolutely zero interest :(. I guess the sticking point might be exactly how many such high quality vids are actually there although my own experience seems to suggest that some sort of mass conversion might be taking place.

Typically these files are:

```
  Duration: 00:03:43.67, start: 0.000000, bitrate: 455 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 480x360, 29.97 tb(r)

```

Now I know aac conversion can be a little problematic under Ubuntu but with a little work these files can also have the sound extracted and converted to mp3 with ffmpeg? It would be nice if your script could incorporate this :-).

All the best,

Andrew

---

### Post by SuperMike on 2009-01-19
Andrew what does this do?

X.aac = name of your AAC file that has other stuff in it (like video), let's say:

ffmpeg   -i   X.aac   X.mp3

Does it just work? Does it pull out that sound stream?

You might need to install the 'lame' libraries to get ffmpeg to do the conversion, perhaps. I'm not familiar with AAC format too much. Most of the time all I need to do is rename something like /tmp/Flashx2338230 into /tmp/song.flv, and then run it through ffmpeg. And if the file is in mono, try and convert it with &fmt=18 on the URL (if from YT) and try again. And if the file is still mono, then use ecasound -etf:8 (or -etf:10, -etf:12, whatever) to convert to simulated stereo after doing the ffmpeg conversion.

---

### Post by andrew.46 on 2009-01-20
Hi SuperMike,

Well, a problem might be the different syntax found with all the different versions of ffmpeg found with Ubuntu. The file I have on my Desktop from youtube is the following:

```
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Rammstein_Mutter.mp4':
  Duration: 00:03:45.90, start: 0.000000, bitrate: 338 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 352x264, 24.99 tb(r)

```

And conversion of audio only with the svn ffmpeg, decreasing the bitrate a little is as follows:

```
andrew@skamandros:~/Desktop$ [B][COLOR="Red"]ffmpeg -i Rammstein_Mutter.mp4 \
-acodec libmp3lame -ab 192k Rammstein_Mutter.mp3[/COLOR][/B]
FFmpeg version SVN-r16683, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --disable-debug --enable-shared --disable-static 
--enable-postproc --enable-avfilter --enable-pthreads --enable-libtheora 
--enable-libvorbis --enable-swscale --enable-x11grab --enable-libmp3lame 
--enable-libxvid --enable-libx264 --enable-libschroedinger 
--enable-libfaac --enable-libamr-wb --enable-libamr-nb 
--enable-libspeex --enable-libgsm --enable-nonfree --enable-gpl
  libavutil     49.14. 0 / 49.14. 0
  libavcodec    52.11. 0 / 52.11. 0
  libavformat   52.24. 1 / 52.24. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 2. 0 /  0. 2. 0
  libswscale     0. 6. 1 /  0. 6. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Jan 19 2009 12:03:54, gcc: 4.3.2
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Rammstein_Mutter.mp4':
  Duration: 00:03:45.90, start: 0.000000, bitrate: 338 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 352x264, 24.99 tb(r)
[B][COLOR="Red"]Output #0, mp3, to 'Rammstein_Mutter.mp3':
    Stream #0.0(und): Audio: libmp3lame, 44100 Hz, stereo, s16, 192 kb/s[/COLOR][/B]

```

and this produces a stereo 192 kbs mp3. I am not sure how the stock Ubuntu ffmpeg handles aac audio though. But the sound and picture quality of the unaltered, downloaded mp4 file is pretty impressive anyway do you think?

Andrew

---

### Post by Sharepointengine on 2009-01-20
Hi,

Smash this is unbelievable!!!!
Extremely excellent effort. 
This is acutely awfully chill…..
:D

---

### Post by SuperMike on 2009-01-20
> **andrew.46 said:**
> Well, a problem might be the different syntax found with all the different versions of ffmpeg found with Ubuntu. The file I have on my Desktop from youtube is the following

Andrew.46: Looks like YT screwed with us again. I can no longer convert the /tmp/Flash* (renamed song.flv) to song.mp3 by either:

# ffmpeg -i song.flv -acodec libmp3lame -ab 192K song.mp3

nor

# ffmpeg -i song.flv song.mp3

**EDIT:** On the conversion, I keep getting:

[flv @ 0xb7ef8110]Unsupported video codec (7)

---

### Post by andrew.46 on 2009-01-20
Hi,

Hmmmm.... I am not sure about that. I tested the following:

```
$ youtube-dl 'http://www.youtube.com/watch?v=EwL0G9wK8j4'
```

Sorry about the boring clip :-). It converted successfully with ffmpeg as follows, I am not sure about the value of increasing the frequency or adding the stereo setting:

```
ffmpeg -i EwL0G9wK8j4.flv -acodec libmp3lame -ar 44100 -ac 2 -ab 112k test.mp3
```

But it certainly produced the required stereo mp3 soundtrack. I should stress that I am not any form of expert with ffmpeg though, just a casual user. For real expertise there is: 

HOWTO: Compile the latest ffmpeg and x264 from source
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Andrew

---

### Post by Ender27182818 on 2009-01-22
Thanks for the work on this.

I run Intrepid Ibex, and I was having trouble with ecasound outputting the mp3 file directly. Seems there's a disconnect between ecasound and lame. Intrepid uses a newer version of lame and and older version of ecasound which doesn't properly understand lame's newer message output.

Anyways, I changed the script a bit so that ecasound does it's mono-to-stereo thing and produces a wav file, then lame directly encodes the mp3 from the .wav. This is definitely sub-optimal, but it IS an effective workaround for Intrepid. 

Of course, original credit goes to SuperMike and others in this forum that have posted information. I just connected the final link for me, and believe in giving back.

My version also keeps most of the files around. /tmp/{filename}.flv is kept, and {filename} (mono).mp3 and {filename} (sim-stereo).mp3 are both produced. The only file I delete is the *.wav file. I do this because I've found on certain videos, I prefer the sound of the mono file.


```

#!/bin/bash
#
# Bash script to convert YouTube Video to Simulated Stereo MP3
#
# Public Domain
# Contributors: Supermike, Crouse, Kai Vehmanen, Chriss.Hi, John-Michael Mulesa, Eli Ribble
#
mkdir -p ~/mp3;cd ~/mp3
read -p "YouTube URL: " ur
read -p "Filename: " nv
echo;echo;
youtube-dl "${ur}" -o "/tmp/${nv}.flv"
ffmpeg -i "/tmp/${nv}.flv" -f mp3 -vn -acodec copy "${nv}.mp3"
ecasound -i "${nv}.mp3" -etf:8 -o "${nv}.wav"
lame "${nv}.wav" "${nv} (sim-stereo).mp3"
mv "${nv}.mp3" "${nv} (mono).mp3"
# Comment out the next line to save the .wav file
rm -f "${nv}.wav"
# Comment out the next line to save the (mono) file
#rm -f "${nv} (mono).mp3"
# Comment out the next line to save the .flv file
#rm -f "/tmp/${nv}.flv"
echo;echo;
echo "File ${nv}.mp3 has been created"


```

-Eli Ribble

---

### Post by SuperMike on 2009-01-23
Ender27182818: Don't forget, you can also add "&fmt=18" on the end of SOME (keyword, SOME) YouTube videos and get better sound quality, if not stereo, and thus ecasound might not be necessary. However, I've noted that some videos already come in stereo, and some videos do not benefit with fmt=18 at all -- it all depends and you must test with your ears before running youtube-dl script.

---

