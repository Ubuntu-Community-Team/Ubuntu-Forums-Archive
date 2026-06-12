---
title: "Error with PSPVC"
date: 2012-12-14
forum: New to Ubuntu
---

### Post by tarfil on 2012-12-14
Hello! I´m noob in Linux and i´m trying to install PSPVC.
I decompressed the packet containing the PSPVC file at [http://pspvc.sourceforge.net/](http://pspvc.sourceforge.net/) . and when i execute the install.sh script i got this message: 
 
ERROR: x264 not found
If you think configure made a mistake, make sure you are using the latest
version from SVN. If the latest version fails, report the problem to the
[EMAIL="ffmpeg-devel@mplayerhq.hu"]ffmpeg-devel@mplayerhq.hu[/EMAIL] mailing list or IRC #ffmpeg on [irc.freenode.net]("http://irc.freenode.net/").
Include the log file "config.err" produced by configure as this will help
solving the problem.
-e \E[01;31mERROR during configure FFMPEG
 
I installed all the libraries that the packet must use: 
nasm
libfaac
libxvidcore
liba52
gtk+2.0
 
 
But nasm is deprecated, I installed Yasm.
I tried to install x264 and reexecute the install.sh script. But the problem persists.
How do i proceed?
 
Thank you very much for your hel :)

---

