---
title: "converter for .mkv to .avi"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-09-05
hello,i am a user of hardy.i want to covert a .mkv file to .avi.how do i do this?i mean i need a converter with a GUI so that i can do that easily.please suggest me names.thanx in advance.

---

### Post by tuxulin on 2008-09-05
in terminal
it has no gui but it works
sudo apt-get install mkvtoolnix


Tuxulin

---

### Post by Alexander Lindskog on 2008-09-05
If you have worked with VirtualDub(Mod) under Windows and you're looking for a graphical tool you should feel right at home with Avidemux. It supports .avi & .mkv among other formats.

You find it in Synaptic

---

### Post by tuxulin on 2008-09-05
along with the above post i have just tried
sudo apt-get install mkvtoolnix mkvtoolnix-gui

and it installed... however i have never used this prog before

Tuxulin

---

### Post by lovinglinux on 2008-09-05
Converting a video file usually requires re-encoding, which means saving the file with another codec. But this is not the case, because mkv's and avi's are just containers.

You can use MKVToolnix to extract the video file from the mkv container, without re-enconding, and saving it as avi. This process is much faster than converting for example an xvid file to h.264 and there is no quality loss. Unfortunately, the mkvtoolnix-gui is designed to create mkv's and not to extract the contents of it. So you will have to use command line. There is a [GUI for MKVextract]("http://coreforge.org/projects/mkvextractgui/"), but I'm not sure how to install on Linux. Both methods will produce a video file and an audio file. Then you have to join them....toooo complicated!

The easiest way of "converting" a mkv file to avi is using Avidemux
```

sudo apt-get install avidemux
```

Open the mkv file on Avidemux. Select "Copy" in the video and audio settings on the left. This will guarantee that the video and the audio are not re-encoded. Then select AVI in the format settings (last button on the left). I guess these are the default settings. Then hit CTRL+S to save it. Choose a name for it and hit "Save". 

This should copy the video and the audio from the mkv file and save it as an avi file, without re-encoding. It will take about 10 seconds to "convert" a 700Mb video. There will be no quality loss whatsoever, but the avi file will be just a little bit bigger than the original mkv (not enough to make you worry about it).

---

### Post by stonecoldjha on 2008-09-07
yea,the conversion is taking palce,but the avi file thai i get did not have any audio.

---

### Post by lovinglinux on 2008-09-07
> **stonecoldjha said:**
> yea,the conversion is taking palce,but the avi file thai i get did not have any audio.

Try doing the same process with an AVI file instead, just to check if the converted file has audio.

MKV's can contain multiple audio tracks, subtitles and other stuff, so maybe the program is not recognizing the audio track or the configuration is wrong.

---

### Post by underground on 2008-09-28
> **lovinglinux said:**
> 
The easiest way of "converting" a mkv file to avi is using Avidemux
```

sudo apt-get install avidemux
```

Open the mkv file on Avidemux. Select "Copy" in the video and audio settings on the left. This will guarantee that the video and the audio are not re-encoded. Then select AVI in the format settings (last button on the left). I guess these are the default settings. Then hit CTRL+S to save it. Choose a name for it and hit "Save". 

This should copy the video and the audio from the mkv file and save it as an avi file, without re-encoding. It will take about 10 seconds to "convert" a 700Mb video. There will be no quality loss whatsoever, but the avi file will be just a little bit bigger than the original mkv (not enough to make you worry about it).

I did what you said but i have audio but no video in vlc..in other players it plays fine

---

### Post by lovinglinux on 2008-09-28
> **underground said:**
> I did what you said but i have audio but no video in vlc..in other players it plays fine

This is weird, because vlc is capable of playing almost anything. Try converting the video instead of just copying it. This is much more time consuming than simply copying the video stream.

---

### Post by psypher on 2008-10-05
Hi,

I have been struggling with this problem as well. Every place I find info on is either incomplete or does not mention the errors I receive or the authors don't comment on other people who have the same errors. I have tried using ffmpeg and avidemux and both of them give me different issues. I would prefer to get a cli program like ffmpeg to work but right now I just want something to work. 

When i try your method using avidemux I first get this pop-up when opening the mkv file:

H264 detected

If the file is using bframe as reference, it can lead to crash or stutteting.
Avidemux can use another mode which is safed but YOU WILL LOOSE FRAME ACCURACY.
Do you want to use that mode ?

My choices are "cancel" or "use that mode" 

tried either way still have the same result. Once I have converted the video to avi and try play it with totem i get the following error:

Totem could not play "the viedo i am tryting to play"

Video codec 'AVC1' is not handled. You might need to install additional plugins to be able to play some types of movies

Cannot find anything on that error. 

What am I doing wrong?

Thanks

---

### Post by m_eoin on 2008-10-17
Hi,

I had the exact same problem as you and like you said there is not a wealth of information about this issue. For that reason I decided to seek another solution.
I am now using the program DeVeDe (available from the Synaptic Manager). It basicall burns the .mkv to a DVD that you can view on a normal DVD player.

There is a option to convert directly to a .avi but when I played this in my media player for some reason the audio was off by around 4 seconds. If I find the solution to this I will let you know.

Anyway hope this helps and let me know if you need any more information regarding this let me know. I include a website which helped me get started.
[http://blogcritics.org/archives/2007/02/05/150718.php](http://blogcritics.org/archives/2007/02/05/150718.php)

---

### Post by aktiwers on 2008-10-17
WinFF
[http://code.google.com/p/winff/](http://code.google.com/p/winff/)

---

