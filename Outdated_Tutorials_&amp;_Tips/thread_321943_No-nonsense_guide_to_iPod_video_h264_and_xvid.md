---
title: "No-nonsense guide to iPod video: h264 and xvid"
date: 2006-12-19
forum: Outdated Tutorials &amp; Tips
---

### Post by jdong on 2006-12-19
**I have written a more streamlined and slightly simplified version of this guide is available on the Ubuntu Wiki:**  [http://wiki.ubuntu.com/iPodVideoEncoding](http://wiki.ubuntu.com/iPodVideoEncoding)

**Introduction**
There are several guides floating around here for encoding video to the iPod but I've always found myself a bit dissatified with them. The reasons included:

   * Some have evolved into ultra-complex scripts that did ALMOST what I wanted, but it was overly involved to tweak it to my liking
   * Most only did MPEG4-ASP (i.e. xvid) at low resolutions
   * Some required the installation of a large number of tools, mostly from source, etc.
   * Still others only handled a particular type of medium, for example, Handbrake only rips DVD's

This guide will give you simple, no-nonsense, 2-line bash scripts to doing a large assortment of video encodes. I am a strong believer in the command line for jobs like this. It gets the job done, is easy to script, and if the script is staightforward enough it's also a breeze to modify.

**The bad news: ffmpeg recompile**
You need to rebuild ffmpeg with restricted format encoding support. I've already provided a patched source package that you can build using debuild or prevu. I will cover the usage of prevu here. There is a guide on installing prevu, search the forums please :)
```

$ prevu http://buntudot.org/people/~jdong/ffmpeg/ffmpeg_0.cvs20060823-3.1ubuntu1+0restricted1.dsc
$ sudo apt-get update
$ sudo apt-get dist-upgrade

```

Say Yes to the prompt about unauthenticated packages. it's ok, it's just the ffmpeg you built.


**The good news, easy to use scripts**

Ok, the general way to use these scripts is **~/ipodconv /path/to/source.avi /path/to/destination.mp4**. The sources can be any format that ffmpeg supports, so think of anything that VLC can play :D. The destination format is an iPod compatible mp4 video file. The codec/resolution used depends on which script variant you use. Replace **ipodconv** with the name of the particular script. Remember to chmod +x ~/ipodconv before using it!


**Script 1: high-quality h264, 640x480**
This creates a very nice quality h264 at 640x480 that looks great on an iPod, on a computer screen, or outputted to a TV. For me, it looks nearly identical to the 1500kbit xvid I start out with. **NOTE**: This is a very slow encode. Expect to use double the run time to encode on a modern processor (i.e. when using my 1.66GHz Core Duo, it takes 5 hours to encode a 2 hour movie). It is not multithreaded by default, because IMO the gain in encode speed does not jusify the gain in CPU usage.
```

#!/bin/bash
ffmpeg -y -i "$1" -v 1 -threads 1 -vcodec h264 -b 500 -bt 175 -refs 2 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -partb8x8 1 -me full -subq 6 -brdo 1 -me_range 21 -chroma 1 -slice 2 -max_b_frames 0 -level 13 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 35 -max_qdiff 4 -i_quant_factor 0.71428572 -b_quant_factor 0.76923078 -rc_max_rate 768 -rc_buffer_size 244 -cmp 1 -s 640x480 -acodec aac -ab 96 -ar 48000 -ac 2 -f mp4 -pass 1 "$2"
ffmpeg -y -i "$1" -v 1 -threads 1 -vcodec h264 -b 500 -bt 175 -refs 2 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -partb8x8 1 -me full -subq 6 -brdo 1 -me_range 21 -chroma 1 -slice 2 -max_b_frames 0 -level 13 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 35 -max_qdiff 4 -i_quant_factor 0.71428572 -b_quant_factor 0.76923078 -rc_max_rate 768 -rc_buffer_size 244 -cmp 1 -s 640x480 -acodec aac -ab 96 -ar 48000 -ac 2 -f mp4 -pass 2 "$2"

```

** Customizing Script #1 **: There's lots of ways you can customize this script:
 (1) Multithreading. If you have multiple cores, adjust **threads 1** to the number of CPU's you want to use to encode. Note that 2 threads on a dual-core system will only provide like a 20% speed improvement; your speed **will not double**.
 (2) Higher bitrate. **-b 500** and **-rc_max_rate 768** control the average bitrate and the maximum instantaneous bitrate, respectively. Both can be increased to 1500 on the 5.5Gen iPod. I've not tested increasing these , though, since for me this setting looks great enough. You can also change the audio bitrate with the **-ab 96** setting. The iPod supports up to 160kbit audio.
 (3) Low-res encode. If you have no desire to output to your TV or view these on your computer, then you can just encode at 320x240, ipod resolution. Note that this will look noticeably blurry if outputed to a computer or HDTV screen, and somewhat blurry on a regular TV too! Change **640x480** to **320x240**, and also you can bump the bitrate **-b 500** down to **-b 175** or even 150. It'll look just as beautiful on your iPod display.
 (3) Do your laundry. Actually, no, unfortunately ffmpeg doesn't do that yet.


**Script 2: Fast xvid, 320x240**
If you don't have the patience or desire to do a high-quality h264 rip, try this xvid rip. On my system it encodes about 8x realtime, which means a 2-hour movie will be converted in 15 minutes. It looks acceptable on the iPod, though there is blocking/blurring in high-motion scenes. It can probably look better with a higher bitrate or a second pass.
```

#!/bin/bash
ffmpeg -y -i "$1" -f mp4 -vcodec xvid -maxrate 1000 -b 400 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 64 -s 320x240 "$2"

```

Wow, doesn't that look a lot simpler? You may ask, why xvid and not ffmpeg's mpeg4? Well, in my experience ffmpeg's mpeg4 generates worse quality for the same bitrate, unless I turn on the highest settings. If I do that, then mpeg4 is slower than xvid. Xvid is fast enough that I think it's worth it to use it!

**Customizing script 2**
  (1) Higher bitrate. Same as script #1. Modify -b (and also maxrate for the max instantaneous rate). The iPod 5.5gen will support up to 2500kbit. Modfiying audio bitrate is identical to #1 too.
  (2) Higher resolution. The iPod supports 640x480, so in theory you can just bump 320x240 up to that. I've not tried 640x480 xvid though, so please let me know how that works out for ya!
  (3) 2-pass encode. See next!


** Script 3: 2-pass xvid, 320x240**
If you want a slightly better quality than #2, then you can elect to do a 2-pass encode. the command looks like:
```

#!/bin/bash
ffmpeg -y -i "$1" -f mp4 -vcodec xvid -maxrate 1000 -b 400 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 64 -s 320x240 -pass 1 "$2"
ffmpeg -y -i "$1" -f mp4 -vcodec xvid -maxrate 1000 -b 400 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 64 -s 320x240 -pass 2 "$2"

```

It takes twice as long as script #2, for a slight but noticeable increase in quality.



**But what about DVD's?**
So far, I've only covered dealing with non-DVD sources. For DVD rips, it's best to cache them to the hard drive with mplayer, then use ffmpeg on the cached file. I'll assume you have mplayer installed. Just do
```

mplayer dvd://1 -dumpstream -dumpfile dvdcache.vob

```
Then use dvdcache.vob as the input file. For picking a different audio stream than the default, you'd need to append -map settings to the ffmpeg command(s). It should be ** -map 0:0 -map 0:***desired_audio_stream*. The desired audio stream can be determined from "ffmpeg -i dvd.vob" output. Sorry I'm so brief on that; I've never done it before ;-)

Alternatively, you can also first do a DVD rip with a DVD ripping program and then feed that output to the conversion scripts.


**Transferring to the iPod**
Well, I intended this to be an encoding guide, but I'll touch bases on tranferring. I use gtkpod to do it; the Edgy-included versions of gtkpod will do it, and there's also guides around here for getting newer version of libgpod and/or gtkpod. But here's a few tips:

 (1) If you rename your output videos with a .mov extension, both the non-AAC and the AAC gtkpod versions will accept and upload it.
 (2) If you transfer it as a .mov, the play time will not be set. Manually set the length (play time) in the properties if you want to use .mov. If you don't do this, you will not be able to see the length of the video as it's playing, or use the wheel to seek through the movie (but FF and REW will still work properly)
 (3) If your gtkpod is AAC-enabled (i.e. you installed gtkpod-aac or built your own gtkpod with AAC/mp4 support), you can directly use a mp4 or m4v extension. In this case, play length is auto detected.
 (4) Amarok doesn't support transferring m4v video without building libgpod 0.4.0, then REBUILDING amarok. Even then, it won't tag the videos correctly unless you have mp4/AAC support turned on, which is not the case in Ubuntu's version.

**It doesn't play! Black screen, etc**
The MP4's that ffmpeg generates are slightly non-standards-compliant. The 1.1 firmware used to really choke on that. However, 1.2 (aka 5.5G) is much better at it, but I've had a few cases with very short H.264 640x480 clips where it doesn't play ffmpeg-generated MP4's, but shows a black screen or even resets.

In that case, you can use MP4Box (install package **gpac**) to re-pack it. Some guides show you how to do an in-place repack, but with recent versions of mp4box, **it doesn't work!** It'll just add the mp4 to itself, doubling the size! Instead, do something like this:
```

MP4Box -add output.mp4 output.mp4.tmp
rm output.mp4
mv output.mp4.tmp output.mp4

```


I haven't put this in my encoding scripts because 99% of the times the videos work perfectly fine without repacking , and repacking is disk-intensive (needs to write the entire MP4 again).

---

### Post by cor2y on 2006-12-26
i know this is a bit late but after getting the latest version of prevu then running 
sudo prevu-init
And after that
sudo prevu-update


I am now stuck with this message as relates to the custom ffmpeg
```

Traceback (most recent call last):
  File "/usr/bin/prevu", line 60, in ?
    print "Package %s:\n%s ==> %s" % (sys.argv[1],getsrcver(sys.argv[1]),buildbackportver(sys.argv[1]))
  File "/usr/bin/prevu", line 16, in buildbackportver
    raise NoSuchPackageException, "Source package %s couldn't be found" % pkg
__main__.NoSuchPackageException: Source package http://buntudot.org/people/~jdong/ffmpeg/ffmpeg_0.cvs20060823-3.1ubuntu1+0restricted1.dsc couldn't be found

```

Obviously something is wrong somewhere, please help

---

### Post by jdong on 2006-12-26
That is not the latest version of prevu... The latest is at [http://sourceforge.net/project/showfiles.php?group_id=125877&package_id=206140](http://sourceforge.net/project/showfiles.php?group_id=125877&package_id=206140) , version 0.4.1

---

### Post by cor2y on 2006-12-26
ok removed the previous version and updated to the latest version and again ran

sudo prevu-init
and
sudo prevu-update

now this is the new error
```

I: Building against currently running distro: dapper
sh: dget: command not found
Traceback (most recent call last):
  File "/usr/bin/prevu", line 144, in ?
    BackportFromDsc(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 83, in backport
    self.prepare_sources()
  File "/usr/bin/prevu", line 131, in prepare_sources
    raise ValueError("Extracting source package failed")
ValueError: Extracting source package failed

```


don't know what it means but might this mysterious "dget" be the problem?

---

### Post by ixus_123 on 2006-12-26
Thanks a lot for the tutorial.  I'm just installing dapper (browsing from the live cd while it installs) but once it's done I'll give it a go.

I'm hoping it will work with matroska containers holding h264 video & ogg sound. My VLC would play these but often crash if I tried to skip forward unless using the chapter menu.

5 hours is fast!  Got to get myself a core duo. I've been seeing times of about 12 hours for a standard movie + 2 soundtracks & subs encoding to h.264 on my 2.14Ghz Sempron

---

### Post by jdong on 2006-12-26
I should've said that I've only tested this configuration on Edgy, but I don't see any reason why it shouldn't work on Dapper.

I'm not sure the extent of ffmpeg's support for mkv, there might be the need for other tools for that job. Try ogmrip for that :)

---

### Post by jdong on 2006-12-30
> **cor2y said:**
> ok removed the previous version and updated to the latest version and again ran

sudo prevu-init
and
sudo prevu-update

now this is the new error
```

I: Building against currently running distro: dapper
sh: dget: command not found
Traceback (most recent call last):
  File "/usr/bin/prevu", line 144, in ?
    BackportFromDsc(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 83, in backport
    self.prepare_sources()
  File "/usr/bin/prevu", line 131, in prepare_sources
    raise ValueError("Extracting source package failed")
ValueError: Extracting source package failed

```


don't know what it means but might this mysterious "dget" be the problem?
Hmm, it's not finding dget, which is in package devscripts.

---

### Post by boog321 on 2006-12-31
> **jdong said:**
> Hmm, it's not finding dget, which is in package devscripts.

could a simple 'sudo ln -s /usr/bin/wget /usr/bin/dget' correct the issue? or is there something different about dget?

---

### Post by jdong on 2006-12-31
No, wget != dget. dget is a script that takes in a link to a .dsc file and fetches everything that apt-get source would given the .dsc file. does the command 'dget' do anything at the command line?

Try apt-get install --reinstall devscripts?

---

### Post by pixelboy on 2006-12-31
edit...

nevermind.. sorted it :)

