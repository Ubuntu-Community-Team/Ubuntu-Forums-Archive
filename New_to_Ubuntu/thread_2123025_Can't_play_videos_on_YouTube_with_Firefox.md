---
title: "Can't play videos on YouTube with Firefox"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by POworker62 on 2013-03-06
Are there drivers I need to load for Firefox to play videos on YouTube?  I get a black screen with a spinning circle.
Also Movie Player doesn't work either! :(

---

### Post by mamamia88 on 2013-03-06
Do you have flash installed?

---

### Post by hawthornso23 on 2013-03-06
You need to install the flashplugin to play flash on firefox. There is a firefox extension called "Flash Aid" that will install the best linux flash plugin it can find for you automatically. 
Alternatively if you just want to watch youtube, you could join their HTML5 beta program. HTML5 is set to replace flash in the near future - at least as far as watching videos is concerned. A third option is to switch from firefox to chrome (or chromium if you want the unbranded version). Google signed a sweetheart deal with Adobe which means chrome has better flash support than firefox these days.

---

### Post by siddharth007 on 2013-03-07
Get the firefox extension "Flash Aid".As for the movie player,you might need to install some plugins to play the files.For this,try opening any video file with the movie player.You will automatically be notified that you need to download the plugins to play the file.You can download the plugins then.

---

### Post by MightyOtis on 2013-03-07
I'm having the same problem the OP is having.  Please forgive me if I'm not allowed to chime in here, but this is my first post in these forums and this thread seems like the best place to comment on this particular issue.

In a nutshell, my concern is whether or not there might be a hardware issue for all of those of us struggling with this problem.  I know it's complex, due to the unwillingness of Adobe to cooperate with the Linux community, but is there also an issue with the nVidia drivers?  I'm seeing a lot of information that indicates there is, but rolling back the drivers hasn't had any effect on my machine.

I just put a fresh install of 12.04.2 LTS Desktop on an Athlon 2500 XP platform PC with an nVidia GeForce2 MX/MX 400 graphics card, and try as I might I can NOT get YouTube videos to play on either Flash OR Chrome.  I've been researching this for weeks, trying all kinds of things (including Flash Aid), and have gotten nowhere.  No matter what I do, when I pull up a YouTube video in Firefox I get a white screen where the video should be.  Sometimes if I mouse over it I can get it to turn black, but nothing ever plays.  If I use Chrome instead, I get the message that Flash needs to be installed.  So I go through the steps to install it and go back to the video but it STILL won't play.  I just don't get it.

Oh, and both Chrome and Firefox offer me the option of viewing the videos in HTML5, but when I try to do that I get some message about MIME type not found.  Another dead end.

I've been in the PC world for over 30 years, but am a total Linux noob.  Any help and/or explanations will be welcomed.

---

### Post by POworker62 on 2013-03-07
Well I've installed "Flash Aid" and that didn't help. Can't see anything with HTML5 either!!! Everything worked well under the last version of Ubuntu I had (10 something) Now this upgrade 12.04 is giving me a hard time.  I'll get it working sooner or later though....

---

### Post by craig10x on 2013-03-07
Did you install "ubuntu restricted extras" from the software center?   That gives you all the codecs, flash, etc that you need...

Google Chrome (which you can get as a deb file from their website) is a nicer browser and it also has it's own flash and even a built in pdf reader...download it, right click and select "install with software center"...
But either way, you should make sure you get the restricted extras package...

---

