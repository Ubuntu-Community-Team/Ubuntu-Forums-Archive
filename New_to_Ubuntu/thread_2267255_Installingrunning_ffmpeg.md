---
title: "Installing/running ffmpeg"
date: 2015-02-28
forum: New to Ubuntu
---

### Post by will65 on 2015-02-28
I want to be able to record decent videos and upload them to Youtube (after a bit of editing). So far I've tried SimpleScreenRecorder, Kazam, and Record my Desktop. All produced sub-standard videos in comparison to Bandicam and Fraps running on Windows 7 on the same machine.

ffmpeg looks like it might be a decent alternative, but as with everything on Ubuntu it seems frustratingly difficult to get working. I've tried [this]("http://ubuntuforums.org/showthread.php?t=2219550&p=13101922#post13101922") and [this]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu"), as well as downloading a static build from [here]("http://johnvansickle.com/ffmpeg/") (but the executable won't launch with vine)... 

All I want to do today is make one short video before I have to go back to being a teacher and marking and planning lessons all Sunday. On Windows I would have installed something hours ago without any hassle, and I feel like whenever I boot up Ubuntu I'm quite literally wasting all my spare time. Can someone please provide me with very simple instructions to get it working (or provide a good alternative) before I start tearing my hair out?

---

### Post by sandyd on 2015-02-28
> **will65 said:**
> I want to be able to record decent videos and upload them to Youtube (after a bit of editing). So far I've tried SimpleScreenRecorder, Kazam, and Record my Desktop. All produced sub-standard videos in comparison to Bandicam and Fraps running on Windows 7 on the same machine.

ffmpeg looks like it might be a decent alternative, but as with everything on Ubuntu it seems frustratingly difficult to get working. I've tried [this]("http://ubuntuforums.org/showthread.php?t=2219550&p=13101922#post13101922") and [this]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu"), as well as downloading a static build from [here]("http://johnvansickle.com/ffmpeg/") (but the executable won't launch with vine)... 

All I want to do today is make one short video before I have to go back to being a teacher and marking and planning lessons all Sunday. On Windows I would have installed something hours ago without any hassle, and I feel like whenever I boot up Ubuntu I'm quite literally wasting all my spare time. Can someone please provide me with very simple instructions to get it working (or provide a good alternative) before I start tearing my hair out?
Ubuntu now uses libav (which is a fork of ffmpeg) over ffmpeg. FFmpeg will return in Ubuntu 15.04.
```

sudo apt-get install libav-tools
```
Use
```

avconv -video_size 1366x768 -framerate 30 -f x11grab -i :0.0 -vcodec libx264 -threads 4 -f alsa -ac 2 -i pulse output.avi
```

Change 1366x768 to your screen resolution and threads to the number of CPUs you have (including HT)

Side note: If you have mulitple monitors, the part after "-i" will have to be fiddled with as well, as this records screen 0 by default.

Side note #2: For future people who find this and are now using Ubuntu 15.04, FFmpeg has returned! Use ffmpeg instead of avconf. This probably goes for anyone whose using the beta as well.

---

### Post by will65 on 2015-02-28
```

avconv -video_size 1366x768 -framerate 30 -f x11grab -i :0.0 -vcodec libx264 -threads 4  output.avi
```

Thanks sandyd, I'll try this out tonight. Do I paste this into the terminal? Also where will it save the video files to?

---

### Post by sandyd on 2015-02-28
> **will65 said:**
> ```

avconv -video_size 1366x768 -framerate 30 -f x11grab -i :0.0 -vcodec libx264 -threads 4  output.avi
```

Thanks sandyd, I'll try this out tonight. Do I paste this into the terminal? Also where will it save the video files to?

This saves the video file to where your terminal is currrently.
You can determine that by running
```
pwd
```

By default, the terminal should open at your home folder.

You can change the location, i.e.
```

avconv -video_size 1366x768 -framerate 30 -f x11grab -i :0.0 -vcodec libx264 -threads 4  -f alsa -ac 2 -i pulse ~/output.avi
```

