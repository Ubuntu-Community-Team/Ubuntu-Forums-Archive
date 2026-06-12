---
title: "Joining *.avi.001, *.avi.002 etc video files"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by oldrocker99 on 2008-05-23
Using QuickPAR on Windows, I could join a video split into many numbered files by just verifying the .PAR file. 

How can I join a 102 part AVI without using CAT and typing in 102 files names? I have tried CAT before and it apparently didn't like binary files...:confused:

---

### Post by bumanie on 2008-05-23
This may help [http://www.doctort.org/adam/nerd-notes/concatenating-avi-files.html](http://www.doctort.org/adam/nerd-notes/concatenating-avi-files.html) or this may help [http://www.afterdawn.com/guides/archive/virtualdub_join_avi.cfm](http://www.afterdawn.com/guides/archive/virtualdub_join_avi.cfm)

---

### Post by aeiah on 2008-05-23
i was gonna suggest cat but it seems you arent happy with it. ive not always got the results i want either without rebuilding with mencoder (forceidx flag)

anyway. i dont know the ins and outs of file downloading on usenet (which i assume you're doing) but here are some links:


[http://www.linuxforums.org/forum/linux-newbie/71673-par-par2-program.html](http://www.linuxforums.org/forum/linux-newbie/71673-par-par2-program.html)

[http://ubuntuforums.org/showthread.php?t=169749](http://ubuntuforums.org/showthread.php?t=169749)

---

### Post by sdennie on 2008-05-23
On the command line, I've used avimerge many times with great success.  I believe it can be installed with:

```

sudo apt-get install transcode

```

For a gui, I think avidemux looks pretty nice but, I've not used it much:

```

sudo apt-get install avidemux

```

---

### Post by el-mar01 on 2008-05-23
Install HJ split for Windows under WINE (don't bother with the Linux version I couldn't get it to work)

[http://www.freebyte.com/hjsplit/](http://www.freebyte.com/hjsplit/)

---

### Post by vanadium on 2008-05-23
cat is perfectly fine for joining files that have been split binary:

cat name.avi.* > myfinalmovie.avi

will do the job.

However, this applies only if an avi file was binary split into pieces (that you cannot play indepedently). If you are looking to join individual functional avi's, then you need avimerge or avidemux (graphical utility very similar to virtualdub).

---

### Post by oldrocker99 on 2008-05-23
> **el-mar01 said:**
> Install HJ split for Windows under WINE (don't bother with the Linux version I couldn't get it to work)

[http://www.freebyte.com/hjsplit/](http://www.freebyte.com/hjsplit/)

Yep, that did the trick. I couldn't get any of the Linux versions to work either.

Thanks!

---

### Post by FakeOutdoorsman on 2008-05-23
ffmpeg can do this: [FFmpeg FAQ: 2.19 How can I join video files?]("http://ffmpeg.mplayerhq.hu/faq.html#SEC29")

---

### Post by colbobs on 2008-06-18
Hello Forum.
Firstly thanks to all the contributers who have made my move to Ubuntu a little less stressful.
I'm having all  kinds of problems in that the suggestions given in this thread are not working for me - I'll admit that I know precious little about Linux and code and so I'm getting very frustrated when I have successfully downloaded split files but cannot get any of the file joiners (linux versions or otherwise) to work.
Anyone shed any light on what I'm doing wrong?  It's probably something very simple.....I hope.  
Col

---

### Post by Martje_001 on 2008-06-18
colbobs: Have you installed wine? You could then try to install the Windows program, as suggested above.

---

### Post by colbobs on 2008-06-18
> **Martje_001 said:**
> colbobs: Have you installed wine? You could then try to install the Windows program, as suggested above.

Thanks Martje.  I had no idea what wine was or meant.  That's the problem with FLAs (four letter acronyms) you have to know them to know what they are.
As soon as you said "have you installed wine" I thought - I'll have a look to see what synaptic package manager will produce for me.  I've found it and I'm downloading now.

UPDATE
Success!  Downloaded hjsplit for windows.  The .exe is on my desktop and I'm assuming I can move it to wherever I pretty much like.  Wondered what had happened to WINE and as its the WINdows Emulator I right clicked and there it was offering to open hjsplit.exe for me.
Joined my files and now I'm a happy bunny!  Thanks Martje!

---

### Post by RomeReactor on 2008-06-18
Hi. Just as a comment, if you don't mind installing Java on your system--or have it already installed--the [Java version of HJ Split]("http://www.freebyte.com/hjsplit/#java") works very well. You can get it [here]("http://www.freebyte.com/download/hjsplit/hjsplit_g.jar").

To run it from the terminal (or by pressing ALT+F2):
```
java -jar /path/to/hjsplit_g.jar
```

You can make a launcher for it using that command.

---

### Post by oudalrich on 2008-06-19
Sorry, but I can't help finding it ridiculous when people recommend installing Wine and a Windows program to do the most simple thing in the world. In the OP's case, all that's necessary is concatenating the files. 7zip will do that just fine (it will also unpack just about anything else for you). Install it (not sure whether you have to enable Universe or something):
```
sudo aptitude install p7zip-full
```
And then give it the name of the first file:
```
7z x myvideo.avi.001
```
Done. For joining individual video files, there's mencoder, which works with wildcards. So suppose you have individual video files vid01.avi ... vid99.avi, all you have to do is install mencoder:
```
sudo aptitude install mencoder
```
... and then use it to create a new single video file:
```
mencoder -ovc copy -oac copy -forceidx -o allvids.avi vid*.avi
```
And done. If you want to join WMV files, there's asfbin, which has a Linux version. Download it [here]("http://www.radioactivepages.com/index.php?docid=asfbin&section=software"), unzip it, make it executable, and do something like this:
```
ls vid*.wmv > vidlist
./asfbin-bin -l vidlist -o allvids.wmv
```
And that's it.

---

### Post by karankrn on 2008-06-19
great post people!
thanks for making the ubuntu journey easier!

---

### Post by colbobs on 2008-06-19
ouldalrich - honestly I've tried other ways and I personally have not had much success - I'm new to Ubuntu and Linux so fiddling with code does not give me a warm fuzzy feeling - not just yet anyway LOL.

RomeReactor - I agree using a java version (with java installed) sounds easy but I'm not very lucky it seems as that wouldn't work either!

WINE however did work, once I figured out what it meant.

---

### Post by kruykaze on 2009-10-17
> **vanadium said:**
> cat is perfectly fine for joining files that have been split binary:

cat name.avi.* > myfinalmovie.avi

will do the job.

However, this applies only if an avi file was binary split into pieces (that you cannot play indepedently). If you are looking to join individual functional avi's, then you need avimerge or avidemux (graphical utility very similar to virtualdub).

Thanks! worked perfectly!

---

### Post by MrWES on 2009-10-17
> **kruykaze said:**
> Thanks! worked perfectly!

Avimerge and avisplit are both part of the transcode package:
```
avimerge
avimerge (transcode v1.0.7) (C) 2001-2004 Thomas Oestreich, T. Bitterberg, 2004-2008 Transcode Team

Usage: avimerge [options]
	 -o file                   output file name
	 -i file1 [file2 [...]]    input file(s)
	 -p file                   multiplex additional audio track from file
	 -a num                    select audio track number from input file [0]
	 -A num                    select audio track number in output file [next]
	 -b n                      handle vbr audio [autodetect]
	 -c                        drop video frames in case audio is missing [off]
	 -f FILE                   read AVI comments from FILE [off]
	 -x FILE                   read AVI index from FILE [off] (see aviindex(1))

```

```
avisplit
avisplit (transcode v1.0.7) (C) 2001-2003 Thomas Oestreich, 2003-2008 Transcode Team

Usage: avisplit [options]
	 -i name             file name
	 -s size             de-chunk based on size in MB (0=dechunk)
	 -H n                split only first n chunks [all]
	 -t s1-s2[,s3-s4,..] de-chunk based on time/framecode (n:m:l.k) [off]
	 -c                  merge chunks on-the-fly for option -t [off]
	 -m                  force split at upper limit for option -t [off]
	 -o base             split to base-%04d.avi [name-%04d]
	 -b n                handle vbr audio [autodetect]
	 -f FILE             read AVI comments from FILE [off]
	 -v                  print version

```

---

### Post by needhelppeeps on 2010-01-14
Mencoder did  not work for me. I used cat to join the avi files. I also found I could cat the files, and use divfx++ to correct them if parts were missing somewhere in the middle

---

### Post by ubuntak2 on 2010-01-24
> **vanadium said:**
> cat is perfectly fine for joining files that have been split binary:

cat name.avi.* > myfinalmovie.avi

will do the job.

However, this applies only if an avi file was binary split into pieces (that you cannot play indepedently). If you are looking to join individual functional avi's, then you need avimerge or avidemux (graphical utility very similar to virtualdub).

This works for me very well, no need to reboot into windows to join these any more. Thanks for the info.
Linux rules

---

### Post by dollzii on 2010-01-24
I use lxsplit, always worked great for me.

[http://lxsplit.sourceforge.net/](http://lxsplit.sourceforge.net/)

lxsplit -j *.avi.001

---

### Post by Pol18 on 2010-01-25
Hi,

As I understand the command "cat name.avi.* > myfinalmovie.avi" does the same thing as
"lxsplit -j *.avi.001" command. Am I right ?

Thanks,
Pol

---

### Post by dollzii on 2010-01-26
I guess so, never used cat for joining files. 

Quote from lxsplit.sourceforge.net:

lxSplit is a simple tool for splitting files and joining the splitted files on unix-like platforms, such as Linux, FreeBSD, OpenBSD, etc. It is fully compatible with the HJSplit utility which is available for other operating systems. Splitting is done without compression.

Mark as solved?

---

### Post by ravi_pr5 on 2010-05-07
cat *.avi* > final.avi works for me ..

---

### Post by MrWES on 2010-05-07
> **Pol18 said:**
> Hi,

As I understand the command "cat name.avi.* > myfinalmovie.avi" does the same thing as
"lxsplit -j *.avi.001" command. Am I right ?

Thanks,
Pol

avimerge and avisplit, which are part of the transcode package. From the terminal:

```
sudo apt-get install transcode
```

Or use the Synaptic Package Manager System > Admin

Bill

---

### Post by fendijr on 2011-08-08
> **MrWES said:**
> avimerge and avisplit, which are part of the transcode package. From the terminal:

```
sudo apt-get install transcode
```

Or use the Synaptic Package Manager System > Admin

Bill


success to install, but what & where are the things???
-newbie-

---

