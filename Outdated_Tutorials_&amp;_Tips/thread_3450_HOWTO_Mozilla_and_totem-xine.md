---
title: "HOWTO: Mozilla and totem-xine"
date: 2004-11-06
forum: Outdated Tutorials &amp; Tips
---

### Post by mercurus on 2004-11-06
Greetings all

This probably needs to be integrated into the Multimedia-HOWTO, but I'll post it separately so it can be viewed and edited without reading the other 8 pages of posts on that sticky thread.

Mozilla and Totem Streaming Solution HOWTO

While MPlayer provides a streaming solution with the Mozilla mplayer-plugin, it is possible to receive and play Windows Media Player streams on Ubuntu without MPlayer. By simply installing the mozplugger and w32codecs packages, and making use of the standard totem-xine package, these streams can be played on Ubuntu Warty 4.1.

Step 0: Install w32codecs.

To play proprietary media formats such as those used by Windows Media Player, Apple's Quicktime, and Real Player it is necessary to install codecs, to de-code the compressed file into a playable format. Due to the legally dubious nature of these codecs they are stored in the Marillat repository, separate from the primary Ubuntu repositories. If you want to use these formats on Ubuntu, these are your best option, but they also raise difficult legal questions. It is your choice whether or not to install them, but they are required to achieve the goal of this HOWTO. Add the Marillat repository to your /etc/apt/sources.list file and update your apt cache with apt-get update. Once completed, install the w32codecs package with apt-get install w32codecs.

Step 1: Install totem-xine.

While totem-gstreamer is a part of the totem-desktop package, you will need to enable the universe repository in order to download the totem-xine package. Uncomment the universal package repository in your /etc/apt/sources.list file, and update your apt-get cache with apt-get update. Once completed, install the totem-xine package with apt-get install totem-xine, which will replace the existing totem-gstreamer package.

Step 2: Install mozplugger.

In order to link Mozilla Firefox and Totem together, we need a plugin that will associate particular mime types with particular applications. Mozplugger is a plugin for Mozilla (Firefox)  that will 'glue' Mozilla to almost any application. Mozplugger is available from the standard Ubuntu depository, and should be installed with apt-get install mozplugger.

Step 3: Configure mozplugger.

While mozplugger is distributed with mplayer in mind, it is quite simple to re-configure it to make use of totem-xine instead. Use sudo and your favourite editor to alter the /etc/mozpluggerrc file to reflect our choice of multimedia player. Where you see:
```

application/x-mplayer2: wmv,asf,mov: Windows Media
video/x-ms-asf: asf,asx,wma,wax,wmv,wvx: Windows Media
video/x-ms-wmv: wmv: Windows Media

```
Add the following line:
```
stream noisy ignore_errors: totem "$file" </dev/null
```
Repeat this line for any other file formats for which totem-xine has codecs, and you wish to access with Mozilla. Once all the changes you wish to make have been made, save the file and exit the editor.

Step 4: Update Mozilla Firefox's Plug-in Registry.

Mozilla keeps a miniature registry of each plugin it is configured to use, which is read each time the browser loads to save time. However, changes to mozilla's plug-ins are not incorporated into the registry unless it is re-generated. The easiest way to regenerate the registry is to delete the current file, and restart Mozilla. The registry file is stored in ~/.mozilla//pluginreg.dat, which you should delete before restarting Mozilla Firefox.

Step 5: Checking Mozilla Firefox is up to date.

To ensure Firefox has picked up the changes to its plug-in configuration, point your newly opened browser window to "about:plugins" and check that mozplugger is there, and includes references to the mime types you associated with totem-xine. If there is no evidence of those mime types, re-check Step 4, and re-check the syntax used in Step 3.

Step 6: Testing Time !

Assuming all went well, your mozilla firefox knows to start totem-xine whenever it encounters specific mime types, including Windows Media Player. Point your browser to your favourite stream and start listening :)

Optional 1: Capturing streams.

It is easy to capture media streams, however I have no idea about the legallity of this course of action. If in doubt, give it a miss. By installing the mimms package from the unviersal repository you can capture .asf streams and store them on your hard disk until you're ready to listen to them. I have a relatively slow internet connection, and several people sharing it, so I make lists of streams I would like to record and download them overnight. If you encouter a .asx file it is in fact a link to an .asf file. Use wget to download the .asx file, and inside you will find the URL to the .asf file. Use mimms to download the .asf file.

