---
title: "What I thought was a simple shell script."
date: 2008-12-22
forum: Programming Talk
---

### Post by Sin@Sin-Sacrifice on 2008-12-22
Yeah so... I wanted to automate the conversion process of videos for my ipod and g1. I know the command works but the script is fouling up by telling me :```
Killmandline$ ./g1movie.sh
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Aug 10 2008 11:11:16, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, avi, from '/home/sin/Videos/sin/robin.hood.tights-pfa.avi':
  Duration: 01:39:53.3, start: 0.000000, bitrate: 979 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 640x336, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 48 kb/s
File '/home/sin/Videos/sin/Who Framed Roger Rabbit[1988].avi' already exists. Overwrite ? [y/N] 

``` when I execute it. Well... as you can see here ```
#!/bin/bash
	#Here we have a complex command turned into a simpler one 
	#that also automates the conversion process of .avi files.
ffmpeg=/usr/bin/ffmpeg

$ffmpeg -i ~/Videos/sin/*.avi -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 ~/g1movies/$1.out

exit 0
``` I want it to write the output to ~/g1movies and have the same  name as the input file and not to the original ~/Videos/sin folder. Am I missing something here?

---

### Post by ghostdog74 on 2008-12-22
i suggest making it one step at a time, use a loop to go over the avi files
```

for files in *.avi
do
  ffmpeg $files ...... -o outfile .....
  mv $outfile $files
done

```

---

### Post by Sin@Sin-Sacrifice on 2008-12-22
I don't want it to overwrite the old avi though. Guess I could just make a second copy of the avi and overwrite the copy. hdd space is cut slim in that scenereo.

---

### Post by ghostdog74 on 2008-12-22
> **Sin@Sin-Sacrifice said:**
> I don't want it to overwrite the old avi though. Guess I could just make a second copy of the avi and overwrite the copy. hdd space is cut slim in that scenereo.

then don't use mv

---

### Post by Sin@Sin-Sacrifice on 2008-12-22
My input is ~/Videos/sin/*.avi   My output is ~/g1movies/$1.out  In my mind I shouldn't have to use mv because it should be put into the output folder so the source folder and its contents should be unaffected. The prompt for overwriting shouldn't even come to pass because the destination folder doesn't have that file in it. I am new to all of this and I am truly sorry if I'm not making sense but I have to be missing something somewhere with that. It shouldn't even be trying to overwrite. Why isn't it converting to ~/g1movies? The command alone does it that way.

---

### Post by kaibob on 2008-12-22
> **Sin@Sin-Sacrifice said:**
> ...I want it to write the output to ~/g1movies and have the same  name as the input file and not to the original ~/Videos/sin folder. Am I missing something here?

I'm not familiar with ffmpeg but shouldn't the output go to /home/username/g1movies/. I guess I don't understand the purpose of $1.out in your script unless you are typing the name of the output directory as a command line parameter.

---

### Post by Sin@Sin-Sacrifice on 2008-12-22
It's just a shortcut... the command, by itself, works. I'm just trying to, eventually, make it automatic. I work midnight shift and can connect to the pc from work but remembering that whole line of stuff... blah. I could just send it to my e-mail and use that at work but then why the heck have shell scripting? Make things easy and fun eh? Anyway... on my system ~/ = /home/user. I'll try changing it to /home/user but doubt that will do much. And $1.out tells  bash to give the output the same name as input. (At least I think that's how this stuff works... not real familiar yet)

---

### Post by Sin@Sin-Sacrifice on 2008-12-22
Ok... I'm not that bright. The command was changed a little for the script. $1.out wasn't in the original because I was only using it to do one file at a time. Could that be the problem? I just tried to run the command alone and it gave me the same overwrite prompt. From what I've read that should work but, as I said, I'm new to this and haven't actually seen this work. What I'm trying to do is make ffmpeg take every avi in the source folder and convert it to a smaller version for my G1 phone in another folder one right after the other and without having to type out all that every time I copy a bunch of my dvds (I get new ones often). I copy and store about 5 - 10 dvds and other home movies and such at a time. I would love not to have to sit here and mess with it for every video. Some direction would be much appreciated.

---

### Post by kaibob on 2008-12-22
Why don't you try the following in a terminal window (change the username in two spots):

```
ffmpeg -i /home/username/Videos/sin/*.avi -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 /home/username/g1movies/
```

I don't believe all command-line utilities support wildcards, and in that case a for loop will be needed. The following is an example:

```
#!/bin/bash
cd /source/directory
for FILE in *.avi ; do 
ffmpeg -i "$FILE" -f mp4 -vcodec mpeg4 -maxrate 1000k \
-b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac \
-ab 192 -s 320x240 -aspect 4:3 /output/directory/
done
```

You have to change the source and output directories in this script.

As an aside, you may want to request that a moderator transfer this thread to the Multimedia & Video forum, where the forum members have an understanding of ffmpeg (which I don't). The shell script part of this is extremely simple.

---

### Post by Sin@Sin-Sacrifice on 2008-12-22
Thanks for the help guys...

---

### Post by kaibob on 2008-12-22
Perhaps you have resolved the issue or figured it's not worth the trouble, but you may want to look at geirha's script in the following thread:

[http://ubuntuforums.org/showthread.php?t=950104](http://ubuntuforums.org/showthread.php?t=950104)

You can just change the ffmpeg options and add a path to the output file, and you're good to go.

---

### Post by slavik on 2008-12-23
the wildcard substitution is done by the shell, unless there are quotesaround what you are saying.

---

### Post by Sin@Sin-Sacrifice on 2008-12-23
Wow... thanks so much kaibob. I have never seen someone so willing to help. Especially on this forum. I'd almost given up hop in it. I had given up on the script a little but I was right back to the research after a nap. Then my wife came home and god forbid I be working on this box while she's here. I really wanted to get this working myself but ah well... I want the script that much more. Thank you thank you thank you.

---

