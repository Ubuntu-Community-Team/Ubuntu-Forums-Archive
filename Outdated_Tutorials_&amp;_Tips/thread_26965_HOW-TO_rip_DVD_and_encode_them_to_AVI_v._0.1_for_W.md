---
title: "HOW-TO: rip DVD and encode them to AVI v. 0.1 for Warty"
date: 2005-04-14
forum: Outdated Tutorials &amp; Tips
---

### Post by LokiAs2 on 2005-04-14
HOW-TO rip DVD and encode them to AVI v. 0.1 for Warty

# sudo gedit /etc/apt/sources.list

Add these lines to the end of the file:

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

# sudo apt-get update
# sudo apt-get install w32codecs
# sudo apt-get install libdvdcss2
# sudo apt-get install vobcopy
# sudo apt-get install manpages-dev
# sudo apt-get install autoconf
# sudo apt-get install automake
# sudo apt-get install libtool
# sudo apt-get install flex
# sudo apt-get install bison
# sudo apt-get install gcc-doc
# sudo apt-get install g++
# sudo apt-get install x-window-system-dev
# sudo apt-get install libgtk1.2-dev
# sudo apt-get install libpng12-dev
# sudo apt-get install fakeroot
# sudo apt-get install liblame-dev
# sudo apt-get install libxvidcore4-dev
# sudo apt-get install libconfhelper-perl

