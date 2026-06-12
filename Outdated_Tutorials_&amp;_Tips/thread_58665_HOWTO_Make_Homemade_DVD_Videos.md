---
title: "HOWTO: Make Homemade DVD Videos"
date: 2005-08-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Tralobyte on 2005-08-21
This HOWTO will enable you how to turn one or more movie files into a DVD video with a basic menu.

Now to get everything we need for the programs LiVES and DVDStyler:
```
#Get MPlayer:
sudo apt-get install mplayer-nogui
sudo apt-get install w32codecs
#Get LiVES requirements:
sudo apt-get install sox
#Get dvdauthor:
sudo apt-get install dvdauthor
#Get DVDStyler requirements:
sudo apt-get install gcc
sudo apt-get install g++
sudo apt-get install libwxgtk2.5-dev
sudo apt-get install mjpegtools
sudo apt-get install netpbm
sudo apt-get install mpgtx
sudo apt-get install libjpeg62-dev
sudo apt-get install checkinstall
#Get Xine for previewing the DVD (this is useful but not necessary):
sudo apt-get install xine-ui
```
We create a temporary directory for all the programs we need to download. (Thanks to Vaego for the temp directory idea.)
```
mkdir temp
cd temp
```
Get libvisual for LiVES:
```
wget sentinel.dk/debian/dists/unstable/main/binary-i386/libs/libvisual0_0.2.0-1_i386.deb
sudo dpkg -i libvisual0_0.2.0-1_i386.deb
```
Get LiVES:
```
wget http://sentinel.dk/linux/debian/packages/lives/lives_0.9.5-pre3-1_i386.deb
sudo dpkg -i lives_0.9.5-pre3-1_i386.deb
```
Get DVDStyler:
Go to [http://prdownloads.sourceforge.net/dvdstyler/DVDStyler-1.4.tar.gz?download](http://prdownloads.sourceforge.net/dvdstyler/DVDStyler-1.4.tar.gz?download) and save it to our temp directory.
```
tar xzvf DVDStyler-1.4.tar.gz
cd DVDStyler-1.4
./configure
make #get a coffee
sudo checkinstall -D
```
When it shows the ">>," just hit Enter. At "Enter a number to change any of them or press ENTER to continue:", enter in 2, then hit Enter to edit the name. Type in "dvdstyler" and hit Enter again. Press Enter one last time to finish the install.

To remove our temporary directory:
```
cd ../..
rm -rf temp
```
Configure LiVES:
To open up LiVES, type "lives" at a command line. Go to Tools->Preferences->Encoding. In the Encoder dropdown box, select mjpegtools_encoder. Hit Ok. Whenever you want to convert a movie file to an mpeg that DVDStyler can read properly, open it in LiVES by using  File->Open File/Directory and then save it with File->Save As. Depending on how big your video is, opening and save can take quite some time. Make sure to save the file with a .mpg extension. I tested the conversion with a .wmv at 30fps.

Make and Burn the DVD with DVDStyler:
To open DVDStyler, type "dvdstyler" at a command line. The interface is intuitive.

---

### Post by matthew on 2005-08-21
Wow. Nice howto, and it's your first post! I'm on my way to bed, but I'm looking forward to trying this out. Thanks and welcome!!

---

### Post by James_Black on 2005-08-21
Very cool howto indeed! Haven't tried it yet, but is it also possible to add subtitles?

---

### Post by Tralobyte on 2005-08-21
Thanks for the feedback!

> Haven't tried it yet, but is it also possible to add subtitles?
According to [this thread](http://sourceforge.net/forum/forum.php?thread_id=1287327&forum_id=318795), they're working on subtitle support for DVDStyler, but you can use [spumux](http://dvdauthor.sourceforge.net/doc/spumux.html) for now. Spumux is a command line utility which comes with the dvdauthor package and adds subtitles onto mpegs. dvdauthor is required by DVDStyler, so if you followed the HOWTO, you already have spumux.

Alternatively, you can try out Cinelerra, which I'm pretty sure has GUI subtitle support, or tovid, which Spago pointed out has command line subtitle support.

---

### Post by sapo on 2005-08-21
You people should try tovid:

[http://tovid.sourceforge.net](http://tovid.sourceforge.net)

it makes the menu, add subtitles, and everything without using comand line.. it uses mplayer and ffmpeg and transcode...

i use it a lot  :grin:

---

### Post by Tralobyte on 2005-08-21
Jure Cuhalev has Ubuntu packages of Cinelerra at [http://www.kiberpipa.org/~gandalf/ubuntu/](http://www.kiberpipa.org/~gandalf/ubuntu/). I'll test them out as soon as I can.

[QUOTE=sapo][tovid] makes the menu, add subtitles, and everything without using comand line.. it uses mplayer and ffmpeg and transcode...[/QUOTE]
Please correct me if I'm wrong, but tovid does not have subtitle support, yet. tovid is a nice program, but DVDStyler feels more intuitive. If someone can get something working in tovid that won't work in DVDStyler, I'll be glad to append the HOWTO for those interested in tovid.

Update: The packages for Cinelerra seem have a dependency issue with libgcc1, and the source seems to depend on XFree86 instead of xorg. Anyone know a workaround?

Update 2: Running alien on the rpm from the site, and then running dpkg -i on the deb installs Cinelerra, but either I'm not using it correctly or it doesn't seem to work right.

---

### Post by sapo on 2005-08-24
[QUOTE=Tralobyte]Jure Cuhalev has Ubuntu packages of Cinelerra at [http://www.kiberpipa.org/~gandalf/ubuntu/](http://www.kiberpipa.org/~gandalf/ubuntu/). I'll test them out as soon as I can.


Please correct me if I'm wrong, but tovid does not have subtitle support, yet. tovid is a nice program, but DVDStyler feels more intuitive. If someone can get something working in tovid that won't work in DVDStyler, I'll be glad to append the HOWTO for those interested in tovid.

Update: The packages for Cinelerra seem have a dependency issue with libgcc1, and the source seems to depend on XFree86 instead of xorg. Anyone know a workaround?[/QUOTE]

tovid HAS subtitle support.. but it isnt in the gui..

if you copy and past the commands that the gui show you and add: 

tovid -subtitles file.srt

it will encode the subtitles in the movie..

btw.. i just mentioned tovid cause i really use it.. theres no problem in your howto btw i think that instead of "should" try maybe i would say "could" try...

---

### Post by Tralobyte on 2005-08-24
[QUOTE=sapo]tovid HAS subtitle support.. but it isnt in the gui..[/QUOTE]
Ah, my mistake. I saw "Capability to add subtitles (as a subtitle stream) to videos." in the Future plans section of their site [here](http://tovid.sourceforge.net/ch03.html), which it turns out is the GUI part only. I also didn't see it in the GUI when I looked at the program, so I jumped to the wrong conclusion. Thanks.

---

### Post by Tralobyte on 2005-08-24
[QUOTE=sapo]tovid HAS subtitle support.. but it isnt in the gui..[/QUOTE]
Ah, my mistake. I saw "Capability to add subtitles (as a subtitle stream) to videos." in the Future plans section of their site [here](http://tovid.sourceforge.net/ch03.html), which it turns out is the GUI part only. I also didn't see it in the GUI when I looked at the program, so I jumped to the wrong conclusion. Admittedly, I was a bit thrown off by "it makes the menu, add subtitles, and everything without using comand line." ;) Thanks for the update.

P.S. Changed "should" to "can" and added tovid as an alternative in the post.

---

### Post by buildid on 2005-08-24
avidemux2 can create :

vcd
svcd
dvd
ksvcd
kdvd
and probally more ..........

with or without subtitles 

this peace of software is 0ke , i use it now for 3 years ,...

creating mpg fies (dvdcompatible with an end size of 1400 or 1500 mb ) you can create a dvd.iso with dvdstyler .you end up with a kdvd and 3 movies .

quality is good ..not as good as dvd afcourse but better as files converted with any windows tool ...

---

### Post by darkjedi8359 on 2005-08-25
I am definatly going to give this a try! :)  

Is it ok to use larger files than it says it is optimized for? I am going to try and see how it goes :P

---

### Post by Statik on 2005-10-12
Well, it seems to install fine, and previews work. However, I can't seem to load the file in. It takes forever. Video seems fine, it's the audio that seems to catch it up. Any ideas? I'm lost with it.

Statik

---

### Post by reet on 2005-10-13
I find LiVES to be too complicated for simply converting a file to DVD format. So what I do is use mplayer at the command line to convert the file, then DVDStyler to create the DVD structure and menus. Works like a charm. I found all the information on how to use mencoder to create a DVD suitable mpeg file on a gentoo website that I can't remember where so I'll just post it here:

mencoder movie.avi -of mpeg -vf scale=720:480,harddup -oac lavc -ovc lavc -lavcopts acodec=ac3:abitrate=192:vcodec=mpeg2video:keyint=25:vbitrate=5000:aspect=16/9 -mpegopts format=dvd -srate 48000 -ofps 30000/1001 -o movie.mpg

# -of means use mpeg file format (instead of avi)
# -vf scale=720:480 means use 720x480 which is NTSC resolution
#     harddup should be used with mencoder
#     use expand=w:h for movies that aren't 4:3 or 16:9
# -oac lavc means use libavcodec for encoding the audio (see lavcopts)
# -ovc lavc means use libavcodec for encoding the video (see lavcopts)
# -lavcopts are the options for libavcodec
#   acodec=ac3 is the audio codec used in DVD's
#   abitrate=192 is the standard bitrate for stereo AC3
#   vcodec=mpeg2video is the MPEG 2 video that DVD's support
#   keyint=25 is necessary for DVD
#   vbitrate=5000 you can adjust this for filesize as necessary
#   aspect=16/9 this should be 16/9 or 4/3 depending on your content
# -mpegopts format=dvd means to use dvd compatible mpeg
# -srate 48000 is an audio sampling rate of 48000Hz which is standard for DVD's
# -ofps 30000/1001 is the framerate (29.97) to be used for NTSC
# -o movie.mpg specifies that the output file should be movie.mpg

If your movie is theatre widescreen 2.35:1 or whatever the ratio is, you need to do some math. You need to convert the resolution to 16:9 aspect ratio. For example if your input video is 640x272, then in 16:9 format it would be 640x360. Now you modify the video filter command to look like this:

-vf expand 640:360,scale=720:480,harddup

That will add the black bars on the top and bottom so the movie isn't stretched out of proportion. Maybe just changing the aspect parameter will work as well but I haven't tried it. Feel free to experiment.

So now after that is done run DVDStyler and away you go.

---

### Post by Statik on 2005-10-13
Well, it looked good until I tried it. Then I get this:
```
statik@ubuntu:~$ mencoder movie.avi -of mpeg -vf scale=720:480,harddup -oac lavc -ovc lavc -lavcopts acodec=ac3:abitrate=192:vcodec=mpeg2video:keyint=25:vbitrate=5000:aspect=16/9 -mpegopts format=dvd -srate 48000 -ofps 30000/1001 -o movie.mpg
MEncoder 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Advanced Micro Devices Athlon MP/XP/XP-M Barton (Family: 6, Stepping: 0)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags: Type: 6 MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE

File not found: 'frameno.avi'
Failed to open frameno.avi
mpegopts is not an MEncoder option

Exiting... (error parsing cmdline)
```

looks like I have something not quite right. Not sure what tho. Any ideas?

Statik

---

### Post by reet on 2005-10-17
I'm not completely sure that this will fix your problem, but I think that mencoder may need a upgrade to the latest version. Your version is copyright 2004.

I have recently upgraded to 5.10, and the version I have is dev-CVS--4.0.2

Upgrading mencoder should give you the latest "lavc" which would have the mpeg2video codec and should not give you the "mpegopts" problem.

---

### Post by Statik on 2005-10-17
I just did the upgrade to 5.10 aswell, so I retested the script. Looks like it's working fine. I'll let it run and see how it does.

Statik

---

### Post by reet on 2005-10-21
[QUOTE=buildid]avidemux2 can create :

vcd
svcd
dvd
ksvcd
kdvd
and probally more ..........

with or without subtitles 

this peace of software is 0ke , i use it now for 3 years ,...

creating mpg fies (dvdcompatible with an end size of 1400 or 1500 mb ) you can create a dvd.iso with dvdstyler .you end up with a kdvd and 3 movies .

quality is good ..not as good as dvd afcourse but better as files converted with any windows tool ...[/QUOTE]

I have recently installed avidemux to try and make a dvd with subtitles. Could you maybe post the settings you use to create a working mpeg file? I tried myself, but the mpeg file caused DVDStyler to crash when I hit the burn button :(

Thanks.

---

### Post by glug101 on 2005-10-22
One small problem with the DVDStyler program.... 

The interface is nice, I was able to quickly create a menu for my dvd and point the buttons to mpeg streams.  However, when I tell it to burn the dvd, or even create the iso file, it crashes.  No error message, no output to the command line, just gone.  Poof.  Bye bye!  :( Now I have to do it all by hand in order to troubleshoot.  (If I wanted error messages that didn't mean anything I would just install windoze:) )

Remembering my Gentoo days, I found this how to on their forums.  It's a bit dated (about two years old) but it's VERY complete and I think that all the packages are installable through Synaptic.

[http://forums.gentoo.org/viewtopic.php?t=117709](http://forums.gentoo.org/viewtopic.php?t=117709)

---

### Post by bored2k on 2005-10-22
To those using avidemux: I have made an avidemux 2.1_branch1 package using SVN. The avidemux creator is urging everyone to use the SVN instead of the old unstable package. I compiled this one for support with pretty much everything. It's a LOT better than the stable avidemux 2.0.42.

[http://rapidshare.de/files/6630821/avidemux_2.1_branch-1_i386.deb.html](http://rapidshare.de/files/6630821/avidemux_2.1_branch-1_i386.deb.html)

---

### Post by reet on 2005-10-22
Thanks for that. I am no expert at compiling my own packages, but I needed to install the "libsmjs1" package in order to get that to work. Maybe there is something that can be done when the package is compiled to add "libsmjs1" to the dependancies.

Also, disregard my previous post about DVDStyler crashing, it appears to be something wrong with the software since I've upgraded to 5.10. I'll have to look into the problem more closely to see if I can fix it.

---

### Post by Statik on 2005-10-23
I too ended up with seg faults after upgrading. However, I cannot seem to roll it back to any other version either. I've resorted to using tovid, which seems to work very nicely. The GUI for tovid hasn't worked properly yet, I get lockups, but the command line is great.

Statik

---

### Post by reet on 2005-10-27
Okay with a small bit of searching I found that mjpegtools is the cause of DVDStyler crashing on Ubuntu 5.10. I've downgraded *mjpegtools* and *libmjpegtools0* to 1.6.2-09 and it's working good now.

I am using the 1.4 Debian package from the DVDStyler website. I did not compile the program myself.

---

### Post by bored2k on 2005-10-28
Well I just compiled DVDStyler on Breezy and using the latest wxgtk (2.6-0) and it looks good and works wonders. You all can get the package here:
[CENTER]
[http://rapidshare.de/files/6859079/dvdstyler-1.4_1.4-1_i386.deb.html](http://rapidshare.de/files/6859079/dvdstyler-1.4_1.4-1_i386.deb.html)

[[IMG]http://img465.imageshack.us/img465/427/screenshotdvdstyleruntitled5rp.th.png[/IMG]](http://img465.imageshack.us/my.php?image=screenshotdvdstyleruntitled5rp.png)[/CENTER]

---

### Post by reet on 2005-10-28
Cool, you didn't have to downgrade mjpegtools? Will it work on my Athlon processor or is it Intel only like your mplayer package?

---

### Post by bored2k on 2005-11-01
You could try but I'm not sure it'll work. And no, I didn't downgrade anything.

---

### Post by wackhacker on 2005-11-23
[QUOTE=Tralobyte]This HOWTO will enable you how to turn one or more movie files into a DVD video with a basic menu. [/QUOTE]

Is it possible to provide a new repository- post with the places where the mentioned packages for 5.10 can be downloaded?

Thanks in advance!

---

### Post by jnie on 2005-12-07
[QUOTE=bored2k]Well I just compiled DVDStyler on Breezy and using the latest wxgtk (2.6-0) and it looks good and works wonders. You all can get the package here:
[CENTER]
[http://rapidshare.de/files/6859079/dvdstyler-1.4_1.4-1_i386.deb.html](http://rapidshare.de/files/6859079/dvdstyler-1.4_1.4-1_i386.deb.html)

[[IMG]http://img465.imageshack.us/img465/427/screenshotdvdstyleruntitled5rp.th.png[/IMG]](http://img465.imageshack.us/my.php?image=screenshotdvdstyleruntitled5rp.png)[/CENTER][/QUOTE]

I'm sorry, but the package does give the same error 
"(dvdstyler:11291): Gtk-WARNING **: gtk_menu_attach_to_widget(): menu already attached to GtkMenuItem
**Segmentation fault**
"

I tried to force a downgrade, but it seems I've somehow corrupted the repositories, because there are no other versions available.:---) 

Any ideas?

Edit: I'm sorry, my mistake! I was'nt aware of the fact that this is a Hoary thread. I'm on Breezy and that means I have the new version 'mjpegtools'.

Jan

---

### Post by reet on 2005-12-07
Hi, I have used Bored2k's .deb package on Breezy without problem, sort of. He didn't name the package correctly so it installs as "dvdstyler-1.4" and not "dvdstyler". All it adds is the gtk interface, there is no extra features or anything so you would probably be just fine with the .deb package from DVDstyler's website.

It seems as though I've run into every problem with DVDstyler that a person can run into. I still needed to downgrade mjpegtools in order to make a DVD. I was then left with a problem where I got many "audio sector out of range" errors when making a DVD. A little reasearch told me that I there was an incompatibility with the new versions of Imagemagick and DVDauthor that comes with Breezy. So after I forced those packages to the Hoary version everything is working great.

I can't wait for a stable version of DVDstyler 1.5 to come out. I am very exited about the subtitle support. I tried compiling 1.5 beta 3 myself but ran into problems.

---

### Post by jnie on 2005-12-07
I've found the repository which holds the files to downgrade mjpegtools, via this thread [http://ubuntuforums.org/showthread.php?t=79715&highlight=downgrade+mjpegtools]("http://ubuntuforums.org/showthread.php?t=79715&highlight=downgrade+mjpegtools")

And that helped me, now I just need to verify that Kino still works the way it used to :???: 

Jan

---

### Post by dgray_from_dc on 2005-12-12
Help!

I followed all the steps and got the following at the ./configure step.

dontrel@LV-426:~/temp/DVDStyler-1.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for install location... /usr/local
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ranlib... ranlib
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for wx-config... no
configure: error:
        Please check that wx-config is in path, the directory
        where wxWidgets libraries are installed (returned by
        'wx-config --libs' command) is in LD_LIBRARY_PATH or
        equivalent variable and wxWidgets is version 2.4.2 or above.

---

### Post by jnie on 2005-12-13
[QUOTE=dgray_from_dc]Help!

I followed all the steps and got the following at the ./configure step.

dontrel@LV-426:~/temp/DVDStyler-1.4$ ./configure
.....
checking for wx-config... no
configure: error:
        Please check that wx-config is in path, the directory
        where wxWidgets libraries are installed (returned by
        'wx-config --libs' command) is in LD_LIBRARY_PATH or
        equivalent variable and wxWidgets is version 2.4.2 or above.[/QUOTE]

Don't compile yourself, use the file that Bored2k submit'ed in post #23, and remember to downgrade the mjpegtools + libmjpegtools0, as I said in post #29.

Remember this thread was originally started as a Hoary HOWTO!

Jan

---

### Post by ezphilosophy on 2005-12-26
Fantastic how-to!  Thanks much

---

### Post by slew on 2005-12-26
[QUOTE=reet]Okay with a small bit of searching I found that mjpegtools is the cause of DVDStyler crashing on Ubuntu 5.10. I've downgraded *mjpegtools* and *libmjpegtools0* to 1.6.2-09 and it's working good now.

I am using the 1.4 Debian package from the DVDStyler website. I did not compile the program myself.[/QUOTE]

I've tryed to install dvdstyler, I get this:

Unpacking dvdstyler (from dvdstyler_1.4-3_i386.deb) ...
dpkg: dependency problems prevent configuration of dvdstyler:
 dvdstyler depends on libgcc1 (>= 1:4.0.2); however:
  Version of libgcc1 on system is 1:4.0.1-4ubuntu9.
 dvdstyler depends on libstdc++6 (>= 4.0.2-4); however:
  Version of libstdc++6 on system is 4.0.1-4ubuntu9.
 dvdstyler depends on libwxgtk2.6-0 (>= 2.6.1.2); however:
  Version of libwxgtk2.6-0 on system is 2.6.1.1.1ubuntu2.
dpkg: error processing dvdstyler (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dvdstyler
---
How do I make this program install? :confused: 
All I want to do is burn an .avi or .mpeg/mpg movie file to a dvd.

---

