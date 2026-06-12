---
title: "[SOLVED] i need an app"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by DarinB on 2008-11-04
I need an application that will convert flv to to video for ipod and convert to an mp3 so i can hear the sound track. i am running intrepid

---

### Post by wizard10000 on 2008-11-04
> **DarinB said:**
> I need an application that will convert flv to to video for ipod and convert to an mp3 so i can hear the sound track. i am running intrepid

You can use ffmpeg to convert the video - look here

[http://www.ubuntugeek.com/convert-flv-google-videos-to-mpg-using-ffmpeg.html](http://www.ubuntugeek.com/convert-flv-google-videos-to-mpg-using-ffmpeg.html)

and you can convert .flv to mp3 like this -

ffmpeg -i movie.flv -f mp3 sound.mp3

good luck!

---

### Post by tomcheng76 on 2008-11-04
what is the video format for ipod?
i don't own ipod ,lol

you can use ffmpeg to convert flv to mp3
To install:
```
sudo apt-get install ffmpeg
```

To convert:
```
ffmpeg -i videoname.flv -vn -acodec copy videoname.mp3
```

---

### Post by click4851 on 2008-11-04
i think "handbrake" is a gui for ffmpeg, if you are so inclined.

---

### Post by DarinB on 2008-11-04
i installed the app then when i cd to the file where the video is then when i add the video name it comes up no file found
here is the print out
darin@darin-desktop:~$ ffmpeg -i Obama Acceptance DNC.flv -vn -acodec copy Obama Acceptance DNC.mp3
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Obama: no such file or directory
darin@darin-desktop:~$

---

### Post by wizard10000 on 2008-11-04
> **DarinB said:**
> i installed the app then when i cd to the file where the video is then when i add the video name it comes up no file found...

Enclose the filenames in single quotes like this - terminal doesn't like spaces in filenames  :)

```
ffmpeg -i 'Obama Acceptance DNC.flv' -vn -acodec copy 'Obama Acceptance DNC.mp3'
```

---

### Post by timcredible on 2008-11-04
you might also want to install winff, it's a gui front end for ffmpeg and has many presets, including ipod.

---

### Post by DarinB on 2008-11-04
still wont work with quotes teh s winff converts to wav but i  don't know where it ended up i want an mp3 and winff won't give me that option

darin@darin-desktop:~$ cd Videos
darin@darin-desktop:~/Videos$ ffmpeg -i 'Obama Acceptance DNC.flv' -vn -acodec copy 'Obama Acceptance DNC.mp3'
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Obama Acceptance DNC.flv: no such file or directory
darin@darin-desktop:~/Videos$

---

### Post by DarinB on 2008-11-04
it ended up in my home folder which is fine but how do i get it to make me an mp3

---

### Post by aktiwers on 2008-11-04
Try winff
[http://code.google.com/p/winff/](http://code.google.com/p/winff/)

Very nice app

---

### Post by DarinB on 2008-11-04
it works great and my ipod plays wav but how do i get it to make an mp3 via the gui winff i can't get the cli to work to convert to mp3???

---

### Post by aktiwers on 2008-11-04
Pick Audio then Mp3 in Winff?

---

### Post by DarinB on 2008-11-05
in convert to  audio is fine but mp3 is not an option 
the options are Ac3 DVD 192kbs stereo
                Ac3 DVD 384kbs stereo
                Wav for CD
                WMA
no choice for mp3 do i need to add something as iblame in audacity????

---

### Post by DarinB on 2008-11-05
Am i missing codex for the conversion options???????????????

---