---

### Post by ThrobbingBrain66 on 2007-01-01
I used the howto from the Wiki and it works great for episodes of The Simpsons, Family Guy and any animated series.  But for any non-animated shows like That 70s Show and Scrubs, the audio starts out sync'd but then goes out of sync.  By the end of some episodes, the audio is off by close to two seconds id say.

Anyone have a fix for this?

---

### Post by jdong on 2007-01-02
I too have noticed this behavior to some extent with mpeg4 content. Also ffmpeg spits out hundreds of errors about the framerate and headers of the **source** media being invalid.

I think it has less to do with animated/non-animated than it does with who/what encoded the content, because I've done animated stuff that fails and I've done live stuff that succeeds.

Try switching a codec... sometimes just going from mpeg4 to h264 helps out. Also, sometimes going from 1-pass to 2-pass makes an impact.

Another thing you can do is a high-bitrate (i.e. 2000kbit xvid) pass re-encoding the source with a mencoder solution such as acidrip. mplayer has much better capabilities for dealing with a-v sync and also corrupt/nonstandard files compared to regular ffmpeg.


Fortunately I have a few videos in my collection that exhibit this behavior so as it annoys me more, I'll definitely research this more in-depth!

---

### Post by Wallakoala on 2007-01-02
nice guide, I am just wondering what are some good resoltions for widescreen movies that will fit on an ipod.

