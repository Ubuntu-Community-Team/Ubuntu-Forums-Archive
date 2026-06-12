---
title: "problems using ffmpeg"
date: 2013-03-22
forum: Programming Talk
---

### Post by IAMTubby on 2013-03-22
Hi,
I am trying to {download an mp3 file from youtube} OR {download a video and then convert it to mp3}. I'm unable to do both probably because of ffmpeg.
I have tried the following so far


1. youtube-dl -o ubuntu.flv [http://www.youtube.com/watch?v=LoXpLUr5WB4](http://www.youtube.com/watch?v=LoXpLUr5WB4) --audio-format=mp3
**strange, but gives me only the flv**


2. Tried without the = also as
youtube-dl -o ubuntu.flv [http://www.youtube.com/watch?v=LoXpLUr5WB4](http://www.youtube.com/watch?v=LoXpLUr5WB4) --audio-format mp3
**again, only downloaded the flv**


3. Tried first downloading the flv/mp4 and then converting to audio. as 
[COLOR=#000000][FONT=Consolas]ffmpeg -i filename.flv filename.mp3
[/FONT][/COLOR]This does generate a file called filename.mp3 , but of size 0. Please find attached the log file of ffmpeg  

And this is the ls output of my audio file
**-rw-rw-r-- 1 IAMTubby IAMTubby 0 2013-03-23 08:18 myaudio.mp3**

4.***I also went to this link [http://ubuntuforums.org/showthread.php?t=1084538&p=8370224#post8370224](http://ubuntuforums.org/showthread.php?t=1084538&p=8370224#post8370224) where OP was facing similar problem . His solution was to do [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install libavcodec-unstripped-52[/FONT][/COLOR] . I did the same but it gives me E: Unable to locate package libavcodec-unstripped-52. I have multiverse enabled. And I have done sudo apt-get upgrade && sudo apt-get update also. Why am I not able to do it ? Please find attached my copy of /etc/apt/sources.list just to see that my multiverse is enabled.*** 

Please advise,
Thanks.

PS : I tried the extract audio options in youtube-dl, youtube-dl [http://www.youtube.com/watch?v=kYfNvmF0Bqw](http://www.youtube.com/watch?v=kYfNvmF0Bqw) --extract-audio and it works too. But it gives me a file type called m4a that I cannot play in my mp3 player that I find it hardly useful.

---

### Post by IAMTubby on 2013-03-23
Okay, got it working.
I did sudo apt-get install ubuntu-restricted-extras and got it to work.

So , if you are stuck with the same problem some time, steps would be something like :
1. Make sure multiverse is checked from SystemTools -> SystemSettings -> SoftwareSources.
2. sudo apt-get update(make sure that you have updates from main, restricted. universe and multiverse)
3. sudo apt-get install ubuntu-restricted-extras
    This is necessary because you actually need to do [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install libavcodec-unstripped-52 [/FONT][/COLOR] but I was, and still am unable to install this. **It says E: Unable to locate package libavcodec-unstripped-52**. So to overcome this, we do sudo apt-get install ubuntu-restricted-extras. This install a whole lot of things, of which one is ffmpeg.
4. Finally, ffmpeg -i videofile.flv filename.mp3

But if someone could tell me why I'm unable to do [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install libavcodec-unstripped-52[/FONT][/COLOR] , it would be great.
Thanks

---

### Post by FakeOutdoorsman on 2013-03-23
For Ubuntu 11.10 you needed **libavcodec-extra-53**. The package name can vary depending on your Ubuntu version.

---

### Post by IAMTubby on 2013-03-23
> **FakeOutdoorsman said:**
> For Ubuntu 11.10 you needed **libavcodec-extra-53**. The package name can vary depending on your Ubuntu version.
Bingo, thanks FakeOutdoorsman.
Would have marked thread as solved but I guess the feature is not active yet on the new site.

---

