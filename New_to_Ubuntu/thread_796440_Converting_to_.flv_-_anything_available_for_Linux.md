---
title: "Converting to .flv - anything available for Linux?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by getmeoutofhere on 2008-05-16
I want to convert video files to .flv, and I can't find anything suitable, that's not too difficult to use.  Ideally I don't want to use command lines, but I suppose I wouldn't mind if there were clear and simple instructions.  Thanks.

---

### Post by shifty_powers on 2008-05-16
[http://ubuntuforums.org/showthread.php?t=652843&highlight=flv+converter](http://ubuntuforums.org/showthread.php?t=652843&highlight=flv+converter)

---

### Post by shifty_powers on 2008-05-16
heh the search function is a wonderful thing :P

---

### Post by getmeoutofhere on 2008-05-16
Thanks for the reply.

Is there anything apart from Fuoco?  Can't get past the message, my attemtp to convert .avi to .flv, "Xterm: Can't execvp TO: No such file or directory". It doesn't seem to work.  I'm quite good at googling, and my search so far has been singularly unsuccessful.

---

### Post by aroch1 on 2008-05-16
VLC has pretty good transcoding abilities.

---

### Post by PinkFloyd102489 on 2008-05-16
ffmpeg can do it, but it's a terminal program.


If you do decide to use it, do this:

```
sudo apt-get install ffmpeg
```

Then to use ffmpeg, do this:

```
ffmpeg -i inputfile.whatever outputfile.whatever
```

Obviously replace the input and output files with what you're converting.

---

### Post by John Jason Jordan on 2008-05-16
[QUOTE=PinkFloyd102489;4975232
```
ffmpeg -i inputfile.whatever outputfile.whatever
```
[/QUOTE]
I just now tried to use ffmpeg to convert an .flv file to .mpg. The conversion went OK, except the .mpg has no sound and the resolution is way lower than the original.

I think the problem is that I know nothing of how video works, and I also know nothing of how ffmpeg works. I read its man page and did not understand much of it.

The first step would be to find the properties of the .flv file so that I can set the switches correctly in ffmpeg. Is there a way to find out the properties of an .flv file?

---

### Post by PinkFloyd102489 on 2008-05-16
I think the ffmpeg man page might have something, not entirely sure. I use ffmpeg to convert youtube videos (flv's) into usuable format, like mpg or avi.

---

### Post by John Jason Jordan on 2008-05-16
> **PinkFloyd102489 said:**
> I think the ffmpeg man page might have something, not entirely sure. I use ffmpeg to convert youtube videos (flv's) into usuable format, like mpg or avi.
That's what I want to do - convert Youtube .flv into .avi or .mpeg for use in an OpenOffice.org Impress slide. Not only do I need to convert it, but hopefully enhance the video as well. The .flv from Youtube is 320 x 240, which is pretty bad when seen on a big screen in a classroom.

Since posting the original query I have found avidemux. I managed to improve the video, but lost the sound in the process.

If you have the command line syntax to convert .flv to .avi with ffmpeg, please let me know, because I can't figure out the man page. And suggestions for any other tools for converting (and resampling the video) would also be gratefully received.

---

### Post by starcannon on 2008-05-16
Heres one of my favorite ffmpeg gui's it should get you up and going.

[http://www.biggmatt.com/winff/](http://www.biggmatt.com/winff/)

---

### Post by Faud on 2008-05-16
What are you doing in Fuoco tools. Ive used it flawlessly for exactly what you want literally 500 times.
You select the file that has been downloaded from youtube.com, then choose which resolution you want in the AVI section, choose a "download to" folder and click on the bird.
You can convert straight from flv to avi. If you get  a problem i would convert to avi same quality first then recode at avi high quality
Edit...just remember that file names in linux cant have spaces...any problems ive ever had, had to due with the filename.

---

### Post by John Jason Jordan on 2008-05-16
> **Faud said:**
> What are you doing in Fuoco tools. Ive used it flawlessly for exactly what you want literally 500 times.
You select the file that has been downloaded from youtube.com, then choose which resolution you want in the AVI section, choose a "download to" folder and click on the bird.
You can convert straight from flv to avi. If you get  a problem i would convert to avi same quality first then recode at avi high quality
Edit...just remember that file names in linux cant have spaces...any problems ive ever had, had to due with the filename.
What file do you download from youtube.com? That is, where do I get Fuoco?

---

### Post by John Jason Jordan on 2008-05-16
> **John Jason Jordan said:**
> What file do you download from youtube.com? That is, where do I get Fuoco?
Never mind. That is, I found Fuoco. Unfortunately, the .deb is only 32-bit, so we x86_64 users are out of luck for now. Unless someone knows where there is a 64-bit .deb or the source. Or maybe I could install it with --force-architecture. Has anyone got it installed on x86_64 Hardy?

---

### Post by Faud on 2008-05-16
I know that Fuoco tools has a website with some forums. You can check there to see if maybe someone has a 64 version.

---

### Post by forrestcupp on 2008-05-16
You could always use an online converter like [Zamzar](http://www.zamzar.com/).  Zamzar will allow you to either browse your hard drive for the video, or enter the url of the video.  You can convert almost any type of video to about any other format.  You can also convert to or from flv.  Then they email you the video.

---

### Post by 3rdalbum on 2008-05-16
Part of the reason why you can't get ffmpeg to convert a .flv to a .avi is because you don't understand what an AVI is.

AVI is just a file format, not a video format. It's a method of storing and interleaving audio and video. So, you could have DIVX format video and AAC format audio, for instance, in an AVI.

Okay. Having said that, I've made a program that converts video files (including FLV) to MP4 using ffmpeg. It requires a version of ffmpeg from the Medibuntu repository. (everything else it requires should be pulled in automatically when you install the .deb).

Go to Sourceforge and look for Blacklight Walkman Manager. Download it and install it. Create a directory called "VIDEO" (all uppercase) in your home directory. When you start it up, it will look for a walkman - just choose your home directory itself. Then tell it to "Acquire" a local file, and choose your file. Don't choose anything for "post-process". Click "Convert", and the file will be converted to MP4 and put into the "VIDEO" directory.

If this sounds a bit convuluted, it's because the program is really designed to encode video for the Sony Walkman, but this procedure lets you make files to keep on your computer.

---

### Post by John Jason Jordan on 2008-05-17
> **3rdalbum said:**
> Part of the reason why you can't get ffmpeg to convert a .flv to a .avi is because you don't understand what an AVI is.
AVI is just a file format, not a video format. It's a method of storing and interleaving audio and video. So, you could have DIVX format video and AAC format audio, for instance, in an AVI.
Okay. Having said that, I've made a program that converts video files (including FLV) to MP4 using ffmpeg. It requires a version of ffmpeg from the Medibuntu repository. (everything else it requires should be pulled in automatically when you install the .deb).
Go to Sourceforge and look for Blacklight Walkman Manager. Download it and install it. Create a directory called "VIDEO" (all uppercase) in your home directory. When you start it up, it will look for a walkman - just choose your home directory itself. Then tell it to "Acquire" a local file, and choose your file. Don't choose anything for "post-process". Click "Convert", and the file will be converted to MP4 and put into the "VIDEO" directory.
If this sounds a bit convuluted, it's because the program is really designed to encode video for the Sony Walkman, but this procedure lets you make files to keep on your computer.
Thanks for Blacklight. I got it installed and I used it to convert the .flv from Youtube to an MP4. And the MP4 plays fine in an Impress slide, at least on my Ubuntu laptop. Next step is to try it in OOo 2.2 on the computer in the classroom. 

But having said that, the resolution is no better than the original .flv file. I wonder if there is a utility that will upsample the video? That is, I already did so with avidemux, but the few times I succeeded in getting the video better I lost the sound. Maybe if I use the MP4 that Blacklight created I can do better now with avidemux.

Thanks again for Blacklight.

---

### Post by 3rdalbum on 2008-05-17
> **John Jason Jordan said:**
> But having said that, the resolution is no better than the original .flv file. I wonder if there is a utility that will upsample the video?

The resolution of 320x240 is hard-coded into the program because that is the resolution of the Walkman's screen.

If you don't mind changing the source code, you can have it upscale to 640x480 or any resolution you want. Bring up the source code in a text editor:

```
gksudo gedit /usr/bin/blacklight2.py
```

I can't remember if there's a variable or if it's hardcoded into the command that gets passed into ffmpeg, but at some part you should see a "320" and a "240". Changing these will change the resolution.

I'll be able to do the changes for you tonight when I get home, and send the new blacklight2.py file. I can't remember exactly how I've done it in the source code and I'm at work :-(

---

### Post by John Jason Jordan on 2008-05-17
> **3rdalbum said:**
> The resolution of 320x240 is hard-coded into the program because that is the resolution of the Walkman's screen.

If you don't mind changing the source code, you can have it upscale to 640x480 or any resolution you want. Bring up the source code in a text editor:

```
gksudo gedit /usr/bin/blacklight2.py
```

I can't remember if there's a variable or if it's hardcoded into the command that gets passed into ffmpeg, but at some part you should see a "320" and a "240". Changing these will change the resolution.

I'll be able to do the changes for you tonight when I get home, and send the new blacklight2.py file. I can't remember exactly how I've done it in the source code and I'm at work :-(
I think I can do it with other tools. The problem is not just changing the resolution but also de-noising it. I accomplished this with avidemux, but in the process lost the audio. There are too many options. If I keep poking at it I can probably get it to work.

---

### Post by Creative2 on 2008-05-17
--fuoco should works fine into 64 system too...
there is a video to install fuoco LOL for 64 system and 32 it's the same

---

### Post by billgoldberg on 2008-05-17
A poster mentioned winff and I second that program.

It uses ffmpeg but it adds a easy GUI to it.

So the program is **extremely easy** to use and works great.

But there is another program that will do it as easily, but also a lot more, the program is called pytube media converter

Read about it here:

[http://linuxowns.wordpress.com/2008/05/07/pytube-media-converter/](http://linuxowns.wordpress.com/2008/05/07/pytube-media-converter/)

---

### Post by John Jason Jordan on 2008-05-17
> **billgoldberg said:**
> A poster mentioned winff and I second that program.
But there is another program that will do it as easily, but also a lot more, the program is called pytube media converter
I tried to install WinFF, but there is no 64-bit .deb. Has anyone ever installed it with --force-architecture or by compiling from source?

Meantime, I installed pytube media converter and it does work fine. I used it to convert the .flv to .avi, and then to resize the .avi from the original 320 x 240 to 640 x 480. However, the resizing did not upsample the resolution. My problem is that I want to play an .flv from Youtube on the screen in a classroom. At a size of three meters by two meters or so it doesn't look very good.

I've accomplished the conversion. Now all I need is a tool to resample the resolution.

---

### Post by Creative2 on 2008-05-18
fuoco is only a script (like a txt ...)

the real program is **kommander** and kommander is a part of kde develop ..so i think it is works fine on 64 bit system...

try to install kommander :

**sudo apt-get install kommander **

if you able to install on 64 system you will be able to use fuoco ... there is a video that shows how to install from "source" 


anyway resizing a 320 to 640 is not a nice thing... you can't do this thinking to keep nice video quality...you could try but.... you could try to increase resolution to 1280 for 800 but this is absolutely crazy

---

### Post by ramjet_1953 on 2008-05-18
If you have no objections to running Windows applications under WINE, this free package works well.

[http://www.brothersoft.com/freez-flv-to-avi-mpeg-wmv-converter-59438.html](http://www.brothersoft.com/freez-flv-to-avi-mpeg-wmv-converter-59438.html)

Regards,
Roger :cool:

---

### Post by John Jason Jordan on 2008-05-18
> **Creative2 said:**
> the real program is **kommander** and kommander is a part of kde develop ..so i think it is works fine on 64 bit system...
try to install kommander :
I can install kommander easily, as it's listed in Synaptic. I have not done so yet because I don't understand why it will help with installing fuoco. For that matter, I am not even sure fuoco is what I need. (see below)

> **Creative2 said:**
> anyway resizing a 320 to 640 is not a nice thing... you can't do this thinking to keep nice video quality...you could try but.... you could try to increase resolution to 1280 for 800 but this is absolutely crazy
Let me clarify my problem, then perhaps someone can suggest what to do.

I have an .flv file from Youtube that is 320 x 240. It was recorded by someone with a webcam and the quality is not very good. It looks acceptable when I play it on my laptop (1680 x 1050), but I need to play it in front of a class on a large screen. I already tried it in the classroom and it is barely acceptable. The sound is OK, but the video is very rough.

Using pytube I changed the resolution from 320 x 240 to 640 x 480. The image was twice as large, but it looked just as bad on screen in the classroom. 

Using avidemux I applied noise filters to the file. Avidemux is hard to figure out - way too many options that I don't understand. However, I successfully enhanced the video so that it looks much better on screen, even at the original 320 x 240. Unfortunately, avidemux either has a bug or I failed to do something correctly, because I lost the sound. 

I think what I need is something like what you can do in Photoshop or the Gimp with a photograph - that is, you can enlarge it and in the process resample the pixels so you get more pixels. It's not perfect, but you can usually do a pretty good job of enlarging a raster image without it looking pixelated. 

Further suggestions welcome. Meantime, I'm looking for a forum or something for avidemux. Maybe if I can find a user list somewhere I can get some advice on how to use it properly. At this point it looks like my best shot.

---

### Post by Frak on 2008-05-18
```
sudo apt-get install ffmpeg2theora
ffmpeg2theora -a 5 filename.flv
```

Converting .flv to OggTheora

---

### Post by Creative2 on 2008-05-19
> **John Jason Jordan said:**
> I can install kommander easily, as it's listed in Synaptic. I have not done so yet because I don't understand why it will help with installing fuoco. For that matter, I am not even sure fuoco is what I need. (see below)


well i have not tested fuoco yet on 64 bit system but now you have confirmed kommander is on 64 bit repository i can tell you fuoco will work 99/100. Kommnader is fuoco's interpreter if it works fuoco works.  

> **John Jason Jordan said:**
> 
Let me clarify my problem, then perhaps someone can suggest what to do.

I have an .flv file from Youtube that is 320 x 240. It was recorded by someone with a webcam and the quality is not very good. It looks acceptable when I play it on my laptop (1680 x 1050), but I need to play it in front of a class on a large screen. I already tried it in the classroom and it is barely acceptable. The sound is OK, but the video is very rough.

Using pytube I changed the resolution from 320 x 240 to 640 x 480. The image was twice as large, but it looked just as bad on screen in the classroom. 

Using avidemux I applied noise filters to the file. Avidemux is hard to figure out - way too many options that I don't understand. However, I successfully enhanced the video so that it looks much better on screen, even at the original 320 x 240. Unfortunately, avidemux either has a bug or I failed to do something correctly, because I lost the sound. 

I think what I need is something like what you can do in Photoshop or the Gimp with a photograph - that is, you can enlarge it and in the process resample the pixels so you get more pixels. It's not perfect, but you can usually do a pretty good job of enlarging a raster image without it looking pixelated. 

Further suggestions welcome. Meantime, I'm looking for a forum or something for avidemux. Maybe if I can find a user list somewhere I can get some advice on how to use it properly. At this point it looks like my best shot.

i have perfectly understood your problem  and i can say this 

mencoder and ffmpeg can do what you need...

well resolution if you have encoded with avidemux and you think it's nice  you could do this

take the flv file and extract audio track with this command line

```
ffmpeg -i  'yourfile.flv' -vn -ac 2 -acodec copy  -y   'TRACK.mp3'
```

then mux audio track to your avi file (encoded with avidemux) with this :

```
mencoder INPUT.avi -oac copy -ovc copy -audiofile 'TRACK.MP3'  -o OUTPUT.avi 
```

well xD you can find this command line on fuoco tools anyway i hope this will work for you

if you  use computer to project   you could think to encode with ffmpeg2theora that convert file into ogg format with this

ffmpeg2theora -v 5 -a 5 -x 720 -y 576  INPUT -o OUTPUT

good luck creative

---

### Post by madhi19 on 2009-05-18
It kind of a moot point now that we can grab video in mp4 from Youtube. See my tutorial on how to best do it with a nice Firefox add-ons.
[http://ubuntuoneweek.blogspot.com/2009/05/firefox-youtube-and-avidemux.html](http://ubuntuoneweek.blogspot.com/2009/05/firefox-youtube-and-avidemux.html)

But I still have a truckload of flv file that I would like to convert to mp4 and not loose much if any resolution I know the standard code for ffmpeg but that does not do a great job.

---

