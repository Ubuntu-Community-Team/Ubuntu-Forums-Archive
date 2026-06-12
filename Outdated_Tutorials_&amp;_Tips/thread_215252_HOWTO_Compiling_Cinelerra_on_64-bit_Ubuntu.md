---
title: "HOWTO: Compiling Cinelerra on 64-bit Ubuntu"
date: 2006-07-13
forum: Outdated Tutorials &amp; Tips
---

### Post by chainzz on 2006-07-13
Yesterday I received my AMD64 processor (AMD Athlon 64 3400+) and I decided to give the 64-bit edition of Ubuntu a go. One of the first things I did was trying to compile Cinelerra, I heard that it worked best on 64-bit PC's. Before this I already compiled it a few times on my old 32-bit Ubuntu installation but compiling on 64-bit gives a few problems you don't get with 32-bit. I finally completed the compilation about 5 minutes ago, but I got numerous errors and other problems so I decided to make a small tutorial on how to do it.

In this tutorial you will downloaded a lot of source-code and stuff like that so I recommend you to make an empty folder on your desktop, cd to that folder and execute all the commands there.

Before you start with the tutorial, you need to install all the packages that are needed (you need to have the extra repositories enabled for this, check out the Ubuntu wiki if you want to know how to do this, or check this thread: [http://www.ubuntuforums.org/showthread.php?t=188264](http://www.ubuntuforums.org/showthread.php?t=188264)):
```
sudo apt-get install build-essential automake1.7 libtool xorg-dev libasound2-dev libogg-dev libvorbis-dev libtheora-dev libopenexr-dev libdv4-dev libpng3-dev libjpeg62-dev uuid-dev libmjpegtools-dev liba52-dev liblame-dev libsndfile1-dev libfaac-dev libfaad2-dev fftw3-dev libraw1394-dev libavc1394-dev libtiff4-dev subversion checkinstall yasm
```

I learned most of this from this thread: [http://www.ubuntuforums.org/showthread.php?t=188264](http://www.ubuntuforums.org/showthread.php?t=188264)
Thanks to Iprofil for learning me the (Cinelerra) compiling basics :)
Cinelerra community version homepage: [http://cvs.cinelerra.org](http://cvs.cinelerra.org)
Offical Cinelerra homepage with explanation of what Cinelerra is: [http://www.heroinewarrior.com/cinelerra.php3](http://www.heroinewarrior.com/cinelerra.php3)

**1. Compiling and installing x264**

First we need to compile x264, because the x264 packages in the Ubuntu repositories are not compiled correctly to be used for compiling Cinelerra (in 32-bit Ubuntu they are compiled correctly but in 64-bit Ubuntu they are not). The first thing we need to do is get the latest x264 revision:
```
svn co svn://svn.videolan.org/x264/trunk x264
```
Then cd into the folder (cd x264) and execute the configure file. However, you need to add the flag --enable-pic, this way x264 will compile in the right way so you can use it with the compilation of Cinelerra.
```
./configure --enable-pic
```
When this is ready, we will compile x264, just type 'make' when you are inside the x264 folder:
```
make
```
After this, install it with 'make install':
```
make install
```
Now you are done with installing x264, let's move on to the important part: compiling and installing Cinelerra!

**2. Compiling and installing Cinelerra**

Get the latest revision of Cinelerra:
```
svn checkout svn://cvs.cinelerra.org/repos/cinelerra/trunk/hvirtual
```
cd into the hvirtual folder that was created when downloading to latest revision and edit the autogen.sh file with gedit:
```
gedit autogen.sh
```
Find this:
```
# export AUTOMAKE=/usr/bin/automake-1.7
# export ACLOCAL=/usr/bin/aclocal-1.7
```
and remove the hashes (#) in front of both lines, and save the file.
Now we are going to compile Cinelerra. cd to the hvirtual directory and execute the following commands:
```
./autogen.sh
./configure
make
```
You have the biggest chance on compile errors in the make process. If you follow this tutorial carefully it shouldn't go wrong but sometimes it still does. Don't panic, I solved most of the problems with Google, just enter (parts of) the error message. With a little smart thinking most of the problems can be easily solved.

When everything is compiled succesfully, the only thing left to do is installing Cinelerra. Most people do it with 'make install' but I prefer to do it with 'checkinstall' because it creates a Debian package of the program so you can easily remove the program again and you can also easily distribute it to others.
The only thing you have to do is type this when you are in the hvirtual folder:
```
checkinstall
```
It will create a Debian package and will also lead you through a simple process where you can set all the options of the Debian package, like the name, description, version, maintainer, architecture etc. Be sure to set the architecture to 'amd64' (not 'x86_64'!) otherwise it will not install.

This is the end of my tutorial, I hope you will enjoy Cinelerra, it's a great piece of software. Be sure to checkout [http://cvs.cinelerra.org](http://cvs.cinelerra.org) regulary to see if a new version has been released, then you will have to recompile again. If you have any questions feel free to ask them here or in Iprofil's thread: [http://www.ubuntuforums.org/showthread.php?t=188264](http://www.ubuntuforums.org/showthread.php?t=188264)

---

### Post by mkw87 on 2006-07-17
Nevermind, figured it out myself, thanks for the good HOWTO though.

---

### Post by lprofil on 2006-07-22
Hi Chainzz,

nice to meet you again on this thread. How comes that i bought myself a AMD-Athlon 64 3000+ 2 weeks ago and that i want to compile Cinelerra on my 64-bit Edgy? Coincidence? ;)

I tried your tutorial and there are some small corections i would like to add:

When i am compiling x264 i get:
```
make: yasm: Command not found
make: *** [common/amd64/dct-a.o] Error 127

```

so you need to add **yasm** to your list of packages to install like:

**1. Compiling and installing x264**

```
sudo apt-get install build-essential automake1.7 libtool xorg-dev libasound2-dev libogg-dev libvorbis-dev libtheora-dev libopenexr-dev libdv4-dev libpng3-dev libjpeg62-dev uuid-dev libmjpegtools-dev liba52-dev liblame-dev libsndfile1-dev libfaac-dev libfaad2-dev fftw3-dev libraw1394-dev libavc1394-dev libtiff4-dev subversion checkinstall yasm
```

Poorly my compiling session breaks after 5 minutes and says:

```
if /bin/bash ../../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../..    -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64    -D_GNU_SOURCE -DHAVE_AV_CONFIG_H -I./.. -g -O2 -MT x264.lo -MD -MP -MF ".deps/x264.Tpo" \
          -c -o x264.lo `test -f 'x264.c' || echo './'`x264.c; \
        then mv -f ".deps/x264.Tpo" ".deps/x264.Plo"; \
        else rm -f ".deps/x264.Tpo"; exit 1; \
        fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../.. -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -D_GNU_SOURCE -DHAVE_AV_CONFIG_H -I./.. -g -O2 -MT x264.lo -MD -MP -MF .deps/x264.Tpo -c x264.c  -fPIC -DPIC -o .libs/x264.o
x264.c: In function 'X264_init':
x264.c:139: error: 'struct <anonymous>' has no member named 'b_cbr'
make[5]: *** [x264.lo] Error 1
make[5]: Leaving directory `/opt/hvirtual/quicktime/ffmpeg/libavcodec'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/opt/hvirtual/quicktime/ffmpeg/libavcodec'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/opt/hvirtual/quicktime/ffmpeg'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/opt/hvirtual/quicktime'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/opt/hvirtual'
make: *** [all] Error 2

```
 
I will try to fix it and post the solution.

#######


/lprofil

---

### Post by lprofil on 2006-07-22
Shops are closing soon and i need to get some food before i end up starving with an empty fridge for the whole weekend.

Cinelerra is compiled now and starts (at least).

Any how and why later.

/lprofil

ps: small hint:
google 
and
[http://www.mail-archive.com/cinelerra@skolelinux.no/msg01767.html](http://www.mail-archive.com/cinelerra@skolelinux.no/msg01767.html)

---

### Post by Ellarco on 2006-07-26
Any progress in the last few days? I too have this problem.

AMD64. Kubuntu. Latest svn of Cinelerra (configured with ```
--with-pic
```) and x264 (configured with ```
--extra-cflags=-fPIC --extra-asflags=-D__PIC__
```).

```

if /bin/sh ../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../..    -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64    -D_GNU_SOURCE -DHAVE_AV_CONFIG_H -I./.. -g -O2 -MT x264.lo -MD -MP -MF ".deps/x264.Tpo" -c -o x264.lo x264.c; \
        then mv -f ".deps/x264.Tpo" ".deps/x264.Plo"; else rm -f ".deps/x264.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../.. -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -D_GNU_SOURCE -DHAVE_AV_CONFIG_H -I./.. -g -O2 -MT x264.lo -MD -MP -MF .deps/x264.Tpo -c x264.c  -fPIC -DPIC -o .libs/x264.o
x264.c: In function 'X264_init':
x264.c:139: error: 'struct <anonymous>' has no member named 'b_cbr'
make[5]: *** [x264.lo] Error 1

```

---

### Post by Ellarco on 2006-07-26
Okay, got it ... Heres what Ive learned (again platform is AMD64/Kubuntu):

1. As I write this, x264 is in rev. 537, Cinelerra is version 2.1 (subversion rev. 839). These versions are incompatible. x264.h has changed, so until Cinelerra catches up you will need rev 536. Get it with subversion:

```
$ svn co svn://svn.videolan.org/x264/trunk x264 -r536
```

2. x264 must be configured with the following flags:

```
$ ./configure --extra-cflags=-fPIC --extra-asflags=-D__PIC__
```

3. I had make problems when it got to the plugins directory, i.e. No rule to make target <blah>. I hacked my way around this (though theres no doubt a proper solution or a patch). Specifically I used a combination of grep and sed to replace all occurances within the source tree of "chromakey-hsv" with "chromakeyhsv", and "/seltempavg/" with "/denoiseseltempavg/" ... :-?  dont ask me why ...

4. Cinelerra must (I think) be configured with the following flag:

```
$ ./configure --with-pic
```

I also think I remember having problems with the Cinelerra tarball (its so long ago that I started this that I cant remember) so you might need to use subversion to get the Cinelerra sources.

Thats it. Its running for me now. Havent tested it out, I just know it starts okay. Id be a little concerned about those plugins in point 3 ...

Thanks for the howto chainzz =D>

---

### Post by lprofil on 2006-07-28
Hi Ellarco,

i had the problems you mentioning in **point 3** too. I solved it by creating the neccesary directory
 and put the requested files into it which i found in the wrong declaired pathes.

Just before "making" Cinelerra type 
Follow these steps:


```

cd /opt/hvirtual
./configure --with-pic --disable-shared --enable-static
```

```
mkdir plugins/chromakey-hsv && cp plugins/chromakeyhsv/* plugins/chromakey-hsv
```

```
mkdir plugins/seltempavg && cp plugins/denoiseseltempavg/* plugins/seltempavg/
```

```
make
```

```
make install
```


I am just compiling x-264 and Cinelerra-64 bit know and will put the 64-bit deb-files on my webspace in case i works out.

/lprofil


**ps:** I now found some **information about the bug** here:
[http://cvs.cinelerra.org/svn_log.php]("http://cvs.cinelerra.org/svn_log.php")
Why is it actually still exsistent if i was already patched?

**pps:** Why am i building a 2.0 Version of Cinelerra if the CVS-Version claims it is 2.1 ?

Answer: My fault!
I messed up:
svn checkout svn://cvs.cinelerra.org/repos/cinelerra/trunk/hvirtual
with this:
svn checkout svn://cvs.cinelerra.org/repos/cinelerra/tags/r1_2_2-last/hvirtual

---

### Post by lprofil on 2006-07-28
Hi,

it worked out with compiling the 64-bit packages of Cinelerra. 

:)

You might shortcut chainzz steps if you are fine with a Cinelerra Version from the 28th of July.
Download the 64-bit deb-files from:
[http://ww2.fs.ei.tum.de/~dr/](http://ww2.fs.ei.tum.de/~dr/)

Then:

```
sudo apt-get install build-essential automake1.7 libtool xorg-dev libasound2-dev libogg-dev libvorbis-dev libtheora-dev libopenexr-dev libdv4-dev libpng3-dev libjpeg62-dev uuid-dev libmjpegtools-dev liba52-dev liblame-dev libsndfile1-dev libfaac-dev libfaad2-dev fftw3-dev libraw1394-dev libavc1394-dev libtiff4-dev subversion checkinstall yasm
```

Now:

```
sudo dpkg -i *.deb
```
in the folder where you downloaded your **two** 64-bit files too.

Finally start cinelerra as root:

```
sudo cinelerra
```


Fahrvergnügen

/lprofile

---

### Post by Ellarco on 2006-07-28
Well done.

---

### Post by macksgarage on 2006-08-14
Thanks for the docs, this page helped a lot in getting Cinellera compiled and running on my machine.

I've managed to compile and run cinelerra on a fresh install of ubuntu 6.06 amd64.  [Some notes are here if it helps anyone.]("http://www.mackallison.net/index.php?title=Cinelerra%2C_Ubuntu_6.06_LTS_amd64")  It took days, there's different sources, obscure notes, and the cinelerra svn server happened to disappear for a bit, leaving behind only a post it thunbtacked to the newsgroup.  Such is the way it goes . . .8-[

---

### Post by supreme_geek_overlord on 2006-08-15
Thanks for all the help. This tutorial is the best I've found so far, and it worked (for the most part). I managed to get everything compiled from source, though I'm sure using **lprofil**'s packages would have been faster/cleaner.

The install was fairly uneventful with these tips, but I have just a couple notes:[LIST]
[*]When I used the *cvs.cinelerra.org* repositories, svn returned an error. Instead, I checked it with the repository from the ["official" instructions]("http://cvs.cinelerra.org/svnusage.html"):
```
svn co svn://svn.skolelinux.org/cinelerra/trunk/hvirtual cinelerra
```
[*]./configure didn't detect some 1394 components (I'm not really sure what "libiec61883" is):
```
Summary of optional components:
...
  libraw1394              missing
  libiec61883             missing
  libavc1394 libraries    found
  libavc1394 headers      found
  librom1394 libraries    found
  librom1394 headers      found
Firewire is disabled
...
```

I'm stuck without capture support, but otherwise everything seems fine. I hear Kino has a better interface for that anyway, so I'll probably use that.[/LIST]Thanks again for all the help -- I was getting frustrated by many of the other methods presented on the net.

**Edit**: On second thought, loading the kernel modules for 1394 might have fixed that second issue, but I don't have the time to try it. Cheers. :)

---

### Post by chainzz on 2006-08-15
It's been a while since I visited this thread, I'm happy to see you guys posting all your solutions to the different compiling problems on 64-bit Ubuntu! Iprofil, nice processor! It must be a big difference compared to your old PIII 700. I added yasm to the packages that need to be installed by the way, thanks for the tip.

I switched back to 32-bit Ubuntu for now, because I couldn't get the ATI drivers running on 64-bit Ubuntu because of a bug that still needs to be fixed. I needed it because I'm learning Blender (a 3D modeling app) right now. I'll give 64-bit Ubuntu a shot again when Edgy is out.

---

### Post by monts on 2006-08-15
> **lprofil said:**
> Hi,

it worked out with compiling the 64-bit packages of Cinelerra. 

:)

You might shortcut chainzz steps if you are fine with a Cinelerra Version from the 28th of July.
Download the 64-bit deb-files from:
[http://ww2.fs.ei.tum.de/~dr/](http://ww2.fs.ei.tum.de/~dr/)

Then:

```
sudo apt-get install build-essential automake1.7 libtool xorg-dev libasound2-dev libogg-dev libvorbis-dev libtheora-dev libopenexr-dev libdv4-dev libpng3-dev libjpeg62-dev uuid-dev libmjpegtools-dev liba52-dev liblame-dev libsndfile1-dev libfaac-dev libfaad2-dev fftw3-dev libraw1394-dev libavc1394-dev libtiff4-dev subversion checkinstall yasm
```

Now:

```
sudo dpkg -i *.deb
```
in the folder where you downloaded your **two** 64-bit files too.

Finally start cinelerra as root:

```
sudo cinelerra
```


Fahrvergnügen

/lprofile

Tried it and when I tried to start it I had this error message. 

```

cinelerra: /lib/libc.so.6: version `GLIBC_2.4' not found (required by cinelerra)

```
 
but it seems that version of glibc is due for edgy not dapper

---

### Post by cesera on 2006-08-23
> **monts said:**
> cinelerra: /lib/libc.so.6: version `GLIBC_2.4' not found (required by cinelerra)
 
I get exactly the same error, any idea why this happens? Is there a way around this?

---

### Post by dna_media on 2006-08-27
I am getting a different problem. I am getting a split second of splash screen and the following error:

"MWindow::init_theme: theme S.U.V. not found."

This seems like a very stupid problem. Any ideas?

---

### Post by aanderse on 2006-08-30
this is the same problem I'm having ...  I'm gonna mess around with some settings see if I can change the theme.  Hopefully someone knows how to solve this one :)

> **dna_media said:**
> I am getting a different problem. I am getting a split second of splash screen and the following error:

"MWindow::init_theme: theme S.U.V. not found."

This seems like a very stupid problem. Any ideas?

---

### Post by aanderse on 2006-08-31
I was on #cinelerra on irc.freenode.org and someone named Huey said that they had the same problem and solved it.


<Huey> you have to delete ~/.bcast
<Huey> I also deleted /usr/lib/cinelerra and reinstalled--there were some old plugins there


I'm gonna mess around with /usr/lib/cinelerra a bit later and post my results back here.

---

### Post by ColinG on 2006-09-04
I have tried the debs bit but have the GLIBC problem. Has a workaround been found? If not how do I uninstall the packages - there is nothing in Synaptic.

Many thanks
Colin

---

### Post by magicmike on 2006-09-13
has anybody found an answer to the above error?

cinelerra: /lib/libc.so.6: version `GLIBC_2.4' not found (required by cinelerra)

Been searching but have not found anything yet.

---

### Post by ColinG on 2006-09-13
Video editing and Linux don't really go together. IMHO.

---

### Post by monts on 2006-09-13
> **magicmike said:**
> has anybody found an answer to the above error?

cinelerra: /lib/libc.so.6: version `GLIBC_2.4' not found (required by cinelerra)

Been searching but have not found anything yet.

Think it has to do with the version of glibc that dapper has (2.3.6 i think) and that edgy will have 2.4. Also if that is with the deb's it was made on an edgy development machine ( tho not to sure on that)

HTH :)

---

### Post by roccofoti on 2006-09-17
Hi all,
I'm also trying to compile cinelerra on Ubuntu64 and i got this message:

videodevice.C: In constructor 'VideoDevice::VideoDevice(MWindow*)':
videodevice.C:112: error: invalid use of undefined type 'struct MWindow'
mwindow.inc:16: error: forward declaration of 'struct MWindow'
make[3]: *** [videodevice.o] Error 1
make[3]: Leaving directory `/home/rocco/hvirtual/cinelerra'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rocco/hvirtual/cinelerra'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rocco/hvirtual'
make: *** [all] Error 2


any ideas?
Please help me!

Rocco

---

### Post by henriquemaia on 2006-10-06
Maybe this is not so easy to accomplish, but can someone create a cinelerra .deb for amd64?

Thanks anyway.

---

### Post by jkwarras on 2006-10-07
> **henriquemaia said:**
> Maybe this is not so easy to accomplish, but can someone create a cinelerra .deb for amd64?

Thanks anyway.
Until amd64 packages for cinelerra 2.1 are available, you could try to download the 2.0-1 rpm version, and convert it to a deb file. I did, and I have cinelerra with capture support, etc... :)

[http://prdownloads.sourceforge.net/heroines/cinelerra-2.0-1.x86_64.rpm?download](http://prdownloads.sourceforge.net/heroines/cinelerra-2.0-1.x86_64.rpm?download)

You must have alien package installed and convert it to deb to be able to install it.

---

### Post by ColinG on 2006-10-07
I'm a noob so could you please explain how to use Alien with the rpm please?

And are you running Edgy or Dapper?

Many thanks
Colin:)

---

### Post by jkwarras on 2006-10-29
Put the rpm in a directory, open a terminal, move to the directory and use alien like this:

```
sudo alien *.rpm
```

it will convert all rpm in the directory to deb.

I was using dapper and now edgy,a nd it works :)

---

### Post by ColinG on 2006-10-29
Many thanks,jkwarras, Alien it is then.

How does Cinelerra run on your 64 bit box? Certainly at 32 bit I noticed performance issues (jerkiness of playback via the timeline that made it through to the final render). I'm hoping performance improves under 64 bit.

Thanks again
Colin :)

---

### Post by jkwarras on 2006-10-31
I didn't have too much time to work with it, but it seems ot work fine.

---

### Post by gratefulfrog on 2006-11-11
Hi!

Great thread! I'm back at cinelerra after a long time away, trying to compile for Dapper amd64. I've had an x264 error, which is slightly different from the one reported earlier in this thread.

I did the following:

Followed all the above instructions for x264:

```
svn co svn://svn.videolan.org/x264/trunk x264 -r536
```
then:
```
./configure --extra-cflags=-fPIC --extra-asflags=-D__PIC__
```
then:
```
make
sudo checkinstall
```

then for cinelerra:
```
./configure --with-pic
make
```

But this error persists (I had it after following the 'basic' instructions on the 1st page of this thread, and still have it now):

```
gcc -shared  .libs/atom.o .libs/avcc.o .libs/avi_hdrl.o .libs/avi_idx1.o .libs/avi_movi.o .libs/avi_strl.o .libs/avi_odml.o .libs/avi_ix.o .libs/avi_indx.o .libs/avi_riff.o .libs/cmodel_default.o .libs/cmodel_float.o .libs/cmodel_yuv420p.o .libs/cmodel_yuv422.o .libs/codecs.o .libs/colormodels.o .libs/ctab.o .libs/dinf.o .libs/dref.o .libs/edts.o .libs/elst.o .libs/esds.o .libs/graphics.o .libs/hdlr.o .libs/ima4.o .libs/interlacemodes.o .libs/jpeg.o .libs/libdv.o .libs/libmjpeg.o .libs/matrix.o .libs/mdat.o .libs/mdhd.o .libs/mdia.o .libs/minf.o .libs/moov.o .libs/mp4a.o .libs/mvhd.o .libs/plugin.o .libs/qtcache.o .libs/qtdv.o .libs/qtffmpeg.o .libs/qth264.o .libs/qtpng.o .libs/qtmp3.o .libs/quicktime.o .libs/raw.o .libs/rawaudio.o .libs/rle.o .libs/smhd.o .libs/stbl.o .libs/stco.o .libs/stsc.o .libs/stsd.o .libs/stsdtable.o .libs/stss.o .libs/stsz.o .libs/stts.o .libs/tkhd.o .libs/trak.o .libs/twos.o .libs/udta.o .libs/ulaw.o .libs/util.o .libs/v308.o .libs/v408.o .libs/v410.o .libs/vmhd.o .libs/vbraudio.o .libs/vorbis.o .libs/workarounds.o .libs/yuv2.o .libs/yuv4.o .libs/yv12.o .libs/wmx2.o .libs/wma.o .libs/mpeg4.o -Wl,--whole-archive ffmpeg/libavcodec/.libs/libavcodec.a encore50/.libs/libencore.a -Wl,--no-whole-archive  -Wl,--rpath -Wl,/home/bob/Desktop/TempCinelerra/hvirtual/libmpeg3/.libs -Wl,--rpath -Wl,/usr/local/lib /usr/lib/liba52.so -L/usr/lib /usr/lib/libvorbisenc.so /usr/lib/libvorbisfile.so /usr/lib/libvorbis.so /usr/lib/libtheora.so /usr/lib/libogg.so /usr/lib/libmp3lame.so -lfaad -lfaac ../libmpeg3/.libs/libmpeg3hv.so -lx264 /usr/lib/libdv.so /usr/lib/libjpeg.so -lpng -lz -lm -ldl -lpthread  -Wl,--no-undefined -Wl,-soname -Wl,libquicktimehv-1.6.0.so.1 -o .libs/libquicktimehv-1.6.0.so.1.0.0
/usr/bin/ld: /usr/lib/libx264.a(common.o): relocation R_X86_64_32S against `a local symbol' can not be used when making a shared object; recompile with -fPIC
/usr/lib/libx264.a: could not read symbols: Bad value
collect2: ld returned 1 exit status

```

It says to recompile with -fPIC, but it was compiled with that option already!

Any ideas?

thanks,
GF.
ps. I have a little help page for referring to a previous version of cinelerra which might interest beginners. follow the link on this page:
[http://gratefulfrog.net/]("http://gratefulfrog.net/")

---

### Post by Spidercorp on 2006-11-21
Thanks very much for putting in such easySpeak for a reticent learner as myself. I've been working through the tutorial just fine until 'make install' for the x264.

charlie@charlie-desktop:~/cine/x264$ make install
install -d /usr/local/bin /usr/local/include
install -d /usr/local/lib /usr/local/lib/pkgconfig
install: cannot create directory `/usr/local/lib/pkgconfig': Permission denied
make: *** [install] Error 1

did i miss something?

Thanks in advance

---

### Post by Spidercorp on 2006-11-21
note: the svn repos is now:
svn checkout svn://svn.skolelinux.org/cinelerra/trunk/hvirtual

btw, sorted out my previous permissions post, ta

---

### Post by cesera on 2006-11-24
> **Spidercorp said:**
> note: the svn repos is now:
svn checkout svn://svn.skolelinux.org/cinelerra/trunk/hvirtual
 
btw, sorted out my previous permissions post, ta
 
 
 
Just logged in to say exactly the same, can the first post be edited to reflect this, please. That would save people the hassle of having to find this out elsewhere.

---

### Post by ryan76 on 2006-11-25
This Howto is awesome and Cinelerra is running but processing movies very slowly, and I am getting this on startup:

[IMG]http://homepages.woosh.co.nz/ryan.kennedy/images/cinelerra-error.jpg[/IMG]

Here's what happens when I do that:

```
ryan@ryan-desktop:~$ sudo echo "0x7fffffff" > /proc/sys/kernel/shmmax
bash: /proc/sys/kernel/shmmax: Permission denied
```

Thanks for any help

---

### Post by cesera on 2006-11-25
> **ryan76 said:**
> 
 
```
ryan@ryan-desktop:~$ sudo echo "0x7fffffff" > /proc/sys/kernel/shmmax
bash: /proc/sys/kernel/shmmax: Permission denied
```
I had the same problem, but the following worked for me (I don't know why):
```
sudo -i
echo "0x7fffffff" > /proc/sys/kernel/shmmax

```
You can also add the 'echo' line to /etc/rc.local (not the 'sudo -i'), then this gets automatically done at startup.

---

### Post by ryan76 on 2006-11-25
awesome, thank you. That worked for the error message on startup although the picture is still lagging behind the audio. I guess I'll cope!


Edit: I'm not coping! How can I get the audio and video to match up when I'm editing? This is driving me crazy!

---

### Post by ryan76 on 2006-11-29
Has anyone else had this problem? What did you do?

Edit: I read the sticky and think I should ask this in another forum but I can't seem to delete this post.

---

### Post by compwiz18 on 2006-12-25
> **cesera said:**
> I had the same problem, but the following worked for me (I don't know why):
```
sudo -i
echo "0x7fffffff" > /proc/sys/kernel/shmmax

```
You can also add the 'echo' line to /etc/rc.local (not the 'sudo -i'), then this gets automatically done at startup.
Just for reference: you can't run echo as sudo - it doesn't work right, hence the problem.  Do sudo su and then echo stuff.

And thanks for the great howto - it is compiling now, not sure if it will work though :P  Hopefully it will :D

---

### Post by Keldek on 2006-12-30
recieving the follow error when trying to make Cinelerra

```
make[1]: /usr/bin/ld: cannot find -lGLU
collect2: ld returned 1 exit status
make[2]: *** [libguicast.la] Error 1
make[2]: Leaving directory `/home/keldek/Downloads/hvirtual/guicast'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keldek/Downloads/hvirtual'
make: *** [all] Error 2


```

---

### Post by luh3417 on 2007-01-04
That link to your useful tips is missing. I do not suppose it had an solution to the conflicting dependency problems I am having with KUbuntu 6.06 AMD 64, When I try installing the dependent packages I get 

The following packages have unmet dependencies:
  libmjpegtools-dev: Depends: libmjpegtools0 (= 1:1.8.0-0.4) but it is not going to be installed
E: Broken packages

Is the only fix for this removing KDE or is there another way?

---

### Post by luh3417 on 2007-01-04
Excellent thread. OK I can get around these dependency issues if I avoid trying to install with apt-get install cinelerra and install automake1.7 and compile the svn source in cd/hvirtual as per this howto.

I now get a make error which I have googled but cannot find an answer: Can ayone advise me on this?

fileogg.C: In member function ‘virtual int FileOGG::open_file(int, int)’:
fileogg.C:644: error: ‘theora_packet_isheader’ was not declared in this scope
fileogg.C:659: error: ‘theora_granule_frame’ was not declared in this scope
fileogg.C: In member function ‘int FileOGG::ogg_get_page_of_frame(sync_window_t*, long int, ogg_page*, int64_t)’:
fileogg.C:1160: error: ‘theora_granule_frame’ was not declared in this scope
fileogg.C: In member function ‘int FileOGG::ogg_seek_to_keyframe(sync_window_t*, long int, int64_t, int64_t*)’:
fileogg.C:1249: error: ‘theora_granule_frame’ was not declared in this scope
fileogg.C: In member function ‘virtual int FileOGG::read_frame(VFrame*)’:
fileogg.C:1474: error: ‘theora_packet_iskeyframe’ was not declared in this scopefileogg.C:1508: error: invalid conversion from ‘char*’ to ‘unsigned char*’
fileogg.C:1508: error:   initializing argument 1 of ‘VFrame::VFrame(unsigned char*, long int, long int, long int, int, int, int, long int)’
fileogg.C: In member function ‘int FileOGG::write_frames_theora(VFrame***, int, int)’:
fileogg.C:1928: error: invalid conversion from ‘unsigned char*’ to ‘char*’
fileogg.C:1929: error: invalid conversion from ‘unsigned char*’ to ‘char*’
fileogg.C:1930: error: invalid conversion from ‘unsigned char*’ to ‘char*’
make[3]: *** [fileogg.o] Error 1
make[3]: Leaving directory `/home/raena/DownloadApps/hvirtual/cinelerra'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/raena/DownloadApps/hvirtual/cinelerra'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/raena/DownloadApps/hvirtual'
make: *** [all] Error 2

---

### Post by luh3417 on 2007-01-04
> **Keldek said:**
> recieving the follow error when trying to make Cinelerra

```
make[1]: /usr/bin/ld: cannot find -lGLU
collect2: ld returned 1 exit status
make[2]: *** [libguicast.la] Error 1
make[2]: Leaving directory `/home/keldek/Downloads/hvirtual/guicast'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keldek/Downloads/hvirtual'
make: *** [all] Error 2


```

Have you checked in the ./configure report what is missing?

---

### Post by compwiz18 on 2007-01-04
> **luh3417 said:**
> Excellent thread. OK I can get around these dependency issues if I avoid trying to install with apt-get install cinelerra and install automake1.7 and compile the svn source in cd/hvirtual as per this howto.

I now get a make error which I have googled but cannot find an answer: Can ayone advise me on this?

fileogg.C: In member function ‘virtual int FileOGG::open_file(int, int)’:
fileogg.C:644: error: ‘theora_packet_isheader’ was not declared in this scope
fileogg.C:659: error: ‘theora_granule_frame’ was not declared in this scope
fileogg.C: In member function ‘int FileOGG::ogg_get_page_of_frame(sync_window_t*, long int, ogg_page*, int64_t)’:
fileogg.C:1160: error: ‘theora_granule_frame’ was not declared in this scope
fileogg.C: In member function ‘int FileOGG::ogg_seek_to_keyframe(sync_window_t*, long int, int64_t, int64_t*)’:
fileogg.C:1249: error: ‘theora_granule_frame’ was not declared in this scope
fileogg.C: In member function ‘virtual int FileOGG::read_frame(VFrame*)’:
fileogg.C:1474: error: ‘theora_packet_iskeyframe’ was not declared in this scopefileogg.C:1508: error: invalid conversion from ‘char*’ to ‘unsigned char*’
fileogg.C:1508: error:   initializing argument 1 of ‘VFrame::VFrame(unsigned char*, long int, long int, long int, int, int, int, long int)’
fileogg.C: In member function ‘int FileOGG::write_frames_theora(VFrame***, int, int)’:
fileogg.C:1928: error: invalid conversion from ‘unsigned char*’ to ‘char*’
fileogg.C:1929: error: invalid conversion from ‘unsigned char*’ to ‘char*’
fileogg.C:1930: error: invalid conversion from ‘unsigned char*’ to ‘char*’
make[3]: *** [fileogg.o] Error 1
make[3]: Leaving directory `/home/raena/DownloadApps/hvirtual/cinelerra'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/raena/DownloadApps/hvirtual/cinelerra'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/raena/DownloadApps/hvirtual'
make: *** [all] Error 2
you've got to install some sort of theora codec, I'm not exactly sure which one, but I had the same error.

---

### Post by radopenev on 2007-04-07
Hi, for all!
How can I solve the problem?
According with your advice ,I downloaded the 2 deb files and sudo ...
After all processing ,when I  
    sudo cinelerra
I've got the message:
cinelerra: /lib/libc.so.6: version `GLIBC_2.4' not found (required by cinelerra
I am trying to install ,but required version isn't in repos.
Litlle help?!:(

---

### Post by 9a3eedi on 2007-05-18
Cinelerra compiled successfully with some suggestions made by members in the first couple of replies.

However, it doesnt run:

```

the9a3eedi@the9a3eedi-desktop:~$ cinelerra
Cinelerra 2.1CV (C) 2006 Heroine Virtual Ltd.
Compiled on Wed May  9 13:37:33 GST 2007

Cinelerra is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it under
certain conditions. There is absolutely no warranty for Cinelerra.
MWindow::init_theme: theme S.U.V. not found.

```

seems like it doesnt find the theme module. How am I supposed to fix this (I hope I don't have to recompile this beast again -__- )

---

### Post by noctrex on 2007-05-26
hello! today i tried doing the steps mentioned here, but unfortunately it seems it doesn't want to compile.
x264-svn compiled fine, but when make'ing cinelerra-svn i get this error:
```
/usr/bin/ld: ffmpeg/libavcodec/.libs/libavcodec.a(simple_idct_mmx.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
ffmpeg/libavcodec/.libs/libavcodec.a(simple_idct_mmx.o): could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [libquicktimehv.la] Error 1
make[3]: Leaving directory `/home/noctrex/svn/hvirtual/quicktime'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/noctrex/svn/hvirtual/quicktime'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/noctrex/svn/hvirtual'
make: *** [all] Error 2
```

has anyone encountered something like this?
BTW, i'm on Feisty amd64.
I'll now try to compile cinelerra using the source from their website, hope i`ll have some success there.

---

### Post by ratm355 on 2007-06-10
I wrote a howto for installing Cinelerra from additional repositories with Feisty 64-bit. It's a little easier.

[CinelerraOnFeistyAMD64]("https://help.ubuntu.com/community/CinelerraOnFeistyAMD64")

---

### Post by 12monkeys on 2007-07-06
> **chainzz said:**
> Yesterday I received my AMD64 processor (AMD Athlon 64 3400+) and I decided to give the 64-bit edition of Ubuntu a go. One of the first things I did was trying to compile Cinelerra, I heard that it worked best on 64-bit PC's. Before this I already compiled it a few times on my old 32-bit Ubuntu installation but compiling on 64-bit gives a few problems you don't get with 32-bit. I finally completed the compilation about 5 minutes ago, but I got numerous errors and other problems so I decided to make a small tutorial on how to do it.

In this tutorial you will downloaded a lot of source-code and stuff like that so I recommend you to make an empty folder on your desktop, cd to that folder and execute all the commands there.

Before you start with the tutorial, you need to install all the packages that are needed (you need to have the extra repositories enabled for this, check out the Ubuntu wiki if you want to know how to do this, or check this thread: [http://www.ubuntuforums.org/showthread.php?t=188264](http://www.ubuntuforums.org/showthread.php?t=188264)):
```
sudo apt-get install build-essential automake1.7 libtool xorg-dev libasound2-dev libogg-dev libvorbis-dev libtheora-dev libopenexr-dev libdv4-dev libpng3-dev libjpeg62-dev uuid-dev libmjpegtools-dev liba52-dev liblame-dev libsndfile1-dev libfaac-dev libfaad2-dev fftw3-dev libraw1394-dev libavc1394-dev libtiff4-dev subversion checkinstall yasm
```

I learned most of this from this thread: [http://www.ubuntuforums.org/showthread.php?t=188264](http://www.ubuntuforums.org/showthread.php?t=188264)
Thanks to Iprofil for learning me the (Cinelerra) compiling basics :)
Cinelerra community version homepage: [http://cvs.cinelerra.org](http://cvs.cinelerra.org)
Offical Cinelerra homepage with explanation of what Cinelerra is: [http://www.heroinewarrior.com/cinelerra.php3](http://www.heroinewarrior.com/cinelerra.php3)

**1. Compiling and installing x264**

First we need to compile x264, because the x264 packages in the Ubuntu repositories are not compiled correctly to be used for compiling Cinelerra (in 32-bit Ubuntu they are compiled correctly but in 64-bit Ubuntu they are not). The first thing we need to do is get the latest x264 revision:
```
svn co svn://svn.videolan.org/x264/trunk x264
```
Then cd into the folder (cd x264) and execute the configure file. However, you need to add the flag --enable-pic, this way x264 will compile in the right way so you can use it with the compilation of Cinelerra.
```
./configure --enable-pic
```
When this is ready, we will compile x264, just type 'make' when you are inside the x264 folder:
```
make
```
After this, install it with 'make install':
```
make install
```
Now you are done with installing x264, let's move on to the important part: compiling and installing Cinelerra!

**2. Compiling and installing Cinelerra**

Get the latest revision of Cinelerra:
```
svn checkout svn://cvs.cinelerra.org/repos/cinelerra/trunk/hvirtual
```
cd into the hvirtual folder that was created when downloading to latest revision and edit the autogen.sh file with gedit:
```
gedit autogen.sh
```
Find this:
```
# export AUTOMAKE=/usr/bin/automake-1.7
# export ACLOCAL=/usr/bin/aclocal-1.7
```
and remove the hashes (#) in front of both lines, and save the file.
Now we are going to compile Cinelerra. cd to the hvirtual directory and execute the following commands:
```
./autogen.sh
./configure
make
```
You have the biggest chance on compile errors in the make process. If you follow this tutorial carefully it shouldn't go wrong but sometimes it still does. Don't panic, I solved most of the problems with Google, just enter (parts of) the error message. With a little smart thinking most of the problems can be easily solved.

When everything is compiled succesfully, the only thing left to do is installing Cinelerra. Most people do it with 'make install' but I prefer to do it with 'checkinstall' because it creates a Debian package of the program so you can easily remove the program again and you can also easily distribute it to others.
The only thing you have to do is type this when you are in the hvirtual folder:
```
checkinstall
```
It will create a Debian package and will also lead you through a simple process where you can set all the options of the Debian package, like the name, description, version, maintainer, architecture etc. Be sure to set the architecture to 'amd64' (not 'x86_64'!) otherwise it will not install.

This is the end of my tutorial, I hope you will enjoy Cinelerra, it's a great piece of software. Be sure to checkout [http://cvs.cinelerra.org](http://cvs.cinelerra.org) regulary to see if a new version has been released, then you will have to recompile again. If you have any questions feel free to ask them here or in Iprofil's thread: [http://www.ubuntuforums.org/showthread.php?t=188264](http://www.ubuntuforums.org/showthread.php?t=188264)

**Really a great job! :D Thanks a lot.**
Following step by step this tutorial, I suceeded in compiling a running CINELERRA on Ubuntu 7.04, Feisty Fawn! for amd64.
With a little googling and post-install of missing packages I got a running Debian package, that you can download from:
[http://www.sai.uni-heidelberg.de/download/hvirtual_2.1-1_amd64.deb]("http://www.sai.uni-heidelberg.de/download/hvirtual_2.1-1_amd64.deb")

Now I will list the steps I also had to follow to reach the goal:

**1. Preparing the system:**

This is the list of the packages I also had to install togheter with the ones suggested from  **chainzz** since I started trying to compile CINELERRA:

alsa-source (1.0.13-3ubuntu1)
debconf-utils (1.5.13ubuntu1)
nasm (0.98.38-1.2)
libgl1-mesa-dev (6.5.2-3ubuntu7)
libx11-dev (2:1.1.1-1ubuntu3)
libxau-dev (1:1.0.3-1)
libxdmcp-dev (1:1.0.2-1)
mesa-common-dev (6.5.2-3ubuntu7)
x11proto-core-dev (7.0.10-1)
x11proto-input-dev (1.4.1-1)
x11proto-kb-dev (1.0.3-2ubuntu1)
xtrans-dev (1.0.3-1)
libfreetype6-dev (2.2.1-5ubuntu1.1)
libglu1-mesa-dev (6.5.2-3ubuntu7)
libglu1-xorg-dev (1:7.2-0ubuntu11)
libsdl-ttf2.0-0 (2.0.8-3build1)
libsdl-ttf2.0-dev (2.0.8-3build1)
libsdl1.2-dev (1.2.11-7ubuntu1)
zlib1g-dev (1:1.2.3-13ubuntu4)
libneon26 (0.26.3-1)
libsvn1 (1.4.3dfsg1-1ubuntu1)
subversion (1.4.3dfsg1-1ubuntu1)
checkinstall (1.6.0-2ubuntu1)
libpng12-dev (1.2.15~beta5-1ubuntu1)
libpng3 (1.2.15~beta5-1ubuntu1)
cpp-3.4 (3.4.6-5ubuntu1)
f2c (20050501-1)
fort77 (1.15-7)
g77-3.4 (3.4.6-5ubuntu1)
gcc-3.4 (3.4.6-5ubuntu1)
gcc-3.4-base (3.4.6-5ubuntu1)
libf2c2 (20050501-2)
libf2c2-dev (20050501-2)
libg2c0 (1:3.4.6-5ubuntu1)
libg2c0-dev (1:3.4.6-5ubuntu1)
libasound2-dev (1.0.13-1ubuntu5)
liba52-0.7.4-dev (0.7.4-7)
libfaac-dev (1.24clean-0ubuntu4)
libfltk1.1 (1.1.7-2)
libmp4v2-dev (2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3)
libopenexr-dev (1.2.2-4.3ubuntu1)
libopenexr2c2a (1.2.2-4.3ubuntu1)
libtiff-opengl (3.8.2-6)
libtiff-tools (3.8.2-6)
libtiff4-dev (3.8.2-6)
libtiffxx0c2 (3.8.2-6)
libvorbis-dev (1.1.2.dfsg-1.2)
openexr (1.2.2-4.3ubuntu1)
uuid-dev (1.2-1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1)
liblame-dev (3.96.1-2ubuntu1)
libfaad2-0 (2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3)
libfaad2-dev (2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3)
xmms-mp4 (2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3)
ffmpeg (3:0.cvs20060823-3.1ubuntu4)
ffmpeg2theora (0.16-2build1)
libavcodec-dev (3:0.cvs20060823-3.1ubuntu4)
libdc1394-13-dev (1.1.0-3ubuntu2)
libdts-dev (0.0.2-svn-1ubuntu2)
libgsm1-dev (1.0.10-13)
libpostproc-dev (3:0.cvs20060823-3.1ubuntu4)
libpostproc0 (1:1.0-pre1.1)
libxxf86vm-dev (1:1.0.1-2)
x11proto-xf86vidmode-dev (2.2.2-4ubuntu1)
faac (1.24clean-0ubuntu4)
gstreamer0.8-faac (0.8.12-2ubuntu1)
libxext-dev (2:1.0.3-1build1)
libxv-dev (2:1.0.1-3ubuntu2)
x11proto-video-dev (2.2.2-4ubuntu1)
x11proto-xext-dev (7.0.2-5ubuntu1)

You can find all the packages through SYNAPTIC.

**2. Compiling and installing x264**

I did exactly as chainzz! (see quoted text)
 
**3. Compiling and installing Cinelerra**

I got the latest revision of Cinelerra not from svn://cvs.cinelerra.org/repos/cinelerra/trunk/hvirtual
but from ```
svn checkout svn://svn.skolelinux.org/cinelerra/trunk/hvirtual
```
I also edited autogen.sh, 
```

gedit autogen.sh

```
but as from Ubuntu 7.04, Feisty Fawn! Version I changed the file as follow:
```

# export AUTOMAKE=/usr/bin/automake-1.7
# export ACLOCAL=/usr/bin/aclocal-1.7

to

export AUTOMAKE=/usr/bin/automake-1.9
export ACLOCAL=/usr/bin/aclocal-1.9

```

In the next step I added to ./configure the option with external ffmpeg as I had some compiling problems with the internal version, so:
```

./autogen.sh
./configure --with-external-ffmpeg
make

```
 This way I got a perfect ./configure:
```

Summary of mandatory components:
  libogg                  found
  libvorbis               found
  libvorbisenc            found
  libvorbisfile           found
  libtheora               found
  OpenEXR                 found
  libdv                   found
  libpng                  found
  libjpeg libraries       found
  libjpeg headers         found
  libtiff libraries       found
  libtiff headers         found
  FreeType 2              found
  libx264 libraries       found
  libx264 headers         found
  libuuid libraries       found
  libuuid headers         found
  mjpegtools              found
  libfftw3 libraries      found
  libfftw3 headers        found
  liba52 libraries        found
  liba52 headers          found
  libmp3lame libraries    found
  libmp3lame headers      found
  libsndfile libraries    found
  libsndfile headers      found
  libfaac libraries       found
  libfaac headers         found
  libfaad libraries       found
  libfaad headers         found

Summary of optional components:
  ESD subsystem           missing
ESD (Enlightenment Sound Daemon) is disabled
  ALSA subsystem          found
ALSA is enabled
  libraw1394              found
  libiec61883             found
  libavc1394 libraries    found
  libavc1394 headers      found
  librom1394 libraries    found
  librom1394 headers      found
Firewire is enabled
  OpenGL 2.0 libraries    found
Hardware acceleration using OpenGL 2.0 is enabled

Now type
          make

to start compilation.

```

And make compiled the whole without erros :D

Now the checkinstall. I changed the suggested versionstring because  with it, it refused to compile the debian package:
```

root@12monkeys:/usr/local/src/cinelerra/hvirtual# checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@12monkeys ]
1 -  Summary: [ Cinelerra on 64-bit Ubuntu ]
2 -  Name:    [ hvirtual ]
3 -  Version: [ 2.1
2.1
2.1
2.1
2.1
2.1 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ hvirtual ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

{snap a lot of code}

./ChangeLog
./README.BUILD
./README.cinelerra_rpm

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package

Do you want to see the log file?  [y]: 

(this is the log):
dpkg-deb: Fehler beim Parsen, in Datei »/var/tmp/gAlPVkbZFWrgenXdWVYAV/package/DEBIAN/control« nahe Zeile 8 Paket »hvirtual«:
 Zeilenvorschub im Feldnamen »2.1«

```
so I did as follow:
```

root@12monkeys:/usr/local/src/cinelerra/hvirtual# checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@12monkeys ]
1 -  Summary: [ Cinelerra on 64-bit Ubuntu ]
2 -  Name:    [ hvirtual ]
3 -  Version: [ 2.1
2.1
2.1
2.1
2.1
2.1 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ hvirtual ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 3
Enter new version: 
>> 2.1

This package will be built according to these values: 

0 -  Maintainer: [ root@12monkeys ]
1 -  Summary: [ Cinelerra on 64-bit Ubuntu ]
2 -  Name:    [ hvirtual ]
3 -  Version: [ 2.1 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ hvirtual ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

{snap a lot of code}

./ChangeLog
./README.BUILD
./README.cinelerra_rpm

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Writing backup package...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /usr/local/src/cinelerra/hvirtual/hvirtual_2.1-1_amd64.deb

 You can remove it from your system anytime using: 

      dpkg -r hvirtual

**********************************************************************

```

Now execute:
```

root@12monkeys:/usr/local/src/cinelerra/hvirtual# ldconfig

```

And now you should be ready to run your cinelerra :D

If you want to avoid all the compilng job, you can install the debian package I mentioned at the beginning.
But you maybe will have to install all the files I needed to compile it as well, as I am not sure, if they are also needed to work with cinelerra. 
FFMPEG is needed anyway as I compiled the package --with-external-ffmpeg.
So excuse my english and I hope you will find this further explanation useful.

---

### Post by cotcot on 2007-10-07
I could not get cinelerra with [[COLOR="Red"]svn checkout svn://cvs.cinelerra.org/repos/cinelerra/trunk/hvirtual[/COLOR]]("svn checkout svn://cvs.cinelerra.org/repos/cinelerra/trunk/hvirtual")

I got it with [[COLOR="Red"]svn checkout svn://svn.skolelinux.org/cinelerra/trunk/hvirtual[/COLOR]]("svn checkout svn://svn.skolelinux.org/cinelerra/trunk/hvirtual")

---

### Post by benlooi on 2007-10-07
Took me a whole day to get cinelerra running on my Ubuntu Fiesty / Dell Vostro 1000.
I followed the main steps recommended, and bumped into a few problems. Searched around here and googled thru, and managed to go round the problems.

The first brick I hit (well, one of the first real brick anyway) was the compilation error of cinelerra. Had a fcdt-mmx error, so I did this:
gedit ./configure 

did a search for "mmx", and changed the line that said 
"enable-mmx=auto" to "enable-mmx=no"

That worked fine. Managed to have a successful ./configure run.

The next problem was the checkinstall. It failed, and when I looked at the log, it said something about error in line .... 2.1.  Followed a thread here and changed the line 3 to 2.1, and hey, it's fine!

Of course, it still failed the checkinstall, and the error log now mentioned something about superuser permission needed for dkpginstall. Couldn't find any thing after 1/2 an hour of searching, so I did the last-ditch thing before smashing my computer -
I entered this: sudo dkpg -i *.deb

and hey hey hey! It worked! Went on with sudo cinelerra, and can almost see the tears of joy rolling down my face when the cinelerra windows started flying onto my screen (compizfusion rocks!)

Not too sure if this is helpful to anyone out there, but hopefully it helps. Now I need to give my Cinelerra a test run...


ben
singapore

---

### Post by cotcot on 2007-10-14
I had to install "nasm" to overcome this error :
> .libs/fdct_mmx.o: No such file or directory
> make[2]: *** [libmpeg2enc.la] Error 1

I followed this way of solving to overcome the error in the quote :
> For some reason there was a problem just on the AMD64 system. It is
> probably just a temporary problem with the state of cinelerra-cvs or with
> the way my system was configured. I got the following error:
> make[4]: Leaving directory `/home/dfort/cinelerra-cvs/cinelerra/hvirtual/po'
> : --update de.po cinelerra.pot
> rm -f de.gmo && : -c --statistics -o de.gmo de.po
> mv: cannot stat `t-de.gmo': No such file or directory
> make[3]: *** [de.gmo] Error 1
> make[3]: Leaving directory `/home/dfort/cinelerra-cvs/cinelerra/hvirtual/po'
> make[2]: *** [stamp-po] Error 2
> make[2]: Leaving directory `/home/dfort/cinelerra-cvs/cinelerra/hvirtual/po'
> make[1]: *** [all-recursive] Error 1
> make[1]: Leaving directory `/home/dfort/test/cinelerra/hvirtual'
> make: *** [all] Error 2
> 
> It isn't good to go on after a make error like this. What I did may have
> been a bad thing, but since I'm only going to use English it probably
> didn't do any harm:
> $touch po/de.gmo
> $touch po/es.gmo
> $touch po/sl.gmo
> $touch po/fr.gmo

I have now cinelerra compiled on an AMD64 with OpenGL enabled.

Thanks for the tutorial. It was helpful.

---

### Post by Guzz on 2008-05-09
When i try to download the x264 code with svn i get this message

guzz@darthvader:~$ svn checkout svn://svn.videolan.org/x264/trunk x264
Área de autenticação: <svn://svn.videolan.org:3690> df754926-b1dd-0310-bc7b-ec298dee348c
Password for 'guzz': 

and my sistem password doesnt work
can anybody help me?

---

### Post by klark.crente on 2008-05-29
Hello! I had the same problem that the user above. When launching "svn co svn: / / svn.videolan.org/x264/trunk x264-r536" I asked a username and a password that know. Thank you. Taking advantage, someone knows if this compilation solve the problems of locking in the cinelerra GUI? Thanks!
:)

---

### Post by vjktm on 2008-06-30
Folks,
I am stuck.  checkinstall aborts after the following lines.  It looks like something to do with libquicktimehv but I don't know how to solve it.  
Thanks in advance for any pointers.

....
libquicktimehv.lax/libencore.a/putvlc.o
ranlib .libs/libquicktimehv.a
rm -fr .libs/libquicktimehv.lax
creating libquicktimehv.la
(cd .libs && rm -f libquicktimehv.la && ln -s ../libquicktimehv.la libquicktimehv.la)
/usr/bin/install -c .libs/libquicktimehv.lai /usr/local/lib/libquicktimehv.la
/usr/bin/install -c .libs/libquicktimehv.a /usr/local/lib/libquicktimehv.a
chmod 644 /usr/local/lib/libquicktimehv.a
chmod: changing permissions of `/usr/local/lib/libquicktimehv.a': No such file or directory
make[3]: *** [install-libLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/vj/hvirtual/quicktime'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/vj/hvirtual/quicktime'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/vj/hvirtual/quicktime'
make: *** [install-recursive] Error 1

---

### Post by vjktm on 2008-07-01
All,
Thank you very much for all the pointers in this thread.

I finally got it to compile and run.

After I installed all the dependencies.
I used 
sudo ./configure --disable-mmx
sudo make
sudo checkinstall
(used 2.1 for version)
sudo ldconfig

---

