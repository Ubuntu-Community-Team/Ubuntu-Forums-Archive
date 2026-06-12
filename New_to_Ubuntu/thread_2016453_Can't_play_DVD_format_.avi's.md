---
title: "Can't play DVD format .avi's"
date: 2012-07-04
forum: New to Ubuntu
---

### Post by Deniz343 on 2012-07-04
How can I play DVD video with .avi extension on XBMC or another video player.

---

### Post by deadflowr on 2012-07-04
You'll have to consult xbmc's help section to figure out how to work it, but this page will get you to enable playback on your system:

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by SeijiSensei on 2012-07-04
You mean you have a DVD with a bunch of AVI files on it?  In most cases you should just be able to open the DVD, double-click a file, and it should play with most modern player software.  Did you try that and have it fail?  We need a bit more information about what you mean by "can't play".

Perhaps you mean you have a DVD rip in the AVI container?  Again you should be able to play that by double-clicking the filename to launch a player.  

I recommend SMPlayer as a general-purpose media player.  It runs mplayer as the engine and provides a nice GUI.  One advantage of having mplayer installed is that it provides excellent diagnostics when run from the command line.  Running "mplayer /path/to/file.avi" should give you some clues about what's going wrong.  SMPlayer makes that same information available via Options > View Logs > MPlayer.

---

### Post by Deniz343 on 2012-07-04
> **deadflowr said:**
> You'll have to consult xbmc's help section to figure out how to work it, but this page will get you to enable playback on your system:

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

I downloaded it.

---

### Post by Deniz343 on 2012-07-04
> **SeijiSensei said:**
> You mean you have a DVD with a bunch of AVI files on it?  In most cases you should just be able to open the DVD, double-click a file, and it should play with most modern player software.  Did you try that and have it fail?  We need a bit more information about what you mean by "can't play".

Perhaps you mean you have a DVD rip in the AVI container?  Again you should be able to play that by double-clicking the filename to launch a player.  

I recommend SMPlayer as a general-purpose media player.  It runs mplayer as the engine and provides a nice GUI.  One advantage of having mplayer installed is that it provides excellent diagnostics when run from the command line.  Running "mplayer /path/to/file.avi" should give you some clues about what's going wrong.  SMPlayer makes that same information available via Options > View Logs > MPlayer.

When I try to play this video on ubuntu default movie player I get this error: > Required plugin could not be found

Python (v2.7) requires to install plugins to play media files of the following type: On2 VP7 decoder
I have xbmc media center and I can play xvid, dvix or .mp4 but can't play > AVI video (video/x-msvideo)

Best Regards

---

### Post by deadflowr on 2012-07-04
> **Deniz343 said:**
> I downloaded it.

I don't understand what you mean. Downloaded what?

Did you install the restricted-extras package?

Did you enable the command:

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

Running this command I've never had an issue with .avi files. In fact all of my family home movies recently converted from VHS are in .avi format, and playback seamlessly. I've watched innumerable netflix DVD's as well.

---

### Post by SeijiSensei on 2012-07-04
The problem isn't that the files are stored in the AVI "container" but that they are encoded with the On2 VP7 codec.  A solution to that problem is described here:

[http://ubuntuforums.org/showthread.php?t=1719370](http://ubuntuforums.org/showthread.php?t=1719370)

However this will only work with mplayer on 32-bit systems.  The VP7 codec is 32-bit and won't work with 64-bit mplayer.  Some possible solutions are discussed in that thread.

Just for reference, multimedia files consist of what is called a "container" like AVI, Matroska (.mkv), or MP4, in which is stored the various "streams" -- audio, video, and subtitles.  Those streams are encoded with "codecs" like H.264, XviD, or in your case VP7.  So the problem isn't that you cannot play AVI files, but that you cannot play a file where the video is encoded with VP7.

CSS isn't the problem here either.  That's the encryption scheme used on commercial DVDs.  If the files exist as AVIs they have already been ripped or otherwise acquired.

---

### Post by Deniz343 on 2012-07-04
> **deadflowr said:**
> I don't understand what you mean. Downloaded what?

Did you install the restricted-extras package?

Did you enable the command:

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

Running this command I've never had an issue with .avi files. In fact all of my family home movies recently converted from VHS are in .avi format, and playback seamlessly. I've watched innumerable netflix DVD's as well.

I did what you sad but no luck on this file to work: [https://rapidshare.com/files/2269910654/The.Simpsons.S06E19.Lisa_s.Wedding.DVDRIP.VP7.KEGGERMAN.avi](https://rapidshare.com/files/2269910654/The.Simpsons.S06E19.Lisa_s.Wedding.DVDRIP.VP7.KEGGERMAN.avi) please check this file.

---

### Post by deadflowr on 2012-07-04
I'm sorry to say that this seems to be a vexing issue for you. Looking around I've found the solution in seijisensei's thread link to be the best working solution available at the moment. I don't know if any video converter programs would work to convert the format to a more appeasing codec.

---

### Post by deadflowr on 2012-07-04
I found this really old forum link of how to convert vp7

[http://ubuntuforums.org/showthread.php?t=502179]("http://ubuntuforums.org/showthread.php?t=502179")

It might help.

---

### Post by Deniz343 on 2012-07-04
> **deadflowr said:**
> I found this really old forum link of how to convert vp7

[http://ubuntuforums.org/showthread.php?t=502179]("http://ubuntuforums.org/showthread.php?t=502179")

It might help.

But I have 22 Seasons of the simpsons :( 
Can I use this only > I have had success using Mplayer with the w32codecs package installed from medibuntu. It includes the VP7 codec. You can also use MEncoder to transcode any Mplayer playable video into whatever you want. I'm converting a season of Simpsons I accidentally downloaded in VP7 into XVid4.

---

### Post by The_Cunning_Stunt on 2013-02-27
When I tried to play *.ts files in Movie Player in Ubuntu 12.10  (64-bit), 
I got the following message 
"python (v2.7) requires to install plugins to play media files of the following type: application/x-mpegts-private-section decoder."
and then my computer would crash......
The files wouldn't play at all in VLC!!!

After a bit of search on the internet, I found a solution of sorts:???:.
Install Medibuntu as follows
```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

sudo apt-get install non-free-codecs
```

<<then install ffmpeg - there seems to be different ways to install ffmpeg>>

Open ffmpeg, and convert the *.ts file to a DVD PAL fullscreen or avi
It can take a while, but once it is done, you can play the file in Movie player or VLC.

I'm sure there is another way, but this worked for me ;)

---

