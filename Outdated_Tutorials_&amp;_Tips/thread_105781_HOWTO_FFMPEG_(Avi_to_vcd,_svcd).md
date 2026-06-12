---
title: "HOWTO: FFMPEG (Avi to vcd, svcd)"
date: 2005-12-19
forum: Outdated Tutorials &amp; Tips
---

### Post by kuleali on 2005-12-19
1. Open Terminal (xterm,aterm etc)
2. Download FFMPEg from cvs:** (Do NOT INSTALL FROM REP)**
**cvs -z9 -d:pserver:anonymous@mplayerhq.hu:/cvsroot/ffmpeg co ffmpeg**
In terminal type:
[B]cd ffmpeg
./configure
make
sudo make install 
[/B]

**AVI to VCD**

**NTSC**

**ffmpeg -i <movie.avi> -target ntsc-vcd <filename.mpg>**

PAL

[B]ffmpeg -i <movie.avi> -target pal-vcd <filename.mpg>
[/B]

**Burn CD**

K3b File > New Project > New Video CD project

---

### Post by jimmyp on 2006-02-22
when I did this and burnt the resulting mpg to a svcd with k3b, the picture was stretched and the sound was off.

---

### Post by rantak on 2006-02-22
The stretched picture is probably because your source was a widescreen picture and you made a 4:3 vcd. You should try this.

ffmpeg -i /path/file.avi -target pal-vcd -s 352x192 -padtop 32 -padbottom 32 /path/output.mpg

More info at [http://gentoo-wiki.com/HOWTO_Create_a_VCD_or_SVCD]("http://gentoo-wiki.com/HOWTO_Create_a_VCD_or_SVCD")

Don't know what you should do with the sound though :(

---

### Post by Marvelous on 2006-02-23
@kuleali
you have just solved the **ONLY** reason i use Windows XP for.
in a very few time until i get better knowledge and more confidence then windows is no more on my laptop.
Thank you

---

### Post by SteveGodfrey on 2006-02-23
I'm following these intstructions but get this, can you suggest what I might be missing?

steve@ubuntu:~/kits/ffmpeg$ sudo make
make -C libavutil all
make[1]: Entering directory `/home/steve/kits/ffmpeg/libavutil'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/steve/kits/ffmpeg/libavutil'
make -C libavcodec all
make[1]: Entering directory `/home/steve/kits/ffmpeg/libavcodec'
gcc -O3 -g -Wall -Wno-switch  -Wdeclaration-after-statement -DHAVE_AV_CONFIG_H -I.. -I/home/steve/kits/ffmpeg/libavutil -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE   -c -o xvid_rc.o xvid_rc.c
xvid_rc.c: In function âff_xvid_rate_control_initâ:
xvid_rc.c:67: error: âxvid_plugin_2pass2_tâ has no member named âvbv_sizeâ
xvid_rc.c:68: error: âxvid_plugin_2pass2_tâ has no member named âvbv_maxrateâ
xvid_rc.c:69: error: âxvid_plugin_2pass2_tâ has no member named âvbv_initialâ
make[1]: *** [xvid_rc.o] Error 1
make[1]: Leaving directory `/home/steve/kits/ffmpeg/libavcodec'
make: *** [lib] Error 2
steve@ubuntu:~/kits/ffmpeg$

---

### Post by jimmyp on 2006-02-23
[QUOTE=Marvelous]@kuleali
you have just solved the **ONLY** reason i use Windows XP for.
in a very few time until i get better knowledge and more confidence then windows is no more on my laptop.
Thank you[/QUOTE]
what program in windows did you use for this?

---

### Post by Rizado on 2006-02-23
[QUOTE=kuleali][B]cd ffmpeg
./configure
make
sudo make install 
[/B][/QUOTE]
Instead of doing "sudo make install" do "sudo checkinstall" (Make sure you have checkinstall first.) This will create a debian package that can be easily removed through synaptic.

And for debian based systems nothing should be installed in /usr/local/ so do "./configure --prefix=/usr" instead. /usr can be changed to wherever you want the files.

This is nothing necessary, but it helps making the life easier :)

---

### Post by Marvelous on 2006-02-23
[QUOTE=jimmyp]what program in windows did you use for this?[/QUOTE]
Used Nero.. just dragged and dropped regardless of the file type then it does the ecoding before burning the cd without interruption

---

### Post by neilyweily on 2006-05-01
i was the exact same, dumping files onto my shared vfat partition, rebooting into windows, then handing my pc over to nero for an hour and a half while it encoded the vcd.

didn't bother me too much, (honest)

then i tried to copy one of the vcd's that nero had made, using nero and no, no , no, not having any of it.

ffmpeg is currently encoding a movie for me now, and o still have full functionality

looks like i may not be a dual boot system for much longer 
:eek:

---

### Post by neilyweily on 2006-05-01
thanks kuleali for the howto :)

---

### Post by MihaiM on 2006-05-02
I use Avidemux and cdrdao and works great.

---

### Post by zba78 on 2006-05-02
Just to let you all know, there is a very easy to use app called tovid. get it at [http://tovid.berlios.de/en/index.html](http://tovid.berlios.de/en/index.html) 

It's just a bunch of scripts that uses mencoder (amongst others) to encode to DVD format. It's slower then ffmpeg but gives higher quality (in my experiance).

Personally I just use ffmpeg.

---

### Post by eduarm76 on 2006-07-17
After enconding a big avi file  I endup with a 1.2Gb mpeg , I couldn't find a way to burn this image in two CDs with k3b. Is there a way to do this?

---

### Post by JMO707 on 2006-10-27
Question: When I make *ffmpeg -i /media/cdrom/archive.avi -target ntsc-svcd -s 704x394 -padtop 32 -padbottom 32 /home/jmo/archive.mpg* because without those specifications, it result in a stretched image and with lower res, for what Im afraid that in the TV it will look ugly, I loose the subtitles. Can I add them to the resulting mpg?, I got te .srt file.

Thanks.

---

