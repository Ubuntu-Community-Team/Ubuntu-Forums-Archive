---
title: "How To: Make A VCD"
date: 2006-02-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Dr Von Bon Bon on 2006-02-01
Hi,


I recently went through a huge ordeal trying to copy a VCD and so people don't have as many problems as I did here is a super mega happy guide.


I'm not sure if all this is needed but this is what I did:

```
sudo apt-get install vcdimager cdrdao
```

This is the bit I'm unsure about for people; whether or not any more codecs need to be installed. I believe that I installed ffmpeg but I'm not sure if that was any help.


The next section of this is to find something that can convert .avi to .mpeg,
the best thing that I have found for this purpose is avidemux:

```
sudo apt-get install avidemux
```

Once that you have installed this open up your .avi file in it and then, on the menu bar at the top, click on the auto button and select VCD.
This will do all the stuff that needs doing for it to work VCD style.

When this is eventually done you now need a program to actually write the VCD. The best one for this use that I found had to be k3b.

```
sudo apt-get install k3b
```

Once this is installed right-click on the blue section bottom middle and select make Video Disc. Now choose your file and burn the VCD.

I hope this has helped!

(P.S. I have only tried it on Gnome so I have no idea if it works on KDE or not)

---

### Post by kittcankitt on 2006-02-03
Could you please post (or inform us) of the address you added in your apt sources list to acquire avidemux?  Thanks and nice how-to.

KCK

---

### Post by daredevil on 2006-03-01
repository plz without which the post is not fruitful

---

### Post by Billquinn1 on 2006-03-01
He does not say which avidemux but you can download it from:

[http://mirrors.dotsrc.org/ubuntu/pool/multiverse/a/avidemux/avidemux_2.0.42-0.0ubuntu2_i386.deb](http://mirrors.dotsrc.org/ubuntu/pool/multiverse/a/avidemux/avidemux_2.0.42-0.0ubuntu2_i386.deb)

Hopefully this helps.

---

### Post by Gray. on 2006-04-20
Object not found.

I just went up one directory and found it though.

---

### Post by jtpratt on 2006-04-25
read my[ Ubuntu Video Conversion Guide]("http://smorgasbord.net/convert_video_linux").  Tovid, ffmpeg, and dvdauthor do the exact same thing (and more....

---

### Post by yorick on 2006-04-27
Hello. Does anyone know how to also add subtitles to the resulted svcd file? 
I mean you usualy have the .avi file and a subtitle in .sub or .srt format. But if you convert the .avi to .mpg and burn the .mpg as svcd you lose the subtitle...

---

### Post by jtpratt on 2006-04-27
For subtitles read:

[DVD Ripping and Transcoding with Linux]("http://bunkus.org/dvdripping4linux/en/single/index.html")

and also, read the [subtitle documentation for DVD::Rip]("http://www.exit1.org/dvdrip/doc/gui-gui_subtitle.cipp").

---

### Post by yorick on 2006-04-28
Thanks for the answer, but it seems I didn't make myself understood. I want to do the reverse process.
 
I don't want to rip a DVD and extract the subtitle from it, but to combine an .avi and .srt or .sub file into an .mpg file in order to write a SVCD with the subtitle included.

---

### Post by jtpratt on 2006-04-28
[QUOTE=yorick]Thanks for the answer, but it seems I didn't make myself understood. I want to do the reverse process.
 
I don't want to rip a DVD and extract the subtitle from it, but to combine an .avi and .srt or .sub file into an .mpg file in order to write a SVCD with the subtitle included.[/QUOTE]

Try using DVD::Rip again.  You can rip the dvd to avi, and also rip the subtitles to vcd or svcd images....and then burn them as one to a cd.  I believe DVD::Rip uses vobsub and transcode for these things.

---

### Post by mean99 on 2006-04-28
[http://fixounet.free.fr/avidemux/doc/en/video6.xml.html](http://fixounet.free.fr/avidemux/doc/en/video6.xml.html)

---

