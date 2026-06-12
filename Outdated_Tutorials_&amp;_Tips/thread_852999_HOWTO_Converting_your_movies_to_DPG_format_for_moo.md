---
title: "HOWTO: Converting your movies to DPG format for moonshell on the Nintendo DS"
date: 2008-07-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Skatertjah on 2008-07-08
This is a how to for converting videos into the DPG format in Ubuntu which can then be run in moonshell on your Nintendo DS.
If you have any tips, found mistakes or found out a better way to get this done, please comment below.

Ok here we go...

**Step 1: Getting the right stuff**

Install mencoder and mplayer:
Open up a terminal and copy this into there:
```
sudo apt-get install mencoder mplayer
```

Get your hands on the dpgconv python script and mpeg_stat:
Download the dpgconv script here ([http://theli.ho.com.ua/dpgconv/dpgconv-0.43.py](http://theli.ho.com.ua/dpgconv/dpgconv-0.43.py))
Get mpeg_stat here ([ftp://ftp.riken.go.jp/pub/FreeBSD/distfiles/mpeg_stat-2.2b-src.tar.gz/](ftp://ftp.riken.go.jp/pub/FreeBSD/distfiles/mpeg_stat-2.2b-src.tar.gz/))
If this link doesn't work I have uploaded the archive below
[B]
Step 2: Setting it up[/B]

Create new folder in your home directory and name it DPG
Move the file you want to convert, the mpeg_stat archive and the dpgconv script into this folder

Now we have to compile mpeg_stat
extract the mpeg_stat archive in the DPG folder (right click --> extract here)
Open up a terminal
```
cd /home/DPG/mpeg_stat-2.2b-src/mpeg_stat
make
```

Move mpeg_stat and mpeg_stat.1 to /bin (otherwise the dpgconv script can't find them)
```
cd /home/DPG
sudo cp mpeg_stat /bin/mpeg_stat
sudo cp mpeg_stat.1 /bin/mpeg_stat.1
```
You can't just copy files into the /bin folder without having the right permissions, hence the sudo command


Create an executable of the dpgconv script
```
cd /home/DPG
chmod +x dpgconv-0.43.py
```
[B]
Step 3: converting the video[/B]
```
cd /home/DPG
python dpgconv-0.43.py video.avi
```

That's about it, enjoy watching videos on your DS!

---

### Post by jonthysell on 2008-07-26
I just ordered an M3 Real and the last time I'd checked (some months ago) I could only find win utilities for making dpg files. I can't wait to try this out (I've been using TCPMP on an old Palm Tungsten E to watch portable movies, but the battery life is bad and the speakers are flaky).

On that note, I have some smooth running specs for putting running XViD videos on the Palm...

---

### Post by nandotron on 2008-07-30
> **Skatertjah said:**
> 

Now we have to compile mpeg_stat
extract the mpeg_stat archive in the DPG folder (right click --> extract here)
Open up a terminal
```
cd /home/DPG/mpeg_stat-2.2b-src/mpeg_stat
make
```



Hi there... i ran into a few problems when i tried to compile, here is the output from the terminal:
```

enda@enda-laptop:~/DPG/mpeg_stat-2.2b-src/mpeg_stat$ make
gcc -I/usr/include -O    -c -o util.o util.c
util.c:46:20: error: stdlib.h: No such file or directory
In file included from util.c:47:
video.h:45:19: error: stdio.h: No such file or directory
video.h:46:20: error: setjmp.h: No such file or directory
In file included from util.c:48:
proto.h:135: error: expected ‘)’ before ‘*’ token
proto.h:136: error: expected ‘)’ before ‘*’ token
In file included from util.c:50:
opts.h:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
opts.h:47: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
opts.h:48: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
opts.h:49: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
opts.h:50: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
opts.h:51: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
opts.h:52: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
opts.h:53: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
util.c: In function ‘correct_underflow’:
util.c:149: warning: incompatible implicit declaration of built-in function ‘fprintf’
util.c:149: error: ‘stderr’ undeclared (first use in this function)
util.c:149: error: (Each undeclared identifier is reported only once
util.c:149: error: for each function it appears in.)
util.c:151: warning: incompatible implicit declaration of built-in function ‘exit’
util.c:154: warning: incompatible implicit declaration of built-in function ‘fprintf’
util.c:165: warning: incompatible implicit declaration of built-in function ‘exit’
util.c: In function ‘next_bits’:
util.c:202: error: ‘NULL’ undeclared (first use in this function)
util.c: In function ‘get_ext_data’:
util.c:255: warning: incompatible implicit declaration of built-in function ‘malloc’
util.c: In function ‘next_start_code’:
util.c:318: error: ‘NULL’ undeclared (first use in this function)
util.c: In function ‘get_extra_bit_info’:
util.c:447: error: ‘NULL’ undeclared (first use in this function)
util.c:452: warning: incompatible implicit declaration of built-in function ‘malloc’
make: *** [util.o] Error 1
```

anyone have any ideas? are there files missing from my unpacked archive?

---

### Post by dbn045 on 2008-07-30
ok for your problem there I don't think you went into the right folder because it says some files do not exist. So go inside of your mpeg_stat-2.2b-src then inside of mpeg_stat folder and click Ctrl+L. It'll tell you the location of that folder. Simply highlight and copy that location. Open up a terminal enter cd then a space and paste what you have just copied then press enter. Now it should be in the right folder so just type the word make. Then it should work.

I am having a problem with this. When i convert video sizes that are around 40 mins and up the sound gets off sync. I am thinking that that would be because the dpg files settings are set to high. 
So basically my question is does the sound get of sync because the quiality of the video is too high for the ds?

Also if the quality is the case what should I make the framerate and bitrate?

---

### Post by mcbean on 2008-07-31
Thanks for this, very useful! 

In case people don't read the .py script, you can add --hq or --lq to the arguments to make it higher or lower quality.

---

### Post by nandotron on 2008-07-31
> **dbn045 said:**
> ok for your problem there I don't think you went into the right folder because it says some files do not exist. So go inside of your mpeg_stat-2.2b-src then inside of mpeg_stat folder and click Ctrl+L. It'll tell you the location of that folder. Simply highlight and copy that location. Open up a terminal enter cd then a space and paste what you have just copied then press enter. Now it should be in the right folder so just type the word make. Then it should work.



Hi dbn045,

no luck with this, i'm definitely in the correct folder.  the archive i'm downloading is the one attached to the end of your original post, not the one thats linked in the actual post (that one takes me to a download link for a .bin file).  Do you mind having a look at the archive to make sure its complete?  Sorry about this, i'm really lost!

---

### Post by vxWorks on 2008-08-01
try: 

sudo apt-get install gcc

after install then:

cd /home/DPG/mpeg_stat-2.2b-src/mpeg_stat

make

when finished. type:

sudo cp mpeg_stat /bin/mpeg_stat
sudo cp mpeg_stat.1 /bin/mpeg_stat.1

then:
cd /home/DPG
chmod +x dpgconv-0.43.py

and finally:

Step 3: converting the video
Code:

cd /home/DPG
python dpgconv-0.43.py video.avi

I think you have to copy the video to encode into the DPG directory. when you are done converting you should find a video.dpg file in this directory.

---

### Post by dbn045 on 2008-08-02
> **nandotron said:**
> Hi dbn045,

no luck with this, i'm definitely in the correct folder.  the archive i'm downloading is the one attached to the end of your original post, not the one thats linked in the actual post (that one takes me to a download link for a .bin file).  Do you mind having a look at the archive to make sure its complete?  Sorry about this, i'm really lost!

I used the archive that your talking about and it worked.(I first tried the link like you did and then I got the archive and it worked).
I don't know what your problem is then you have tried downloading the file again I assume? If not maybe download it again its worth a try lol.
well hope you get it working its pretty sweet I have mine working and it works like a charm except for long videos i'm having a bit of a trouble with there words being off sync. Though I might be able to solve that if i just simply lower the frames per second maybe.

---

### Post by ericsteindorff on 2008-08-08
Thanks I now have the conversion working on Debian ETCH

---

### Post by yanghyungryul on 2008-09-13
What is a terminal???

---

### Post by Inversions on 2008-09-25
yanghyungryul: Go to the menu: Applications > Accessories > Terminal

---

### Post by NorQue on 2008-09-29
> **nandotron said:**
> Hi there... i ran into a few problems when i tried to compile, here is the output from the terminal:
```

enda@enda-laptop:~/DPG/mpeg_stat-2.2b-src/mpeg_stat$ make
gcc -I/usr/include -O    -c -o util.o util.c
util.c:46:20: error: stdlib.h: No such file or directory
In file included from util.c:47:
video.h:45:19: error: stdio.h: No such file or directory
video.h:46:20: error: setjmp.h: No such file or directory
In file included from util.c:48:
proto.h:135: error: expected ‘)’ before ‘*’ token
proto.h:136: error: expected ‘)’ before ‘*’ token
In file included from util.c:50:
opts.h:46: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
opts.h:47: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
opts.h:48: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
opts.h:49: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
opts.h:50: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
opts.h:51: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
opts.h:52: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
opts.h:53: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
util.c: In function ‘correct_underflow’:
util.c:149: warning: incompatible implicit declaration of built-in function ‘fprintf’
util.c:149: error: ‘stderr’ undeclared (first use in this function)
util.c:149: error: (Each undeclared identifier is reported only once
util.c:149: error: for each function it appears in.)
util.c:151: warning: incompatible implicit declaration of built-in function ‘exit’
util.c:154: warning: incompatible implicit declaration of built-in function ‘fprintf’
util.c:165: warning: incompatible implicit declaration of built-in function ‘exit’
util.c: In function ‘next_bits’:
util.c:202: error: ‘NULL’ undeclared (first use in this function)
util.c: In function ‘get_ext_data’:
util.c:255: warning: incompatible implicit declaration of built-in function ‘malloc’
util.c: In function ‘next_start_code’:
util.c:318: error: ‘NULL’ undeclared (first use in this function)
util.c: In function ‘get_extra_bit_info’:
util.c:447: error: ‘NULL’ undeclared (first use in this function)
util.c:452: warning: incompatible implicit declaration of built-in function ‘malloc’
make: *** [util.o] Error 1
```

anyone have any ideas? are there files missing from my unpacked archive?

It may be a little bit late since that post is from July, but maybe someone else will have the same problem (I know I did :) ).

The problem is that the "buld-essential" package isn't installed, that's why gcc can't find all the standard C header files.

```
sudo apt-get install build-essential
```

gets rid of those error messages.

---

### Post by tryorke on 2008-09-29
Great guide!

Just to add to this a bit: You can take this one step further and convert files anywhere, not just within the DPG folder:

Open a terminal window in your home directory, then navigate to ~/.gnome2/nautilus-scripts:
```
cd ~/.gnome2/nautilus-scripts
```

Then create a shell script for automating the conversion:
```
gedit "Convert to DPG.sh"
```

Then copy and paste the following:
```
#!/usr/bin/env bash

python **/path/to**/dpgconv-0.43.py $1
wait
zenity --info --text="$1 converted for NDS!"
```
Make sure to edit the /path/to/ with the actual path where you put your dpgconv-0.43.py script. I put mine in ~/.scripts with the rest of my miscellaneous scripts

Finally, save and close gedit, then make the file executable:
```
chmod +x "Convert to DPG.sh"
```

Now you can convert any video from Nautilus by right clicking on it, selecting "Scripts" and choosing "Convert to DPG.sh" from the menu.

---

### Post by jaguar1975cn on 2008-09-30
Woohoo, I tried your tools. Perfect!!!!
Thanks a lot.

---

### Post by paracite on 2008-10-06
I'm having trouble with this. I don't think it's working properly... 

I used the tools, and that script and it says "Converted for NDS!" But I don't see the file anywhere.

---

### Post by babujbf on 2008-11-05
> **mcbean said:**
> Thanks for this, very useful! 

In case people don't read the .py script, you can add --hq or --lq to the arguments to make it higher or lower quality.

yeah about that... if you were to use that... where do you put the argument?

python dpgconv-0.43.py video.avi --lq ?

---

### Post by skedone on 2008-11-14
you put the arguments after the name of the program mate in other words .py --hq or --lq

---

### Post by sp176 on 2008-12-05
Thanks for the info you provided, but I am stuck on step 2:
Here is output from my terminal

~/DPG$ cd /home/DPG/mpeg_stat-2.2b-src/mpeg_stat
~/DPG/mpeg_stat-2.2b-src/mpeg_stat$ make
strip mpeg_stat
~/DPG/mpeg_stat-2.2b-src/mpeg_stat$ cd /home/DPG
~/DPG$ sudo cp mpeg_stat /bin/mpeg_stat
cp: cannot stat `mpeg_stat': No such file or directory
~/DPG$ sudo mpeg_stat.1 /bin/mpeg_stat.1
sudo: mpeg_stat.1: command not found


Please let me know where I have gone wrong.  Those files look like there are there to me.  Is it the 'make' that isn't working?

---

### Post by gCuezy on 2008-12-14
hopefull someone's still checking this topic...

I compiled mpeg_stat and it's in the bin and I am using my desktop instead of the DPG folder.

I tried making the dpgconv.py file executable but the terminal kept saying "No Such Command" (or w/e).  

So I instead started typing "python dpgconv.py filename.ext" and I get
```
Error:
Sh: mpeg_stat: Permission Denied
```

Same thing if I add 'sudo'


Please help... would like to get this working for my NDS ;)

---

### Post by NorQue on 2008-12-15
> **gCuezy said:**
> I compiled mpeg_stat and it's in the bin [...]Is mpeg_stat.1 there, too?  And is mpeg_stat properly installed? It should start reading from stdin when you start it from command line with 'mpeg_stat'. Have you followed the tutorial from post #1 in this thread?

EDIT:
Oh, and make sure you got the latest version of dpgconv, the one from post #1 is a bit outdated, newest is 8. [Homepage](http://theli.is-a-geek.org/blog/static/dpgconv) has moved, too.

---

### Post by sugargenius on 2008-12-16
I get these error when I compile
```

wlott@pluto:~/DPG/mpeg_stat$ make
gcc -I/usr/include -O    -c -o util.o util.c
gcc -I/usr/include -O    -c -o main.o main.c
main.c: In function âmainâ:
main.c:518: warning: passing argument 2 of âsignalâ from incompatible pointer type
main.c:171: warning: return type of âmainâ is not âintâ
gcc -I/usr/include -O    -c -o decoders.o decoders.c
gcc -I/usr/include -O    -c -o video.o video.c
video.c: In function âParseGOPâ:
video.c:952: warning: incompatible implicit declaration of built-in function âmemsetâ
gcc -I/usr/include -O    -c -o jrevdct.o jrevdct.c
gcc -I/usr/include -O    -c -o parseblock.o parseblock.c
parseblock.c: In function âParseReconBlockâ:
parseblock.c:132: warning: incompatible implicit declaration of built-in function âstrcatâ
parseblock.c:227: warning: incompatible implicit declaration of built-in function âstrcatâ
parseblock.c:273: warning: incompatible implicit declaration of built-in function âstrcatâ
parseblock.c:298: warning: incompatible implicit declaration of built-in function âstrcatâ
parseblock.c:333: warning: incompatible implicit declaration of built-in function âstrcatâ
parseblock.c:359: warning: incompatible implicit declaration of built-in function âstrcatâ
gcc -I/usr/include -O    -c -o motionvector.o motionvector.c
gcc -I/usr/include -O    -c -o filter.o filter.c
gcc -I/usr/include -O    -c -o readfile.o readfile.c
readfile.c: In function âReadPackHeaderâ:
readfile.c:583: warning: format â%08xâ expects type âunsigned intâ, but argument 6 has type âlong unsigned intâ
readfile.c:589: warning: format â%08xâ expects type âunsigned intâ, but argument 4 has type âlong unsigned intâ
readfile.c: In function âReadSystemHeaderâ:
readfile.c:664: warning: format â%08xâ expects type âunsigned intâ, but argument 4 has type âlong unsigned intâ
readfile.c:666: warning: format â%08xâ expects type âunsigned intâ, but argument 4 has type âlong unsigned intâ
readfile.c:672: warning: format â%08xâ expects type âunsigned intâ, but argument 4 has type âlong unsigned intâ
readfile.c:686: warning: format â%0xâ expects type âunsigned intâ, but argument 5 has type âlong unsigned intâ
readfile.c: In function âReadPacketâ:
readfile.c:970: warning: format â%uâ expects type âunsigned intâ, but argument 4 has type âlong unsigned intâ
readfile.c:970: warning: format â%08xâ expects type âunsigned intâ, but argument 5 has type âlong unsigned intâ
readfile.c:973: warning: format â%uâ expects type âunsigned intâ, but argument 4 has type âlong unsigned intâ
readfile.c:973: warning: format â%08xâ expects type âunsigned intâ, but argument 5 has type âlong unsigned intâ
readfile.c:911: warning: ignoring return value of âfreadâ, declared with attribute warn_unused_result
readfile.c:921: warning: ignoring return value of âfreadâ, declared with attribute warn_unused_result
readfile.c:929: warning: ignoring return value of âfreadâ, declared with attribute warn_unused_result
readfile.c:930: warning: ignoring return value of âfreadâ, declared with attribute warn_unused_result
readfile.c:934: warning: ignoring return value of âfreadâ, declared with attribute warn_unused_result
readfile.c:935: warning: ignoring return value of âfreadâ, declared with attribute warn_unused_result
readfile.c:940: warning: ignoring return value of âfreadâ, declared with attribute warn_unused_result
readfile.c:941: warning: ignoring return value of âfreadâ, declared with attribute warn_unused_result
readfile.c:948: warning: ignoring return value of âfreadâ, declared with attribute warn_unused_result
readfile.c:1049: warning: ignoring return value of âfreadâ, declared with attribute warn_unused_result
readfile.c:1059: warning: ignoring return value of âfreadâ, declared with attribute warn_unused_result
gcc -g util.o main.o decoders.o video.o jrevdct.o parseblock.o motionvector.o filter.o readfile.o  -lm -o mpeg_stat
strip mpeg_stat


```

---

### Post by NorQue on 2008-12-19
sugargenius, you need to install build-essential.

---

### Post by sugargenius on 2008-12-23
> **NorQue said:**
> sugargenius, you need to install build-essential.

Nope.  build-essentials was installed when I compiled.

wlott@pluto:~/DPG/mpeg_stat$ dpkg-query -s build-essential
Package: build-essential
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 48
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 11.4

---

### Post by mcbean on 2009-04-10
ignore me! I don't know how to delete posts!
 
I couldn't get the nautilus script posted earlier to work. But I added quotation marks to the argument as it was skipping the spaces ^^.

---

### Post by SPARTAN-118 on 2009-07-24
> **tryorke said:**
> Great guide!

Just to add to this a bit: You can take this one step further and convert files anywhere, not just within the DPG folder:

Open a terminal window in your home directory, then navigate to ~/.gnome2/nautilus-scripts:
```
cd ~/.gnome2/nautilus-scripts
```Then create a shell script for automating the conversion:
```
gedit "Convert to DPG.sh"
```Then copy and paste the following:
```
#!/usr/bin/env bash

python **/path/to**/dpgconv-0.43.py $1
wait
zenity --info --text="$1 converted for NDS!"
```Make sure to edit the /path/to/ with the actual path where you put your dpgconv-0.43.py script. I put mine in ~/.scripts with the rest of my miscellaneous scripts

Finally, save and close gedit, then make the file executable:
```
chmod +x "Convert to DPG.sh"
```Now you can convert any video from Nautilus by right clicking on it, selecting "Scripts" and choosing "Convert to DPG.sh" from the menu.

Nvm, this script works, just make sure the file doesn't have any spaces.
Underscores work, and I think dashes work, too, just not spaces.

SPARTAN-118

BTW, does anybody know where I can find a [Linux] media player capable of playing DPG files? I want to make sure they work before I put them on my R4DS.

---

### Post by Devi 710 on 2009-08-30
Hi,

After installing everything fine I get this error in terminal:

```
  File "dpgconv-0.43.py", line 13
    <HEAD>
    ^
SyntaxError: invalid syntax

```

I tried taking out line 13 by changing it to:
```
#<HEAD>
```

and

```
#</HEAD>
```

Then I ran the script again and got this:

```
File "dpgconv-0.43.py", line 14
SyntaxError: Non-ASCII character '\xd5' in file dpgconv-0.43.py on line 14, but no encoding declared; see http://www.python.org/peps/pep-0263.html for details
```

Can anyone help me out?

Thanks,

Devi

---

### Post by marc_firth on 2009-09-14
Hi Dev,

I had this error as well.  It appears that the original link is now an HTML page and no longer the python script.

I got a clue from the wiki article ([http://en.wikipedia.org/wiki/NDs-mPeG](http://en.wikipedia.org/wiki/NDs-mPeG)) and used a mirror libnk to get the python script:
[http://theli.is-a-geek.org/files/dpgconv/dpgconv-0.43.py.gz](http://theli.is-a-geek.org/files/dpgconv/dpgconv-0.43.py.gz)

Hope that helps you.

Marc

---

### Post by stefcep on 2009-12-12
> **sp176 said:**
> Thanks for the info you provided, but I am stuck on step 2:
Here is output from my terminal

~/DPG$ cd /home/DPG/mpeg_stat-2.2b-src/mpeg_stat
~/DPG/mpeg_stat-2.2b-src/mpeg_stat$ make
strip mpeg_stat
~/DPG/mpeg_stat-2.2b-src/mpeg_stat$ cd /home/DPG
~/DPG$ sudo cp mpeg_stat /bin/mpeg_stat
cp: cannot stat `mpeg_stat': No such file or directory
~/DPG$ sudo mpeg_stat.1 /bin/mpeg_stat.1
sudo: mpeg_stat.1: command not found


Please let me know where I have gone wrong.  Those files look like there are there to me.  Is it the 'make' that isn't working?

i had the same errors: no such file or directory using 9.04.

its because the /home is where you already are when you open a terminal.

i did this: 
cd DPG
cd mpeg_stat-2.2b-src
cd mpeg_stat
sudo cp mpeg_stat /bin/mpeg_stat
sudo cp mpeg_stat.1 /bin/mpeg_stat.1

All works for me, and it converts avi video really quickly compared to Super in Windows.

---

### Post by HeadHunter00 on 2009-12-14
> **yanghyungryul said:**
> What is a terminal???
:lolflag: Anyway, its like command prompt in windows, you go to applications->accessories->terminal

---

### Post by HeadHunter00 on 2009-12-14
yeah. worked like a charm. but only when I use the nautilus script. Otherwise, the file isn't there.

---

### Post by Kierek on 2010-01-17
Hi.

I have a problem with this script. It seems that it doesn't see files which I want to convert. 

```
desktop:/home/kierek/DPG# python dpgconv-9.py dbk31.avi  
mpeg_stat -- MPEG Analyzer for MPEG I video streams (version 2.2b) 
MPlayer SVN-r30075 (C) 2000-2009 MPlayer Team 
Error: 
MPlayer SVN-r30075 (C) 2000-2009 MPlayer Team 
No file given 
 
Exiting... (error parsing command line) 
```Am I doing something wrong?

PS.
It doesn't work through nautilus script, too. >_>

[SIZE=1]Sorry for my crappy English.[/SIZE]

---

### Post by hibliss on 2010-03-09
This works great as others have said. The sit ehosting the Python script was not working for me, so I found it on Google and copied it to a blank document, naming it appropriately.

Here it is, just copy and paste to an empty doc:

```
#! /usr/bin/python
# DPG Converter by Anton Romanov (c) 2006
# released under GPL-2
# 
"""A script to transcode video files to DPG format suitable for
   Nintendo DS (tm)
   
dpgconv.py file1 file2 file3 ... fileN
command line options:
	--dpg
		0,1,2 sets DPG version.. default is DPG2
	
	--pf
		sets pixel format, default is 3
		0        RGB15
		1        RGB18
		2        RGB21
		3        RGB24 

	-q,--hq
		high quality video
	-l,--lq
		low quality video(takes no effect when --hq,-q is set)]
	default is normal quality
	
	-v,--vbps xxx
		sets video stream bps in kb/s(default: 256)
	-a,--abps xxx
		sets audio stream bps kb/s (default: 128)
	-f,--fps xx
		sets video frames per second (default:15)
	-z,--hz
		sets audio frequency (default:32000)
	-c,--channels
		2 - stereo, 1 - mono
		default is to leave as is unless input audio channels
		number is bigger then 2 ... then default is stereo
	--aid n
		use audio track n
	--height xxx
		destination video height
	--width xxx
		destination video width

	--mv
		additional parameters for mencoder for video

	--ma
		additional parameters for mencoder for audio
	
	Hardcoding subtitles
	--nosub
		do no try autoloading of subtitles
		(default is to try to load subtitle with matching filename)
	--sub,-s xxx
		Specify subtitles for hardcoding into video output
		(is obviously only usable if you specify one file at a time)
	--sid n
		use subtitle track n
	--subcp xxx
		specify subtitles encoding
	--font xxx
		specify font for subtitles
  EXAMPLE:
    --font ~/arial-14/font.desc
    --font ~/arialuni.ttf
    --font 'Bitstream Vera Sans'

  You can specify font, subcp and other additional mencoder parameters in
	~/.mplayer/mencoder.conf
  EXAMPLE:
	font=/usr/local/share/fonts/msfonts/comic.ttf
	subcp=cp1251

"""
import sys, os, optparse
MP2TMP="mp2tmp.mp2"
MPGTMP="mpgtmp.mpg"
HEADERTMP="header.tmp"
GOPTMP="gop.tmp"
STATTMP="stat.tmp"

MENCODER="mencoder"
MPLAYER="mplayer"
MPEG_STAT="mpeg_stat"




#Print a help message if requested.
if "-h" in sys.argv or "-help" in sys.argv or "--help" in sys.argv:
	print __doc__
	raise SystemExit

def cleanup_callback(a,b):
	print "Removing temporary files"
	if os.path.lexists ( MPGTMP ):
		os.unlink ( MPGTMP )
	if os.path.lexists ( MP2TMP ):
		os.unlink ( MP2TMP )
	if os.path.lexists ( HEADERTMP ):
		os.unlink ( HEADERTMP )
	if os.path.lexists ( GOPTMP ):
		os.unlink ( GOPTMP )
	if os.path.lexists ( STATTMP ):
		os.unlink ( STATTMP )

def conv_vid(file):
	if options.dpg == 0:
		v_pf = "format=rgb24,"
		options.pf = 3
	elif options.pf == 3:
		v_pf = "format=rgb24,"
	elif options.pf == 2:
		v_pf = "format=rgb21,"
	elif options.pf == 1:
		v_pf = "format=rgb18,"
	elif options.pf == 0:
		v_pf = "format=rgb15,"
	else:
		v_pf = "format=rgb24,"
		options.pf = 3

	if options.hq:
		v_cmd =  ( " \""+ file +"\" -v -ofps " + `options.fps` + " -sws 9 -vf " + v_pf + "scale=" + `options.width` + ":" + `options.height` +":::3 -nosound -ovc lavc -lavcopts vcodec=mpeg1video:vstrict=-2:mbd=2:trell:cbp:mv0:cmp=6:subcmp=6:precmp=6:dia=3:predia=3:last_pred=3:vbitrate=" + `options.vbps` + " -o " + MPGTMP + " -of rawvideo" )
	elif options.lq:
		v_cmd = ( " \"" + file + "\" -v -ofps " + `options.fps` + " -vf " + v_pf + "scale=" + `options.width` + ":" + `options.height` + " -nosound -ovc lavc -lavcopts vcodec=mpeg1video:vstrict=-2:vbitrate=" + `options.vbps` + " -o " + MPGTMP + " -of rawvideo" )
	else :
		v_cmd = ( " \""+ file +"\" -v -ofps " + `options.fps` + " -sws 9 -vf " + v_pf + "scale=" + `options.width` + ":" + `options.height` + ":::3 -nosound -ovc lavc -lavcopts vcodec=mpeg1video:vstrict=-2:mbd=2:trell:cbp:mv0:cmp=2:subcmp=2:precmp=2:vbitrate=" + `options.vbps` + " -o " + MPGTMP + " -of rawvideo")
	
	if options.nosub:
		if options.sub != None:
			v_cmd = " -sub \"" + options.sub + "\" " + v_cmd
	else:
		basename = os.path.splitext ( file )[0]
		if options.sid != None:
			v_cmd = " -sid \"" + str(options.sid) + "\" " + v_cmd
		if options.sub != None:
			v_cmd = " -sub \"" + options.sub + "\" " + v_cmd
		elif os.path.exists ( basename + ".***" ):
			v_cmd = " -sub \"" + basename + ".***" + "\" " + v_cmd
		elif os.path.exists ( basename + ".srt" ):
			v_cmd = " -sub \"" + basename + ".srt" + "\" " + v_cmd
		elif os.path.exists ( basename + ".sub" ):
			v_cmd = " -sub \"" + basename + ".sub" + "\" " + v_cmd
		elif os.path.exists ( basename + ".ssa" ):
			v_cmd = " -sub \"" + basename + ".ssa" + "\" " + v_cmd
	
	if options.subcp != None:
		v_cmd = " -subcp " + options.subcp + v_cmd
	if options.font != None:
		v_cmd = " -font \"" + options.font + "\"" + v_cmd

	v_cmd = MENCODER + " " + v_cmd
	v_cmd = v_cmd + " " + options.mv
	#print v_cmd 
	proc = subprocess.Popen(v_cmd,shell=True,stdout=subprocess.PIPE,universal_newlines=True,stderr=open('/dev/null', 'w'))
	
	p = re.compile ("f (\(.*%\))")
	for line in proc.stdout:
		m = p.search( line )
		
		if m:
			print "Transcoding video: " + m.group(1) + "\r" ,



	print "Transcoding video:   done"

def conv_aud(file):
	a_cmd = ( MENCODER + " \"" +file + "\" -v -of rawaudio -oac lavc -ovc copy -lavcopts acodec=mp2:abitrate=" + `options.abps` + " -o " + MP2TMP )
	identify = commands.getoutput( MPLAYER + " -frames 0 -vo null -ao null -identify \"" + file + "\" | grep -E \"^ID|VIDEO|AUDIO\"")
	p = re.compile ("([0-9]*)( ch)")
	m = p.search( identify )
	if m:
		c = m.group(1)
		if options.channels == None:
			if c > 2:
				a_cmd = a_cmd + " -af channels=2,resample=" +`options.hz`+ ":1:2"
			else:
				a_cmd = a_cmd + " -af resample=" +`options.hz`+ ":1:2"
		elif options.channels >= 2:
			a_cmd = a_cmd + " -af channels=2,resample=" +`options.hz`+ ":1:2"
		else:
			a_cmd = a_cmd + " -af channels=1,resample=" +`options.hz`+ ":1:2"
	else:
		print "Error running mplayer:"
		print identify

	if options.aid != None:
		a_cmd = a_cmd + " -aid " + str(options.aid)

	a_cmd = a_cmd + " " + options.ma
	#print a_cmd

	proc = subprocess.Popen(a_cmd,shell=True,stdout=subprocess.PIPE,universal_newlines=True,stderr=subprocess.STDOUT)

	v_out = ""
	
	p = re.compile ("f (\(.*%\))")
	for line in proc.stdout:
		m = p.search( line )
		if m:
			print "Transcoding audio: " + m.group(1) + "\r" ,
	print "Transcoding audio:   done"


def write_header(frames):
	print "Creating header"

	audiostart=36
	if options.dpg == 1:
		audiostart += 4
	elif options.dpg == 2:
		audiostart += 12
	
	audiosize = os.stat(MP2TMP)[stat.ST_SIZE]
	videosize = os.stat(MPGTMP)[stat.ST_SIZE]
	videostart = audiostart + audiosize
	videoend = videostart + videosize
	f=open(HEADERTMP, 'wb')
	DPG = "DPG" + `options.dpg`
	headerValues = [ DPG, int(frames), options.fps, 0, options.hz , 0 ,int(audiostart), int(audiosize), int(videostart), int(videosize) ]
	
	f.write (struct.pack( "4s" , headerValues[0]))
	f.write (struct.pack ( "<l" , headerValues[1]))
	f.write (struct.pack ( ">h" , headerValues[2]))
	f.write (struct.pack ( ">h" , headerValues[3]))
	f.write (struct.pack ( "<l" , headerValues[4]))
	f.write (struct.pack ( "<l" , headerValues[5]))
	f.write (struct.pack ( "<l" , headerValues[6]))
	f.write (struct.pack ( "<l" , headerValues[7]))
	f.write (struct.pack ( "<l" , headerValues[8]))
	f.write (struct.pack ( "<l" , headerValues[9]))

	if options.dpg == 0:
		f.write (struct.pack ( "<l" , options.pf ))
	if options.dpg == 2:
		gopsize = os.stat(GOPTMP)[stat.ST_SIZE]
		f.write (struct.pack ( "<l" , videoend ))
		f.write (struct.pack ( "<l" , gopsize))
		f.write (struct.pack ( "<l" , options.pf ))


	f.close()
def mpeg_stat():
	p = re.compile ("frames: ([0-9]*)\.")
	s_out = commands.getoutput( MPEG_STAT + " -offset " + STATTMP + " " + MPGTMP )
	m = p.search( s_out )
	if m:
		frames = m.group(1)
		if options.dpg == 2:
			gop=open(GOPTMP, 'wb')
			stat=open(STATTMP, 'rb')
			frame = 0
			for line in stat:
				sline = line.split()
				if sline[0] == "picture" :
					frame += 1
				elif sline[0] == "sequence":
					gop.write (struct.pack ( "<l" , frame ))
					gop.write (struct.pack ( "<l" , int(sline[1])/8 )) # mpeg_stat shows bit offsets
			gop.close()
			stat.close()
	else:
		print s_out
		return 0
	return frames

def conv_file(file):
	if not (os.path.lexists ( file )):
		print "File " + file + " doesn't exist"
#		return
	print "Converting " + file
	conv_vid (file)
	conv_aud(file)
	frames = mpeg_stat()
	if frames == 0:
		print "Error using mpeg_stat ... see error above"
		cleanup_callback (0,0)
		return
	write_header(frames)
	dpgname = os.path.basename ( os.path.splitext ( file )[0] ) + ".dpg"
	
	print "Creating " + dpgname
	commands.getoutput( "cat \"" + HEADERTMP + "\" \"" + MP2TMP + "\" \"" + MPGTMP + "\" > \"" + dpgname + "\"")
	if options.dpg == 2:
		commands.getoutput( "cat \"" + GOPTMP + "\" >> \"" + dpgname + "\"")
	
	cleanup_callback (0,0)
	print "Done converting \"" + file + "\" to \"" + dpgname + "\""



from optparse import OptionParser
parser = OptionParser()
parser.add_option("-f","--fps", type="int", dest="fps" , default=15)
parser.add_option("-q","--hq",action="store_true", dest="hq", default=False)
parser.add_option("-l","--lq",action="store_true", dest="lq", default=False)
parser.add_option("-v","--vbps", type="int", dest="vbps", default=256)
parser.add_option("-a","--abps", type="int", dest="abps", default=128)
parser.add_option("--height", type="int", dest="height", default=192)
parser.add_option("--width", type="int", dest="width", default=256)
parser.add_option("-z","--hz", type="int", dest="hz", default=32000)
parser.add_option("-c","--channels", type="int", dest="channels")
parser.add_option("--subcp", dest="subcp")
parser.add_option("-s","--sub", dest="sub")
parser.add_option("--font", dest="font")
parser.add_option("--mv", dest="mv",default="")
parser.add_option("--ma", dest="ma",default="")
parser.add_option("--nosub",action="store_true", dest="nosub", default=False)
parser.add_option("--dpg", type="int" , dest="dpg", default=2)
parser.add_option("--pf", type="int" , dest="pf", default=3)
parser.add_option("--sid", type="int" , dest="sid")
parser.add_option("--aid", type="int" , dest="aid")
(options, args) = parser.parse_args()

import signal

signal.signal(signal.SIGINT, cleanup_callback)
signal.signal(signal.SIGTERM, cleanup_callback)

import commands,re,stat,struct,subprocess
if options.dpg > 2:
	options.dpg = 2
if options.dpg < 0:
	options.dpg = 2


test = commands.getoutput ( MPEG_STAT + " --" )
m = re.compile ("mpeg_stat --(.*)").search(test)
if m:
	print m.group(0)
else:
	print "Error:"
	print test
	exit (0)
test = commands.getoutput ( MPLAYER )
m = re.compile ("^MPlayer.*").search(test)
if m:
	print m.group(0)
else:
	print "Error:"
	print test
	exit (0)
test = commands.getoutput ( MENCODER)
m = re.compile ("^MEncoder.*").search(test)
if m:
	print m.group(0)
else:
	print "Error:"
	print test
	exit (0)
print "It seems we found all programs :)...continuing"
print "______________________________________________"

for file in args:
	conv_file(file)

```

---

### Post by sebbytek on 2010-05-17
I' on Ubuntu Lucid 10.04 and it does not work :(
this is the message I got

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
Usage:   mplayer [options] [url|path/]filename

Basic options: (complete list in the man page)
 -vo <drv>        select video output driver ('-vo help' for a list)
 -ao <drv>        select audio output driver ('-ao help' for a list)
 vcd://<trackno>  play (S)VCD (Super Video CD) track (raw device, no mount)
 dvd://<titleno>  play DVD title from device instead of plain file
 -alang/-slang    select DVD audio/subtitle language (by 2-char country code)
 -ss <position>   seek to given (seconds or hh:mm:ss) position
 -nosound         do not play sound
 -fs              fullscreen playback (or -vm, -zoom, details in the man page)
 -x <x> -y <y>    set display resolution (for use with -vm or -zoom)
 -sub <file>      specify subtitle file to use (also see -subfps, -subdelay)
 -playlist <file> specify playlist file
 -vid x -aid y    select video (x) and audio (y) stream to play
 -fps x -srate y  change video (x fps) and audio (y Hz) rate
 -pp <quality>    enable postprocessing filter (details in the man page)
 -framedrop       enable frame dropping (for slow machines)

Basic keys: (complete list in the man page, also check input.conf)
 <-  or  ->       seek backward/forward 10 seconds
 down or up       seek backward/forward  1 minute
 pgdown or pgup   seek backward/forward 10 minutes
 < or >           step backward/forward in playlist
 p or SPACE       pause movie (press any key to continue)
 q or ESC         stop playing and quit program
 + or -           adjust audio delay by +/- 0.1 second
 o                cycle OSD mode:  none / seekbar / seekbar + timer
 * or /           increase or decrease PCM volume
 x or z           adjust subtitle delay by +/- 0.1 second
 r or t           adjust subtitle position up/down, also see -vf expand

 * * * SEE THE MAN PAGE FOR DETAILS, FURTHER (ADVANCED) OPTIONS AND KEYS * * *


Help me please ! It was working on 9.10

---

### Post by aglauser on 2010-05-27
> **sebbytek said:**
> I' on Ubuntu Lucid 10.04 and it does not work :(
this is the message I got

bt_audio_service_open: connect() failed: Connection refused (111)


I too ran into this problem.

I found the solution on [LinuxQuestions]("http://www.ogre3d.org/addonforums/viewtopic.php?f=10&t=11539") by googling "bt_audio_service_open: connect() failed".

The short answer is to remove the package "bluez-alsa".  It seems that ALSA is trying to access Bluetooth audio devices even though none are attached.

---

### Post by xdzzz on 2011-04-27
> **Kierek said:**
> Hi.

I have a problem with this script. It seems that it doesn't see files which I want to convert. 

```
desktop:/home/kierek/DPG# python dpgconv-9.py dbk31.avi  
mpeg_stat -- MPEG Analyzer for MPEG I video streams (version 2.2b) 
MPlayer SVN-r30075 (C) 2000-2009 MPlayer Team 
Error: 
MPlayer SVN-r30075 (C) 2000-2009 MPlayer Team 
No file given 
 
Exiting... (error parsing command line) 
```Am I doing something wrong?

PS.
It doesn't work through nautilus script, too. >_>

[SIZE=1]Sorry for my crappy English.[/SIZE]

BUMP. I'm having the EXACT same error! I followed the directions exactly. We might be missing a dependency or something. but I checked EVERYTHING. mpeg_stat GOOD. ffmpeg GOOD. mencoder GOOD. mplayer GOOD. dpgconv-10.py GOOD. I still get that same error. If i use dpgconv-0.3.py it converts it to a .mpg file but not a .dpg

---

### Post by asifior on 2011-06-28
Thank you, Skatertjah, for sharing this. And thanks to hibliss for providing the script.
I was able to make it work like a charm under Ubuntu 11.04.

Here is the complete package, just follow the directions from the first post (starting from the make).

[http://goo.gl/Vq9rV](http://goo.gl/Vq9rV)

---