Go to the mplayer home site [http://www.mplayerhq.hu](http://www.mplayerhq.hu) and download the latest release, fonts, and a skin (these all is up to you, you can just use a console version of mplayer, but at least you need a release and fonts).

# cd YOUR_DOWNLOAD_FOLDER
# tar -xvjf MPlayer-1.0pre6a.tar.bz2
# cd Mplayer-1.0pre6a
(your file name may vary depending on the version of mplayer)

This is optional, but strongly recommended:

# gedit debian/rules
find "--enable-runtime-cpudetection" and delete it, it won't enable run-time cpu detection, and let YOUR build of MPlayer be optimized for YOUR cpu and give a significant performance boost.

# fakeroot debian/rules binary

Go get some coffee and when the build is complete do:

# cd ..
# sudo dpkg -i mplayer_1.0cvs_i386.deb (your package name may be different)
You now have mplayer and mencoder installed.
In order to install a skin, download a skin (eg. Blue-1.4.tar.bz2) do:
# tar -xvjf Blue.tar.bz2
# mv Blue /usr/share/mplayer/Skin/default
In order to install fonts, download a font package (eg. mplayerfonts_win1251_v1.tar.gz)
# tar -xvzf mplayerfonts_win1251_v1.tar.gz
# sudo cp windows-1251/arial-14/* /usr/share/mplayer/font/

Now on to encoding:

I chose “Chronicles of Riddick” DVD for my example

First you must rip your VOBs to harddisk:
# vobcopy -i YOUR_MOUNT_POINT_FOR_DVD_DRIVE -o YOUR_PLACE_TO_STORE_VOBS
# cd  YOUR_PLACE_TO_STORE_VOBS

Encode the audio only:
# mplayer dvd://1 -v
Find something that looks like this:
[open] audio stream: 0 audio format: ac3 (5.1) language: en aid: 128
[open] audio stream: 1 audio format: ac3 (5.1) language: ru aid: 129
Remember the aid, in my case this is ru aid: 129, then run:

# cat *.vob | mencoder -ovc frameno -o frameno.avi -oac mp3lame -lameopts abr:br=128 -aid 129 -

Your audio will be transcoded using lame with average bitrate ~128kb\s (you may choose whatever bitrate you want or even leave it as .ac3 - for ac3 run the following: cat *.vob | mencoder -ovc frameno -o frameno.avi -oac copy -aid 129 - , but I'd recommend using mp3, because with audio in ac3 the file size may be too big ),write down the bitrate for your desired file size. In my case it is 781 for a 700 mb file.

NB: You may find out that you don't have /dev/dvd, so place the following line in 
/etc/mplayer/mplayer.conf:
dvd-device=/dev/YOUR_DVDROM

Find the right numbers for cropping:
#mplayer -vf cropdetect vts_01_1.vob
Write down the numbers (eg. 704:320:8:128)

Find the right numbers for scaling:
#mplayer -vf crop=704:320:8:128,scale=512:200 vts_01_1.vob

Write down the numbers again, find the line:
VO: [xv] 512x200 => 512x218 Planar YV12
and remember the second (eg. 512x218)

Generate a preview (1st pass):

# mencoder -oac copy -o /dev/null -ovc xvid -xvidencopts vhq=1:pass=1:qpel:trellis -sws 2 -ni -vf crop=704:320:8:128,scale=512:283 -ss 0:20 -endpos 0:30 VTS_01_3.VOB (of course put YOUR numbers)

Generating a preview (2nd pass):

# mencoder -oac copy -o preview.avi -ovc xvid -xvidencopts vhq=1:pass=2:qpel:trellis:bitrate=781 -sws 2 -ni -vf crop=704:320:8:128,scale=512:283 -ss 0:20 -endpos 0:30 VTS_01_3.VOB (use the same numbers plus you bitrate from audio section)

The final stage:

Generate the final AVI (1st pass):

#cat *.VOB |  mencoder -oac copy -o /dev/null -ovc xvid -xvidencopts vhq=1:pass=1:qpel:trellis -sws 2 -ni -vf crop=704:320:8:128,scale=512:283  -

Generate the final AVI (2nd pass):

#cat *.VOB |  mencoder -oac copy -o chronicles_of_riddick.avi -ovc xvid -xvidencopts vhq=1:pass=2:qpel:trellis:bitrate=781 -sws 2 -ni  -vf  crop=704:320:8:128,scale=512:283 -

It take about 2-2,5 hours to encode a 1 hour film, so be patient.

ps. You are very welcome to add some more parameters, read man mplayer and documentation found in the mplayer_source/DOCS directory.

---

### Post by MetalMusicAddict on 2005-04-14
Very, very nice man. I just wish it was as easy as Gordianknot.

---

### Post by gil-galad on 2005-04-14
Or just use dvdrip, which has a very good interface for ripping dvd's.

---

### Post by LokiAs2 on 2005-04-14
I think it's easier than gordian knot, and takes less time, the result for xvid is better under Linux

---

### Post by MetalMusicAddict on 2005-04-14
[QUOTE=LokiAs2]I think it's easier than gordian knot, and takes less time, the result for xvid is better under Linux[/QUOTE]
Really? Gotta try this. 

Nice to see I can crop also. 

Can subtitles be added also? Or a target file-size? ie: 1400megs. I do see where you can mux .ac3 but can I transcode to a different bitrate for the .ac3? ie: 443 to 224 or 192?

DVDRip looks nice. Gotta see how it stacks up to DVD Decrypter. I dont mean to sound rude by comparing but apps like the ones I mentioned are the main reason I still dual-boot.

If I find good replacements thats great. If only we could a Cd ripper/encoder as good as EAC or Audiograbber. ;)

---

### Post by LokiAs2 on 2005-04-14
Recommended bitrate for xvid is displayed after transcoing audio, read carefully:
eg. 781 for 1x700Mb
    1052 for 2x700Mb
     ...     for 1x650 Mb
etc

From mencoder documentation:

7.8. Extracting DVD subtitles to VOBsub file

MEncoder is capable of extracting subtitles from a DVD into VOBsub formatted files. They consist of a pair of files ending in .idx and .sub and are usually packaged in a single .rar archive. MPlayer can play these with the -vobsub and -vobsubid options.

You specify the basename (i.e without the .idx or .sub extension) of the output files with -vobsubout and the index for this subtitle in the resulting files with -vobsuboutindex.

If the input is not from a DVD you should use -ifo to indicate the .ifo file needed to construct the resulting .idx file.

If the input is not from a DVD and you do not have the .ifo file you will need to use the -vobsubid option to let it know what language id to put in the .idx file.

Each run will append the running subtitle if the .idx and .sub files already exist. So you should remove any before starting.

Example 7.3. Copying two subtitles from a DVD while doing 2-pass encoding

rm subtitles.idx subtitles.sub
mencoder dvd://1 -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vpass=1 -vobsubout subtitles -vobsuboutindex 0 -sid 2
mencoder dvd://1 -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vpass=2 -vobsubout subtitles -vobsuboutindex 1 -sid 5

Example 7.4. Copying a french subtitle from an MPEG file

rm subtitles.idx subtitles.sub
mencoder movie.mpg -ifo movie.ifo -vobsubout subtitles -vobsuboutindex 0 -vobsuboutid fr -sid 1

so, I suppose it's possilble to rip subtitles, but I haven't tried it myself.

Mencoder is faster than dvdrip (it's actually just a front-end for "transcode" and some other programs)

And, of course there is no need to keep windows running, because of dvd decrypter. I can suggest using "grip" instead of audiograbber or eac

---

### Post by simple on 2005-06-12
[QUOTE=LokiAs2]Recommended bitrate for xvid is displayed after transcoing audio, read carefully:
eg. 781 for 1x700Mb
    1052 for 2x700Mb
     ...     for 1x650 Mb
etc

From mencoder documentation:

7.8. Extracting DVD subtitles to VOBsub file

MEncoder is capable of extracting subtitles from a DVD into VOBsub formatted files. They consist of a pair of files ending in .idx and .sub and are usually packaged in a single .rar archive. MPlayer can play these with the -vobsub and -vobsubid options.

You specify the basename (i.e without the .idx or .sub extension) of the output files with -vobsubout and the index for this subtitle in the resulting files with -vobsuboutindex.

If the input is not from a DVD you should use -ifo to indicate the .ifo file needed to construct the resulting .idx file.

If the input is not from a DVD and you do not have the .ifo file you will need to use the -vobsubid option to let it know what language id to put in the .idx file.

Each run will append the running subtitle if the .idx and .sub files already exist. So you should remove any before starting.

Example 7.3. Copying two subtitles from a DVD while doing 2-pass encoding

rm subtitles.idx subtitles.sub
mencoder dvd://1 -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vpass=1 -vobsubout subtitles -vobsuboutindex 0 -sid 2
mencoder dvd://1 -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vpass=2 -vobsubout subtitles -vobsuboutindex 1 -sid 5

Example 7.4. Copying a french subtitle from an MPEG file

rm subtitles.idx subtitles.sub
mencoder movie.mpg -ifo movie.ifo -vobsubout subtitles -vobsuboutindex 0 -vobsuboutid fr -sid 1

so, I suppose it's possilble to rip subtitles, but I haven't tried it myself.

Mencoder is faster than dvdrip (it's actually just a front-end for "transcode" and some other programs)

And, of course there is no need to keep windows running, because of dvd decrypter. I can suggest using "grip" instead of audiograbber or eac[/QUOTE]
 what about avi to dvd?

---

