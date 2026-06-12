---
title: "how can I compile a standalone binary that doesn't need shared libs?"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by petermg on 2014-03-06
I'm trying to compile the latest version of minidlna 
[http://sourceforge.net/projects/minidlna/files/minidlna/1.1.1/](http://sourceforge.net/projects/minidlna/files/minidlna/1.1.1/)
and I have been trying for days to figure out how to make it so that it doesn't need to load shared libaries.  I tried using ./configure --enable-static but I guess that doesn't create a standalone binary.  Thought they were also called static binaries.  I've read about editing Makefiles, and I read someone needed to hardcode something into his older version to get it to work.  Basically I'm trying to run it on a platform that I don't have RW access to the shared libs dir.  This is what I get when I try to run it:
```
./minidlnad: error while loading shared libraries: libavutil.so.49: cannot open shared object file: No such file or directory
```
that's why I'm trying to make it look in a relative directory for the libs it needs.  Sorry I'm a super noob when it comes to this stuff.

---

### Post by TheFu on 2014-03-06
Compiling for static libs is hard if that is NOT the default for a build.  Why not just change the LD_LIBRARY_PATH and use the shared libs? It is fine to do this for 1 program for everybody, for 1 userid, for every program, for a userid or group or for the entire OS.

I'd build the app and keep it in a self-contained area under my HOME ... 
minidlna with subdirs
/bin/
/lib/
/contrib/
/etc/

BTW, if you like miniDLNA, you might like plex. Plex isn't F/LOSS, but  it is the best DLNA server that I've found.

---

### Post by petermg on 2014-03-06
> **TheFu said:**
> Compiling for static libs is hard.  Why not just change the LD_LIBRARY_PATH and use the shared libs?
It is find to do this for 1 program for 1 userid, every program for a userid or group or the entire OS.

I'd build the app and keep it in a self-contained area under my HOME ... 
minidlna with subdirs
/bin/
/lib/
/contrib/
/etc/

BTW, if you like miniDLNA, you might like plex. Plex isn't F/LOSS, but  it is the best DLNA server that I've found.

Ok how can I do it using LD_LIBRARY_PATH?  Is that a field in the Makefile?  Does that allow me to point it to recursive/relative directories such as /lib/, /bin/, etc. as you wrote?  Thanks for replying to me.

---

### Post by TheFu on 2014-03-06
No. The LD_LIBRARY_PATH is a runtime control. There is one already set and if no, the system default is used. It is very similar in use as the PATH - just for locating libraries.

So - get the source from the minidlna place again, compile it using shared libraries (or whatever their default is) and you can run minidlna it by setting an LD_LIBRARY_PATH like this:

```
#!/bin/sh
MDLNA_HOME=/home/myuser/minidlna
export LD_LIBRARY_PATH=$MDLNA_HOME/lib:$LD_LIBRARY_PATH
$MDLNA_HOME/bin/minidlna .... *plus any options it needs*

```
Very easy.  Works for any programs you need different library paths for on any UNIX-like OS ... well, AIX uses LIBPATH, but you get the idea. SunOS, Solaris, Linux all use LD_LIBRARY_PATH.

---

### Post by petermg on 2014-03-06
> **TheFu said:**
> No. The LD_LIBRARY_PATH is a runtime control. There is one already set and if no, the system default is used. It is very similar in use as the PATH - just for locating libraries.

So - get the source from the minidlna place again, compile it using shared libraries (or whatever their default is) and you can run minidlna it by setting an LD_LIBRARY_PATH like this:

```
#!/bin/sh
MDLNA_HOME=/home/myuser/minidlna
export LD_LIBRARY_PATH=$MDLNA_HOME/lib:$LD_LIBRARY_PATH
$MDLNA_HOME/bin/minidlna .... *plus any options it needs*

```
Very easy.  Works for any programs you need different library paths for on any UNIX-like OS ... well, AIX uses LIBPATH, but you get the idea. SunOS, Solaris, Linux all use LD_LIBRARY_PATH.

Thank you.  Now I just put that into a script right, after tailoring it to my dirs and options?  Make like a minidlna.sh file or something? After making it executable and whatnot?

---

### Post by petermg on 2014-03-06
> **petermg said:**
> Ok how can I do it using LD_LIBRARY_PATH?  Is that a field in the Makefile?  Does that allow me to point it to recursive/relative directories such as /lib/, /bin/, etc. as you wrote?  Thanks for replying to me.

How much resources does Plex use in comparison to miniDLNA?  Basically I'm going with miniDLNA because of it's minimal resource usage.

---

### Post by petermg on 2014-03-06
> **TheFu said:**
> No. The LD_LIBRARY_PATH is a runtime control. There is one already set and if no, the system default is used. It is very similar in use as the PATH - just for locating libraries.

So - get the source from the minidlna place again, compile it using shared libraries (or whatever their default is) and you can run minidlna it by setting an LD_LIBRARY_PATH like this:

```
#!/bin/sh
MDLNA_HOME=/home/myuser/minidlna
export LD_LIBRARY_PATH=$MDLNA_HOME/lib:$LD_LIBRARY_PATH
$MDLNA_HOME/bin/minidlna .... *plus any options it needs*

```
Very easy.  Works for any programs you need different library paths for on any UNIX-like OS ... well, AIX uses LIBPATH, but you get the idea. SunOS, Solaris, Linux all use LD_LIBRARY_PATH.

I'm getting the following error:
```
Trace/breakpoint trap
```
When I try to run this script:
```
#!/bin/sh
MDLNA_HOME=/tmp/mnt/34AC20EBAC20A8F6/minidlna
export LD_LIBRARY_PATH=$MDLNA_HOME/usr/lib:$LD_LIBRARY_PATH
$MDLNA_HOME/bin/minidlnad -V

```

---

### Post by TheFu on 2014-03-06
I looked at minidlna many years ago.  At the time, it needed to be forced manually to update the content DB. I found it to be always out of date and frustrating. Haven't looked at it recently. 

Used NFS and CIFS remote storage to access media on the network here. Had just 1 DLNA device until Xmas '13, so that was really the best way to access media. It was a WDTV-Live HD.

For the last 2 yrs, been running XBMC on a $100 PC (AMD E-350 APU) happily. It handles 1080p down to very low resolution stuff in the media library. It also doesn't have many limitations about video/audio codec support - it will play pretty much anything, unlike most specialized, cheaper, devices.

Plex is new to me as well.  Only had it about a month.  Wish I would have switched last year. I still use XBMC for playback, but Plex for organization and streaming to pretty much any device in the house. It is always up-to-date about the content. Things deleted are automatically removed, things added show up in a few minutes.  Even have it streaming local media to a Chromecast.

Plex resource use is tiny, unless you ask it to transcode on-the-fly for an odd device. For example, most of my videos are TV recordings with AC3 5.1 audio.  The chromecast doesn't play AC3-anything, so the audio needs to be converted to AAC.  The E-350 APU just doesn't have enough power for that in real-time streaming. It handles HiDef playback thanks to a built-in Radeon GPU handling h.264 and mpeg2 content in hardware. SD content of any sort is handled in software easily. It is connected to a projector with a 90inch screen and THX receiver for surround audio.  XMBC does the playback on the same machine. It isn't perfect, but it is amazing.

So, I cannot provide a comparison, beyond saying that plex server feels light. It is just a catalog after all - not a player.

If you have Android devices, install BubbleUPnP and connect it to your DLNA devices AND to plex server. That app will let you control what media plays where anything in the house.

---

### Post by TheFu on 2014-03-07
Don't run programs from non-Linux file systems.  That means use EXT2/3/4 or similar file systems - NOT FAT, NTFS.

---

### Post by petermg on 2014-03-07
> **TheFu said:**
> Don't run programs from non-Linux file systems.  That means use EXT2/3/4 or similar file systems - NOT FAT, NTFS.

Ok that's probably my problem.  And thanks for the info on the Plex media server.  I am actually compiling the miniDLNA app for my WDTV LIVE PLUS, with custom firmware aka WDLXTV firmware.  I am able to compile from the info here:
[http://forum.wdlxtv.com/viewtopic.php?f=43&t=494](http://forum.wdlxtv.com/viewtopic.php?f=43&t=494)
and run it fine in the debian image but when I create an app.bin it asks for the lib mentioned earlier.  However I'll create an app.bin with that script and see how it works.  I was just running from a non linux file system when I got that error I mentioned before.  I'll have to see if Plex is something I can compile and run on this thing.

---

### Post by petermg on 2014-03-07
> **TheFu said:**
> Don't run programs from non-Linux file systems.  That means use EXT2/3/4 or similar file systems - NOT FAT, NTFS.

Turns out I was still getting
```
Trace/breakpoint trap
```
until I removed redundant libraries that were already picked up on the system.  I didn't realize that LD_LIBRARY_PATH was like adding a path, I thought it was making it the only path for it's libs that's why I put ALL of it's required libs as listed by ldd in the it's relative usr/lib folder.  After I removed the redundant libs, my script worked.  I just make it output the version number with the -V option just for testing.  Now to see if I can get it to start up automatically and via the webend for the wdlxtv.... there is a startup script in it's relative etc/init.d folder and I'm thinking maybe I can just add LD_LIBRARY_PATH somewhere in there? ?

---

### Post by TheFu on 2014-03-07
I have a WDTV Live HD (non-Plus version).  Found the DLNA uses of it to be lacking. I hope it works better for you.  Having filetypes that it sometimes played and others that it refused to play just got too frustrating.  Doesn't that firmware support NFS?  You can mount /opt from a different machine with standard UNIX permissions and run code from it.

So - let me understand - you are cross compiling code to run ON the WDTV Live?  I have some experience with cross-compiling - did it for a living for about 8 yrs. Did compilations on normal machines to run on other, limited machines.

I've never bothered to load WDLXTV firmware. Too many other x86 systems around here to bother.  I did use it as a slow NAS for a few weeks. The 100base-tx bandwidth was just too slow. [http://blog.jdpfu.com/2011/02/10/very-cheap-nas-wd-tv-hd-live](http://blog.jdpfu.com/2011/02/10/very-cheap-nas-wd-tv-hd-live)

Plex won't work on non-Linux file systems either.  You can format that USB flash drive with EXT2/3/4 and use it. Just sayin'.  Plex won't run on the WDTV ... that would be a client. They don't source releases, which is a huge negative, but the ability to stream and transcode to almost any other DLNA device makes up for that.

---

### Post by TheFu on 2014-03-07
LD_LIBRARY_PATH shouldn't have anything to do with your compilation. I hope you didn't change it for that - it is just for running the resulting program.  

Compilation would depend on the way you specify -l in the link parts of the Makefile.  If you use shorthand, can be dangerous, but if you specify the exact path to the library you want, then it will use that library.  Order of the LD_LIBRARY_PATH matters - also, it wuold be best if there weren't any duplicate directories inside it --- it should only contain directories. Never said that before, but it works like PATH owrks on every OS - just directories, not complete filenames.

---

### Post by petermg on 2014-03-07
> **TheFu said:**
> I have a WDTV Live HD (non-Plus version).  Found the DLNA uses of it to be lacking. I hope it works better for you.  Having filetypes that it sometimes played and others that it refused to play just got too frustrating.  Doesn't that firmware support NFS?  You can mount /opt from a different machine with standard UNIX permissions and run code from it.

So - let me understand - you are cross compiling code to run ON the WDTV Live?  I have some experience with cross-compiling - did it for a living for about 8 yrs. Did compilations on normal machines to run on other, limited machines.

I've never bothered to load WDLXTV firmware. Too many other x86 systems around here to bother.  I did use it as a slow NAS for a few weeks. The 100base-tx bandwidth was just too slow. [http://blog.jdpfu.com/2011/02/10/very-cheap-nas-wd-tv-hd-live](http://blog.jdpfu.com/2011/02/10/very-cheap-nas-wd-tv-hd-live)

Plex won't work on non-Linux file systems either.  You can format that USB flash drive with EXT2/3/4 and use it. Just sayin'.  Plex won't run on the WDTV ... that would be a client. They don't source releases, which is a huge negative, but the ability to stream and transcode to almost any other DLNA device makes up for that.

I am actually connected directly to the WDTV LIVE PLUS via SSH and/or Telnet and then mount the downloaded debian squeeze image to do my compiling.
[http://forum.wdlxtv.com/viewtopic.php?f=43&t=494](http://forum.wdlxtv.com/viewtopic.php?f=43&t=494)
so no need to cross compile ;)
works great but some apps, minidlna for example, will run fine from the debian image file system but when trying to run directly off the wdtv live plus, asks for certain libs.  Now because I'm using a custom firmware FLASHED to the WDTV LIVE PLUS, I cannot just place the missing libs in the libs folder, I WOULD be able to do this if I used the NON-FLASH EXT3 version of the custom firmware, but I was hoping to make this an app.bin that I could redistribute on the forum.  I have a couple tablets and a newer Gen3 WDTV LIVE PLUS SMP that I also use.  I was originally using my Windows 7 built-in media server for streaming my content, but it has problems seeing some files and sometimes just NOT updating at all.  Then I was using PS3 media server and that works GREAT!!! But then I started playing with an older minidlna someone made for the WDTV LIVE PLUS and I liked it and so I started thinking maybe it would be cool to put all my media collection on my 1TB USB drive and simply share THAT off the WDTV LIVE PLUS using miniDLNA instead of serving everything off my PC.  Plus I am already serving SOME media off my WDTV LIVE PLUS using miniDLNA that's on the 32GB thumb drive that's in there.  The WDTV LIVE PLUS plays files that my older WDTV box didn't play.  So far I can't think of any files I have that it will not play, but I can't say I'm informed as to what's the limitations it has in that regard.  Right now I modified the startup script someone wrote with the older minidlna version and I just added that (defined) variable of "MDLNA_HOME=" and "export LD_LIBRARY_PATH=$MDLNA_HOME/usr/lib:$LD_LIBRARY_PATH" into the beginning of the startup script that was already there. Then I think I also prefixed "$MDLNA_HOME/bin/" to any mention the script had of running the binary, which actually I think was in just one area.  Now it runs from the webend just fine since the webend uses that script to start it.  :D  so THANK YOU!!  The person who put the older version of minidlna for the WDTV LIVE PLUS together somehow hardcoded something into it to fix the issue it was having with a missing lib.  I read his post somewhere but I can't find it again for the life of me.  So with HIS version you could ssh in and run minidlna from the command line, for example:
```
./minidlna -V
```
would tell you the version.  But now you can't do that because it will error out because of a missing lib.  No biggie.  Most people using the webend/gui aren't interested in running something from the command line.  Also you can modify the config file from the web gui for the WDLXTV (modified firmware for the WDTV LIVE PLUS) and the start up script passes that config along to the binary so in a nutshell it's working :D  Thanks again!!!!!  :KS:KS:D:D:popcorn:

---

### Post by petermg on 2014-03-07
Also as far as the speed of the device, here is a very interesting article of speed testing with different protocols on it you may find interesting.  
[http://wdtvforum.com/main/index.php?topic=5393.0](http://wdtvforum.com/main/index.php?topic=5393.0)

---

### Post by petermg on 2014-03-07
and now I see that just 20 hours ago a NEWER version of minidlna was released..  time to compile again ;)

---

