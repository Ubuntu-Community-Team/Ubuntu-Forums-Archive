---
title: "Convert Video Files to 3GP for a Nokia Symbian 60"
date: 2006-09-14
forum: Outdated Tutorials &amp; Tips
---

### Post by darrenm on 2006-09-14
Bit of a specific howto this one.

If you have a Nokia 66 series phone which is the Symbian 60 series OS (or maybe other phones) then converting video files in Linux to go onto it may seem difficult.

Found a few bits and pieces on the web so just thought I would make a script to do all the work for you:

```
gksudo gedit /usr/bin/mk3gp
```
Paste the following:
```
#!/bin/bash

SETUP ()
{
rm -rf ~/.3gptemp
mkdir ~/.3gptemp
cd ~/.3gptemp
sudo apt-get install -y subversion mencoder mplayer build-essential
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
mkdir ffmpeg/libavcodec/amr_float
cd ffmpeg/libavcodec/amr_float
wget http://www.3gpp.org/ftp/Specs/archive/26_series/26.104/26104-510.zip
unzip 26104-510.zip
unzip 26104-510_ANSI*.zip
cp -f makefile.gcc makefile
cd ../../
echo -e "\nWe are in `pwd`\n"
./configure --enable-amr_nb
make
sudo make install
}

MAKE ()
{
echo $file
mencoder $file -nosound -ovc lavc -lavcopts vcodec=mpeg4 -vop expand=176:144,scale=176:-2 -o movie.avi -ofps 12
mplayer -vo null -ao pcm -af resample=8000,volume=+4db:sc $file
ffmpeg -i movie.avi -i audiodump.wav -b 48 -ac 1 -ab 12 -map 0.0 -map 1.0 $file2
}

if [ "$1" = "setup" ] ; then SETUP
        elif [ "$1" = "make" ] ; then file=$2; file2=$3 ;MAKE
else echo "Useage: mk3gp setup|make input_filename output_filename"
fi

```
```
sudo chmod a+x /usr/bin/mk3gp
```
Then run it like so:
```
mk3gp setup
```
Which will grab a few bits, compile it etc.
```
cd /dir_the_vids_are_in
mk3gp video_file.mpg video_file.3gp
```

And hey presto. Tested it here and it works but if you have problems let me know, it is 1.30am here and I'm tired ;)

---

### Post by anakin_sk4jvoker on 2006-09-20
i get this at the end of setup :(

 inflating: interf_dec.c
  inflating: interf_dec.h
  inflating: interf_enc.c
  inflating: interf_enc.h
  inflating: interf_rom.h
  inflating: makefile.gcc
  inflating: makefile.win32
  inflating: readme.txt
  inflating: rom_dec.h
  inflating: rom_enc.h
  inflating: sp_dec.c
  inflating: sp_dec.h
  inflating: sp_enc.c
  inflating: sp_enc.h
  inflating: decoder.c
/usr/bin/mk3gp: line 16: ./configure: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.

what to do?

---

### Post by darrenm on 2006-09-20
Hmm tried it here on a fresh Dapper system and it did need build-essential so I've added that but it looks like you may have missed the ./configure file from SVN.

I've changed it slightly, can you re-copy and paste then if it fails post back what you are getting?

Thanks

---

### Post by anakin_sk4jvoker on 2006-09-20
now is ok , thanks :)

---

### Post by kipe on 2006-09-24
Very nice HOW-TO but it gave me some strange error when I'm trying to convert mpeg file. I've copy/paste the code so there is no typo. Here is the error:

[h263 @ 0x84d20d8]The specified picture size of 176x148 is not valid for the H.263 codec.
Valid sizes are 128x96, 176x144, 352x288, 704x576, and 1408x1152. Try H.263+.
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

And it cannot merge the wav file and the avi file and the 3gp file is 0 bytes . Help me please

---

### Post by darrenm on 2006-09-24
Have you been able to convert any other files ok? Does it just fail on the one?

It looks like the H.263 codec is not able to decode the source file correctly. Not sure what to suggest apart from changing this line:

```
mencoder $file -nosound -ovc lavc -lavcopts vcodec=mpeg4 -vop expand=176:144,scale=176:-2 -o movie.avi -ofps 12
```

To this:
```
mencoder $file -nosound -ovc lavc -lavcopts vcodec=mpeg4 -vop expand=176:148,scale=176:-2 -o movie.avi -ofps 12
```

and see if it makes any difference.

---

### Post by kipe on 2006-09-25
OK, I'll check this line later when I get home! I've managed to convert some .avi files without problem, so the only problem is with mpeg files. I'll check this resoulution 176:148 and I will write back. Thank you for your quick answer ;)

---

### Post by Zhukov on 2006-09-25
Wanna merge work?

[http://ubuntuforums.org/showthread.php?t=216083](http://ubuntuforums.org/showthread.php?t=216083)

---

### Post by darrenm on 2006-09-26
Aha excellent. I was thinking of trying to do a GUI but it looks you already have something very nice.

Let me know how I can help. Cheers.

---

### Post by Zhukov on 2006-11-23
Sorry, I only saw you message today! :S
Was kinda busy...
I will start working on this tomorrow.

---

### Post by rootkit on 2007-12-07
My mk3gp script is better, have a look: [http://teknoraver.campuslife.it/software/mp4tools/](http://teknoraver.campuslife.it/software/mp4tools/)

---

### Post by rootkit on 2008-01-20
I added black borders removal and scaling while keeping aspect ratio. url is the same

---

### Post by rootkit on 2008-01-20
> **darrenm said:**
> 
-vop expand=176:144,scale=176:-2

This won't work if the movie has an aspect ratio lower than 1.22 (eg. 100x100)

---

