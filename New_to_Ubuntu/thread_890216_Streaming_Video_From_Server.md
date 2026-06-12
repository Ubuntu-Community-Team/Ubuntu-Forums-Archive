---
title: "Streaming Video From Server"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by moose4204l on 2008-08-14
Ok, I have access to my server. As of now I browse to http://<ip addr>/my_files and i get a list of the files I have on my server. I want to be able to click on a video and have it stream right there like Youtube does or VEOH. something like that, so they dont have to download it or anything. I also have a dvd.iso file. Do i need to convert that over to an avi or something or can an .iso file stream from the site?

thanks

---

### Post by moose4204l on 2008-08-14
bump

---

### Post by willskills on 2008-08-14
> **moose4204l said:**
> Ok, I have access to my server. As of now I browse to http://<ip addr>/my_files and i get a list of the files I have on my server. I want to be able to click on a video and have it stream right there like Youtube does or VEOH. something like that, so they dont have to download it or anything. I also have a dvd.iso file. Do i need to convert that over to an avi or something or can an .iso file stream from the site?

thanks

Then you need to install a streaming media server.

Try; [http://osflash.org/red5](http://osflash.org/red5) - for Flash (Youtube style, you'll need to convert your video to FLV format)

Or; [http://developer.apple.com/opensource/server/streaming/index.html](http://developer.apple.com/opensource/server/streaming/index.html) for .mov or 3gp format.

or VLC, there are many - google is your friend :)

---

### Post by moose4204l on 2008-08-14
i installed the ubuntu server edition. i need extra server stuff for this?

edit: i tried download vls but the server box is text only. so when i ran vls.. No configuration file found (vls.cfg)..came up

---

### Post by willskills on 2008-08-14
Yes - server edition just comes with a few different packages than the normal edition of ubuntu. (and no GUI) - to get a GUI, type 'sudo apt-get install ubuntu-desktop' at your terminal.

You should go to [http://www.ubuntu.com/](http://www.ubuntu.com/) and read the differences between Desktop and Server Edition.

EDIT - What is VLS?

I meant you should take a look at VLC - [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by moose4204l on 2008-08-14
> **willskills said:**
> Yes - server edition just comes with a few different packages than the normal edition of ubuntu. (and no GUI) - to get a GUI, type 'sudo apt-get install ubuntu-desktop' at your terminal.

You should go to [http://www.ubuntu.com/](http://www.ubuntu.com/) and read the differences between Desktop and Server Edition.

EDIT - What is VLS?

I meant you should take a look at VLC - [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

i know, i been looking at vlc and im still lost. im a complete noob at this and i am learning as i go. right now i am trying to follow [http://www.n00tz.net/2008/07/vlc-media-server-ubuntu-hardy/](http://www.n00tz.net/2008/07/vlc-media-server-ubuntu-hardy/)
but i dont know if im following it right. so any help you can give is great

---

### Post by moose4204l on 2008-08-18
anyone, i want to have a my files stream in a video player or music player on the website when you click it.

---

### Post by billgoldberg on 2008-08-18
> **moose4204l said:**
> anyone, i want to have a my files stream in a video player or music player on the website when you click it.

Right-clicking the file an choosing open with totem should stream the video or mp3.

At least, that works with ssh and worked with my mp3 server using the web interface.

---

### Post by moose4204l on 2008-08-18
> **billgoldberg said:**
> Right-clicking the file an choosing open with totem should stream the video or mp3.



this will download it i think and then play it. I want it to stream from the website with a media player like youtube, or music like lastfm, thins like that

---

### Post by Dill on 2008-08-18
You could check out the Darwin Streaming Server:

[http://ubuntuforums.org/showthread.php?t=346292](http://ubuntuforums.org/showthread.php?t=346292)

I've never tried to set this up myself, but it looks like it may work for you.

---

### Post by FakeOutdoorsman on 2008-08-18
You need to install Apache or lighttpd and then a Flash web video player (if you're using Flash like Youtube does).  My favorite player is [Flowplayer]("http://flowplayer.org/").  It's free, updated often, and is easy to use.  You also need to convert your videos to a format and codec that will work with the video player, such as flv or f4v with codecs like h264, MPEG-4, VP6, or Sorensen.  I use ffmpeg to convert videos to these formats, but getting into ffmpeg is a whole thread in itself.  Take a look at this:

[Build Your Own Video Community With Lighttpd And FlowPlayer (Debian Etch)]("http://www.howtoforge.org/video_streaming_lighttpd_flowplayer")

It's a year old article and things have changed with Flash, like h264 video playback capability, but it should give you a good start.  I recommend skipping the ffmpeg section since they are using an ancient version of ffmpeg and installing it yourself either by using the Medibuntu repository, or if you like the bleeding edge or feel like procrastinating you can compile ffmpeg yourself:

[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by Francewhoa on 2009-07-03
There's an easier way. You can watch full Veoh videos with the 'Illimitux' plug-in for Firefox. Read more at [http://ubuntuforums.org/showthread.php?p=7554700#post7554700](http://ubuntuforums.org/showthread.php?p=7554700#post7554700)

---

