---
title: "HOWTO: Totem embeded with mozplugger (At Last!)"
date: 2005-03-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Nis on 2005-03-02
Attached is my mozpluggerrc which can now play embeded movie streams using totem-xine.

Things to know:
- I did this on Hoary so I'm not sure if it will work on Warty (because of the mozplugger version change)
- You need totem-xine and mozplugger (in universe).  You'll also need w32codecs if you want to stream anything using a proprietary codec.
- I set up some audio stream capabilities but I haven't tested it yet (I never listen to embeded audio streams).  If you can test this, please do and report any success or failure.
- Remove the .txt file extension and place as /etc/mozpluggerrc.
- You'll need to remove ~/.mozilla/firefox/pluginreg.dat for mozplugger to recognize the configuration changes.

Have fun. :)

---

### Post by jdodson on 2005-03-02
[QUOTE=Nis]Attached is my mozpluggerrc which can now play embeded movie streams using totem-xine.

Things to know:
- I did this on Hoary so I'm not sure if it will work on Warty (because of the mozplugger version change)
- You need totem-xine and mozplugger (in universe).  You'll also need w32codecs if you want to stream anything using a proprietary codec.
- I set up some audio stream capabilities but I haven't tested it yet (I never listen to embeded audio streams).  If you can test this, please do and report any success or failure.
- Remove the .txt file extension and place as /etc/mozpluggerrc.
- You'll need to remove ~/.mozilla/firefox/pluginreg.dat for mozplugger to recognize the configuration changes.

Have fun. :)[/QUOTE]

i think this should go to the howto section.  if you have no problems with that.

---

### Post by Nis on 2005-03-02
No problems at all.

---

### Post by rapala61 on 2005-03-02
wow.. nice job.. if u had post this yesterday u could have saved from a loot of work.. anyway.. thanks a lot.

---

### Post by amoser on 2005-03-02
You my friend are a freakin genus, I have been trying to do this for weeks, how did you do it?

~Alan

---

### Post by Nis on 2005-03-02
[QUOTE=amoser]You my friend are a freakin genus, I have been trying to do this for weeks, how did you do it?

~Alan[/QUOTE]
 I looked at the default mozpluggerrc and picked apart the mozplugger man page. :)  Really I was just tired of waiting for the Totem mozilla plugin so I decided to try this route.  The big thing was using --toggle-controls flag for Totem; without this the video kept coming out really small.  In reality I'm just happy to contribute back to a community that has been really great. :)

---

### Post by amoser on 2005-03-02
[QUOTE=Nis]In reality I'm just happy to contribute back to a community that has been really great. :)[/QUOTE]

The community thanks you back, I have been waiting for something like this for along time.  Now GNOME is on the same level as KDE (in this area)

~Alan

---

### Post by madzzoni on 2005-03-19
[QUOTE=Nis]Attached is my mozpluggerrc which can now play embeded movie streams using totem-xine.

Things to know:
- I did this on Hoary so I'm not sure if it will work on Warty (because of the mozplugger version change)
- You need totem-xine and mozplugger (in universe).  You'll also need w32codecs if you want to stream anything using a proprietary codec.
- I set up some audio stream capabilities but I haven't tested it yet (I never listen to embeded audio streams).  If you can test this, please do and report any success or failure.
- Remove the .txt file extension and place as /etc/mozpluggerrc.
- You'll need to remove ~/.mozilla/firefox/pluginreg.dat for mozplugger to recognize the configuration changes.

Have fun. :)[/QUOTE]
FINALLY, FINALLY, FINALLY my DELL LapTop plays Video/audio-streaming in Hoary. I just now listen to DK Radio, and it works just like the Mplayerplug-in i use to play it with in Warty!
It's even more cool, because it shows nice effects in the "player address-window" when streaming audio.
A BIG HUG FROM ME!!! My multi-media nightmare is over!!! THANKS for this great Work!!! :D

---

### Post by bored2k on 2005-03-19
Cool.

You will receive a lot of kudos for this ... a lot .

---

### Post by telmo on 2005-03-19
Sweet! I'll give points for this!  :-$

---

### Post by bored2k on 2005-03-19
[QUOTE=telmo]Sweet! I'll give points for this!  :-$[/QUOTE]
 telmo don't say it ! its better if he doesn't know where those 2 points came from !

...oh crap I blew my cover .

---

### Post by bored2k on 2005-03-19
Here are one of the sites where I've tested Nis's method:

Video Stream:
Gamespot.com [windows media video]
Apple.com/trailers [quicktime video]

Audio Stream:
RFI.fr [windows media audio]

So it's all good.
If you think its not working, leave it a little bit, sometimes it will grab a big chunk of the media .

---

### Post by budge on 2005-03-20
Hi All, really new to Linux/Ubuntu but having fun learning and so far this is the best distro I've  tried. Great support and Forum.

