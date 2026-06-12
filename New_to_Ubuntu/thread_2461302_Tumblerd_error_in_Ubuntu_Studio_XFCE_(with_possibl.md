---
title: "Tumblerd error in Ubuntu Studio XFCE (with possible solution)"
date: 2021-04-28
forum: New to Ubuntu
---

### Post by oscarsanchezrequena on 2021-04-28
Tumblerd error in Ubuntu Studio (with possible solution)

9 years ago I abandoned Xubuntu (and Thunar) because of this bug that would not let me work. Today he has returned ... I do not understand, how is it possible that this problem exists in an S.O. dedicated to graphic design, photography, illustration, etc. :confused:


**Tumblerd** appears when I open a window with images (thumbnail preview). And every time Tumblerd appears, the system becomes unstable, the image viewer (Viewnior) crashes ... (it happened 9 years ago and now too) Does it only happen to me ?!

One solution they gave me is this executable file "Killtumberd.sh"



```
#! / bin / bash
while [true]
do
        if ["` ps -ef | grep tumblerd | wc -l` "-gt" 1 "]; then

                `killall tumblerd`
        fi
        sleep 2
done

```


Every 2 seconds he runs and kills Tumblerd. This reduces overall performance but it works, at least it doesn't crash the computer.


Now I thought maybe it is a better idea to remove Thunar and replace with PCmanFM.

My question is: Can I remove Thunar from Ubuntu Studio, or is it better to leave it grounded in a dark corner?


My Linux level is small, I'm just a designer.

Thanks and greetings to all.
oscar

---

### Post by oscarsanchezrequena on 2021-04-28
The problem! 

Youtube video-screen: [https://www.youtube.com/watch?v=hQa8arQ0tYM](https://www.youtube.com/watch?v=hQa8arQ0tYM)

PCmanFM not resolve.... :(

---

### Post by Holger_Gehrke on 2021-04-28
tumblerd is a background process which creates thumbnail-files in  '~/.cache/thumbnails'. If Thunar doesn't find a thumbnail for a file  that should have one, it starts tumblerd through dbus. The operation of  tumblerd is controlled by the configuration files  '/etc/xdg/tumbler/tumbler.rc' and '~/.config/tumbler/tumbler.rc'. The  latter file is a personal configuration that overrides the other, system  wide configuration. In tumbler.rc you can enable or disable the various  plugins used to create thumbnails, limit the maximum size of file to  create thumbnails for, set what directories to create thumbnails for and  set priorities for the plugins. Documentation for tumbler can be found  at [xfce.org]("https://docs.xfce.org/xfce/tumbler/start").  Setting tumbler to not create thumbnails for videos and to leave files  bigger then 2MB alone has reduced the load created by tumbler on my  machine to unnoticeable levels.

Holger

---

### Post by oscarsanchezrequena on 2021-04-28
Very thanks! :)

Do you think it is related to the problem shown in the video (youtube) in my second comment? [https://www.youtube.com/watch?v=hQa8arQ0tYM](https://www.youtube.com/watch?v=hQa8arQ0tYM)

---

### Post by ajgreeny on 2021-04-28
On my Xubuntu 20.04 install this is the section of my /etc/xdg/tumbler/tumbler.rc file (lines 45-57) that I have edited to disable Video thumbnails creation and just like Holger the system slow-down that used to occur in the past is no longer happening.
The line shown in red is the only change I made.
```
    	###
    	# Video Thumbnailers
    	###
    	
    	# Download cover from omdbapi.com or themoviedb.org if an
    	# API key is given. This plugin is disabled because it
    	# sends your (private) movie names over the internet.
    	[CoverThumbnailer]
    	[COLOR="#FF0000"]Disabled=true[/COLOR]
        Priority=3
    	Locations=
    	MaxFileSize=0
    	#APIKey=your-api-key-from-themoviedb.org
```

---

### Post by Holger_Gehrke on 2021-04-28
@ajgreeny: That's a thumbnailer that downloads cover for recognized  videofiles from the net and is disabled by default because it has  implications for privacy. The settings for the other video thumbnailers  (FfmpegThumbnailer and GstThumbnailer) are below that in the tumbler.rc.  Those are enabled by default and are the ones I disabled. Setting  reasonable values for MaxFileSize for the JPEGThumbnailer, the  PixbufThumbnailer and the RawThumbnailer is also a good idea, especially  if you're often working with large RAW images (those can easily be  dozens of MB, creating thumbnails for a SD-card from a DSLR camera full  with raw images is probably not a good idea). You can also set Locations  (a list of directories, separated by ';') for each thumbnailer; by  setting something like  'Locations=~/Pictures/;/media/$USER/filesystem-label-or-UUID-of-a-specific-Flashdrive/'  you can stop tumblerd from running amok when you connect your camera  but still have it create thumbnails for a USB-HD you are using as a  picture archive ...

@[COLOR=#000000]oscarsanchezrequena[/COLOR]:  The behaviour shown in your video does not look like the effects of  slowdown thanks to tumblerd. I haven't seen anything like that before,  but it looks more like video driver trouble to me. What kind of video  hardware do you have and what driver are you using ? 

Holger

---

### Post by ajgreeny on 2021-04-28
@ Holger_Gehrke

Whoops! How right you are!
I used to edit this file in previous Xubuntu versions as I had a huge problem with tumbler using high cpu %ages which disappeared once I had made the edit to this file.
It was a long time ago and I had forgotten that I have not needed to make any edit on my 20.04 Xubuntu install which does not suffer in the same way.

Apologies to oscarsanchezrequena for any confusion; *mea culpa!*

---