### Post by arpanaut on 2013-03-07
@MightyOtis the Athlon 2500 does not support sse2 which is necessary for using newer flash releases.
You will need to downgrade to an older flash version.
See this thread that has ways to do that.  [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

You can find out if your processor supports sse2 by running in the terminal (ctrl+alt+t) ```
cat /proc/cpuinfo
```

hope this helps.

---

### Post by MightyOtis on 2013-03-07
> **arpanaut said:**
> @MightyOtis the Athlon 2500 does not support sse2 which is necessary for using newer flash releases. You will need to downgrade to an older flash version. See this thread that has ways to do that.  [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)  You can find out if your processor supports sse2 by running in the terminal (ctrl+alt+t) ```
cat proc/cpuinfo
```  hope this helps.  

@arpanaut: THANK YOU!  This was what I was looking for.  I tried **cat proc/cpuinfo** but it told me there was no such file or directory.  

I'm hot on the downgrade tip, however.  I've already downloaded Flash version 11.1.102.63 as the link you gave me specified, but when I went to copy the .so file into the plugins directory (~/.mozilla/plugins/) there wasn't any plugins directory and the extensions directory was empty - so I created the plugins directory and stuck the file in there.    

When I do about:plugins in Firefox it shows Shockwave Flash 11.2r202 at /usr/lib/flashplugin-installer/libflashplayer,so AND Shockwave Flash 11.1r102 at /usr/lib/mozilla/plugins/libflashplayer.so.  Don't know what to make of any of that, but it doesn't look good to me.  My first impulse is to copy the libflashplayer.so from version 11.1.102.63 into /usr/lib/flashplugin-installer/, but I don't want to mess anything up....

_UPDATE_: I tried copying the libflashplayer.so from version 11.1.102.63 into /usr/lib/flashplugin-installer/, but that didn't work.  So I used Flash-Aid's Advanced Mode and pointed it to 
[http://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz](http://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz) 
instead of downloading the tarball, and restarted Firefox.  Lo and behold, it now works!  After weeks of wrestling with this thing and mountains of research, it works.  Thanks arpanaut.  I owe you one - maybe even two... :)

---

### Post by arpanaut on 2013-03-07
I screwed up I left out the "/" before the proc part of the command, my bad.
It should work by just putting the .so file in the plugins directory you created, have you tried using flash on say youtube?
See also: [http://ubuntuforums.org/showthread.php?t=1983218&p=11951782&viewfull=1#post11951782](http://ubuntuforums.org/showthread.php?t=1983218&p=11951782&viewfull=1#post11951782)

---

### Post by Terry of Astoria on 2013-03-08
Firefox displayed a blank area where the flash content should have been.
Using the advice of darkod, I downloaded the file
[http://github.com/downloads/webgapps...ux.i386.tar.gz]("http://github.com/downloads/webgapps/flashaid/flashplayer11_1r102_63_linux.i386.tar.gz") 
unzipped it and copied the libflashplayer...so file into my /HOME/ME/.mozilla/plugins folder (I had to make the folder myself)
RESTART FIREFOX 
FLASH WORKS
YIPPEE!
THANKS GUYS! (Sorry about all the noise.)

---

### Post by siddharth007 on 2013-03-08
Good that you got it working on Firefox.For the same on google chrome you can follow this [link]("http://www.howtoforge.com/how-to-enable-adobes-flash-player-in-google-chrome-ubuntu-9.04-p2")

---

### Post by Zensailor on 2013-03-09
I saw this in another thread, perhaps another solution?

> **nomenkultur said:**
> _all_ youtube videos are playable in html5


 every single video is available as mp4.

 I don't use flash for security reasons.

 
 If you use internet explorer 10 in windows7 without flash you will notice all videos play flawlessly

 in ubuntu with firefox or chromium you will notice some videos will complain about not being able to play without flash

 e.g.

 [https://www.youtube.com/watch?v=xXIcQaNiy0g](https://www.youtube.com/watch?v=xXIcQaNiy0g)

 now observe how easily we can make it play without flash:

 [https://www.youtube.com/embed/xXIcQaNiy0g](https://www.youtube.com/embed/xXIcQaNiy0g)


 it has nothing to do with flash but everything to do with ads and youtube partners and monetization and google shenanigans

in your channel settings turn off ads and monetization etc etc and your channel will be 100% html5:

[https://www.youtube.com/user/nomenkultur](https://www.youtube.com/user/nomenkultur)

 I haven't used flash in over a year now and everything in my youtube works fine


 also in case you didn't know

[https://www.youtube.com/tv#/browse](https://www.youtube.com/tv#/browse)

---

