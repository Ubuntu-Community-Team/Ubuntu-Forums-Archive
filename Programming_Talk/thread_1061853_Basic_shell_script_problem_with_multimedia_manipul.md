---
title: "Basic shell script problem with multimedia manipulation"
date: 2009-02-06
forum: Programming Talk
---

### Post by szczym on 2009-02-06
helo

Im multimedia artist on daily basis, please excuse me my basic problems. Im building dedicated box for encoding and publishing of video material for my community. 

Big video files (~ 1-5 gb) will come into folder shared via samba. 

What i want the script to do:
1 After founding the file, move it to "encoding" folder 
2 Encode source into theora
3 Move output into seeding directory 
4 Generate torrent out of output
5 Send torrent to remote ftp location 
6 Encode input into .flv
7 Copy output.flv into remote location
8 Encode input into .mp4 ipod format 
9 Copy output.mp4 into remote location 
10 Done/wait for next job

Yesterday a college wrote me a shell script for doing the torrent stuff, it looks like that:
```

#!/bin/sh
# encode videos from incoming and create torrent
# to share the torrent run something like btlaunchmany on $seeding or use the scandir feature available in many torrent clients
incoming=/home/szczym/encode/auto/incoming
encoding=/home/szczym/encode/auto/encoding
seeding=/home/szczym/encode/auto/seeding
f2t_params="-p videobin"

while [ 1 ]; do
  for i in `ls $incoming/*`; do
    mv $i $encoding
    ffmpeg2theora $encoding/`basename $i` -o $seeding/`basename $i`.ogv $f2t_params && \
    btmakemetafile http://tpb.tracker.thepiratebay.org/announce $seeding/`basename $i`.ogv
  done
  sleep 900 # wait for 15 minutes
done
```

So that script do what i need very well, now im extending it for static files and ftp. I have following questions to You:

1. How to turn on seeing of commands, that are beeing inserted by script? When i run it, i see only output of commands, cant actually spot a problem 
2.How to reliably upload output to ftp via shell ? 
3 How to log output into a file and send summary via email ?

Thanx for any help !

---

### Post by lensman3 on 2009-02-06
>>1. How to turn on seeing of commands, that are beeing inserted by script? 
>>When i run it, i see only output of commands, cant actually spot a problem

Add to the first line (#!/bin/sh) -xv so that the first line looks like #!/bin/sh -xv


>>3 How to log output into a file and send summary via email?

Redirect the out put of the shell.  So when you run your script:

./script >output_file.

or
./script | mail [email]xxx@at.xxx[/email]

will mail it to you.  If you want to see the commands as they execute then

./script | tee | mail [email]xxx@at.xxx[/email]

The mail program "mail" will probably only work in your immediate network because it will try and connect across the Internet using port 25 which is often blocked or you IP range will be on a blacklist.

---

### Post by ghostdog74 on 2009-02-06
> **szczym said:**
> 
...
  for i in `ls $incoming/*`; do
    mv $i $encoding
 ...[/CODE]

you are going to encounter problems later if your files contains spaces. And stop using "ls" like that in a for loop. Its called useless use of "ls". Use bash's shell expansion
```

for i in $incoming/*
do
  mv "$i" "$encoding"
...
done

```
always make it a habit to quote your variables.

---

### Post by szczym on 2009-02-07
thanx a lot for help, i have included your changes and it works ok. 

But after some tests, i will tray different approach: turnkeylinux@virtualbox + Torrentflux-b4rt  + drupal+media mover, since any way it will publish stuff to podcast site bult on drupal 

[http://www.turnkeylinux.org/appliances/lamp](http://www.turnkeylinux.org/appliances/lamp)
[http://tf-b4rt.berlios.de/](http://tf-b4rt.berlios.de/)
[http://drupal.org/project/media_mover](http://drupal.org/project/media_mover)

if some one is interested in results, please PM me

---

### Post by geirha on 2009-02-07
I do spot another flaw, which is: What if your script runs right after an upload has started?

Say the file is 1GiB, and when your script runs, 1MiB has been copied so far. 1GiB will not be uploaded instantly, it will take time no matter how fast your harddrives and network are.

So:

1. Your script will first move the file to a different location. If the location is on the same filesystem, that will work just fine; the file will just have a new link and samba will continue to add data to the file as if nothing happened. If it's on a different filesystem, the move will probably result in a partial file unless the mv command runs slower than the upload.

2. Let's say the move is on the same filesystem, then ffmpeg2theora wil be started on an uncomplete file. If the upload is faster than ffmpeg2theora, this will most likely work out just fine, ffmpeg2theora eventually processing the entire file. But if for some reason the upload is slowed considerably, ffmpeg2theora may reach the end of the file before the upload is completed.

I think you should take that scenario into consideration. Perhaps by uploading an empty file, after the media file is complete, with the same name as the media file, but with the added extension ".complete" or something along those lines. Then have your script only process files which has a corresponding .complete-file.

---

