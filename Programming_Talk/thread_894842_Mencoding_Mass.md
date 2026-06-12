---
title: "Mencoding Mass"
date: 2008-08-19
forum: Programming Talk
---

### Post by Ryan450 on 2008-08-19
Hey guys,

Lately I've been dumping a lot of my home videos from tape to digital formats using a capture card. After editing I get a .avi file format, and then use mencoder to convert to dvd format for burning.

However lately I've gotten a lot of files ready for conversion, but its getting tedious. I'd like to automate the encode process.

 Here's the command I run.

```
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:480,harddup \
-srate 48000 -af lavcresample=48000 \
-lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:aspect=16/9:\
acodec=ac3:abitrate=192:threads=4 -ofps 30000/1001 -o your_video.mpg your_video.avi
```

I'd like to run this command on every file in my directory, put the output of the command into its own directory for easy management.

---

### Post by loganwm on 2008-08-19
> **Ryan450 said:**
> Hey guys,

Lately I've been dumping a lot of my home videos from tape to digital formats using a capture card. After editing I get a .avi file format, and then use mencoder to convert to dvd format for burning.

However lately I've gotten a lot of files ready for conversion, but its getting tedious. I'd like to automate the encode process.

 Here's the command I run.

```
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:480,harddup \
-srate 48000 -af lavcresample=48000 \
-lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:aspect=16/9:\
acodec=ac3:abitrate=192:threads=4 -ofps 30000/1001 -o your_video.mpg your_video.avi
```

I'd like to run this command on every file in my directory, put the output of the command into its own directory for easy management.

I'll write you up something in C if I can figure it.

Is there a command line argument to have it exit when done with one video?

---

### Post by meanburrito920 on 2008-08-19
I would suggest using a bash script. I myself would probably use python (I did a python script like this recently to fix a subversion problem.) if you want to do python, the class you want to look at is os.walk()

---

### Post by Ryan450 on 2008-08-19
> **meanburrito920 said:**
> I would suggest using a bash script. I myself would probably use python (I did a python script like this recently to fix a subversion problem.) if you want to do python, the class you want to look at is os.walk()

Yes a bash script would suit perfectly, and is what I've been trying to do for the last little bit but I just cant remember bash scripting, been having a hard time finding a decent resource to do this.

Only thing that ever comes up in google is these stupid little snippits that have nothing to do with what I'm actually looking for.

---

### Post by loganwm on 2008-08-19
> **Ryan450 said:**
> Yes a bash script would suit perfectly, and is what I've been trying to do for the last little bit but I just cant remember bash scripting, been having a hard time finding a decent resource to do this.

Only thing that ever comes up in google is these stupid little snippits that have nothing to do with what I'm actually looking for.

WinFF could also be suitable for your needs, that is, if I understand you correctly.

---

### Post by Ryan450 on 2008-08-19
> **loganwm said:**
> WinFF could also be suitable for your needs, that is, if I understand you correctly.

Why use something different if what I'm currently using good enough already? I also dont know what settings that gui is using.

For instance the command above I figured out by reading mencoders documentation to figure out the options I wanted and to get it to use all 4 of my processor cores for maximum speed.

I'd much rather use a script in the terminal rather then a gui any day as I can further customize it in the future.

---

### Post by hod139 on 2008-08-19
Not sure what you want.  This one liner will run your mencoder command on every file with a .mpg extension.  Note, this is untested and might break if files have spaces.
```

for i in `ls *.mpg`; do
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:480,harddup \
-srate 48000 -af lavcresample=48000 \
-lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:aspect=16/9:\
acodec=ac3:abitrate=192:threads=4 -ofps 30000/1001 -o ${i} ${i%.mpg}.avi;
done

```

---

### Post by loganwm on 2008-08-19
> **Ryan450 said:**
> Why use something different if what I'm currently using good enough already? I also dont know what settings that gui is using.

For instance the command above I figured out by reading mencoders documentation to figure out the options I wanted and to get it to use all 4 of my processor cores for maximum speed.

I'd much rather use a script in the terminal rather then a gui any day as I can further customize it in the future.

It's alright man, I didn't realize that you wanted it in a specific method.

Just giving suggestions.

---

### Post by meanburrito920 on 2008-08-19
If you're looking to learn some bash, look here. tldp.org has some great stuff.

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

---

### Post by Ryan450 on 2008-08-19
ok What I have is a ton of .avi files in a directory. 

I want to run the command I supplied in my first post in this thread on every .avi file in the directory.

The output of the command is a .mpg which I want in its own directory called output.

---

### Post by meanburrito920 on 2008-08-19
Do you need to work recursively through the directory? or just one layer?

---

### Post by Ryan450 on 2008-08-19
just one layer. keep it simple. But I'd like the output directory to be in the same folder as the .avi's

---

### Post by sloggerkhan on 2008-08-19
if 
```

for i in `ls *.mpg`; do
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:480,harddup \
-srate 48000 -af lavcresample=48000 \
-lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:aspect=16/9:\
acodec=ac3:abitrate=192:threads=4 -ofps 30000/1001 -o ${i} ${i%.mpg}.avi;
done

```
as posted above works to do the encoding changed to start with .avi instead of .mpg,
then for what you want:
```

#! /bin/sh
for i in `ls *.avi`; do
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:480,harddup \
-srate 48000 -af lavcresample=48000 \
-lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:aspect=16/9:\
acodec=ac3:abitrate=192:threads=4 -ofps 30000/1001 -o ${i} ${i%}.mpg;
done
mkdir output
mv *.mpg output

```
(not sure this is 100% correct, but you should be able to make a file allong these lines executable and run it in a directory to convert the files and move them.)

---

### Post by Ryan450 on 2008-08-19
BINGO! Thank you very much Sir :).

That is exactly what I wanted. I knew the script would be simple, I've just not had enough time to re-learn my bash scripting. Something I'll have to brush up on very soon.

---

### Post by meanburrito920 on 2008-08-19
in bash you could do something like:

```

#!/usr/bin/env bash

echo starting....

for f in ./*.avi; do

mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd -vf scale=720:480,harddup \
-srate 48000 -af lavcresample=48000 \
-lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=18:aspect=16/9:\
acodec=ac3:abitrate=192:threads=4 -ofps 30000/1001 -o $f.mpg $f.avi ;
done;

echo finished...

```

Of course, you would need to strip the file extension off the file name, and maybe debug a bit, but it should work fine.

---

### Post by meanburrito920 on 2008-08-19
Ah, beaten to the punch! :-)

---

### Post by ghostdog74 on 2008-08-19
> **hod139 said:**
>  Note, this is untested and might break if files have spaces.
```

for i in `ls *.mpg`; 

```
the above is what people call useless use of ls. use shell expansion instead
```

for i in *.mpg

```

---

### Post by medya on 2008-12-20
hey these scripts work fine for file names without space !
but they dont work for file names with spaces, 
for example
it wont work for "Scrubs S03E03 My White Whale [FuFu].avi"

is there any way to make it work for file names with space ?

---

### Post by medya on 2008-12-20
the error message is 
> MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8200  @ 2.66GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
File not found: '[FuFu].avi'


---

### Post by wmcbrine on 2008-12-20
> **medya said:**
> is there any way to make it work for file names with space ?Use quote marks, e.g. "$1" instead of $1.

---

