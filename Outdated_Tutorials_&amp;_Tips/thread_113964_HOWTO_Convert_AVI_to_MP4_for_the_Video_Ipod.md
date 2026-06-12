---
title: "HOWTO: Convert AVI to MP4 for the Video Ipod"
date: 2006-01-07
forum: Outdated Tutorials &amp; Tips
---

### Post by Baens on 2006-01-07
I have taken a AVI file and converted to the correct mp4 to put it onto my 30GB iPod. I have taken notes and heres what Ive come up with. I hope it helps!

First get the latest CVS with this:

```
cvs -z9 -d:pserver:anonymous@mplayerhq.hu:/cvsroot/ffmpeg co ffmpeg
```

This will make a ffmpeg dir and get all the needed files off the server (duh i guess but just explaining everything :))

You then get into that dir and need to configure the build. For some reason this part was the hardest for me to get. I had to run the following command before i ran the ./configure. This will pull everything ffmpeg needs and shouldn't give any build errors.

```
sudo apt-get build-dep ffmpeg
```

Make sure to have the sources in the repositories correct.

as well get the following 2 commands for libfaad-dev and libfaac-dev and the xvid librarys

```
sudo apt-get install libfaac-dev
```
```
sudo apt-get install libfaad2-dev
```
```
sudo apt-get install libxvidcore4-dev
```

Ok so ready to configure for build heres what i used:

```
./configure  --enable-gpl --enable-pp --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-faac --enable-xvid
```

Ok now lets build
```
make
```

Let it run through, takes a few minutes on a 2GHz

Once completed go ahead and install it with:

```
sudo make install
```

Done!

Now to convert here is the command I used, it doesnt do a great job at making the files smaller but it works as of right now and Im working on getting a better way of getting the files smaller

```
ffmpeg -y -i input.avi -b 768 -s 320x240 -vcodec xvid -ab 128 -acodec aac -ac 2 -ab 64 -f mp4 output.avi
```

And that is all to it! Took me about 10 minutes to convert a 45 minute show.

I hope this helps someone because I have been looking everywhere to find a solution to this. And if this doesn't help anyone...well umm Im sorry Im no help still a total newbie at this stuff.

~Baens

---

### Post by phyzome on 2006-05-04
All of that can be done in one step:
```
sudo apt-get install ffmpeg
```

---

### Post by RAOF on 2006-05-05
[QUOTE=phyzome]All of that can be done in one step:
```
sudo apt-get install ffmpeg
```[/QUOTE]
Except that the version of FFmpeg in the repositories is more than 6 months old, and the .mp4 muxer has seen some very heavy development over those 6 months.  (Read: it now will probably work ;)).

That said, there are a number of things not quite right: you're creating a file "output.avi" which is really an MP4 file - you should probably call it "output.mp4" instead.  And I think that you need some additional ratecontrol parameters - I believe that the command line you used will, under certain circumstances, produce files that the iPod can't play.  There's actually a iPod howto on this very board, and I think it gets that stuff right.

Might I in fact suggest [this howto]("http://www.ubuntuforums.org/showthread.php?t=114946&highlight=ipod+mp4")?

---

### Post by sudipta_cht on 2008-03-04
I found this link that seems easier to handle:
[http://www.ubuntu-unleashed.com/2007/08/howto-convert-videos-to-ipod-smartphone.html](http://www.ubuntu-unleashed.com/2007/08/howto-convert-videos-to-ipod-smartphone.html)

---

