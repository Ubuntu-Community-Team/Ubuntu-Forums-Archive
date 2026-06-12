---
title: "SOXObjective measure of sound file quality (consolidating music collection)"
date: 2012-06-02
forum: New to Ubuntu
---

### Post by pcvchriskmg on 2012-06-02
Hi,

I have about 20,000 music files in my collection, from many different sources. I have many duplicate songs from differing sources.

Can I use SOX to analyze and compare two sound files, and then choose the one of "higher quality"? I am interested in consolidating my collection and retaining the files that sound the best.

For example, if I have 2 songs and they are both 128 kbps, stereo, and the same Hz, is there some other measure of quality I can use? I've heard of "Total Harmonic Distortion" but know who to measure that.

Perhaps I'm not thinking about this the right way, so any and all suggestions are welcome.

In the spirit of full disclosure, I also posted this question in another forum, looking for a windows or Ubuntu solution:

[http://forums.techguy.org/multimedia/1055583-objective-measure-sound-file-quality.html#post8371059](http://forums.techguy.org/multimedia/1055583-objective-measure-sound-file-quality.html#post8371059)

Thanks!

Chris

---

### Post by Senior_Buckethead on 2012-06-04
I dont know about SOX but I know about ffmpeg which can convert your sound files to any bitrate you like and have alot of additional functionality, might be worth a look. Its a command line app, but you can get winff wich is a gui front to ffmpeg.

Both can be obtained via. apt-get.

Still, its not  the answer you were searching for, hopefully someone more experienced than me will give you a better answer.

All the best.

---

### Post by andrew.46 on 2012-06-06
SoX will show some basic information on the files using the *soxi* command:

```

andrew@skamandros~/media/ftgws$ **[COLOR="Red"]soxi ftgws_29042012.ogg ftgws_20052012.ogg [/COLOR]**

Input File     : 'ftgws_29042012.ogg'
Channels       : 2
Sample Rate    : 48000
Precision      : 16-bit
Duration       : 02:11:55.86 = 379961344 samples ~ 593690 CDDA sectors
File Size      : 154M
Bit Rate       : 155k
Sample Encoding: Vorbis
Comments       : 
title=29-04-2012
artist=Stephen Watkins
album=For the God Who Sings


Input File     : 'ftgws_20052012.ogg'
Channels       : 2
Sample Rate    : 48000
Precision      : 16-bit
Duration       : 02:11:54.84 = 379912192 samples ~ 593613 CDDA sectors
File Size      : 150M
Bit Rate       : 152k
Sample Encoding: Vorbis
Comments       : 
title=20-05-2012
artist=Stephen Watkins
album=For the God Who Sings

Total Duration of 2 files: 04:23:50.70

```

Not sure if this is enough for you though?

---

### Post by FakeOutdoorsman on 2012-06-08
> **pcvchriskmg said:**
> For example, if I have 2 songs and they are both 128 kbps, stereo, and the same Hz, is there some other measure of quality I can use?

I don't have a solution, but remember that not all encoders are equal in output quality despite both files sharing similar bitrates, etc.

---

