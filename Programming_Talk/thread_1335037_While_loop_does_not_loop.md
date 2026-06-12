---
title: "While loop does not loop"
date: 2009-11-23
forum: Programming Talk
---

### Post by prconnor@gmail.com on 2009-11-23
Hello,

I am converting a series of vob files to avi and for which I also am extracting the sound as .mp3 to make a soundtrack.

I attempted to make a shell script to accomplish this for me, and it correctly works through a single iteration, then it exits without completing the loop.  Here is my code:

```

while read line
	do
  	        echo "Making $line.avi ..."
		mencoder $line.vob -ofps 30 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000  -vf scale -zoom -xy 720 -xvidencopts fixed_quant=4  -o ./avi/$line.avi
		echo "Making $line.mp3 . . ."
		ffmpeg -i ./avi/$line.avi -acodec copy ./mp3/$line.mp3

	done <input.txt 

echo "Done! All Files Created"
beep -r 10

```

input.txt is a file that I created that is basically a list of all the vob files in the directory.  I created it using 

```
ls *.vob > input.txt
```

then I opened gedit and did a find a replace to remove ".vob" from each string.  I couldn't think of a way to remove the string ".vob" using the script itself, so I'm open to suggestions to accomplish this also.

When I comment the two lines that actually do anything (the mencoder, and ffmpeg commands) the script correctly reads all the lines as indicated by the echo commands.

Thank you for any assistance.  This is my first attempt at a shell script, so I may ask some stupid questions.

---

### Post by prconnor@gmail.com on 2009-11-23
OK, maybe I fixed it.  I removed one of the commands from the while loop and put it in a separate while loop as follows:

```
while read line
	do
  	echo "Making $line.avi ..."
		mencoder $line.vob -ofps 30 -ovc xvid -oac mp3lame -lameopts abr:br=128 -srate 48000  -vf scale -zoom -xy 720 -xvidencopts fixed_quant=4  -o ./avi/$line.avi
	done <test.txt

while read line
	do
		echo "Making $line.mp3 . . ."
		ffmpeg -i ./avi/$line.avi -acodec copy ./mp3/$line.mp3

	done <test.txt 

echo "Done! All Files Created"
beep -r 10
```

The script has now passed through a second iteration of the first while loop, I'll keep watching it to see if it works.  I don't understand why this would work and having both commands in the same loop would not though.

---

### Post by mo.reina on 2009-11-23
can you run the script with :

```
bash -x *scriptname*
```

this way we can see where the script stops. just post the output

---

### Post by prconnor@gmail.com on 2009-11-23
Alright, I have found that the first while loop correctly propogates to its conclusion, and the secon, with the ffmpeg command, does not.  So it seems that it is the ffmpeg command that makes the loop exit.  I have commented all of the first while loop so that only the second while loop executes.  This is the output from running
```
 bash -x scriptname 
```
Terminal output:
```

+ read line
+ echo 'Making 2008Oct1_05.mp3 . . .'
Making 2008Oct1_05.mp3 . . .
+ ffmpeg -i ./avi/2008Oct1_05.avi -acodec copy ./mp3/2008Oct1_05.mp3
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
Input #0, avi, from './avi/2008Oct1_05.avi':
  Duration: 00:10:22.3, start: 0.000000, bitrate: 673 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x404 [PAR 1:1 DAR 180:101], 30.00 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Output #0, mp2, to './mp3/2008Oct1_05.mp3':
    Stream #0.0: Audio: libmp3lame, 48000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
size=    9347kB time=622.4 bitrate= 123.0kbits/s    
video:0kB audio:9347kB global headers:0kB muxing overhead 0.000000%
+ read line
+ echo 'Done! All Files Created'
Done! All Files Created
+ beep -r 10

```

---

### Post by diesch on 2009-11-24
ffmpeg sucks out stdin (for the "Press [q] to stop encoding") so there's nothing left for a second iteration of the while loop.

Use
```
ffmpeg -i ./avi/$line.avi -acodec copy ./mp3/$line.mp3 < /dev/null
```

---

### Post by Rany Albeg on 2009-11-24
> then I opened gedit and did a find a replace to remove ".vob" from each string.  I couldn't think of a way to remove the string ".vob" using the script itself, so I'm open to suggestions to accomplish this also.


