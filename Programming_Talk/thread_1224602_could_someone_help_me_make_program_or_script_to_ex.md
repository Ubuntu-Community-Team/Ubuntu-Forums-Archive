---
title: "could someone help me make program or script to extract audio from video?"
date: 2009-07-27
forum: Programming Talk
---

### Post by jcm1107 on 2009-07-27
Hi, I would like to make my first program or script. I have a command that I use sometimes to take audio from a video file. I just want to make a script that will do it or make a gui program that I can use to edit video. I have never done this before but really want to learn how. I have been wanting to learn programming and I think this may be a good way to start. well here is my command

```

mplayer -quiet video.mp4 -ao pcm:fast:file=output.wav -vc dummy -vo null -channels 2 -ss 0:01 -endpos 3:11

```

where video is the name of the video I am getting the music from and output.wav is the audio file and the -ss 0:01 is start time for extraction and -endpos 3:11 is the end of the audio.

I want to be able to just click on a video file and run this and change the extraction time and everything by gui so I guess I would need to probably make a program that could do that? If someone would help I would appreciate it a lot!! Thanks.

---

### Post by jcm1107 on 2009-07-29
Could someone please just point me in the right direction? All I can find on learning to make programs is the simple hello world one that makes it say that on the command line. I have found others but they are too much advanced for me. I just need the next step from a hello world program to get a start, becase I cant see how you can do much just by making something print in the terminal.

---

### Post by Reiger on 2009-07-29
You are doing something fairly specific. I/O (input/output) is usually covered towards mid/end sections of language tutorials.

In any case for your script you would probably be happy if you could "just" ask for input file and output file as well as end-pos? 
The invocation on the commandline would look like:
```

./myscript infile outfile endpos
```

In your code infile will be available as $1, outfile as $2, and endpos as $3. So your sh script would look like:
```

#!/bin/sh

# Usage: script name infile outfile endpos. Rips audio from A/V stream.

mplayer -quiet $1 -ao pcm:fast:file=$2 -vc dummy -vo null -channels 2 -ss 0:01 -endpos $3
```

---

### Post by jcm1107 on 2009-07-29
> **Reiger said:**
> You are doing something fairly specific. I/O (input/output) is usually covered towards mid/end sections of language tutorials.

In any case for your script you would probably be happy if you could "just" ask for input file and output file as well as end-pos? 
The invocation on the commandline would look like:
```

./myscript infile outfile endpos
```

In your code infile will be available as $1, outfile as $2, and endpos as $3. So your sh script would look like:
```

#!/bin/sh

# Usage: script name infile outfile endpos. Rips audio from A/V stream.

mplayer -quiet $1 -ao pcm:fast:file=$2 -vc dummy -vo null -channels 2 -ss 0:01 -endpos $3
```

And then I just compile this with gcc? Thanks for replying and trying to help me with my first working script!!

---

### Post by monraaf on 2009-07-29
> **jcm1107 said:**
> And then I just compile this with gcc? 

:lolflag:

---

### Post by Reiger on 2009-07-29
No. That *is* your working script.

---

### Post by jcm1107 on 2009-07-29
Sorry guys I am new to this and I don't know how to do it. So please don't make fun of me. This is my first script and everything I try it does not work. If someone could just walk me through this till I can get it to work then I will see how to do it myself from now on.

---

### Post by jcm1107 on 2009-07-29
> **Reiger said:**
> No. That *is* your working script.

Well I tried running it like that and it didn't work! I will try to get it to but I don't know how. Sorry guys, this is why I asked for help.

---

### Post by Reiger on 2009-07-29
You must make it executable. From the commandline issue 
```
chmod +x scriptname
```

E.g.
```

chmod +x audiorip.sh

```

---

### Post by issih on 2009-07-29
I'd say you should consider using avidemux:

[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)

which I think is in the repositories, if not its on getdeb

You just load the video file (or drag and drop it on to the program)

select the mark in and mark out positions, select the audio codec you want to output in and then go to audio->save in the menus (or hit ctrl+alt+s)

This gives you your gui, and you can set the mark in and mark out positions from the video preview.

I've found it very useful for stripping extraneous language tracks from video files.

Hope that helps

---

### Post by jcm1107 on 2009-07-29
> **Reiger said:**
> You must make it executable. From the commandline issue 
```
chmod +x scriptname
```

E.g.
```

chmod +x audiorip.sh

```

THANKS!!! I did that and then I got it to work!! thanks Reiger for helping me. I am sorry I am a beginer and don't know much about stuff like that now maybe I can try some more stuff with what you taught me!!! Again THANKS!!!!:P:P

---

### Post by skullmunky on 2009-08-01
Here's a hint for your next learning project - make an awesome GUI frontend for this script.

What it'll do: let you choose a file from a file chooser dialog, choose a name for the audio file you want, and then do the extraction.

How to learn how to do that:

1. learn a little python
2. write a python script that will ask the user for the name of the video file, the name of the audio file you want, and then launch the mplayer process.

3. learn a little PyQT by following some tutorials.  I like this one: [//zetcode.com/tutorials/pyqt4/]("http://zetcode.com/tutorials/pyqt4/")

4. write PyQT program to do the file choosing parts
5. now add in the bit from step 2 where it launches the mplayer script ... ta dah!  

btw:  you only have to compile with GCC if you're using a language like C or C++.  Bash or Python scripts can be run directly without compiling.

---

### Post by jcm1107 on 2009-08-01
> **skullmunky said:**
> Here's a hint for your next learning project - make an awesome GUI frontend for this script.

What it'll do: let you choose a file from a file chooser dialog, choose a name for the audio file you want, and then do the extraction.


I would love to be able to do this! that is what I wanted to do in the first place but I see it will take me a lot of learning before I can do that. I don't even have a clue how to make a gui at all.

> 

How to learn how to do that:

1. learn a little python
2. write a python script that will ask the user for the name of the video file, the name of the audio file you want, and then launch the mplayer process.

I think I will use your advice. I have my bash script working awesome, when I run it it then asks you for the directory of the movie and then it asks the name of the movie and then it asks the name for the audio file that will be made it then asks for the start time and stop time. The only thing is it does it all from the command line as a bash script which is fine with me but I just want to try to make a gui and I think it would make a good first project. I know it is a bit on the difficult side for a first project but I figure if I can do this then I would know enough to make larger programs the could do more than a  one line  command. I have been trying to convert my script to c++ and that is too hard for me. I did manage to make a program in c++ and one in C but I don't know enough to pass user input as command argument.

> 
3. learn a little PyQT by following some tutorials.  I like this one: [//zetcode.com/tutorials/pyqt4/]("http://zetcode.com/tutorials/pyqt4/")

4. write PyQT program to do the file choosing parts
5. now add in the bit from step 2 where it launches the mplayer script ... ta dah!  

btw:  you only have to compile with GCC if you're using a language like C or C++.  Bash or Python scripts can be run directly without compiling.

I did figure out what gcc and g++ do and now I know how to use them and I know how to make any of my commands into bash scripts. Bash scripts seem easy at least so far. I am sure there is a lot about them I don't know but I hope to keep learning. If anyone would want to talk programing to a beginner via email, IM, or whatever I would be glad to learn about it and talk about it.

---

### Post by skullmunky on 2009-08-01
Great - good luck!  I'd start with Python for this one, also - it's easier than C++ in a lot of ways, and you can make basic GUI apps like this pretty quickly.

---

