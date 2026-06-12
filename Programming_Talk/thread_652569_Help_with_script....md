---
title: "Help with script..."
date: 2007-12-28
forum: Programming Talk
---

### Post by smartboyathome on 2007-12-28
I am writing a script for myself which converts a movie file to the correct format for my MP3 player. I am having trouble with it, though, since mencoder isn't acting like when I run it. Here is a copy of the script:

```
#!/bin/sh
# **********************************************
# *           Insignia Video Encoder           *
# * Encodes your video for your Insignia sport *
# *             By smartboyathome              *
# **********************************************

echo "Type the path to your video that you want to encode and press [ENTER]: "
read pathdecoded

echo "Type where you want the encoded video to be put (including the video's file name) and press [ENTER]: "
read pathencoded

echo "Encoding, please wait..."
mencoder $pathdecoded ovc lavc -oac mp3lame -lameopts cbr:br=128 -ffourcc XVID -lavcopts vcodec=mpeg4:vbitrate=256 -vf scale=220:176,crop=220:176 -ofps 15 -o $pathencoded >> /dev/null

echo "Done!"
```

Basically, it is supposed to take in which movie I want to convert, and where I want to convert it to, and then convert it for me. When I run the mencoder without the script, it doesn't ask me for the -ovc, but when I run it with the script, it does. Please help make this run like executing the command.

Also, how do I make it so that it doesn't show the output?

---

### Post by smartboyathome on 2007-12-29
Please help? I am trying to get this to work so I don't have to remember the command.

---

### Post by amo-ej1 on 2007-12-29
Hmmz well one comment when looking at the mencoder manpage, shouldn't it be "-ovc" instead of "ovc".

And what do you mean with not showing the output ? I think you are suppressing standard output but not standard error. Observer the following: 

```

edb@elske:~$ mencoder 
MEncoder 2:1.0~rc2-0ubuntu1~gutsy1 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 4, Stepping: 10)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
No file given

Exiting... (error parsing command line)
edb@e:~$ mencoder >/dev/null
No file given
edb@e:~$ mencoder >/dev/null 2>/dev/null
edb@e:~$ 

```

You have two streams, standard output and standard error, by only putting ">/dev/null" (or 1>/dev/null) you only suppress standard output, 2>/dev/null also suppresses standard error.

---

### Post by altonbr on 2007-12-29
Which I think means your code should look like this:
```
#!/bin/sh
# **********************************************
# *           Insignia Video Encoder           *
# * Encodes your video for your Insignia sport *
# *             By smartboyathome              *
# **********************************************

echo "Type the path to your video that you want to encode and press [ENTER]: "
read pathdecoded

echo "Type where you want the encoded video to be put (including the video's file name) and press [ENTER]: "
read pathencoded

echo "Encoding, please wait..."
mencoder $pathdecoded **-**ovc lavc -oac mp3lame -lameopts cbr:br=128 -ffourcc XVID -lavcopts vcodec=mpeg4:vbitrate=256 -vf scale=220:176,crop=220:176 -ofps 15 -o $pathencoded **2>&1 > /dev/null**

[I]# WMV to AVI
# mencoder $pathdecoded -ofps 23.976 -ovc lavc -oac copy -o outfile.avi[/I]

echo "Done!"
```

I just added that WMV to AVI for ya ;)

---

### Post by smartboyathome on 2007-12-29
Thanks both of you! I will try this out on a video I need to do it with and report back if I have any problems (it will take a little while to encode).

EDIT: I have a problem: It still displays the skipping frame messages, and doesn't redirect them. Please help :)

EDIT2: Fixed it on my own.

---

