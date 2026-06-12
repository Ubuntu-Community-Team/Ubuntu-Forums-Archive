---
title: "FLV files into MP3"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by s.fox on 2008-06-28
Hi everyone.

I have recently made the switch from Vista to Ubuntu and just trying to find all the applications that would be useful to me.  I was wondering if their is an application in ubuntu that allows you to convert flv files (ideally youtube videos) into mp3.  I have been able to do it from terminal,  but i would much rather use some kind of gui.   

On my Vista PC i use the software from -[http://www.dvdvideosoft.com/products/dvd/Free-YouTube-to-iPod-Converter.htm]("http://www.dvdvideosoft.com/products/dvd/Free-YouTube-to-iPod-Converter.htm")

This software allows you to literally just paste in the youtube video url and click convert.  Something that simple is kind of what i am looking for.

The code i run in terminal in ubuntu to do the same thing is like this-

```
mplayer -dumpaudio test.flv -dumpfile nameofoutput.mp3 
```

The main problem with this is that i have to download the youtube video first,  whilst not a major problem is annoying after a while.

Thanks for any suggestions.

---

### Post by gn2 on 2008-06-28
I have used this free on-line service to do what you want: [http://www.mediaconverter.org/](http://www.mediaconverter.org/)

---

### Post by s.fox on 2008-06-28
Thanks for the quick response.

I suppose i could you online applications to do this.  In the past i have used [www.vixy.net](www.vixy.net) but would definitely  prefer an application that sits on my machine.

---

### Post by gn2 on 2008-06-28
I have found vixy to be unreliable often unavailable, the one in the link has given me much better results.

---

### Post by s.fox on 2008-06-28
I really wouldn't know how reliable vixy is these days,  as i have not used it in over a year.

---

### Post by RomeReactor on 2008-06-28
Hi. You might want to try PyTube ([homepage]("http://bashterritory.com/pytube/"), [download]("http://bashterritory.com/pytube/index.php?option=com_remository&Itemid=26&func=showdown&id=1")).

---

### Post by hexanol on 2008-06-28
And since Ubuntu and Linux-based operating system are about open source software and open standard, I would recommend you to convert your audio file to the (Ogg)[Vorbis]("http://en.wikipedia.org/wiki/Vorbis") open-format instead of the proprietary MP3 format.

---

### Post by s.fox on 2008-06-29
Thanks for the Pytube suggestion.   Exactly the kinda thing i was looking for.

I do however have a slight problem with it.  When i use it to convert a youtube url video into mp3 it doesn't play, :confused:.  I have checked the flv file it downloaded and that plays just fine.

Sorry to be a pain but does somebody have any idea what i am doing wrong?

---

### Post by sixgunSal on 2008-07-18
I have been using vixy on xp lately and have found it to be very reliable.  Is there a version for Ubuntu?  Since I have changed to Ubuntu, I have tried clive, but being new to all this, never did figure out how to use it.  thanks

---

### Post by Melindrea on 2008-07-18
This guide was quite helpful for me =)

[http://ubuntuforums.org/showthread.php?t=855433&highlight=yt2mp3]("http://ubuntuforums.org/showthread.php?t=855433&highlight=yt2mp3")

---

### Post by ad_267 on 2008-07-18
You can just use sound converter, it will convert the audio from the flv to mp3 or ogg.

sudo apt-get install soundconverter

Edit: Didn't read the part about wanting to use the youtube url, this won't be that helpful for that.

---

### Post by jamesrfla on 2008-07-18
I just tried [http://www.mediaconverter.org/](http://www.mediaconverter.org/) and it works great.

---