I hope that helps !
[email]mercurus@gmail.com[/email]

Cheers
mercurus

---

### Post by leeech on 2004-11-06
thanks for the how-to...

my soundcard is workin and totem if play avi/dvd has sound...

but when i stream video, i can see video but no sound...

why?

---

### Post by mercurus on 2004-11-08
[QUOTE=leeech]thanks for the how-to...

my soundcard is workin and totem if play avi/dvd has sound...

but when i stream video, i can see video but no sound...

why?[/QUOTE]
 In short, no idea.

But I have a few suggestions ...

1. Run totem from a terminal and point it to the resource you're trying to stream. Observe the output and see if it gives any errors, warnings or suggestions as to what is wrong.

2. Check that you've unmuted "Video" or any other possible Output sources in your Volume Control settings. For the moment, if you know what it is unmute it. If you don't know what it is, unmute it anyway.

3. Check that your internet connection is capable of streaming both sound and video simultaneously. My 128kbps ISDN struggles with sound only, let alone both !

4. Try a few different sources and make sure that they are streaming both video and audio. Try streaming audio-only and see if that works. I know I can stream WMV audio and totem visualises, but I don't think I've tested video.

5. Check that all the codecs you need are installed.

6. What file type are you trying to stream ? Make sure that the configuration line from the HOWTO above is included in your config file under ALL the file types you want to stream, then clear the plug-in cache, and restart firefox.

If none of that works, I have no ideas ... anyone else ?

Cheers
mercurus

---

### Post by leeech on 2004-11-08
i'm gettin this error

