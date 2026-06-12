---
title: "HOWTO make a photo dvd"
date: 2007-03-03
forum: Outdated Tutorials &amp; Tips
---

### Post by mapalma on 2007-03-03
Download dvd-slideshow
[http://downloads.sourceforge.net/dvd-slideshow/dvd-slideshow-0.8.0-1_all.deb?modtime=1168802075&big_mirror=0](http://downloads.sourceforge.net/dvd-slideshow/dvd-slideshow-0.8.0-1_all.deb?modtime=1168802075&big_mirror=0)

Install tools
$ apt-get install mjpegtools sox dvdauthor

Image list
dir2slideshow -n 'My Photos' -t 15 /dir_photos (-n, title; -t  time)

Example

background:0::black
background:1
fadein:1
title:15:prueba
background:0::black
fadeout:1
background:2
fadein:1
/home/mapalma/fotos/1.jpg:15
fadeout:1
/home/mapalma/fotos/2.jpg:15
fadein:1
/home/mapalma/fotos/3.jpg:15
crossfade:2
/home/mapalma/fotos/4.jpg:15
fadeout:3
/home/mapalma/fotos/5.jpg:15
fadeout:1
background:2

Make video
dvd-slideshow -n 'My  Photos' -f list.txt -a 'my_music.ogg'

Make output dir 
$ mkdir salidamenu

dvd-menu -o outputmenu -t 'Option Menu 1' -f my_photos.xml -n 'My Photos'

make other .xml for more options menu

k3b > File > New Project > New Video Dvd project.
and burn dvd


Aditional tools (convert mp3 to ogg)
sudo apt-get install soundconverter
sudo apt-get install vorbis-tools

Vob to avi or mpeg
apt-get install ffmpeg
ffmpeg -i video.vob video.mpg/avi

---

### Post by schumifer on 2007-03-05
Excellent work my friend. I would recommend to all interested to also take a good look at this
[http://dvd-slideshow.sourceforge.net/wiki/Complete_Example](http://dvd-slideshow.sourceforge.net/wiki/Complete_Example)

A word of caution. If you want to use multiple folders with pictures, go ahead and do so. Just remember not to create more than 1 vob at a time cause you might have a error in multiplexing. You will get you vob alright but not your xml

---

### Post by mj295 on 2008-02-14
Got this far:

[dvd-slideshow]            dvd-slideshow 0.8.0-pre10
[dvd-slideshow]            Licensed under the GNU GPL
[dvd-slideshow]            Copyright 2003-2006 by Scott Dylewski
[dvd-slideshow]            
[dvd-slideshow] Output directory not specified.
[dvd-slideshow] Using /home/mark
/usr/bin/dvd-slideshow: line 3418: convert: command not found
[dvd-slideshow] ERROR:  no ImageMagick found for audio processing
[dvd-slideshow]         You need to download and install ImageMagick.
[dvd-slideshow]         [http://ImageMagick.sourceforge.net](http://ImageMagick.sourceforge.net)
[dvd-slideshow] cleanup...


Will have a dig around.

---

### Post by raulrm on 2011-02-10
Imagination
[http://imagination.sourceforge.net/](http://imagination.sourceforge.net/)

---

### Post by geazzy on 2011-07-02
nice how to... :D

---