thanks

---

### Post by jdong on 2007-01-02
you just have to keep width below 640 and height below 480.... I've simply scaled down the width of my videos to 640 and then used the same scaling ratio on the height for my stuff... I'm sure that'll make the media techies here freak and start yelling at me but I've had no issue with that yet :D

---

### Post by steveyos666 on 2007-01-04
I'm trying to use the wiki link since I didn't manage to get the tutorial in the post itself working..

I'm at the part with the following:

```
apt-get source ffmpeg
cd ffmpeg-*/
./configure --enable-gpl --enable-pp --enable-zlib --enable-vorbis \
        --enable-libogg --enable-theora --enable-a52 --enable-dts \
        --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
        --enable-faad --enable-faac --enable-xvid --enable-x264
make
sudo make install
```

I'm not quite sure if I'm supposed to copy that whole thing into the terminal or one line at a time (I don't mean the make/ sudo make of course) with ./configure in front of each line, but either way I get the following:

Unknown option "--enable-zlib"

Any ideas?

---

### Post by jdong on 2007-01-04
Remove any options that ffmpeg doesn't recognize... different versions of ffmpeg may support different subsets of commands.

---

### Post by steveyos666 on 2007-01-04
> **jdong said:**
> Remove any options that ffmpeg doesn't recognize... different versions of ffmpeg may support different subsets of commands.

I ended up putting in:

```
./configure --enable-gpl --enable-pp --enable-vorbis \
        --enable-libogg --enable-a52 --enable-dts \
        --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
        --enable-faad --enable-faac --enable-xvid

```

That gave some lines... Then I typed make and now it's giving me I'd have to say at least 100+ lines so far, most of them with "warning" in them...

It's still going too... I don't got much of a good feeling about this, but I'll let it do what it has to do.

---

### Post by steveyos666 on 2007-01-04
Alright I got it working, thank you.

Is there any way to do more than one movie at once? I wanna put some TV shows on here for when I'm really bored and actually feel like watching TV but nothing's on (usually when I'm going to bed).

Or even better, is there a GUI? I'm no good with the terminal, completely noobafied when it comes to it.

---

### Post by jdong on 2007-01-05
You can script it at a terminal like:

```

for source in /path/to/*.avi /yet/another/file.avi; do
ipodconv "$source" "$source.m4v"
done

```

List all the files you want to convert after "in" on the first line. You can use wildcards or files separated by a space. The output files will be in the same directory as the source file with a m4v extension. Unfotunately the extension will be avi.m4v.

If that bothers you, you can complicate the ipodconv line into:
```

ipodconv "$source" "`basename \"$source\" avi`m4v"

```

If you ask me, unless you're a seasoned Linux guru the above line is absurdly hard to remember/learn, so I'd personally just live with an extra .avi.m4v :D


As far as a GUI, I currently have no plans on wrapping a GUI around this. I've been a strong believer in the command line for stuff like this, and I'm simply too busy right now to devote time to that. Others are perfectly welcome to wrap this in a GUI though! I do encourage these code snippets to be treated as GPL though, but I have no idea if legally I can enforce that for a single ffmpeg command line :D

---

### Post by steveyos666 on 2007-01-05
You'd actually rather use the terminal? Maybe that's why there's people out there still using Windows :O

Wouldn't it be better to have like a window that has maybe 10 or so browse parts, then next to them are a space where you'd type what you wanted the file name to be and where you wanted to save it? Or maybe convert a whole directory with sub folders just by choosing it?

I mean why not make it easier for those of us who are new and don't want to go back to Windows but can't make any sense whatsoever of the terminal :(

I mean here's one for ya, at the end of the directory is a $, but Ubuntu is free! ahh!

No really though, thanks for the help. Maybe in ten years when I finally know what I'm doing, I can make a GUI-based video converter :D

---

### Post by steveyos666 on 2007-01-05
That didn't work so I changed it to ipodvidenc and it seems to be working. Seems like it's saving it as a .mov, which is ok with me, unfortunitly saving it in the home folder but that's alright too... I'm not quite sure if it's gonna do every video I have in the folder but I'll see what happens.

I don't know if it matters or not, but having spaces in the folder/file names seems to cause a problem. I'm not sure though.



EDIT: Well once one movie is done it asks for the name of the next one and stuff. I was hoping it'd just do them all so I didn't have to sit here, but it's all good, can't complain when it's free :D

---

### Post by Wallakoala on 2007-01-13
after finally getting ffmpeg compiled with x264 support, I ran the script for the high quality h264 video. I get the following error:

```
Input #0, mpeg, from 'dvdcache.vob':
  Duration: 01:01:46.4, start: 0.233567, bitrate: 5303 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480, 5000 kb/s, 29.97 fps(r)
  Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, 224 kb/s
Output #0, mp4, to 'video.mp4':
  Stream #0.0: Video: h264, yuv420p, 640x480, q=2-35, pass 2, 500 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: aac, 48000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
**x264 [error]: invalid width x height (0x640)**
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

what is bolded seems to be what the main problem is. I have done some google searching and there have been lots of people with teh same problem, but no fixes. Any help?

---

### Post by jdong on 2007-01-13
Hmm, weird; I've yet to see this error (I mostly use Edgy)

Are you using Dapper?

---

### Post by Wallakoala on 2007-01-14
> **jdong said:**
> Hmm, weird; I've yet to see this error (I mostly use Edgy)

Are you using Dapper?

no, i'm using edgy. I think it has something to do with x264. Did you compile x264? Whenever I try to compile x264 with mp4 support it fails miserably. For now I am using the 2 pass xvid at 640x480 and it looks great on the ipod, but i am just wondering why the h264 isn't working.

---

### Post by jdong on 2007-01-14
I think it was an interaction between Dapper's ffmpeg and Dapper's x264... I doubt anyone tested to see if the two would cooperate :D

Neither are trivial to backport, so I guess H.264 encoding won't work for Dapper users :-/

If other dapper users can confirm ,then I'll make a note about this on the wiki page.

---

### Post by FernandoMilton on 2007-01-18
> **steveyos666 said:**
> You'd actually rather use the terminal? Maybe that's why there's people out there still using Windows :O

Wouldn't it be better to have like a window that has maybe 10 or so browse parts, then next to them are a space where you'd type what you wanted the file name to be and where you wanted to save it? Or maybe convert a whole directory with sub folders just by choosing it?

I mean why not make it easier for those of us who are new and don't want to go back to Windows but can't make any sense whatsoever of the terminal :(

I mean here's one for ya, at the end of the directory is a $, but Ubuntu is free! ahh!

No really though, thanks for the help. Maybe in ten years when I finally know what I'm doing, I can make a GUI-based video converter :D

Try [Vive]("http://vive.sourceforge.net/"), based on the efforts of this other [thread]("http://ubuntuforums.org/showthread.php?t=114946") concerning to conversion to video Ipod. I agree that command line on this case can be very confusing to the less experienced users, but you should take in account that the Ipod Video is still young and it is very "sentimental" concerning to the format it accepts. 

All these command lines are kinda trial and error (myself having tried sucessfully a couple of others based on mencoder to hardcode subtitles, as english is not my first language and I really need them, but Ipod doesn't support). As soon as these scripts are mature enough, people with more skill in GUIs will eventually pick up and develop good tools to ease the task. 

This is the free way to do things, a collaborative network of people, usually without support from the companies, blindly experimenting in the first months, then coming (or not) with a mature and enjoyable product. Anyway, don't let the command line discourage you to use Linux.

---

### Post by jdong on 2007-01-18
FernandoMilton, very articulately spoken.


Basically, these lengthy ffmpeg commands are still very much in development... I am still up to now sorting through them, compensating for common variations of commands...

At the same time, I'm working on another more complex but easier-to-use Python script that will set up its own ffmpeg environment for encoding and take easier command lines, and also be designed from ground-up as a library that another program can use.

That way, once this is all complete, it will be simple to make a GUI around this base. But for now, time spent writing a GUI is time wasted perfecting these commands. Having a pretty GUI that pumps out incorrect, distorted, and/or unplayable video files is more useless than an ugly command-line program that generates correct results.

---

### Post by alphazero on 2007-01-20
This guide worked great for me with one small little hitch. The outputted videos have an additional pixel on the left and right sides of the screen. The end result is what appears to be an uncropped video with a long black line on both sides. I rechecked the source to make sure it wasn't it but it came down to the outputted files. Any ideas are greatly appreciated.

---

### Post by pestie on 2007-01-21
I'm running Dapper and trying to follow the instructions [here]("https://help.ubuntu.com/community/iPodVideoEncoding") and, as you might expect, I've run into a problem. The recompile of ffmpeg went just fine, no problems there. But I'm attempting h.264 encoding and getting this error:
```
ffmpeg: unrecognized option '-refs'
```
I'm guessing this has something do with the note below:
[INDENT]*Note that as of December 2006, the SVN version of ffmpeg has changed the name of several of the options used in this command, so it will not work on newer ffmpeg. Sitting down for a few minutes with the error messages and ffmpeg's help output will sort that out. When such a version of ffmpeg becomes in a released version of Ubuntu, this guide will be updated with appropriate commands, but for now there is not that much of a demand.*[/INDENT]
So, in trying not to be an idiot, I did exactly that - looked at the man page for ffmpeg. But the problem is, I have no *old* man page to look at, so I have no way to determine what "-refs" is supposed to do and find the new command-line option.

FWIW, 2-pass xvid encoding, using the command lines from the first post of this thread, seems to work fine.

I'm quite familiar with transcoding video using mencoder, but ffmpeg is pretty much a black box to me. Can anyone point me in the right direction?

---

### Post by jdong on 2007-01-21
Lovely, welcome to the world of ffmpeg and changing commands :)

-refs is supposed to set the # of H.264 reference frames to use. Using reference frames allows recycling more information from previous frames in constructing new ones, so it increases quality at a given bitrate.

The iPod officially does NOT support reference frames but from the documentation for the Broadcom video chipset and testing, it's been found that you can get away with 1 or 2 reference frames (and maybe 3 or 4 in 320x240 or lower resolutions)


If you can't find the command for it in earlier ffmpeg, you can feel free to drop it altogether (it should default to 0, which should still work)

One of these days I'm planning on making a more intricate Python script that not only can encode but also set up a designated ffmpeg setup for encoding to the iPod :)

---

### Post by j0nheck on 2007-01-24
Success with Edgy:

Recompiled ffMPEG with this guide: [http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu/](http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu/) 

Using the high-quality script from the first post in the thread works great. I am still not satisfied with the quality though. Utilizing HandBrake (uses ffMPEG) on my Mac I am able to achieve better quality results.

I'm off to read through the ffMPEG docs and figure out what all those options in your high quality script do!

j0nheck.

---

### Post by jdong on 2007-01-24
Hmm, are you selecting a higher bitrate on your Mac compared to this script? -b 500 is not always enough for iPod H264 due to its lower complexity profile.

This script activates virtually every enhanced quality option that can possibly be supported by the iPod (in fact, it exceeds the iPod's official specs but stays within the specs for its Broadcom video chipset from the OEM supplier)

---

### Post by j0nheck on 2007-01-25
I did select a higher bitrate (running 1000 with a max of 1200). But I think I found out part of the problem.

When previewing the files on my Ubuntu box they look crumy--artifacts, boxes--it looks like a high jpeg compression. BUT--when i use quicktime on my Mac--they videos look beautiful.   VLC on my Mac produced similar (though not quiet as good) of results as Quicktime. 

I've been encoding 23minute TV episodes and getting from 170-200MB, i'm going to start trying lower bitrates and a few other options (Changing 'me method' from 'full' to 'epzs') Right now it takes about 2 hours for a 2-pass encoding of one of these shows, seems a little long to me.

Has anyone tried experimenting with doing a lower quality second pass? I've read that it can speed up encode times and give similar quality results.

---

### Post by jdong on 2007-01-25
Strange indeed. For me Ubuntu plays these back just as good as any other OS.

---

### Post by Protoss on 2007-02-04
Greate guide! I am currently converting the Scrubs Musical (best. episode. ever.) using your script, and so far its doing pretty well, and I can actually use my computer while converting! In windows I couldn't do a thing if Nero was doing its thing.

---

### Post by jdong on 2007-03-04
[https://help.ubuntu.com/community/iPodVideoEncoding#head-ebb27b589cb5a6aa0c7fca5837cb0e0eb76b1909](https://help.ubuntu.com/community/iPodVideoEncoding#head-ebb27b589cb5a6aa0c7fca5837cb0e0eb76b1909)

^^ I wrote a Python CLI frontend to these commands the other day. I have found that people often want to customize resolution and bitrate and don't want to deal with editing a 5-line-long ffmpeg command.

Now, it's as simple as

```

pypodconv -i input.avi -o output.m4v

``` 
For default (2-pass, 320xNNN H.264, 200kbit). The script supports easy-to-use switches for common customizations:
```

jdong@severance:~/src/pypodconv$ pypodconv
Usage: pypodconv [options]

Options:
  -h, --help            show this help message and exit
  -i INPUT, --input=INPUT
                        Source file to encode
  --sd, --320, --standard-definition
                        Encode to Standard Definition (that is, 320xNNN,
                        native iPod screen resolution) [DEFAULT]
  --hd, --640, --high-definition
                        Encode to High Definition (that is, 640xNNN, maximum
                        iPod-supported resolution
  -c CODEC, --codec=CODEC
                        Video Codec: h264 [DEFAULT], xvid, or mpeg4.
  -o OUTPUT, --output=OUTPUT
                        Output file, with file extension.
  -b VBITRATE, --vbitrate=VBITRATE
                        Video Bitrate, in kbit/s. (default: 200)
  -p PASSES, --passes=PASSES
                        Number of passes. (Default: 2)

```


One of the cooler features is --sd vs --hd, the video is automatically scaled so that it fits the iPod guidelines for either resolution , but also preserves aspect. No more fumbling with a calculator :)


Do people like this approach better? The script is considerably longer (111 lines) but it does make the user's life easier :)

---

### Post by FakeOutdoorsman on 2007-03-17
John,

Can you explain to me how you came up with -bt 175?  Shoudn't this value change depending on your bitrate and maxrate, ie the differences in --sd vs --hd?  Maybe I just need an education as to what -bt really does.  man ffmpeg just states "Set video bitrate tolerance" which is not helpful.  I have a basic idea, but I may be wrong.

---

### Post by FakeOutdoorsman on 2007-03-17
> **jdong said:**
> This script activates virtually every enhanced quality option that can possibly be supported by the iPod (in fact, it exceeds the iPod's official specs but stays within the specs for its Broadcom video chipset from the OEM supplier)

Where are the Broadcom specs you are referring to?  I found [Broadcom VideoCore BCM2722]("http://www.broadcom.com/products/Cellular/Mobile-Multimedia-Processors/BCM2722") info at the OEM site, but the data sheet doesn't really have useful specifications.

---

### Post by jdong on 2007-03-17
> **FakeOutdoorsman said:**
> John,

Can you explain to me how you came up with -bt 175?  Shoudn't this value change depending on your bitrate and maxrate, ie the differences in --sd vs --hd?  Maybe I just need an education as to what -bt really does.  man ffmpeg just states "Set video bitrate tolerance" which is not helpful.  I have a basic idea, but I may be wrong.

That is the tolerance (the maximum accepted deviation from targeted bitrate) that is permitted for the current encoding buffer (bufsize). You can play around with that value, but as long as it's about 50% or greater than the bitrate I've found it makes no appreciable difference. So 175 in the end was an arbitrary value that worked for both --sd and --hd.

> 
Where are the Broadcom specs you are referring to? I found Broadcom VideoCore BCM2722 info at the OEM site, but the data sheet doesn't really have useful specifications.

I can't find it ATM but there was a very helpful post to the ffmpeg mailing list describing what kind of things the chip was capable of for xvid decoding. The H.264 stuff mainly came from me experimenting with ref frames, etc settings and seeing how far I could push it before it fails to decode.

---

### Post by Protoss on 2007-03-18
Would there be any way to convert a whole folder of videos with your pypodconv script?

---

### Post by jdong on 2007-03-18
Sure, by a bash loop:

```

for i in *.avi; do
pypodconv -i "$i" -o "$i.m4v" --other-options
done

```

This will output files with names of filename.avi.m4v. if you are a _REAL_ perfectionist you can use instead:
```

pypodconv -i "$i" -o "`basename "$i" .avi`.m4v" --other-options

```

This will strip the .avi off the final name and make it .m4v.

---

### Post by Protoss on 2007-03-18
Sweet, thank you! Now if I wanted to output all the files to one folder...?

---

### Post by jdong on 2007-03-18
After they're done encoding just "mv *.m4v /path/to/destination"

Or change -o "$i.m4v" to -o "/path/to/destination/$i.m4v"

---

### Post by Protoss on 2007-03-18
Awesome, thank you for this script! Overnight convertions of Scrubs, here I come!

---

### Post by jdong on 2007-03-18
LOL I've done some massive season conversions of various shows and .... they take a while, especially on HD ;-)

I think at the end I had all 5 of my computers involved and it took 4 days :)

---

### Post by FakeOutdoorsman on 2007-04-05
I'd like to tweak your pypodconv script to work with SVN ffmpeg and x264, but I'm not very script inclined and have some questions:

1. What are the exact commands that the script is running for a 320x240 x264 2-pass encode?

2. Is -b_quant_factor even required since you are not using b-frames?

3. Why not use -subq 1 for the first pass and -subq 6 for the second pass to speed the encoding?  Very little loss of PSNR will occur and it may encode much faster.  I need to perform some speed tests on that though.

---

### Post by jdong on 2007-04-05
> **FakeOutdoorsman said:**
> I'd like to tweak your pypodconv script to work with SVN ffmpeg and x264, but I'm not very script inclined and have some questions:

1. What are the exact commands that the script is running for a 320x240 x264 2-pass encode?

Add "-s" to the command line, and it will print out all the commands it would issue, instead of issuing them ;-)

> 
2. Is -b_quant_factor even required since you are not using b-frames?

Probably not I guess :) Haven't tried without.

> 
3. Why not use -subq 1 for the first pass and -subq 6 for the second pass to speed the encoding?  Very little loss of PSNR will occur and it may encode much faster.  I need to perform some speed tests on that though.
Sounds like a great idea. Just need to test it and see if it works :)

---

### Post by FakeOutdoorsman on 2007-04-06
I did some test to determine length of encoding and Peak Signal to Noise Ratio (PSNR) loss using SVN of ffmpeg and x264 for 320x240 x264.

I used "time ffmpeg ..." to determine encoding length and the -psnr option in all tests.

**pypodconv script default**
encoding time: 1m 53.4s
Global PSNR (higher is better): 36.110 dB

**pypodconv script with first pass as -subq 1**
1m 34.2s
PSNR: 36.089

**Robert Swain's values** [(link)]("http://rob.opendot.cl/index.php/useful-stuff/ipod-video-guide/")
2m 25s
PSNR: 36.281

I can upload the resulting videos and the actual commands if anyone is interested.  Personally I couldn't tell much difference between Swain's and the default pypodconv except at the end around some text.  It was barely noticable, but it was a little blockier in the pypodconv script.

This wasn't a very scientific test and I only used a 1m 15s  video to test with so results may vary.

---

### Post by FakeOutdoorsman on 2007-04-06
This script could probably work easily with the SVN versions.  I'd test it, but today's SVN of x264 is broken when using -threads > 1.  Instead I'll list the command changes.

Ubuntu ffmpeg command (equivalent SVN command):
-bt 200 (-bt 200k)
-max_b_frames (-bf)
-max_qdiff (-qdiff)
-i_quant_factor (-i_qfactor)
-b_quant_factor (-b_qfactor) *not required since the script isn't using b-frames
-rc_max_rate 1500 (-maxrate 1500k)
-rc_buffer_size 244 (-bufsize 244k)

I think that should do it.

---

### Post by jdong on 2007-04-06
Hmm I'll throw together a quick bzr branch making those substitutions, and we'll see where that takes us.

**UPDATE**: 

I added the -subq 1 -> -subq 6 optimization to the main pypodconv script at: [http://web.mit.edu/jdong/www/pypodconv/](http://web.mit.edu/jdong/www/pypodconv/)

I started making the changes you described for ffmpeg svn in a bzr branch at [http://web.mit.edu/jdong/www/pypodconv.ffmpegsvn/](http://web.mit.edu/jdong/www/pypodconv.ffmpegsvn/)

(Both directories linked are branchable bzr repositories.) I'm pretty sure I'm missing something in the ffmpeg SVN script, I tried to make as many of the changes as I remembered were needed, but can't guarantee I got them all. At the moment I don't have a ffmpeg SVN copy to test, so if someone can test out H.264, xvid, and mpeg4 codecs, that'd be great :)

---

### Post by FakeOutdoorsman on 2007-04-07
Success!  The threads issue was resolves and I was able to test the basic operation of the script and it worked fine in SVN ffmpeg and x264.  I haven't tested for xvid or mpeg4 yet, but I'll try to do that later today.

One question, why not just use "-threads auto"?  Probably really doesn't matter.

From the helpful [14.5. Encoding with the x264 codec]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-x264.html"):
threads: This option allows to spawn threads to encode in parallel on multiple CPUs. You can manually select the number of threads to be created or, better, set threads=auto and let x264 detect how many CPUs are available and pick an appropriate number of threads. If you have a multi-processor machine, you should really consider using it as it can to increase encoding speed linearly with the number of CPU cores (about 94% per CPU core), with very little quality reduction (about 0.005dB for dual processor, about 0.01dB for a quad processor machine).

---

### Post by jdong on 2007-04-07
(1) Didn't know it existed
(2) Wanted users to be able to override it via the cmdline anyway

IIRC auto picks 1.5x CPU's anyway, like us. At least that was the recommended # stated in the x264 SVN commit that added the new threading.

---

### Post by FakeOutdoorsman on 2007-04-08
I was able to do some more testing using the basic operations:

**x264**
Complains that "width or height not divisible by 16 (320x212), compression will suffer."  Should the size be 320x240?  The source is dv video 720x480 non-square pixels.

**mpeg4 and xvid**
Script is using -b 200 instead of -b 200k

**mpeg4** (after changing -b 200 to -b 200k)
[mpeg4 @ 0x84809b0]rc buffer underflow
[mpeg4 @ 0x84809b0][lavc rc] Error: bitrate too low for this video with these parameters.
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

I tried 200k and 512k and got the above messages for mpeg4 encode and was able to remove those messages and get a working video when I increased bitrate to 768k.  I don't know why those errors are showing up.

---

### Post by jdong on 2007-04-08
> **FakeOutdoorsman said:**
> I was able to do some more testing using the basic operations:

**x264**
Complains that "width or height not divisible by 16 (320x212), compression will suffer."  Should the size be 320x240?  The source is dv video 720x480 non-square pixels.

320x212 is an aspect-ratio-scale down to 320xNNN.... 320x240 would lose the aspect ratio... What really needs to be done is:

(A) Add to or subtract from the smaller dimension until it is a factor of 16
(B) Find an integer number of width less than 320 that produces a height divisible by 16

A is the easiest, but it'll stretch/shrink an image by 8 pixels max (to the nearest 16), but B is more complex..

In the end, the 'lost compression' is a useless set of null bits from 212 to the nearest multiple of 16. I don't think it's a terribly big deal.

> 
**mpeg4 and xvid**
Script is using -b 200 instead of -b 200k


I pushed out a new version that fixes -b %s to -b %sk

---

### Post by FakeOutdoorsman on 2007-04-08
I think dv video might be tricky for the script because of it's non-square, rectangular pixels.  If it is resized to 320x212 then it looks horizontally squished on a computer or other square pixel viewer, but if it is resized to 4:3, such as 640x480 or 320x240, then it looks normal.  I also resize widescreen (16:9) dv to 320x176 for ipod.

Thanks for updating the script!

---

### Post by jdong on 2007-04-08
> **FakeOutdoorsman said:**
> I think dv video might be tricky for the script because of it's non-square, rectangular pixels.  If it is resized to 320x212 then it looks horizontally squished on a computer or other square pixel viewer, but if it is resized to 4:3, such as 640x480 or 320x240, then it looks normal.  I also resize widescreen (16:9) dv to 320x176 for ipod.

Thanks for updating the script!
You mean DV pixels aren't square? Hmm that would be a tough one :-/

---

### Post by drworm01 on 2007-04-08
> **jdong said:**
> You mean DV pixels aren't square? Hmm that would be a tough one :-/

Could that be an issue of cropping? And is there a way to handle cropping in pypodconv? I'm trying to encode movies for the Internet Archive and some of the mpeg2's I have are 640x480 but also widescreen (so unnecessary black pixels all along the top and bottom). Is there a way to crop them out in the encoding process or do I have to do that before hand?

Also, I haven't used pypodconv yet. I'm trying the ipodvideoenc from the wiki. Initially it wouldn't work because aac didn't work (I didn't have faac installed). Should the batch download/configure commands be edited to include that?

I want to say though that I'm very happy with these guides. So helpful. The more I use Ubuntu and Linux, the more I love the command line. So thank you for the guide, the script and for giving me one less thing I need XP to do for me. Thank you so much.

---

### Post by drworm01 on 2007-04-08
Just tried pypodconv and got this output: 
```
user@user-desktop:~/Desktop$ pypodconv -i Horrors_of_Spider_Island.mpeg -o Horrors_of_Spider_Island.mp4
Traceback (most recent call last):
  File "/usr/local/bin/pypodconv", line 160, in ?
    enc=AVEncoder(options.input,options.output,options.maps)
  File "/usr/local/bin/pypodconv", line 36, in __init__
    self.resolution=parseVideoInfo(input_file,maps)
  File "/usr/local/bin/pypodconv", line 87, in parseVideoInfo
    streamno=int(line.split()[1][:-1].split('.')[-1].strip('(und)')) #Gets the stream number, i.e. Stream #0.X
ValueError: invalid literal for int(): 0[0x1e0]

```

Where am I going wrong?

---

### Post by jdong on 2007-04-08
> **drworm01 said:**
> Just tried pypodconv and got this output: 
```
user@user-desktop:~/Desktop$ pypodconv -i Horrors_of_Spider_Island.mpeg -o Horrors_of_Spider_Island.mp4
Traceback (most recent call last):
  File "/usr/local/bin/pypodconv", line 160, in ?
    enc=AVEncoder(options.input,options.output,options.maps)
  File "/usr/local/bin/pypodconv", line 36, in __init__
    self.resolution=parseVideoInfo(input_file,maps)
  File "/usr/local/bin/pypodconv", line 87, in parseVideoInfo
    streamno=int(line.split()[1][:-1].split('.')[-1].strip('(und)')) #Gets the stream number, i.e. Stream #0.X
ValueError: invalid literal for int(): 0[0x1e0]

```

Where am I going wrong?

Congratulations, I think you found a bug in pypodconv :)

Can you post the output of "ffmpeg -i Horrors_of_spider_island.mpeg"?

---

### Post by drworm01 on 2007-04-08
> **jdong said:**
> Congratulations, I think you found a bug in pypodconv :)

Yay! I win!

> Can you post the output of "ffmpeg -i Horrors_of_spider_island.mpeg"?

Here is is:

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-libogg --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-x264 
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Apr  8 2007 02:23:51, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
Input #0, mpeg, from 'Horrors_of_Spider_Island.mpeg':
  Duration: 01:14:41.9, start: 39647.575578, bitrate: 3178 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480, 8000 kb/s, 29.97 fps(r)
  Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, 192 kb/s
Must supply at least one output file

```

The file comes from a DVD > MPEG2 PS transcode in VLC.

---

### Post by jdong on 2007-04-08
Ok, I've fixed that bug in both branches. Please let me know if that works :)

---

### Post by drworm01 on 2007-04-09
The new version produced a successful encode and it looks great. Thanks!

---

### Post by drworm01 on 2007-04-12
I have a new issue now with cropping. I'm trying to convert a video with tons of black space all around it so I went into the bash file and added
```
-croptop 72 -cropbottom 52 -cropleft 10 -cropright 38
```
just before the -s command and changed -s to 320x192. So now the code looks like this:
```
ffmpeg -y -i "$1" -v 1 -threads 1 -vcodec h264 -b 768 -bt 175 -refs 2 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -partb8x8 1 -me full -subq 6 -brdo 1 -me_range 21 -chroma 1 -slice 2 -max_b_frames 0 -level 13 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 35 -max_qdiff 4 -i_quant_factor 0.71428572 -b_quant_factor 0.76923078 -rc_max_rate 768 -rc_buffer_size 244 -cmp 1 -croptop 72 -cropbottom 52 -cropleft 10 -cropright 38 -s 320x192 -acodec aac -ab 128 -ar 48000 -ac 2 -f mp4 -pass 1 "$2"
```
This produces an mp4 with all the surrounding black parts removed, but when I try to play it back in Totem, MPlayer or VLC, it's stretched to fill the screen. When I hit "Properties" on the file itself, it says it's 320x192. When I try to run the conversion through pypodconv, obviously I don't get the option to input the cropping details, but I get the same output-a fully-cropped mp4 that's stretched to fill the screen.
So my question is first, does the problem lie in some unknown display setting on my computer or is it a problem with the file. And second, how do I solve the problem whatever its source?
Finally, does pypodconv and the bash have an auto-crop function built-in? If so, it's doing one hell of a job. The edges are sharp and don't go too far. It really nails it. Obviously I'd like that to be an adjustable option, but it's hard to find complaint when the built-in version works so well.
Thanks for your time.

---

### Post by jdong on 2007-04-12
I am by no means a video expert (in fact I am quite clueless :D), but I think there's something called a "SAR" that stores the original aspect ratio, and will always attempt to maintain that aspect ratio, unless you override it as 1:1. I'm not sure exactly how to do that.

---

### Post by FakeOutdoorsman on 2007-04-12
This is confusing and I don't get it either.  I tried to read some info the Transcode Wiki. Start with [Aspect Ratio]("http://www.transcoding.org/cgi-bin/transcode?Aspect_Ratio").  Next read [Calculating Frame Size And Aspect Ratio]("http://www.transcoding.org/cgi-bin/transcode?Calculating_Frame_Size_And_Aspect_Ratio").  So it all depends on your source, how much you crop, your final encoded size, your container format, your decoder, and finally what you watch the video on.  Head...hurts.

You can set the aspect ratio in ffmpeg with:
-aspect aspect      set aspect ratio (4:3, 16:9 or 1.3333, 1.7777), ex: -aspect 4:3

---

### Post by jdong on 2007-04-12
Hmm, do you think we can solve our square/rectangular pixel issue via this -aspect flag?

If you have "rectangular pixel" DV-videos, can you get ffmpeg -i output for them? I want to see if there's something we can parse from ffmpeg output to detect non-square pixels.

---

### Post by FakeOutdoorsman on 2007-04-12
Here is the output from a DV file:
```
ffmpeg -i safetyladder.avi 
Input #0, avi, from 'safetyladder.avi':
Duration: 00:01:15.5, start: 0.000000, bitrate: 30313 kb/s
Stream #0.0: Video: dvvideo, yuv411p, 720x480, 29.97 fps(r)
Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
```

Standard definition DV is always 720x480 and ffmpeg always lists the format as **dvvideo**.

I simpily just resize to 640x480 or 320x240 from dv which makes the SAR 1:1 to fit a computer or ipod and don't even mention -aspect.  I never used ffmpeg to encode a vob, but I bet resizing it to 640x480, 320x240 would work too.

I just mentioned the ffmpeg -aspect command since I thought it might be useful with a cropped, odd sized video like drworm01 is using.

---

### Post by jdong on 2007-04-12
Hmm, ffmpeg does not output any information that would hint at rectangular pixels... Perhaps I should add a manual override flag for resolution.

---

### Post by drworm01 on 2007-04-13
> **FakeOutdoorsman said:**
> I simply just resize to 640x480 or 320x240 from dv which makes the SAR 1:1 to fit a computer or ipod and don't even mention -aspect.  I never used ffmpeg to encode a vob, but I bet resizing it to 640x480, 320x240 would work too.

That's the odd part. I tried encoding with no cropping at all. I set the resize to 320x240 and came out with a file that had removed all the surrounding black and stretched the remaining image into the 4:3 ratio anyway. It's also odd that the file properties say it has the assigned pixel ratio (320x192 when encoded with the crop command). So it seems ffmpeg is auto-cropping the file and then stretching the remaining pixels to a 4:3 ratio. I'll try the -aspect command and see what that does. 320x192 works out to 5:3. 16:9 would be 320x180 which is close, but I'll see how much leeway ffmpeg gives me. Also wonder if I should set -aspect to the original input aspect ratio (4:3) or to the desired output's (5:3 or as close to 16:9 as I can get).

---

### Post by FakeOutdoorsman on 2007-04-13
I didn't think ffmpeg does any sort of autocropping.  What is your source?  Maybe your source video doesn't have the surrounding blackness and your player is just adding them.

---

### Post by drworm01 on 2007-04-14
No, the source has them. It's a 4:3 movie from one of those cheap-o 50-Movie Packs. There's actually the movie in widescreen, a dark black outline around that and a slightly less dark outline filling the rest of the screen. I don't know where the cropping was coming from-native to ffmpeg, some command in the bash/pypodconv-but it was doing it without any intervention on my part.
BUT! The -aspect command worked. I kept the cropping commands in and tried -aspect 4:3 (the video's original aspect ratio). The output while it was encoding featured SAR: 4/5. I have no idea what that means. The video, though, came out 4:3, cropped and stretched. I tried again, this time with -aspect 5:3 (320x192) with all the cropping details and it worked! The output said SAR: 1:1, which it had said before, but this time it stuck to it throughout. So thank you all so much for the help. It feels so good to finally have that working.

---

### Post by jdong on 2007-04-14
Interesting... I wonder if we can work out a sanity check for pypodconv... such that it will enforce a 1:1 SAR and abort or recover if that is not the case (the iPod AFAIK can only display SAR 1:1 undistorted)

---

### Post by jariy on 2007-04-21
Whoa! What a great script! I can confirm that these videos work also in Nokia N95. Well, the phone doesn't show preview images, but the video plays fine.

---

### Post by thojo on 2007-05-15
Been using your pypodconv script and it works great for the most part. On some videos, its sometimes adds an additional 30 minutes of unsync'd video and sound to the end.

---

### Post by ephman on 2007-05-19
hi,

i installed prevu from the instructions on the board and it didn't have any errors.  then i followed the instructions to a t in this posting, and get this error below.  my search for a solution didn't find anything.  any help would be really appreciated.

thanks for the bandwidth,
ephman

> FSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE    -c -o x264.o x264.c
x264.c: In function 'X264_init':
x264.c:147: error: 'struct <anonymous>' has no member named 'i_rf_constant'
make[2]: *** [x264.o] Error 1
make[2]: Leaving directory `/var/cache/prevu/src/11978/ffmpeg-0.cvs20060823/libavcodec'
make[1]: *** [lib] Error 2
make[1]: Leaving directory `/var/cache/prevu/src/11978/ffmpeg-0.cvs20060823'
make: *** [build-stamp] Error 2
Copying back the cached apt archive contents
 -> unmounting /var/cache/prevu/src/11978 filesystem
 -> unmounting /var/cache/prevu/feisty-debs filesystem
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> cleaning the build env 
    -> removing directory /var/cache/prevu/builds/12084 and its subdirectories
Traceback (most recent call last):
  File "/usr/bin/prevu", line 175, in <module>
    BackportFromDsc(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 115, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 96, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 44, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
OSError: [Errno 2] No such file or directory

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/prevu", line 175, in <module>
    BackportFromDsc(sys.argv[1],DIST).backport()
  File "/usr/bin/prevu", line 115, in backport
    self.do_compile()
  File "/usr/bin/prevu", line 96, in do_compile
    raise ValueError("Build failed.")
ValueError: Build failed.
ephman@wintermute:~$ 



---

### Post by ephman on 2007-05-22
bumpy?  any help with the above post?  

on a side note in the meanwhile i'm using avidemux, but i'd rather a quick one line command.

thanks for the bandwidth,
ephman

---

### Post by GMaq on 2007-05-23
Hi,
 Excellent script!! Wondering about how it handles Telecining and if deinterlacing could be added as an option. If your source is 23.976fps then it's no biggie, However 29.97fps should be de-interlaced, and I can do it in the ffmpeg commandline (-deinterlace) but your script is far preferable with the mp4Box workaround. I am a Linux and Terminal newbie so forgive me if I'm asking for the world here! Thanks for your time, and again excellent work!

---

### Post by FakeOutdoorsman on 2007-07-20
The pypodconv doesn't work with ffmpeg SVN because some parameters have changed again:
-vcodec h264 is now -vcodec libx264
-acodec aac is now -acodec libfaac

I guess I could subscribe to their mailing list to keep up to date with their changes, but they might not even mention it.

---

### Post by jdong on 2007-07-20
Oh those freaks! I'll update the bzr branches... soon.

---

