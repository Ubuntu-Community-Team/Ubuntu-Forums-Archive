---
title: "mp3 compressor"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by bkamalnivas on 2008-06-23
Is there any software that would compress my MP3s effectively??
(need for my mp3 player....)

---

### Post by Nikitas350 on 2008-06-23
See this: soundconverter.berlios.de
You can install it by running this command in terminal:
sudo apt-get install soundconverter

---

### Post by cubeist on 2008-06-23
> **bkamalnivas said:**
> Is there any software that would compress my MP3s effectively??
(need for my mp3 player....)

The only way I know is to re-compress them at a lower bit rate.  Less bits will equal a smaller size but also less audio quality. lame is the go to program on linux, but you will have to read through *man lame* for the options that work best for you...

---

### Post by stchman on 2008-06-23
> **bkamalnivas said:**
> Is there any software that would compress my MP3s effectively??
(need for my mp3 player....)

So you are wanting to reduce the size of you existing mp3s?  Say reduce the bitrate from 128K to 64K?

LAME will re-encode mp3s to a lower bitrate from the command line.

[http://lame.cvs.sourceforge.net/*checkout*/lame/lame/USAGE](http://lame.cvs.sourceforge.net/*checkout*/lame/lame/USAGE)

To install all the necessary packages for this task do the following:

CODEC install.
```

sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

If you are using 64 bit then omit the pitfdll package.

Next install the LAME package.

LAME CLI.
```
sudo apt-get install lame
```

Hope this helps.

---