My query is obviously about this mozplugger modification that allows embedded media to play in FireFox. Everything works a treat. The only problem I have now is that Real Player video/sound files when accessed via news items on [http://www bbc.co.uk ](http://www bbc.co.uk ).has sound but no video anymore.

Using Hoary by the way.

Anyone else?

Tried to reinstall  RealPlayer using the "How To" guide but still no video, only sound.

Thanks
Paul

---

### Post by snaga on 2005-03-20
[QUOTE=Nis]Attached is my mozpluggerrc which can now play embeded movie streams using totem-xine.
[/QUOTE]

This worked great for video, for which you have my thanks. However, for some reason, I have no audio when streaming. Audio in general works, and I can open a movie from within an embedded totem instance and the audio is fine. But, I can't get audio on any movie that I am streaming.

Any thoughts?

dm

---

### Post by bored2k on 2005-03-20
[QUOTE=snaga]This worked great for video, for which you have my thanks. However, for some reason, I have no audio when streaming. Audio in general works, and I can open a movie from within an embedded totem instance and the audio is fine. But, I can't get audio on any movie that I am streaming.

Any thoughts?

dm[/QUOTE]
 Weird , worked for me .

---

### Post by Nis on 2005-03-20
Concerning no audio, what kind of files are you trying to stream and what files do you play locally?  If you don't have the right codecs for Quicktime, for example, you'll get video but no audio.

Hopefully this howto will be rendered obsolete eventually because the Totem developers have begun actively working again on the [Totem Mozilla plugin](http://bugzilla.gnome.org/show_bug.cgi?id=144937).

---

### Post by snaga on 2005-03-20
[QUOTE=Nis]Concerning no audio, what kind of files are you trying to stream and what files do you play locally?  If you don't have the right codecs for Quicktime, for example, you'll get video but no audio.[/QUOTE]

I suspect this is it. Hopefully I will have time tomorrow to figure it out. thanks.

dm

---

### Post by dangparker on 2005-03-21
Hi!

Thanks for your great work on this....it's gotten me further down the road to gnome nirvana....

One thing I can't figure out though is how to access sites that check for a particular media player installation (like [www.ifilm.com](www.ifilm.com))

It checks my "system configuration" and reports that quicktime and windows media player is not installed (thus no video).

Any idea how to make firefox or mozilla report that these programs are available?

Thanks in advance.

Daniel

---

### Post by occy8 on 2005-03-23
- You'll need to remove ~/.mozilla/firefox/pluginreg.dat for mozplugger to recognize the configuration changes.

I can't find that file 
I'm using Firefox 1.0.1


stupid me worked it out sorry

---

### Post by Michael on 2005-03-30
Oh my god this is simply great! I can even play QuickTime movies!

Thank you thank you thank you :grin:

---

### Post by LongTooth on 2005-03-31
For those of us who are mentally challanged, could someone please put these instructions in a form a moron like me can follow? I've just installed Ubuntu on a test box and I'd like to try this out before I do the same to my main box. Thanks.

---

### Post by Liau on 2005-03-31
Awesome! this worked great :D

Funny thing though, sometimes when I try to open up a windows media stream the image won't show until I pause the stream and restart it. Ah whatever, at least it's working..

---

### Post by bored2k on 2005-03-31
Only *problem* I'm having with this is totem wanting for some reason to play the video with hardly any downloaded data [my xDSL is not as fast as totem wants to stream videos @ times :(] .

---

### Post by Nis on 2005-03-31
[QUOTE=bored2k]Only *problem* I'm having with this is totem wanting for some reason to play the video with hardly any downloaded data [my xDSL is not as fast as totem wants to stream videos @ times :(] .[/QUOTE]
 This is more due to xine than Totem.  There's supposed to be a way to increase the number of buffers xine uses but I'm not sure how to do it.  This might make streaming videos a little smoother.

---

### Post by bored2k on 2005-03-31
[QUOTE=Nis]This is more due to xine than Totem.  There's supposed to be a way to increase the number of buffers xine uses but I'm not sure how to do it.  This might make streaming videos a little smoother.[/QUOTE]
 You made this howto, do you know at least where can I look for this option ? its really sad I can't watch trailers at large/fscreen size without the video doing the slow motion robot dance..

---

### Post by Nis on 2005-03-31
[QUOTE=bored2k]You made this howto, do you know at least where can I look for this option ? its really sad I can't watch trailers at large/fscreen size without the video doing the slow motion robot dance..[/QUOTE]
 I did a quick Google search but I couldn't find anything.  Sorry. :(

---

### Post by CowPie on 2005-03-31
Cool!  This even kind of wokrs with Opera.

---

### Post by bored2k on 2005-03-31
[QUOTE=Nis]I did a quick Google search but I couldn't find anything.  Sorry. :([/QUOTE]
 I can't even find somewhere to contact developers :\ .

---

### Post by Nano on 2005-03-31
I can't run it!

It shows me this syntax error:
```

mariano@Nano:/etc$ ./mozpluggerrc
./mozpluggerrc: line 23: syntax error near unexpected token `[,]'
./mozpluggerrc: line 23: `changequote([,])'

```

Any idea why?
I don't want to be the only one who can't run it :)

Thanks in advance!

---

### Post by Nis on 2005-04-01
As of two days ago the official Totem Mozilla plugin [is working](http://bugzilla.gnome.org/show_bug.cgi?id=144937).  While this won't make Hoary maybe we'll see a backport of it (hint, hint jdong:)).  It will probably requre the latest Totem so it might be too much for a backport but there's always hope.  Let's see if this HOWTO can be made obsolete.

---

### Post by LongTooth on 2005-04-02
Sorry guys. I've tried many things that have messed up my system. So fear of the unknown is not something that will stop me. But I still don't get it. I'm excited about enabling embeded streaming video on my machine but I don't know what to do. So, be kind and take me by the hand, please. What are the steps? Can't decipher Nis' HowTo. Thanks.

---

### Post by Muchacho_Gasolino on 2005-04-02
noobie version:

-open up synaptic
-do a search for mozplugger. it should find a package called mozplugger. mark it for install if its checkbox is not filled in already
-do a search for totem-xine. it should find a package called totem-xine. mark it for install if its checkbox is not filled in already
-apply changes
-download Nis's mozpluggerrc.txt. rename it in nautilus to just mozpluggerrc
-open up a terminal, navigate to the directory mozpluggerrc is in, and input ```
sudo cp ./mozpluggerrc /etc/mozpluggerrc
```
-open up your home directory in nautilus, show hidden files, open up the .mozilla directory, then the firefox directory, then delete pluginreg.dat

should be good to go  :wink: 

let me know if you need any further clarification

the only thing i dont understand is where to get the w32codecs from

---

### Post by ubuntu_demon on 2005-04-02
Muchacho_Gasolino : w32codecs you get from marillat

---

### Post by LongTooth on 2005-04-02
Here's something I think about when Mozplugger is to be used; Currently I'm using Ubuntu-geek's Auto Script which installed, among other things, Totem-xine . I like my video downloads to open in separate apps - in this case, Totem. In other installs, I have used Mplayer. In those systems, when I installed mozplugger, the stand-alone video viewer (Mplayer-Totem-Xine) was superceded by the plugin. Will this be the case here? For example: can I go to the Apple Trailer site and view their embedded film clips on my browser via the pluggin and also view other .mov files with Totem when it's called for? I don't want mozplugger to take over my viewing options. In other words, Totem opens and plays a clip when called upon and the pluggin plays a film clip in the browser when it's called to do so. Maybe I'm asking for too much. Is this a case of 'either/or' and not both?  Anyway, let me know. Before I install this on my main Linux box, I'll give it a shot on my test box. 

Muchacho_Gasolino, thanks for the clarification. I think I can work with this.

---

### Post by Muchacho_Gasolino on 2005-04-02
[QUOTE=demon666_nl]w32codecs you get from marillat[/QUOTE]

i dont have any package called w32codecs in my repositories(AMD64) from marillat
i looked through the lists on the unstable i386 repository on marillat's site and couldnt find the package there either

---

### Post by ubuntu_demon on 2005-04-03
[QUOTE=Muchacho_Gasolino]i dont have any package called w32codecs in my repositories(AMD64) from marillat
i looked through the lists on the unstable i386 repository on marillat's site and couldnt find the package there either[/QUOTE]
 that's bad
maybe it is or will be in hoary-extras (part of the backports project)

---

### Post by Leif on 2005-04-03
I just wanna say thanks for this too. Works nicely under Opera, except for the problem with viewing large trailers, as mentioned by others.

---

### Post by macewan on 2005-04-03
[QUOTE=LongTooth]For those of us who are mentally challanged, could someone please put these instructions in a form a moron like me can follow? I've just installed Ubuntu on a test box and I'd like to try this out before I do the same to my main box. Thanks.[/QUOTE]

thanks for saving me the time and stigma of asking this for this :wink:

---

### Post by bradword on 2005-04-03
You are my hero!  Mplayer plugin is sooo bad.  This works great.  I can stream from audible.com and mlb.com!  I can now watch my mlbtv package.  I'm so close to getting rid of windows all together.  I just need something to sync my ipod and download audible :).  Oh any pcAnywhere.  I'll keep looking around.  Again thanks for a great how-to.

---

### Post by LongTooth on 2005-04-03
macewan, always will to take a hit to get a procedure clarified. When I saw Nis' tip, I just couldn't figure it out. 

And Muchacho_Gasolino, I have to thank you for the 'noobie' instructions.

To answer my last post, this does not seem to interfere with the stand-alone video player (Totem-xine). I was able to view inline and downloaded videos using both (browser-plugin & Totem as called for). This worked on my test box. Now to try it out on my main box.

And last but certainly not least, a big thanks to Nis.

---

### Post by LongTooth on 2005-04-03
As  an after thought: Here's a site I use to test my system for everything. You'll see what I mean. [http://fredrik.hubbe.net/plugger.html](http://fredrik.hubbe.net/plugger.html)

Go to the bottom of the page. 'Testing Your Plugin'. "Plugger testing grounds".  When you're there: Menu on left side. Go to the bottom. Click on 'More Mime-types from Linspire'. Test to your hearts desire.


And I did installed in on my main box. Great! I can now say my system is complete.

---

### Post by saik0 on 2005-04-10
This worked great for me, I noticed however it wont play nice with other Totem windows

---

### Post by Nis on 2005-04-10
[QUOTE=saik0]This worked great for me, I noticed however it wont play nice with other Totem windows[/QUOTE]
 What do you mean by not playing nice?  Does it not work when another Totem window is open (as I believe it is doing now on my end) or does it replace what is playing?  If it is the second that is by design choice.

---

### Post by jeffjj on 2005-04-11
You guys rock! I have been using Linux for a few years now and just thought the multimedia stuff just didn't work. I see now that people are just weird about distributing the codes. I used this forum and the one from the unofficial documentation and now have full multimedia capabiltiy! Yeah, I'm so excited!

---

### Post by saik0 on 2005-04-11
[QUOTE=Nis]What do you mean by not playing nice?  Does it not work when another Totem window is open (as I believe it is doing now on my end) or does it replace what is playing?  If it is the second that is by design choice.[/QUOTE]

The first one Nis. This includes previously opened Totem windows as well as ones opened after it is embedded in the browser.

---

### Post by tanari on 2005-04-11
[http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/)
I think this plugin much better.
It has all buttons like play/pause/fullscreen/save movie to hdd

---

### Post by Nis on 2005-04-11
[QUOTE=tanari][http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/)
I think this plugin much better.
It has all buttons like play/pause/fullscreen/save movie to hdd[/QUOTE]
 I agree that mplayerplug-in is more featured than this workaround for Totem, but the last time I used it (from universe in Hoary) all the features you cite were not compiled in.  And it also require Mplayer which can be a pain to get working on some machines.  Totem-xine should work for most people and this tip takes advantage of that.

---

### Post by Cuber on 2005-04-11
I tried this with a Quicktime movie, had video but no sound. Couldn't play wmv file, missing codecs.

Cannot seem to find the codecs though. Anybody knows where to find them?

---

### Post by brickbat on 2005-04-11
Thanks. It is an excellent solution.

I do notice a rebuffering problem with the stream even though plenty of bandwidth is available.  What i have found so far is that there is a file in ~/.xine/catalog.cache that contains settings for the decoder.  Now we just need to figure out how to mod it without breaking something.

ciao
bb

---

### Post by Nis on 2005-04-11
[QUOTE=Cuber]I tried this with a Quicktime movie, had video but no sound. Couldn't play wmv file, missing codecs.

Cannot seem to find the codecs though. Anybody knows where to find them?[/QUOTE]
 The w32codecs are in hoary-extras of the [Ubuntu backports project](backports.ubuntuforums.org[/url).

---

### Post by Cuber on 2005-04-12
Ok, installed the codecs from the backport. Now I can play wmv files with sound. Quicktime movies do have sound / work on some sites, not on all (quicktime trailers work, embedded movies on [www.nintendo.com](www.nintendo.com) don't)

---

### Post by Nis on 2005-04-12
[QUOTE=Cuber]Ok, installed the codecs from the backport. Now I can play wmv files with sound. Quicktime movies do have sound / work on some sites, not on all (quicktime trailers work, embedded movies on [www.nintendo.com](www.nintendo.com) don't)[/QUOTE]
 Quicktime embedded videos do have sound for me.  Try playing a Quicktime video in a standalone totem instance and then try it embedded.  I discuss this [here](http://www.ubuntuforums.org/showpost.php?p=128464&postcount=32).

---

### Post by Cuber on 2005-04-12
[QUOTE=Nis]Quicktime embedded videos do have sound for me.  Try playing a Quicktime video in a standalone totem instance and then try it embedded.  I discuss this [here](http://www.ubuntuforums.org/showpost.php?p=128464&postcount=32).[/QUOTE]
 Standalone .mov files play without music as well.

It's a quick time codec issue I assume since some movies won't play as standalone or streaming at all (Totem give's a error)

---

### Post by mohaham on 2005-04-12
Awesome...
now Ubuntu is multimedia ready...
Thanks...

---

### Post by Nis on 2005-04-13
If you would rather have the (still in progress) official Totem-Mozilla plugin then check out [this thread](http://ubuntuforums.org/showthread.php?t=21405).  Requires some use of apt-get (not Synaptic), installing dev packages, editing files, and building debian packages.  If you decide to go this route (which is very very cool) you will need mozilla-dev or the plugin will not be compiled.

---

### Post by segrewb on 2005-04-13
Excellent!  I'm going to give it a try.

---

### Post by Jump on 2005-04-13
I can play apple trailers but they dont have any sound. I also can't play anything at gamespot.com

I followed the directions perfectly, it's just not working.

---

### Post by j_baer on 2005-04-13
The **_no_** sound issue is usually associated with the win32 codecs not installing. I would double check this and install if missing. There is a really nice script from Nis titled Hoary After Installation located here ...

[http://www.ubuntuforums.org/showthread.php?t=22860](http://www.ubuntuforums.org/showthread.php?t=22860)

Cheers ...

---

### Post by NeoChaosX on 2005-04-13
Works fine, except some WMVs don't play with sound in Totem. But in general, I've had problems getting WMVs to play with sound in Totem anyway. :-?

---

### Post by Cuber on 2005-04-14
I ran the HAIH script, it said I had the embedded media already installed. So I tried the quicktime movies that didn't work and now they do work with sound....

Weird, but I am happy.

Thanks.

---

### Post by merlyn on 2005-04-14
Thankyou so much, this is extremely cool !!!  :smile: 

Out of curiosity would it also be possible to do likewise with totem-gstreamer.

---

### Post by Nis on 2005-04-15
[QUOTE=merlyn]Thankyou so much, this is extremely cool !!!  :smile: 

Out of curiosity would it also be possible to do likewise with totem-gstreamer.[/QUOTE]
 I believe as long as you have totem-gstreamer installed instead of totem-xine than it should work.  Not sure since I haven't tried.  The problems with totem-gstreamer are lack of DVD menu support and the inability to correctly play many of the formats that are streamed over the web.  Until ffmpeg and gstreamer-dvd become more mature I recommend going with totem-xine.

---

### Post by NTolerance on 2005-04-20
I've followed the tutorial through twice and I still can't get streaming quicktime and wmv to work.  I have totem-xine, gstreamer, mozplugger, and w32codecs installed.  I can play quicktime and wmv files locally, but not streaming with Firefox.  Totem starts up when I click on a quicktime or wmv file in firefox, but I get this error:

```
There is no plugin to handle this movie.
```

---

### Post by Nis on 2005-04-20
[QUOTE=NTolerance]I've followed the tutorial through twice and I still can't get streaming quicktime and wmv to work.  I have totem-xine, gstreamer, mozplugger, and w32codecs installed.  I can play quicktime and wmv files locally, but not streaming with Firefox.  Totem starts up when I click on a quicktime or wmv file in firefox, but I get this error:

```
There is no plugin to handle this movie.
```[/QUOTE]
 Did you get the mozpluggerrc.txt attached at the beginning of this thread?  Did you rename it to /etc/mozpluggerrc?  Also, post the output of
```

ls -l /usr/lib/mozilla-firefox/plugins

```

---

### Post by NTolerance on 2005-04-20
[QUOTE=Nis]Did you get the mozpluggerrc.txt attached at the beginning of this thread?  Did you rename it to /etc/mozpluggerrc?  Also, post the output of
```

ls -l /usr/lib/mozilla-firefox/plugins

```[/QUOTE]

Yeah, I copied that file to /etc/mozpluggerrc.  

Here's the output:

```
ls -l /usr/lib/mozilla-firefox/plugins
total 0
lrwxrwxrwx  1 root root 37 2005-04-18 06:17 flashplayer.xpt -> ../../mozilla/plugins/flashplayer.xpt
lrwxrwxrwx  1 root root 39 2005-04-18 06:17 libflashplayer.so -> ../../mozilla/plugins/libflashplayer.so
lrwxrwxrwx  1 root root 58 2005-04-18 06:38 libjavaplugin_oji.so -> /usr/java/jre1.5.0_02/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx  1 root root 35 2005-04-18 15:11 mozplugger.so -> ../../mozilla/plugins/mozplugger.so
lrwxrwxrwx  1 root root 50 2005-04-18 06:17 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so


```

---

### Post by Nis on 2005-04-20
[QUOTE=NTolerance]Yeah, I copied that file to /etc/mozpluggerrc.  

Here's the output:

```
ls -l /usr/lib/mozilla-firefox/plugins
total 0
lrwxrwxrwx  1 root root 37 2005-04-18 06:17 flashplayer.xpt -> ../../mozilla/plugins/flashplayer.xpt
lrwxrwxrwx  1 root root 39 2005-04-18 06:17 libflashplayer.so -> ../../mozilla/plugins/libflashplayer.so
lrwxrwxrwx  1 root root 58 2005-04-18 06:38 libjavaplugin_oji.so -> /usr/java/jre1.5.0_02/plugin/i386/ns7/libjavaplugin_oji.so
lrwxrwxrwx  1 root root 35 2005-04-18 15:11 mozplugger.so -> ../../mozilla/plugins/mozplugger.so
lrwxrwxrwx  1 root root 50 2005-04-18 06:17 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so


```[/QUOTE]
 Have you tried removing ~/.mozilla/firefox/pluginreg.dat (or something like that).  mozplugger will not pick up configuration changes (such as the replacement of /etc/mozpluggerrc) until that file has been removed and recreated.

---

### Post by madzzoni on 2005-04-20
[QUOTE=NTolerance]I've followed the tutorial through twice and I still can't get streaming quicktime and wmv to work.  I have totem-xine, gstreamer, mozplugger, and w32codecs installed.  I can play quicktime and wmv files locally, but not streaming with Firefox.  Totem starts up when I click on a quicktime or wmv file in firefox, but I get this error:

```
There is no plugin to handle this movie.
```[/QUOTE]
You had to delete /home/your_username/.mozilla/firefox/[COLOR=Red]pluginreg.dat[/COLOR]
after replacing mozpluggerrc.

Then restart Firefox.

---

### Post by hector on 2005-04-20
Hello,

I followed your instructions on installing mozplugger and everything seems to be working ok except for one thing: if I revisit a web page with embedded media the media won't play (I get a blank box).  I have to flush the cache in firefox to be able to see it again. This is very inconvenient if you want to go back and forward while browsing.

anyone knows why?

cheers!


hector.

---

### Post by NTolerance on 2005-04-20
[QUOTE=Nis]Have you tried removing ~/.mozilla/firefox/pluginreg.dat (or something like that).  mozplugger will not pick up configuration changes (such as the replacement of /etc/mozpluggerrc) until that file has been removed and recreated.[/QUOTE]

I did that before and did it again for good measure, still no change.  I might add that I can play avi and mpeg files through Firefox/Totem, just not mov and wmv files.

Edit:  After further testing I am finding that it's only particular videos that do this.  I have found some streaming video test sites that work fine with all types of media.  This is the particular wmv file that I was having problems with:

mms://66.235.201.198/relapsemedia/video/BLOOD_%20AND_THUNDER.wmv

I'm assuming at this point that there's extra stuff in that wmv that's not covered by w32codecs.

Sorry for the wild goose chase everyone.

---

### Post by veritas366 on 2005-04-23
Thank you!  I don't know whose confusion is where but I want to add a couple of things.

First off, [this tutorial](http://ubuntuforums.org/archive/index.php/t-3450.html)  is the one I tried to follow. This puts in totem-xine and the mozplugger.  Then you have to edit the mozplugger which is at /etc/mozpluggerrc.  The problem with the tutorial was that it was really unclear exactly where to add this certain line it tells you to add.  the instructions are vague and I guess, from the reaction to this new approach, maybe not even correct.

Anyway, now you can follow the tutorial up until it says to start messing with mozpluggerrc.  Open it in a text editor as it suggests and then simply replace ALL of it with the text in the first post of this thread.  

Now, if no one who gets this far was confused about this much...well...sorry!  Just thought I'd make it double clear for newbies.

A couple more thoughts.  First, I could not get mplayer to work.  It would simply hang after buffering 25%...whether large file or small.  This was similar to its behavior in FC3 so it's not a Ubuntu thing but I couldn't figure it out.  

Second, I've found at least one thing that totem-xine can't open streaming...and that is certain quicktime files.  I think they also utilize activex or something. If you go to the apple movie site, for example, [here](http://www.apple.com/trailers/) and you have the same experience I do, then the following happens.  Links to sites where you must first click on small, medium, or large which then opens a separate page to play the clip work great.  The other type, where you are to click WITHIN THE FRAME of the area where the movie will play, do not work.  I looked at source once and like I said, I think these types have an activex component.

Anyway..thanks for this great fix...I was getting frustrated!

---

### Post by bahumbug on 2005-04-26
anyone else have a problem with the mozplugger plugin and the mozilla plugin for acroread?  whenever i try to install mozplugger, through synaptic, it says that i have to remove mozilla-acroread.

i have adobe acrobat installed and i prefer it to xpdf, is there any way to get mozilla-acroread working with the mozplugger? or must i choose... that would suck

PEACE

---

### Post by hobnob on 2005-04-28
To get PDFs to display using mozplugger, edit the following line in /etc/mozpluggerrc from ```
repeat swallow(acrobatreader) fill: acroread -geometry +9000+9000 +useFrontEndProgram -tempFileTitle acrobatreader "$file"
``` to ```
repeat swallow(acroread) fill: acroread -geometry +9000+9000 -tempFileTitle acrobatreader "$file"
``` You'll find it under "text/x-pdf: pdf: PDF file".

---

### Post by Spoofhound on 2005-05-02
This is really cool. Being totally new to Ubuntu (and Linux), help like this makes life sooooo easy. Thanks a bunch (ok, lotsa people have already said this, but that's not the issue), giving like this is what will eventually turn people onto Linux

---

### Post by Mon on 2005-05-03
Hi,
i'd like to play some realaudio stuff. The Apple trailers work fine, but can totem handle realmedia? I've also installed helix-player since it's opensource and should work with it, but it doesn't. Can anyone figure out how to fix this?

---

### Post by NeoChaosX on 2005-05-03
If you have w32codecs installed, then yeah, Totem can handle RealMedia just fine. Helix doesn't support Real formats, though, get RealPlayer itself if you want that.

---

### Post by linuxnomad on 2005-05-06
Thanks for the totem plugin it works great. I have not found to much that totem can't play on the net. The only things totem can't play are the same things Mplayer can't play. 

I can't seem to goto full screen, but the only Mplayer plugin I could utilize the full screen function on was in Gentoo, so totem is still just as good as Mplayer if not a little better in my opion. 

Is there a fix that can let me use the fullscreen function?

---

### Post by pseudonym on 2005-05-10
Just wanted to add my thanks for this as well! :D Previously, I was using a combination of gxine and vlc for video, with vlc set up for embedded. But that used to crap out more often than not, unfortunately. Now, with totem-xine and mozplugger, there's very little that won't play! :D

---

### Post by bored2k on 2005-05-10
I just started using kaffeine plugin for mozilla. Working wonders right now.

---

### Post by NeoChaosX on 2005-05-14
[Is there anybody else who's having streaming issues for Totem-xine? Mozplugger streams the video to Totem fine, my problem is that Totem stops too often to buffer the video again and again. I was hoping it's stream continously without stopping like mplayerplug-in.

EDIT: Nevermind, got rid of the mozplugger I compiled from source and installed the version in the repositories, and now the streaming problem is fixed.

---

### Post by lark5000 on 2005-05-15
What am I doing wrong?

I've followed the instructions at the top of page 4 of this thread, but when I select some media to play, Firefox is still tied to Mplayer as the plug-in.

Any suggestions?...

Oops, just figured it out.  I went to Synaptic and uninstalled mozilla-mplayer.  Now it works!  Thanks all...

---

### Post by rwabel on 2005-05-15
thanks a lot, works fine. Just wondering if the configuration button works for you guys?
For me when clicking on it, nothing happens

---

### Post by no-success on 2005-05-15
mozilla didnt rebuild its registry. ive closed mozilla and restarted my comp twice with no luck? any suggestions? can someone just send me their file?

---

### Post by rwabel on 2005-05-16
Audio is also working fine for me. But on this site it just won't play
[www.skyrock.com]("www.skyrock.com")
does anyone can confirm that?

another thing, if you click on the pause button, does it just pause or stop. I mean does it still use bandwidth for the streaming?

---

### Post by madzzoni on 2005-05-16
[QUOTE=rwabel]Audio is also working fine for me. But on this site it just won't play
[www.skyrock.com]("www.skyrock.com")
does anyone can confirm that?

another thing, if you click on the pause button, does it just pause or stop. I mean does it still use bandwidth for the streaming?[/QUOTE]

For me skyrock TV works fine, using Totem/mozpluggerrc

---

### Post by rwabel on 2005-05-16
[QUOTE=madzzoni]For me skyrock TV works fine, using Totem/mozpluggerrc[/QUOTE]
 that's right, skyrock tv is working. I meant skyrock radio :-) sorry for not beeing precise

---

### Post by no-success on 2005-05-16
[QUOTE=no-success]mozilla didnt rebuild its registry. ive closed mozilla and restarted my comp twice with no luck? any suggestions? can someone just send me their file?[/QUOTE]

Firefox still wont rewrite the pluginreg.dat file. any suggestions?

---

### Post by bjunix on 2005-05-16
hello . 
dont know if this is the right place to ask. but i didnt dare to open a new "totem" thread.

i installed the win32 codecs manualy and totem-xine is complaining about missing codecs. i found no way to configure totem to use my manualy installed codecs.

i've allready configured xine to use the win32 codecs, but that does not solve my problem


edit: ok i found the config file myself at ~/.gnome2/totem_config

---

### Post by dominik on 2005-05-22
i still dont get it to work. i installed everything and firefox still says "you dont have the wright plugin".

I use Firefox 1.0.4 from the Ubuntu Backports.
> 
dominik@ubuntu:~$ ls -l /usr/lib/mozilla-firefox/plugins
insgesamt 0
lrwxrwxrwx 1 root root 37 2005-05-21 13:31 flashplayer.xpt -> ../../mozilla/plugins/flashplayer.xpt
lrwxrwxrwx 1 root root 39 2005-05-21 13:31 libflashplayer.so -> ../../mozilla/plugins/libflashplayer.so
lrwxrwxrwx 1 root root 39 2005-05-21 13:37 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root 35 2005-05-21 22:13 mozplugger.so -> ../../mozilla/plugins/mozplugger.so 

any ideas?  :?

---

### Post by gamma on 2005-06-08
Thanks for posting there. I used to use the totem mozilla plugin using epiphany/mozilla backend. It didn't support enough mimetypes though. I then switched to firefox and the plugin no longer installed. I luckily found this post.

The only issue I'm having is the buffer is too small and videos stop to rebuffer a lot. Sometimes the movies don't play at all, and movies with advertisements at first dont want to play either...

---

### Post by jzke on 2005-06-09
O... M... G... this is great, I cannot that you enough!!!  :-)  \\:D/

---

### Post by fsman on 2005-06-17
can someone suggest a good site to test that this is working. On BTyahoo video section I select Windows Media player - totem starts with video but no sound

---

### Post by bored2k on 2005-06-17
[QUOTE=fsman]can someone suggest a good site to test that this is working. On BTyahoo video section I select Windows Media player - totem starts with video but no sound[/QUOTE]
 [http://www.gamespot.com/gslive/index.html](http://www.gamespot.com/gslive/index.html)
[http://www.apple.com/trailers/](http://www.apple.com/trailers/)

---

### Post by greenwom on 2005-06-17
I made sure the Packages were installed, removed the .txt extension and copied the file, and rm ~/.mozilla/firefox/pluginreg.dat

When I try to strean a .wmv file the white Mplayerplug-in screen runs and nothing it just loads and loads.....

What do I do?  

EDIT:  [COLOR=DarkOrange]I deleted the file again, guess I had to save when I shut down the box?[/COLOR]

---

### Post by Moosferatu on 2005-06-29
It doesn't seem to work of the streaming [Daily Show](http://www.comedycentral.com/shows/the_daily_show/videos/most_recent/index.jhtml) clips either.  Is there a way to fix this?

---

### Post by rwabel on 2005-06-30
[QUOTE=Moosferatu]It doesn't seem to work of the streaming [Daily Show](http://www.comedycentral.com/shows/the_daily_show/videos/most_recent/index.jhtml) clips either.  Is there a way to fix this?[/QUOTE]
 for me it even works in opera!

---

### Post by sirro on 2005-07-19
any chance you can add to the first post all the additional stuff you may have to do to install it so it works? like installing codecs and stuff like that......cause i am a true noob to this and instructions that are not STEP BY STEP or need additional stuff lose me totally......like assuming i know where things r in this topy turvy non-dos world of linux.........

i HATE windows with a passion..and i love what linux is all about.....but i cant swim here yet....and im not the only one.....the esyer it is the more converts we will have...i implore you to go by K.I.S.S. ;-)

---

### Post by darkmatter on 2005-07-19
Exellent. Even wma streams play perfectly. Tested on many sites, [Dreamland](http://www.unknowncountry.com/dreamland/) is a good example.

---

### Post by ubuntp on 2005-07-20
As an alternative you can install totem with builtin mozilla-plugin, it'll even show controls on videos then.

---

### Post by irkab1rka on 2005-07-23
In other words:

# please open a terminal (right click on desktop, and choose the first menu item: open new terminal)
# get access to the files as root: (will ask for root user's password)
sudo su
# extend the list of available updates by modify the line by adding **universe** (and probably the **multiverse)** option to it:
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted **universe** **multiverse**
vim /etc/apt/sources.list
# now you have to update the list of available software updates
apt-get update
# and you can do the install of the codecs (coder-decocoder) by:
apt-get install totem-xine
# at this point you probably will be able to open most of the files and you can watch them and you can hear them. I hope I have saved some  ](*,)  for you  ;-)

A comment should be added:
you can check the file (/etc/apt/sources.list) by using the menu: System/Administration/Update manager
Then please select "Ubuntu 5.04 binary" (or whatever you have except the CD) and  click 'edit'. On the panel you will find the 'Groups' section where 'main restricted' appears. If you change it to 'main restricted universe multiverse' (then save) then you did the same changes as i described above, so you can open the terminal for update and install.

---

### Post by WebbyBabe on 2005-08-29
I can't get this to work. :( All I get is a black box with the controls on the bottom.  ](*,)

---

### Post by darkmatter on 2005-08-29
[QUOTE=WebbyBabe]I can't get this to work. :( All I get is a black box with the controls on the bottom.  ](*,)[/QUOTE]

Make sure to install totem-xine, w32codecs, libquicktime, and any other media formats that you want playback capability for.

---

### Post by kairu0 on 2005-08-29
You are GOD! I've waited ages for a personnage like to grace the presence of the hallowed ubuntu forums!

---

### Post by WebbyBabe on 2005-08-30
[QUOTE=darkmatter]Make sure to install totem-xine, w32codecs, libquicktime, and any other media formats that you want playback capability for.[/QUOTE]

I have all of those things installed and still no luck.  ](*,)

---

### Post by eddietours on 2005-09-02
[QUOTE=WebbyBabe]I have all of those things installed and still no luck.  ](*,)[/QUOTE]
 hello everybody i just want to let you guys know thank you for all this great info am not using ubuntu but debian since ubuntu is built on debian i follow all the info in the forum and i have to said am very happy just keep the good work.

---

### Post by eddietours on 2005-09-02
sorry about the qoute it was not my intention i just wanted to said all the info is grate thz.

---

### Post by mbeach on 2005-09-12
anyone happen to get the xm radio feed working (available at: [http://xmro.xmradio.com/xstream/index.jsp)?](http://xmro.xmradio.com/xstream/index.jsp)?)  I get the little visualization in the player window, but no sound.  However, if I view the source and see that it is pointing to: 
[http://player.xmradio.com/hotstream/metafile.jsp?ch=16&speed=low&s=121326557&e=121326557&h=64786f65](http://player.xmradio.com/hotstream/metafile.jsp?ch=16&speed=low&s=121326557&e=121326557&h=64786f65)

[I changed the values of the s e and h for this post (see the link for the full url)]

so, after reading something about launching totem from the command line at least once, so I ran:
```
totem [http://player.xmradio.com/hotstream/metafile.jsp?ch=16&speed=low&s=121326557&e=121326557&h=64786f65](http://player.xmradio.com/hotstream/metafile.jsp?ch=16&speed=low&s=121326557&e=121326557&h=64786f65)

```
which launches totem, but I get a login error (I'm using my legitimate usr/pwd).  In the console I get this though:
```

[1] 20396
[2] 20397
[3] 20398
[4] 20399
[2]   Done                    speed=low
[3]   Done                    s=121326557
[4]   Done                    e=121326557

```
and eventually:
```

StreamCount r=0x0  1  1
Total Unfree 60 bytes cnt 1 [(nil),0]

```
My gut feeling is the parameters are too long, or there are too many of them.  The same output is seen when running gxine.  

So, my question is, has anyone gotten the XM Radio player to work [I think you can sign up for a 3 day trial]?

Any ideas?
mb.

---

### Post by seiflotfy on 2005-10-06
where did the txt file go

---

### Post by Mon on 2005-10-13
The script worked great for me in Hoary. However a new era of Linux has come, and it's name is Breezy Badger as you'd might have noticed :)
The Breezy installer appearantly overwrote my old config. Are there any plans to adapt the mozplugger file for Breezy so i can watch trailers at Apple again? Or should the Hoary file still be compatible? I checked the new mozplugger file and it does seem to handle files different than this version...

---

### Post by madzzoni on 2005-10-13
[QUOTE=Mon]The script worked great for me in Hoary. However a new era of Linux has come, and it's name is Breezy Badger as you'd might have noticed :)
The Breezy installer appearantly overwrote my old config. Are there any plans to adapt the mozplugger file for Breezy so i can watch trailers at Apple again? Or should the Hoary file still be compatible? I checked the new mozplugger file and it does seem to handle files different than this version...[/QUOTE]

This works for my Breezy, only thing it seems not to handle is the apple/trailers (.mov).
I following the "hoary" instruction.

---

### Post by crypto178 on 2005-10-14
[QUOTE=madzzoni]This works for my Breezy, only thing it seems not to handle is the apple/trailers (.mov).
I following the "hoary" instruction.[/QUOTE]

Same thing here, I don't know why but apple.com trailers don't work, totem loads but an error occurs that goes like : "there was no plugin to handle this" (rough translation from french).

---

### Post by John.Michael.Kane on 2005-10-15
do you have the quicktime files installed ie:libquicktime

---

### Post by OttoDestruct on 2005-10-16
I have this working... somewhat... it shows about 3 seconds of video then just stops. Doesn't matter how long I sit there for the stream to download or whatever, it can be an hour for a 1mb video, and it only shows ~3 seconds.

---

### Post by livecdlover on 2005-10-16
Here's the best advice I can give that is almost guaranteed to work perfectly and play movies from [http://www.apple.com/trailers/](http://www.apple.com/trailers/) embedded in Firefox.  Go to this link and follow the directions.  In my plugin folder I had three files with Totem in the name that I had to delete.  Here's the link: [http://www.ubuntuforums.org/showthread.php?p=418707&posted=1#post418707](http://www.ubuntuforums.org/showthread.php?p=418707&posted=1#post418707)

I just used the Mplayer instruction above and the repository information at [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html) . I found this link in the Ubuntu forums. Mplayer now works perfectly embedded in Firefox. I can even hit the back button in Firefox while playing a movie and Firefox doesn't shut down. I don't kow why Ubuntu uses Totem.  Mplayer looks very nice embedded in Firefox and works great.  :D

---

### Post by Mon on 2005-10-17
[QUOTE=SD-Plissken]do you have the quicktime files installed ie:libquicktime[/QUOTE]
I didn't.. So i installed libquicktime1.
Still get "Totem could not play 'fd://0'. No plugin ..."
Do you have it working on Breezy?

Using an online radio thingy (which used to work) i get this in a terminal:
$ ** Message: error: There is no plugin to handle thi s movie.
The program 'totem-mozilla-viewer' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 1379 error_code 9 request_code 14 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by crypto178 on 2005-10-17
[QUOTE=SD-Plissken]do you have the quicktime files installed ie:libquicktime[/QUOTE]

Yes, it didn't help though :(
I think the problem comes from apple.com using advanced quicktime features (beyond simple video files), such as an embedded movie file redirecting to another (more hidden) file. To prevent leeching I guess, bah!
Just pure speculation :D

---

### Post by eddietours on 2005-10-20
hello i can see the regular quicktime video but not the hd aka h.264 can anybody help please:confused:

---