Will force the output to your home folder instead of wherever in the filesystem you have browsed to.

---

### Post by FakeOutdoorsman on 2015-02-28
> **will65 said:**
> ffmpeg looks like it might be a decent alternative, but as with everything on Ubuntu it seems frustratingly difficult to get working. I've tried [this]("http://ubuntuforums.org/showthread.php?t=2219550&p=13101922#post13101922") and [this]("https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu"), as well as downloading a static build from [here]("http://johnvansickle.com/ffmpeg/") (but the executable won't launch with vine)

The PPA you used provides ancient builds, and I'm not sure if it supports x11grab. I know the static build does not support x11grab. [mc4man's PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) might, but I'm unsure. Using his PPA would currently be the easiest method if it does support x11grab.

You followed the compile guide? In what way did it not work for you? (Sorry, but I'm not sure what vine is).

---

### Post by mc4man on 2015-02-28
> **FakeOutdoorsman said:**
> The PPA you used provides ancient builds, and I'm not sure if it supports x11grab. I know the static build does not support x11grab. [mc4man's PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) might, but I'm unsure. Using his PPA would currently be the easiest method if it does support x11grab.

You followed the compile guide? In what way did it not work for you? (Sorry, but I'm not sure what vine is).
The ffmpeg build there is/will be a static build using latest ffmpeg release. (currently 2.5.4
It isn't explicitly configured for x11grab but it's enabled via xcbgrab. So commands remain the same, ie. -f x11grab ect.

(-I've also a shared versions of 2.5.4 release  & 2.5.4+git  elsewhere where some apps have been redone to use the shared libs, what happens when the next *major* release occurs not decided yet, probably keep going to some extent .

---

### Post by sandyd on 2015-02-28
Updated post above to clarify and reflect movement to libav from ffmpeg

---

### Post by will65 on 2015-02-28
> **FakeOutdoorsman said:**
> The PPA you used provides ancient builds, and I'm not sure if it supports x11grab. I know the static build does not support x11grab. mc4man's PPA might, but I'm unsure. Using his PPA would currently be the easiest method if it does support x11grab. 
 
You followed the compile guide? In what way did it not work for you? (Sorry, but I'm not sure what vine is). 
 
Sorry, meant Wine, not vine. Half asleep today. 
 
I followed the guide correctly as far as I could. I copied and pasted each individual code box into the terminal, hit enter and then give it my password. Ubuntu installed all the libraries in turn, and then compiled ffmpeg. Then came the 'conclusion' section of the guide. For new users, it might as well be written in Swahili. Navigate to where? Execute how exactly? Or you can use the full path (huh?) to the binary (come again?). The Ubuntu/Linux community seem really great at replying quickly to my questions and being helpful, but I feel like I'm doing my physics degree again and the professor is only writing every third line of a derivation and just assuming I know how he reached the next step...

Anyway, I tried using libav as you suggested sandyd. It produces nice small files but they completely lack sound and they're really choppy, almost as though it's only recording every other frame. That's a bit odd considering that it's set for 30 fps :/

---

### Post by sandyd on 2015-02-28
> **will65 said:**
> Sorry, meant Wine, not vine. Half asleep today. 
 
I followed the guide correctly as far as I could. I copied and pasted each individual code box into the terminal, hit enter and then give it my password. Ubuntu installed all the libraries in turn, and then compiled ffmpeg. Then came the 'conclusion' section of the guide. For new users, it might as well be written in Swahili. Navigate to where? Execute how exactly? Or you can use the full path (huh?) to the binary (come again?). The Ubuntu/Linux community seem really great at replying quickly to my questions and being helpful, but I feel like I'm doing my physics degree again and the professor is only writing every third line of a derivation and just assuming I know how he reached the next step...

Anyway, I tried using libav as you suggested sandyd. It produces nice small files but they completely lack sound and they're really choppy, almost as though it's only recording every other frame. That's a bit odd considering that it's set for 30 fps :/
Odd,
works fine here with nvidia card. What video card are you using? Are there any video drivers installed?

Can you post the output of the command when your running it - should have some diagnostics stuff.

Meanwhile, I have added audio to the above commands.

---

### Post by FakeOutdoorsman on 2015-02-28
> **will65 said:**
> Sorry, meant Wine, not vine. Half asleep today.
How is Wine involved here? Are you attempting to make a screencast of something you're running in Wine? 
 
> **will65 said:**
> Then came the 'conclusion' section of the guide. For new users, it might as well be written in Swahili.
Maybe I'll try to simplify that section sometime soon. However, that section can be skipped. Basically it is (attempting) to instruct a user how the new ffmpeg (the "binary") that was compiled can be accessed and used. There are three main ways you can do that:

**Option 1**
Navigate to the directory containing the new ffmpeg and run it. The guide places the new ffmpeg in "/home/will65/bin". So you would run (notice the **./**):
```
cd /home/will65/bin
./ffmpeg -i input output
```

**Option 2**
Use the full path. The full path is the long-form way of telling the terminal where something is located. Example:
```
/home/will65/bin/ffmpeg -i input output
```

**Option 3**
Put it in a location that the terminal will automatically look for it when you simply enter "ffmpeg" (run "echo $PATH" to view where it will look). "/home/will65/bin" is one of those default locations in stock Ubuntu, but for some reason sometimes you have to refresh it once after compiling for it to notice. That's what the "hash -r" and ". ~/.profile" commands in the guide are for. Alternatively you could log out and log in.

> **will65 said:**
> Anyway, I tried using libav as you suggested sandyd. It produces nice small files but they completely lack sound and they're really choppy, almost as though it's only recording every other frame. That's a bit odd considering that it's set for 30 fps :/
A satisfactory result can depend on many factors including the complexity of your input, available system resources, your encoding options, the specific encoder you're using, how ffmpeg was compiled, how old your ffmpeg is, and your hardware. (I'm referring to ffmpeg here; I'm not an avconv user). Even if the output is perfect whatever you use to decode it may not be able to do it properly.

> **sandyd said:**
> works fine here with nvidia card. What video card are you using?
The card type won't matter in this case unless the card and ffmpeg build supports NVENC (I don't think Libav does at all). Recording games might actually be a good use case for it, but I don't really know and I've never tried it. Also, x264 can utilize some OpenCL stuff, but that's not really worth the time or effort according to my tests ages ago.

---

### Post by will65 on 2015-03-01
> **sandyd said:**
> Odd, 
works fine here with nvidia card. What video card are you using? Are there any video drivers installed? 
 
I'm using a GeForce 560ti. Using the proprietary Nvidia 331.113 drivers that seem to be the most stable. On a side note, after installing a driver ppa when I first put Ubuntu on my machine a week ago, I've lost the 'tested' driver option. Is there anyway to get that back? I was trying to get the very latest Nvidia drivers at the time but I'm starting to think that the tested ones would have been more stable. 
 
> Can you post the output of the command when your running it - should have some diagnostics stuff. 
 
Meanwhile, I have added audio to the above commands. 
 
Just tried the updated command to add audio and now instead of capturing very crisp frames but with very low framerate, now the framerate is OK, but every frame is either terribly pixelated or very low resolution (it's hard to tell which) and there's still no audio.

This is what the terminal is outputting while recording (I only copied the last few lines, but there's a constant stream of those non-monotonous DTS messages):

> Non-monotonous DTS in output stream 0:1; previous: 1606, current: 1536; changing to 1607. This may result in incorrect timestamps in the output file.
Non-monotonous DTS in output stream 0:1; previous: 1607, current: 1537; changing to 1608. This may result in incorrect timestamps in the output file.
frame=  924 fps= 25 q=31.0 Lsize=    7271kB time=36.92 bitrate=1613.3kbits/s    
video:6663kB audio:538kB other streams:0kB global headers:0kB muxing overhead: 0.966396%
Received signal 2: terminating.
 
> **FakeOutdoorsman said:**
> How is Wine involved here? Are you attempting to make a screencast of something you're running in Wine? 
 
Probably more to do with my own partial understanding of what I was being directed to do. I know Wine allows programs written for Windows to run in Ubuntu. I assumed that somewhere in the folders created by following the guide there'd be the equivalent of a .exe file. A few files looked as though they'd open with Wine (they had the purple diamond Wine application icon), but I couldn't figure out how. 

I still can't get your instructions to work though. I'm guessing that the installation was bad, or it's not placed it where you expected it to. When I put this code into the terminal (here's a [screenshot]("http://i.imgur.com/TrmCYBy.png")), it just tells me "there's no such file or directory":

```
cd /home/will/bin
./ffmpeg -i input output
```

On a side note, doesn't anyone write complete programs with installers for things in Linux? I'm not too lazy to search for instructions and teach myself how to do things, but I work at 60 hour week and only have Saturdays to muck around on my PC, and I spent all yesterday pissing around in Ubuntu and getting very frustrated because people don't write clear instructions for newbs. I'm getting very close to just calling it a day and deleting the Ubuntu partition. It's no wonder people use Windows when it takes a new user literally days to install something as innocuous as screen capture program in Linux. I had Bandicam installed and working in minutes on Windows 7. The only reason I'm even bothering really is because Kerbal Space Program uses Unity, which is only stable as a 32 bit program on Windows and limits RAM usage. Seriously, things shouldn't be this difficult. You shouldn't have to copy and paste dozens of command lines into terminal just to install something that can't be found in Software Centre. No one is ever going to challenge Microsoft as long as the alternative is this.

---

### Post by FakeOutdoorsman on 2015-03-01
> I still can't get your instructions to work though. I'm guessing that the installation was bad, or it's not placed it where you expected it to.
Looks like there is no bin directory, so you must have encountered an issue.

> On a side note, doesn't anyone write complete programs with installers for things in Linux?
That's what apt-get, the Software Center, and synaptic are for. They all basically do the same thing, but it is nice to have options.

> getting very frustrated because people don't write clear instructions for newbs.
I found out that writing instructions that anyone can follow is challenging.

> You shouldn't have to copy and paste dozens of command lines into terminal just to install something that can't be found in Software Centre.
I agree. The lack of ffmpeg in the Software Center was a result of political shenanigans that ended up hurting the users.

> No one is ever going to challenge Microsoft as long as the alternative is this.
Linux isn't for everyone. Also, you were compiling which is an advanced task...and try doing that in Windows (I wouldn't know how). Anyway, if Linux is frustrating to you and Windows suits you better then I recommend you stay with Windows. Don't take it as an insult because it isn't. Personally, I often end up in a monkey-rage when I use Windows because I feel like it attempts to control me instead of the other way around, so I tend to avoid it.

If you want to continue with Ubuntu and ffmpeg then I believe your best course of action is to use [mc4man's PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media). Perhaps someone can provide the easiest, friendliest method to enable that and install ffmpeg from the PPA. I only know how to do it from the terminal but I assume you're tired of installing via that. If you get that far then I can provide some example commands.

Or you can keep on trying with avconv from the repo, but so far it seems crappy.

---

### Post by mc4man on 2015-03-01
While I wouldn't dissuade you from using ppa or ffmpeg or avconv you may be better off seeing if you can get a decent recording in a gui. In that case simplescreenrecorder is quite fine, actually does audio better than anything else I've tried.
Most likely your issue is you may not have enough resources or cpu power to do whatever & record/encode at same time. (at least in linux or linux/wine

Maybe try some of the various presets in ssr, start with "ultrafast" & test with various crf values or try crf at  0

To use that ppa you go to the ppa page & read some of the warning before adding/using. (in most cases a dist-upgrade is best option.. to do upgrades

---

