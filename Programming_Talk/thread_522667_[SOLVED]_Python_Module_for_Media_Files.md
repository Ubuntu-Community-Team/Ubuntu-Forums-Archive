---
title: "[SOLVED] Python Module for Media Files??"
date: 2007-08-10
forum: Programming Talk
---

### Post by WinterWeaver on 2007-08-10
Hey everyone!

I'm looking for a python module that can read media file information, like the length, bitrate, etc. of media files. (more specifically mp4 and mpg files).

I need to write a small program that can take this information and write it to a XML file. It's best if this module can work cross platfrom between linux and windows, cause at work we use both.

Thanks in advance ^_^

ps. I haven't written code in about 8 years... only picked up again about 2 weeks ago :P

WW

---

### Post by apetresc on 2007-08-11
I know the python-id3 package will read id3 tags fine (the format most commonly used in audio files.) I'm not sure what metadata format video files use, but maybe it's the same. You can try it with ```
sudo apt-get install python-id3
``` and a little code sample is available at: [http://id3-py.sourceforge.net/](http://id3-py.sourceforge.net/) . The API seems super-simple to me.

---

### Post by WinterWeaver on 2007-08-11
Thanks, I'll give it a go. However I don't think it will help, as I need to extract actual video information, like the bitrate, video size, length, channels etc.

I think I'm going to try and use ffmpeg in the meantime to extract the information. I have no idea what I'll use in windows though.

Thanks for the info on ID3 module though.

WW

---

### Post by ssam on 2007-08-11
you might be able to do it with gstreamer

---

### Post by UbuWu on 2007-08-11
[PyMedia]("http://pymedia.org/") might be helpful.

---

### Post by UbuWu on 2007-08-11
Found a better one: [kaa-metadata]("http://freevo.sourceforge.net/cgi-bin/freevo-2.0/Kaa") does exactly what you want! :KS

---

### Post by WinterWeaver on 2007-08-11
Thanks!! Kaa seems like it's exactly what I need ^_^

Thanks for everyones help !! :)

---