This will erase .vob extension from var:
```
var=${var%.vob}
```

In your script you can use sed to remove the extension:

```
rany@rany-laptop:~$ cat>file
file.vob
file2.vob
file3.vob
rany@rany-laptop:~$ sed 's/.vob//' -i file
rany@rany-laptop:~$ cat file 
file
file2
file3
rany@rany-laptop:~$
```

---

### Post by mo.reina on 2009-11-24
> **diesch said:**
> ffmpeg sucks out stdin (for the "Press [q] to stop encoding") so there's nothing left for a second iteration of the while loop.

Use
```
ffmpeg -i ./avi/$line.avi -acodec copy ./mp3/$line.mp3 < /dev/null
```

that's interesting, i would never have thought about that.  so even though ffmpeg is forked into a child process it can still take STDIN from *while-read-line*?

---

### Post by Tony Flury on 2009-11-24
Just to be clear It does not read it from the "while read line". 

When you fork a process unless you tell it otherwise it uses the same stdin that the parent uses, so both your parent script (the while read line) and the ffmpeg command are reading from the same input stream, and because of the functionality of ffmpeg (i.e. it keeps grabbing input until it sees EOF or "q") then it will consume all of your input file, and probably do so quicker than your bash script can get through the rest of the of the loop to read the next line.

---

### Post by mo.reina on 2009-11-24
ah my bad.  you're right of course.  so there are two input streams running, one from *while-read-line*, which determines how many times the loop is run, and one from the loop itself, which is the one that is being sucked in by ffmpeg, correct?

however isn't STDIN from the loop dependent on *while-read-line*?  i mean, the loop is fed whatever $line is, which is determined by the conditional statements.  don't the conditional statements give the value of $line to commands in the loop, then after the commands terminate, feed it the next value of $line?  or does it feed the value of $line all at once?

---

### Post by diesch on 2009-11-24
> **mo.reina said:**
> 
ah my bad.  you're right of course.  so there are two input streams running, one from *while-read-line*, which determines how many times the loop is run, and one from the loop itself, which is the one that is being sucked in by ffmpeg, correct?


No, it's just one stream used by multiple processes.

> **mo.reina said:**
> 
however isn't STDIN from the loop dependent on *while-read-line*?  i mean, the loop is fed whatever $line is, which is determined by the conditional statements.  don't the conditional statements give the value of $line to commands in the loop, then after the commands terminate, feed it the next value of $line?  or does it feed the value of $line all at once?

*read* is just a command that reads a line from stdin and saves its content in a variable or returns a code > 0 id there is nothing left to read. It gets executed every time the *while* statement is evaluated until it returns a code > 0

---

### Post by mo.reina on 2009-11-24
ok, so STDIN is not controlled and given piecemeal to the loop.  basically it's just there and ffmpeg hijacks it when it goes into interactive mode, leaving nothing for the second iteration of the loop.  

so in theory if i put an "echo $line" **after** the ffmpeg command, it would still echo the first line of the file, even though STDIN has been appropriated and there is nothing left for read to read.  

just trying to understand the unerlying mechanics, sorry if it's getting a bit technical

---

### Post by diesch on 2009-11-24
> **mo.reina said:**
> 
so in theory if i put an "echo $line" **after** the ffmpeg command, it would still echo the first line of the file, even though STDIN has been appropriated and there is nothing left for read to read.  


Yes. $line get a value from read and keeps it until it get a new one.

---

### Post by grayrainbow on 2009-11-25
Off: I'm just in love of the name of this thread :)

---

### Post by prconnor@gmail.com on 2009-11-27
> **Rany Albeg said:**
> 

In your script you can use sed to remove the extension:
...
 sed 's/.vob//' -i file
...

Worked like a champ.  Thank you for your assistance.

---

### Post by prconnor@gmail.com on 2009-11-27
> **diesch said:**
> 
```
ffmpeg -i ./avi/$line.avi -acodec copy ./mp3/$line.mp3 < /dev/null
```

This is awesome.  Thank you for sharing your knowledge.  It worked perfectly.

---

