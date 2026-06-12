---
title: "Is There a Video File Converter for Ubuntu 12.04"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by Melita on 2013-02-14
Is there a Free Video File Converter on the Internet, compatible with Ubuntu 12.04? This is to convert the format of a video file to another format.

Thank you.

---

### Post by GameX2 on 2013-02-14
I use AVConvert, it's a Nautilus-Script.

[https://dl.dropbox.com/u/67605655/avconvert](https://dl.dropbox.com/u/67605655/avconvert)

Mirror link:
[http://gnome-look.org/content/show.php/Audio%2BVideo%2BImage%2BText%2BISO+Convert?content=92533]("http://gnome-look.org/content/show.php/Audio%2BVideo%2BImage%2BText%2BISO+Convert?content=92533")

Place the script in ~/.gnome2/nautilus-scripts.

You can launch it by right-clicking and selecting the menu "Scripts".
I mean, the script is extremely powerful, and it's only 76KB! :O

It can convert multiple formats, not only videos, but also images, and music.

---

### Post by slickymaster on 2013-02-14
There's Handbrake, a video transcoder application, available for all platforms. It has lot of cool features and it supports variety of formats, so it can convert your video files for any devices you want.

To install it open a terminal and run these commands:
```
sudo apt-add-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake
```

---

### Post by mlentink on 2013-02-14
ffmpeg

---

### Post by deadflowr on 2013-02-14
> **mlentink said:**
> ffmpeg

Or the ffmpeg frontend winff.

---

### Post by Melita on 2013-02-14
> **deadflowr said:**
> Or the ffmpeg frontend winff.

I am new to Ubuntu and need more help. I went to these web pages. They say that winff is included in Ubuntu and to install it from the package manager. How do I set about doing this please? 

This will suit me only if it can convert video formats,** specially the blu-ray formats**,  to the AVI formats. Can this do it?

Regards.

---

### Post by HermanAB on 2013-02-14
VLC, mplayer, ffmpeg, handbrake...

---

### Post by FakeOutdoorsman on 2013-02-14
> **Melita said:**
> This will suit me only if it can convert video formats,** specially the blu-ray formats**,  to the AVI formats. Can this do it?

AVI is a container format that can contain a larger number of video and audio formats. Also it is quite dated. Is there a specific reason you want or need AVI? See [What is a Codec (e.g. DivX?), and how does it differ from a File Format (e.g. MPG)?](http://superuser.com/a/300997/110524) for more info.

---

### Post by stuckeyneila1982 on 2013-02-14
+1 to Handbrake works pretty well.  can make some pretty good compressed videos. My windows box runs handbrake + handbrake batch video and when utorrent downloads a video it drops in a directory and handbrake batch converter sees the new file it auto converts it to .MP4 h.264 then drops it from there to my Ubuntu file server / streaming box automatically, then i can play it on my flat screen with a WD tv Live from the Ubuntu shared folder via Samba.  Pretty sweet setup without much hassle.  Not sure how you would batch convert in ubuntu probably with ffmpeg and terminal some how that's beyond my skill level.  I don't download movies from torrents  anymore got the letter of doom.

not sure why you would want anything other than .MP4 h.264 pretty much the standard movie container and codec for internet or device use these days.

Sorry to keep posting. But you dont really want to compress a video that has been already compressed.  In handbrake you can make a 1 to 1 copy and just change the container and  format.  otherwise it will look like poo.  fuzzy and the black areas will look like moving checker boards.  You cant take a poor quality video and make it look good by re encoding either.  If the source video sucks it will keep sucking no matter what, whether blue ray, DVD or any format.  But FFMpeg is the best but hard to use unless you have a GUI front end.  handbrake probably #2 just cuz your options are limited.  FFMpeg will go as far as you can.

---

### Post by sbnwl on 2013-02-15
Arista Transcoder?

```
sudo apt-get install arista
```

---

### Post by Melita on 2013-02-15
> **FakeOutdoorsman said:**
> AVI is a container format that can contain a larger number of video and audio formats. Also it is quite dated. Is there a specific reason you want or need AVI? See [What is a Codec (e.g. DivX?), and how does it differ from a File Format (e.g. MPG)?]("http://superuser.com/a/300997/110524") for more info.

  I am not fond of watching movies on the computer. I have a little media player that is always connected to my TV. I download a movie, put it in a USB drive, connect the USB to the media player and watch on the TV. This is a simple method and easily done on Windows.  Sometimes the movie is in Blu-ray or MKV format, which the media player cannot read. I use Format Factory and Iwisoft Free Media Converter to change the format to Xvid, Divx or RMVB which the Media player is comfortable with. All this is in Windows. I need a format converter for my Ubuntu 12.04 which is what I mostly use. I tried opening iwisoft (which I have in a USB drive), in Ubuntu but it does not open.  Regards.

---

### Post by FakeOutdoorsman on 2013-02-15
What is the brand/make and model of this media player?

---

### Post by Melita on 2013-02-15
It is a cheap item I picked up from ebay for $20. Came from China. The name is HD Media Player, which of course means nothing! It performs perfectly in every way except with Blu-ray and MKV. It comes up with a notice that the file type is not compatible, when I try to play one of those. The 'instructions' that came with it also says these file formats are not compatible.  Regards.

---

### Post by Hampster on 2013-02-15
I am watching this thread with interest as I have a similar problem with a Video MP3 player and my inability to convert video files.

Enuff said I don't want to hyjack the thread.

---

### Post by FakeOutdoorsman on 2013-02-15
andrew.46 has a good ffmpeg example command that I suspect will work on these picky devices: [video format conversion](http://ubuntuforums.org/showpost.php?p=12418095&postcount=3).

Note that will may need to install the **libavcodec-extra-5*** package to enable the MP3 encoder.

---

### Post by Melita on 2013-02-18
Thank you for all the help and suggestions.  Best regards to all.

---

