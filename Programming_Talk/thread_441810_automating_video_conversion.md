---
title: "automating video conversion"
date: 2007-05-12
forum: Programming Talk
---

### Post by JugglesGeese on 2007-05-12
Hi all...

I've installed and configured a program called 'Galleon' which is a home media server that connects to TiVo and has the ability to grab video and transfer it from the TiVo to the PC (much like the TiVo desktop under windows).  Galleon dumps the video into a specified directory.  I want to automatically run 'tivodecode' and 'ffmpeg' on those TiVo files so there will be a mp4 file waiting to be written to my iPod as soon as i sit down in front of my PC. So in essence, I want to write a script/program that will check to see if there are any mpeg files in the TiVo directory and then run the conversion programs on each of those files in turn. Then I can just use a cron/at job to schedule it to run every fifteen minutes or so.

How would I go about this?  I've looked through some shell scripting tutorials, but I can't seem to find what I'm looking for. I'm also new to shell scripting, but I've been programming OO under windows for years, so I understand the concepts well enough...it's just that I'm a complete newbie to any kind of linux programming.  

Any help would be appreciated.

---

### Post by loboc on 2009-01-25
> **JugglesGeese said:**
> Hi all...

I've installed and configured a program called 'Galleon' which is a home media server that connects to TiVo and has the ability to grab video and transfer it from the TiVo to the PC (much like the TiVo desktop under windows).  Galleon dumps the video into a specified directory.  I want to automatically run 'tivodecode' and 'ffmpeg' on those TiVo files so there will be a mp4 file waiting to be written to my iPod as soon as i sit down in front of my PC. So in essence, I want to write a script/program that will check to see if there are any mpeg files in the TiVo directory and then run the conversion programs on each of those files in turn. Then I can just use a cron/at job to schedule it to run every fifteen minutes or so.

How would I go about this?  I've looked through some shell scripting tutorials, but I can't seem to find what I'm looking for. I'm also new to shell scripting, but I've been programming OO under windows for years, so I understand the concepts well enough...it's just that I'm a complete newbie to any kind of linux programming.  

Any help would be appreciated.

Try modifying this bash script

[https://www.linuxquestions.org/questions/linux-software-2/script-to-automatically-convert-video-files-using-ffmpeg-610874/](https://www.linuxquestions.org/questions/linux-software-2/script-to-automatically-convert-video-files-using-ffmpeg-610874/)

---

### Post by bruce89 on 2009-01-25
I like to use GStreamer for this sort of thing, ffmpeg reimplements each codec instead of using the original libraries like GStreamer does.

```
gst-launch-0.10 filesrc location=$input ! decodebin name=decode ! xvidenc pass=3 quantizer=6 gmc=true lumimasking=true ! matroskamux name=mux ! filesink location=$input.mkv decode. ! queue ! audioconvert ! audioresample ! audio/x-raw-float,rate=24000 ! vorbisenc quality=0.3 ! mux.
```

Obviously you'd need to change the elements in the pipeline to do what you want, see the output of *gstreamer-inspect-0.10* for the elements you have.

---