$ totem [http://movies.apple.com/movies/disney/cars/cars-teaser_240.mov](http://movies.apple.com/movies/disney/cars/cars-teaser_240.mov)
External func COMCTL32.dll:16
External func COMCTL32.dll:17
wine/module: Unsupported QuickTime version (0x6693c3e0)

i've install w32codecs

---

### Post by wallijonn on 2004-11-08
I've had problems adding the [ftp://ftp.nerim.net/debian-marillat/dists/](ftp://ftp.nerim.net/debian-marillat/dists/) unst to /etc/apt/sources.list.What is the correct format?

---

### Post by umarmung on 2004-11-09
First of all, thx a lot for this HOWTO mercurus. I knew about mozplugger, but i had no idea you could get it to work with totem.  :D 

Next: I found out why you get only video but no sound with quicktime trailers. I downloaded an older version of the qt-codecs from the mplayer site (Don't worry, they work with totem-xine too).
[list]
[*] download [http://www1.mplayerhq.hu/MPlayer/releases/codecs/qt6dlls-20040626.tar.bz2](http://www1.mplayerhq.hu/MPlayer/releases/codecs/qt6dlls-20040626.tar.bz2)
[*] extract the archive to /usr/lib/win32
[*] watch and **hear** quicktime videos  :lol: 
[/list]

---

### Post by Cloudchaser on 2004-12-30
I tried all of the above instructions but I have a couple of questions. When I add the line: stream noisy ignore_errors: totem "$file" </dev/null do I remove the references to mplayer in this line: stream noisy ignore_errors: mplayer -really-quiet -nojoystick -nofs -

i just added what it said to in the how-to and I got farther. Firefox no longer says I need mplayer-plugin and the file opens in totem-xine but has no audio, so I extracted the older files as umarmung's post suggested but when extracted they are placed into a dir called  qt6dlls-20040626. Do i move them from this dir into /usr/lib/win32 and if I do that, will I mess up anything that might want the newer qt codecs?

Thank you,

Cloudchaser

---

### Post by Cpennyspal on 2007-03-09
> **mercurus said:**
> Greetings all

This probably needs to be integrated into the Multimedia-HOWTO, but I'll post it separately so it can be viewed and edited without reading the other 8 pages of posts on that sticky thread.

Mozilla and Totem Streaming Solution HOWTO

While MPlayer provides a streaming solution with the Mozilla mplayer-plugin, it is possible to receive and play Windows Media Player streams on Ubuntu without MPlayer. By simply installing the mozplugger and w32codecs packages, and making use of the standard totem-xine package, these streams can be played on Ubuntu Warty 4.1.

Step 0: Install w32codecs.

To play proprietary media formats such as those used by Windows Media Player, Apple's Quicktime, and Real Player it is necessary to[COLOR="Red"] install codecs[/COLOR], to de-code the compressed file into a playable format. Due to the legally dubious nature of these codecs they are stored in the Marillat repository, separate from the primary Ubuntu repositories. If you want to use these formats on Ubuntu, these are your best option, but they also raise difficult legal questions. It is your choice whether or not to install them, but they are required to achieve the goal of this HOWTO. Add the Marillat repository to your** /etc/apt/sources.list file **and update your apt cache with apt-get update. Once completed, install the w32codecs package with apt-get install w32codecs.

Step 1: Install totem-xine.

While totem-gstreamer is a part of the totem-desktop package, you will need to enable the universe repository in order to download the totem-xine package. Uncomment the universal package repository in your[COLOR="Red"] /etc/apt/sources.list file[/COLOR], and update your apt-get cache with apt-get update. Once completed, install the totem-xine package with apt-get install totem-xine, which will replace the existing totem-gstreamer package.

Step 2: Install mozplugger.

In order to link Mozilla Firefox and Totem together, we need a plugin that will associate particular mime types with particular applications. Mozplugger is a plugin for Mozilla (Firefox)  that will 'glue' Mozilla to almost any application. Mozplugger is available from the standard Ubuntu depository, and should be installed with apt-get install mozplugger.

Step 3: Configure mozplugger.

While mozplugger is distributed with mplayer in mind, it is quite simple to re-configure it to make use of totem-xine instead. Use sudo and your favourite editor to alter the /etc/mozpluggerrc file to reflect our choice of multimedia player. Where you see:
```

application/x-mplayer2: wmv,asf,mov: Windows Media
video/x-ms-asf: asf,asx,wma,wax,wmv,wvx: Windows Media
video/x-ms-wmv: wmv: Windows Media

```
Add the following line:
```
stream noisy ignore_errors: totem "$file" </dev/null
```
Repeat this line for any other file formats for which totem-xine has codecs, and you wish to access with Mozilla. Once all the changes you wish to make have been made, save the file and exit the editor.

Step 4: Update Mozilla Firefox's Plug-in Registry.

Mozilla keeps a miniature registry of each plugin it is configured to use, which is read each time the browser loads to save time. However, changes to mozilla's plug-ins are not incorporated into the registry unless it is re-generated. The easiest way to regenerate the registry is to delete the current file, and restart Mozilla. The registry file is stored in ~/.mozilla//pluginreg.dat, which you should delete before restarting Mozilla Firefox.

Step 5: Checking Mozilla Firefox is up to date.

To ensure Firefox has picked up the changes to its plug-in configuration, point your newly opened browser window to "about:plugins" and check that mozplugger is there, and includes references to the mime types you associated with totem-xine. If there is no evidence of those mime types, re-check Step 4, and re-check the syntax used in Step 3.

Step 6: Testing Time !

Assuming all went well, your mozilla firefox knows to start totem-xine whenever it encounters specific mime types, including Windows Media Player. Point your browser to your favourite stream and start listening :)

Optional 1: Capturing streams.

It is easy to capture media streams, however I have no idea about the legallity of this course of action. If in doubt, give it a miss. By installing the mimms package from the unviersal repository you can capture .asf streams and store them on your hard disk until you're ready to listen to them. I have a relatively slow internet connection, and several people sharing it, so I make lists of streams I would like to record and download them overnight. If you encouter a .asx file it is in fact a link to an .asf file. Use wget to download the .asx file, and inside you will find the URL to the .asf file. Use mimms to download the .asf file.

I hope that helps !
[email]mercurus@gmail.com[/email]

Cheers
mercurus

Thank you for your help in getting Totem to work.  However, I am new to 
Ubuntu and have no clue what certain items mean and how to do them!

 I have highlighted the items that I do not understand how to do.
Is there any place I can find information on how to do these procedures in 
plain newcomer form?

I do not understand many of the terms and need something to explain things
in simple step by step form for a complete new user that has no idea.

 (Sorry!  I am unable to highlight the items I need explained)  I can't seem to do
anything in Ubuntu except  search the internet with Firefox and Mozilla. 
Thanks,

Ed (Cpennyspal@msn.com)

 
Greetings all

This probably needs to be integrated into the Multimedia-HOWTO, but I'll post it separately so it can be viewed and edited without reading the other 8 pages of posts on that sticky thread.

Mozilla and Totem Streaming Solution HOWTO

While MPlayer provides a streaming solution with the Mozilla mplayer-plugin, it is possible to receive and play Windows Media Player streams on Ubuntu without MPlayer. By simply installing the mozplugger and w32codecs packages, and making use of the standard totem-xine package, these streams can be played on Ubuntu Warty 4.1.

Step 0: Install w32codecs.

To play proprietary media formats such as those used by Windows Media Player, Apple's Quicktime, and Real Player it is necessary to install codecs, to de-code the compressed file into a playable format. Due to the legally dubious nature of these codecs they are stored in the Marillat repository, separate from the primary Ubuntu repositories. If you want to use these formats on Ubuntu, these are your best option, but they also raise difficult legal questions. It is your choice whether or not to install them, but they are required to achieve the goal of this HOWTO. Add the Marillat repository to your /etc/apt/sources.list file and update your apt cache with apt-get update. Once completed, install the w32codecs package with apt-get install w32codecs.

Step 1: Install totem-xine.

While totem-gstreamer is a part of the totem-desktop package, you will need to enable the universe repository in order to download the totem-xine package. Uncomment the universal package repository in your /etc/apt/sources.list file, and update your apt-get cache with apt-get update. Once completed, install the totem-xine package with apt-get install totem-xine, which will replace the existing totem-gstreamer package.

Step 2: Install mozplugger.

In order to link Mozilla Firefox and Totem together, we need a plugin that will associate particular mime types with particular applications. Mozplugger is a plugin for Mozilla (Firefox) that will 'glue' Mozilla to almost any application. Mozplugger is available from the standard Ubuntu depository, and should be installed with apt-get install mozplugger.

Step 3: Configure mozplugger.

While mozplugger is distributed with mplayer in mind, it is quite simple to re-configure it to make use of totem-xine instead. Use sudo and your favourite editor to alter the /etc/mozpluggerrc file to reflect our choice of multimedia player. Where you see:
Code:

application/x-mplayer2: wmv,asf,mov: Windows Media
video/x-ms-asf: asf,asx,wma,wax,wmv,wvx: Windows Media
video/x-ms-wmv: wmv: Windows Media

Add the following line:
Code:

stream noisy ignore_errors: totem "$file" </dev/null

Repeat this line for any other file formats for which totem-xine has codecs, and you wish to access with Mozilla. Once all the changes you wish to make have been made, save the file and exit the editor.

Step 4: Update Mozilla Firefox's Plug-in Registry.

Mozilla keeps a miniature registry of each plugin it is configured to use, which is read each time the browser loads to save time. However, changes to mozilla's plug-ins are not incorporated into the registry unless it is re-generated. The easiest way to regenerate the registry is to delete the current file, and restart Mozilla. The registry file is stored in[SIZE="6"] ~/.mozilla//pluginreg.dat, w[/SIZE]hich you should delete before restarting Mozilla Firefox.

Step 5: Checking Mozilla Firefox is up to date.

To ensure Firefox has picked up the changes to its plug-in configuration, point your newly opened browser window to "about:plugins" and check that mozplugger is there, and includes references to the mime types you associated with totem-xine. If there is no evidence of those mime types, re-check Step 4, and re-check the syntax used in Step 3.

Step 6: Testing Time !

Assuming all went well, your mozilla firefox knows to start totem-xine whenever it encounters specific mime types, including Windows Media Player. Point your browser to your favourite stream and start listening :)

Optional 1: Capturing streams.

It is easy to capture media streams, however I have no idea about the legallity of this course of action. If in doubt, give it a miss. By installing the mimms package from the unviersal repository you can capture .asf streams and store them on your hard disk until you're ready to listen to them. I have a relatively slow internet connection, and several people sharing it, so I make lists of streams I would like to record and download them overnight. If you encouter a .asx file it is in fact a link to an .asf file. Use wget to download the .asx file, and inside you will find the URL to the .asf file. Use mimms to download the .asf file.

I hope that helps !
[email]mercurus@gmail.com[/email]

Cheers
mercurus

---

### Post by Yellowbelly on 2007-04-10
I had a problem with apt-get update. Here's what it said:

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Did I jack something up?

And what's the code to add the Marillat repository? I searched it and some guy said it was a bad idea since it's for debian only. (?) [http://ubuntuforums.org/showthread.php?t=393220&highlight=marillat](http://ubuntuforums.org/showthread.php?t=393220&highlight=marillat)

---

