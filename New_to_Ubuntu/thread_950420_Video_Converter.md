---
title: "Video Converter"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by Mr. Man on 2008-10-17
Could someone plz tell me about a good video format converter... I made a few videos of my desktop while i was doing some stuff with compiz fusion. I would like to convert them to my phone (N95 8GB) to show them to my friends and stuff. With windows i used to convert movies into the preffered format of my phone. I now have about 6 full length movies on my phone (i resized them when they converted. I haven't been able to find a good converter to good media converter ever since i downloaded ubuntu. Could you plz help me find one? 

Thanks

most important formats are:
.avi -> ???
.ogg -> ???

If you know what format(s) my phone works off the top of your head plz tell me...

---

### Post by billgoldberg on 2008-10-17
I googled your phone and some dude on a forum said:

```
Ive tried various MP4 files and they work fine (Tried DivX and H264).

Try converting your video to 320x240 H264 or MPEG4 using the Videora iPod converter:
```

I presume Videora iPod converter is some windows or osx app, so lets dismiss that.

I'm going to give you terminal commands, it's easier than explaining how to do it using the GUI.

In a terminal (applications -> add/remove) copy/paste this:

```
sudo apt-get autoremove ffmpeg --purge
```

Press enter, give your password and press enter again.

You might have to press "y" and enter when promted for it.

After that's done, copy/paste this:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install ffmpeg
```

When it's finished, go this website:

[http://code.google.com/p/winff/downloads/list](http://code.google.com/p/winff/downloads/list)

And download the winff-0.42-i386.deb file or the adm64.deb file depending on your computer.

If you aren't sure, download the i386 one.

After the file is downloaded, double click it to install.

Then in applications -> sound & video you'll see a program called "winff".

It's very easy to use, so use it to convert it to mp4 (divx or h264).

---

