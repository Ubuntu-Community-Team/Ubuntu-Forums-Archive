---
title: "HowTo: Encode Video for iPod Video"
date: 2006-01-09
forum: Outdated Tutorials &amp; Tips
---

### Post by endersshadow on 2006-01-09
------**Last Update**------
January 1, 2008: Started the New Year off with minor changes.  Modified the installed packages for Gutsy and the FFMPEG SVN configure commands for the latest SVN.
------------------------

After much searching and about a week of on and off again attempts, I finally got video to encode for my iPod Video.  So, I thought I'd share with you how.

This HowTo is broken up into three sections:
Vive
Transferring Video to the iPod Video
Encoding Video to the iPod Video

[size=6]**Vive**[/size]

[Vive](http://vive.sourceforge.net) is the project that stemmed out of this HowTo.  It is a GUI for ffmpeg, but has presets already loaded for the iPod (just for you!).  Downloads can be found [here](http://sourceforge.net/project/showfiles.php?group_id=158461).

Currently, 2.0.0-beta1 is released, or you can use the SVN version.  I always make sure that it runs before I commit to the SVN, so that would be the recommended way to go about it.  Here's how to install it (you need to install ffmpeg first, so see below for it):

```
sudo apt-get install vobcopy mplayer libgtk2.0-dev libvte-dev libgnome2-dev libgnomeui-dev
```

If you want DVD support, you need to do the following.  If you do not want it, you must use the --disable-dvd flag for ./configure.
```
sudo apt-get install libdvdcss2-dev libdvdnav-dev libdvdread-dev
```

Next, installation is rather simple (assuming you get the package either via the [released package](https://sourceforge.net/project/showfiles.php?group_id=158461), or via the [SVN](https://sourceforge.net/svn/?group_id=158461).
```
./configure --prefix=/usr
make
sudo make install
```

Also, if you'd like the preloaded presets, please do the following:
```
mkdir ~/.vive
cp examples/preferences ~/.vive
```

[size="6"]**Transferring Video to the iPod Video**[/size]

You will need to use [gtkpod](http://gtkpod.sourceforge.net) to transfer your files to your iPod.  It's only one command:

```
sudo apt-get install gtkpod-aac
```

This provides the ability to load video and audio that use the AAC sound codec, and it's also built with MPEG4 support.  If anybody remembers the old instructions, this is MUCH easier.

Congratulations, you can now transfer videos to your iPod Video :-D

[size="6"]**Encoding Video for the iPod Video**[/size]

**[color=red]Dapper Packages!!![/color]**
SBX has been kind enough to create .deb packages for ffmpeg and Vive for Dapper.  You can get them [here](http://skulboxx.com/Ubuntu/sbx/) and install them both with sudo dpkg -i packagename.deb.  Thanks so much to SBX for this contribution!

In order to encode video for the iPod Video, you need to install ffmpeg from source because it does not come with the support needed for the iPod Video format for a litany of legal reasons concerning the distribution of Ubuntu.  Luckily, this is still very legal, and you are not breaking any law in the United States or anywhere else by configuring and installing ffmpeg in this way.  This section of the guide is broken into two subsections:

1. Installing ffmpeg
2. ipodvidenc Script

The ipodvidenc Script is a simple bash script written by me to make encoding videos for the iPod Video quick and painless.  Now, without further interruption, how to encode video for the iPod Video:

[size=5]**Installing ffmpeg**[/size]

First, we need to fix ffmpeg for Ubuntu.  We'll build it from source...but don't worry, it won't hurt.  We'll also need to install some other libraries.  So, here goes:

```
sudo apt-get install liblame-dev libxvidcore4-dev libx264-dev libfaac-dev libfaad2-dev liba52-dev libdc1394-dev libgsm1-dev libtheora-dev libvorbis-dev
sudo apt-get build-dep ffmpeg
```

There are 2 ways to do this.  The version in the Ubuntu repositories does **not** have x264 support correct.  You get an error in the ffmpeg code when you try to compile it.  This can be averted by using the SVN version of ffmpeg.  However, there are different flags to use, so the first one is using the ffmpeg in the repos (aka no x264), and the second is via the SVN (aka with x264).

**Without x264:**
```
apt-get source ffmpeg
cd ffmpeg-*/
./configure --enable-gpl --enable-pp --enable-vorbis \
	--enable-libogg --enable-a52 --enable-dts \
	--enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
	--enable-faad --enable-faac --enable-xvid --enable-pthreads --enable-shared
make
sudo make install
```

**With x264:**
```
sudo apt-get install subversion
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg/
./configure --prefix=/usr --enable-gpl --enable-pp --enable-pthreads --enable-libdc1394 --enable-liba52 --enable-libfaac \
--enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libtheora --enable-libvorbis \
--enable-libx264 --enable-libxvid --enable-shared --disable-debug
make
sudo make install
```

You're done!  You can now enjoy ffmpeg!

[size=5]**ipodvidenc Script**[/size]

And last, but certainly not least, you can create a script for converting your videos to iPod Video format.

```
gedit
```

This should pop up a blank document. Now, just copy and paste this code into it:

```
#!/bin/bash
## ipodvidenc - The iPod Video Encoder for Linux.
## Created by Eric Hewitt, January 9, 2006.
## Released under the GPL.  Go nuts.

input_file=$1

echo "What would you like to name the output file (sans extension)?"

read output_file_name

echo "$output_file_name will be located in $PWD. Is this acceptable? [y/n]"

read output_file_loc_permis

if [ $output_file_loc_permis = 'n' ] || [ $output_file_loc_permis = 'N' ]
then
	echo "Where would you like to store $output_file_name.mov?"
	read output_dir
else
	output_dir=$PWD
fi

ffmpeg -i "${input_file}" -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 "${output_dir}/${output_file_name}.mov"
```

Save as ipodvidenc in your present working directory (it will be moved, anyway).  Back in the terminal, run:

```
chmod 755 ipodvidenc
sudo mv ipodvidenc /usr/bin
```

Now, when you want to encode a video to iPod format, run this command:

```
ipodvidenc video.avi
```

It will run you through a few prompts and then encode the video.  You can now use gtkpod to upload the video onto your iPod just like you load mp3's onto it.

*Note: You can now use ipodvidenc to encode straight from a *.vob file.  This way, you can rip your DVDs using dvd::rip, and then simply encode them by passing them through ipodvidenc.  Make sure that you compile ffmpeg with a52 support in order to do this, though.

This is a very basic script if you do not want the much larger and GUI version of ipodvidenc which can be found attached.

[size=5]**Fixing Video for the 60GB iPod v1.1 Firmware**[/size]

In the new firmware for the 60GB iPods, video will play for 15 seconds, stop, and then continue without audio.  If this happens to you, you need to install gpac, like this:

```
sudo apt-get install gpac
```

You can then remux the video so that it will work on your iPod using the following command:

```
MP4Box -add videofile.mov videofile.mov
```

A note: You can use the same name for the input and the output...it will simply overwrite the existing file.

Happy encoding!

[size=6]**Credits:**[/size]
**Original Sources:**
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=108255](http://ubuntuforums.org/showthread.php?t=108255)
[*][http://clug.net.nz/index.php/IpodSupportUnderLinux](http://clug.net.nz/index.php/IpodSupportUnderLinux)
[*]A page that I can't find right now that supplied me with the correct ffmpeg command...I'd really like to give credit to them, but I can't seem to find it.  If anybody finds it, let me know, and I'll update this to give them full credit.[/LIST]

**Much thanks to:**
[LIST]
[*][Iandefor](http://ubuntuforums.org/member.php?u=39464) for countless suggestions, bugfixes, and corrections.
[*][Dromio](http://ubuntuforums.org/member.php?u=10869) for corrections.
[*][quietglow](http://ubuntuforums.org/member.php?u=33815) for corrections and the .deb support for mpeg4ip
[*][pestilence4hr](http://ubuntuforums.org/member.php?u=9507) for corrections regarding the building of ffmpeg
[*][hal pacino](http://ubuntuforums.org/member.php?u=59888) for the info about MP4Box
[*]SBX for the Dapper packages.
[*][Sir_Yaro](http://ubuntuforums.org/member.php?u=51286) for information about the mpeg4ip error correction.
[/LIST]

---

### Post by endersshadow on 2006-01-11
Update: Now on the [Wiki](https://wiki.ubuntu.com/iPodVideo) :-D

I've decided to make this post the Change Log, so here it is:

------------------------
Updated: January 1, 2008: Started the New Year off with minor changes.  Modified the installed packages for Gutsy and the FFMPEG SVN configure commands for the latest SVN.
Updated: July 20, 2007: Huge news!  Vive 2.0.0 has finally been released!  Download it [here](https://sourceforge.net/project/showfiles.php?group_id=158461)!  Also, an Ubuntu Feisty package has been added.  I suggest that you use the [Medibuntu](http://medibuntu.org) repository to meet the dependencies, as the Ubuntu package is compiled to allow DVD usage.  Enjoy!
Updated: July 11, 2007: Vive 2.0.0-beta2 is now available!  New features include multiple file and folder support, a simplified and streamlined interface, and a lot of behind the scenes stuff that makes me sleep better at night but you won't notice unless you look at the code.  So [download it today](https://sourceforge.net/project/showfiles.php?group_id=158461)!
Updated: June 1, 2007: Fixed some legacy issues with the bitrate handling of ffmpeg (used to be in kb/s, now in b/s) for the script and ipodvidenc, which is now v1.6.
Updated: April 20th, 2007: Major update for Feisty & Edgy - MUCH EASIER!!!
Updated: December 12th, 2006: ffmpeg configure altered to support H.264 format.
Updated: November 7th, 2006: Post updated with tweaks so that it will work on Edgy.
Updated: October 2nd, 2006: Released Vive 1.0.2 as a bug-fix release.  You can find it on [Sourceforge](http://sourceforge.net/project/showfiles.php?group_id=158461).
Updated: September 20th, 2006: Released Vive 1.0.1 to fix the configure script.
Updated: September 18th, 2006: Released Vive 1.0.0.  Check it out at [http://vive.sourceforge.net](http://vive.sourceforge.net)!  Note: It will detect a previous version of Vive and update it accordingly without deleting any of your previously saved preferences!
Updated: June 4th, 2006: Released Vive 0.3 Beta 2 Release.  Check it out at [http://vive.sourceforge.net](http://vive.sourceforge.net)!  Note: It will detect a previous version of Vive and update it accordingly without deleting any of your previously saved preferences!
Updated: May 21st, 2006: Added error correction for mpeg4ip thanks to Sir_Yaro. Also added the shameless self promotion of Vive.
Updated: April 30th, 2006: Okay, I know that it's been a while, but here are some updates.  First, SBX gave us Dapper packages of Vive and ffmpeg.  Go SBX.  Second, I found out that the XML Perl Parser is in the repos...I'm an idiot...so I included it.  Third, I added how to remux videos for the 60GB iPod v1.1 Firmware, and much thanks to hal pacino for that.  I haven't forgotten about Vive...I'm just really busy, but it's almost ready for 0.3 to be unleashed...I went back and rewrote most of the code to make it a bit better.
Updated: March 23rd, 2006: I've released [Vive 0.2 (Beta Release)](http://vive.sourceforge.net), and have attached a screenshot of the main window and the preferences window!
Updated: February 27th, 2006: I've released [Vive](http://vive.sourceforge.net), and have attached a screenshot!
Updated: February 10th, 2006: Updated install script and HowTo to correct libgpod installation issues, as well as added to the HowTo and the Wiki the same information.
Updated: January 26th, 2006: Updated iPod Video Encoder to version 1.5 to include OGM support as requested [here](http://ubuntuforums.org/showthread.php?p=682988#post682988).
Updated: January 25th, 2006: Updated iPod Video Encoder to version 1.4.  There are so many new features, that I'm just including the full change log:

NEW: Added default videos directory option.
NEW: Added CLI interface.
NEW: Added support for standard size AVI encoding.
NEW: Added support for standard size MPEG encoding.
NEW: Added a preview feature.
NEW: Added help file. (Access via ipodvidenc -h).
IMPROVED: Condensed the installation to one script that automatically detects your previous level of installation.
IMPROVED: Uninstall script updated.
BUG FIX: Inability to remove original files with spaces in the name bug fixed.
BUG FIX: Overwriting existing files bug fixed.
Updated: January 24th, 2006: Updated iPod Video Encoder to version 1.3 to fix a couple of bugs and add a new feature, options, to cut down on the number of dialogs in the ripping and encoding process.
Updated: January 23rd, 2006: Updated iPod Video Encoder and HowTo to correct some ffmpeg configuration errors. Also added some features/improvements and bug fixes to iPod Video Encoder. See attached README file for a detailed list of changes to iPod Video Encoder
Updated: January 17th, 2006: Updated HowTo and iPod Video Encoder (to v1.1) to use dpkg-buildpackage to build ffmpeg. Much thanks to [pestilence4hr](http://ubuntuforums.org/member.php?u=9507), who brought this to my attention! 
Updated: January 16th, 2006: Added iPod Video Encoder (ipodvidenc), the GUI to make iPod Videos.
Updated: January 14th, 2006: Added .deb package for mpeg4ip and updated format of the HowTo as well as the Sources.  Also editted the title.
Updated: January 13th, 2006: Added support for encoding vob files, and ipodvidenc script modified slightly for optimization. Also corrected the commands to install mpeg4ip.
Updated: January 12th, 2006: Corrected commands associated with compiling and installing mpeg4ip.
------------------------

---

### Post by Iandefor on 2006-01-12
Good guide. I'll do it someday, when I get a 5th generation iPod. Until then, I'll adapt it to my *cough* encoding needs.

---

### Post by sbaush on 2006-01-12
Thanks for this howto that i've aked for!!!
You're great!!

---

### Post by endersshadow on 2006-01-12
Quite welcome...and trust me, I'm not that great...just a guy who was determined to get his iPod Video to work on Ubuntu :KS

---

### Post by Dromio on 2006-01-12
Thanks for the tutorial.  I'm having some trouble getting the dependencies installed.  

sudo apt-get install libfaad2-dev libfaac-dev libxvidcore4-dev checkinstall fakeroot
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxvidcore4-dev: Depends: libxvidcore4 (= 2:1.0.3-0.0) but 2:1.1.0-beta1-0.0 is to be installed
E: Broken packages

I don't think I've done anything to get a special version of libxvidcore4, but I suppose it is possible.  Do you have any suggestions on how to fix this?

---

### Post by Dromio on 2006-01-12
I got synaptic to pin the older version of libxvidcore4, so I'm ok with that now.

But now I'm getting confused while compiling and installing mpeg4ip.

It looks to me like
```
[FONT=monospace]
[/FONT]cp mpeg4ip_config.h mpeg4ip_version.h /usr/local/include[FONT=monospace]
[/FONT]cp include/mpeg4ip.h /usr/local/include

```
should actually be 
```

sudo cp mpeg4ip_config.h /usr/local/include

[FONT=monospace] [/FONT]sudo cp include/mpeg4ip.h include/mpeg4ip_version.h /usr/local/include
 
```
(need to be superuser to copy to /usr/local/include and the mpe4ip_version.h file is actually under the include folder in the source)

Then, you edit the makefile for the lib/mp4v2 subfolder.  Do you compile within that subfolder, or go back to the root folder to compile everything?  When it asks for a package name, it's suggesting mp4v2, which seems a far cry from mpeg4ip.

---

### Post by endersshadow on 2006-01-12
All apologies...you're right, it does need to be sudo.

*And* you need to do the configure, make, and install from the main mpeg4ip directory.  I'll update the HowTo.

I apologize...as I said, it was a long time of me trying different things, and then finally getting to work, and then I had to sort through my .bash_history file to get all the correct commands...sorry for that!

---

### Post by endersshadow on 2006-01-13
Update: Added instructions on how to convert straight from raw vob files.  Note that if you've followed this HowTo before, you just need to do:

```
sudo apt-get install liba52-0.7.4 liba52-0.7.4-dev
```

Then add the line:

```
confflags += --enable-a52
```

To the debian/rules file in the ffmpeg source directory.  Then in the ffmpeg source directory run:

```
./configure && make && sudo make install
```

You'll be all set :)

---

### Post by putte30 on 2006-01-13
Getting dependency problem with "sudo apt-get build-dep ffmpeg", any idea?

Been looking for a guide like this for months, thanks man. :)

---

### Post by endersshadow on 2006-01-13
[QUOTE=putte30]Getting dependency problem with "sudo apt-get build-dep ffmpeg", any idea?

Been looking for a guide like this for months, thanks man. :)[/QUOTE]

Post your full output here, so we know what the error is.  I'll try to get back to it today, but I'm moving back to school today, so bear with me :-D

And you're welcome.

---

### Post by Dromio on 2006-01-13
No need to apologize, I understand how hard this must have been to get together.

As a stickler, here's a couple of corrections:

```

sudo cp mpeg4ip_config.h mpeg4ip_version.h /usr/local/include
sudo cp include/mpeg4ip.h /usr/local/include

```
should actually be 
```

sudo cp mpeg4ip_config.h /usr/local/include
 sudo cp include/mpeg4ip.h include/mpeg4ip_version.h  /usr/local/include

```

And when you put in 
```

cd ../
make
sudo checkinstall -D make install

```
you should actually be going up 2 levels:
```

cd ../..
make
sudo checkinstall -D make install

```

---

### Post by Dromio on 2006-01-13
I'm still have trouble compiling mpeg4ip.  I must be missing some dependency:

> 
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_init':
: undefined reference to `dts_init'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame':
: undefined reference to `dts_frame'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame':
: undefined reference to `dts_blocks_num'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame':
: undefined reference to `dts_block'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame':
: undefined reference to `dts_samples'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame':
: undefined reference to `dts_blocks_num'
/usr/lib/libavcodec.a(dtsdec.o): In function `dts_decode_frame':
: undefined reference to `dts_syncinfo'
/usr/lib/libavcodec.a(oggtheora.o): In function `Theora_decode_frame':
: undefined reference to `theora_decode_packetin'
/usr/lib/libavcodec.a(oggtheora.o): In function `Theora_decode_frame':
: undefined reference to `theora_decode_YUVout'
/usr/lib/libavcodec.a(oggtheora.o): In function `Theora_decode_end':
: undefined reference to `theora_info_clear'
/usr/lib/libavcodec.a(oggtheora.o): In function `Theora_decode_end':
: undefined reference to `theora_comment_clear'
/usr/lib/libavcodec.a(oggtheora.o): In function `Theora_decode_init':
: undefined reference to `theora_info_init'
/usr/lib/libavcodec.a(oggtheora.o): In function `Theora_decode_init':
: undefined reference to `theora_decode_header'
/usr/lib/libavcodec.a(oggtheora.o): In function `Theora_decode_init':
: undefined reference to `theora_decode_init'
/usr/lib/libavcodec.a(libgsm.o): In function `libgsm_init':
: undefined reference to `gsm_create'
/usr/lib/libavcodec.a(libgsm.o): In function `libgsm_close':
: undefined reference to `gsm_destroy'
/usr/lib/libavcodec.a(libgsm.o): In function `libgsm_encode_frame':
: undefined reference to `gsm_encode'
/usr/lib/libavcodec.a(libgsm.o): In function `libgsm_decode_frame':
: undefined reference to `gsm_decode'
collect2: ld returned 1 exit status


Anyone have any idea what could be missing?

---

### Post by putte30 on 2006-01-13
[QUOTE=endersshadow]Post your full output here, so we know what the error is.  I'll try to get back to it today, but I'm moving back to school today, so bear with me :-D

And you're welcome.[/QUOTE]

Im getting :

Observe, choosing liba52-0.7.4-dev instead of liba52-dev

Builddependency for ffmpeg could not be satisfied.

(Translated from Swedish ;) )

Also problem with :

The following packages have unmet dependencies:
libxvidcore4-dev: Depends: libxvidcore4 (= 2:1.0.3-0.0) but 2:1.1.0-beta1-0.0 is to be installed
E: Broken packages


Something missing in my sources.list?

---

### Post by Dromio on 2006-01-13
[quote=putte30]
The following packages have unmet dependencies:
libxvidcore4-dev: Depends: libxvidcore4 (= 2:1.0.3-0.0) but 2:1.1.0-beta1-0.0 is to be installed
E: Broken packages
[/quote] 
I had this issue as well.  It looks like the libxvidcore4-dev package is currently broken.  You have to set apt to "pin" to the older version of libxvidcore4.  I don't know how to do this using apt, but in Synaptic you just select the package and choose Package >> Force Version.

---

### Post by Dromio on 2006-01-13
I solved my compile issue by removing libavcodec-dev from my system.  Now on to the next step. . .

---

### Post by Dromio on 2006-01-13
I finally made it through and have gtkpod running!  

I could not find libgpod in any of my repositories.  Instead, I got it from picpac's post in  [this thread]("http://ubuntuforums.org/showthread.php?t=104937").

I have to wait to actually try it out until I get home and can plug in the ipod.

---

### Post by quietglow on 2006-01-13
Not to derail the excellent conversation, but I thought I'd share. I've been holding back on picking up a 5G but this thread finally pushed me over the edge: I just got back from picking one up! I'm going to use this guide to start doing my own conversions in a bit. Right now I'm just enjoying the 8 zillion video podcasts via itunes. Man this thing rocks!

Don't underestimate the influence of your good work!

---

### Post by endersshadow on 2006-01-13
Dirmo, thanks for your input.  I've updated the HowTo.

As I said, I tried to piece together everything after I found it worked...it's a shame that I didn't take any notes...

And quietglow, you're quite welcome...I'm happy a few people can benefit from it.

---

### Post by daigorobr on 2006-01-14
First of all, great guide, man. I don't own an iPod but all the info on ffmpeg and its tricks are useful for PSP encoding.
My question is: all my videos encoded in MP4 format with AAC audio seem to crash Nautilus (right clicking it and going to Properties). I though it was something I did wrong, but I saw that downloaded videos from Google Video for the PSP also do it.
Does it happen with iPod videos? Can somebody confirm and reproduce it?

---

### Post by putte30 on 2006-01-14
Anyone got a solution for my problem? :confused: 

Observe, choosing liba52-0.7.4-dev instead of liba52-dev

Builddependency for ffmpeg could not be satisfied.

(Translated from Swedish )

Solved! The problem was a conflikt with Kubuntu, I uninstalled it and now it works!

---

### Post by quietglow on 2006-01-14
Again, wonderful guide!

Just a note that may save someone some serious messing around time:

If you don't already have a /usr/local/include folder, you need to make one before you start this whole process:

```
sudo mkdir /usr/local/include
```

If you don't, when you do this:

```
sudo cp mpeg4ip_config.h /usr/local/include
```

You'll get a file (not a directory) with the content of mpeg4ip_config.h. 

This will cause havoc with your compiler!

---

### Post by quietglow on 2006-01-14
I know this is cheating, but after my third unsucessful attempt to compile mpeg4ip I got desperate and found this:

[http://rarewares.org/debian/packages/unstable/mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb](http://rarewares.org/debian/packages/unstable/mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb)

Compiled gtkpod and I have video transfer! Now on to converting my own stuff...

---

### Post by endersshadow on 2006-01-14
[QUOTE=quietglow]I know this is cheating, but after my third unsucessful attempt to compile mpeg4ip I got desperate and found this:

[http://rarewares.org/debian/packages/unstable/mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb](http://rarewares.org/debian/packages/unstable/mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb)

Compiled gtkpod and I have video transfer! Now on to converting my own stuff...[/QUOTE]

That's not cheating, that's just what you call "better" haha.

I'll post it in the guide as an alternative, because I know that mpeg4ip is a pain and a half sometimes with dependencies and the like.

Thanks!!!

Oh, and a quick sneak peak into what I'm working on now: A program to rip straight from DVD to iPod format.  Stay tuned :-D

---

### Post by quietglow on 2006-01-14
> Oh, and a quick sneak peak into what I'm working on now: A program to rip straight from DVD to iPod format. Stay tuned 

Man that would rock! I'm finally getting round to watching some podcasts (diggnation rules) and would LOVE to be able to go directly from DVD to ipod. Imagine the Family Guy episodes!

---

### Post by Iandefor on 2006-01-16
[quote=quietglow]Man that would rock! I'm finally getting round to watching some podcasts (diggnation rules) and would LOVE to be able to go directly from DVD to ipod. Imagine the Family Guy episodes![/quote] Don't just stop at Family Guy! Go for something like Invader Zim or Neverwhere!

---

### Post by endersshadow on 2006-01-16
As promised, I've written the GUI for this.

Check it out in the original post :-D

---

### Post by Iandefor on 2006-01-16
And don't forget to mention you need vobcopy for the encoding script to work :-D!

---

### Post by endersshadow on 2006-01-16
[QUOTE=Iandefor]And don't forget to mention you need vobcopy for the encoding script to work :-D![/QUOTE]

I added it to the install scripts to automatically install it.

Thanks for the heads up!

Edit: It uses cpdvd, as well.  I added the apt-get install in the scripts, as well.

vobcopy and cpdvd are installed in both the baseinstall and install scripts.

Thanks Iandafor!

Another edit: Added a question dialog asking if you would like to delete the VOB...again, thanks to Iandafor :)

---

### Post by pestilence4hr on 2006-01-17
Since you are modifying debian/rules, shouldn't you be building with

```
fakeroot dpkg-buildpackage
```

Doing ./configure && make doesn't pick up the options that you modified debian/rules to specify.

---

### Post by endersshadow on 2006-01-17
[QUOTE=pestilence4hr]Since you are modifying debian/rules, shouldn't you be building with

```
fakeroot dpkg-buildpackage
```

Doing ./configure && make doesn't pick up the options that you modified debian/rules to specify.[/QUOTE]

Updated the program, the HowTo, and the Wiki.

Thank you!

---

### Post by Iandefor on 2006-01-17
[QUOTE=endersshadow]I added it to the install scripts to automatically install it.

Thanks for the heads up!

Edit: It uses cpdvd, as well.  I added the apt-get install in the scripts, as well.

vobcopy and cpdvd are installed in both the baseinstall and install scripts.

Thanks Iandafor!

Another edit: Added a question dialog asking if you would like to delete the VOB...again, thanks to Iandafor :)[/QUOTE] Very much welcome. Anything to help a "friend" :-D.

---

### Post by pestilence4hr on 2006-01-17
[QUOTE=endersshadow]
Thank you![/QUOTE]

No problem, I'm glad you wrote this guide.  I have a question that perhaps you can answer.  Should a video encoded in this manner be transferrable to the ipod through itunes in windows?  (I skipped the mpeg4ip and gtkpod step, since I don't own an ipod and the person I am encoding for doesn't run linux)  

Perhaps I did something wrong, and maybe it doesn't help that I have to first transcode from rmvb using mencoder to something that ffmpeg can transcode.  But quicktime won't play it and itunes won't transfer it to the ipod.  Maybe I'll have to get the ipod here and hook it up to gtkpod ;)

---

### Post by endersshadow on 2006-01-18
[QUOTE=pestilence4hr]No problem, I'm glad you wrote this guide.  I have a question that perhaps you can answer.  Should a video encoded in this manner be transferrable to the ipod through itunes in windows?  (I skipped the mpeg4ip and gtkpod step, since I don't own an ipod and the person I am encoding for doesn't run linux)  

Perhaps I did something wrong, and maybe it doesn't help that I have to first transcode from rmvb using mencoder to something that ffmpeg can transcode.  But quicktime won't play it and itunes won't transfer it to the ipod.  Maybe I'll have to get the ipod here and hook it up to gtkpod ;)[/QUOTE]

In theory, it should work...but I don't know, I don't have a Windows computer at my disposal.

But note that gtkpod will not recognize an iTunesDB that was created with iTunes...gtkpod still has a ways to go in development before it's totally interoperable...unfortunately :-|

---

### Post by Heliode on 2006-01-18
[QUOTE=endersshadow]
But note that gtkpod will not recognize an iTunesDB that was created with iTunes...gtkpod still has a ways to go in development before it's totally interoperable...unfortunately :-|[/QUOTE]

Well, I regularly use iTunes as well as GTKPod, but all I get from GTKPod after using iTunes is this:

```
iTunesDB '/media/ipod/iPod_Control/iTunes/iTunesDB' does not match checksum in extended information file '/media/ipod/iPod_Control/iTunes/iTunesDB.ext'
gtkpod will try to match the information using MD5 checksums. This may take a long time.
```

And after a while everything is fine 
(the "a long time" part is greatly exaggerated

---

### Post by endersshadow on 2006-01-18
[QUOTE=Heliode]Well, I regularly use iTunes as well as GTKPod, but all I get from GTKPod after using iTunes is this:

```
iTunesDB '/media/ipod/iPod_Control/iTunes/iTunesDB' does not match checksum in extended information file '/media/ipod/iPod_Control/iTunes/iTunesDB.ext'
gtkpod will try to match the information using MD5 checksums. This may take a long time.
```

And after a while everything is fine 
(the "a long time" part is greatly exaggerated[/QUOTE]

It's cracking an MD5 sum...which...in many cases, does take a long time :-D

---

### Post by Heliode on 2006-01-19
Doesn't even take a minute on my PC. The only thing GTKpod screws up for me is the top-25 most played list, which it fills with whatever I last copied onto the pod...

---

### Post by endersshadow on 2006-01-19
[QUOTE=Heliode]Doesn't even take a minute on my PC. The only thing GTKpod screws up for me is the top-25 most played list, which it fills with whatever I last copied onto the pod...[/QUOTE]

Cool! This is good info to know, thank you!

Heliode, could you perhaps test the uploading of videos encoded by ffmpeg in Ubuntu using iTunes in Windows?

---

### Post by Heliode on 2006-01-19
[QUOTE=endersshadow]Cool! This is good info to know, thank you!

Heliode, could you perhaps test the uploading of videos encoded by ffmpeg in Ubuntu using iTunes in Windows?[/QUOTE]

Don't have an iPod Video, just an iPod Photo. And I don't feel like ponying up another $300 :p 

Your howto was useful for me to get the latest version of GTKPod running though... the older one was a bit buggy.

---

### Post by hatstand on 2006-01-19
Have follwed the howto and I get the app in my menu and all seems to work but it doesn't make videos!

I looked into the config log and was told that libgopd was not found.

So I downloaded libgpod.
Cant configure it: het this message:
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool


Help!

---

### Post by endersshadow on 2006-01-20
[QUOTE=hatstand]Have follwed the howto and I get the app in my menu and all seems to work but it doesn't make videos!

I looked into the config log and was told that libgopd was not found.

So I downloaded libgpod.
Cant configure it: het this message:
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool


Help![/QUOTE]

[http://ubuntuforums.org/showpost.php?p=282843&postcount=2](http://ubuntuforums.org/showpost.php?p=282843&postcount=2)

[QUOTE=SGC]To install the XML parser, run the following command:
```

sudo perl -MCPAN -e shell

```

When asked to do a manual configuration, type **no**

At  the**cpan>** prompt type:
```

install XML::Parser

```

After the installation complete, type **exit** and try to install gnomeicu and gnome-ppp again[/QUOTE]

That should fix the problem :-D

---

### Post by juantxorena on 2006-01-20
When I try to encode a video I get this:
```
What would you like to name the output file (sans extension)?
Cradle\ Of\ Filth\ -\ From\ The\ Cradle\ To\ Enslave
Cradle Of Filth - From The Cradle To Enslave will be located in /home/juantxorena/Incoming/videos. Is this acceptable? [y/n]

/usr/bin/ipodvidenc: line 16: [: =: unary operator expected
/usr/bin/ipodvidenc: line 16: [: =: unary operator expected
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
Cradle: I/O error occured
Usually that means that input file is truncated and/or corrupted.
```
I can watch videos with Xine properlly. Help?

---

### Post by endersshadow on 2006-01-20
[QUOTE=juantxorena]When I try to encode a video I get this:
```
What would you like to name the output file (sans extension)?
Cradle\ Of\ Filth\ -\ From\ The\ Cradle\ To\ Enslave
Cradle Of Filth - From The Cradle To Enslave will be located in /home/juantxorena/Incoming/videos. Is this acceptable? [y/n]

/usr/bin/ipodvidenc: line 16: [: =: unary operator expected
/usr/bin/ipodvidenc: line 16: [: =: unary operator expected
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
Cradle: I/O error occured
Usually that means that input file is truncated and/or corrupted.
```
I can watch videos with Xine properlly. Help?[/QUOTE]

Try naming it without spaces.

I believe that this is a limitation with bash...as I said, I whipped this script up quickly...it's rough around the edges, but it works...

When I get some time to do it, I'll improve it a lot...but for now you have to work with bash :-|

Sorry.

---

### Post by Iandefor on 2006-01-20
[quote=endersshadow]Try naming it without spaces.

I believe that this is a limitation with bash...as I said, I whipped this script up quickly...it's rough around the edges, but it works...

When I get some time to do it, I'll improve it a lot...but for now you have to work with bash :-|

Sorry.[/quote] He could also try enclosing the filename in quotes. I think bash is interpreting the spaces to be seperate files.

---

### Post by riiidaa on 2006-01-20
[B]Guys,

I get the video successfuly encoded dialog but i also have no .mov in the destination  folder, ran it from command line to find out this:
[/B]
riiidaa@flag:~/downloaded-files$ ipodvidenc /home/riiidaa/downloaded-files/24se1 ep1.avi
Encode a video

(gnome-terminal:822): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible
GTK Accessibility Module initialized
**sorted this one**

(gnome-terminal:822): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible

**Sorry I'm a noob, please help :confused:**

---

### Post by juantxorena on 2006-01-21
I got this when trying to convert a .avi video without spaces in the name (both output and input):
```
What would you like to name the output file (sans extension)?
cradle_of_filth_-_her_ghost_in_the_fog
cradle_of_filth_-_her_ghost_in_the_fog will be located in /home/juantxorena/Incoming/videos. Is this acceptable? [y/n]
/usr/bin/ipodvidenc: line 16: [: =: unary operator expected
/usr/bin/ipodvidenc: line 16: [: =: unary operator expected
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
Input #0, avi, from 'Cradle_of_Filth_-_Her_Ghost_In_The_Fog.avi':
  Duration: 00:04:32.8, start: 0.000000, bitrate: 925 kb/s
  Stream #0.0: Video: msmpeg4, yuv420p, 352x288, 25.00 fps
  Stream #0.1: Audio: wmav2, 44100 Hz, stereo, 64 kb/s
Unknown codec 'aac'
```
I tried to convert it to mpg using ffmpeg and it works, so ffmpeg works. :???:

---

### Post by endersshadow on 2006-01-21
[QUOTE=riiidaa][B]Guys,

I get the video successfuly encoded dialog but i also have no .mov in the destination  folder, ran it from command line to find out this:
[/B]
riiidaa@flag:~/downloaded-files$ ipodvidenc /home/riiidaa/downloaded-files/24se1 ep1.avi
Encode a video

(gnome-terminal:822): Gnome-WARNING **: Accessibility: failed to find module 'libgail-gnome' which is needed to make this application accessible
GTK Accessibility Module initialized
**sorted this one**

(gnome-terminal:822): Gnome-WARNING **: Accessibility: failed to find module 'libatk-bridge' which is needed to make this application accessible

**Sorry I'm a noob, please help :confused:**[/QUOTE]

Try calling it using this command, instead:

```
ipodvidenc /home/riiidaa/downloaded-files/24se1\ ep1.avi
```

You have to escape the space with a \

**juantxorena:** You haven't compiled ffmpeg with AAC support.  You need to make sure that ffmpeg is compiled with the --enable-faac flag.

---

### Post by riiidaa on 2006-01-21
[QUOTE=endersshadow]Try calling it using this command, instead:

```
ipodvidenc /home/riiidaa/downloaded-files/24se1\ ep1.avi
```

You have to escape the space with a \
[/QUOTE]

Thanks but the 'libatk-bridge' issue is nothing to do with spaces in file names, I've tried using many diff source videos, and after reading the other posts I can see spaces in file names do cause problems, so made sure to try using files that don't have any.

Still looking for a resolution to my libatk-bridge nightmare - it's getting me down :mad: lol

Great work on the ipod vid project btw

---

### Post by riiidaa on 2006-01-21
[QUOTE=riiidaa]Still looking for a resolution to my libatk-bridge nightmare - it's getting me down :mad: lol

Great work on the ipod vid project btw[/QUOTE]

HEY, I solved this by installing the at-spi package.


BUT now it produces no error warnings and still no output file, any ideas?

---

### Post by endersshadow on 2006-01-21
I noticed that you're using Kubuntu, so see if you can encode the video manually with this command:

ffmpeg -i infile.avi -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 outfile.mov

If not, post the error messages.  The GUI program was written for Gnome :-|

---

### Post by endersshadow on 2006-01-21
Itchy trigger finger...duplicate post :-|

---

### Post by hatstand on 2006-01-21
I have a problem with this.  I followed the instruction on this How To and it installed ipodvidenc OK, but when I try to encode a video file (have tried .avi so far), it guides me through the script but does nothing. The terminal flashes open for about .5 seconds, but no script is seen on it. Then I get the "successfully encoded" message and reques to delete the orignal, which I do.

No new film appears in the target folder and the old file still exists, yet ipodvidenc tells me that everything was succesful.

So i followed the instructions in the Wiki for ffmpeg and reinstalled ipodvidenc. Same results. i cannot use ffmpeg as I get this error:

$ ffmpeg -i filmmontealban.avi -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 output_file.
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
filmmontealban.avi: I/O error occured
Usually that means that input file is truncated and/or corrupted.
mat@ubuntu:~$ ffmpeg -i film montealban.avi -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 output_file.
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
film: I/O error occured
Usually that means that input file is truncated and/or corrupted.

As you can see, I tried it with and without spaces in the title, and from the directory that contains it. I changed the name to monte.avi and got a different message:

Input #0, avi, from 'monte.avi':
  Duration: 00:00:11.0, start: 0.000000, bitrate: 1247 kb/s
  Stream #0.0: Video: mjpeg, yuvj422p, 320x240, 10.00 fps
  Stream #0.1: Audio: pcm_u8, 8000 Hz, mono, 64 kb/s
Unknown codec 'aac'

---

### Post by endersshadow on 2006-01-23
[QUOTE=hatstand]I have a problem with this.  I followed the instruction on this How To and it installed ipodvidenc OK, but when I try to encode a video file (have tried .avi so far), it guides me through the script but does nothing. The terminal flashes open for about .5 seconds, but no script is seen on it. Then I get the "successfully encoded" message and reques to delete the orignal, which I do.

No new film appears in the target folder and the old file still exists, yet ipodvidenc tells me that everything was succesful.

So i followed the instructions in the Wiki for ffmpeg and reinstalled ipodvidenc. Same results. i cannot use ffmpeg as I get this error:

$ ffmpeg -i filmmontealban.avi -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 output_file.
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
filmmontealban.avi: I/O error occured
Usually that means that input file is truncated and/or corrupted.
mat@ubuntu:~$ ffmpeg -i film montealban.avi -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 output_file.
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
film: I/O error occured
Usually that means that input file is truncated and/or corrupted.

As you can see, I tried it with and without spaces in the title, and from the directory that contains it. I changed the name to monte.avi and got a different message:

Input #0, avi, from 'monte.avi':
  Duration: 00:00:11.0, start: 0.000000, bitrate: 1247 kb/s
  Stream #0.0: Video: mjpeg, yuvj422p, 320x240, 10.00 fps
  Stream #0.1: Audio: pcm_u8, 8000 Hz, mono, 64 kb/s
Unknown codec 'aac'[/QUOTE]

Do the following in the terminal:

```
cd ~/.ipodvidenc/install/ffmpeg-*cvs*/
./configure --enable-gpl --enable-pp --enable-zlib --enable-vorbis \
	--enable-libogg --enable-theora --enable-a52 --enable-dts \
	--enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
	--enable-faad --enable-faac --enable-xvid --enable-a52
make
sudo make install
```

Then try it again.  The first one was due to the spaces...I'm working on fixing that bug...

---

### Post by endersshadow on 2006-01-23
I've updated iPod Video Encoder to v1.2 to fix a few bugs, and I added support for spaces in file names.

Also, I updated the install script...if you're having problems with ffmpeg, please run the full install or upgrade script to install.  If you're encoding just fine, please just run the base install script for installation.

---

### Post by hatstand on 2006-01-23
[QUOTE=endersshadow]Do the following in the terminal:

```
cd ~/.ipodvidenc/install/ffmpeg-*cvs*/
./configure --enable-gpl --enable-pp --enable-zlib --enable-vorbis \
	--enable-libogg --enable-theora --enable-a52 --enable-dts \
	--enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
	--enable-faad --enable-faac --enable-xvid --enable-a52
make
sudo make install
```

Then try it again.  The first one was due to the spaces...I'm working on fixing that bug...[/QUOTE]

It works! Perserverence and constant pestering pays off!

Endersshadow (btw, I love Ender's Game), YOU ARE THE MAN!

many, many thanks!:D

---

### Post by endersshadow on 2006-01-23
All right hatstand!  Glad to hear somebody else got this working! :-D

Oh, and also, I updated iPodVidEnc...I uploaded it earlier and then ran off to class and in class I sat there thinking to myself, "Oh boy...I uploaded the bugged devel version," and sure enough I did.  So, if you've installed version 1.2, just redownload it and do the base install and all will be fine!

---

### Post by Iandefor on 2006-01-24
Just an update/testimonial: after working with Endersshadow, we found a few problems in ipovidenc 1.2 which were quickly corrected. Ender has updated the script to 1.3. Get it on the guide! It's hot off the griddle!

Oh, and it's even working for me, who seems to have had the most trouble getting ffmpeg to work. Thanks again, Ender!

---

### Post by endersshadow on 2006-01-25
Because I finally got it to work for Iandefor, I started adding features like crazy.  Now, we're up to version 1.4 and it's better than ever!

Here's the full change log:

NEW: Added default videos directory option.
NEW: Added CLI interface.
NEW: Added support for standard size AVI encoding.
NEW: Added support for standard size MPEG encoding.
NEW: Added a preview feature.
NEW: Added help file. (Access via ipodvidenc -h).
IMPROVED: Condensed the installation to one script that automatically detects your previous level of installation.
IMPROVED: Uninstall script updated.
BUG FIX: Inability to remove original files with spaces in the name bug fixed.
BUG FIX: Overwriting existing files bug fixed.

As you can see, I've been busy...and I'm happy to release this version...it's awesome :-D

---

### Post by Iandefor on 2006-01-25
Ender, you're crazy, but I love ya anyways for making such an awesome script :-D! The new features just make it soo much better! Thanks ten billion times over!

---

### Post by quietglow on 2006-01-26
Oh man do you rock ender...

I'm thinking that this weekend if I can get some time, I'm going to try to put together a script which will pull video out of my MythTV folder at a specified time and then pass it on to ipodvidenc. I'm dreaming of waking up every morning to a video iPod synced to whatever I Myth-ed (doesn't have the ring of Tivo'd) the day before!

---

### Post by endersshadow on 2006-01-26
[QUOTE=quietglow]Oh man do you rock ender...

I'm thinking that this weekend if I can get some time, I'm going to try to put together a script which will pull video out of my MythTV folder at a specified time and then pass it on to ipodvidenc. I'm dreaming of waking up every morning to a video iPod synced to whatever I Myth-ed (doesn't have the ring of Tivo'd) the day before![/QUOTE]

Shouldn't be too hard...just use the command:

```
ipodvidenc -c ipod moviein.avi movieout.mov
```

:-D

---

### Post by riiidaa on 2006-01-28
[QUOTE=endersshadow]I noticed that you're using Kubuntu, so see if you can encode the video manually with this command:

ffmpeg -i infile.avi -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 outfile.mov

If not, post the error messages.  The GUI program was written for Gnome :-|[/QUOTE]

Oops, was going to switch to kde after installing but desided to stick with Gnome.

I'll try your latest version from the top this weekend and hopefully it will produce .mov's :)

---

### Post by Vincent_Lin on 2006-01-31
Hi,

I just purchased a VideoPod (not received yet) but I decided not to put money into buying a QuickTime license to do this encoding.  This howto is great!  Easy to follow and it's working in encoding my video colections into VPod format.

One small question:  the script specifies -aspect to be 4:3.  I believe this is due to the screen resolution that vpod has.  Could any one tell me what I should specify if the original video is at the aspect ratio other than 4:3?  Say 720x480 clip that has 3:2, or 16:9 from others?  The first thing I tried this script on a video with 720x480 resolution, is to remove -aspect 4:3, but the result is still the same as if -aspect 4:3 is specified.  Looks like the other option specified -s 320x240 dominates?  The picture looks like it is been squeezed side-way.  Persons look taller, you know, squeezed side-way.

The real question is: what options I could choose if I want to maintain 720x480 (3:2) or 16:9 aspect ratios since I don't mind to have two black bars on both top and bottom parts of the screen?

Thanks.

Vincent Lin

---

### Post by endersshadow on 2006-01-31
[QUOTE=Vincent_Lin]Hi,

I just purchased a VideoPod (not received yet) but I decided not to put money into buying a QuickTime license to do this encoding.  This howto is great!  Easy to follow and it's working in encoding my video colections into VPod format.

One small question:  the script specifies -aspect to be 4:3.  I believe this is due to the screen resolution that vpod has.  Could any one tell me what I should specify if the original video is at the aspect ratio other than 4:3?  Say 720x480 clip that has 3:2, or 16:9 from others?  The first thing I tried this script on a video with 720x480 resolution, is to remove -aspect 4:3, but the result is still the same as if -aspect 4:3 is specified.  Looks like the other option specified -s 320x240 dominates?  The picture looks like it is been squeezed side-way.  Persons look taller, you know, squeezed side-way.

The real question is: what options I could choose if I want to maintain 720x480 (3:2) or 16:9 aspect ratios since I don't mind to have two black bars on both top and bottom parts of the screen?

Thanks.

Vincent Lin[/QUOTE]

Hey Vincent.  Try making the aspect 3:2 instead of 4:3, but leave the size.  The size is important because it's the size of the screen on the iPod.

---

### Post by Vincent_Lin on 2006-01-31
Thanks.  

That's about the only idea I think I would try.

Meanwhile, I am trying your GUI stuff on Gnome, and it works great.  

I used to run DVD::rip to get my DVD collection onto HD, and really, it runs too slow.  I am encoding DVDs on IBM X31 laptop (1.3GHz Centrino), my only fast machine, and it usually takes more than several hours to fully encode a movie, overnight is the way I would put it.  But, with your GUI one, it seems it can be done within the time frame the same as the movie runs.  I did not know transcode can be this slow. Hmmmm

Anyhow, iPod Video Encoder allows me to save the vob file (without deleting it) after the encoding for iPod is done.  How about another option that allows me to specify the encoding options for the result file?  Say the resulting resolution, maybe?  I believe many people will appreciate the convenience and speed this iPod Video Encoder can bring to them (me).

Thanks for the great work that puts all these things together.

Vincent Lin

---

### Post by endersshadow on 2006-01-31
[QUOTE=Vincent_Lin]Thanks.  

That's about the only idea I think I would try.

Meanwhile, I am trying your GUI stuff on Gnome, and it works great.  

I used to run DVD::rip to get my DVD collection onto HD, and really, it runs too slow.  I am encoding DVDs on IBM X31 laptop (1.3GHz Centrino), my only fast machine, and it usually takes more than several hours to fully encode a movie, overnight is the way I would put it.  But, with your GUI one, it seems it can be done within the time frame the same as the movie runs.  I did not know transcode can be this slow. Hmmmm

Anyhow, iPod Video Encoder allows me to save the vob file (without deleting it) after the encoding for iPod is done.  How about another option that allows me to specify the encoding options for the result file?  Say the resulting resolution, maybe?  I believe many people will appreciate the convenience and speed this iPod Video Encoder can bring to them (me).

Thanks for the great work that puts all these things together.

Vincent Lin[/QUOTE]

I'm working on that very thing right now.  For now, though, iPod Video Encoder does encode into the default size of the VOB in MPEG, AVI, and OGM formats.

At any rate, I'm working as I can in between everything else on a program that gives video encoding a GUI in Linux...and doesn't suck.  It'll take a little time...but I promise, it's coming :-D

---

### Post by JedTheHead on 2006-02-02
Absolutely smashing!  I have been driving myself nuts trying to accomplish this! 

Thank you!!!

NOTE:  I had dvdrip and transcode installed previously which cause the ffmpeg deps to not build.  Specifically liba5 as previously stated in this fourm.  I removed the offending library and these instructions worked flawlessly!

Thanks again!

---

### Post by endersshadow on 2006-02-02
[QUOTE=JedTheHead]Absolutely smashing!  I have been driving myself nuts trying to accomplish this! 

Thank you!!!

NOTE:  I had dvdrip and transcode installed previously which cause the ffmpeg deps to not build.  Specifically liba5 as previously stated in this fourm.  I removed the offending library and these instructions worked flawlessly!

Thanks again![/QUOTE]
Quite welcome, Jed.

Just a quick q: Did you just do sudo apt-get remove liba5 to remove the library?  If so, then I can make sure that it gets into the next version of the install script.

---

### Post by JedTheHead on 2006-02-02
No prob...

Actually I went into Synaptic to take care of it because I wasn't positive what was causing the build-deps to fail concerning liba52-0.7.4

I removed it, which also removed dvdrip, transcode, etc. and then ran the ffmpeg install as outlined in your post.  Once done, and looking at it now, both liba52-0.7.4 and the -dev libraries are installed.  

Hope that helps!

Thanks again!

---

### Post by jacrider on 2006-02-03
Love this HowTo, and I really want to get my video iPod hooked up to my Ubuntu box.  

I am stuck at the install of libgpod.  

Doesn't find it with a apt-get command.

I then found the message to install it manually, but the perl installation of the XML fails.

Any ideas on how to get libgpod another way?

Thanks again for a great HowTo.  Must have taken a ton of time as the scripts were very long and involved.

Thanks.

---

### Post by endersshadow on 2006-02-03
[QUOTE=jacrider]Love this HowTo, and I really want to get my video iPod hooked up to my Ubuntu box.  

I am stuck at the install of libgpod.  

Doesn't find it with a apt-get command.

I then found the message to install it manually, but the perl installation of the XML fails.

Any ideas on how to get libgpod another way?

Thanks again for a great HowTo.  Must have taken a ton of time as the scripts were very long and involved.

Thanks.[/QUOTE]

Can you post your error message here so that I can get a better idea of how to help you?

Thanks :)

---

### Post by jacrider on 2006-02-04
Ok, I found a post on the XML installation that led me to another lib file needed.  After installing that, the perl XML install went ok.

I finished up the rest of the install and all seems great.

New problem.  I started to encode a DVD to move it to my iPod and the encoder stopped with an error.  There was no error in the log file, but the process stopped at 4096MB.  Am I missing something about file sizes?

The encoded file plays wonderfully, but ends 75% of the way through the movie.

Thanks.

---

### Post by jacrider on 2006-02-04
As a follow-up, the encoding was way faster than a windows product (pdqipod or something like that) that I used before.   It was about run-time in length on a faster computer.  This was about 10 or 12 minutes to do the 4GB before failing.

---

### Post by endersshadow on 2006-02-04
Try running from the command line:

```
ipodvidenc -v
```

This will give you the verbose mode.  Vobcopy or ffmpeg should spit out an error if it's not finishing the file.  I've had a bunch of buffer underflows from ffmpeg every now and then, but if you just let it go, it's never been a problem for me...

---

### Post by jacrider on 2006-02-04
In doing some more research, FAT32 has a max file size of 4GB.  Exactly where I the encoding blew up.  I was saving to a FAT32 HD shared by ubuntu and windows.

I will redirect the encoding output to another drive that is ext3.

I will let you know how this works.

---

### Post by jacrider on 2006-02-04
I tried to encode a small file from a DVD and the first process to create the .vob file worked (quickly).  Then the encoding took my preference to iPod and started to work and the following error was recorded in the log file:

```
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr 
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
Input #0, mpeg, from '/media/data/My_Video/Test2-1.vob':
  Duration: 00:06:13.8, start: 0.187978, bitrate: 5253 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480, 29.97 fps, 9800 kb/s
  Stream #0.1[0x20]: Subtitle: dvdsub
  Stream #0.2[0x21]: Subtitle: dvdsub
  Stream #0.3[0x22]: Subtitle: dvdsub
  Stream #0.4[0x80]: Audio: ac3, 48000 Hz, stereo, 192 kb/s
  Stream #0.5[0x81]: Audio: ac3, 48000 Hz, stereo, 192 kb/s
Unknown codec 'aac'
```

Did I mess up the install of ffmpeg?  It looks like I don't have the aac codec.

Thanks.

---

### Post by endersshadow on 2006-02-04
Well, I guess you learn something new every day :lol:

It must have been at the vobcopy part and never even got to ffmpeg.  Your final video should be around 700mb...which FAT32 can handle (which is a good thing, as the iPod Video is a FAT32 drive).

---

### Post by endersshadow on 2006-02-04
[QUOTE=jacrider]I tried to encode a small file from a DVD and the first process to create the .vob file worked (quickly).  Then the encoding took my preference to iPod and started to work and the following error was recorded in the log file:

```
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr 
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
Input #0, mpeg, from '/media/data/My_Video/Test2-1.vob':
  Duration: 00:06:13.8, start: 0.187978, bitrate: 5253 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480, 29.97 fps, 9800 kb/s
  Stream #0.1[0x20]: Subtitle: dvdsub
  Stream #0.2[0x21]: Subtitle: dvdsub
  Stream #0.3[0x22]: Subtitle: dvdsub
  Stream #0.4[0x80]: Audio: ac3, 48000 Hz, stereo, 192 kb/s
  Stream #0.5[0x81]: Audio: ac3, 48000 Hz, stereo, 192 kb/s
Unknown codec 'aac'
```

Did I mess up the install of ffmpeg?  It looks like I don't have the aac codec.

Thanks.[/QUOTE]

ffmpeg was not compiled w/ aac support for whatever reason.  Do this:

```
sudo apt-get install liblame-dev libfaad2-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev
```

Next, go to the ffmpeg source folder, and then run:

```
./configure --enable-gpl --enable-pp --enable-zlib --enable-vorbis \
	--enable-libogg --enable-theora --enable-a52 --enable-dts \
	--enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
	--enable-faad --enable-faac --enable-xvid
make
sudo make install
```

Then try again..

---

### Post by jacrider on 2006-02-04
Thanks for all your assistance.  Everything seems to be working.

I just need to find a bigger ext3 HD space to hold the .vob files.

Great HowTo!

---

### Post by Vincent_Lin on 2006-02-07
jcrider,

How did you resove libgpod issue?  My apt-get could not find it either, as a consequence, gtkpod could not compile.  Could you share the method you get this libgpod installed?

Thanks.

Vincent

ps. I just received my video pod from Amazon, 1 week earlier than promised.  iTunes would not allow me to add movies that were transcoded by ffmpeg, per iPod Video Encoder script.  And I could compile gtkpod with video support.  Just yet.

---

### Post by quietglow on 2006-02-07
I was just setting up a machine this morning and also noticed that libgpod is missing from the repositories. I wonder what the heck is up. If you're interested,  its pretty easy to build from source: check the gtkpod page for info.

---

### Post by endersshadow on 2006-02-07
libgpod is in the Dapper repositories, and you can find the debs [here](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libgpod&searchon=names&subword=1&version=dapper&release=all).

---

### Post by Vincent_Lin on 2006-02-07
Thanks.

I actually downloaded source code from sourceforge and compiled it.  So the whole installation is working.  I had to link libgpod.so from /usr/local/bin to /usr/lib though.

Just one question about gtkpod:  How can I download video encoded using your encoding GUI program?  These .mov files are there, but I can't seem to find the procedure to put it on to my brand video pod?  gtkpod recognises ipod, but I just can't find a way to put .mov onto ipod.

Thanks again.

Vincent

---

### Post by endersshadow on 2006-02-07
Oh, sure...here's how to do it:

Load up gtkpod, hit the Read button.  Then, go to the playlist that you want your video to be in (or none) on the left hand side.  Then hit the button "Add files."  Select your videos, then hit Sync, and you'll be all set!

Oh, and one note on this: You must manually edit the metadata on the files once they are on the iPod to have the length written to it.  Otherwise, you will not be able to scroll through the movie.  This is a limitation of gtkpod, as it does not copy metadata for videos (as of yet).

---

### Post by jacrider on 2006-02-07
Vincent:  I started with this post that has the website to download the source for libgpod:

[http://www.ubuntuforums.org/showthread.php?t=104937&highlight=libgpod](http://www.ubuntuforums.org/showthread.php?t=104937&highlight=libgpod)

Then in order to compile this, I needed to install XML/perl.

I started with this forum topic:

[http://ubuntuforums.org/showthread.php?p=282843#post282843](http://ubuntuforums.org/showthread.php?p=282843#post282843)

but ran into problems, so I had to install another library:

sudo apt-get install libexpat-dev     
(Note: I see a more recent post that says this is now lipexpat1-dev)

Then the instructions in the second thread worked perfectly.

Then, I had the means to install the downloaded package (which is a .deb) file) with the following terminal line:

sudo dpkg -i libgpodxxxxx.deb   (the xxxxx is the version you download)

Then I was done.  If you don't have any luck with gtkpod, you can do the same process.

Good luck.

---

### Post by halfname on 2006-02-07
When I try to get ffmpeg, this is what happens 
```
sudo apt-get build-dep ffmpeg Reading package lists... 
Done Building dependency tree... 
Done E: Build-dependencies for ffmpeg could not be satisfied.

``` 

Can anyone help me with this?

---

### Post by Vincent_Lin on 2006-02-07
Hi, again.

So I fooled around gtkpod with sync, add files, add folders, read, etc..., and eventually those files got copied to ipod.  Honestly, I still did not know what sequence caused the operation to suceed.

Then I went ahead to change metadata of the files on ipod.  

It's the right click on the files/.mov items when ipod is the focus, right?  Select "Edit Details" and change "Play Time" to the actually run-time I got form gxine, apply it, and Quit.  Unit is in minutes.  So 2 hours 20 minutes and 20 seconds run-time would be 140:20.

Then I right-click again to click on "Update", after all tracks/videos have been typed with proper run-time.

Then I click on sync.

Now all the information I typed in gtkpod are transferred to ipod.
(This procedure costs me a couple of hours to figure out.)

And video I encoded with your setting can be played on iPod video.  Hurray!!

Only one problem:  audio will only play about one minute then iPod stops playing the vidoe, for a brief monent.  Then it resumes without audio.  Well, scroll forward a couple ticks and it is in sunc again.  Then it plays a munite or so, then the same drill.  Note: short video (2:35) would not have this behaviour.

Simply can't figure out what happened.  All the video files are from DVD, and they play well under gxine.

So far so good, I would say to myself.  But, Help!!

Thanks all the time and efforts in doing the developing and supporting.  Can't say enough about that!!!


Vincent

---

### Post by hal pacino on 2006-02-08
I have the exact same problem: video pauses and resumes with audio cut out. What's that about?

---

### Post by endersshadow on 2006-02-08
For kicks and giggles, what happens if you don't set the play time?

---

### Post by Vincent_Lin on 2006-02-08
If playtime is not set, I could not sroll (forward / backward) at all.
The display on ipod is always 0:00 and 0:00 when playtime not set.

When playtime is set, it shows the correct run-time at left, and the total play-time at right, as usual song playing would display.

Thanks.

Vincent

---

### Post by endersshadow on 2006-02-08
[QUOTE=Vincent_Lin]If playtime is not set, I could not sroll (forward / backward) at all.
The display on ipod is always 0:00 and 0:00 when playtime not set.

When playtime is set, it shows the correct run-time at left, and the total play-time at right, as usual song playing would display.

Thanks.

Vincent[/QUOTE]

Right, this is to be expected, but does the video play all the way through without interruption?

---

### Post by Vincent_Lin on 2006-02-08
As I described in previous post, video will pause a brief moment (10-15 seconds), and it resumes without audio.  Just scroll a tick or 2 (forward 1 or 2 seconds) will bring back audio, sort of like the old days when software DVD players runs out of sync of video/audio, but a pause or forward/rewind brings it back in sync.

Short video does not have this behaviour (2:35).  

Those videos that have these behaviour are all full feature movies (around 2 hours) encoded from DVDs.  A relatively short film (Glenn Gould Plays Goldberg Variations) with runtime about 58 minutes has this problem too.

All these videos when played on ipod show the current-run-time and total-run-time properly, after play-time information is added, updated, and sync-ed.  Scroll forward/backward updates current-run-time correctly as well.

Thanks.

Vincent

---

### Post by endersshadow on 2006-02-08
[QUOTE=Vincent_Lin]As I described in previous post, video will pause a brief moment (10-15 seconds), and it resumes without audio.  Just scroll a tick or 2 (forward 1 or 2 seconds) will bring back audio, sort of like the old days when software DVD players runs out of sync of video/audio, but a pause or forward/rewind brings it back in sync.

Short video does not have this behaviour (2:35).  

Those videos that have these behaviour are all full feature movies (around 2 hours) encoded from DVDs.  A relatively short film (Glenn Gould Plays Goldberg Variations) with runtime about 58 minutes has this problem too.

All these videos when played on ipod show the current-run-time and total-run-time properly, after play-time information is added, updated, and sync-ed.  Scroll forward/backward updates current-run-time correctly as well.

Thanks.

Vincent[/QUOTE]

I'm going to level with you: I'm totally befuddled...I haven't had the problem nor can I reproduce it, so I haven't been able to play around with it :-|

All apologies...mayhaps someone with more expertise can help...

---

### Post by endersshadow on 2006-02-10
I've updated the HowTo with instructions on how to install the XML Parser and libgpod, and I've updated the install script and Wiki accordingly.

All should be well in iPod Video land :-D

---

### Post by rdwtux on 2006-02-11
Hi, thanks for the great howto.

There seems to be an error with the install script for ipodvidenc.  line 148 and 150 (think that's them) have "if <blah> then;" rather than "if <blah>; then"

I changed it in my copy and all is well. Cept know I'm having dependency hell.. but I'll keep working on that.

---

### Post by endersshadow on 2006-02-11
Thanks for the info...it's fixed.

BTW, what dependency problems are you having?  Hopefully, I can solve them all via the install script, so then people wouldn't have any problems in the future.

Thanks again!

---

### Post by rdwtux on 2006-02-11
I was having huge dependency problems with mpeg4ip so i compiled from source.  Compiling from source seems to have worked for mpeg4ip but FFMPEG is failing now. 

> me@localhost:~/$ sudo apt-get build-dep ffmpeg
Reading package lists... Done
Building dependency tree... Done
E: Build-dependencies for ffmpeg could not be satisfied.


If I skip this step, configure works fine for ffmpeg but then make fails with a syntax error:

> dtsdec.c: At top level:
dtsdec.c:315: error: &#8216;dts_state_t&#8217; undeclared here (not in a function)
dtsdec.c:315: error: syntax error before &#8216;)&#8217; token
make[1]: *** [dtsdec.o] Error 1
make: *** [lib] Error 2



I think automatix might be the root cause of most of my problems. 

I also noticed that in the instructions it didn't say to change the name of libgtkpod-0.3.0 to libgtkpod.

---

### Post by rdwtux on 2006-02-11
OK so it's definately conflicts caused by automatix.

Had to install the following packages via synaptics - removing all conflicts:

libdts-dev
libtheora-dev
libgsm1-dev
libraw1394-dev

Then go back and re-run:
> sudo apt-get build-dep ffmpeg

Then just keep following instructions. I also had to change the recommendation of ffmpeg's version number.  The doc recommends 1.0xxxxx.. i almost immediately got a prompt to update my ffmpeg from ubuntu repositories to 3:0.1cvsxxxxx... so i changed my custom version to "3:1.0csv_custom"

Also, the ffmpeg binaries were installed in /usr/local/bin but the ipodvidenc script looked for them in /usr/bin. so I sym linked all 3 binaries.. but not the best way to do it.  The configure should specify the prefix.

---

### Post by pestilence4hr on 2006-02-11
[QUOTE=Heliode]Don't have an iPod Video, just an iPod Photo. And I don't feel like ponying up another $300 :p 

Your howto was useful for me to get the latest version of GTKPod running though... the older one was a bit buggy.[/QUOTE]

Well, I finally got the windows machine in front of me to test it myself.  Quicktime won't even play the movie, it gives "Error -2048: the file is not a movie file".  I can't seem to even add the movie to itunes.  Could somebody else see if their movie plays with a version of quicktime?  I assume that it should...

It plays just fine in mplayer, and mplayer reports the correct codecs being used.

---

### Post by pestilence4hr on 2006-02-12
Ok, so even though quicktime won't play the file, and itunes won't do anything with it, transferring it over to the ipod using gtkpod worked perfectly.  The video plays great on the ipod.  Great howto!

---

### Post by endersshadow on 2006-02-12
The source of this problem w/ Quicktime and/or iTunes could be that the file has no metadata other than length.  Not for any real lack of knowing how to do it, it's just unnecessary w/ gtkpod because gtkpod doesn't transfer metadata of the videos (which is why you need to manually put in the length of the video in gtkpod).

rdwtux: Were the conflicts caused by Automatix just the fact that these files weren't installed: libdts-dev, libtheora-dev, libgsm1-dev, libraw1394-dev? If so, I'll include them in the install file.

---

### Post by rdwtux on 2006-02-12
[QUOTE=endersshadow]
rdwtux: Were the conflicts caused by Automatix just the fact that these files weren't installed: libdts-dev, libtheora-dev, libgsm1-dev, libraw1394-dev? If so, I'll include them in the install file.[/QUOTE]

Well they probably should be included in your script, as ffmpeg won't compile without them.  But Automatix seems to have installed some video libs that conflict with libdts-dev and libtheora-dev. So I basically had to uninstall each offending lib/app.  I had to uninstall all the way down to totem.. then reinstall what I needed from OFFICIAL ubuntu repositories later.

I've read many people complaining about Automatix and it really shouldn't be used as it modifies your source.list file... but it was useful.  Now I understand the repercusions.

---

### Post by endersshadow on 2006-02-12
[QUOTE=rdwtux]Well they probably should be included in your script, as ffmpeg won't compile without them.  But Automatix seems to have installed some video libs that conflict with libdts-dev and libtheora-dev. So I basically had to uninstall each offending lib/app.  I had to uninstall all the way down to totem.. then reinstall what I needed from OFFICIAL ubuntu repositories later.

I've read many people complaining about Automatix and it really shouldn't be used as it modifies your source.list file... but it was useful.  Now I understand the repercusions.[/QUOTE]

The install script changes out your sources.list file and then puts it all back to what you had before when it does it (just using official Ubuntu repositories).  Since they do provide some conflicts that need to be fixed by hand, I suppose that I'll just leave them out...

I've used an earlier version of Automatix and haven't had any problems, though.

---

### Post by rdwtux on 2006-02-14
If I enode an avi file using ffmpeg the way you mention, i get great results.  However if i try to add an MP4 file that was preformatted for the IPOD I generally get an error with gtkpod saying it doesn't understand the format.  

This isn't a huge issue.  I've setup a cron script on my system to automatically encode any video I have in a certain directory during the night.. the next morning I can add it to my ipod. 

But just wondering, can you add MP4 files directly to gtkpod?

---

### Post by endersshadow on 2006-02-14
[QUOTE=rdwtux]If I enode an avi file using ffmpeg the way you mention, i get great results.  However if i try to add an MP4 file that was preformatted for the IPOD I generally get an error with gtkpod saying it doesn't understand the format.  

This isn't a huge issue.  I've setup a cron script on my system to automatically encode any video I have in a certain directory during the night.. the next morning I can add it to my ipod. 

But just wondering, can you add MP4 files directly to gtkpod?[/QUOTE]

Rename the file to .mov.  For some reason, gtkpod doesn't play nice with .mp4 files.

---

### Post by rdwtux on 2006-02-14
[QUOTE=endersshadow]Rename the file to .mov.  For some reason, gtkpod doesn't play nice with .mp4 files.[/QUOTE]

*LAFF*  do you know how many hours I've spent re-encoding The Family Guy because of this! hehe.

I just figured it was an encoding issue.  *slap*

Thanks.

---

### Post by hal pacino on 2006-02-16
I'm still having the pausing problem of the video playing for a few seconds fine and then pausing itself and then playing with no sound. HELP!!!

---

### Post by rdwtux on 2006-02-16
I'm not having any issues with pausing/no audio.  However another guy here at work who has a 5G video and only uses itunes has the same issue your mentioning.  You might want to see if it's actually an ipod issue rather than a gtkpod/ffmpeg issue. 

He started having issues when he upgraded to firmware 1.1, however i'm running 1.1. without issues.

---

### Post by endersshadow on 2006-02-16
Try rebooting the iPod.  Press and hold the menu and the center button simultaneously until you get a glowing apple logo.

---

### Post by rdwtux on 2006-02-16
Found the problem with video playing for 10 seconds and then freezing, then no audio. 

It's a problem with the 1.1 firmware on the 60GB Ipod (i just exchanged my 30gb for the 60gb and had the same issue). 

Basically you have to downgrade the firmware on the 60gb ipod from 1.1 to 1.0.  This does not affect the 30gb ipod apparently. 

Here's the original thread: 
[http://digg.com/apple/iPod_Update_Causing_Major_Headache_for_Some_Video_Owners](http://digg.com/apple/iPod_Update_Causing_Major_Headache_for_Some_Video_Owners)

Here are the steps (copied from thread - i tried it and it works fine): 
> 
1. Download iPodWizard here:
sourceforge.net/project/showfiles.php?group_id=153441
(download the release, top link of the two)

2. Extract the files, and launch the program.

3. Put in your Original CD,
On The iPodWizard, Click Open Updater..
point to the CD, Program Files/ iPod/ updater exe

4. Click Load on the iPodWizard

5. Click on DownGrade Firmware

6. Exit the Wizard

7. Open the iPodupdater directly from CD/ Program Files/ iPod/ Updater.exe
it will said ur iPod is OutDated 1.1

Click Update... instead of Restore....

and u will be back to 1.0



---

### Post by endersshadow on 2006-02-16
Okay, just would like to say:

Woot. Not my fault!

---

### Post by Edward The Bonobo on 2006-02-17
I had a problem with the Make on the HowTo.  See this thread, where I've pasted what I got in my terminal. [http://www.ubuntuforums.org/showthread.php?t=127542](http://www.ubuntuforums.org/showthread.php?t=127542)

Can anyone help?  (In relative newbie language, I'm afraid)

---

### Post by Vincent_Lin on 2006-02-17
Count me in for the video stop and then audio cut off victim.

Reverting back to iPod software 1.0 from CD (I have to use a Windows PC to do so) brings my iPod back to the whole glory.  Unfortunately that I have to do restore instead of Update options, since update option is greyed out.  No matter, transferring files "only" took about 2 hours.  I had 19Gig music, 15 Gig photos, and 8 Gig .mov files, and growing and growing.

Anyhow, thanks to all, especially Endersshadow for this wonderful Howto and scripts.

I am watching Cats, the DVD which I purchased back in 1998, encoded by this wonderful scripts and put onto my iPod video.

A very happy ubuntu user,

Vincent Lin

BTW, specifying -aspect 16x9 in ffmpeg does encode those wide-screen clips into a better looking .mov file.  Thanks.  Can't say more about Thanks.

---

### Post by KingOfNowhere on 2006-02-19
hey, endersshadow, great guide. 

just one question, when i encode videos with ipodvidenc i cannot move forward/backward though the playback on my ipod. what would you recommend to fix this?

---

### Post by endersshadow on 2006-02-19
[QUOTE=KingOfNowhere]hey, endersshadow, great guide. 

just one question, when i encode videos with ipodvidenc i cannot move forward/backward though the playback on my ipod. what would you recommend to fix this?[/QUOTE]

In gtkpod, you need to edit the metadata (right click on the video, and select properties) and manually enter in the length (in minutes:seconds, so if you had a clip 2 hours, 28 minutes, 32 seconds, it would be 148:32 instead of 2:28:32).  This is only because gtkpod is not able to pull the metadata from any video file, and one of the things that the devel of it is working very hard on doing.

---

### Post by chronusdark on 2006-02-23
is there anyway to modify this script to do batch reencodings (ie all the video files in a directory at once)

also i was wondering about reencoding ogg and mkv with dual audio for ipod...(selecting only the english audio track)

thanks

---

### Post by endersshadow on 2006-02-27
[QUOTE=chronusdark]is there anyway to modify this script to do batch reencodings (ie all the video files in a directory at once)

also i was wondering about reencoding ogg and mkv with dual audio for ipod...(selecting only the english audio track)

thanks[/QUOTE]

Other than making a for loop, I'm not sure about the first.

As for the second, I'm not exactly sure what you mean, but it's late...however, you may need to hack the script or run a custom command...

---

### Post by endersshadow on 2006-02-27
Introducing...[VIVE](http://vive.sourceforge.net) - the cohesive GUI for encoding videos for the iPod Video!!!  I've attached a screenshot, and I've updated the main post...it took a lot of work, and my eyes are about to fall out, but it's finally ready for release :-D

---

### Post by beaucollins on 2006-02-27
I just tried to install and I get this (there's a syntax error or something):

beau@optimus:~/ipodvidenc$ ./install
mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb
gtkpod-0.99.2
gtkpod-0.99.2.tar.gz
cat: /home/beau/.ipodvidenc/install/ffmpeg-*/debian/rules: No such file or directory
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources
Fetched 4B in 1s (2B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
vobcopy is already the newest version.
cpdvd is already the newest version.
ogmtools is already the newest version.
build-essential is already the newest version.
make is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
./install: line 153: syntax error near unexpected token `else'
./install: line 153: `          else'

---

### Post by endersshadow on 2006-02-27
Lines 146-156 of the install file should read as follows:

```
		if make; then
			if sudo make install; then
				echo "ffmpeg installed correctly."
			else
				echo "ffmpeg not configured correctly."
				exit 1
			fi
		else
			echo "ffmpeg not configured correctly."
			exit 1
		fi
```

What do you have?

---

### Post by moebis on 2006-02-27
[QUOTE=endersshadow]Introducing...[VIVE](http://vive.sourceforge.net) - the cohesive GUI for encoding videos for the iPod Video!!!  I've attached a screenshot, and I've updated the main post...it took a lot of work, and my eyes are about to fall out, but it's finally ready for release :-D[/QUOTE]

First and foremost, GREAT WORK! You are adding to a much needed cause in the Ubuntu community (our love for iPods).

I'm running Dapper F4, been experimenting and troubleshooting all those little things to help make this the best release yet, however I can't seem to get your guide to work on it. First it doesn't like to compile ffmpeg, and one that comes with Dapper might already have all the needed parts. So I removed the first few lines of your install script to not detect what ffmpeg I have.... proceeded with the installation and apt-get installed anything else that was missing. Finally got it to run, but when I do an encode it seems to just hang trying to read the DVD. Any ideas suggestions. I'm willing to put the time in to debug this thing for Dapper.

---

### Post by endersshadow on 2006-02-27
[QUOTE=moebis]First and foremost, GREAT WORK! You are adding to a much needed cause in the Ubuntu community (our love for iPods).

I'm running Dapper F4, been experimenting and troubleshooting all those little things to help make this the best release yet, however I can't seem to get your guide to work on it. First it doesn't like to compile ffmpeg, and one that comes with Dapper might already have all the needed parts. So I removed the first few lines of your install script to not detect what ffmpeg I have.... proceeded with the installation and apt-get installed anything else that was missing. Finally got it to run, but when I do an encode it seems to just hang trying to read the DVD. Any ideas suggestions. I'm willing to put the time in to debug this thing for Dapper.[/QUOTE]

Great! I've got two debuggers for Dapper! (Another anonymous buddy will remain so because he screwed up his Xgl/Compiz install on Breezy and was forced to upgrade to Dapper).

Anyway, Vive uses cpdvd to get your DVD results.  I wasn't thinking too clearly when I made that part and just made the default /dev folder for the dvd /dev/dvd and the mount points either /cdrom or /dvd and nothing else (poor choice, and it will be fixed in 0.2)...The code starts on line 273 of the program (/usr/bin/vive).  Keep in mind I'm learning Perl whilst writing this, so my code may be a bit messy.  And I will clean up the install script...I just spent a lot of time getting Vive the program done, the install and the web page were just afterthoughts and I didn't have the time to put into them to make them really good.

---

### Post by marks_linux on 2006-02-27
vive looks fantastic, had some little bugs like having to create the .vive directory and copying vive.xbm to /usr/share? But after mucking around for two days with various other options and not even getting dvdrip to do anything, vive is a godsend!

quick question, when taking a copy of a DVD do you have to do each 'title' seperately. I've got a dvd that shows 4 titles so I started four copies of vive one for each title. but playing back the partial files they look and sound the same.

Am I being really stupid here?

---

### Post by chronusdark on 2006-02-27
i have a question about vive does the encoding bypass the bug from video ipod version 1.1 firmware where the sound drops out?

---

### Post by Vincent_Lin on 2006-02-27
Hi,

Vive looks great!  Thanks a huge bunch!!

I eventually installed it also bypassing the check for ffmpeg, as another person did.  Could I also request another feature?  As I did not see it as an option as original iPod Video Encoder have?  That is to have the option to keep the vob file that vobcopy'd saved.  I am "dreaming" about building my media PC using ubuntu, and I would like to used the resulting vob files to become my DVD "collections".

As to the ipod, while palying video, pauses and resumes without audio issue, it is a known bug, for firmware 1.1 on 60Gig iPod Video only.  A more comprehensive discussion and only solution can be seen here at ipodlounge:
[http://forums.ilounge.com/showthread.php?threadid=143446](http://forums.ilounge.com/showthread.php?threadid=143446)

Thanks again.


Vincent

---

### Post by endersshadow on 2006-02-27
[QUOTE=marks_linux]vive looks fantastic, had some little bugs like having to create the .vive directory and copying vive.xbm to /usr/share? But after mucking around for two days with various other options and not even getting dvdrip to do anything, vive is a godsend!

quick question, when taking a copy of a DVD do you have to do each 'title' seperately. I've got a dvd that shows 4 titles so I started four copies of vive one for each title. but playing back the partial files they look and sound the same.

Am I being really stupid here?[/QUOTE]

As per the install script, this was the sequence of events last night in my head:

"HOLY CRAP!!! IT WORKS!!!!"
...30 seconds later...
"Hmmm...crap...need an install script..."
...30 seconds later...
"Okay, need to improve the web site..."
...30 seconds later...
"Time to tell everyone!"
...30 seconds later...
"Bed!"

As you can tell, I did not spend a ton of time on either the install script nor the web site--something I fully plan to rectify in the coming versions.

As per the DVD titles, I'm not sure what you're doing, but, in theory, that should work.  Let me explain a bit about the way that DVD's are interpretted just as a general FYI...DVD's contain a variety of titles which lead to certain content, say the actual movie, or perhaps a menu, or even a bonus feature (like outtakes, or games, etc.).  Inside titles are chapters which break it up into sections.  So, for example, I have a copy of *Tommy Boy* (the greatest movie ever, not up for debate), and it has 13 or so titles.  However, title #1 is the actual movie, the other 12 are just extra stuff.  Generally, the one you want will be the longest one.  Inside that title are like 30 chapters, but vobcopy ignores chapters and just copies the entire title.  Mayhaps I'll bug the guy who's behind vobcopy and we'll work together on getting chapters integrated...he may be getting some more demand if Vive picks up in popularity.  At any rate, I'm not sure if that spiel helped...but maybe you have a better understanding of what the program does!

[quote=chronusdark]i have a question about vive does the encoding bypass the bug from video ipod version 1.1 firmware where the sound drops out?[/quote]

As Vincent said, this is a bug with Apple's firmware.  Otherwise known as: Not my fault, but I do blame Steve Jobs, or "NMFBIDBSJ".  Okay, made that last thing up, but downgrade to firmware 1.0 and the problem will be gone.

[quote=Vincent_Lin]I eventually installed it also bypassing the check for ffmpeg, as another person did. Could I also request another feature? As I did not see it as an option as original iPod Video Encoder have? That is to have the option to keep the vob file that vobcopy'd saved. I am "dreaming" about building my media PC using ubuntu, and I would like to used the resulting vob files to become my DVD "collections".[/quote]

Fantastic suggestion and that will be included in v0.1.1, I guarantee you.  Sorry for leaving it out!

(BTW, ipodvidenc and vive use the same programs for a backend, so I've sped nothing up, just condensed it all into one GUI :-D)

---

### Post by beaucollins on 2006-02-28
line #146 had to be changed, it was:
			if make then;

I changed to:
			if make; then

and all is good

---

### Post by chronusdark on 2006-03-01
[QUOTE=endersshadow]
As Vincent said, this is a bug with Apple's firmware.  Otherwise known as: Not my fault, but I do blame Steve Jobs, or "NMFBIDBSJ".  Okay, made that last thing up, but downgrade to firmware 1.0 and the problem will be gone.
[/QUOTE]

i hate to change the subject but is there any way to do this without a windows box?

i kinda feel like im being punished for being  brave and going all out linux.

---

### Post by endersshadow on 2006-03-01
[QUOTE=chronusdark]i hate to change the subject but is there any way to do this without a windows box?

i kinda feel like im being punished for being  brave and going all out linux.[/QUOTE]

The only thing I could find on it was this:

[http://armin.emx.at/ipod/update_howto.html](http://armin.emx.at/ipod/update_howto.html)

I'll bring this issue up w/ some of the devels of the community that are working together to make the iPod fully available on Linux, and this will definitely be on the to-do list.

---

### Post by hal pacino on 2006-03-02
It shouldn't be necessary. isquid and I think one other ffmpeg based converter have both released fixes for the 1.1 firmware issue. I guess, the linux community will be there shortly too. Personally, I don't know ffmpeg well enough to know what they did to work around this issue, but I read somewhere that gpac can also work around it by remuxing files.

I hope someone who actually knows what they're doing adds their two cents, as I'm not really a programmer or anything of that sort.

---

### Post by endersshadow on 2006-03-02
[QUOTE=hal pacino]It shouldn't be necessary. isquid and I think one other ffmpeg based converter have both released fixes for the 1.1 firmware issue. I guess, the linux community will be there shortly too. Personally, I don't know ffmpeg well enough to know what they did to work around this issue, but I read somewhere that gpac can also work around it by remuxing files.

I hope someone who actually knows what they're doing adds their two cents, as I'm not really a programmer or anything of that sort.[/QUOTE]

Do you have any articles?

---

### Post by Mark JB on 2006-03-02
I get this error while trying to fix ffmpeg.

mark@ubuntu:~$ apt-get source ffmpeg
E: Opening /etc/apt/sources.list - ifstream::ifstream (13 Permission denied)
E: The list of sources could not be read.

Is it a repositorty problem ? Any ideas ?

---

### Post by endersshadow on 2006-03-02
[QUOTE=Mark JB]I get this error while trying to fix ffmpeg.

mark@ubuntu:~$ apt-get source ffmpeg
E: Opening /etc/apt/sources.list - ifstream::ifstream (13 Permission denied)
E: The list of sources could not be read.

Is it a repositorty problem ? Any ideas ?[/QUOTE]

Try:

```
sudo apt-get source ffmpeg
```

Apt-get requires root :-D

---

### Post by Mark JB on 2006-03-02
[QUOTE=endersshadow]Try:

```
sudo apt-get source ffmpeg
```

Apt-get requires root :-D[/QUOTE]

Cheers mate that now works.

When i enter the make command i get this error though :( 
[PHP]mark@ubuntu:~/ffmpeg-0.cvs20050121$ make
make -C libavcodec all
make[1]: Entering directory `/home/mark/ffmpeg-0.cvs20050121/libavcodec'
gcc -O3 -Wall -Wno-switch  -DHAVE_AV_CONFIG_H -I.. -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE  -c -o bitstream.o bitstream.c
In file included from avcodec.h:14,
                 from bitstream.c:28:
common.h:59: error: array type has incomplete element type
common.h:63: error: array type has incomplete element type
make[1]: *** [bitstream.o] Error 1
make[1]: Leaving directory `/home/mark/ffmpeg-0.cvs20050121/libavcodec'
make: *** [lib] Error 2
[/PHP]

Soory for the noob-ness!

---

### Post by endersshadow on 2006-03-02
[QUOTE=Mark JB]Cheers mate that now works.

When i enter the make command i get this error though :( 
[PHP]mark@ubuntu:~/ffmpeg-0.cvs20050121$ make
make -C libavcodec all
make[1]: Entering directory `/home/mark/ffmpeg-0.cvs20050121/libavcodec'
gcc -O3 -Wall -Wno-switch  -DHAVE_AV_CONFIG_H -I.. -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE  -c -o bitstream.o bitstream.c
In file included from avcodec.h:14,
                 from bitstream.c:28:
common.h:59: error: array type has incomplete element type
common.h:63: error: array type has incomplete element type
make[1]: *** [bitstream.o] Error 1
make[1]: Leaving directory `/home/mark/ffmpeg-0.cvs20050121/libavcodec'
make: *** [lib] Error 2
[/PHP]

Soory for the noob-ness![/QUOTE]

What was the output of your ./configure statement?

---

### Post by Mark JB on 2006-03-02
[QUOTE=endersshadow]What was the output of your ./configure statement?[/QUOTE]

Really sorry but how do i view that, i cant find it in my home directory.

---

### Post by endersshadow on 2006-03-02
[QUOTE=Mark JB]Really sorry but how do i view that, i cant find it in my home directory.[/QUOTE]

```
./configure --enable-gpl --enable-pp --enable-zlib --enable-vorbis \
	--enable-libogg --enable-theora --enable-a52 --enable-dts \
	--enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
	--enable-faad --enable-faac --enable-xvid
```

:-D

---

### Post by Mark JB on 2006-03-02
[QUOTE=endersshadow]```
./configure --enable-gpl --enable-pp --enable-zlib --enable-vorbis \
	--enable-libogg --enable-theora --enable-a52 --enable-dts \
	--enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
	--enable-faad --enable-faac --enable-xvid
```

:-D[/QUOTE]

ah, i get you now, i though u wanted me to look elsewhere :rolleyes: 

[PHP]Install prefix   /usr/local
Source path      /home/mark/ffmpeg-0.cvs20050121
C compiler       gcc
make             make
CPU              x86 (generic)
Big Endian       no
inttypes.h       yes
broken inttypes.h no
MMX enabled      yes
Vector Builtins  no
gprof enabled    no
zlib enabled     yes
mp3lame enabled  yes
vorbis enabled   yes
faad enabled     yes
faadbin enabled  no
faac enabled     yes
xvid enabled     yes
a52 support      yes
a52 dlopened     no
dts support      yes
pp support       yes
debug symbols    no
strip symbols    yes
optimize         yes
shared pp        no
Video hooking    yes
SDL support      yes
risky / patent encumbered codecs yes
Imlib2 support   yes
freetype support yes
Sun medialib support no
pthreads support no
AMR-NB float support no
AMR-NB fixed support no
AMR-WB float support no
network support      yes
IPv6 support         yes
License: GPL
Creating config.mak and config.h
config.h is unchanged
[/PHP]

thats the output mate.:-k

---

### Post by patsissons on 2006-03-03
Not sure if this will help anyone out, but I built an ffmpeg deb file with most of the options enabled.  it's available here.  Honestly I don't know if I set everything up right in the rules file, so use this deb at your own risk.

[http://box.go.dyndns.org/dev/ffmpeg_0.cvs20050918-4ubuntu1_i386.deb](http://box.go.dyndns.org/dev/ffmpeg_0.cvs20050918-4ubuntu1_i386.deb)

On the other side of things, if you already have ffmpeg with aac and mp4 enabled (or managed to get my deb working) then i made a handy script for converting video files to (efficient) ipod format.  This script will shrink the videos down enough such that they are small and managable (and the conversion doesn't take too long either), but not so much that they look like garbage.  I also included my scripts for dvd conversion (you need handbreak tho, which i don't have a deb for).

video2ipod
```

#!/bin/bash
# $1 - video file
ffmpeg -i $1 -f mp4 -vcodec mpeg4 -acodec aac -b 300 -ab 48 -r 15 `basename $1`.mp4

```

dvd2ipod
```

#!/bin/bash
# $1 - output filename
# $2 - title number
handbrake -f mp4 -i /dev/hdd -o $1.mp4 -t $2 -e ffmpeg -E faac -w 320 -r 15 -b 384 -B 48

```

dvd2ipodx (for converting multiple titles, particularily usefull when converting dvd's with multiple tv episodes)
```

#!/bin/bash
# $1 - start title
# $2 - end title
# $3 - base output file name
if [ -z "$3" ]
then
        echo -e "Usage :"
        echo -e "\t$0 start_title end_title output_name\n"
        echo -e "e.g. $0 1 4 myrips"
else
        start=$1
        end=$2
        for (( i=$start; i <= $end; i++ ))
        do
                dvd2ipod $3-$i $i
        done
fi

```

Hopefully these will be beneficial to some of you out there.  Enjoy :)

---

### Post by xmastree on 2006-03-03
Hm... :-k

I tried this with a veiw to making mp4 files for my phone. After downloading and running the install script, fixing the syntax error and running it again, I thought I had it. But... whatever options I try, ffmpeg fails with the same error.

```
Unsupported codec for output stream #0.1
```

And it looks nothing like the screenshot either. :???:

---

### Post by Edward The Bonobo on 2006-03-03
There's been a lot of developments over the last couple of weeks.  Great stuff and I'm sure a lot of people will be very grateful (especially me!)

Suggestion - this would be a good time to take stock and revise the howto wiki to show the simplified process, based on:
[LIST]
[*]ffmpeg install from the deb
[*]Vive
[/LIST]
I'd volunteer myself - but I'm not expert enough and would probably get it wrong.

---

### Post by xmastree on 2006-03-03
I like the idea, then a numpty like me can give it another go and maybe succeed this time. :???:

All I want is to make a couple of MP4s... :-(

---

### Post by rdwtux on 2006-03-03
There's a syntax error in the install script.  The script and HOWTO are great, but both times I've tried it there have been syntax errors in the install script - very hard for average users to use it in this condition as they can't troubleshoot the syntax errors if they don't know programming. 

Line ~149 has an error in the if statement - the semicolon is in the wrong spot.

---

### Post by endersshadow on 2006-03-03
[QUOTE=xmastree]I like the idea, then a numpty like me can give it another go and maybe succeed this time. :???:

All I want is to make a couple of MP4s... :-([/QUOTE]

What's the output if you try this manually:

```
ffmpeg -i infile.avi -f mp4 -vcodec mpeg4 -maxrate 1000 \
		-b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 \
		-acodec aac -ab 192 -s 320x240 -aspect 4:3 outfile.mov
```

Also, let's see this:
```
ffmpeg -formats
```

As per the syntax, I thought I had reuploaded the correct one...but apparently not.  I've uploaded it again...sorry!

As per the wiki, I may add the ffmpeg .deb file, but I'm hesitant to post Vive there.  First and foremost, I don't want to use the Wiki as my personal advertisement.  Secondly, it's still an alpha release.  I will say this: Wait till Alpha Release 2...it's looking awesome...

---

### Post by Mark JB on 2006-03-03
Any ideas with my problem mate ?

Should i try install from the Deb on the previous page ?

---

### Post by endersshadow on 2006-03-03
[QUOTE=Mark JB]Any ideas with my problem mate ?

Should i try install from the Deb on the previous page ?[/QUOTE]

I'm sorry, I completely forgot to address your post.

And yeah, I'd say give it a definite try w/ the deb on that page.

---

### Post by xmastree on 2006-03-03
[QUOTE=endersshadow]What's the output if you try this manually:

```
ffmpeg -i infile.avi -f mp4 -vcodec mpeg4 -maxrate 1000 \
		-b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 \
		-acodec aac -ab 192 -s 320x240 -aspect 4:3 outfile.mov
```[/quote]
```
chris@xmastree:~/Downloaded$ ffmpeg -i gun.wmv -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 outfile.mov

ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --prefix=/usr
  built on Mar  1 2006 22:51:48, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Seems that stream 1 comes from film source: 1000.00 (1000/1) -> 30.00 (30/1)
Input #0, asf, from 'gun.wmv':
  Duration: 00:00:13.9, start: 5.000000, bitrate: 448 kb/s
  Stream #0.0: Audio: wmav2, 32000 Hz, stereo, 48 kb/s
  Stream #0.1: Video: wmv2, yuv420p, 320x240, 1000.00 fps
Output #0, mp4, to 'outfile.mov':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, 30.00 fps, q=3-5, 700 kb/s
  Stream #0.1: Audio: aac, 32000 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
[aac @ 0x8335848]libfaac doesn't support this output format!
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height
```

> Also, let's see this:
```
ffmpeg -formats
```



```
chris@xmastree:~/Downloaded$ ffmpeg - formats

ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --prefix=/usr
  built on Mar  1 2006 22:51:48, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Unable for find a suitable output format for 'pipe:'

chris@xmastree:~/Downloaded$
```

I get the same result if the outfile is .mp4 rather than .mov :confused:

---

### Post by endersshadow on 2006-03-03
Make sure there's no space in -formats --  you put it as:

```
ffmpeg - formats
```

When it should be...

```
ffmpeg -formats
```

---

### Post by hal pacino on 2006-03-04
A possible solution for firmware 1.1 and those who don't use Mac or Windows: [http://www.isquint.org/cgi-bin/ikonboard.cgi?;act=ST;f=2;t=199;&#top](http://www.isquint.org/cgi-bin/ikonboard.cgi?;act=ST;f=2;t=199;&#top) . This forum suggests a workaround by remuxing the files. Would it be possible for someone to write a linux script to remux the files. If so this would be the easiest solution for those of us who don't use MacWin.

Good luck and good linuxing!

---

### Post by xmastree on 2006-03-04
[QUOTE=endersshadow]Make sure there's no space in -formats[/QUOTE]
Oops... :rolleyes: 

```
chris@xmastree:~$ ffmpeg -formats
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --prefix=/usr
  built on Mar  1 2006 22:51:48, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
File formats:
  E 3g2             3gp2 format
  **[COLOR="Red"]E 3gp             3gp format[/COLOR]**
 D  4xm             4X Technologies format
 D  RoQ             Id RoQ format
 DE ac3             raw ac3
 DE alaw            pcm A law format
 DE asf             asf format
  E asf_stream      asf format
 DE au              SUN AU Format
 DE audio_device    audio grab and output
 DE avi             avi format
  E crc             crc testing format
 D  daud            D-Cinema audio format
 D  dc1394          dc1394 A/V grab
 D  dts             raw dts
 DE dv              DV video format
 D  dv1394          dv1394 A/V grab
  E dvd             MPEG2 PS format (DVD VOB)
 D  ea              Electronic Arts Multimedia Format
 DE ffm             ffm format
 D  film_cpk        Sega FILM/CPK format
 D  flic            FLI/FLC animation format
 DE flv             flv format
 DE gif             GIF Animation
 DE h261            raw h261
 DE h263            raw h263
 DE h264            raw H264 video format
 D  idcin           Id CIN format
 DE image           image sequence
 DE image2          image2 sequence
 DE image2pipe      piped image2 sequence
 DE imagepipe       piped image sequence
 D  ipmovie         Interplay MVE format
 DE m4v             raw MPEG4 video format
 D  matroska        Matroska file format
 DE mjpeg           MJPEG video
 DE mmf             mmf format
  E mov             mov format
 D  mov,mp4,m4a,3gp,3g2 QuickTime/MPEG4 format
  E mp2             MPEG audio layer 2
 DE mp3             MPEG audio layer 3
  E mp4             mp4 format
 DE mpeg            MPEG1 System format
  E mpeg1video      MPEG video
  E mpeg2video      MPEG2 video
 DE mpegts          MPEG2 transport stream format
 D  mpegvideo       MPEG video
  E mpjpeg          Mime multipart JPEG format
 DE mulaw           pcm mu law format
 D  nsv             NullSoft Video format
  E null            null video format
 DE nut             nut format
 DE ogg             Ogg Vorbis
  E psp             psp mp4 format
 D  psxstr          Sony Playstation STR format
 DE rawvideo        raw video format
 D  redir           Redirector format
 DE rm              rm format
  E rtp             RTP output format
 D  rtsp            RTSP input format
 DE s16be           pcm signed 16 bit big endian format
 DE s16le           pcm signed 16 bit little endian format
 DE s8              pcm signed 8 bit format
 D  sdp             SDP
 D  shn             raw shn
 D  sol             Sierra SOL Format
  E svcd            MPEG2 PS format (VOB)
 DE swf             Flash format
 DE u16be           pcm unsigned 16 bit big endian format
 DE u16le           pcm unsigned 16 bit little endian format
 DE u8              pcm unsigned 8 bit format
  E vcd             MPEG1 System format (VCD)
 D  video4linux     video grab
 D  vmd             Sierra VMD format
  E vob             MPEG2 PS format (VOB)
 DE wav             wav format
 D  wc3movie        Wing Commander III movie format
 D  wsaud           Westwood Studios audio format
 D  wsvqa           Westwood Studios VQA format
 DE yuv4mpegpipe    YUV4MPEG pipe format

Image formats (filename extensions, if any, follow):
 DE gif    gif

Codecs:
 D V    4xm
 D V D  8bps
 DEA    aac
 D V D  aasc
 DEA    ac3
 DEA    adpcm_4xm
 DEA    adpcm_adx
 DEA    adpcm_ct
 DEA    adpcm_ea
 DEA    adpcm_ima_dk3
 DEA    adpcm_ima_dk4
 DEA    adpcm_ima_qt
 DEA    adpcm_ima_smjpeg
 DEA    adpcm_ima_wav
 DEA    adpcm_ima_ws
 DEA    adpcm_ms
 DEA    adpcm_swf
 DEA    adpcm_xa
 DEA    adpcm_yamaha
 D A    alac
 DEV D  asv1
 DEV D  asv2
 D V D  camtasia
 D V D  cinepak
 D V D  cljr
 D V D  cyuv
 D A    dts
 DES    dvbsub
 D S    dvdsub
 DEV D  dvvideo
 DEV D  ffv1
 DEVSD  ffvhuff
 D A    flac
 D V D  flic
 DEVSD  flv
 D V D  fraps
 DEA    g726
 DEA    gsm
 DEV D  h261
 DEVSDT h263
 D VSD  h263i
  EV    h263p
 D V DT h264
 DEVSD  huffyuv
 D V D  idcinvideo
 D V D  indeo2
 D V    indeo3
 D A    interplay_dpcm
 D V D  interplayvideo
  EV    ljpeg
 D V D  loco
 D A    mace3
 D A    mace6
 D V D  mdec
 DEV D  mjpeg
 D V D  mjpegb
 DEA    mp2
 DEA    mp3
 D A    mp3adu
 D A    mp3on4
 DEVSDT mpeg1video
 DEVSDT mpeg2video
 DEVSDT mpeg4
 D A    mpeg4aac
 D VSDT mpegvideo
 DEVSD  msmpeg4
 DEVSD  msmpeg4v1
 DEVSD  msmpeg4v2
 D V D  msrle
 D V D  msvideo1
 D V D  mszh
 DEV    pam
 DEV    pbm
 DEA    pcm_alaw
 DEA    pcm_mulaw
 DEA    pcm_s16be
 DEA    pcm_s16le
 DEA    pcm_s24be
 DEA    pcm_s24daud
 DEA    pcm_s24le
 DEA    pcm_s32be
 DEA    pcm_s32le
 DEA    pcm_s8
 DEA    pcm_u16be
 DEA    pcm_u16le
 DEA    pcm_u24be
 DEA    pcm_u24le
 DEA    pcm_u32be
 DEA    pcm_u32le
 DEA    pcm_u8
 DEV    pgm
 DEV    pgmyuv
 DEV    png
 DEV    ppm
 D V D  qdraw
 D V D  qpeg
 D V D  qtrle
 DEV    rawvideo
 D A    real_144
 D A    real_288
 D A    roq_dpcm
 D V D  roqvideo
 D V D  rpza
 DEV D  rv10
 DEV D  rv20
 D A    shorten
 D V D  smc
 DEV    snow
 D A    sol_dpcm
 DEA    sonic
  EA    sonicls
 D V D  sp5x
 DEV D  svq1
 D VSD  svq3
 D V    theora
 D V D  truemotion1
 D V D  ultimotion
 D V    vc9
 D V D  vcr1
 D A    vmdaudio
 D V D  vmdvideo
 DEA    vorbis
 D V    vp3
 D V D  vqavideo
 D A    wmav1
 D A    wmav2
 DEVSD  wmv1
 DEVSD  wmv2
 D V    wmv3
 D V D  wnv1
 D A    ws_snd1
 D A    xan_dpcm
 D V D  xan_wc3
 D V D  xl
  EV    xvid
 DEV D  zlib

Supported file protocols:
 file: pipe: udp: rtp: tcp: http:
Frame size, frame rate abbreviations:
 ntsc pal qntsc qpal sntsc spal film ntsc-film sqcif qcif cif 4cif
Motion estimation methods:
 zero(fastest) full(slowest) log phods epzs(default) x1

Note, the names of encoders and decoders dont always match, so there are
several cases where the above table shows encoder only or decoder only entries
even though both encoding and decoding are supported for example, the h263
decoder corresponds to the h263 and h263p encoders, for file formats its even
worse
chris@xmastree:~$

```
Am I right inthinking that means I should be able to encode 3gp? That's what I'm after.

---

### Post by endersshadow on 2006-03-04
It almost looks like it can't deal w/ the inputted format...what if you try another video in a different format?

---

### Post by xmastree on 2006-03-04
Here's one of the files I'm tying to encode:
[http://movies26.enwhore.com/abiggun1.wmv](http://movies26.enwhore.com/abiggun1.wmv)
(rather funny actually...)
I have another, in mpg format, but that gives the same result. :???:

---

### Post by T*&amp;1p87)v# on 2006-03-05
[QUOTE=endersshadow]In gtkpod, you need to edit the metadata (right click on the video, and select properties) and manually enter in the length (in minutes:seconds, so if you had a clip 2 hours, 28 minutes, 32 seconds, it would be 148:32 instead of 2:28:32).  This is only because gtkpod is not able to pull the metadata from any video file, and one of the things that the devel of it is working very hard on doing.[/QUOTE]

Hi guys,

1st thanks for the great howto at the beginning, really THANKS.

today I wanted to watch some of the video files on my ipod, and I found out that some of them I can scroll without problem and some of them I cannot scroll at all, well after a short investigation I found out that the ones in which I  can scroll are mp4 and they were official movie trailers from the apple website. And the others in which I cannot scroll are the ones created using ipodvidenc.

But if I rename some of the .mov files created with ipodvidenc to .mp4 everything is fine, I can scroll without any problem, so I have changed the ipodvidenc script on my pc to save directly to .mp4 files.

Any comments on that?

---

### Post by Formidable1987 on 2006-03-11
I don't seem to be able to encode movies =(
> beelzebub1987@ray-ubuntu-k7:~/_/Movies$ sudo ipodenc Baseketball.avi
Password:
What would you like to name the output file (sans extension)?
Baseketball
Baseketball will be located in /home/beelzebub1987/_/Movies. Is this acceptable? [y/n]
y
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid
  built on Mar 11 2006 14:09:31, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Input #0, avi, from 'Baseketball.avi':
  Duration: 01:38:00.7, start: 0.000000, bitrate: 937 kb/s
  Stream #0.0: Video: msmpeg4, yuv420p, 704x336, 23.98 fps
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 96 kb/s
Output #0, mp4, to '/home/beelzebub1987/_/Movies/Baseketball.mp4':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, 23.98 fps, q=3-5, 700 kb/s
  Stream #0.1: Audio: aac, 48000 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0x8335bc8]removing common factors from framerate
[mpeg4 @ 0x8335bc8]timebase not supported by mpeg 4 standard
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

---

### Post by dpaint4 on 2006-03-13
Wow. I've never compiled from source, but I followed your steps and everything succeeded. So now I pass all the program checks, but when I get to the very **last step** in exeuting the INSTALL as sudo, I receive this message:

```
Checking ffmpeg installation...  [ OK ]
Checking vobcopy installation... [ OK ]
Checking cpdvd installation...   [ OK ]
Checking VLC installation...     [ OK ]
Checking Totem installation...   [ OK ]
Installing Vive...               [ FAIL ]

cp: cannot stat `vive': No such file or directory
```

I've taken a look at the steps that the script executes and I think I could just do them myself. Should I? Why can't it find the file? It's sitting right next to the install file.

Help out a well-intentioned, quickly developing Newbie. This program is exactly what I've been looking for, and I think I'm very close to success.

---

### Post by dpaint4 on 2006-03-13
[QUOTE=dpaint4]Wow. I've never compiled from source, but I followed your steps and everything succeeded. So now I pass all the program checks, but when I get to the very **last step** in exeuting the INSTALL as sudo, I receive this message:

```
Checking ffmpeg installation...  [ OK ]
Checking vobcopy installation... [ OK ]
Checking cpdvd installation...   [ OK ]
Checking VLC installation...     [ OK ]
Checking Totem installation...   [ OK ]
Installing Vive...               [ FAIL ]

cp: cannot stat `vive': No such file or directory
```

I've taken a look at the steps that the script executes and I think I could just do them myself. Should I? Why can't it find the file? It's sitting right next to the install file.

Help out a well-intentioned, quickly developing Newbie. This program is exactly what I've been looking for, and I think I'm very close to success.[/QUOTE]

Nevermind. I figured out I needed to cd to the directory before running the script. I'm learning, I swear I am.

---

### Post by rathortushar on 2006-03-15
Hi, 

i used your useful information on encoding the video for ipod and compiling gtk with the mpeg4ip support.
After the encoding was done, i was also able to play ( with audio support ) on my linux pc. doing a file on the encoded movie gave me : movie.mp4: ISO Media, MPEG v4 system, version 1

But after transferring the movie to my ipod video, i am not able to hear the audio.

Any help to solve this .

---

### Post by dpaint4 on 2006-03-19
[QUOTE=rathortushar]Hi, 

i used your useful information on encoding the video for ipod and compiling gtk with the mpeg4ip support.
After the encoding was done, i was also able to play ( with audio support ) on my linux pc. doing a file on the encoded movie gave me : movie.mp4: ISO Media, MPEG v4 system, version 1

But after transferring the movie to my ipod video, i am not able to hear the audio.

Any help to solve this .[/QUOTE]

Same here. No audio on any of the files of various formats that I've transcoded with Vive. Most have MP3 streams as the audio of the original source. Some are from DVD. Some are Quicktime MOV files. They all transcode gorgeously, but with no audio at all.

---

### Post by endersshadow on 2006-03-19
Are you using a 60gig iPod Video with Firmware 1.1?

And please excuse my tardiness in replies...I've been coast to coast in the past two weeks :)

---

### Post by dpaint4 on 2006-03-19
[QUOTE=endersshadow]Are you using a 60gig iPod Video with Firmware 1.1?

And please excuse my tardiness in replies...I've been coast to coast in the past two weeks :)[/QUOTE]

Oh wow! I can't believe you're replying in person; isn't Vive your software? You're a little bit of a celebrity then! 

Yes. I remember reading something about the 60 gig's having a firmware glitch, and that is indeed what I'm using. :\ 

I'm also using Ubuntu as my only OS on my only personal computer, so I guess I'll have to do an upgrade when Apple releases one on my Mac at work. Not comfortable downgrading I don't think. Wish there was a way around this.

Videora iPod was a free app on Windows that was able to transcode for my unit, so I'm holding out hope for a work-around in the future. Wine dosen't handle it though because it relies on Quicktime (I think...).

Thanks for the reply. Really wasn't expecting it actually, so there's no such thing as a 'tardy' reply. :D

---

### Post by Iandefor on 2006-03-19
[quote=dpaint4]Oh wow! I can't believe you're replying in person; isn't Vive your software? You're a little bit of a celebrity then![/quote] Umm... I'm a little confused. Want to elaborate on why Ender is a "bit of a celebrity"?

---

### Post by endersshadow on 2006-03-19
[QUOTE=dpaint4]Oh wow! I can't believe you're replying in person; isn't Vive your software? You're a little bit of a celebrity then! 

Yes. I remember reading something about the 60 gig's having a firmware glitch, and that is indeed what I'm using. :\ 

I'm also using Ubuntu as my only OS on my only personal computer, so I guess I'll have to do an upgrade when Apple releases one on my Mac at work. Not comfortable downgrading I don't think. Wish there was a way around this.

Videora iPod was a free app on Windows that was able to transcode for my unit, so I'm holding out hope for a work-around in the future. Wine dosen't handle it though because it relies on Quicktime (I think...).

Thanks for the reply. Really wasn't expecting it actually, so there's no such thing as a 'tardy' reply. :D[/QUOTE]

It's the firmware issue, then, not a Vive issue...sorry :-|

As per me being a celebrity, you made my week.  I'm not really all that much of a celebrity...just a dude who solved a problem.  And I'm the only one that I know of supporting Vive, so, yes, yes I will be around much.  I've just taken a two week vacation or something like it--so my apologies for not getting back to you sooner...otherwise, I'm on here every day :-D

I'm working on the Beta release of it right now...trust me...it's awesome.

Now that I'm a celebrity, it's time for...groupies....

---

### Post by dpaint4 on 2006-03-19
[QUOTE=Iandefor]Umm... I'm a little confused. Want to elaborate on why Ender is a "bit of a celebrity"?[/QUOTE]

Well, Endersshadow is a bit of a celebrity to me, personally, because I'm a web designer at my dayjob, which means that I know just enough about code to admire people who do it well, and enough about interface to admire people who do that well too. 

Plus I'm a video/audio compression fanatic, and so Endersshadow falls neatly into the 'celebrity' category, as far as I'm concerned.

As far as the firmware issue is concerned, I understand. Hate that the 30 and 60 would have different firmware! How frustrating right? Well. I'm assuming they'll update soon enough. 

Thanks for all the work on Vive!

---

### Post by endersshadow on 2006-03-19
[QUOTE=dpaint4]Well, Endersshadow is a bit of a celebrity to me, personally, because I'm a web designer at my dayjob, which means that I know just enough about code to admire people who do it well, and enough about interface to admire people who do that well too. 

Plus I'm a video/audio compression fanatic, and so Endersshadow falls neatly into the 'celebrity' category, as far as I'm concerned.

As far as the firmware issue is concerned, I understand. Hate that the 30 and 60 would have different firmware! How frustrating right? Well. I'm assuming they'll update soon enough. 

Thanks for all the work on Vive![/QUOTE]

You're quite welcome, and thank you for the compliments!

And nevermind Ian...he's just upset because I called him [an idiot](http://ubuntuforums.org/showthread.php?p=841603#post841603) :-D

---

### Post by Iandefor on 2006-03-19
[quote=endersshadow]You're quite welcome, and thank you for the compliments!

And nevermind Ian...he's just upset because I called him [an idiot]("http://ubuntuforums.org/showthread.php?p=841603#post841603") :-D[/quote] lol. Thanks, Eric. And I was just confused as to how Eric was a celebrity, seeing as how he doesn't have that much notoriety.

---

### Post by dpaint4 on 2006-03-20
I booted back into Windows to use Videora iPod coverter, which is based on ffmpeg.  Anyway, the new version includes an option to 'fix for 60gb 1.1 firmware'.

Also look at this page, which is for a Mac app with an apple script that does the same thing.

[http://www.isquint.org/](http://www.isquint.org/)

Here's a quote from the page:

> AppleScript to fix up previously-converted videos for 1.1 Firmware Posted Wednesday, March 1, 2006 by Tyler Loch
iSquint Forum rockstar macr0t0r has come up with a nice AppleScript droplet that will batch-fix any .mp4 files created with previous versions of iSquint (or any ffmpeg-based compressor) to work without incident on version 1.1 of the 60GB iPod's firmware:
[http://homepage.mac.com/james_sorenson/ReMux_Quicktime.dmg](http://homepage.mac.com/james_sorenson/ReMux_Quicktime.dmg)
It's already made one 3-year-old overly happy, and hopefully it'll do the same for you too.

We should find out what they're 'fixing' about the file and do the same. Hope this is helpful.

---

### Post by endersshadow on 2006-03-20
[QUOTE=dpaint4]I booted back into Windows to use Videora iPod coverter, which is based on ffmpeg.  Anyway, the new version includes an option to 'fix for 60gb 1.1 firmware'.

Also look at this page, which is for a Mac app with an apple script that does the same thing.

[http://www.isquint.org/](http://www.isquint.org/)

We should find out what they're 'fixing' about the file and do the same. Hope this is helpful.[/QUOTE]

Thanks!  I've emailed Tyler and hopefully he'll get back to me and let me take a peek at the source code for the fix.  I can't find any info or discussion on it out there, but I'll keep Googling.  I think that the trick is to fool it into thinking that it came from iTunes.  If it does in fact include putting DRM on it, I don't think that I can legally put it in the program (as Vive is GPL'd).  Let's just cross our fingers though and hopefully he'll let me take a quick look at the AppleScript (which, for anyone wondering, reads like a book).

---

### Post by endersshadow on 2006-03-20
Well, Tyler got back to me, and good news, I just have to pass it through mpeg4ip (which you would have installed, anyway, if you're using gtkpod to put videos onto your iPod).  I'll include it in the next version of Vive.

If Tyler comes across this, thanks to him for his help!

---

### Post by dpaint4 on 2006-03-20
[QUOTE=endersshadow]Well, Tyler got back to me, and good news, I just have to pass it through mpeg4ip (which you would have installed, anyway, if you're using gtkpod to put videos onto your iPod).  I'll include it in the next version of Vive.

If Tyler comes across this, thanks to him for his help![/QUOTE]

That's really good news. So glad that there turns out to be a way! :KS

---

### Post by hal pacino on 2006-03-20
I fixed my mp4s for ipod G5 1.1 by remuxing with MP4Box.

```
wget http://internap.dl.sourceforge.net/sourceforge/gpac/gpac-0.4.0-rc2.tar.gz
wget http://internap.dl.sourceforge.net/sourceforge/gpac/gpac_extra_libs-0.4.0.tar.gz
tar -zxf gpac-0.4.0-rc2.tar.gz
tar -zxf  gpac_extra_libs-0.4.0.tar.gz
cd gpac_extra_libs
cp -r * ../gpac/extra_lib
cd ../gpac
chmod +x configure
./configure
make lib
make apps
make install
```

Then just type:
```
MP4Box -add <inputvideo>.mp4 <outputvideo>.mp4
```

It doesn't take long. Remuxing is a lot quicker than encoding.

---

### Post by endersshadow on 2006-03-21
[QUOTE=hal pacino]I fixed my mp4s for ipod G5 1.1 by remuxing with MP4Box.

```
wget http://internap.dl.sourceforge.net/sourceforge/gpac/gpac-0.4.0-rc2.tar.gz
wget http://internap.dl.sourceforge.net/sourceforge/gpac/gpac_extra_libs-0.4.0.tar.gz
tar -zxf gpac-0.4.0-rc2.tar.gz
tar -zxf  gpac_extra_libs-0.4.0.tar.gz
cd gpac_extra_libs
cp -r * ../gpac/extra_lib
cd ../gpac
chmod +x configure
./configure
make lib
make apps
make install
```

Then just type:
```
MP4Box -add <inputvideo>.mp4 <outputvideo>.mp4
```

It doesn't take long. Remuxing is a lot quicker than encoding.[/QUOTE]

Thanks for the tip. When I installed it, it did not copy libgpac.so over, so after make install, you need to do this:

```
cd bin/gcc
sudo cp libgpac.so /usr/lib/
```

But only do that if you get an error when you try to run MP4Box :-D

---

### Post by chrluc on 2006-03-22
I have tried to read thru this thread and find it pretty confusing, someware a few weeks ago someone sugested that the wiki be updated to reflect some of the changes in the process, but I think it has not been done (not sure) but the wiki does not even mention vive or how to install it or ipodvidenc.

Here are a few of the questions I have

1.What is the difference between ipodvidenc-1.5.tar.gz and vive-0.1.tar.gz, I first thought that vive is the new ipodvidenc but after tring to just install vive i got shut down right away (would not install) then i thought will maybe vive is just the gui for ipodvidenc but after trying to install ipodvidenc I got this message 
" => `libgpod-0.3.0.tar.gz'
Resolving umn.dl.sourceforge.net... 128.101.240.209
Connecting to umn.dl.sourceforge.net|128.101.240.209|:80... failed: Connection refused.
tar: libgpod-0.3.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
./install: line 80: cd: libgpod-0.3.0/: No such file or directory
./install: line 83: ./configure: No such file or directory
libgpod not configured correctly. Please see ~/.ipodvidenc/install/install.log for details."
so im still not sure if vive is just a gui.

2.if I only want to transfer video to a PSP do i need to install ALL the suggested programs, like mpeg4ip and gtkpod or are they just for ipod?

and thats the questions so far, iknow im just at the start of the whole process, but could really use some advice this far.

---

### Post by endersshadow on 2006-03-22
[QUOTE=chrluc]I have tried to read thru this thread and find it pretty confusing, someware a few weeks ago someone sugested that the wiki be updated to reflect some of the changes in the process, but I think it has not been done (not sure) but the wiki does not even mention vive or how to install it or ipodvidenc.

Here are a few of the questions I have

1.What is the difference between ipodvidenc-1.5.tar.gz and vive-0.1.tar.gz, I first thought that vive is the new ipodvidenc but after tring to just install vive i got shut down right away (would not install) then i thought will maybe vive is just the gui for ipodvidenc but after trying to install ipodvidenc I got this message 
" => `libgpod-0.3.0.tar.gz'
Resolving umn.dl.sourceforge.net... 128.101.240.209
Connecting to umn.dl.sourceforge.net|128.101.240.209|:80... failed: Connection refused.
tar: libgpod-0.3.0.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
./install: line 80: cd: libgpod-0.3.0/: No such file or directory
./install: line 83: ./configure: No such file or directory
libgpod not configured correctly. Please see ~/.ipodvidenc/install/install.log for details."
so im still not sure if vive is just a gui.

2.if I only want to transfer video to a PSP do i need to install ALL the suggested programs, like mpeg4ip and gtkpod or are they just for ipod?

and thats the questions so far, iknow im just at the start of the whole process, but could really use some advice this far.[/QUOTE]

Hey there, sorry to confuse you!

First and foremost, I did not feel as though putting Vive in the Wiki was very tasteful.  Afterall, it's my program that I wrote, and I would hate to use someone else's space to promote it.

Secondly, to answer your last question, you do not need mpeg4ip and/or gtkpod to transfer files to your PSP, only ffmpeg.  Here's what you're going to do:

```
sudo apt-get build-dep ffmpeg
sudo apt-get install liblame-dev libfaad2-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev
apt-get source ffmpeg
cd ffmpeg-*/
./configure --enable-gpl --enable-pp --enable-zlib --enable-vorbis \
	--enable-libogg --enable-theora --enable-a52 --enable-dts \
	--enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
	--enable-faad --enable-faac --enable-xvid
make
sudo make install
```

If you don't have the necessary codecs installed, you'll have to work through those with the ffmpeg installation (it will tell you what you're missing, but you should be able to get everything with the Multimedia Codecs page in the Wiki).  Then, install Vive, select the iPod/PSP Video preset, and you'll be off to the races.

Thirdly, as for the differences between ipodvidenc and Vive.  Both accomplish (nominally) the same task.  ipodvidenc was designed specifically with the iPod and Ubuntu in mind (hence the gtkpod and mpeg4ip install).  Also, it was written in bash and the GUI was via zenity.  I decided that I needed to make it more accessible for other distributions and a bit more professional than just a series of pop-up windows.  Vive was born.  They're both GUIs, and do nominally the same thing...one was just a full installation and automation script for Ubuntu, and the other is a video encoding frontend for ffmpeg for the masses.  I've got Vive v0.2 (Beta release) currently done, and trust me, it's awesome.  I'm writing the configuration and installation processes right now, and should be done by the end of this week. :-D

Hope this helps!

---

### Post by endersshadow on 2006-03-23
Well, the day hath come.  I present: Vive 0.2 (Beta Release)!  Now featuring Preferences, a more configurable interface, a more horizontal interface, the Firmware 1.1 workaround, and more!  Vive has transformed from an iPod Video video encoding frontend to *the* application to take care of all of your video encoding and/or DVD ripping needs.  I'm nice like that.  Grab it at [http://vive.sourceforge.net](http://vive.sourceforge.net)!!!

[img]http://vive.sourceforge.net/images/vive_main_screenie.png[/img]

[img]http://vive.sourceforge.net/images/vive_prefs_screenie.png[/img]

---

### Post by Vincent_Lin on 2006-03-23
Hi,

I recently spent the money to purchase Apple AV cable, hoping that videos stored in my iPod, encoded by ipodvidenc, can be enjoyed as displayed on TV.  It works.  But the image quality is not even on par as VHS tape stuff.  The video, while played on iPod's tiny screen as perfect/beautiful as it should be, shows a lot of artifacts and the color seems to be washed out.  I wonder if there is room for improvement for ffmpeg's encoding process??

I went on the net to research, starting from ffmpeg home page at sourceforge.net.  And here is what I found:

1. Quality
[http://ffmpeg.sourceforge.net/ffmpeg-doc.html#SEC7](http://ffmpeg.sourceforge.net/ffmpeg-doc.html#SEC7)
I wonder if the -hq setting mentioned in this documentation does make any difference.

2. Size of encoded video
[http://homepage.mac.com/major4/ipod_for_tv.html](http://homepage.mac.com/major4/ipod_for_tv.html)
This page, mentioned in ffmpeg.sourceforge.net, documents an OSX application using ffmpeg.  And the instereting bit of this page is the option to encode video into bigger size (than 320x240) while iPod video can still play it, and supposedly if output to TV via AV cable you would get better image quality.  A higher bit rate up to 2500kbps is also possible.

3. AV cable 
[http://www.macdevcenter.com/pub/a/mac/2005/11/18/video-ipod.html?page=1](http://www.macdevcenter.com/pub/a/mac/2005/11/18/video-ipod.html?page=1)
It turns out Apple AV cable is nothing but a general AV cable such as provided by video camara with a twist in output heads arrangement.  Even so, I don't think I am going to return the cable I bought from Apple Store.

Would you care to comment and, if possible, implement the options to change size of video and various bitrates possible?  And what the heck "-hq" option  is for??

Thanks.

Vincent

---

### Post by endersshadow on 2006-03-23
[QUOTE=Vincent_Lin]Hi,

I recently spent the money to purchase Apple AV cable, hoping that videos stored in my iPod, encoded by ipodvidenc, can be enjoyed as displayed on TV.  It works.  But the image quality is not even on par as VHS tape stuff.  The video, while played on iPod's tiny screen as perfect/beautiful as it should be, shows a lot of artifacts and the color seems to be washed out.  I wonder if there is room for improvement for ffmpeg's encoding process??

I went on the net to research, starting from ffmpeg home page at sourceforge.net.  And here is what I found:

1. Quality
[http://ffmpeg.sourceforge.net/ffmpeg-doc.html#SEC7](http://ffmpeg.sourceforge.net/ffmpeg-doc.html#SEC7)
I wonder if the -hq setting mentioned in this documentation does make any difference.

2. Size of encoded video
[http://homepage.mac.com/major4/ipod_for_tv.html](http://homepage.mac.com/major4/ipod_for_tv.html)
This page, mentioned in ffmpeg.sourceforge.net, documents an OSX application using ffmpeg.  And the instereting bit of this page is the option to encode video into bigger size (than 320x240) while iPod video can still play it, and supposedly if output to TV via AV cable you would get better image quality.  A higher bit rate up to 2500kbps is also possible.

3. AV cable 
[http://www.macdevcenter.com/pub/a/mac/2005/11/18/video-ipod.html?page=1](http://www.macdevcenter.com/pub/a/mac/2005/11/18/video-ipod.html?page=1)
It turns out Apple AV cable is nothing but a general AV cable such as provided by video camara with a twist in output heads arrangement.  Even so, I don't think I am going to return the cable I bought from Apple Store.

Would you care to comment and, if possible, implement the options to change size of video and various bitrates possible?  And what the heck "-hq" option  is for??

Thanks.

Vincent[/QUOTE]

1 & 2. I'll add -hq and 2 pass encoding into Vive 1.0 (the next release)...a glaring omission that I thought about at one point and then promptly forgot.  As per the size, with the new release of Vive, you can change the size (or even leave them blank, and it will be the size of the original video).

If you'd like to try out -hq and 2 pass encoding (better quality), in the Bitrate setting, make it read:

700 -hq -pass 2

I (quite foolishly, and am realizing it now) did not put data integrity checking into Vive and it's possibly a security risk (not really too much of one, especially considering the limited reach of Vive and the lack of any internet connections.

3. Given this stuff, let me know how it turns out :-D

---

### Post by marks_linux on 2006-03-23
any ideas what this:

Use of uninitialized value in substitution (s///) at /usr/bin/cpdvd line 76.

means when clicking encode?

I'm not sure anything 'happens' after this. vive GUI doesn't refresh, using 'top' etc shows no CPU activity.


cheers
Mark

---

### Post by chrluc on 2006-03-23
thanks for the quick reply, I understand pretty well now but I still am having problems w/ ffmpeg, at "sudo make install"...

make -C libavcodec all
make[1]: Entering directory `/home/clucas/Desktop/ffmpeg-0.4.9-pre1/libavcodec'
gcc -O3 -Wall  -DHAVE_AV_CONFIG_H -I.. -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -o common.o common.c
In file included from avcodec.h:14,
                 from common.c:28:
common.h:67: error: array type has incomplete element type
common.h:71: error: array type has incomplete element type
make[1]: *** [common.o] Error 1
make[1]: Leaving directory `/home/clucas/Desktop/ffmpeg-0.4.9-pre1/libavcodec'
make: *** [lib] Error 2
 
I got this from a ffmpeg download because apt-get source ffmpeg gave me nothing but errors.

any ideas?

---

### Post by endersshadow on 2006-03-23
[QUOTE=chrluc]thanks for the quick reply, I understand pretty well now but I still am having problems w/ ffmpeg, at "sudo make install"...

make -C libavcodec all
make[1]: Entering directory `/home/clucas/Desktop/ffmpeg-0.4.9-pre1/libavcodec'
gcc -O3 -Wall  -DHAVE_AV_CONFIG_H -I.. -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE -c -o common.o common.c
In file included from avcodec.h:14,
                 from common.c:28:
common.h:67: error: array type has incomplete element type
common.h:71: error: array type has incomplete element type
make[1]: *** [common.o] Error 1
make[1]: Leaving directory `/home/clucas/Desktop/ffmpeg-0.4.9-pre1/libavcodec'
make: *** [lib] Error 2
 
I got this from a ffmpeg download because apt-get source ffmpeg gave me nothing but errors.

any ideas?[/QUOTE]

It appears that there's an error in the code...I'm not going to make you look through a bunch of C code to find it, that's for sure.  I posted it incorrectly, so did you do "sudo apt-get source ffmpeg" or did you neglect to put the sudo in (as I had written)?

[quote=marks_linux]any ideas what this:

Use of uninitialized value in substitution (s///) at /usr/bin/cpdvd line 76.

means when clicking encode?

I'm not sure anything 'happens' after this. vive GUI doesn't refresh, using 'top' etc shows no CPU activity.


cheers
Mark[/quote]

cpdvd has a little snafu in that it sometimes tries to pass an uninitialized variable through a function when it's not copying DVDs.  However, it shouldn't implement that when you press "Encode," only when you press "Load DVD"...

Is it still producing the video?

---

### Post by endersshadow on 2006-03-26
Well, Vincent, I've been experimenting and adding new options to Vive, and I've found the following:

Old iPod configuration (single pass, w/o the -hq, 320x240 size) on a 5:22 video: 34.4MB
New iPod configuration (dual pass, w/ the -hq, default video size) on a 5:22 video: 230.5MB
Raw VOB of same 5:22 video: 304.1MB

So, as you can see, you go from a 90% compression to a 20% compression...but it does look good large...I'll grant you that :-D

---

### Post by hatstand on 2006-03-26
Great programme. Love using it. The new script is great.

---

### Post by endersshadow on 2006-03-26
[QUOTE=hatstand]Great programme. Love using it. The new script is great.[/QUOTE]

Thanks for the compliments :-D

As I know that you have a 60GB w/ 1.1 firmware, I'll ask you: Does Vive encode the video correctly for it?

---

### Post by hatstand on 2006-03-26
Hold on: It's just gone!
I tried a few other movies and they didn't work, so I tried the movie it worked on orignally and now I get this:

Seems that stream 1 comes from film source: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from '/home/mat/videos/streakerscores.wmv':
  Duration: 00:00:20.4, start: 3.000000, bitrate: 503 kb/s
  Stream #0.0: Audio: wmav2, 44100 Hz, stereo, 64 kb/s
  Stream #0.1: Video: wmv2, yuv420p, 384x288, 1000.00 fps
Unknown codec 'aac'

Hmm. I did move all the ipodvidenc, gtkpod debs and folders from my home folder to a backup, but I have moved them back and no difference!

¿que pasó?

---

### Post by endersshadow on 2006-03-26
[QUOTE=hatstand]Hold on: It's just gone!
I tried a few other movies and they didn't work, so I tried the movie it worked on orignally and now I get this:

Seems that stream 1 comes from film source: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from '/home/mat/videos/streakerscores.wmv':
  Duration: 00:00:20.4, start: 3.000000, bitrate: 503 kb/s
  Stream #0.0: Audio: wmav2, 44100 Hz, stereo, 64 kb/s
  Stream #0.1: Video: wmv2, yuv420p, 384x288, 1000.00 fps
Unknown codec 'aac'

Hmm. I did move all the ipodvidenc, gtkpod debs and folders from my home folder to a backup, but I have moved them back and no difference!

¿que pasó?[/QUOTE]

¿Qué es el resulto de ffmpeg -formats?

---

### Post by hatstand on 2006-03-26
[QUOTE=endersshadow]¿Qué es el resulto de ffmpeg -formats?[/QUOTE]


¿hablas Español? Que bueno. Aquí está:

ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)
File formats:
  E 3g2             3gp2 format
  E 3gp             3gp format
 D  4xm             4X Technologies format
 D  RoQ             Id RoQ format
 DE ac3             raw ac3
 DE alaw            pcm A law format
 DE asf             asf format
  E asf_stream      asf format
 DE au              SUN AU Format
 DE audio_device    audio grab and output
 DE avi             avi format
  E crc             crc testing format
 D  daud            D-Cinema audio format
 D  dc1394          dc1394 A/V grab
 D  dts             raw dts
 DE dv              DV video format
 D  dv1394          dv1394 A/V grab
  E dvd             MPEG2 PS format (DVD VOB)
 D  ea              Electronic Arts Multimedia Format
 DE ffm             ffm format
 D  film_cpk        Sega FILM/CPK format
 D  flic            FLI/FLC animation format
 DE flv             flv format
 DE gif             GIF Animation
 DE h261            raw h261
 DE h263            raw h263
 DE h264            raw H264 video format
 D  idcin           Id CIN format
 DE image           image sequence
 DE image2          image2 sequence
 DE image2pipe      piped image2 sequence
 DE imagepipe       piped image sequence
 D  ipmovie         Interplay MVE format
 DE m4v             raw MPEG4 video format
 D  matroska        Matroska file format
 DE mjpeg           MJPEG video
 DE mmf             mmf format
  E mov             mov format
 D  mov,mp4,m4a,3gp,3g2 QuickTime/MPEG4 format
  E mp2             MPEG audio layer 2
 D  mp3             MPEG audio
  E mp4             mp4 format
 DE mpeg            MPEG1 System format
  E mpeg1video      MPEG video
  E mpeg2video      MPEG2 video
 DE mpegts          MPEG2 transport stream format
 D  mpegvideo       MPEG video
  E mpjpeg          Mime multipart JPEG format
 DE mulaw           pcm mu law format
 D  nsv             NullSoft Video format
  E null            null video format
 DE nut             nut format
 DE ogg             Ogg Vorbis
  E psp             psp mp4 format
 D  psxstr          Sony Playstation STR format
 DE rawvideo        raw video format
 D  redir           Redirector format
 DE rm              rm format
  E rtp             RTP output format
 D  rtsp            RTSP input format
 DE s16be           pcm signed 16 bit big endian format
 DE s16le           pcm signed 16 bit little endian format
 DE s8              pcm signed 8 bit format
 D  sdp             SDP
 D  shn             raw shn
 D  sol             Sierra SOL Format
  E svcd            MPEG2 PS format (VOB)
 DE swf             Flash format
 DE u16be           pcm unsigned 16 bit big endian format
 DE u16le           pcm unsigned 16 bit little endian format
 DE u8              pcm unsigned 8 bit format
  E vcd             MPEG1 System format (VCD)
 D  video4linux     video grab
 D  vmd             Sierra VMD format
  E vob             MPEG2 PS format (VOB)
 DE wav             wav format
 D  wc3movie        Wing Commander III movie format
 D  wsaud           Westwood Studios audio format
 D  wsvqa           Westwood Studios VQA format
 DE yuv4mpegpipe    YUV4MPEG pipe format

Image formats (filename extensions, if any, follow):
 DE gif    gif

Codecs:
 D V    4xm
 D V D  8bps
 D V D  aasc
 DEA    ac3
 DEA    adpcm_4xm
 DEA    adpcm_adx
 DEA    adpcm_ct
 DEA    adpcm_ea
 DEA    adpcm_ima_dk3
 DEA    adpcm_ima_dk4
 DEA    adpcm_ima_qt
 DEA    adpcm_ima_smjpeg
 DEA    adpcm_ima_wav
 DEA    adpcm_ima_ws
 DEA    adpcm_ms
 DEA    adpcm_swf
 DEA    adpcm_xa
 DEA    adpcm_yamaha
 D A    alac
 DEV D  asv1
 DEV D  asv2
 D V D  camtasia
 D V D  cinepak
 D V D  cljr
 D V D  cyuv
 D A    dts
 DES    dvbsub
 D S    dvdsub
 DEV D  dvvideo
 DEV D  ffv1
 DEVSD  ffvhuff
 D A    flac
 D V D  flic
 DEVSD  flv
 D V D  fraps
 DEA    g726
 DEA    gsm
 DEV D  h261
 DEVSDT h263
 D VSD  h263i
  EV    h263p
 D V DT h264
 DEVSD  huffyuv
 D V D  idcinvideo
 D V D  indeo2
 D V    indeo3
 D A    interplay_dpcm
 D V D  interplayvideo
  EV    ljpeg
 D V D  loco
 D A    mace3
 D A    mace6
 D V D  mdec
 DEV D  mjpeg
 D V D  mjpegb
 DEA    mp2
 D A    mp3
 D A    mp3adu
 D A    mp3on4
 DEVSDT mpeg1video
 DEVSDT mpeg2video
 DEVSDT mpeg4
 D VSDT mpegvideo
 DEVSD  msmpeg4
 DEVSD  msmpeg4v1
 DEVSD  msmpeg4v2
 D V D  msrle
 D V D  msvideo1
 D V D  mszh
 DEV    pam
 DEV    pbm
 DEA    pcm_alaw
 DEA    pcm_mulaw
 DEA    pcm_s16be
 DEA    pcm_s16le
 DEA    pcm_s24be
 DEA    pcm_s24daud
 DEA    pcm_s24le
 DEA    pcm_s32be
 DEA    pcm_s32le
 DEA    pcm_s8
 DEA    pcm_u16be
 DEA    pcm_u16le
 DEA    pcm_u24be
 DEA    pcm_u24le
 DEA    pcm_u32be
 DEA    pcm_u32le
 DEA    pcm_u8
 DEV    pgm
 DEV    pgmyuv
 DEV    png
 DEV    ppm
 D V D  qdraw
 D V D  qpeg
 D V D  qtrle
 DEV    rawvideo
 D A    real_144
 D A    real_288
 D A    roq_dpcm
 D V D  roqvideo
 D V D  rpza
 DEV D  rv10
 DEV D  rv20
 D A    shorten
 D V D  smc
 DEV    snow
 D A    sol_dpcm
 DEA    sonic
  EA    sonicls
 D V D  sp5x
 DEV D  svq1
 D VSD  svq3
 D V    theora
 D V D  truemotion1
 D V D  ultimotion
 D V    vc9
 D V D  vcr1
 D A    vmdaudio
 D V D  vmdvideo
 DEA    vorbis
 D V    vp3
 D V D  vqavideo
 D A    wmav1
 D A    wmav2
 DEVSD  wmv1
 DEVSD  wmv2
 D V    wmv3
 D V D  wnv1
 D A    ws_snd1
 D A    xan_dpcm
 D V D  xan_wc3
 D V D  xl
 DEV D  zlib

Supported file protocols:
 file: pipe: udp: rtp: tcp: http:
Frame size, frame rate abbreviations:
 ntsc pal qntsc qpal sntsc spal film ntsc-film sqcif qcif cif 4cif
Motion estimation methods:
 zero(fastest) full(slowest) log phods epzs(default) x1

Note, the names of encoders and decoders dont always match, so there are
several cases where the above table shows encoder only or decoder only entries even though both encoding and decoding are supported for example, the h263 decoder corresponds to the h263 and h263p encoders, for file formats its even worse


Gracias

---

### Post by endersshadow on 2006-03-26
[QUOTE=hatstand]¿hablas Español? Que bueno. Aquí está:

ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Sep 29 2005 03:25:16, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu8)

Gracias[/QUOTE]

Hablo español un poco, pero trato, es verdad.  Sin embargo, tu problema...

Es obvio que no hay aac en tu resulto...aquí:

 D V    4xm
 D V D  8bps
 D V D  aasc
 DEA    ac3

Debe estar aac antes de aasc...así, hace este:

```
sudo apt-get install faac libfaac0 libfaac-dev gstreamer0.8-faac faac
```

Y también, es posible que necesites compilar ffmpeg también con --enable-faac y --enable-faad.

Dígame si ese es bueno. :-D

---

### Post by hatstand on 2006-03-26
[QUOTE=endersshadow]Hablo español un poco, pero trato, es verdad.  Sin embargo, tu problema...

Es obvio que no hay aac en tu resulto...aquí:

 D V    4xm
 D V D  8bps
 D V D  aasc
 DEA    ac3

Debe estar aac antes de aasc...así, hace este:

```
sudo apt-get install faac libfaac0 libfaac-dev gstreamer0.8-faac faac
```

Y también, es posible que necesites compilar ffmpeg también con --enable-faac y --enable-faad.

Dígame si ese es bueno. :-D[/QUOTE]

La contesta corta es "no"

Ya tengo faac libfaac0 etc.

Entonces necesito compilar ffmpeg. ¿Como se puede hacerlo? ¿Tengo que reinstalar y reconstruir ffmpeg from source?

Gracias mate

---

### Post by hatstand on 2006-03-26
[QUOTE=hatstand]La contesta corta es "no"

Ya tengo faac libfaac0 etc.

Entonces necesito compilar ffmpeg. ¿Como se puede hacerlo? ¿Tengo que reinstalar y reconstruir ffmpeg from source?

Gracias mate[/QUOTE]


ups

hicé un error.

usé vi debian/rules y cambié unas lineas pero las equivicadas. Ahora se me olvidó las originales. Voy a reconstruir ffmpeg usando las instrucciónes de pagaina 1.

te diré las resultados

---

### Post by endersshadow on 2006-03-26
[QUOTE=hatstand]ups

hicé un error.

usé vi debian/rules y cambié unas lineas pero las equivicadas. Ahora se me olvidó las originales. Voy a reconstruir ffmpeg usando las instrucciónes de pagaina 1.

te diré las resultados[/QUOTE]

Bueno...entonces, no necesitas mi contesta que escribí :-D

---

### Post by hatstand on 2006-03-26
Bueno: aquí lo tenemos:

con un test video estaba bien pero con el segundo video tengo errores como esos:

Seems that stream 1 comes from film source: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from '/home/mat/Palace Vids/champ.wmv':
  Duration: 00:03:57.5, start: 8.000000, bitrate: 156 kb/s
  Stream #0.0: Audio: wmav2, 32000 Hz, mono, 20 kb/s
  Stream #0.1: Video: wmv3, yuv420p, 320x240, 1000.00 fps
Output #0, mp4, to '/home/mat/videos/champ.mov':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, 25.00 fps, q=3-5, 700 kb/s
  Stream #0.1: Audio: aac, 32000 Hz, mono, 192 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
[wmv3 @ 0x8335b88]This decoder is not supposed to produce picture. Dont report this as a bug!
[wmv3 @ 0x8335b88]Profile 1:
frmrtq_postproc=4, bitrtq_postproc=2
LoopFilter=1, MultiRes=0, FastUVMV=0, Extended MV=0
Rangered=0, VSTransform=1, Overlap=1, SyncMarker=0
DQuant=1, Quantizer mode=0, Max B frames=0
Press [q] to stop encoding
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]Transform used: 4x8
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors
[wmv3 @ 0x8335b88]VOP DQuant info
[wmv3 @ 0x8335b88]concealing 300 DC, 300 AC, 300 MV errors

---

### Post by endersshadow on 2006-03-26
Escondí esta pagina en este problema:

[http://www.richardgoodwin.com/wp/2006/02/15/building-ffmpeg-to-support-windows-media-files/](http://www.richardgoodwin.com/wp/2006/02/15/building-ffmpeg-to-support-windows-media-files/)

Recuerda que usar el ./configure de la primera pagina, y no uses solamente ./configure sin las opciones.

---

### Post by hatstand on 2006-03-26
parece que es el tipo de video que estoy bajando. Funciona con todos otros videos.

---

### Post by endersshadow on 2006-03-26
[QUOTE=hatstand]parece que es el tipo de video que estoy bajando. Funciona con todos otros videos.[/QUOTE]

Sí, es el tipo de video.  Ya que es un WMV3 para su video, necesitas una modificación a la fuente de ffmpeg por que puedas usar ese tipo de video.

Lo siento :-|

---

### Post by hatstand on 2006-03-26
está bien. lo que es más importante es que puedo convertir mis DVDs para usar en el ipod. los otros serían un bonus nada más.

Es un buen programa y gracias por todo su ayuda.

---

### Post by endersshadow on 2006-03-26
[QUOTE=hatstand]está bien. lo que es más importante es que puedo convertir mis DVDs para usar en el ipod. los otros serían un bonus nada más.

Es un buen programa y gracias por todo su ayuda.[/QUOTE]

De nada y gracias.

Now, in English for everybody that may have the same problem:
When he did ffmpeg -formats, he didn't get aac as a codec.  Therefore, he had to install the aac packages (faac, gstreamer0.8-faac, libfaac0, libfaac-dev), and configure ffmpeg w/ the flags that can be found on the first page.

If you need to use Vive to encode WMV files, you need to follow the guide on the following page:

[http://www.richardgoodwin.com/wp/2006/02/15/building-ffmpeg-to-support-windows-media-files/](http://www.richardgoodwin.com/wp/2006/02/15/building-ffmpeg-to-support-windows-media-files/)

---

### Post by hatstand on 2006-03-26
whoops

404 error page, endersshadow

keep up the good work

---

### Post by endersshadow on 2006-03-26
[QUOTE=hatstand]whoops

404 error page, endersshadow

keep up the good work[/QUOTE]

Whoops...selected the text from the post instead of the link...my fault--fixed :-D

---

### Post by Hydoskee on 2006-04-05
I think I did one better.  I made a perl script to encode a whole folder's worth of video, automatically.

put the file below, saved as "convert.pl" in the directory you wish to convert, and run the following lines:

```

ls > files 
./convert.pl files
./conversionscript.sh

```

Takes the pain out of doing it one by one!

Here's the code for convert.pl
```

#!/usr/bin/perl

$ROOM=$ARGV[0];
$in=$ROOM;
$out="conversionscript.sh";

open(input,$in);
open(output,">>$out");
@filenames=<input>;
close(input);


print output "#!/bin/bash\n";
foreach $file (@filenames)
{
$length = length($file);
if(index($file, '.') != -1 ){
	chop($file);
#	print $file;
#	print "\n";
	print output "ffmpeg -i ";
	print output '"';
	print output $file;
	print output '"';
	print output ' ';
	print output " -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 ";
	$length = length($file);
	print output '"';
	print output substr($file, 0, $length - 3);
	print output "mp4";
	print output '"';
	print output "\n";
	}
}
close(output);

```

enjoy!

---

### Post by endersshadow on 2006-04-05
Interesting...I'll have to make the next version of Vive have a batch encode feature...

Thanks!

---

### Post by ruvil on 2006-04-07
excuse me.. but does anyone know what i have done wrong?
When i run the 'ipodvidenc' script (i have installed ffmpeg exactly as you told "me") this shows up:
/usr/bin/ipodv: line 17: [: missing `]'
/usr/bin/ipodv: line 18: ]: command not found
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid
  built on Apr  8 2006 03:14:36, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Input #0, avi, from 'myfile.avi':
  Duration: 00:03:30.9, start: 0.000000, bitrate: 2426 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 640x480, 25.00 fps
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 192 kb/s
Must supply at least one output file
/usr/bin/ipodv: line 27: -qmin: command not found
/usr/bin/ipodv: line 28: -aspect: command not found

anyone knows what is wrong? Is it okay to remove the -qmin and aspect lines from the script and encode without them?
Or will the video be messed up then?

---

### Post by x5452 on 2006-04-10
i just set up a ubuntu system for my friends laptop and he has an ipod video, i found your how to post just in time since hes bringing his ipod over tomorrow, thanks for writing the how to, hope it works well for me!  
I have gtkpod installed already but it is not the new 9 version, should i uninstall it before begining the how to procedure?

Awsome name by the way, the Ender series was awsome!  although, I think Ender's game was my favorite book of them all!!   :mrgreen:

---

### Post by endersshadow on 2006-04-10
[QUOTE=x5452]i just set up a ubuntu system for my friends laptop and he has an ipod video, i found your how to post just in time since hes bringing his ipod over tomorrow, thanks for writing the how to, hope it works well for me!  
I have gtkpod installed already but it is not the new 9 version, should i uninstall it before begining the how to procedure?

Awsome name by the way, the Ender series was awsome!  although, I think Ender's game was my favorite book of them all!!   :mrgreen:[/QUOTE]

Nope, you don't need to uninstall.  The newer version will update it automatically.

As for Ender...yeah, I think *Ender's Game* was the best, but my favorite character has always been Bean.  But naming yourself Bean just leads to a lot of questions :-D

---

### Post by x5452 on 2006-04-10
right on, thanks, i hate uninstalling stuff, the last time i did it took my desktop with it, stupid evolution!

Yeah, I guess bean would get questions here huh? lol  they were supposed to make an Ender movie, guess it got scrapped though, too bad.  All the other books got too religious for sci-fi anyways

thanks for your help

---

### Post by riiidaa on 2006-04-10
With assistance from my mate, we've got ipodvidenc and vive working, Thanks lots for the work!

However my problem is that i want to encode .mp4 vids on the ubuntu server and then ftp the encoded video to my windows box where i can then use iTunes to chuck them onto my ipod.

Sadly it falls down at the iTunes -> iPod section, at first it was giving me the "not a video file" error when I was trying to copy it to the iTunes library but then I read back on page 11 something about blank meta data fields so went back to VIVE and entered in info in the "copyright" etc boxes. Then it allowed it to copy to the iTunes library and even play! 

BUT even tho it plays the file fine when I i play the file in iTunes if i try to copy it to the iPod it says it can't ](*,) 

Really need to be able to do this, any ideas??

---

### Post by endersshadow on 2006-04-10
[QUOTE=riiidaa]With assistance from my mate, we've got ipodvidenc and vive working, Thanks lots for the work!

However my problem is that i want to encode .mp4 vids on the ubuntu server and then ftp the encoded video to my windows box where i can then use iTunes to chuck them onto my ipod.

Sadly it falls down at the iTunes -> iPod section, at first it was giving me the "not a video file" error when I was trying to copy it to the iTunes library but then I read back on page 11 something about blank meta data fields so went back to VIVE and entered in info in the "copyright" etc boxes. Then it allowed it to copy to the iTunes library and even play! 

BUT even tho it plays the file fine when I i play the file in iTunes if i try to copy it to the iPod it says it can't ](*,) 

Really need to be able to do this, any ideas??[/QUOTE]

Make sure that it's named .mov instead of .mp4...it matters, for some reason.

Also, do you happen to have a 60GB iPod?

Oh, and if you'd like to do it in Windows, check out [Videora](http://www.videora.com/en-us/Converter/) if the above doesn't work.  It may be quicker.

And a question: Would a CLI be helpful for Vive?

---

### Post by riiidaa on 2006-04-10
When it was .mov before it didn't wanna know at all but then the extra metadata wasn't there, thanks I shall try that.

I'm on the 30gb version.

On windows indeed i have been running Videora, it works well, and outputs .mp4 that i have no sweat in watching / copying over to my pod.

Reason i wanna do it from ubuntu is that I'm gonna house it in a datacentre, and grab stuff from newsgroups, then keep it on my personal ftp share but also make ipod video versions of the files that i can easily download if i wanna watch a vid at short notice - method in my madness you might say...

---

### Post by riiidaa on 2006-04-10
[QUOTE=endersshadow]Make sure that it's named .mov instead of .mp4...it matters, for some reason.
[/QUOTE]

Renaming to .mov proves fruitless mate, iTunes doesn't allow it to add to library when it's a .mov

bummer

---

### Post by endersshadow on 2006-04-10
Try encoding it with the container format being h264 instead of mp4 and let me know how it works.

---

### Post by x5452 on 2006-04-10
ok i have confused myself, i just got my friends ipod video here now.  I plugged it in the usb, and it showed up on the desktop, cool?  I have an old version of gtkpod installed.  I began reading your how to again and got confused, first, i tried downloading the attached ipodvidenc-1.5.tar.gz and it didnt do anything, i click save and it doesnt download? weird.  second, at the top of your post it says that "The full install actually also does this whole HowTo for you. I've called it, very unimaginitively, "iPod Video Encoder" or ipodvidenc for short."  does that mean there is something to download that will install the gui, new gtkpod and set me up for making videos and sending stuff to the ipod, all at once?  if so where is that link? 

Lol, i guess im basically asking where to begin?  thanks Bean  :mrgreen:

---

### Post by x5452 on 2006-04-10
ok so when im on my computer thats running ubuntu, i go to page one of this post and click the download link of the attached file, and it ask me if i want to save it to disk, i click yes, then the box dissappears, no dowload box shows up, and the file is nowhere to be found.  then i was able to download the vive tar file, and i could not follow the read me instruction very well.  i unpacked the tar file in my home directiory, i opened up terminal and typed ./configure, it did some stuff and told me to install mp4box, but it did work, it said try wget for two files, i did.  then i tried typing make.  nothing.  make install.  nothing, im sure im an idiot, but what do i do?

---

### Post by x5452 on 2006-04-11
Please help, ive tried a dozen different how to's, and somewhere ]there is always an error or somthing wont install or dependencies conflict.  here is the script from my last attempt following the HowTo at the beginning of this thread:

scott@ubuntu:~$ sudo apt-get remove libmp4v2-0 libmp4v2-dev faac gstreamer0.8-faac libfaac0 libfaac-dev
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  faac gstreamer0.8-faac libfaac-dev libfaac0 libmp4v2-0 libmp4v2-dev
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 2683kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 84635 files and directories currently installed.)
Removing faac ...
Removing gstreamer0.8-faac ...
Removing libfaac-dev ...
Removing libfaac0 ...
Removing libmp4v2-dev ...
Removing libmp4v2-0 ...
scott@ubuntu:~$ wget [http://rarewares.org/debian/packages/unstable/mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb](http://rarewares.org/debian/packages/unstable/mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb)
--22:59:59--  [http://rarewares.org/debian/packages/unstable/mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb](http://rarewares.org/debian/packages/unstable/mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb)
           => `mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb.1'
Resolving rarewares.org... 66.225.254.3
Connecting to rarewares.org|66.225.254.3|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 499,078 (487K) [text/plain]

100%[====================================>] 499,078      314.62K/s

23:00:01 (313.56 KB/s) - `mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb.1' saved [499078/499078]

scott@ubuntu:~$ sudo dpkg -i mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb
(Reading database ... 84581 files and directories currently installed.)
Unpacking mpeg4ip-libs (from mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb) ...Setting up mpeg4ip-libs (1.2.5+cvs20050126.20-0.0) ...

scott@ubuntu:~$ wget [http://internap.dl.sourceforge.net/sourceforge/mpeg4ip/mpeg4ip-1.4.1.tar.gz](http://internap.dl.sourceforge.net/sourceforge/mpeg4ip/mpeg4ip-1.4.1.tar.gz)
--23:02:35--  [http://internap.dl.sourceforge.net/sourceforge/mpeg4ip/mpeg4ip-1.4.1.tar.gz](http://internap.dl.sourceforge.net/sourceforge/mpeg4ip/mpeg4ip-1.4.1.tar.gz)
           => `mpeg4ip-1.4.1.tar.gz.1'
Resolving internap.dl.sourceforge.net... 64.74.207.43
Connecting to internap.dl.sourceforge.net|64.74.207.43|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,791,075 (4.6M) [application/x-gzip]

100%[====================================>] 4,791,075    320.65K/s    ETA 00:00

23:02:50 (311.80 KB/s) - `mpeg4ip-1.4.1.tar.gz.1' saved [4791075/4791075]

scott@ubuntu:~$ tar xzf mpeg4ip-1.4.1.tar.gz
scott@ubuntu:~$ cd mpeg4ip-1.4.1
scott@ubuntu:~/mpeg4ip-1.4.1$ ./bootstrap --disable-server
dir: .
SDL does not appear to be installed - install the SDL development package
You must have sdl-config in your path to continue
scott@ubuntu:~/mpeg4ip-1.4.1$


Ideas?>  Help please

---

### Post by endersshadow on 2006-04-11
Skip the installing from the mpeg-1.4.1 from source step.  You've already installed it with the deb file.

Just go straight to installing gtkpod.

Sorry for not getting to you sooner, I just reinstalled and I'm working on getting a dual booting Ubuntu/Arch machine...but I've done the HowTo from beginning to end, and it worked for me on a clean install.

---

### Post by x5452 on 2006-04-11
no problem, I understand people get busy :mrgreen:  I guess got got messed up, (being new) at the part about where i wget the deb from rarewares then dpkg it, i didnt iknow if the next few code boxes were only for the people doing source or not, and i tried the cd../../ make and checkinstall stuff and got errors, probably because i wasnt supposed to do that right? ](*,)   So now im not sure of my mpeg4 status, not sure of any lib files, i do have the newest .99.2 gtkpod installed, is there a way to "start over"  or does it matter?  can i just do the mpe4 part, then skip to the ffmpeg part?  sorry for my retardation

---

### Post by endersshadow on 2006-04-11
[QUOTE=x5452]no problem, I understand people get busy :mrgreen:  I guess got got messed up, (being new) at the part about where i wget the deb from rarewares then dpkg it, i didnt iknow if the next few code boxes were only for the people doing source or not, and i tried the cd../../ make and checkinstall stuff and got errors, probably because i wasnt supposed to do that right? ](*,)   So now im not sure of my mpeg4 status, not sure of any lib files, i do have the newest .99.2 gtkpod installed, is there a way to "start over"  or does it matter?  can i just do the mpe4 part, then skip to the ffmpeg part?  sorry for my retardation[/QUOTE]

Start right over from scratch.  It will overwrite any of the stuff you've done previously.  Also, you need to have mpeg4ip installed before gtkpod...it gets weird, I know, but trust me on this. :-D

---

### Post by x5452 on 2006-04-11
should i uninstall the .99.2 gtkpod first then? or will following the steps and installing .99.2 gtkpod overwite the current version and mainain the oreder of installation?

---

### Post by endersshadow on 2006-04-11
[QUOTE=x5452]should i uninstall the .99.2 gtkpod first then? or will following the steps and installing .99.2 gtkpod overwite the current version and mainain the oreder of installation?[/QUOTE]

No, you don't need to uninstall the .99.2 version...just start it up from the top, and it will all be taken care of automatically :-D

---

### Post by x5452 on 2006-04-11
Sorry but I dont know what im doing wrong, i just started from the beginning, here is the entire terminal copy of what i did, and i just copy and pasted exactly what was written i typed nothing.  i get to the perl makefile part and it says not such thing:

scott@ubuntu:~$ sudo apt-get remove libmp4v2-0 libmp4v2-dev faac gstreamer0.8-faac libfaac0 libfaac-dev
Password:
Reading package lists... Done
Building dependency tree... Done
Package libmp4v2-0 is not installed, so not removed
Package libmp4v2-dev is not installed, so not removed
Package faac is not installed, so not removed
Package gstreamer0.8-faac is not installed, so not removed
Package libfaac0 is not installed, so not removed
Package libfaac-dev is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
scott@ubuntu:~$ wget [http://rarewares.org/debian/packages/unstable/mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb](http://rarewares.org/debian/packages/unstable/mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb)
--14:37:02--  [http://rarewares.org/debian/packages/unstable/mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb](http://rarewares.org/debian/packages/unstable/mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb)
           => `mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb.2'
Resolving rarewares.org... 66.225.254.3
Connecting to rarewares.org|66.225.254.3|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 499,078 (487K) [text/plain]

100%[====================================>] 499,078      206.16K/s

14:37:05 (205.35 KB/s) - `mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb.2' saved [499078/499078]

scott@ubuntu:~$ sudo dpkg -i mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb
(Reading database ... 84716 files and directories currently installed.)
Preparing to replace mpeg4ip-libs 2:1.2.5+cvs20050126.20-0.0 (using mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb) ...
Unpacking replacement mpeg4ip-libs ...
Setting up mpeg4ip-libs (1.2.5+cvs20050126.20-0.0) ...

scott@ubuntu:~$ sudo apt-get install libexpat1-dev libglade2-0 libglade2-dev flex libid3tag0 libid3tag0-dev
Reading package lists... Done
Building dependency tree... Done
libexpat1-dev is already the newest version.
libglade2-0 is already the newest version.
libglade2-dev is already the newest version.
flex is already the newest version.
libid3tag0 is already the newest version.
libid3tag0-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
scott@ubuntu:~$ wget [http://search.cpan.org/CPAN/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz](http://search.cpan.org/CPAN/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz)
--14:39:14--  [http://search.cpan.org/CPAN/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz](http://search.cpan.org/CPAN/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz)
           => `XML-Parser-2.34.tar.gz.2'
Resolving search.cpan.org... 216.52.237.135
Connecting to search.cpan.org|216.52.237.135|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://www.ibiblio.org/pub/mirrors/CPAN/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz](http://www.ibiblio.org/pub/mirrors/CPAN/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz) [following]
--14:39:14--  [http://www.ibiblio.org/pub/mirrors/CPAN/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz](http://www.ibiblio.org/pub/mirrors/CPAN/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz)
           => `XML-Parser-2.34.tar.gz.2'
Resolving [www.ibiblio.org](www.ibiblio.org)... 152.2.210.80
Connecting to www.ibiblio.org|152.2.210.80|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://mirrors.ibiblio.org/pub/mirrors/CPAN/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz](http://mirrors.ibiblio.org/pub/mirrors/CPAN/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz) [following]
--14:39:14--  [http://mirrors.ibiblio.org/pub/mirrors/CPAN/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz](http://mirrors.ibiblio.org/pub/mirrors/CPAN/authors/id/M/MS/MSERGEANT/XML-Parser-2.34.tar.gz)
           => `XML-Parser-2.34.tar.gz.2'
Resolving mirrors.ibiblio.org... 152.2.210.65
Connecting to mirrors.ibiblio.org|152.2.210.65|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 229,689 (224K) [application/x-gzip]

100%[====================================>] 229,689      175.20K/s

14:39:16 (174.58 KB/s) - `XML-Parser-2.34.tar.gz.2' saved [229689/229689]

scott@ubuntu:~$ tar xzf XML-Parser-2.34.tar.gz
scott@ubuntu:~$ perl Makefile.PL
Can't open perl script "Makefile.PL": No such file or directory
scott@ubuntu:~$


sorry foir long post, do you have any idea what i am doing wrong?

---

### Post by x5452 on 2006-04-11
ok so im an idiot again, i did not realize i had to cd into the new place.  the checkinstall wouldnt work for me because i didnt know i had to INSTALL checkinstall, lol, i thought it was pre installed.  In my haste i did not read all the way through the gtkpod install part, where you say dont forget to rename gtkpod, i just pushed y and enter and never renamed anything.  does it really matter, and is there a way to rename it later?

---

### Post by endersshadow on 2006-04-11
[QUOTE=x5452]ok so im an idiot again, i did not realize i had to cd into the new place.  the checkinstall wouldnt work for me because i didnt know i had to INSTALL checkinstall, lol, i thought it was pre installed.  In my haste i did not read all the way through the gtkpod install part, where you say dont forget to rename gtkpod, i just pushed y and enter and never renamed anything.  does it really matter, and is there a way to rename it later?[/QUOTE]

It only really matter unless you'd like to upgrade it or remove it.

---

### Post by x5452 on 2006-04-11
ok, whats the deal with the ffmpeg build dependencies? i saw another post about it and the guy installed libdts-dev, libtheora-dev, libgsm1-dev, libraw1394-dev so i sud apt-get installed them, and tried sudo apt-get build-dep ffmpeg again and get 
 reading package lists... Done
Building dependency tree...Done
Note, selecting liba52-0.7.4-dev instead of liba52-dev
E: Build-dependencies for ffmpeg could not be satisfied

whats that mean?

---

### Post by x5452 on 2006-04-11
ok, whats the deal with the ffmpeg build dependencies? i saw another post about it and the guy installed libdts-dev, libtheora-dev, libgsm1-dev, libraw1394-dev so i sud apt-get installed them, and tried sudo apt-get build-dep ffmpeg again and get 
 reading package lists... Done
Building dependency tree...Done
Note, selecting liba52-0.7.4-dev instead of liba52-dev
E: Build-dependencies for ffmpeg could not be satisfied

whats that mean?

---

### Post by x5452 on 2006-04-13
Guess ill be normal and post in here, I feel bad for bothering Mr. Ender so much.  I was finally able to get Vive working and encoding properly, im sure that in my haste i missed some key steps initially. However, while befuddling around i had installed ipodvidenc probably twice or so, and support files with it, and im wondering how can I find out how to uninstall it?  I go to cd vive-0.2 try uninstall and it says directoiry does not exist?  but i know it does, because I can run ipodvidenc through my menu... can someone please help me clean up my system from the mistakes i made, thanks in advance.

---

### Post by endersshadow on 2006-04-13
[QUOTE=x5452]Guess ill be normal and post in here, I feel bad for bothering Mr. Ender so much.  I was finally able to get Vive working and encoding properly, im sure that in my haste i missed some key steps initially. However, while befuddling around i had installed ipodvidenc probably twice or so, and support files with it, and im wondering how can I find out how to uninstall it?  I go to cd vive-0.2 try uninstall and it says directoiry does not exist?  but i know it does, because I can run ipodvidenc through my menu... can someone please help me clean up my system from the mistakes i made, thanks in advance.[/QUOTE]

Do you want to uninstall Vive or ipodvidenc?  If you want to uninstall ipodvidenc, simply do this:

```
sudo rm -f /usr/bin/ipodvidenc
sudo rm -rf /home/YOUR_USERNAME/.ipodvidenc/
```

Done :-D

---

### Post by x5452 on 2006-04-13
lol, i knew i must have messed something up when trying to install and get everything going.  nothing happens when i type those codes in

---

### Post by endersshadow on 2006-04-13
[QUOTE=x5452]lol, i knew i must have messed something up when trying to install and get everything going.  nothing happens when i type those codes in[/QUOTE]

That means they worked :-D

Fun fact about Linux: It usually assumes that you're not an idiot, so it doesn't congradulate you when you do something right.  Instead, it only yells at you once you've done something wrong.

Your system is good to go :mrgreen:

---

### Post by x5452 on 2006-04-13
crap sorry, i should have clarified myself, all the program is stillthere, still in menu, still folders in home ect.

---

### Post by endersshadow on 2006-04-13
[QUOTE=x5452]crap sorry, i should have clarified myself, all the program is stillthere, still in menu, still folders in home ect.[/QUOTE]

Oh, right...my fault...do you want to uninstall Vive or ipodvidenc?  Knowing what you did, you don't have any bloat on your system as far as Vive installation is concerned (stuff overwrites itself...Linux is good about that).  As per the ipodvidenc menu, my fault for not doing it:

```
sudo rm /usr/share/pixmaps/ipodvidenc.xpm
sudo rm /usr/share/applications/ipodvidenc.desktop
killall gnome-panel
```

You can also cd to your home folder and run:

```
rm -rf ipodvidenc*
```

And if you want to remove the Vive source, just do this:

```
rm -rf vive*
```

Should be all set :-D

---

### Post by x5452 on 2006-04-14
ok thanks ill give that a go, no I dont want vive gone, its awsome now that you helped me set it up here, lol.  I just want to clean this system up as much as i can before i give it back to the owner, (all this and its not even mine, I dont even have an IPOD!) lol  thanks

---

### Post by endersshadow on 2006-04-14
Glad I could help out :-D

Would a "Beginner's Guide to the iPod and MP3 Players" be helpful, or is the information out there already and it would just be redundant?

---

### Post by x5452 on 2006-04-14
i think it would be very helpful to have all the info "consolidated" there is a lot of info, but I must have bookmared 15 different pages when going through stuff and its easy to get lost, so I think its a good idea.

(while your here), lol, what the hell is nautilus and whys it eat my memory like candy

---

### Post by endersshadow on 2006-04-14
Okay, I'll work on that :)

Erm, probably wrong thread, but as per Nautilus...it's your file manager and also handles drawing the desktop.  I've attached a screenshot of it in action.  But make sure that you're looking at *Resident* Memory and not *Virtual* Memory.  Suffice it to say that Virtual Memory is an inflated number than what is actually being used on your system...it's a long story, so I'll give it the short version.  Anyway, at idle, I've got Nautilus using 12MB of RM and 29.4MB of VM...so there's a difference.  Don't worry about it, but it's needed.  I've also included a screenshot of the system monitor, for good measure :)

---

### Post by Iandefor on 2006-04-30
'ello, Eric! I don't know if this has been posted yet, but someone made a .deb for vive. It's for Dapper, but Dapper's out in a month anyways.
 
[http://skulboxx.com/Ubuntu/sbx/]("http://skulboxx.com/Ubuntu/sbx/")
 
Looks like there's an "optimized" ffmpeg there, too.

---

### Post by endersshadow on 2006-04-30
[QUOTE=Iandefor]'ello, Eric! I don't know if this has been posted yet, but someone made a .deb for vive. It's for Dapper, but Dapper's out in a month anyways.
 
[http://skulboxx.com/Ubuntu/sbx/]("http://skulboxx.com/Ubuntu/sbx/")
 
Looks like there's an "optimized" ffmpeg there, too.[/QUOTE]

I've updated the main post, there, sweetie.  But thank you :-D

SBX was kind enough to email me about them...he made them via checkinstall, so use at your own risk, but they should work on every installation w/o trouble.

---

### Post by Iandefor on 2006-05-01
[quote=endersshadow]I've updated the main post, there, sweetie.  But thank you :-D

SBX was kind enough to email me about them...he made them via checkinstall, so use at your own risk, but they should work on every installation w/o trouble.[/quote] Like I'm gonna bother reading the rest of the damn thread ;)?

---

### Post by jms830 on 2006-05-02
I'm having some problems compiling the stuff for MP4box, is there a .deb or can anyone post/send me a .deb or something? thanks.

---

### Post by jms830 on 2006-05-04
just wanted to note that the new ipod firmware 1.1.1 supposedly fixes the video playback problems of 1.1,  So far, I haven't had the problem since I upgraded to 1.1.1

---

### Post by ubernoob on 2006-05-11
Well... your script didn't work. I tried it once. And it failed. Then when i tried again it failed on the same place.

Trying to revert the stuff the script did seems to be impossible....

Your script overwrote my original source list when i tried to run the script the second time :(

---

### Post by endersshadow on 2006-05-11
[QUOTE=ubernoob]Well... your script didn't work. I tried it once. And it failed. Then when i tried again it failed on the same place.

Trying to revert the stuff the script did seems to be impossible....

Your script overwrote my original source list when i tried to run the script the second time :([/QUOTE]

Could you please provide the error messages that you received?

Edit: To get your old sources.list back:

```
sudo mv /etc/apt/sources.list.bak /etc/apt/sources.list
```

---

### Post by ubernoob on 2006-05-11
there were several errors. One of them was about some xml parser. And the other was that [http://rarewares.org/debian/packages/unstable/mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb](http://rarewares.org/debian/packages/unstable/mpeg4ip-libs_1.2.5+cvs20050126.20-0.0_i386.deb) doesn't exist.

You should change your script to check if sources.list.ipodvidenc.bak exists. If it does, you shouldn't overwrite it. Because if the script hangs before you revert the original source from sources.list.ipodvidenc.bak and you run it again. You will overwrite the original source which is in sources.list.ipodvidenc.bak

> sudo mv /etc/apt/sources.list.bak /etc/apt/sources.list
I don't have that. But i think i have been able to restore it more or less like it was before this.

Does the script have anything that is not in the howto or the wiki? Should i try to run it again? Or is it waste of time? I'm about to finnish the rest of the stuff from the wiki now.

---

### Post by ubernoob on 2006-05-11
Error while following the wiki:

Selecting previously deselected package xml-parser-2.34.
(Reading database ... 168615 files and directories currently installed.)
Unpacking xml-parser-2.34 (from .../xml-parser-2.34_2.34-1_i386.deb) ...
dpkg: error processing /home/ubuntu/XML-Parser-2.34/xml-parser-2.34_2.34-1_i386.deb (--install):
 trying to overwrite `/usr/local/lib/perl/5.8.7/perllocal.pod', which is also in package vive
Errors were encountered while processing:
 /home/ubuntu/XML-Parser-2.34/xml-parser-2.34_2.34-1_i386.deb


The wiki doesn't say that i should rename it from "xml-parser-2.34" to "xml-parser". Should I always rename and remove the version when using checkinstall?

Edit: removing vive helped.

---

### Post by endersshadow on 2006-05-11
To get the XML Parser:

```
sudo apt-get install libxml-parser-perl
```

Try doing that, and then continuing on with the HowTo.  I'll recheck the Wiki.

---

### Post by ubernoob on 2006-05-12
I'm trying to convert some Episodes of Simpsons. When i right click on the films, it says:

DivX MS-MPEG-4 Version 3

Do you know how i convert them?

---

### Post by endersshadow on 2006-05-12
[QUOTE=ubernoob]I'm trying to convert some Episodes of Simpsons. When i right click on the films, it says:

DivX MS-MPEG-4 Version 3

Do you know how i convert them?[/QUOTE]

Try this command:

ffmpeg -i simpsons_movie.mpeg -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 output_movie.mov

And let me know what the output is.

---

### Post by ubernoob on 2006-05-13
it seems like that worked like it should! Thanks alot! Now i just need my ipod. I'm getting it in the mail on monday... can hardly wait :rolleyes:

---

### Post by ubernoob on 2006-05-14
Strange... some of the episodes works, but other doesn't:

This is the first, that works (i killed it thats why the sig term in the end): 
```
ubernoob@ubuntu:/data/ipodsimpsons$ ffmpeg -i Simpsons\ 15x01* -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 Simpsons_15x0111.mov
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid
  built on May 12 2006 20:42:40, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Input #0, avi, from 'Simpsons 15x01 - Treehouse of Horror XIV [rl].avi':
  Duration: 00:21:31.6, start: 0.000000, bitrate: 650 kb/s
  Stream #0.0: Video: msmpeg4, yuv420p, 320x240, 23.94 fps
  Stream #0.1: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Output #0, mp4, to 'Simpsons_15x0111.mov':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, 23.94 fps, q=3-5, 700 kb/s
  Stream #0.1: Audio: aac, 44100 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=  273 q=0.0 Lsize=     940kB time=11.4 bitrate= 675.1kbits/s
video:692kB audio:241kB global headers:0kB muxing overhead 0.773557%
Received signal 2: terminating.

```

The second which is coded with the same says:

```

ubernoob@ubuntu:/data/ipodsimpsons$ ffmpeg -i Simpsons\ 15x02* -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 Simpsons_15x02.mov
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid
  built on May 12 2006 20:42:40, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Input #0, avi, from 'Simpsons 15x02 - My Mother The Carjacker [rl].avi':
  Duration: 00:21:23.4, start: 0.000000, bitrate: 654 kb/s
  Stream #0.0: Video: msmpeg4, yuv420p, 320x240, 23.97 fps
  Stream #0.1: Audio: mp3, 44100 Hz, stereo, 128 kb/s
Output #0, mp4, to 'Simpsons_15x02.mov':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, 23.97 fps, q=3-5, 700 kb/s
  Stream #0.1: Audio: aac, 44100 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0x8334688]timebase not supported by mpeg 4 standard
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

---

### Post by endersshadow on 2006-05-14
[This](http://linuxfr.org/forums/9/13750.html) was the only info I could find on the matter, and it's in French.  Attempting to translate (I speak Spanish, not French :) ), the replier says that apparently the codec doesn't support certain timebases.

Other than that, I haven't been able to find any info :-|

---

### Post by Sir_Yaro on 2006-05-20
For everyone who has problems with mpeg4ip compilation:
mpeg4ip_1.4.1-3_i386.deb
gtkpod_0.99.4-1_i386.deb
[http://yaro.gdi.pl/deb/index.php](http://yaro.gdi.pl/deb/index.php)

both working under breezy

---

### Post by ubernoob on 2006-05-20
I'm having problems with the sound on my 5G videos. I have tried to install gpac, but someting has gone wrong:

```
ubernoob@ubuntu:/data/downloads/ipodsimpsons$ MP4Box -add Simpsons_15x01.mov Simpsons_15x01.mov
MP4Box: error while loading shared libraries: libgpac.so: cannot open shared object file: No such file or directory


ubernoob@ubuntu:/data/downloads/ipodsimpsons$ ls -l /usr/local/lib/libgpac*
-rwxr-xr-x 1 root root 2397496 2006-05-20 23:42 /usr/local/lib/libgpac-0.4.0.so
lrwxrwxrwx 1 root root      16 2006-05-20 23:42 /usr/local/lib/libgpac.so -> libgpac-0.4.0.so
-rw-r--r-- 1 root root 2799390 2006-05-20 23:41 /usr/local/lib/libgpac_static.a

```

---

### Post by Sir_Yaro on 2006-05-20
```

         "Please install MP4Box by running:
        ./install mp4box
Or, run the following commands by yourself:
        wget http://internap.dl.sourceforge.net/sourceforge/gpac/gpac-0.4.0-rc2.tar.gz
        wget http://internap.dl.sourceforge.net/sourceforge/gpac/gpac_extra_libs-0.4.0.tar.gz
        tar -zxf gpac-0.4.0-rc2.tar.gz
        tar -zxf  gpac_extra_libs-0.4.0.tar.gz
        cd gpac_extra_libs
        cp -r * ../gpac/extra_lib
        cd ../gpac
        chmod +x configure
        ./configure
        make lib
        make apps
        make install
        sudo cp bin/gcc/libgpac.so /usr/lib\n";


```
Did you do last step ?

---

### Post by ubernoob on 2006-05-21
Thanks. I hadn't done that. Where did you find that instruction? It wasn't on the first page here.

---

### Post by ubernoob on 2006-05-21
After you have used MP4Box, you should rename your files to mp4 instead of mov. Or else you won't be able to search/skip in the movie.

Does anyone know how to move some of the videos to "Music Videos"?

---

### Post by Sir_Yaro on 2006-05-21
[QUOTE=ubernoob]Thanks. I hadn't done that. Where did you find that instruction? It wasn't on the first page here.[/QUOTE]
It is in a viva configure file
```
[...]
print "Checking for MP4Box...";
$check{'mp4box'} = `MP4Box -h`;
if ($check{'mp4box'} =~ /not found/i || $check{'mp4box'} !~ /crypt/)
{
        print "Not found or incorrect version\n";
        die "Please install MP4Box by running:
        ./install mp4box
Or, run the following commands by yourself:
        wget http://internap.dl.sourceforge.net/sourceforge/gpac/gpac-0.4.0-rc2.tar.gz
        wget http://internap.dl.sourceforge.net/sourceforge/gpac/gpac_extra_libs-0.4.0.tar.gz
        tar -zxf gpac-0.4.0-rc2.tar.gz
        tar -zxf  gpac_extra_libs-0.4.0.tar.gz
        cd gpac_extra_libs
        cp -r * ../gpac/extra_lib
        cd ../gpac
        chmod +x configure
        ./configure
        make lib
        make apps
        make install
        sudo cp bin/gcc/libgpac.so /usr/lib\n";
}
else
{
        print "Found\n";
}

`perl Makefile.PL`;
[...]

```

---

### Post by Hikaru79 on 2006-05-26
Hi. Just got an iPod video, and this thread was perfect, but I'm getting an error that I cannot understand. It comes when I try to convert AVI files.

```
[wmv3 @ 0x8335bc8]This decoder is not supposed to produce picture. Dont report this as a bug!
[wmv3 @ 0x8335bc8]Profile value 2 is forbidden

```

I've tried a few different encode scripts, and I keep getting this.

Any ideas?

---

### Post by Iandefor on 2006-05-27
[quote=Hikaru79]Hi. Just got an iPod video, and this thread was perfect, but I'm getting an error that I cannot understand. It comes when I try to convert AVI files.

```
[wmv3 @ 0x8335bc8]This decoder is not supposed to produce picture. Dont report this as a bug!
[wmv3 @ 0x8335bc8]Profile value 2 is forbidden

``` 
I've tried a few different encode scripts, and I keep getting this.

Any ideas?[/quote] That output is from the decoder- which is for wmv. Try encoding in formats other than wmv.

---

### Post by Hikaru79 on 2006-05-27
[quote=Iandefor]That output is from the decoder- which is for wmv. Try encoding in formats other than wmv.[/quote] 
That doesn't really solve the problem, as the files are in AVI (wmv?) format to begin with. Is there a fix?

--edit--
Doesn't seem to like the matroska wrapper either. 

```
 hikaru@navi:/multimedia/animanga/anime/Ghost in the Shell - Standalone Complex$ ipod-encoder -tfv /multimedia/animanga/anime/Ghost\ in\ the\ Shell\ -\ Standalone\ Complex/\[a4e\]Ghost_in_Shell_TV_02\[divx5.2.0\].mkv
Encoding:  /multimedia/animanga/anime/Ghost in the Shell - Standalone Complex/[a4e]Ghost_in_Shell_TV_02[divx5.2.0].mkv
--> iPod video, 2891148206x1305088130:
  /multimedia/animanga/anime/Ghost in the Shell - Standalone Complex/[a4e]Ghost_in_Shell_TV_02[divx5.2.0].mkv
  Converting to iPod: 480x208
ffmpeg -i "/multimedia/animanga/anime/Ghost in the Shell - Standalone Complex/[a4e]Ghost_in_Shell_TV_02[divx5.2.0].mkv" -r 20 -t 00:00:10 -y -vcodec xvid -vtag mp4v -b 1024 -acodec aac -ac 2 -ab 128 -f mp4 -s 480x208 "/multimedia/animanga/anime/Ghost in the Shell - Standalone Complex/[a4e]Ghost_in_Shell_TV_02[divx5.2.0].mkv"
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid
  built on May 26 2006 10:17:36, gcc: 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
[matroska @ 0x82c7660]Ignoring seekhead entry for ID=0x1549a966
[matroska @ 0x82c7660]Ignoring seekhead entry for ID=0x1654ae6b
[matroska @ 0x82c7660]Ignoring seekhead entry for ID=0x114d9b74
[matroska @ 0x82c7660]Ignoring seekhead entry for ID=0x1043a770
[matroska @ 0x82c7660]Unknown entry 0x7ba9 in info header
[matroska @ 0x82c7660]Unknown entry 0x73a4 in info header
[matroska @ 0x82c7660]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x82c7660]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x82c7660]Unknown audio track header entry 0x78b5 - ignoring
[matroska @ 0x82c7660]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x82c7660]Unknown audio track header entry 0x78b5 - ignoring
[matroska @ 0x82c7660]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x82c7660]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x82c7660]Unknown track header entry 0x6d80 - ignoring
[matroska @ 0x82c7660]Unknown track header entry 0x23314f - ignoring
[matroska @ 0x82c7660]Unknown track header entry 0x6d80 - ignoring
[matroska @ 0x82c7660]Unknown matroska file header ID 0x1043a770
[matroska @ 0x82c7660]Unknown/unsupported CodecID A_AAC/MPEG4/LC/SBR.
[matroska @ 0x82c7660]Unknown/unsupported CodecID A_AAC/MPEG4/LC/SBR.

Seems that stream 0 comes from film source: 1000.00 (1000/1) -> 24.00 (24/1)
Input #0, matroska, from '/multimedia/animanga/anime/Ghost in the Shell - Standalone Complex/[a4e]Ghost_in_Shell_TV_02[divx5.2.0].mkv':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Video: mpeg4, yuv420p, 640x352, 1000.00 fps
  Stream #0.1: Audio: 0x0000, 22050 Hz, 5:1
  Stream #0.2: Audio: 0x0000, 22050 Hz, 5:1
Resampling with input channels greater than 2 unsupported.Can't resample.  Aborting.
Abort at ffmpeg.c:1704
```

---

### Post by drobvice on 2006-06-03
I have been using Vive to convert some avi videos I...uh...obtained and it fails if there is a space in the title.  I did not have this issue with the ipodvidenc script or the 1.5 gui.  So if it was called, say, "24 Season 2 Episode 3", Vive would not convert it but if I replace all spaces with an _ underscore, it would work fine.  Is there a way around this?  I don't mind renaming files but if I have many episodes to do (something like 24 of them) it gets cumbersome.  And like I said, it wasn't a problem with ipodvidenc.  Failing that, is there an easy way to replace spaces with underscores in a folder full of files?

---

### Post by endersshadow on 2006-06-03
[QUOTE=drobvice]I have been using Vive to convert some avi videos I...uh...obtained and it fails if there is a space in the title.  I did not have this issue with the ipodvidenc script or the 1.5 gui.  So if it was called, say, "24 Season 2 Episode 3", Vive would not convert it but if I replace all spaces with an _ underscore, it would work fine.  Is there a way around this?  I don't mind renaming files but if I have many episodes to do (something like 24 of them) it gets cumbersome.  And like I said, it wasn't a problem with ipodvidenc.  Failing that, is there an easy way to replace spaces with underscores in a folder full of files?[/QUOTE]

This is a bug fix that's coming within the week in the next Vive, I'm just packaging it up right now, but if you can't wait that long, do this:

```
sudo gedit /usr/bin/vive
```

And then right after line 72, which is this:

```
$ffmpeginfo{'infile'} = $file_input->get_text();
```

Insert this:

```
$ffmpeginfo{'infile'} =~ s/\ /\\\ /g;
```

And then after the next line (the output line), just do this:

```
$ffmpeginfo{'output'} =~ s/\ /\\\ /g;
```

So that the entire block of code should look like (starting at line 72):

```
$ffmpeginfo{'infile'} = $file_input->get_text();
$ffmpeginfo{'infile'} =~ s/\ /\\\ /g;
$ffmpeginfo{'output'} = $output_entry->get_text();
$ffmpeginfo{'output'} =~ s/\ /\\\ /g;
```

And that be that.

---

### Post by drobvice on 2006-06-03
I haven't tried inserting the code yet but thanks!!  Looking forward to the next release.

---

### Post by endersshadow on 2006-06-04
News:

Vive 0.3 Beta 2 released today!  Grab it at [vive.sourceforge.net](http://vive.sourceforge.net)!

---

### Post by drobvice on 2006-06-05
I get the following on ./configure:

desktop:~/Download/vive-0.3$ ./configure
syntax error at ./configure line 119, near "/."
Execution of ./configure aborted due to compilation errors.

---

### Post by INMCM on 2006-06-05
Ditto on the Line 119 error. Tried to fiddle with the code to make it work, but no go.

---

### Post by endersshadow on 2006-06-05
I've reuploaded the file to Sourceforge and attached it here.

You can simply right click and save as in the Vive-0.3 directory, then do this:

```
mv configure.txt configure
chmod 755 configure
```

Then proceed w/ the ./configure etc...sorry about that!

Edit: Fixed it...seriously.

---

### Post by drobvice on 2006-06-06
I followed above instructions and got this:

desktop:~/Download/vive-0.3$ ./configure
Bareword found where operator expected at ./configure line 119, near "/vive/preferences"
        (Missing operator before preferences?)
syntax error at ./configure line 119, near "/vive/preferences"
Execution of ./configure aborted due to compilation errors.

I tried downloading the current 0.3 beta 2 and starting over and got the same message as before:

desktop:~/Download/vive-0.3$ ./configure
syntax error at ./configure line 119, near "/."
Execution of ./configure aborted due to compilation errors.

---

### Post by endersshadow on 2006-06-06
You know those days you have when you do something quick because you think you've diagnosed the problem and then you realize that you, in fact, have only made said problem worse when it was a simple problem to begin with?  That was yesterday.

It's seriously fixed this time.  I tested it...something I failed to do after adding that part twice...lesson: learned.

---

### Post by drobvice on 2006-06-07
Trust me.  You will get no complaints from me.  Looking forward to trying it out (at work right now).  Out of curiosity, what was wrong?  I looked at the code and tried to "fix" it but the missing operator I had no clue on...I know nothing about writing code at all.

---

### Post by endersshadow on 2006-06-07
[QUOTE=drobvice]Trust me.  You will get no complaints from me.  Looking forward to trying it out (at work right now).  Out of curiosity, what was wrong?  I looked at the code and tried to "fix" it but the missing operator I had no clue on...I know nothing about writing code at all.[/QUOTE]

I forgot to put the path name in quotes :oops:

---

### Post by ubernoob on 2006-06-08
last time i tried to convert a dvd in widescreen to the ipod, it stretches the image, instead of making a black border on the top and bottom. Do you know how to keep the original aspect ratio?

---

### Post by endersshadow on 2006-06-08
[QUOTE=ubernoob]last time i tried to convert a dvd in widescreen to the ipod, it stretches the image, instead of making a black border on the top and bottom. Do you know how to keep the original aspect ratio?[/QUOTE]

Either specify the Aspect Ratio in Vive or leave it blank and it will take it from the video.

---

### Post by drobvice on 2006-06-09
I created a profile for iPod Widescreen on my copy.  Change aspect to 16:9 and make it 180x320.  Don't forget to save a .mp4 for scrolling on the pod!

*Edit*

enders, would you like bug/feature requests submitted to this thread or sourceforge?

---

### Post by endersshadow on 2006-06-09
[QUOTE=drobvice]I created a profile for iPod Widescreen on my copy.  Change aspect to 16:9 and make it 180x320.  Don't forget to save a .mp4 for scrolling on the pod!

*Edit*

enders, would you like bug/feature requests submitted to this thread or sourceforge?[/QUOTE]

This thread, a PM, or my email box at endersshadow at users dot sourceforge dot net would probably be best, since those are the things I check most often :)

---

### Post by drobvice on 2006-06-09
When I choose an avi file to convert, the preview button chokes.  If I run from terminal, I get no messages and have to force quit the app.  Also, the version number still shows 0.1 alpha 2 in help-->about.  Let me know if this is an error with my setup or if it's working for you.

---

### Post by endersshadow on 2006-06-09
[QUOTE=drobvice]When I choose an avi file to convert, the preview button chokes.  If I run from terminal, I get no messages and have to force quit the app.  Also, the version number still shows 0.1 alpha 2 in help-->about.  Let me know if this is an error with my setup or if it's working for you.[/QUOTE]

The Help->About thing is definitely not something wrong with your setup...solamente my laziness.  As per the AVI file, I'm not at my computer right now and I'm on a Windows 2000 box, so testing it is not in the works for me tonight.  If you could run the file through ffmpeg via the command line just to get what its video and audio input codecs are and post that output here, that'd be a helpful, as AVI is just a container format.

Thanks!

---

### Post by ubernoob on 2006-06-10
im trying to copy a dvd from a iso image. 

I mount the iso with: mount -o loop -t iso9660 file.iso /media/virtualdisc

So in vive, i have set both the device and mount point to be /media/virtualdisc in its own profile. (Btw... why do all the profile have to have the same device? If i change one, they all changes)


I only get this error message:

```

Use of uninitialized value in substitution (s///) at /usr/bin/cpdvd line 76.
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 robos@muon.de
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

path to dvd: /dev/loop0
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Could not open /dev/loop0 with libdvdcss.
libdvdread: Can't open /dev/loop0 for reading

[Error] Path thingy didn't work '(null)'
[Error] Try someting like -i /cdrom, /dvd  or /mnt/dvd
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid
  built on May 20 2006 21:01:41, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
/data/vive_dvd_temp*.vob: I/O error occured
Usually that means that input file is truncated and/or corrupted.

```

---

### Post by drobvice on 2006-06-10
[QUOTE=endersshadow]If you could run the file through ffmpeg via the command line just to get what its video and audio input codecs are and post that output here, that'd be a helpful, as AVI is just a container format.

Thanks![/QUOTE]

The video converts with no problems.  It's just that the preview doesn't work.  I think it just opens totem to play but that isn't happening.  Previously, I would get a message regarding not being able to find the file due to the spaces present but now it doesn't.

---

### Post by endersshadow on 2006-06-11
[QUOTE=ubernoob]im trying to copy a dvd from a iso image. 

I mount the iso with: mount -o loop -t iso9660 file.iso /media/virtualdisc

So in vive, i have set both the device and mount point to be /media/virtualdisc in its own profile. (Btw... why do all the profile have to have the same device? If i change one, they all changes)


I only get this error message:

```

Use of uninitialized value in substitution (s///) at /usr/bin/cpdvd line 76.
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 robos@muon.de
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

path to dvd: /dev/loop0
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Could not open /dev/loop0 with libdvdcss.
libdvdread: Can't open /dev/loop0 for reading

[Error] Path thingy didn't work '(null)'
[Error] Try someting like -i /cdrom, /dvd  or /mnt/dvd
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid
  built on May 20 2006 21:01:41, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
/data/vive_dvd_temp*.vob: I/O error occured
Usually that means that input file is truncated and/or corrupted.

```[/QUOTE]

Quite frankly, I never foresaw this occurance.  The setting is global for all presets, since it just sets the node and path to your DVD for cpdvd, though in Dapper, the node will become obsolete, I've left it in for those running legacy software.  I'll look at including it in the next release

[QUOTE=drobvice]The video converts with no problems.  It's just that the preview doesn't work.  I think it just opens totem to play but that isn't happening.  Previously, I would get a message regarding not being able to find the file due to the spaces present but now it doesn't.[/QUOTE]

If you'd like to fix this, you can edit it yourself (and thanks for the bug find, btw):

After line 1600, which is this:

```
my $file_play = $file_input->get_text();
```

Simply add this line:

```
$file_play =~ s/\ /\\\ /g;
```

And all will be fixed :-D

---

### Post by ubernoob on 2006-06-13
More to debug: :D

```
Use of uninitialized value in substitution (s///) at /usr/bin/cpdvd line 76.
WARNING **: invalid source position for horizontal gradient
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 robos@muon.de
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

path to dvd: /dev/hdc
libdvdread: Using libdvdcss version 1.2.5 for DVD access
There are 12 titles on this DVD.
[Error] Invalid title 0.
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid
  built on May 20 2006 21:01:41, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
/home/vive_dvd_temp*.vob: I/O error occured
Usually that means that input file is truncated and/or corrupted.

```


Btw if you find a way that i can copy directly from iso, that would be greate!

---

### Post by hanzomon4 on 2006-07-17
This is really neat.
I have an error on an some avi files can't make an any sense of it.
```
.avi':
  Duration: 01:14:06.4, start: 0.000000, bitrate: 1154 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 704x464, 30000.00 fps
  Stream #0.1: Audio: mp3, 44100 Hz, stereo, 128 kb/s
File '/home/hanzomon4/test.mov' already exists. Overwrite ? [y/N] y
Output #0, mp4, to '/home/hanzomon4/test.mov':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, 29.97 fps, q=3-5, 700 kb/s
  Stream #0.1: Audio: aac, 44100 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0x83346a8]timebase not supported by mpeg 4 standard
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```

---

### Post by endersshadow on 2006-07-17
> **hanzomon4 said:**
> This is really neat.
I have an error on an some avi files can't make an any sense of it.
```
.avi':
  Duration: 01:14:06.4, start: 0.000000, bitrate: 1154 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 704x464, 30000.00 fps
  Stream #0.1: Audio: mp3, 44100 Hz, stereo, 128 kb/s
File '/home/hanzomon4/test.mov' already exists. Overwrite ? [y/N] y
Output #0, mp4, to '/home/hanzomon4/test.mov':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, 29.97 fps, q=3-5, 700 kb/s
  Stream #0.1: Audio: aac, 44100 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0x83346a8]timebase not supported by mpeg 4 standard
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```

What parameters did you use when trying to encode this?

---

### Post by hanzomon4 on 2006-07-18
None. I had no idea you could set parameters.
I'll try that video again see if I can get it work.

---

### Post by OrganicPanda on 2006-07-18
hey this sounds really good but following the guide i'm having install problems, par example:

the configure stage works well up untill:

```

...snip...
gcc -O3 -Wall -Wno-switch  -DHAVE_AV_CONFIG_H -I.. -I'/home/panda/ffmpeg-0.cvs20050918'/libavutil -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE    -c -o faad.o faad.c
faad.c:29:18: error: faad.h: No such file or directory
faad.c:57: error: syntax error before ‘faacDecHandle’
faad.c:57: warning: no semicolon at end of struct or union
faad.c:58: error: syntax error before ‘*’ token
faad.c:58: error: syntax error before ‘hDecoder’
faad.c:58: warning: type defaults to ‘int’ in declaration of ‘faacDecConfigurationPtr’
faad.c:58: error: ‘faacDecConfigurationPtr’ declared as function returning a function
faad.c:58: warning: data definition has no type or storage class
faad.c:60: error: syntax error before ‘hDecoder’
faad.c:62: error: syntax error before ‘hDecoder’
faad.c:66: error: syntax error before ‘hDecoder’
faad.c:69: error: syntax error before ‘hDecoder’
faad.c:92: error: syntax error before ‘hDecoder’
faad.c:95: warning: type defaults to ‘int’ in declaration of ‘FAACContext’
faad.c:95: warning: data definition has no type or storage class
faad.c: In function ‘faac_init_mp4’:
faad.c:105: error: ‘s’ undeclared (first use in this function)
faad.c:105: error: (Each undeclared identifier is reported only once
faad.c:105: error: for each function it appears in.)
faad.c:105: error: syntax error before ‘)’ token
faad.c: In function ‘faac_decode_frame’:
faad.c:133: error: ‘s’ undeclared (first use in this function)
faad.c:133: error: syntax error before ‘)’ token
faad.c:136: warning: unused variable ‘sample_buffer’
faad.c: In function ‘faac_decode_end’:
faad.c:179: error: ‘s’ undeclared (first use in this function)
faad.c:179: error: syntax error before ‘)’ token
faad.c: In function ‘faac_decode_init’:
faad.c:190: error: ‘s’ undeclared (first use in this function)
faad.c:190: error: syntax error before ‘)’ token
faad.c:212: error: ‘faacDecOpen’ undeclared (first use in this function)
faad.c:213: error: ‘faacDecGetCurrentConfiguration’ undeclared (first use in this function)
faad.c:260: error: ‘faac_cfg’ undeclared (first use in this function)
faad.c:287: error: ‘LC’ undeclared (first use in this function)
make[1]: *** [faad.o] Error 1
make[1]: Leaving directory `/home/panda/ffmpeg-0.cvs20050918/libavcodec'
make: *** [lib] Error 2


```

what can i do to remedy this?
cheers,


EDIT: i got vive working from the sbx packages but when trying to use it the encode button doesnt work lol, it looks like an excellent program aswell](*,)

---

### Post by hanzomon4 on 2006-07-18
> **endersshadow said:**
> What parameters did you use when trying to encode this?

I am  using the parameters in the ipodvidence script ```
 -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 test.mo
```

Could it have some thing to do with the bitrate being to high, for this perticular video the bitrate  is  ```
bitrate: 1154 kb/s
```

Also in all of the videos seeking does not work

EDIT: The seek problem is with gtkpod > #  Mark Duncan Says:
December 24th, 2005 at 8:40 pm

Getting movies to ffw and rew with gtkpod:

Drag your movie over to your iPod with gtkpod
Right-click on the movie and click on “Edit details”
Go to the “General” tab and set the play time.
Click Apply and OK.
Sync

The problems comes from gtkpod setting a 0:00 play time for all movies. Manually setting it has worked for every movie I put on so far. I will see about making a patch so gtkpod does this automatically tomorrow.

EDIT Again:I fixed all of my problems even the seek problem by changing the the command at the end of the ipodvidenc to this ```
ffmpeg -vcodec xvid -b 300  -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 96 -i "${input_file}"  -s 320x240 -aspect 4:3  "${output_dir}/${output_file_name}.mp4"

```
I found the command at this [website]("http://atomized.org/2005/11/converting-video-to-play-on-your-ipod-with-ffmpeg/")
I'm not sure what all of the parameters mean but it has a higher buffer size(so that fixed my first problem)and all of the videos had the correct play time(fixing the seek issue with out editing the play time in gtkpod).

If anybody with a better understanding of ffmpeg could explain what the options mean and why it fixed my problems I would greatly  appreciate it.

Okay I think thats all.

---

### Post by jms830 on 2006-07-19
whenever I try to install vive 0.3 from source, it tells me I need mp4box. so then i follow the instructions to install gpac. however, it always fails when I "make install", I think due to some errors from the other make commands. Any help? Or maybe someone could post a .deb for the new vive?  Here is my output

```
sudo make install
install -d "/usr/local/bin"
install -c -s -m 755 bin/gcc/MP4Box "/usr/local/bin"
install -c -s -m 755 bin/gcc/MP42Avi "/usr/local/bin"
make -C applications install
make[1]: Entering directory `/home/jordan/Desktop/vive-0.3/gpac/applications'
for i in mp4client osmozilla ; do make -C $i install; done
make[2]: Entering directory `/home/jordan/Desktop/vive-0.3/gpac/applications/mp4client'
rm -f main.o  ../../bin/gcc/MP4Client
make -override BUILD_INSTALL=yes all
make[3]: Entering directory `/home/jordan/Desktop/vive-0.3/gpac/applications/mp4client'
gcc -O3 -fno-strict-aliasing -Wall -I/home/jordan/Desktop/vive-0.3/gpac/include -DGPAC_MODULES_PATH=\"/usr/local/lib/gpac\" -c -o main.o main.c
gcc -Wl,--warn-common -o ../../bin/gcc/MP4Client main.o  -L../../bin/gcc -lgpac
make[3]: Leaving directory `/home/jordan/Desktop/vive-0.3/gpac/applications/mp4client'
install -c -s -m 755 ../../bin/gcc/MP4Client "/usr/local/bin"
make[2]: Leaving directory `/home/jordan/Desktop/vive-0.3/gpac/applications/mp4client'
make[2]: Entering directory `/home/jordan/Desktop/vive-0.3/gpac/applications/osmozilla'
g++ -O3 -fno-strict-aliasing -Wall -I/home/jordan/Desktop/vive-0.3/gpac/include -I/home/jordan/Desktop/vive-0.3/gpac/extra_lib/include/gecko-sdk -I/home/jordan/Desktop/vive-0.3/gpac/extra_lib/include/gecko-sdk/plugin/include -I/home/jordan/Desktop/vive-0.3/gpac/extra_lib/include/gecko-sdk/nspr/include -I/home/jordan/Desktop/vive-0.3/gpac/extra_lib/include/gecko-sdk/java/include -I/home/jordan/Desktop/vive-0.3/gpac/extra_lib/include/gecko-sdk/xpcom/include  -DXP_UNIX -DMOZ_X11 -DNPBASIC_EXPORTS -DMOZILLA_STRICT_API -DXPCOM_GLUE -c -o osmozilla.o osmozilla.cpp
In file included from osmozilla.cpp:44:
osmozilla.h:50:27: error: X11/Intrinsic.h: No such file or directory
/home/jordan/Desktop/vive-0.3/gpac/extra_lib/include/gecko-sdk/xpcom/include/nsISupportsBase.h:80: warning: ‘class nsISupports’ has virtual functions but non-virtual destructor
/home/jordan/Desktop/vive-0.3/gpac/extra_lib/include/gecko-sdk/xpcom/include/nsIServiceManager.h:40: warning: ‘class nsIServiceManager’ has virtual functions but non-virtual destructor
/home/jordan/Desktop/vive-0.3/gpac/extra_lib/include/gecko-sdk/xpcom/include/nsIMemory.h:54: warning: ‘class nsIMemory’ has virtual functions but non-virtual destructor
/home/jordan/Desktop/vive-0.3/gpac/extra_lib/include/gecko-sdk/xpcom/include/nsIProgrammingLanguage.h:32: warning: ‘class nsIProgrammingLanguage’ has virtual functions but non-virtual destructor
/home/jordan/Desktop/vive-0.3/gpac/extra_lib/include/gecko-sdk/xpcom/include/nsIClassInfo.h:33: warning: ‘class nsIClassInfo’ has virtual functions but non-virtual destructor
nsIOsmozilla.h:25: warning: ‘class nsIOsmozilla’ has virtual functions but non-virtual destructor
osmozilla.h:68: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
osmozilla.h:178: error: ‘Widget’ does not name a type
osmozilla.h:201: warning: ‘class nsClassInfoMixin’ has virtual functions but non-virtual destructor
osmozilla.cpp: In constructor ‘nsOsmozillaInstance::nsOsmozillaInstance(nsPluginCreateData*)’:
osmozilla.cpp:171: error: ‘mXtwidget’ was not declared in this scope
make[2]: *** [osmozilla.o] Error 1
make[2]: Leaving directory `/home/jordan/Desktop/vive-0.3/gpac/applications/osmozilla'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/jordan/Desktop/vive-0.3/gpac/applications'
make: *** [install] Error 2

```

---

### Post by ringjp on 2006-07-19
I just went through this tutorial step-by-step and everything seemed to go okay.  However, now I'm trying to install Vive and I'm hitting the following error while trying to configure Vive:

```
The program ffmpeg has been installed, but it does not have the optimal configuration for Vive.  Run:
        ./install ffmpeg

This will activate the Vive install script to install ffmpeg.  If you prefer to compile it yourself, the optimal configuration for Vive is:
        ./configure --enable-gpl --enable-pp --enable-zlib \
                --enable-vorbis --enable-libogg --enable-theora \
                --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm\
                --disable-debug --enable-mp3lame --enable-faad\
                --enable-faac --enable-xvid --enable-ogm
You may continue on with installing Vive and install an updated ffmpeg later, if you so choose, as well.
Checking for vobcopy...Can't exec "vobcopy": No such file or directory at ./configure line 41.
Use of uninitialized value in pattern match (m//) at ./configure line 42.
Found
Checking for cpdvd...Use of uninitialized value in pattern match (m//) at ./configure line 54.
Checking for MP4Box...Can't exec "MP4Box": No such file or directory at ./configure line 61.
Use of uninitialized value in pattern match (m//) at ./configure line 62.
Use of uninitialized value in pattern match (m//) at ./configure line 62.
Not found or incorrect version
Please install MP4Box by running:
        ./install mp4box
Or, run the following commands by yourself:
        wget http://internap.dl.sourceforge.net/sourceforge/gpac/gpac-0.4.0-rc2.tar.gz
        wget http://internap.dl.sourceforge.net/sourceforge/gpac/gpac_extra_libs-0.4.0.tar.gz
        tar -zxf gpac-0.4.0-rc2.tar.gz
        tar -zxf  gpac_extra_libs-0.4.0.tar.gz
        cd gpac_extra_libs
        cp -r * ../gpac/extra_lib
        cd ../gpac
        chmod +x configure
        ./configure
        make lib
        make apps
        make install
        sudo

 cp bin/gcc/libgpac.so /usr/lib

```

It seemed like ffmpeg installed just fine.  Any ideas?  BTW, I'm kind of a newbie...

Edit: Never mind, I fixed it.

---

### Post by endersshadow on 2006-07-21
Hey guys, I apologize profusely, but I've had (and have) some unfortunate family matters to attend to, so I won't be able to get back to y'all until August.  I really apologize, but sometimes, family trumps all.

I'll do this as quick as I can, but I apologize if it's not enough:

@hanzo: ffmpeg commands and their functions can be found [here](http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html).

@jms: If you are not using the 1.1 version of the iPod Video 60GB firmware, you will not need MP4Box.  Simply comment out (or delete) those lines from the configure script and all will run smoothly.  The newest version of the iPod Video 60GB (1.2) does, in fact, fix this problem.  It was an heinous oversight on my part and I absolutely apologize for it.  Sometimes, developers deserve slaps on the wrist, and this is one of those times.  When Vive goes final release, the installation process is something I am definitely going to focus on.  I'm letting people test it and seeing what bugs come in now.  For the most part, it's been with MP4Box, so I will do my best to update that and make that seamless.  Unfortunately, video encoding is a messy process and sometimes us developers don't make it as easy as it should be :)

@ring: Glad you fixed it :)

---

### Post by ringjp on 2006-07-22
Endershadow,

You've done some great work and we really appreciate it.  I hope the family matters work out for you (family definitely comes first).

---

### Post by dyssident on 2006-07-26
your origional settings are confirmed working with the Samsung t809 phone..

for reference (pasted from my script):

AB = 192		# audio bitrate kbit/s (default=64)
B = 700			# video bitrate kbit/s (default=200kbs)
MAXRATE = 1000 		# max video bitrate in kbit/s; max 2500 for mpeg4
ACODEC = aac		# audio codec
ASPECT = 4:3		# aspect ratio
BUFSIZE = 4096		# rate control buffer size
F = mp4		# container file type
G = 300		# GOP size
S = 320x240		# video dimension
QMAX = 5		# maximum video quantiser scale
QMIN = 3		# minimum video quantiser scale
VCODEC = mpeg4		# video codec; should only ever be mpeg4 or xvid

---

### Post by coreyt on 2006-08-02
For the love of god..


Please get this added to Automatix :)



Tried and half these packages will not install on Default install.  I assume you need other repositories.

---

### Post by endersshadow on 2006-08-03
> **coreyt said:**
> For the love of god..


Please get this added to Automatix :)



Tried and half these packages will not install on Default install.  I assume you need other repositories.

Iandefor has been kind enough to supply it in BUMPS for Dapper.  Since I kind of upset the Automatix people by calling them temporary fools (i.e.-fools for a temporary time, they certainly aren't characteristically foolish) a little while ago, I doubt that Vive is anywhere near their radar, but hey, whatever.  My own doing.  Anyway, here's the [BUMPS thread](http://ubuntuforums.org/showthread.php?t=181251).

Edit: I apologize for this stuff being a bit convoluted.  Because of the codecs and legalities, and how very, very messy video encoding is at the moment, this stuff can just get a lot a bit wacky.  Once you throw in firmware bugs and manufacturing guffaws, it just gets messier (hence the reason for MP4Box).  Once I get around to it, I'm really going to focus on the installation process, as that is what seems to be the biggest problem.  Basically, the program is feature complete and functional, people just have a tough time getting it up and running.  And for that, I'm going to do everything I can to fix that once I finally get some time on my hands.  Again, in the words of the late Kurt Cobain, "all apologies."

---

### Post by coreyt on 2006-08-04
I'm having hell of a time with this program.

First you have to redo ffmpeg (Why is it this way in the repo's in the first place.  Recompiled version just enables more options)

Second tried HandBrake, but have no idea where to get jam from.

There used to be a package for Vive which looks great, but I cant get it to compile.  Asks for other stuff to be compiled from source.  I'd rather have a package to deal with.

I used to build rpm's for Suse/Fedora for gaim on the 64 bit platforms for awhile.  I'm just learning on how dpkg handles things.  I could host the packages I believe.  I currently have 300g of transfer a month and I can stretch that with torrents possibly.  I hardly use more than 100m of that bandwidth nowdays.

I have an iPod Video I would love to be able to rip dvd's to it on this machine since it's a dual core AMD X2 and I'd like to see it doing me some good.  Takes hours for handbrake to do that on my g4 mac mini.

---

### Post by coreyt on 2006-08-04
Oh hey about the BUMPS.


Vive is not in there at all and it always fails on downloading packages.

I'd love to see what packages need enhancements so I can see about how we can get them put into the dapper main branches.  Better for those who dont want to use multiverse or outside sources.

---

### Post by mrpeanut on 2006-08-07
After trying several times to get this to work, and searching for related errors, it's time for me to just ask.  Every time I put in the code 'make' I get this is as the output, and the process fails. Does anybody have any ideas?

```
tmr7@tidbit-laptop:~/mpeg4ip-1.4.1$ make
make  all-recursive
make[1]: Entering directory `/home/tmr7/mpeg4ip-1.4.1'
Making all in include
make[2]: Entering directory `/home/tmr7/mpeg4ip-1.4.1/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/tmr7/mpeg4ip-1.4.1/include'
Making all in lib
make[2]: Entering directory `/home/tmr7/mpeg4ip-1.4.1/lib'
Making all in utils
make[3]: Entering directory `/home/tmr7/mpeg4ip-1.4.1/lib/utils'
source='config_opts.cpp' object='config_opts.lo' libtool=yes \
        DEPDIR=.deps depmode=none /bin/sh ../../depcomp \
        /bin/sh ../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../include   -D_REENTRANT -fexceptions -Wall  -DMPEG4IP -I/usr/include/SDL -D_REENTRANT -c -o config_opts.lo config_opts.cpp
libtool: ignoring unknown tag CXX
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../include -D_REENTRANT -fexceptions -Wall -DMPEG4IP -I/usr/include/SDL -D_REENTRANT -c config_opts.cpp  -fPIC -DPIC -o .libs/config_opts.o
../../libtool: line 1223: g++: command not found
make[3]: *** [config_opts.lo] Error 1
make[3]: Leaving directory `/home/tmr7/mpeg4ip-1.4.1/lib/utils'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tmr7/mpeg4ip-1.4.1/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tmr7/mpeg4ip-1.4.1'
make: *** [all] Error 2
```

---

### Post by endersshadow on 2006-08-07
mrpeanut, what's your ./configure command and output look like?

---

### Post by mrpeanut on 2006-08-07
Thanks for the quick response endersshadow.  It seems that at a certain point the terminal stops displaying some of the information that it feeds out.  The ./config output was cut short by it.  I'll display what I have.  If there is a way for it to store more, or maybe log so I can go back and copy the whole ouput over just let me know. As for the output, here is what I have.

```
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for inline... inline
checking for an ANSI C-conforming const... yes
checking whether we are using the GNU C++ compiler... (cached) no
checking whether g++ accepts -g... (cached) no
checking dependency style of g++... (cached) none
checking for a BSD-compatible install... /usr/bin/install -c
checking for working alloca.h... yes
checking for alloca... yes
checking for dlopen... yes
checking for dlopen in -lc... no
checking for dlopen in -ldl... yes
checking for OSS audio support... yes
checking for ALSA CFLAGS...
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 0.9.0... found.
checking for snd_ctl_open in -lasound... yes
-- /usr/lib/libasound.so.* -> libasound.so.2
checking for dlvsym... yes
checking for artsc-config... /usr/bin/artsc-config
checking for aRts development environment... yes
-- /usr/lib/libartsc.so.* -> libartsc.so.0
checking for esd-config... /usr/bin/esd-config
checking for ESD - version >= 0.2.8... yes
-- /usr/lib/libesd.so.* -> libesd.so.0
checking for NAS audio support... no
checking for Linux 2.4 unified input interface... yes
checking for pthreads... yes
checking for recursive mutexes... yes
checking for pthread semaphores... yes
checking for broken glibc 2.0 pthreads... no
checking whether semun is defined in /usr/include/sys/sem.h... no
checking sigaction... yes
checking for GCC Altivec instruction support... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating include/Makefile
config.status: creating src/Makefile
config.status: creating src/audio/Makefile
config.status: creating src/audio/alsa/Makefile
config.status: creating src/audio/arts/Makefile
config.status: creating src/audio/baudio/Makefile
config.status: creating src/audio/dc/Makefile
config.status: creating src/audio/disk/Makefile
config.status: creating src/audio/dma/Makefile
config.status: creating src/audio/dmedia/Makefile
config.status: creating src/audio/dsp/Makefile
config.status: creating src/audio/esd/Makefile
config.status: creating src/audio/macrom/Makefile
config.status: creating src/audio/mint/Makefile
config.status: creating src/audio/mme/Makefile
config.status: creating src/audio/nas/Makefile
config.status: creating src/audio/nto/Makefile
config.status: creating src/audio/openbsd/Makefile
config.status: creating src/audio/paudio/Makefile
config.status: creating src/audio/riscos/Makefile
config.status: creating src/audio/sun/Makefile
config.status: creating src/audio/ums/Makefile
config.status: creating src/audio/windib/Makefile
config.status: creating src/audio/windx5/Makefile
config.status: executing depfiles commands
configure: configuring in lib/rtp
configure: running /bin/sh './configure' --prefix=/usr/local  --cache-file=/dev/null --srcdir=.
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking target system type... i686-pc-linux
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking how to run the C preprocessor... gcc -E
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking stropts.h usability... yes
checking stropts.h presence... yes
checking for stropts.h... yes
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking for stdint.h... (cached) yes
checking for inttypes.h... (cached) yes
checking for int8_t... yes
checking for int16_t... yes
checking for int32_t... yes
checking for int64_t... yes
checking for uint8_t in <stdint.h>... yes
checking for uint16_t in <stdint.h>... yes
checking for uint32_t in <stdint.h>... yes
checking whether byte ordering is bigendian... no
checking whether char is unsigned... no
checking for /dev/urandom... yes
checking for vsnprintf... yes
checking for inet_pton... yes
checking for inet_ntop... yes
checking for inet_aton... yes
checking for socklen_t... yes
checking for library containing socket... none required
checking for library containing inet_addr... none required
checking for getipnodebyname in <netdb.h>... no
checking netinet6/in6.h usability... no
checking netinet6/in6.h presence... no
checking for netinet6/in6.h... no
checking netinet/ip6.h usability... yes
checking netinet/ip6.h presence... yes
checking for netinet/ip6.h... yes
checking for struct addrinfo in <netdb.h>... yes
checking for sin6_len in struct sockaddr_in6... no
checking for gtkdoc-scan... no
configure: compiler warnings will not be errs
checking whether c compiler accepts -Wmissing-prototypes... yes
checking whether c compiler accepts -Wmissing-declarations... yes
checking whether c compiler accepts -Wbad-function-cast... yes
checking whether c compiler accepts -Wwrite-strings... yes
checking whether c compiler accepts -Wformat=2... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating win32/Makefile
config.status: creating uclconf.h
config.status: uclconf.h is unchanged
config.status: executing depfiles commands
configure: configuring in common/video/iso-mpeg4
configure: running /bin/sh './configure' --prefix=/usr/local  --cache-file=/dev/null --srcdir=.
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking target system type... i686-pc-linux
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking libtool tag=C for nasm... yes
checking whether make sets $(MAKE)... (cached) yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether we are using the GNU C++ compiler... (cached) no
checking whether g++ accepts -g... (cached) no
checking dependency style of g++... (cached) none
checking for inline... inline
checking for an ANSI C-conforming const... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for X... libraries /usr/X11R6/lib, headers
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking whether byte ordering is bigendian... no
checking for ANSI C header files... (cached) yes
checking whether time.h and sys/time.h may both be included... yes
checking for long... yes
checking size of long... 4
checking for bool... no
checking size of bool... 0
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for unistd.h... (cached) yes
checking for stdint.h... (cached) yes
checking for inttypes.h... (cached) yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking byteswap.h usability... yes
checking byteswap.h presence... yes
checking for byteswap.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for strerror... yes
checking for strcasestr... yes
checking for poll... yes
checking for getopt... yes
checking for getopt_long... yes
checking for getopt_long_only... yes
checking for getrusage... yes
checking for socketpair... yes
checking for strsep... yes
checking for inet_ntoa... yes
configure: compiler warnings will not be errs
checking whether c compiler accepts -malign-loops... no
checking whether c compiler accepts -falign-loops... yes
checking whether c compiler accepts -malign-functions... no
checking whether c compiler accepts -falign-functions... yes
checking whether c compiler accepts -malign-jumps... no
checking whether c compiler accepts -falign-jumps... yes
checking whether c compiler accepts -Wmissing-prototypes... yes
checking whether c compiler accepts -Wmissing-declarations... yes
checking whether c compiler accepts -Wno-char-subscripts... yes
checking whether c compiler accepts -Wno-unknown-pragmas... yes
checking whether c compiler accepts -Wformat=2... yes
checking whether c++ compiler accepts -Wmissing-prototypes... no
checking whether c++ compiler accepts -Wno-char-subscripts... no
checking whether c++ compiler accepts -Woverloaded-virtual... no
checking whether c++ compiler accepts -Wno-unknown-pragmas... no
checking whether c++ compiler accepts -Wno-deprecated... no
checking whether c++ compiler accepts -Wformat=2... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating mpeg4-2000.h
config.status: mpeg4-2000.h is unchanged
config.status: executing depfiles commands
```

Thanks for any insight or help you can provide! -Greg-

---

### Post by mrpeanut on 2006-08-13
Does anyone have any idea of what I should do?

---

### Post by jimmygoon on 2006-08-14
"sudo apt-get install build-essential g++"

then ./configure
and then make

---

### Post by coreyt on 2006-08-14
```

Checking your system in order to install Vive...
Checking for ffmpeg...Found
The program ffmpeg has been installed, but it does not have the optimal configuration for Vive.  Run:
        ./install ffmpeg

This will activate the Vive install script to install ffmpeg.  If you prefer to compile it yourself, the optimal configuration for Vive is:
        ./configure --enable-gpl --enable-pp --enable-zlib \
                --enable-vorbis --enable-libogg --enable-theora \
                --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm\
                --disable-debug --enable-mp3lame --enable-faad\
                --enable-faac --enable-xvid --enable-ogm
You may continue on with installing Vive and install an updated ffmpeg later, if you so choose, as well.
Checking for vobcopy...Found
Checking for cpdvd...Use of uninitialized value in pattern match (m//) at ./configure line 54.
Checking for MP4Box...Can't exec "MP4Box": No such file or directory at ./configure line 61.
Use of uninitialized value in pattern match (m//) at ./configure line 62.
Use of uninitialized value in pattern match (m//) at ./configure line 62.
Not found or incorrect version
Please install MP4Box by running:
        ./install mp4box
Or, run the following commands by yourself:
        wget http://internap.dl.sourceforge.net/sourceforge/gpac/gpac-0.4.0-rc2.tar.gz
        wget http://internap.dl.sourceforge.net/sourceforge/gpac/gpac_extra_libs-0.4.0.tar.gz
        tar -zxf gpac-0.4.0-rc2.tar.gz
        tar -zxf  gpac_extra_libs-0.4.0.tar.gz
        cd gpac_extra_libs
        cp -r * ../gpac/extra_lib
        cd ../gpac
        chmod +x configure
        ./configure
        make lib
        make apps
        make install
        sudo cp bin/gcc/libgpac.so /usr/lib

```



Okay where is the install script this error mentions.  And ffmpeg should already be configured correctly.

---

### Post by MotK on 2006-08-25
endersshadow,

quick suggestion:

vive is a great prog! could you maybe add batch encoding at some point? that way, i can just select a crapload of files and encode them overnight without having to watch them?

plus, do you know a way to add mp4 files to gtkpod without having to encode them yourself? bc any mp4 file for ipod that i download off ipodnova.net or elsewhere, gtkpod doesnt recognize it? do you know of a fix?

---

### Post by hardkaare on 2006-08-30
I would be nice with a new packages for the newest vive.
Thx for a very nice guide.

---

### Post by gandalf2041 on 2006-08-31
endersshadow, 

Very Nice Work! Thank You! :D   

I d/l and installed the latest Vive from sourceforge (BTW: SBX .debs work great but the Vive is a bit outdated).  At any rate, I didn't have any of the presets or scripts mentioned in the README but, thankfully, I didn't need them. I was able to create my own preset based upon your script parameters for ffmpeg. During my first encode, my home directory ran out of space :oops:  I guess that's what caused the computer to hang (although you might consider a 'disable screensaver' option).  At any rate, I ended up with a 7.6 GB file with a .mov.vob extension.  I assume this is because Vive didn't get to finish.  Will the interim .vob be the same size as the original? and if so, what is the normal average compression? (I'm wondering how much space I need to add to my /home).  

Thanks again for all your hard work!

---

### Post by KageKeeper on 2006-09-04
> **coreyt said:**
> ```

Checking your system in order to install Vive...
Checking for ffmpeg...Found
The program ffmpeg has been installed, but it does not have the optimal configuration for Vive.  Run:
        ./install ffmpeg

This will activate the Vive install script to install ffmpeg.  If you prefer to compile it yourself, the optimal configuration for Vive is:
        ./configure --enable-gpl --enable-pp --enable-zlib \
                --enable-vorbis --enable-libogg --enable-theora \
                --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm\
                --disable-debug --enable-mp3lame --enable-faad\
                --enable-faac --enable-xvid --enable-ogm
You may continue on with installing Vive and install an updated ffmpeg later, if you so choose, as well.
Checking for vobcopy...Found
Checking for cpdvd...Use of uninitialized value in pattern match (m//) at ./configure line 54.
Checking for MP4Box...Can't exec "MP4Box": No such file or directory at ./configure line 61.
Use of uninitialized value in pattern match (m//) at ./configure line 62.
Use of uninitialized value in pattern match (m//) at ./configure line 62.
Not found or incorrect version
Please install MP4Box by running:
        ./install mp4box
Or, run the following commands by yourself:
        wget http://internap.dl.sourceforge.net/sourceforge/gpac/gpac-0.4.0-rc2.tar.gz
        wget http://internap.dl.sourceforge.net/sourceforge/gpac/gpac_extra_libs-0.4.0.tar.gz
        tar -zxf gpac-0.4.0-rc2.tar.gz
        tar -zxf  gpac_extra_libs-0.4.0.tar.gz
        cd gpac_extra_libs
        cp -r * ../gpac/extra_lib
        cd ../gpac
        chmod +x configure
        ./configure
        make lib
        make apps
        make install
        sudo cp bin/gcc/libgpac.so /usr/lib

```



Okay where is the install script this error mentions.  And ffmpeg should already be configured correctly.

Getting the same exact issues.

Any suggestions?

---

### Post by endersshadow on 2006-09-04
> **MotK said:**
> endersshadow,

quick suggestion:

vive is a great prog! could you maybe add batch encoding at some point? that way, i can just select a crapload of files and encode them overnight without having to watch them?

plus, do you know a way to add mp4 files to gtkpod without having to encode them yourself? bc any mp4 file for ipod that i download off ipodnova.net or elsewhere, gtkpod doesnt recognize it? do you know of a fix?

Rename the files from .mp4 to .mov.

As for those having MP4Box configure issues, I'm going to edit the configure script and post a new one for you.  It should be up in the next hour or so.  I apologize for my absence as of late, I do.  I shall get back to you in a bit :)

---

### Post by endersshadow on 2006-09-04
Hey there you crazy kids, I've fixed the configure script, and you can download the new Vive 0.3 package [here](http://prdownloads.sourceforge.net/vive/vive-0.3.tar.gz?download).  I will be starting work on Vive 1.0 shortly, and will finally get out a full release that works :)

---

### Post by gandalf2041 on 2006-09-05
Hi endersshadow, 

Welcome back! Vive seems to be turning out nicely but, alas...I can't seem to get it to work for me :-k  v3 beta 2 compiled and installed fine.  I can read the DVD and select the pre-sets.  When I push encode, it says it's encoding but a second later it's done and there's no file. 

I have compiled ffmpeg and it encodes a vob which I extracted (using dvdbackup - vobcopy would've worked too I guess) beautifully.  I'm sure it's something simple, is there an error log I can review?

---

### Post by endersshadow on 2006-09-05
> **gandalf2041 said:**
> Hi endersshadow, 

Welcome back! Vive seems to be turning out nicely but, alas...I can't seem to get it to work for me :-k  v3 beta 2 compiled and installed fine.  I can read the DVD and select the pre-sets.  When I push encode, it says it's encoding but a second later it's done and there's no file. 

I have compiled ffmpeg and it encodes a vob which I extracted (using dvdbackup - vobcopy would've worked too I guess) beautifully.  I'm sure it's something simple, is there an error log I can review?

In my infinite wisdom, I do not have an error log that you can review...I apologize.

However, try starting it from the terminal, which will show all output in the terminal for you to review :)

---

### Post by gandalf2041 on 2006-09-08
Sorry it took so long... here's the terminal output:

```
[21:33:25]-rand:~(0)>> vive
Use of uninitialized value in substitution (s///) at /usr/bin/cpdvd line 76.
Vobcopy 0.5.14 - GPL Copyright (c) 2001 - 2004 robos@muon.de
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library

path to dvd: /dev/hdd
libdvdread: Using libdvdcss version 1.2.9 for DVD access
There are 4 titles on this DVD.
There are 37 chapters on the dvd.
Most chapters has title 1 with 29 chapters.

There are 4 angles on this dvd.
Using Title: 2
Title has 2 chapters and 1 angles
Using Chapter: 1
Using Angle: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000002ed
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0001c7f9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x003d1b5b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003d1b5f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003d5236
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003d523a
libdvdread: Elapsed time 0
libdvdread: Found 3 VTS's
libdvdread: Elapsed time 0

DVD-name: vive_dvd_temp

your-name for the dvd: vive_dvd_temp

Outputting to /home/vive_dvd_temp2-1.vob

[Error] error opening file /home/vive_dvd_temp2-1.vob.partial
FFmpeg version SVN-r6155, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid
  libavutil version: 49.0.0
  libavcodec version: 51.12.0
  libavformat version: 50.5.0
  built on Sep  3 2006 11:38:04, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
/home/vive_dvd_temp*.vob: I/O error occured
Usually that means that input file is truncated and/or corrupted.

```

Not sure why it's complaining about the input file. vobcopy seems to run OK from the command line and I've successfully encoded the .vob via ffmpeg (the one I took from dvdbackup):-k

---

### Post by endersshadow on 2006-09-09
I'll tell you what's happening: It's jumping to ffmpeg before vobcopy is done creating the vob.

I'll tell you what I don't know: Why it's happening. But that's a pure, honest-to-goodness bug that I'll definitely look into.  I apologize for that. You know how us damned developers and bug-free software go together like peanut butter and pepperoni pizza.  Sorry :-|

---

### Post by gandalf2041 on 2006-09-09
> I apologize for that. You know how us damned developers and bug-free software go together like peanut butter and pepperoni pizza. Sorry

No need to apologize! :-D  That's what makes OSS so fantastic!  People like you who put time and effort into something simply because they enjoy it!  My hat is off to you!  Thanks for all you hard work! :KS

---

### Post by PriceChild on 2006-09-16
Trying out the 0.3 beta 2.... It just deleted 2 Gbs of videos when i selected my destination folder and clicked encode...

---

### Post by endersshadow on 2006-09-18
I've released Vive 1.0.0, the full release! No more Beta!

The VOB bug should be fixed, as well as the deletion in multiple file things....(sorry about that...that's rather embarassing and unfortunate, PriceChild)...

Check it out at [http://vive.sourceforge.net](http://vive.sourceforge.net)!

---

### Post by darksider415 on 2006-09-24
I've been noticing the shell script in the beginning of the HOWTO was lacking a couple of things, so I'm posting the modifications that a friend of mine and I have done, over the past week or so. I have tested this with my 5G iPod, and things do work with it.

*Alex and I did the version numbering scheme for our modifications, with Eric's original script being version 1.0, which may differ from how he did it. - CSC - 9/25/06*

```
#!/bin/bash
## ipodvidenc - The iPod Video Encoder for Linux.
## Created by Eric Hewitt, January 9, 2006. Modified by Caleb Cupples, 17 September 2006. Further modified by Alex Lowe, 17 September 2006. Cinematic Widescreen functionality added by C. Cupples on 24 September 2006
## Released under the GPL.  Go nuts.

## Version 1.2

# Make the first argument the input file
input_file=$1

echo "What would you like to name the output file (sans extension)?"

read output_file_name

widescreen='N'
system:/media
echo "Is this video widescreen? (Fullscreen (4:3) assumed otherwise) [y/N]"

read widescreen

case "$widescreen" in
		n*|N*|*)
	aspect_ratio="4:3"
	resolution="320x240"
;;esac

#The cinematic widescreen format is the standard, according to several sources. Please email me at cscupples [at] gmail.com if I was incorrect on this. - C. Cupples

case "$widescreen" in
		y*|Y*)
	echo "Is this cinematic widescreen (1.85:1) or not? (16:9 assumed otherwise.) [y/N]"
	
	read cinematic

	case "$cinematic" in
			n*|N*|*)
		aspect_ratio="16:9"
		resolution="320x180"
	;;esac

	case "$cinematic" in
			y*|Y*)
		aspect_ratio="370:200"
		resolution="320x172"
	;;esac
;;esac


output_file_loc_permis='Y'

echo "$output_file_name will be located in $PWD. Is this acceptable? [Y/n]"

read output_file_loc_permis

case "$output_file_loc_permis" in
		n*|N*)
	echo "Where would you like to store $output_file_name.mov?"
	read output_dir
;;esac

case "$output_file_loc_permis" in
		y*|Y*|*)
	output_dir=$PWD
;;esac


ffmpeg -i "${input_file}" -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s $resolution -aspect $aspect_ratio "${output_dir}/${output_file_name}.mov"
```

C. Cupples

---

### Post by hardkaare on 2006-09-26
Could someone make a new deb for vive's new version?

---

### Post by darksider415 on 2006-09-27
I've created a .deb of the current version of Vive, available at [http://cscupples.strangled.net/]("http://cscupples.strangled.net/")

It should work, but if not, drop me an email and I'll see what I can do, if it's an issue with my particular setup.

C. Cupples

--Update--
The deb wasn't working for me at first, so I had to redo it, but it now works. I built it on Kubuntu Edgy Knot 3, but it should run on Dapper, I think.

CSC

---

### Post by siiib on 2006-09-27
i've been following this thread with interest.. 

slightly OT i know but what do you guys reckon is the optimum rate for encoding for ipod?? i've been sort of doing it at 300 megs an hour .. simply based on the fact that an average film is two hours and fits on one cd without much loss of quality in mp4.. i reckon i may be overdoing it and could cut this down a bit.. main reason being i'd like to post my optimised ipod vids cos they can be difficult to get hold of.. errm assuming anyone is interested in my collection of war films or bbc documentaries.. heh. save someone else the hassle..
any tips, links etc much appreciated

regards Simon

p.s. looks like itunes has had it now.. not much left on the xp partition left to replace!

---

### Post by darksider415 on 2006-09-27
I'm getting pretty nice quality in the 200-220 MB/hr range for video, using ffmpeg for encoding. Most of this depends on the quality of the source file, though. 

CC

---

### Post by siiib on 2006-09-28
cheers mate..  the source is the original dvd!.. oops i asked a question in the wrong bit.. sorry:p

---

### Post by endersshadow on 2006-10-02
There was an issue w/ the 1.0.1 release with DVD-to-video encoding, which is now fixed in 1.0.2, available at [Sourceforge](http://sourceforge.net/project/showfiles.php?group_id=158461).

---

### Post by KingFuzz on 2006-10-04
I'm having a problem wih vive. When pushing the encode button and black window pops up twice and nothing happens. I've compiled it from the latest source..
Thank you in advance..

-Chris

---

### Post by Kryten107 on 2006-10-08
After getting the "unknown codec 'acc'" error, I tried to recompile ffmpeg to make sure I had AAC support. I had to add the Edgy repos to satisfy the liblame-dev stuff, and even after recompiling it still didn't work. ffmpeg -formats doesn't list aac as an option, and --enable-faac isn't listed in the parameters under ffmpeg.

When compiling ffmpeg, make gets an error that I couldn't figure out:
```
devin@Nayru:~/CVS/ffmpeg-0.cvs20050918$ make
make -C libavutil all
make[1]: Entering directory `/home/devin/CVS/ffmpeg-0.cvs20050918/libavutil'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/devin/CVS/ffmpeg-0.cvs20050918/libavutil'
make -C libavcodec all
make[1]: Entering directory `/home/devin/CVS/ffmpeg-0.cvs20050918/libavcodec'
gcc -O3 -Wall -Wno-switch  -DHAVE_AV_CONFIG_H -I.. -I'/home/devin/CVS/ffmpeg-0.cvs20050918'/libavutil -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_GNU_SOURCE   -c -o dtsdec.o dtsdec.c
dtsdec.c:27:17: error: dts.h: No such file or directory
dtsdec.c:59: error: syntax error before &#65533;&#65533;&#65533;*&#65533;&#65533;&#65533; token
dtsdec.c: In function &#65533;&#65533;&#65533;convert2s16_2&#65533;&#65533;&#65533;:
dtsdec.c:62: error: &#65533;&#65533;&#65533;_f&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:62: error: (Each undeclared identifier is reported only once
dtsdec.c:62: error: for each function it appears in.)
dtsdec.c:66: error: &#65533;&#65533;&#65533;s16&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c: At top level:
dtsdec.c:72: error: syntax error before &#65533;&#65533;&#65533;*&#65533;&#65533;&#65533; token
dtsdec.c: In function &#65533;&#65533;&#65533;convert2s16_4&#65533;&#65533;&#65533;:
dtsdec.c:75: error: &#65533;&#65533;&#65533;_f&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:79: error: &#65533;&#65533;&#65533;s16&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c: At top level:
dtsdec.c:87: error: syntax error before &#65533;&#65533;&#65533;*&#65533;&#65533;&#65533; token
dtsdec.c: In function &#65533;&#65533;&#65533;convert2s16_5&#65533;&#65533;&#65533;:
dtsdec.c:90: error: &#65533;&#65533;&#65533;_f&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:94: error: &#65533;&#65533;&#65533;s16&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c: At top level:
dtsdec.c:103: error: syntax error before &#65533;&#65533;&#65533;*&#65533;&#65533;&#65533; token
dtsdec.c: In function &#65533;&#65533;&#65533;convert2s16_multi&#65533;&#65533;&#65533;:
dtsdec.c:106: error: &#65533;&#65533;&#65533;_f&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:108: error: &#65533;&#65533;&#65533;flags&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:110: error: &#65533;&#65533;&#65533;DTS_MONO&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:113: error: &#65533;&#65533;&#65533;s16&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:117: error: &#65533;&#65533;&#65533;DTS_CHANNEL&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:118: error: &#65533;&#65533;&#65533;DTS_STEREO&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:119: error: &#65533;&#65533;&#65533;DTS_DOLBY&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:122: error: &#65533;&#65533;&#65533;DTS_3F&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:131: error: &#65533;&#65533;&#65533;DTS_2F2R&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:134: error: &#65533;&#65533;&#65533;DTS_3F2R&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:137: error: &#65533;&#65533;&#65533;DTS_LFE&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c: In function &#65533;&#65533;&#65533;channels_multi&#65533;&#65533;&#65533;:
dtsdec.c:194: error: &#65533;&#65533;&#65533;DTS_LFE&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:198: error: &#65533;&#65533;&#65533;DTS_CHANNEL_MASK&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:198: error: &#65533;&#65533;&#65533;DTS_2F2R&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c: In function &#65533;&#65533;&#65533;dts_decode_frame&#65533;&#65533;&#65533;:
dtsdec.c:219: error: &#65533;&#65533;&#65533;dts_state_t&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:219: error: &#65533;&#65533;&#65533;state&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:241: warning: implicit declaration of function &#65533;&#65533;&#65533;dts_syncinfo&#65533;&#65533;&#65533;
dtsdec.c:255: error: &#65533;&#65533;&#65533;level_t&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:255: error: syntax error before &#65533;&#65533;&#65533;level&#65533;&#65533;&#65533;
dtsdec.c:256: error: &#65533;&#65533;&#65533;sample_t&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:260: error: &#65533;&#65533;&#65533;level&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:261: error: &#65533;&#65533;&#65533;bias&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:263: error: &#65533;&#65533;&#65533;DTS_ADJUST_LEVEL&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:264: warning: implicit declaration of function &#65533;&#65533;&#65533;dts_frame&#65533;&#65533;&#65533;
dtsdec.c:269: warning: implicit declaration of function &#65533;&#65533;&#65533;dts_blocks_num&#65533;&#65533;&#65533;
dtsdec.c:271: warning: implicit declaration of function &#65533;&#65533;&#65533;dts_block&#65533;&#65533;&#65533;
dtsdec.c:276: warning: implicit declaration of function &#65533;&#65533;&#65533;dts_samples&#65533;&#65533;&#65533;
dtsdec.c:277: error: &#65533;&#65533;&#65533;DTS_CHANNEL_MASK&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c:277: error: &#65533;&#65533;&#65533;DTS_LFE&#65533;&#65533;&#65533; undeclared (first use in this function)
dtsdec.c: In function &#65533;&#65533;&#65533;dts_decode_init&#65533;&#65533;&#65533;:
dtsdec.c:298: warning: implicit declaration of function &#65533;&#65533;&#65533;dts_init&#65533;&#65533;&#65533;
dtsdec.c:298: warning: assignment makes pointer from integer without a cast
dtsdec.c: At top level:
dtsdec.c:315: error: &#65533;&#65533;&#65533;dts_state_t&#65533;&#65533;&#65533; undeclared here (not in a function)
dtsdec.c:315: error: syntax error before &#65533;&#65533;&#65533;)&#65533;&#65533;&#65533; token
make[1]: *** [dtsdec.o] Error 1
make[1]: Leaving directory `/home/devin/CVS/ffmpeg-0.cvs20050918/libavcodec'
make: *** [lib] Error 2
```

I'm assuming the make error would have something to do with the lack of aac support. Any ideas?

Update: Also, it seems Banshee can't play AAC files anymore, so although I reinstalled all the packages that I had uninstalled (including packages like mplayer that were uninstalled with the AAC stuff) AAC remains broken. I'll look into it more.

Update #2: There were a few packages that needed to be downgraded in order to accomodate the AAC packages (apparently I had never noticed that the build-dep for ffmpeg had failed) but my AAC is back and I'm encoding things fine. :P

---

### Post by starwarsfan982 on 2006-10-09
Hi, I was looking for a gui solution for encoding video, and this one seems really nice. Only one problem, it doesn't work. When i run this from the terminal, it pops up. I select to encode in AVI from a vob file i got using vobcopy. I output to a directory naming it whatever.avi When I click encode, a terminal pops up and then closes. When i check the Terminal I ran it from, i get the this error: 

mv: invalid option -- r
Try `mv --help' for more information.

Does anyone have any idea how to fix this? I will post in the Desktop forums too, but this also seemed like an appropriate place.

---

### Post by kerme8503 on 2006-10-10
I have got upto the "sudo make install blah blah"  I do that, it goes for a while, then it says "Install failed"  "cleaning up"  "Bye"  hmm... help please  :)

---

### Post by misteral on 2006-10-20
Has anyone gotten this to work on a 64 bit system (AMD 64 in particular in my case)?

Thanks

---

### Post by apoclypse on 2006-10-29
> **starwarsfan982 said:**
> Hi, I was looking for a gui solution for encoding video, and this one seems really nice. Only one problem, it doesn't work. When i run this from the terminal, it pops up. I select to encode in AVI from a vob file i got using vobcopy. I output to a directory naming it whatever.avi When I click encode, a terminal pops up and then closes. When i check the Terminal I ran it from, i get the this error: 

mv: invalid option -- r
Try `mv --help' for more information.

Does anyone have any idea how to fix this? I will post in the Desktop forums too, but this also seemed like an appropriate place.

I have this issue too. it just doesn't seem to work for me. Another thing does this support h.264 encoding, cause thats what I'm looking to convert my dvds. What we need is something like ffmpegx which is for the mac. I've tried the ipodenc scripts and that gives me errors. I just don't know what to do anymore. I really don't want to use windows to encode my files. If someone can give the actual commandline steps I don't care how long the steps are. I know it can be done cause I've seen quite a few sites with very sparse info but they sure show a lot of examples. This is frustrating me to no end.

---

### Post by apoclypse on 2006-10-29
Nevermind. I found this great little app called handbrake which does the trick rather well. I think it statically links all the file to it but the dependancies are pretty similar to what you see in the howto here. Right now only the commandline tool seems to compile. There is some code for a gtk frontnd but it doesn't seem to compile. If any one can get this thing working  with a gui I think it would be incredible. Vive seems nice but it just doesn't work for me at all, neither does ipodenc. The cli version is super easy to use and there is documentation on how to use it for the most common tasks, in this case that would be encoding a dvd for an ipod. It works great so far and supports the x.264 library which was really the most important thing for me. 

Vive just needs to mature a little, I think maybe the authors might want to redo a few things, such as the preferences. Other than that everything is pretty easy to use. I just wish it would actually work when it came to encoding stuff. Ah, well such is the nature of beta software I guess.

---

### Post by KillerFrog_505 on 2006-11-08
HELP!!! i get this error message

casey@burnsie:~$ sudo apt-get install libtool libsdl1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libtool is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages

---

### Post by endersshadow on 2006-11-08
> **KillerFrog_505 said:**
> HELP!!! i get this error message

casey@burnsie:~$ sudo apt-get install libtool libsdl1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libtool is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages

Could you paste your /etc/apt/sources.list file?

Thanks!

As for everybody else, I'm very sorry for not getting on things right away! College hath grabbed me by the arm and yanked me away from fun things like Vive, but after Thanksgiving, I'll have some time to sit down and really bang out some bugs.

Thanks and sorry again!

---

### Post by KillerFrog_505 on 2006-11-08
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy-plf free non-free                                               
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen

#Beryl Repositories for Edgy Eft (Ubuntu 6.10)
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) edgy main-edgy
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) edgy main-edgy

# Treviño's Beryl-SVN Ubuntu Edgy Eft Repository
# GPG key: 81836EBF
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy beryl-svn

## Automatix repo
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main


#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by mike41 on 2006-11-12
I'm having a problem while compiling the mpeg4ip

when I say "make" I get the following error:

```
libtool: ignoring unknown tag CXX
../../libtool: line 1223: g++: command not found
make[3]: *** [config_opts.lo] Error 1
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
mike@mike-tc:~/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1$ make < ~out.a
make  all-recursive
make[1]: Entering directory `/home/mike/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1'
Making all in include
make[2]: Entering directory `/home/mike/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mike/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1/include'
Making all in lib
make[2]: Entering directory `/home/mike/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1/lib'
Making all in utils
make[3]: Entering directory `/home/mike/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1/lib/utils'
source='config_opts.cpp' object='config_opts.lo' libtool=yes \
        DEPDIR=.deps depmode=none /bin/bash ../../depcomp \
        /bin/bash ../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../include   -D_REENTRANT -fexceptions -Wall  -DMPEG4IP -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -c -o config_opts.lo config_opts.cpp
libtool: ignoring unknown tag CXX
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../include -D_REENTRANT -fexceptions -Wall -DMPEG4IP -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -c config_opts.cpp  -fPIC -DPIC -o .libs/config_opts.o
../../libtool: line 1223: g++: command not found
make[3]: *** [config_opts.lo] Error 1
make[3]: Leaving directory `/home/mike/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1/lib/utils'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mike/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mike/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1'
make: *** [all] Error 2

```

I tried going into the specified makefiles and removing -Werror, but i still get the error. I've searched the forum, and the web for hours now trying to find other ways to do this stuff, but I haven't had any luck. 

PLEASE ANY HELP!!! :)

---

### Post by endersshadow on 2006-11-13
Killer Frog: Try looking for the glu-dev packages suggested.  That's what libsdl1.2-dev is complaining about.

mike41: Did it get through the ./bootstrap step and ./configure without errors?

---

### Post by mike41 on 2006-11-13
yea I got through everything until the "make", and then I removed the -Werror lines in the makefiles, then I retyped make, and got the same error. I have a copy of Nero, so I installed that and Nero Recode is working nicely (in windows of course). I suppose I'll just stick with that for now.

---

### Post by iggywig on 2006-11-14
I've got a problem with ffmpeg and libfaac.. I've built ffmpeg from the source as page one says. I'm not using the script yet just the ffmpeg command line from the script:

ian@ian-ubuntu:~$ ffmpeg -i test.avi  -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 ipodtest

It fails immediately and I get this:
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-faadbin 
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Nov 14 2006 14:25:55, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
Input #0, mpeg, from 'test.avi':
  Duration: 00:00:41.6, start: 0.500000, bitrate: 660 kb/s
  Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 320x240, 104857 kb/s, 29.97 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 22050 Hz, mono, 56 kb/s
File 'ipodtest' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'ipodtest':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, q=3-5, 700 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: aac, 22050 Hz, mono, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[aac @ 0x849ef18]libfaac doesn't support this output format!
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

Any ideas?
Cheers

---

### Post by Slace on 2006-11-15
does anyone have a script that will encode for an iPod in H.264 format, using x264?

---

### Post by Choxo on 2006-11-29
Hi,

I tried to 'make' but I've got the error:

```

make[6]: *** [sys_block.lo] Error 1
make[6]: Leaving directory `/home/spitz/mpeg4ip-1.4.1/common/video/iso-mpeg4/src'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/spitz/mpeg4ip-1.4.1/common/video/iso-mpeg4'
make[4]: *** [all] Error 2
make[4]: Leaving directory `/home/spitz/mpeg4ip-1.4.1/common/video/iso-mpeg4'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/spitz/mpeg4ip-1.4.1/common/video'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/spitz/mpeg4ip-1.4.1/common'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/spitz/mpeg4ip-1.4.1'
make: *** [all] Error 2

```

I deleted -Werrior in the line, but it still doesn't work.
I don't have to delete the entire line, do I?

The ending of my ./configure was like this: ```

checking whether c++ compiler accepts -Wformat=2... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating mpeg4-2000.h
config.status: mpeg4-2000.h is unchanged
config.status: executing depfiles commands

```
Thanks,

Choxo

---

### Post by sirmrmatt on 2006-11-29
Hi.

I *HAD* Vive installed and working fine yesterday, but then I installed the .deb package over it and it's not working anymore!! ARRRGGHHH!!! ](*,) 

So anyhow, when I start it from the Ubuntu Programs menu, I get nothing. Just does nothing. From the command line, I am getting this message in an endless repeat pattern:

```
Use of uninitialized value in pattern match (m//) at /usr/local/bin/vive line 376
```

Any help on this one? I tried deleting the /usr/local/bin/vive and recompiling/installing, but it didn't work. ](*,) BAAHHH! lol

Any help?

- Matt

---

### Post by chaumurky on 2006-11-30
Ok, using the 'ipodvidenc' script I'm getting the "[mpeg4 @ 0x849ee58]timebase not supported by mpeg 4 standard" error for avi's created by my stills camera. "Vive" just spits out a 0k sized file so I assume it's the same problem. It seems the frame rate/timebase of 12fps is the issue. Is it possible to fix the frame rate by an added parameter or something? "Frame-doubling" perhaps?

---

### Post by ooosadface on 2006-12-02
> **mike41 said:**
> I'm having a problem while compiling the mpeg4ip

when I say "make" I get the following error:

```
libtool: ignoring unknown tag CXX
../../libtool: line 1223: g++: command not found
make[3]: *** [config_opts.lo] Error 1
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
mike@mike-tc:~/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1$ make < ~out.a
make  all-recursive
make[1]: Entering directory `/home/mike/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1'
Making all in include
make[2]: Entering directory `/home/mike/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mike/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1/include'
Making all in lib
make[2]: Entering directory `/home/mike/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1/lib'
Making all in utils
make[3]: Entering directory `/home/mike/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1/lib/utils'
source='config_opts.cpp' object='config_opts.lo' libtool=yes \
        DEPDIR=.deps depmode=none /bin/bash ../../depcomp \
        /bin/bash ../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../include   -D_REENTRANT -fexceptions -Wall  -DMPEG4IP -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -c -o config_opts.lo config_opts.cpp
libtool: ignoring unknown tag CXX
 g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../include -D_REENTRANT -fexceptions -Wall -DMPEG4IP -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -c config_opts.cpp  -fPIC -DPIC -o .libs/config_opts.o
../../libtool: line 1223: g++: command not found
make[3]: *** [config_opts.lo] Error 1
make[3]: Leaving directory `/home/mike/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1/lib/utils'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mike/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mike/Desktop/vive-1.0.2/mpeg4ip-1.5.0.1'
make: *** [all] Error 2

```

I tried going into the specified makefiles and removing -Werror, but i still get the error. I've searched the forum, and the web for hours now trying to find other ways to do this stuff, but I haven't had any luck. 

PLEASE ANY HELP!!! :)

I was having the same problem. I found this to be the problem. I needed to install g++. When I went to Package Manager I installed the latest (g++-4.1.something). Anyway the make is looking for the command g++. My command after installing g++ was 'g++-4.1', g++ didn't exist. So, I went back to package manager and installed the plain jane g++. Now, it works! :D 

I found info on doing an alias and something called symlink or something, but once I found alias wasn't a reckognized command I went straight to the install plain g++ idea.

---

### Post by endersshadow on 2006-12-04
Ah, makes a lot of sense now.  Thanks sadface!

---

### Post by berteh on 2006-12-09
Hi,

I tried to run vive-1.0.2 on Dapper and got some troubles.

Install seemed to have worked well (I actually installed .debs with an older version and updated the /usr/bin/vive script from the new sources).

After loading a dvd, selecting the adequate title, output file and preset I hit encode and got the following error:

Use of uninitialized value in substitution (s///) at /usr/bin/vive line 162, namely the ```
s/\.//
``` below:

```
elsif ($vob_keep || $vob_only_checked)
{
  $ffmpeginfo{'vobfile'} =~ s/\.//;
  $vobkeepcommand="mv -f $ffmpeginfo{'outfile'}/vive_dvd_temp*.vob $ffmpeginfo{'output'}.vob 2>&1";
}
```

I got no clue why this happens.. as anyone else seem to be happy with VIVE, so please let me know how to fix this... or if you need any other information in order to to so.

thanks.

PS: is there any other place with "official" support for vive? I didn't see anything on the Sourceforge forum...

---

### Post by endersshadow on 2006-12-10
What was your output file input and/or which box did you check (keep or only for the VOB)?

Also, "official" support is just emailing me at endersshadow AT users DOT sourceforge DOT net.  I'm not a huge project by any means, so that's pretty much it.

Thanks!

---

### Post by berteh on 2006-12-11
> **endersshadow said:**
> What was your output file input and/or which box did you check (keep or only for the VOB)?


I tried 
- input: /dev/dvdrw and /dvd (alias)
- output: /media/rip/7arrive.avi   (where the current user has rwx access to /media/rip directory)
- encoding using your "custom AVI" settings
- "keep VOB" checked (and NOT the only VOB one)

thanks for your help.

---

### Post by endersshadow on 2006-12-12
You can delete 162. My fault for just leaving that line in there.

I'm working on 1.0.3 which should fix a few other bugs.  Stay tuned!

---

### Post by FakeOutdoorsman on 2006-12-12
I'm have the same error as sirmrmatt from message #[333]("http://ubuntuforums.org/showpost.php?p=1822187&postcount=333").

I followed the install instructions from Vive 1.0.2 README, but I used *sudo checkinstall -D make install* instead of *sudo make install*.  I wanted it listed in Synaptic.  When I try to start the program in terminal I get this message once:

```
Use of uninitialized value in pattern match (m//) at /usr/local/bin/vive line 376.

```

and then I get repeats of the same line over and over again except it is at line 441.

I uninstalled Vive from Synaptic and then i recompiled and remade everything from a new folder and I still get this error.  I compiled ffmpeg from SVN yesterday and I am using Edgy.

---

### Post by FakeOutdoorsman on 2006-12-12
I noticed a problem with using the ffmpeg SVN instead of a version from the repository.  Using the ipodvidenc or the ffmpeg options shown in the wiki article [iPodVideoEncoding]("https://help.ubuntu.com/community/iPodVideoEncoding") will result in an error:

```
mpeg4 @ 0x84f6338]rc buffer underflow
```

The ffmpeg SVN units for options have recently changed from kilobits/sec to bits/sec, so it is trying to encode at a really low bitrate with a very high quality setting (-qmin 3 -qmax 5).  I think the unit change applies to maxbitrate and b.

References:
[URL="http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-October/004902.html"][Ffmpeg-user] buffer underflow errors
[/URL]
[[Ffmpeg-user] maxrate]("http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-October/004647.html")

---

### Post by endersshadow on 2006-12-13
Well that's a fun fact.

What rates do you have to use now?

Also, I was going through the code trying to clean it up, and let's just say that I'm rather embarassed that I wrote this stuff.  Over my winter break, I'm gonna work on an entire rewrite in C.  Should run faster, smoother, and allow for a bit more cleanliness all around.  I apologize to everybody for my awful, awful, awful code.  I'm in the middle of finals right now, so please be patient!

---

### Post by FakeOutdoorsman on 2006-12-13
> **endersshadow said:**
> What rates do you have to use now?

I tried multiplying the original bitrates for "maxbitrate" and "b" by 1024 to change kilobits to bits but I was still getting the same errors; even after removing qmin and qmax.  I just deleted the SVN version of ffmpeg and went with the Ubuntu repository source version.  It worked for me after I did that, but now I'm getting the *AC EOB marker is absent* error with some of my DV source movies.

It's frustrating to find a good ffmpeg code example and find it doesn't work because ffmpeg likes to change the option names and units.  It's doubly frustrating when the ipod firmware updates screws things up too.

You shouldn't be embarassed for your code.  ffmpeg isn't easy to work with.

---

### Post by endersshadow on 2006-12-13
> **FakeOutdoorsman said:**
> I tried multiplying the original bitrates for "maxbitrate" and "b" by 1024 to change kilobits to bits but I was still getting the same errors; even after removing qmin and qmax.  I just deleted the SVN version of ffmpeg and went with the Ubuntu repository source version.  It worked for me after I did that, but now I'm getting the *AC EOB marker is absent* error with some of my DV source movies.

It's frustrating to find a good ffmpeg code example and find it doesn't work because ffmpeg likes to change the option names and units.  It's doubly frustrating when the ipod firmware updates screws things up too.

You shouldn't be embarassed for your code.  ffmpeg isn't easy to work with.

If you can read Perl, read through the code...you'll shake your head through most of it.  It's not ffmpeg, it's that I had to go through roundabout ways of making things work because I thought to myself, "Well, Perl would be a good choice for a GUI plugin..."

Suffice it to say that I'm an idiot.  I'll figure it out and get it working well. I promise :-D

---

### Post by FakeOutdoorsman on 2006-12-15
I was able to resolve my issues from post 341.  The uninstall instructions from the README weren't working correctly so I did it myself:

```

sudo unlink /usr/local/bin/vive
sudo unlink /usr/local/man/man1/vive.1p
sudo unlink /usr/local/lib/perl/5.8.8/auto/Vive/.packlist
sudo rm -f /usr/share/pixmaps/vive.xpm
sudo rm -f /usr/share/applications/vive.desktop
sudo rm -f /usr/local/bin/vive
sudo rm -f /usr/local/man/man1/vive.1p
sudo rm -rf /usr/local/lib/perl/5.8.8/auto/Vive
sudo rm -rf /blib/script/vive

```

I reinstalled Vive from scratch and tried to start it but it still gave me the same errors, but once I restarted the computer everything worked.

---

### Post by FakeOutdoorsman on 2006-12-19
Mpeg4ip will encounter an error if you try to install it with a svn of x264 after 07-18-2006, revision 536:
```

video_x264.cpp: In member function `virtual bool CX264VideoEncoder::Init()': 
video_x264.cpp:173: error: 'struct x264_param_t::<anonymous>' has no member named 'b_cbr' 
make[4]: *** [video_x264.lo] Error 1 

```

The API for x264 changed and mpeg4ip 1.5.0.1 doesn't include those changes.  You can either comment out the line or download and complile the current CVS of mpeg4ip:
```

cvs -z3 -d:ext:developername@mpeg4ip.cvs.sourceforge.net:/cvsroot/mpeg4ip co -P mpeg4ip

```

If it asks for a password just hit enter.  You will need to get CVS from Synaptic.

---

### Post by Smokeymcpawt on 2006-12-21
```
jared@jareds:~$ ipodvidenc /home/jared/torrents/borat.avi
What would you like to name the output file (sans extension)?
borat     
borat will be located in /home/jared. Is this acceptable? [y/n]
/y
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Sep 20 2006 00:26:15, gcc: 4.1.2 20060906 (prerelease) (Ubuntu 4.1.1-13ubuntu2)
Input #0, avi, from '/home/jared/torrents/borat.avi':
  Duration: 01:20:20.0, start: 0.000000, bitrate: 1217 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 624x336, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 32 kb/s
Unknown codec 'aac'
jared@jareds:~$ 

```

I get "Unknown codec 'aac'"

Any way to fix this, i DO have faac codec's installed.

---

### Post by endersshadow on 2006-12-22
Smokey,

ffmpeg is not configured with the --enable-faac flag.

---

### Post by SirKillalot on 2006-12-22
> **FakeOutdoorsman said:**
> Mpeg4ip will encounter an error if you try to install it with a svn of x264 after 07-18-2006, revision 536:
```

video_x264.cpp: In member function `virtual bool CX264VideoEncoder::Init()': 
video_x264.cpp:173: error: 'struct x264_param_t::<anonymous>' has no member named 'b_cbr' 
make[4]: *** [video_x264.lo] Error 1 

```

The API for x264 changed and mpeg4ip 1.5.0.1 doesn't include those changes.  You can either comment out the line or download and complile the current CVS of mpeg4ip:
```

cvs -z3 -d:ext:developername@mpeg4ip.cvs.sourceforge.net:/cvsroot/mpeg4ip co -P mpeg4ip

```

If it asks for a password just hit enter.  You will need to get CVS from Synaptic.

Hello, did you solve your problem? I got the same issue...

---

### Post by FakeOutdoorsman on 2006-12-22
> **SirKillalot said:**
> Hello, did you solve your problem? I got the same issue...

The Problem: Newer versions of x264 changed some parameters.  mpeg4ip 1.5.0.1 doesn't reflect those changes so an error message shows up during mpeg4ip 1.5.0.1 installation.

The Fix: Either install an older version of x264 (pre revision 536) or get mpeg4ip through CVS.  I recommend getting the new mpeg4ip through CVS rather than using an old x264 version.

What I did: I reinstalled mpeg4ip using CVS.  Uninstall your current version of mpeg4ip.  Get mpeg4ip through CVS (just enter that code from my previous post into a terminal session).  Then follow the mpeg4ip install instructions from the first page of this topic.

Install CVS if you don't have it:
```

sudo apt-get install cvs

```
or get it from System -> Administration -> Synaptic Package Manager.

If you want to know more about mpeg4ip CVS:
[Mpeg4ip CVS information at Sourceforge]("http://sourceforge.net/cvs/?group_id=18676")

---

### Post by Smokeymcpawt on 2006-12-24
hmm, i can't figure out how to put them on my ipod with gtkpod, :(

---

### Post by endersshadow on 2006-12-24
Are you using gtkpod from the repos or did you build gtkpod according to the HowTo (first post)?

---

### Post by Smokeymcpawt on 2006-12-24
iv tried both, but iv figured out how to manually put them on my ipod.

---

### Post by BetaMaster on 2006-12-24
I can't get the ffmpeg section working properly.

When I enter
```
sudo apt-get build-dep ffmpeg
```

I get
```
sven@sven-desktop:~/torrents$ sudo apt-get build-dep ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for ffmpeg
```

And when I try
```
apt-get source ffmpeg
```

I get
```
sven@sven-desktop:~/torrents$ apt-get source ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for ffmpeg
```

=\ Help?

---

### Post by endersshadow on 2006-12-24
Need your /etc/apt/sources.list file. You probably don't have your deb-src repos enabled.

---

### Post by BetaMaster on 2006-12-24
My entire sources.list file:

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END
deb [http://kubuntu.org/packages/amarok-144](http://kubuntu.org/packages/amarok-144) edgy main
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
# Treviño's Beryl-SVN Ubuntu Repository
 # GPG key: 81836EBF
 deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy beryl-svn
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy stable dev
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb [http://albertomilone.com/drivers/edgy/nonlegacy/32bit](http://albertomilone.com/drivers/edgy/nonlegacy/32bit) binary/

My deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe was commented out but I uncommented it just now.
Now the error message I get is
> sven@sven-desktop:~/Desktop$ sudo apt-get build-dep ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_universe_source_Sources - open (2 No such file or directory)

---

### Post by BetaMaster on 2006-12-25
Ah, figured it out. Sorry to have seemed stupid.

---

### Post by kylejack on 2006-12-26
Having some dependency problems early in the process.

kyle@ubuntu:~$ sudo apt-get install libsdl1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages
kyle@ubuntu:~$ 


I have the universe/debian repositories enabled, so I don't understand what could be causing this.  Any ideas?

---

### Post by FakeOutdoorsman on 2006-12-26
kylejack: This is probably an issue with your sources. Try commenting out any unofficial sources you have in /etc/apt/sources.list.  Enter the following code and then try to reinstall.
```
sudo cp /etc/apt/sources.list sources.list.bak
gksudo gedit /etc/apt/sources.list
sudo apt-get update
```

While you're at it you should post your sources.list here.

---

### Post by kylejack on 2006-12-26
Ok, I commented out the other repositories I've added in.

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main restricted multiverse

##deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

##deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
## deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) edgy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) edgy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## created by arnieplanetremoved

##deb [http://debian.space-based.de/debs/](http://debian.space-based.de/debs/) experimental main
##deb-src [http://debian.space-based.de/debs/](http://debian.space-based.de/debs/) experimental main		

##deb  [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse
##deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse

##deb [http://albertomilone.com/drivers/edgy/nonlegacy/32bit](http://albertomilone.com/drivers/edgy/nonlegacy/32bit) binary/
##deb [http://albertomilone.com/drivers/edgy/nonlegacy/64bit](http://albertomilone.com/drivers/edgy/nonlegacy/64bit) binary/

#AUTOMATIX REPOS START

##deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

##deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

##deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

##deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
#AUTOMATIX REPOS END


Still getting the same error.

---

### Post by patsissons on 2006-12-26
just a note, the deb that SBX created is missing the following dependencies:

- libglib-perl
- libgtk2-perl

There may be others missing, but these two were the only packages that i noticed.

---

### Post by patsissons on 2006-12-26
See if you can figure this one out, it has me very stumped at the moment.

```

ffmpeg -i "test.avi" -f mp4 -vcodec mpeg4 -maxrate 1000 -b 300 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 48 -s 320x240 "test.avi.mp4"
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-shared --prefix=/usr
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Dec 26 2006 13:35:47, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
Input #0, avi, from 'test.avi':
  Duration: 00:41:26.3, start: 0.000000, bitrate: 1186 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 624x352, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Unknown codec 'aac'

```

---

### Post by patsissons on 2006-12-26
found the answer, turns out if you compile it with just the faac-dev package installed it builds fine, but when you run ffmpeg it throws up.  so MAKE SURE you have the faac package installed as well.

---

### Post by FakeOutdoorsman on 2006-12-27
kylejack:
There are a few other topics that involve libsdl1.2-dev problems that may be able to help:
[Re: Dosbox 0.65 is out!]("http://ubuntuforums.org/showthread.php?t=158723&page=2")
[Can't Install libsdl1.2-dev in dapper]("http://ubuntuforums.org/showthread.php?p=1570003")
[Re: Wanna 3d a retro game... help?!]("http://www.ubuntuforums.org/showthread.php?p=1928157")

If I got this error I would backup my sources.list and try a fresh, new sources list.  [Source-o-matic]("http://www.ubuntu-nl.org/source-o-matic/") might help.  If that didn't work I would try to install the unmet dependencies listed in the error message (libglu-dev).

---

### Post by musse1 on 2006-12-28
I get lots and lots of warnings when I do the "make" command after doing exactly as said in the first post of how to install ffmpeg. I do have changed the repositories and gotten the codecs. But the x264 codec doesnt work. Don't know why.

./configure --enable-gpl --enable
-pp --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-dc1394 --
enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --ena
ble-xvid --enable-pthreads

Efter doing this command without the x264 codec I get this:

install prefix   /usr/local
source path      /home/musse1/ffmpeg-0.cvs20060823
C compiler       gcc
make             make
CPU              x86 (generic)
big-endian       no
inttypes.h       yes
broken inttypes.h no
MMX enabled      yes
Vector Builtins  yes
3DNow! Builtins  yes
gprof enabled    no
zlib enabled     yes
libgsm enabled   yes
mp3lame enabled  yes
libogg enabled   yes
Vorbis enabled   yes
FAAD enabled     yes
faadbin enabled  no
FAAC enabled     yes
XviD enabled     yes
x264 enabled     no
a52 support      yes
a52 dlopened     no
DTS support      yes
pp support       yes
Software Scaler enabled no
debug symbols    no
strip symbols    yes
optimize         yes
static           yes
shared           no
video hooking    yes
SDL support      yes
Imlib2 support   yes
FreeType support yes
Sun medialib support no
pthreads support yes
AMR-NB float support no
AMR-NB fixed support no
AMR-WB float support no
AMR-WB IF2 support no
network support      yes
IPv6 support         yes
.align is power-of-two no
License: GPL
Creating config.mak and config.h...

After this I do the "make" command and the server is working for a couple of minutes and are printing lots of warning messages. When I try to run ffmpeg -i video.avi -b 250 -s 320x240 -r 30 -f avi -an newmovie.avi it is just saying that codec isn't found.

What to do about this? HELP ME!

---

### Post by FakeOutdoorsman on 2006-12-28
Do you have checkinstall installed?
```

sudo apt-get install checkinstall

```

Do you have x264 installed?
```

sudo apt-get install x264

```

What are some of the errors you get when you try to install ffmpeg with --enable-x264?

---

### Post by musse1 on 2006-12-28
I managed to install checkinstall now but still the same problem. It keep saying unsupported codec.

This is the message when I try to enable x264:

ERROR: x264 not found
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
[email]ffmpeg-devel@mplayerhq.hu[/email] mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.

---

### Post by FakeOutdoorsman on 2006-12-28
I don't think you have x264 installed.  Look at my last post (I must have edited it while you were responding).

---

### Post by musse1 on 2006-12-28
couldnt find package x264...what to do?

---

### Post by patsissons on 2006-12-28
> **musse1 said:**
> couldnt find package x264...what to do?

The package you seek is called x264-bin, and you will also need the dev package libx264-dev

also, i don't recommend using checkinstall if you don't have to.  You can get the ffmpeg source package by doing

apt-get source ffmpeg

from there, all you need to do is cd into the ffmpeg directory created and then do the following:

fakeroot debian/rules binary

this will create actual *.deb files that you can install with dpkg -i, this is a much better (and cleaner) approach to building your own packages.  Note that you will either have to edit the rules file or do a ./configure with all the flags you want before hand (otherwise it will just build the default ubuntu package).  Also note that this requires the package fakeroot (apt-get install fakeroot).

---

### Post by rodney16 on 2006-12-28
hi im new  to linux and i cant figure out what im doin wrong everytime i try to run
ipodvidenc video.avi i get this message
rodney@rodney-desktop:~$ ipodvidenc video.avi
What would you like to name the output file (sans extension)?
ipod vids
ipod vids will be located in /home/rodney. Is this acceptable? [y/n]
y
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-ogm
  built on Apr 29 2006 00:14:12, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
video.avi: I/O error occured
Usually that means that input file is truncated and/or corrupted.

help please

---

### Post by DaveQB on 2006-12-29
> **BetaMaster said:**
> Ah, figured it out. Sorry to have seemed stupid.

What was your solution ?

---

### Post by shriphani on 2006-12-30
could someone tell me what the problem is? i encountered it after running make

x264.c:21:18: error: x264.h: No such file or directory
x264.c:25: error: syntax error before ‘x264_param_t’
x264.c:25: warning: no semicolon at end of struct or union
x264.c:26: warning: type defaults to ‘int’ in declaration of ‘enc’
x264.c:26: warning: data definition has no type or storage class
x264.c:27: error: syntax error before ‘pic’
x264.c:27: warning: type defaults to ‘int’ in declaration of ‘pic’
x264.c:27: warning: data definition has no type or storage class
x264.c:29: error: syntax error before ‘}’ token
x264.c:29: warning: type defaults to ‘int’ in declaration of ‘X264Context’
x264.c:29: warning: data definition has no type or storage class
x264.c: In function ‘X264_log’:
x264.c:35: error: ‘X264_LOG_ERROR’ undeclared (first use in this function)
x264.c:35: error: (Each undeclared identifier is reported only once
x264.c:35: error: for each function it appears in.)
x264.c:35: error: array index in initializer not of integer type
x264.c:35: error: (near initialization for ‘level_map’)
x264.c:36: error: ‘X264_LOG_WARNING’ undeclared (first use in this function)
x264.c:36: error: array index in initializer not of integer type
x264.c:36: error: (near initialization for ‘level_map’)
x264.c:37: error: ‘X264_LOG_INFO’ undeclared (first use in this function)
x264.c:37: error: array index in initializer not of integer type
x264.c:37: error: (near initialization for ‘level_map’)
x264.c:38: error: ‘X264_LOG_DEBUG’ undeclared (first use in this function)
x264.c:38: error: array index in initializer not of integer type
x264.c:38: error: (near initialization for ‘level_map’)
x264.c: At top level:
x264.c:49: error: syntax error before ‘x264_nal_t’
x264.c: In function ‘encode_nals’:
x264.c:51: error: ‘buf’ undeclared (first use in this function)
x264.c:54: error: ‘nnal’ undeclared (first use in this function)
x264.c:55: warning: implicit declaration of function ‘x264_nal_encode’
x264.c:55: error: ‘size’ undeclared (first use in this function)
x264.c:55: error: ‘nals’ undeclared (first use in this function)
x264.c: In function ‘X264_frame’:
x264.c:67: error: ‘x4’ undeclared (first use in this function)
x264.c:69: error: ‘x264_nal_t’ undeclared (first use in this function)
x264.c:69: error: ‘nal’ undeclared (first use in this function)
x264.c:71: error: ‘x264_picture_t’ undeclared (first use in this function)
x264.c:71: error: syntax error before ‘pic_out’
x264.c:73: error: ‘X264_CSP_I420’ undeclared (first use in this function)
x264.c:82: error: ‘X264_TYPE_AUTO’ undeclared (first use in this function)
x264.c:84: warning: implicit declaration of function ‘x264_encoder_encode’
x264.c:84: error: ‘pic_out’ undeclared (first use in this function)
x264.c:95: error: ‘X264_TYPE_IDR’ undeclared (first use in this function)
x264.c:96: error: ‘X264_TYPE_I’ undeclared (first use in this function)
x264.c:99: error: ‘X264_TYPE_P’ undeclared (first use in this function)
x264.c:102: error: ‘X264_TYPE_B’ undeclared (first use in this function)
x264.c:103: error: ‘X264_TYPE_BREF’ undeclared (first use in this function)
x264.c: In function ‘X264_close’:
x264.c:117: error: ‘x4’ undeclared (first use in this function)
x264.c:120: warning: implicit declaration of function ‘x264_encoder_close’
x264.c: In function ‘X264_init’:
x264.c:128: error: ‘x4’ undeclared (first use in this function)
x264.c:130: warning: implicit declaration of function ‘x264_param_default’
x264.c:164: warning: implicit declaration of function ‘x264_encoder_open’
make[1]: *** [x264.o] Error 1
make[1]: Leaving directory `/home/shriphani/ffmpeg-0.cvs20050918/libavcodec'
make: *** [lib] Error 2
[email]shriphani@ubuntu-box:~/ffmpeg-0.cvs[/email]20050918$

---

### Post by xyz on 2006-12-30
Thanks a lot for the guide. Great job!
When I get to:
```
tar xzf libgpod-0.3.2.tar.gz
```
I get:
> th@luser:~/mpeg4ip-1.5.0.1$ tar xzf libgpod-0.3.2.tar.gz
tar: libgpod-0.3.2.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

On the SourceForge site, I noticed it's now:
> libgpod-0.4.0
but it doesn't work either. What am I doing wrong?

---

### Post by etola on 2006-12-30
Hi, 

I'm having the below error while I'm trying to compile mpeg4ip. any idea why this could happen ? 

```
Making all in ffmpeg
make[5]: Entering directory `/home/tola/downloads/mpeg4ip-1.5.0.1/player/plugin/audio/ffmpeg'
if /bin/bash ../../../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../../../.. -I../../../../player/src -I../../../../player/lib -I../../../../include -I../../../../lib -I../../../../lib/mp4av -I../../../../lib/mp4v2 -I../../../../lib/sdp    -D_REENTRANT -DNOCONTROLS -fexceptions -Wall -Wno-char-subscripts -Woverloaded-virtual -Wno-unknown-pragmas -Wno-deprecated -Wformat=2 -Wpointer-arith -Wsign-compare -g -O2 -DMPEG4IP -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -MT ffmpeg.lo -MD -MP -MF ".deps/ffmpeg.Tpo" -c -o ffmpeg.lo ffmpeg.cpp; \
        then mv -f ".deps/ffmpeg.Tpo" ".deps/ffmpeg.Plo"; else rm -f ".deps/ffmpeg.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I../../../.. -I../../../../player/src -I../../../../player/lib -I../../../../include -I../../../../lib -I../../../../lib/mp4av -I../../../../lib/mp4v2 -I../../../../lib/sdp -D_REENTRANT -DNOCONTROLS -fexceptions -Wall -Wno-char-subscripts -Woverloaded-virtual -Wno-unknown-pragmas -Wno-deprecated -Wformat=2 -Wpointer-arith -Wsign-compare -g -O2 -DMPEG4IP -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -MT ffmpeg.lo -MD -MP -MF .deps/ffmpeg.Tpo -c ffmpeg.cpp  -fPIC -DPIC -o .libs/ffmpeg.o
ffmpeg.cpp: In function 'codec_data_t* ffmpeg_create(const char*, const char*, int, int, format_list_t*, audio_info_t*, const uint8_t*, uint32_t, audio_vft_t*, void*)':
ffmpeg.cpp:169: error: invalid conversion from 'void*' to 'uint8_t*'
make[5]: *** [ffmpeg.lo] Error 1
make[5]: Leaving directory `/home/tola/downloads/mpeg4ip-1.5.0.1/player/plugin/audio/ffmpeg'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/tola/downloads/mpeg4ip-1.5.0.1/player/plugin/audio'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/tola/downloads/mpeg4ip-1.5.0.1/player/plugin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tola/downloads/mpeg4ip-1.5.0.1/player'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tola/downloads/mpeg4ip-1.5.0.1'
make: *** [all] Error 2

```

---

### Post by FakeOutdoorsman on 2006-12-30
shriphani: do you have x264 installed?  Try installing it via Synaptic.  You could use the [x264 SVN]("http://developers.videolan.org/x264.html") as well, but you will encounter errors with mpeg4ip.  If you want to use x264 SVN then read post #[347]("http://ubuntuforums.org/showpost.php?p=1907905&postcount=347").

xyz: you will get those errors if you try to run tar on a file that does not exist in the current directory.  Find out where you downloaded libgpod-0.3.2.tar.gz to and run "tar xzf libgpod-0.3.2.tar.gz" in that same directory.

---

### Post by etola on 2006-12-30
ok, forget about that. I hacked the code a little bit and now it compiles...

> **etola said:**
> Hi, 

I'm having the below error while I'm trying to compile mpeg4ip. any idea why this could happen ? 

```
Making all in ffmpeg
make[5]: Entering directory `/home/tola/downloads/mpeg4ip-1.5.0.1/player/plugin/audio/ffmpeg'
if /bin/bash ../../../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../../../.. -I../../../../player/src -I../../../../player/lib -I../../../../include -I../../../../lib -I../../../../lib/mp4av -I../../../../lib/mp4v2 -I../../../../lib/sdp    -D_REENTRANT -DNOCONTROLS -fexceptions -Wall -Wno-char-subscripts -Woverloaded-virtual -Wno-unknown-pragmas -Wno-deprecated -Wformat=2 -Wpointer-arith -Wsign-compare -g -O2 -DMPEG4IP -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -MT ffmpeg.lo -MD -MP -MF ".deps/ffmpeg.Tpo" -c -o ffmpeg.lo ffmpeg.cpp; \
        then mv -f ".deps/ffmpeg.Tpo" ".deps/ffmpeg.Plo"; else rm -f ".deps/ffmpeg.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I../../../.. -I../../../../player/src -I../../../../player/lib -I../../../../include -I../../../../lib -I../../../../lib/mp4av -I../../../../lib/mp4v2 -I../../../../lib/sdp -D_REENTRANT -DNOCONTROLS -fexceptions -Wall -Wno-char-subscripts -Woverloaded-virtual -Wno-unknown-pragmas -Wno-deprecated -Wformat=2 -Wpointer-arith -Wsign-compare -g -O2 -DMPEG4IP -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -MT ffmpeg.lo -MD -MP -MF .deps/ffmpeg.Tpo -c ffmpeg.cpp  -fPIC -DPIC -o .libs/ffmpeg.o
ffmpeg.cpp: In function 'codec_data_t* ffmpeg_create(const char*, const char*, int, int, format_list_t*, audio_info_t*, const uint8_t*, uint32_t, audio_vft_t*, void*)':
ffmpeg.cpp:169: error: invalid conversion from 'void*' to 'uint8_t*'
make[5]: *** [ffmpeg.lo] Error 1
make[5]: Leaving directory `/home/tola/downloads/mpeg4ip-1.5.0.1/player/plugin/audio/ffmpeg'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/tola/downloads/mpeg4ip-1.5.0.1/player/plugin/audio'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/tola/downloads/mpeg4ip-1.5.0.1/player/plugin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tola/downloads/mpeg4ip-1.5.0.1/player'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tola/downloads/mpeg4ip-1.5.0.1'
make: *** [all] Error 2

```

---

### Post by xyz on 2006-12-31
> **FakeOutdoorsman said:**
> shriphani: do you have x264 installed?  Try installing it via Synaptic.  You could use the [x264 SVN]("http://developers.videolan.org/x264.html") as well, but you will encounter errors with mpeg4ip.  If you want to use x264 SVN then read post #[347]("http://ubuntuforums.org/showpost.php?p=1907905&postcount=347").

xyz: you will get those errors if you try to run tar on a file that does not exist in the current directory.  Find out where you downloaded libgpod-0.3.2.tar.gz to and run "tar xzf libgpod-0.3.2.tar.gz" in that same directory.
How stupid of me! The HowTo says:
> wget [http://umn.dl.sourceforge.net/sourceforge/gtkpod/libgpod-0.4.tar.gz](http://umn.dl.sourceforge.net/sourceforge/gtkpod/libgpod-0.4.tar.gz)
tar xzf libgpod-0.3.2.tar.gz
cd libgpod-0.3.2/
It should say:
> tar xzf libgpod-0.4.0.tar.gz
cd libgpod-0.4.0/
..then tar woks much better!!
Now it's obvious...I can't tar 0.3.2 when I downloaded 0.4.0!!!
Must be the end of the year!!
Thanks for the help.

---

### Post by FernandoMilton on 2007-01-04
For all you guys with trouble compiling ffmpeg, getting the "ERROR: x264 not found" error message.

The problem, as I found [here]("http://lists.mplayerhq.hu/pipermail/ffmpeg-devel/2006-August/013616.html") is that you must to enable pthreads when compiling ffmpeg with x264 support, so, append "--enable-pthreads" to the end of your "./configure" line and it will compile OK :)

---

### Post by TuxGirl on 2007-01-06
I'm hitting the same problem as some of the other people, but I didn't see an answer here.  

ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-ogm 
  built on Apr 29 2006 00:14:12, gcc: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)
Input #0, mov,mp4,m4a,3gp,3g2, from '300k.mov':
  Duration: 00:01:36.2, start: 0.000000, bitrate: 390 kb/s
  Stream #0.0: Video: svq1, yuv410p, 320x240, 600.00 fps
  Stream #0.1: Audio: QDM2 / 0x324D4451, 22050 Hz, mono
File 'ipod/300k.mov' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'ipod/300k.mov':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, 600.00 fps, q=3-5, 700 kb/s
  Stream #0.1: Audio: aac, 22050 Hz, mono, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[aac @ 0x83346a8]libfaac doesn't support this output format!
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

I'd appreciate any pointers on what could be wrong.  My command-line is below:
ffmpeg -i "$1" -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 ipod/$new_name;

Thanks!  
~TuxGirl

---

### Post by jak on 2007-01-14
Please note, when building ffmpeg you also need to install the following packages beforehand:-

libdts-dev libvorbis-dev libx264-dev libgsm1-dev libdc1394-13-dev libraw1394-dev

( Ubuntu Edgy, AMD64 )

---

### Post by stoic on 2007-01-18
TuxGirl:

Looks like your audio settings are causing problems.

You are asking ffmpeg to encode aac at a high bitrate (192kbps) but low frequency and only in mono (these last two are probably because you are using a low quality source file).

Either try a higher quality source, or reduce the bitrate (the -ab option).
It may also help to state the frequency and channels directly, ie -ar 22050 and -ac 1 (for mono).

Stoic

---

### Post by bitterbug on 2007-01-18
If anyone else has run into 'unk208' compile errors with the latest gtkpod/libgpod releases, just edit the relevant files in the /src directory.

Replace 'unk208' with 'mediatype' in:

file.c
file_itunesdb.c

and everything should work fine after that.

thanks to this thread:
[http://article.gmane.org/gmane.comp.ipod.gtkpod/1618/match=track+member+named+unk208](http://article.gmane.org/gmane.comp.ipod.gtkpod/1618/match=track+member+named+unk208)

---

### Post by musse1 on 2007-01-22
Gave this a try again and followed this tutorial:
[http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu-edgy/](http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu-edgy/)
But I still can't get it to encode ANYTHING! If I use x264:

ffmpeg -i /var/www/www/stream/tackle.avi -vcodec x264 -acodec mp3 -s 340x280 /var/www/www/stream/test.avi

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-vorbis --enable-libogg --ena
ble-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp
3lame --enable-faad --enable-faac --enable-xvid --enable-pthreads --enable-x264
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Jan 22 2007 17:10:17, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-
13ubuntu5)
Input #0, avi, from '/var/www/www/stream/tackle.avi':
  Duration: 00:00:29.1, start: 0.000000, bitrate: 545 kb/s
  Stream #0.0: Video: 3IV2 / 0x32564933, 320x256, 25.00 fps(r)
Unknown codec 'x264'


This is how it looks with any of the codecs I try to use. If I use xvid instead I get this result: Unsupported codec (id=0) for input stream #0.0. What to do?!?!?

---

### Post by dumbkiwi on 2007-01-22
You need to call the codec 'h264', not 'x264'.  However, you may want to try [http://thinliquidfilm.org](http://thinliquidfilm.org) which is a nice gui app for encoding and transferring video to your ipod.

---

### Post by musse1 on 2007-01-23
Then it says this instead:

ffmpeg -i /var/www/www/stream/tackle.avi -vcodec h264
-acodec mp3 -s 340x280 /var/www/www/stream/test.avi
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-vorbis --enable-libogg --ena
ble-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp
3lame --enable-faad --enable-faac --enable-xvid --enable-pthreads --enable-x264
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Jan 22 2007 17:10:17, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-
13ubuntu5)
Input #0, avi, from '/var/www/www/stream/tackle.avi':
  Duration: 00:00:29.1, start: 0.000000, bitrate: 545 kb/s
  Stream #0.0: Video: 3IV2 / 0x32564933, 320x256, 25.00 fps(r)
File '/var/www/www/stream/test.avi' already exists. Overwrite ? [y/N] y
PIX_FMT_YUV420P will be used as an intermediate format for rescaling
Output #0, avi, to '/var/www/www/stream/test.avi':
  Stream #0.0: Video: h264, yuv420p, 340x280, q=2-31, 200 kb/s, 25.00 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
[h264 @ 0x85368d8]width or height not divisible by 16 (340x280), compression wil
l suffer.
[h264 @ 0x85368d8]using cpu capabilities MMX MMXEXT SSE 3DNow!
Unsupported codec (id=0) for input stream #0.0

---

### Post by endersshadow on 2007-01-23
Your problem isn't h264, it's 3IV2.  At the moment, this is a read only codec for Linux ([http://www.3ivx.com/download/unix.html](http://www.3ivx.com/download/unix.html)) and ffmpeg does not support it.

---

### Post by musse1 on 2007-01-23
Managed to encode with php:

exec("/usr/local/bin/ffmpeg -i /var/www/www/stream/video/Yes.wmv -b 300 -maxrate 300 -r 25 -s 384x256 -vcodec h264 -acodec mp3 /var/www/www/stream/video/test.avi");

But the video gets fliped upsidedown when played in the browser but not in the mediaplayer. Whats the problem? Is there a way to flip the files with fmpeg?

---

### Post by djmadkins on 2007-01-28
I've been using the command line to do this and was hoping one of you guys could help me.

Sometimes when transcoding the contents of a DVD for my Ipod I will get the French soundtrack or the director's commentary instead of the english soundtrack which is what I want.


I do a two step process:

1)
```
mplayer dvd://1 -dumpstream -dumpfile dvdcache.vob
```

Now this VOB file is the input into a shell script that issues the following:

2)
```
ffmpeg -y -i "$1" -f mp4 -vcodec xvid -maxrate 1000 -b 400 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 128 -s 320x240 "$2"
```

On a recent transcode I got the following output which ends up being in french:

```
Input #0, mpeg, from 'blackhawk_down.vob':
  Duration: 02:24:19.7, start: 0.041500, bitrate: 5195 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480, 9800 kb/s, 29.97 fps(r)
  Stream #0.1[0x81]: Audio: ac3, 48000 Hz, stereo, 192 kb/s
  Stream #0.2[0x80]: Audio: ac3, 48000 Hz, 5:1, 448 kb/s
Output #0, mp4, to 'blackhawk_down.mp4':
  Stream #0.0: Video: xvid, yuv420p, 320x240, q=3-5, 400 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: aac, 48000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
```

I suspect that the audio I really want is the stream 0.2 and this is my question.. What is the format or use of the map switch to do this?

thanks in advance!
Jeff

---

### Post by FakeOutdoorsman on 2007-01-28
I've never done this, but I believe you will want to add "-map 0:0 -map 0:2" to your command so in the end it might look like this:

```

ffmpeg -y -i "$1" -map 0:0 -map 0:2 -f mp4 -vcodec xvid -maxrate 1000 -b 400 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 128 -s 320x240 "$2"

```

More info:
[ffmpeg audio/video manipulation]("http://howto-pages.org/ffmpeg/#map")
[Converting Video Formats with FFmpeg]("http://www.linuxjournal.com/article/8517")

---

### Post by patsissons on 2007-01-30
I can't remember if I have posted this before, but in any case, I have built a script that works quite well for encoding video for the ipod.  You will need ffmpeg with all the compile time options enabled, if you don't have this already, i have another thread that explains how to get it without too much trouble.

[http://ubuntuforums.org/showthread.php?t=325963]("http://ubuntuforums.org/showthread.php?t=325963")

the script itself is completely configurable, so you can change any of the default settings if you like.  The default settings are designed for small file size with no noticeable loss of quality _while viewing on the ipod._  If you plan on using the video on a larger screen i would recommend bumping up the video (and probably also the audio) quality.  Also, this script uses a 2pass h264 encode by default.  here is the script:

```

#!/bin/sh
# ipodvidenc
# Created by Pat Sissons

# general format config
# PASSLOG   = where the 1st pass data is stored
# FORMAT    = type of video file, for ipod this must be either mov, mp4, or h264
PASSLOG=/tmp/ipodvidenc.pass
FORMAT=h264

# video format config
# VCODEC    = video codec, generally h264 or mpeg4
# VBITRATE  = video bit rate (300 looks decent)
# VMAXRATE  = max video bit rate (400 is good)
# VSIZE     = video size [WxH] (320x240 is standard)
# ASPECT    = aspect ratio (4:3 is standard)
# FRAMERATE = fps for the video (ntsc is standard, but 15 cuts the filesize down a lot)
VCODEC=h264
VBITRATE=300
VMAXRATE=400
VSIZE=320x240
ASPECT=4:3
FRAMERATE=15

# video advanced settings
# MOTION    = motion estimator (epzs, full, etc...)
# QPEL      = subpel refinement quality (1 = slow/HQ, 8 = fast/LQ)
# REFS      = encode quality? (higher values = higher quality but slower)
# BUFSIZE   = rate control buffer size
# GOPSIZE   = how many frames between I-Frames
MOTION=epzs
QPEL=8
REFS=1
BUFSIZE=244
GOPSIZE=300

# audio format settings
# ACODEC    = audio codec (this shouldn't change from aac)
# AFREQ     = audio frequency (48000 is normal)
# ABITRATE  = audio bit rate (48 sounds good with standard ipod headphones)
ACODEC=aac
AFREQ=48000
ABITRATE=48

while [ $# -gt 1 ]
do
    case "$1" in
            --help)
                echo "Options :"
                echo -e "\t--help (display this help text)\n"
                echo -e "\t--passlog s (default is /tmp/ipodvidenc.pass)"
                echo -e "\t--format s (default is h264)"
                echo -e "\t--vcodec s (default is h264)"
                echo -e "\t--vbitrate s (default is 300)"
                echo -e "\t--vmaxrate s (default is 400)"
                echo -e "\t--vsize s (default is 320x240)"
                echo -e "\t--aspect s (default is 4:3)"
                echo -e "\t--framerate s (default is 15)"
                echo -e "\t--motion s (default is epzs)"
                echo -e "\t--qpel s (default is 8)"
                echo -e "\t--refs s (default is 1)"
                echo -e "\t--bufsize s (default is 244)"
                echo -e "\t--gopsize s (default is 300)"
                echo -e "\t--acodec s (default is aac)"
                echo -e "\t--afreq s (default is 48000)"
                echo -e "\t--abitrate s (default is 48)"
                exit
                ;;
            --passlog)
                PASSLOG=$2
                shift 2
                ;;
            --format)
                FORMAT=$2
                shift 2
                ;;
            --vcodec)
                VCODEC=$2
                shift 2
                ;;
            --vbitrate)
                VBITRATE=$2
                shift 2
                ;;
            --vmaxrate)
                VMAXRATE=$2
                shift 2
                ;;
            --vsize)
                VSIZE=$2
                shift 2
                ;;
            --aspect)
                ASPECT=$2
                shift 2
                ;;
            --framerate)
                FRAMERATE=$2
                shift 2
                ;;
            --motion)
                MOTION=$2
                shift 2
                ;;
            --qpel)
                QPEL=$2
                shift 2
                ;;
            --refs)
                REFS=$2
                shift 2
                ;;
            --bufsize)
                BUFSIZE=$2
                shift 2
                ;;
            --gopsize)
                GOPSIZE=$2
                shift 2
                ;;
            --acodec)
                ACODEC=$2
                shift 2
                ;;
            --afreq)
                AFREQ=$2
                shift 2
                ;;
            --abitrate)
                ABITRATE=$2
                shift 2
                ;;
            *)
                echo "Unknown Option [$1]"
                shift
                ;;
    esac
done

input_file=$1

output_file=`basename "${input_file}"`

ffmpeg -y -pass 1 -passlogfile ${PASSLOG} -i "${input_file}" -vcodec ${VCODEC} -me ${MOTION} -refs ${REFS} -subq ${QPEL} -b ${VBITRATE} -rc_max_rate ${VMAXRATE} -rc_buffer_size ${BUFSIZE} -s ${VSIZE} -r ${FRAMERATE} -max_b_frames 0 -level 13 -g ${GOPSIZE} -f ${FORMAT} /dev/null
ffmpeg -y -pass 2 -passlogfile ${PASSLOG} -i "${input_file}" -vcodec ${VCODEC} -me ${MOTION} -refs ${REFS} -subq ${QPEL} -b ${VBITRATE} -rc_max_rate ${VMAXRATE} -rc_buffer_size ${BUFSIZE} -s ${VSIZE} -r ${FRAMERATE} -max_b_frames 0 -level 13 -g ${GOPSIZE} -acodec ${ACODEC} -ar ${AFREQ} -ab ${ABITRATE} "${output_file}.mp4"

```

The only problem with it at the moment is that it dumps an h264 log file in your current directory.  I haven't figured out how to set the location of this yet, but it is fairly small and low priority.  Hope this is useful for some people.

---

### Post by djmadkins on 2007-01-30
-map 0:0 -map 0.2 added to the line did the trick.

thanks :)

---

### Post by c.dric on 2007-02-04
hi, 

i've used the ipodvidenc script successfully to encode avi files in the 4:3 aspect ... but most of my movies are way too stretched ... so i've tried a few other aspects like 16:9 or 2.4761 but those movies don't play on my ipod. i get a blackscreen for a second or 20 then it goes back to the menu.

here are the options i'm using (the exact same options with 4:3 aspect worked perfectly) :

```
ffmpeg -i ${input_file} -f mp4 -vcodec xvid -maxrate 700 -b 2500 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 640x480 -aspect 16:9 .... 
```

for the record ... it's a new 30gb video ipod (i guess that's a 5.5) version is 1.2.1

any ideas what i'm doing wrong ?

---

### Post by FakeOutdoorsman on 2007-02-04
You need to change 640x480 to 640x352 for 16:9 widescreen movies.

---

### Post by c.dric on 2007-02-05
> **FakeOutdoorsman said:**
> You need to change 640x480 to 640x352 for 16:9 widescreen movies.

Thanks, that did it ...

I do have another question ... 
There is one of my movie that's out of sync after the encoding ... only one out of the seven i did so far. the original avi is fine so i don't know what the problem may be.

here is the command i've used : ```
ffmpeg -i ${input_file} -f mp4 -vcodec xvid -maxrate 700 -b 2500 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 640x352 ....
```

i've tried with only one pass then i tried with 2 passes but with the same result.
what else could i try ?

---

### Post by endersshadow on 2007-02-05
c.dric, do you have the output for ffmpeg for that?

---

### Post by c.dric on 2007-02-05
> **endersshadow said:**
> c.dric, do you have the output for ffmpeg for that?

output of pass 1 :

```
cedric@mobile:$ ffmpeg -i movie.avi -f mp4 -vcodec xvid -maxrate 700 -b 2500 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 640x296 -pass 1 /home/cedric/movie.mov
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-libogg --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-x264 
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Feb  2 2007 22:39:15, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
Input #0, avi, from 'movie.avi':
  Duration: 02:24:32.3, start: 0.000000, bitrate: 870 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 588x244, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 112 kb/s
Output #0, mp4, to '/home/cedric/movie.mov':
  Stream #0.0: Video: xvid, yuv420p, 640x296, q=3-5, pass 1, 2500 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: aac, 48000 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=216808 q=2.0 Lsize= 2309066kB time=8669.8 bitrate=2181.8kbits/s    
video:2129302kB audio:174884kB global headers:0kB muxing overhead 0.211812%

```

output of pass 2 :

```
cedric@mobile:$ ffmpeg -i movie.avi -f mp4 -vcodec xvid -maxrate 700 -b 2500 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 640x296 -pass 2 /home/cedric/movie.mov
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-libogg --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-x264 
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Feb  2 2007 22:39:15, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
Input #0, avi, from 'movie.avi':
  Duration: 02:24:32.3, start: 0.000000, bitrate: 870 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 588x244, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 112 kb/s
Output #0, mp4, to 'movie.mov':
  Stream #0.0: Video: xvid, yuv420p, 640x296, q=3-5, pass 2, 2500 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: aac, 48000 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=216808 q=3.0 Lsize= 1577240kB time=8669.8 bitrate=1490.3kbits/s    
video:1397476kB audio:174884kB global headers:0kB muxing overhead 0.310396%

```

---

### Post by endersshadow on 2007-02-05
It's possibly because your new audio bitrate is greater than the previous audio bitrate.  Try leaving the -ab 192 tag off and just do one pass to save a bit of time to test it.

---

### Post by c.dric on 2007-02-05
i removed the -ab 192 but that didn't solve it.
here is the output : 

```
cedric@mobile:/$ ffmpeg -i movie.avi -f mp4 -vcodec xvid -maxrate 700 -b 2500 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -s 640x296 /home/cedric/movie.mov
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-libogg --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-x264 
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Feb  2 2007 22:39:15, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
Input #0, avi, from 'movie.avi':
  Duration: 02:24:32.3, start: 0.000000, bitrate: 870 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 588x244, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 112 kb/s
Output #0, mp4, to '/home/cedric/movie.mov':
  Stream #0.0: Video: xvid, yuv420p, 640x296, q=3-5, 2500 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: aac, 48000 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=216808 q=3.0 Lsize= 1459927kB time=8669.8 bitrate=1379.5kbits/s    
video:1387205kB audio:67842kB global headers:0kB muxing overhead 0.335423%
```

should i try another codec ?

---

### Post by endersshadow on 2007-02-05
Hrm.  You can try playing with the -async flag by adding -async 10 or if you just want to set the first timestamp correctly, -async 1.  Let me know.

---

### Post by c.dric on 2007-02-05
i did a test on the first 10000 frames with the -async 1 option and it looks (or sounds) ok now :)

i'm gonna try the full film.

thanks endersshadow :)

---

### Post by c.dric on 2007-02-05
ok, full film was fine with -async 1 option too.

i did notice something strange with gtkpod or the ipod tho : 

after my successful encoding i erased the out of sync copy i had on my ipod and copied the good copy from my computer using gtkpod. i try the newly transfered copy on my ipod and it was out of sync. 

so i removed the copy on my ipod again, renamed the good copy on my comp and transfered again using gtkpod and then it was fine. 

is there some kind of caching system in gtkpod or the ipod ? is it a bug ?

anyway it's nothing critical. my movies are all great now. i'm just curious :)

---

### Post by endersshadow on 2007-02-05
Well, you do have to commit to the iPod with gtkpod, since it caches everything and saves the write until you hit the "Write to iPod" button.  That way, it's much faster.  That's the only thing I can think of.

Glad to hear you got it working!

---

### Post by c.dric on 2007-02-05
> **endersshadow said:**
> Well, you do have to commit to the iPod with gtkpod, since it caches everything and saves the write until you hit the "Write to iPod" button. 

ooh ](*,) that must be it. i didn't save the changes after removing the old version so it must have cancelled the removal when i added a new copy with the same name.

---

### Post by NorthernLights on 2007-02-13
For all you people who are trying to easily encode videos to use on iPod Video : I'm developping a GUI to mplayer, mencoder and mp4creator to do just that. It's currently in alpha version but it's usable. Check [http://sive.sourceforge.net](http://sive.sourceforge.net) ;)

---

### Post by endersshadow on 2007-02-14
> **NorthernLights said:**
> For all you people who are trying to easily encode videos to use on iPod Video : I'm developping a GUI to mplayer, mencoder and mp4creator to do just that. It's currently in alpha version but it's usable. Check [http://sive.sourceforge.net](http://sive.sourceforge.net) ;)

Best of luck to you.  Looks promising.  My suggestion would be not to name it Simple iPod Video Encoder if you want to add other functionality to it later, as a more generic mencoder frontend.  Just a thought...at any rate, good luck.

Oh, and Sourceforge's shell is down so I can't upload a web page, but at any rate, I released Vive 2.0.0-beta1 today.  All the beta1 means is that I've got a bit of code cleanup to do, especially w/r/t slight memory leaks that really don't effect things too much, but drive me crazy, so I'll fix them.  You can download it at the [Vive Project Page](https://sourceforge.net/projects/vive).  Feel free to give me feedback either here or at endersshadow AT users DOT sourceforge DOT net.  Thanks!

---

### Post by NorthernLights on 2007-02-14
Thanks for the comments :) 

Did you include subtitles support in your new version ? I tried VIVE before, but could not find this functionality ; that contributed to give me the idea of SIVE.

---

### Post by endersshadow on 2007-02-14
Not in the beta.  I'm putting them in for the actual release, though.

---

### Post by InsaneDuz on 2007-02-17
> **etola said:**
> ok, forget about that. I hacked the code a little bit and now it compiles...

etola: I came across the same problem, but I'm not sure what modifications to make to the code to fix it. Can you explain what you did please?

---

### Post by InsaneDuz on 2007-02-17
> **InsaneDuz said:**
> etola: I came across the same problem, but I'm not sure what modifications to make to the code to fix it. Can you explain what you did please?

Never mind, I figured it out.  For anyone else that comes across this issue, to fix it, replace the following lines of code:

in file: player/plugin/audio/ffmpeg/ffmpeg.cpp, line 169:
replace:
```
ffmpeg->m_c->extradata = (void *)userdata;
```
with:
```
ffmpeg->m_c->extradata = (uint8_t *)userdata;
```

in file: player/plugin/video/ffmpeg/ffmpeg.cpp, line 258:
replace:
```
ffmpeg->m_c->extradata = (void *)userdata;
```
with:
```
ffmpeg->m_c->extradata = (uint8_t *)userdata;
```

This should resolve this compile error.

---

### Post by c.dric on 2007-03-02
how should i do to encode the subtitles in the movie with ffmpeg ?

i have a .srt file in the same directory and the same name as the .avi file.

mplayer plays the movie with the subs but ffmpeg doesn't add the subs to the output movie and i couldn't find an option in the man pages.

thanks.

ps : i've downloaded the SIVE program but i'm having problems compiling the mpeg4ip program required.

---

### Post by rabid9797 on 2007-03-04
i have a question about Vive! where do i find libvte? i have libvte9 and such installed from apt-get but there is no just "libvte" :confused:

---

### Post by wilbur.harvey on 2007-03-05
When trying to compile mpeg4ip-1.5.0.1 I get the following error. (Feisty as of 2007-03-02)

/data/software/mpeg4ip-1.5.0.1/player/src/video_sdl.cpp:280: undefined reference to `XMoveWindow'
collect2: ld returned 1 exit status

wharvey@LUNFORCE40:/data/software/mpeg4ip-1.5.0.1$ grep -R XMoveWindow *
player/src/video_sdl.cpp:       XMoveWindow(info.info.x11.display, info.info.x11.wmwindow, 
Binary file player/src/.libs/video_sdl.o matches
Binary file player/src/.libs/libmp4sdlvideo.a matches
Binary file player/src/video_sdl.o matches
wharvey@LUNFORCE40:/data/software/mpeg4ip-1.5.0.1$ 

Any ideas?

---

### Post by endersshadow on 2007-03-07
Okay, sorry for the late reply...real world stuff has taken me ahold and won't let go, but I'll do this as quick as possible:

c.dric: When I try to get subtitles with ffmpeg, I get nothing.  I would advise mencoder, which can be used via AcidRip or gmencoder.  Sorry :-|

rabid: sudo apt-get install libvte-dev

wilbur: sudo apt-get install libsdl1.2-dev

Cheers :-D

---

### Post by montgoss on 2007-03-08
Just an FYI.

I had some trouble compiling ffmpeg.  There were several libraries missing.  I believe the ones I had to install were ogg, vorbis, dts, dc1394, and x264.  If there was an apt-get in there that I missed, my bad.  Otherwise, it might be good to add that to make sure anyone more noobish than me won't have a problem.

My second problem compiling ffmpeg were some "permission denied" errors when I tried to do ./configure and make.  I had to run those two with sudo.  I'm not sure why.  Perhaps "apt-get source" made the files downloaded owned by root?

But other than that, the guide was great.  I got the latest episode of House on my iPod!  	=D>   
The next step is getting MythTV to automatically transcode shows for the iPod.  :popcorn:

---

### Post by FakeOutdoorsman on 2007-03-08
> I had some trouble compiling ffmpeg. There were several libraries missing. I believe the ones I had to install were ogg, vorbis, dts, dc1394, and x264. If there was an apt-get in there that I missed, my bad. Otherwise, it might be good to add that to make sure anyone more noobish than me won't have a problem.

The latest ffmpeg SVN configure options have changed for some libraries.  For example you might have used this:

```
./configure --enable-gpl --enable-pp --enable-vorbis --enable-ogg --enable-dc1394 --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-pthreads --enable-x264
```

The latest SVN won't work with the above code, but it would work with:
```
./configure --enable-gpl --enable-pp --enable-libvorbis --enable-libogg --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-xvid --enable-pthreads --enable-x264
```

Sometimes you need to make sure that the dev versions of some libraries are installed as well.  If you have liblame0, then ffmpeg might not install unless you also install liblame-dev.

---

### Post by endersshadow on 2007-03-08
> **montgoss said:**
> My second problem compiling ffmpeg were some "permission denied" errors when I tried to do ./configure and make.  I had to run those two with sudo.  I'm not sure why.  Perhaps "apt-get source" made the files downloaded owned by root?

This is exactly the problem.  apt-get source does not need to be run as sudo.  If it is, all files are owned by root.

Glad to hear you got it working, though :-D

---

### Post by invids on 2007-03-09
how exactly do you link link libgpod.so from /usr/local/bin to /usr/lib ?
I dont know the command to  type.

---

### Post by Nephiel on 2007-03-10
The command to create a symbolic link is "ln":
```
ln -s TARGET LINK_NAME
```

For example, to create a symbolic link to /usr/local/lib/libgpod.so in /usr/lib/ :
```
ln -s /usr/local/lib/libgpod.so /usr/lib/libgpod.so
```
You may need to be root to create files in /usr/lib, so use "sudo" before the ln command if you need it.

For more info about the "ln" command:
```
man ln
```

---

### Post by montgoss on 2007-03-11
I can't get Vive to build.  I can't even get past the ./configure step.  It says:```
configure: error: libdvdread development files are not install but are required to compile.
```
But ```
sudo apt-get install libdvdread-dev libdvdread3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread-dev is already the newest version.
libdvdread3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

So, I don't understand why it's giving me that error.  I saw some option to compile without DVD support.  I did that the first time.  But now I'd like to rip some DVDs and Acidrip is producing audio sync issue.  Maybe Vive will have better luck, if I can get it to build...   Any ideas?

---

### Post by endersshadow on 2007-03-11
montgross, what do you get when you try this command:

```
locate dvdread
```

---

### Post by montgoss on 2007-03-12
> **endersshadow said:**
> montgross, what do you get when you try this command:

```
locate dvdread
```

I get:
```
locate dvdread
/var/lib/dpkg/info/libdvdread3.shlibs
/var/lib/dpkg/info/libdvdread3.list
/var/lib/dpkg/info/libdvdread3.postinst
/var/lib/dpkg/info/libdvdread3.postrm
/var/lib/dpkg/info/libdvdread3.md5sums
/var/lib/dpkg/info/libdvdread-dev.md5sums
/var/lib/dpkg/info/libdvdread-dev.list
/home/montgoss/myth_svn/mythtv/libs/libmythdvdnav/.svn/text-base/dvdread_internal.h.svn-base
/home/montgoss/myth_svn/mythtv/libs/libmythdvdnav/.svn/prop-base/dvdread_internal.h.svn-base
/home/montgoss/myth_svn/mythtv/libs/libmythdvdnav/.svn/props/dvdread_internal.h.svn-work
/home/montgoss/myth_svn/mythtv/libs/libmythdvdnav/.svn/wcprops/dvdread_internal.h.svn-work
/home/montgoss/myth_svn/mythtv/libs/libmythdvdnav/dvdread_internal.h
/home/montgoss/montgoss-MythTV/mythtv-0.20/libs/libmythdvdnav/dvdread_internal.h
/home/moko/openembedded/packages/libdvdread
/home/moko/openembedded/packages/libdvdread/libdvdread_0.9.6.bb
/usr/include/dvdread
/usr/include/dvdread/dvd_reader.h
/usr/include/dvdread/ifo_types.h
/usr/include/dvdread/ifo_read.h
/usr/include/dvdread/ifo_print.h
/usr/include/dvdread/nav_types.h
/usr/include/dvdread/nav_read.h
/usr/include/dvdread/nav_print.h
/usr/include/dvdread/cmd_print.h
/usr/lib/gstreamer-0.10/libgstdvdread.so
/usr/lib/vlc/access/libdvdread_plugin.so
/usr/lib/libdvdread.so.3.2.0
/usr/lib/libdvdread.so.3
/usr/lib/libdvdread.a
/usr/lib/libdvdread.la
/usr/lib/libdvdread.so
/usr/lib/gstreamer-0.8/libgstdvdreadsrc.so
/usr/share/doc/libdvdread3
/usr/share/doc/libdvdread3/changelog.Debian.gz
/usr/share/doc/libdvdread3/install-css.sh
/usr/share/doc/libdvdread3/changelog.gz
/usr/share/doc/libdvdread3/TODO
/usr/share/doc/libdvdread3/README.Debian
/usr/share/doc/libdvdread3/copyright
/usr/share/doc/libdvdread-dev
/usr/share/doc/libdvdread-dev/changelog.Debian.gz
/usr/share/doc/libdvdread-dev/changelog.gz
/usr/share/doc/libdvdread-dev/copyright
```

---

### Post by endersshadow on 2007-03-12
Try this:

```
./configure --PREFIX=/usr
```

---

### Post by montgoss on 2007-03-12
```
$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ffmpeg... yes
checking for vobcopy... yes
checking for mplayer... yes
checking whether DVD is enabled... yes
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... yes (version 2.10.6)
checking for vte_terminal_new in -lvte... yes
checking for dvdcss_open in -ldvdcss... yes
checking for DVDOpen in -ldvdread... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking gtk/gtk.h usability... yes
checking gtk/gtk.h presence... yes
checking for gtk/gtk.h... yes
checking vte/vte.h usability... yes
checking vte/vte.h presence... yes
checking for vte/vte.h... yes
checking dvdcss/dvdcss.h usability... yes
checking dvdcss/dvdcss.h presence... yes
checking for dvdcss/dvdcss.h... yes
checking dvdnav/ifo_read.h usability... no
checking dvdnav/ifo_read.h presence... no
checking for dvdnav/ifo_read.h... no
configure: error: libdvdread development files are not install but are required to compile.
```

---

### Post by endersshadow on 2007-03-12
My fault. Try:

```
sudo apt-get install libdvdnav-dev libdvdnav4
```

---

### Post by montgoss on 2007-03-13
Ok, so I got it to build.  But it just segfaults when I click encode (after choosing all my settings).  It also won't save my preferences.  I'm not sure if that could be related.

Ya know, I don't really need a GUI.  What's the syntax to get ffmpeg to read straight from a DVD?

---

### Post by endersshadow on 2007-03-13
Well that's interesting.

And ffmpeg can't read from DVD's, so you need to use vobcopy or mencoder.

Let me know what settings you were using and I'll give you the exact commands.

---

### Post by montgoss on 2007-03-13
Can mencoder rip to mpeg-4?  I used Acidrip to rip to mpeg-2, but it screws up the audio sync on this particular TV series.  If I ripped to an avi, it works.  But it takes so much longer and doesn't look as good.

The ffmpeg command I used to get a decent video off DVD is:
> ffmpeg -i VTS_05_1.VOB -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 480x270 -aspect 16:9 /home/montgoss/Desktop/iPod_Videos/Carnivale-S2E03-Ingram,_TX_part1.m4v
This command produces a beautiful little video.

The problem is that VTS_05_1.vob isn't the full title off the DVD.  Some of the vobs aren't even broken down in logical points.  Like, VTS_05_1.vob is the first 26 minutes of an episode.  Then VTS_05_2.vob is the last 25 minutes of the episode plus the first 2 minutes of the next episode.  Mencoder understands this, but gets the audio sync wrong.

I think I tried vobcopy.  But all it seemed to do was rip a vob off the DVD.  Will it actually rip a title off?  Like the straight mpeg-2?  Cause that's what I need.

---

### Post by Inbo on 2007-03-17
I've tried doing what FernandoMilton suggested to get rid of the 'ERROR: x264 not found' but it's still not working:

```
mik@mik-desktop:~/Desktop/ffmpeg-0.cvs20060823$ ./configure --enable-gpl --enable-pp --enable-vorbis --enable-pthreads \
> --enable-libogg --enable-a52 --enable-dts \
> --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
> --enable-faad --enable-faac --enable-xvid --enable-x264
ERROR: x264 not found
If you think configure made a mistake, make sure you are using the latest
version from SVN.  If the latest version fails, report the problem to the
ffmpeg-devel@mplayerhq.hu mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.err" produced by configure as this will help
solving the problem.
mik@mik-desktop:~/Desktop/ffmpeg-0.cvs20060823$ 

```

---

### Post by CarsomyrXIII on 2007-03-17
I've been having the following error in building mpeg4ip and was wondering if anyone here would be able to help.

```
ffmpeg.cpp: In function 'int ffmpeg_decode(codec_data_t*, frame_timestamp_t*, int, int*, uint8_t*, uint32_t, void*)':
ffmpeg.cpp:229: error: 'avcodec_decode_audio2' was not declared in this scope
make[5]: *** [ffmpeg.lo] Error 1

```

I tried the other fix that involves ffmpeg.cpp but it doesn't help [slightly different error].

---

### Post by endersshadow on 2007-03-17
What'd your configure look like?

---

### Post by FakeOutdoorsman on 2007-03-17
Inbo,

Did you look though config.err?  IT has additional info that may tell you what is wrong, especially at the end of that file.  This is going to sound obvious, but do you have x264 installed?

---

### Post by CarsomyrXIII on 2007-03-18
Tail end of ./bootstrap:
```

Mp4live encoder report:
    ffmpeg encoder is installed
    xvid encoder is installed
    x264 encoder is installed
    lame encoder is installed
    faac encoder is installed
*** twolame encoder is not installed


```
Tail end of ./configure:
```
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating mpeg4-2000.h
config.status: mpeg4-2000.h is unchanged
config.status: executing depfiles commands

```

---

### Post by jangeles on 2007-03-24
I've just registered with the ubuntu forums solely to say a BIG thank you to the writer of the main post and also the people that helped out by posting how they fixed various issues they had.

Viva la iPod video on linux! :-)))))))))

---

### Post by CAN-CAN on 2007-03-26
I followed the instructions in the [[COLOR="Blue"]_wiki_[/COLOR]]("https://help.ubuntu.com/community/iPodVideo") and I cannot make encoding to work..

I tried both scripts and I get errors in both..
1st Script (pypodconv) ouput..
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame 
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Mar 17 2007 23:24:34, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
Input #0, avi, from 'Death_Wish.avi':
  Duration: 01:29:36.4, start: 0.000000, bitrate: 1091 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 672x384, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 112 kb/s
Warning: not compiled with thread support, using thread emulation
Output #0, mp4, to '/dev/null':
  Stream #0.0: Video: 0x0000, yuv420p, 320x182, q=2-51, pass 1, 760 kb/s, 25.00 fps(c)
Stream mapping:
  Stream #0.0 -> #0.0
Unsupported codec for output stream #0.0
Encode step FAILED:  ffmpeg -y -i "Death_Wish.avi" -f mp4 -pass 1 -threads 1 -an -v 1 -vcodec h264 -b 760 -bt 175 -refs 2 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -partb8x8 1 -subq 6 -brdo 1 -me_range 21 -chroma 1 -max_b_frames 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -max_qdiff 4 -i_quant_factor 0.71428572 -b_quant_factor 0.76923078 -rc_max_rate 1500 -rc_buffer_size 244 -cmp 1 -s 320x182  -map 0.0  /dev/null
```

2nd Script (ipodvidenc) output:
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame 
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Mar 17 2007 23:24:34, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
Input #0, avi, from 'Death_Wish.avi':
  Duration: 01:29:36.4, start: 0.000000, bitrate: 1091 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 672x384, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 112 kb/s
Unknown codec 'aac'
```

Can anyone help me with at least one of the Scripts.
My distribution is Ubuntu Edgy.

---

### Post by FakeOutdoorsman on 2007-03-26
CAN-CAN,

I'm not sure of what version of ffmpeg you're using since your configuration shows SVN-rUNKNOWN.  Looks like you're trying to encode a h264 video with aac audio, but you don't have these libraries enabled in your ffmpeg install: specifically --enable-x264 --enable-faac.  Try removing ffmpeg and reinstalling it with the directions on the wiki [iPod Video Encoding]("https://help.ubuntu.com/community/iPodVideoEncoding") page under the "Fixing ffmpeg on Ubuntu" secion.

---

### Post by CAN-CAN on 2007-03-27
I tried to reinstall ffmpeg through the the wiki ut in the **make** step I get this output..

```
/home/can-can/ffmpeg-0.cvs20060823/version.sh "/home/can-can/ffmpeg-0.cvs20060823"
make -C libavutil   all
make[1]: Entering directory `/home/can-can/ffmpeg-0.cvs20060823/libavutil'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/can-can/ffmpeg-0.cvs20060823/libavutil'
make -C libavcodec  all
make[1]: Entering directory `/home/can-can/ffmpeg-0.cvs20060823/libavcodec'
gcc -DHAVE_AV_CONFIG_H -I.. -I/home/can-can/ffmpeg-0.cvs20060823/libavutil -O3  -pthread -Wdeclaration-after-statement -Wall -Wno-switch -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE    -c -o x264.o x264.c
x264.c: In function &#8216;X264_init&#8217;:
x264.c:147: error: &#8216;struct <anonymous>&#8217; has no member named &#8216;i_rf_constant&#8217;
make[1]: *** [x264.o] Error 1
make[1]: Leaving directory `/home/can-can/ffmpeg-0.cvs20060823/libavcodec'
make: *** [lib] Error 2
```

Anyone can help..?

---

### Post by FakeOutdoorsman on 2007-03-27
> **CAN-CAN said:**
> x264.c:147: error: &#8216;struct <anonymous>&#8217; has no member named &#8216;i_rf_constant&#8217;

Did you make sure you ran *sudo apt-get install libx264-dev* before you tried to install ffmpeg?

Do you have a 64 bit CPU?  You can try *uname -a* in terminal to find out.  The output will show x86_64 or something like that.  If so, make sure to follow the 64 bit section in the wiki page you mentioned earlier.

---

### Post by CAN-CAN on 2007-03-27
Yes I am sure..
I have an AMD64 CPU but I don't have a 64-bit kernel of Ubuntu.
This the output of *uname -a*:
```
Linux Marianta 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux
```

---

### Post by CAN-CAN on 2007-03-27
Yes I am sure..
I have an AMD64 CPU but I don't have a 64-bit kernel of Ubuntu.
This the output of *uname -a*:
```
Linux M****** 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux
```

---

### Post by FakeOutdoorsman on 2007-03-27
Go ahead and try the 64 bit instrucitons anyway and see if that helps.

---

### Post by CAN-CAN on 2007-03-27
I've already tried and it didn't work..

---

### Post by juanhunglow on 2007-03-27
Feisty success.. mostly

Following the [_wiki _]("https://help.ubuntu.com/community/iPodVideoEncoding")I was able to get thinliquidfilm to convert a video that works on my 5G ipod.  I had to download the SVN of ffmpeg (per the ffmpeg webpage), then followed the remainder of the instructions to get the proper things enabled in ffmpeg.

Neither script 1 nor script 2 worked for me.  

Also, I had been using tovid to covert .avi's but now for some reason the sound does not want to encode properly, however the video is fine.  Guessing I borked something in ffmpeg to cause that problem.

Well done and please keep up the great work.

---

### Post by FakeOutdoorsman on 2007-03-27
Neither of the scripts are configured to work with the SVN of ffmpeg.  The SVN is a tricky beast to work with because the install and encoding options will often change between revisions meaning lots of google searches and reading of the sometimes sparse *man ffmpeg*.  For example, my SVN configuration uses --enable-libmp3lame  instead of --enable-mp3lame and the SVN encoding uses bits/s instead of kilobits such as -b 500k vs -b 500.

---

### Post by juanhunglow on 2007-03-27
> **FakeOutdoorsman said:**
> Neither of the scripts are configured to work with the SVN of ffmpeg.  The SVN is a tricky beast to work with because the install and encoding options will often change between revisions meaning lots of google searches and reading of the sometimes sparse *man ffmpeg*.  For example, my SVN configuration uses --enable-libmp3lame  instead of --enable-mp3lame and the SVN encoding uses bits/s instead of kilobits such as -b 500k vs -b 500.

Yes, the first thing I noticed what that "lib..." was required for several of the entries.  Good thing the Feisty sandbox is just for play right now.  I'll wait for the updated wiki after feisty gets released.

---

### Post by CAN-CAN on 2007-03-27
No one has a solution for my problem?:(

---

### Post by nandasunu on 2007-03-27
First off, thanks so much for the guide, it really helped a lot.

I don't know if this was asked before or not (I don't have time to read though the 45 pages of replies on this thread), but the videos that are converted through your (great :) ) script can't be resumed properly on the ipod and you can skip through the video either, which is pretty essential for me on longer vids. I noticed that this seems to happen on all the .mov videos on the ipod, but not on the .mp4 or .m4v files. How can I modify this script to give this format?

---

### Post by endersshadow on 2007-03-27
Can-Can, you may want to [report a ffmpeg bug](http://ffmpeg.mplayerhq.hu/bugreports.html).  It seems that it is a problem with their code.

nandasunu, you need a little program called MP4Box, which is in the gpac package.

```
sudo apt-get install gpac
MP4Box -add /path/to/movie.mov /path/to/movie.mov
```

This will overwrite itself with a working video.

To everybody, I'm sorry that I didn't get right back to you all.  My computer died this past week, and it's been quite the traumatic experience :-P

---

### Post by NorthernLights on 2007-04-03
> **c.dric said:**
> ps : i've downloaded the SIVE program but i'm having problems compiling the mpeg4ip program required.

Hi ! Sorry for answering late, but since several versions SIVE can work with MP4Box instead of mpeg4ip, which, as said just above, is in the Ubuntu repositories in the GPAC package.

See you !

PS : FYI, i'm the author of SIVE. Sorry for I don't come here often. BTW, you can always come talk on the forums of SIVE : [http://sive.sourceforge.net](http://sive.sourceforge.net).
Also, i'm in need of testers, so if anyone feels like helping, that would be great. There's one tester now, he's doing good job but is quite busy.

---

### Post by endersshadow on 2007-04-03
> **NorthernLights said:**
> Hi ! Sorry for answering late, but since several versions SIVE can work with MP4Box instead of mpeg4ip, which, as said just above, is in the Ubuntu repositories in the GPAC package.

See you !

PS : FYI, i'm the author of SIVE. Sorry for I don't come here often. BTW, you can always come talk on the forums of SIVE : [http://sive.sourceforge.net](http://sive.sourceforge.net).
Also, i'm in need of testers, so if anyone feels like helping, that would be great. There's one tester now, he's doing good job but is quite busy.

mpeg4ip is needed to move files to the ipod using gtkpod, not for encoding video.

Cheers.

---

### Post by NorthernLights on 2007-04-06
I saw someone said he tried sive but could not get mpeg4ip to work, so i answered him that mpeg4ip was not needed anymore. That's the problem of answering late, you guys were already talking about something else when i answered. :)

---

### Post by aiserv on 2007-04-15
Have a trouble with installing VIVE... have any ideas?
```
checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: GTK is not version >= 2.0.0.  Please update GTK.
```

---

### Post by endersshadow on 2007-04-15
aiserv:

```
sudo apt-get install libgtk2.0-dev
```

---

### Post by endersshadow on 2007-04-20
Updated the HOWTO big time.  Including much easier ways to install gtkpod, the updated ffmpeg info for Edgy/Feisty, and installation instructions for Vive.  Also updated the MP4Box info to make that easier, too.

No more mpeg4ip! Woohoo!

---

### Post by ngardner on 2007-04-28
> **CAN-CAN said:**
> I tried to reinstall ffmpeg through the the wiki ut in the **make** step I get this output..

```
/home/can-can/ffmpeg-0.cvs20060823/version.sh "/home/can-can/ffmpeg-0.cvs20060823"
make -C libavutil   all
make[1]: Entering directory `/home/can-can/ffmpeg-0.cvs20060823/libavutil'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/can-can/ffmpeg-0.cvs20060823/libavutil'
make -C libavcodec  all
make[1]: Entering directory `/home/can-can/ffmpeg-0.cvs20060823/libavcodec'
gcc -DHAVE_AV_CONFIG_H -I.. -I/home/can-can/ffmpeg-0.cvs20060823/libavutil -O3  -pthread -Wdeclaration-after-statement -Wall -Wno-switch -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_ISOC9X_SOURCE    -c -o x264.o x264.c
x264.c: In function ‘X264_init’:
x264.c:147: error: ‘struct <anonymous>’ has no member named ‘i_rf_constant’
make[1]: *** [x264.o] Error 1
make[1]: Leaving directory `/home/can-can/ffmpeg-0.cvs20060823/libavcodec'
make: *** [lib] Error 2
```

Anyone can help..?


After alot of head banging, I resolved the issue.
you need to open /libavcodec/x264.c and goto line 147.   Change i_rf_constant to f_rf_constant
Apparently it changed from int to float, and was missed there.

---

### Post by diom on 2007-04-28
> **endersshadow said:**
> aiserv:

```
sudo apt-get install libgtk2.0-dev
```

Hi endersshadow.

Listen I have the exact same problem with GTK. I have tried to reinstall it but to no avail...it just says that I already have the most up-to-date version. I have confimed it in Synaptic and by going to the /usr/lib/ directory. I also had trouble when I tried to install "libdvdcss2-dev"...couldn't find that.
Anyways have you any recommendations/suggestions for me. Stuck on this for the last 2 hours.

Thanks.

---

### Post by endersshadow on 2007-04-28
Hey diom,

Can you post your /etc/apt/sources.list as well as the output from ./configure?

Thanks!

---

### Post by diom on 2007-04-29
> **endersshadow said:**
> Hey diom,

Can you post your /etc/apt/sources.list as well as the output from ./configure?

Thanks!

Hi,
Actually now it is saying that I do have GTK...but, well you'll see.

**./configure output**
```

praetorian@Empire:~/Desktop/vive-2.0.0-beta1$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ffmpeg... yes
checking for vobcopy... yes
checking for mplayer... yes
checking whether DVD is enabled... yes
checking for pkg-config... /usr/bin/pkg-config
[b]checking for GTK+ - version >= 2.0.0... yes (version 2.10.11)
checking for vte_terminal_new in -lvte... no
configure: error: libvte is not installed.[/b]

```


**/etc/apt/sources.list**
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ie.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ie.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ie.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://ie.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ie.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ie.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://ie.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```

As I said before I had trouble trying to get libdvdcss2-dev installed (couldn't find it). 
Thanks again.
D

---

### Post by endersshadow on 2007-04-29
diom, add the following line to your sources.list:

```
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
```

Then do this:

```
sudo apt-get update
sudo apt-get install libvte-dev libdvdcss2-dev libdvdnav-dev libdvdread-dev
```

Then try the configure again.

---

### Post by Sammi on 2007-04-29
I keep getting a core dump:
```
Segmentation fault (core dumped)
```
I don't see more info than that in the terminal. How do I troubleshoot?

---

### Post by endersshadow on 2007-04-29
Sammi,

Is this beta1 or an SVN checkout?  Also, what are you doing when it segfaults?

---

### Post by Sammi on 2007-04-29
beta1

I'm just pressing the encode button 

Don't know if I've been fiddling too much with installing ffmpeg... It may be screwed up or something. Oh and I'm using Feisty.

EDIT: Trying to install svn gives this error while compiling:
encode.c
encode.c: In function &#8216;encode_vid_new&#8217;:
encode.c:599: error: void value not ignored as it ought to be
make[2]: *** [encode.o] Error 1
make[2]: Leaving directory `/home/<user>/programs/vive/2.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/<user>/programs/vive/2.0.0'
make: *** [all] Error 2

---

### Post by endersshadow on 2007-04-29
Well, that error was a boneheaded mistake on my part.  I had a comparison in there for debug purposes and only deleted half of it...try the checkout again.

Apologies :)

(BTW, you get to see the latest and greatest feature...multiple file input and selecting a folder to recursively select all of the videos and encoded them.  Cool, eh?)

---

### Post by Sammi on 2007-04-29
Ok great :D I'm fairly sure I've got the newest svn of both vive and ffmpeg installed now.

Vive does look different. There seem to be more features like you describe.

Sadly it still dumps it core when I press encode, but this time it gives a fair amount more info:
```
$ vive
*** glibc detected *** vive: malloc(): memory corruption: 0x085da6c0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb74e8ef3]
/lib/tls/i686/cmov/libc.so.6[0xb74e990c]
/lib/tls/i686/cmov/libc.so.6(__libc_memalign+0xb1)[0xb74ea7c1]
/lib/tls/i686/cmov/libc.so.6(posix_memalign+0x88)[0xb74ea958]
/usr/lib/libglib-2.0.so.0[0xb78aa694]
/usr/lib/libglib-2.0.so.0(g_slice_alloc+0x364)[0xb78ab0c4]
/usr/lib/libvte.so.9[0xb76d9905]
/usr/lib/libvte.so.9[0xb76e865d]
vive[0x8054475]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb791a9d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb790d62b]
/usr/lib/libgobject-2.0.so.0[0xb791e103]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb791f627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb791f7e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_button_clicked+0x53)[0xb7c9a163]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c9bdae]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb791a9d9]
/usr/lib/libgobject-2.0.so.0[0xb790be49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb790d62b]
/usr/lib/libgobject-2.0.so.0[0xb791e59a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb791f627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb791f7e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_button_released+0x53)[0xb7c9a1f3]
/usr/lib/libgtk-x11-2.0.so.0[0xb7c9a251]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x60)[0xb7d6a6b0]
/usr/lib/libgobject-2.0.so.0[0xb790be49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb790d62b]
/usr/lib/libgobject-2.0.so.0[0xb791e753]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb791f3ef]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb791f7e9]
/usr/lib/libgtk-x11-2.0.so.0[0xb7e7ee18]
/usr/lib/libgtk-x11-2.0.so.0(gtk_propagate_event+0x183)[0xb7d639c3]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x317)[0xb7d64bc7]
/usr/lib/libgdk-x11-2.0.so.0[0xb7be612a]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7893df2]
/usr/lib/libglib-2.0.so.0[0xb7896dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7897179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7d65044]
vive[0x8056097]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7496ebc]
vive[0x804b211]
======= Memory map: ========
08048000-08058000 r-xp 00000000 08:02 476114     /usr/bin/vive
08058000-08059000 rw-p 0000f000 08:02 476114     /usr/bin/vive
08059000-085ef000 rw-p 08059000 00:00 0          [heap]
b044c000-b044d000 ---p b044c000 00:00 0 
b044d000-b0c4d000 rwxp b044d000 00:00 0 
b0c4d000-b0cc3000 r--p 00000000 08:02 573989     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b0cc3000-b0cc4000 ---p b0cc3000 00:00 0 
b0cc4000-b14c4000 rwxp b0cc4000 00:00 0 
b14c4000-b14c5000 ---p b14c4000 00:00 0 
b14c5000-b1cc5000 rwxp b14c5000 00:00 0 
b1cc5000-b1d25000 rw-s 00000000 00:08 6062104    /SYSV00000000 (deleted)
b1d25000-b1d4c000 rw-p b1d25000 00:00 0 
b1d4c000-b2039000 r--p 00000000 08:02 704540     /usr/share/fonts/truetype/baekmuk/dotum.ttf
b2039000-b206a000 rw-p b2039000 00:00 0 
b206a000-b27d4000 r--p 00000000 08:02 704544     /usr/share/fonts/truetype/kochi/kochi-gothic-subst.ttf
b27d4000-b27f6000 r--p 00000000 08:02 639312     /usr/share/fonts/type1/gsfonts/n022003l.pfb
b27f6000-b2832000 r--p 00000000 08:02 2375768    /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf
b2832000-b287c000 r--p 00000000 08:02 2375738    /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf
b287c000-b2896000 r--p 00000000 08:02 2375757    /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf
b28a3000-b28df000 r--p 00000000 08:02 573998     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono-Bold.ttf
b28df000-b291e000 r--p 00000000 08:02 574001     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b291e000-b291f000 ---p b291e000 00:00 0 
b291f000-b311f000 rwxp b291f000 00:00 0 
b311f000-b3120000 r--p 00000000 08:02 786797     /usr/share/vte/termcap/xterm
b3120000-b3122000 r--p 00000000 08:02 558228     /usr/share/locale-langpack/en_GB/LC_MESSAGES/atk10.mo
b3122000-b334a000 r--p 00000000 08:02 1150900    /usr/share/icons/hicolor/icon-theme.cache
b334a000-b4434000 r--p 00000000 08:02 1097774    /usr/share/icons/crystalsvg/icon-theme.cache
b443400Aborted (core dumped)
```

---

### Post by endersshadow on 2007-04-29
What options were you using, per chance?  I'll try to replicate it here.  I have to run to a meeting right now, so I won't be immediately responsive, but I definitely want to get to the root of this.

---

### Post by Sammi on 2007-04-29
Nv I wasn't even able to replicate it myself. Now I'm getting this:
```
$ ffmpeg -y -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -bufsize 4096 -pass 1 -aspect 4:3 -s 320x240 -acodec aac -ab 128 -ar 44100 -comment "Encoded by Vive"  -i /home/<user>/Desktop/file.avi /home/<user>/Desktop/file.mp4
FFmpeg version SVN-r8857, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-pp --enable-pthreads --enable-dc1394 --enable-liba52 --enable-libfaac --enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libogg --enable-libtheora --enable-libvorbis --enable-x264 --enable-xvid --enable-shared --disable-debug
  libavutil version: 49.4.0
  libavcodec version: 51.40.4
  libavformat version: 51.12.1
  built on Apr 29 2007 18:25:02, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Input #0, avi, from '/home/<user>/Desktop/file.avi':
  Duration: 00:22:29.1, start: 0.000000, bitrate: 1473 kb/s
  Stream #0.0: Video: msmpeg4v2, yuv420p, 480x360, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 44100 Hz, stereo, 320 kb/s
Output #0, mp4, to '/home/<user>/Desktop/file.mp4':
  Stream #0.0: Video: mpeg4, yuv420p, 480x360, q=2-31, pass 1, 0 kb/s, 23.98 fps(c)
  Stream #0.1: Audio: aac, 44100 Hz, stereo, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0xb7e03cc8]removing common factors from framerate
[mpeg4 @ 0xb7e03cc8]timebase not supported by mpeg 4 standard
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```I really know almost nothing about ffmpeg and codec parameters, so this doesn't tell me much. Feels like I'm stuck in error hell. Getting flash-backs to Red Hat RPM dependancy hell :D

EDIT: I can see that I must be using the newest ffmpeg svn as the error says "built on Apr 29 2007 18:25:02, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)", which in my time-zone was just about forty minutes ago. The exact time when I compiled it.

---

### Post by endersshadow on 2007-04-29
Well, you're getting that error because ffmpeg changed how it uses bit rates.  Instead of being in kb/s (previous way), they changed to bits/s...this just became the case in the Feisty build of ffmpeg.  Take away the -maxrate, -b, and -bufsize flags and values and then see what happens.  It's a pain in the neck, but I gotta change it.  The real question is just determining which one to use for a user's ffmpeg installation (for the time being).

Email me at endersshadow AT users DOT sourceforge DOT net, and I'll roll you a debugging distribution of the code to narrow this problem down if you feel like keeping on trying.  If not, I understand :)

---

### Post by kaitwospirit on 2007-04-29
I'm still learning all this tech stuff, so please help me.

When I'm trying to install vive from the SVN, when I run ./configure I get this error:

"checking for libgnomevfs... configure: error: Package requirements (gnome-vfs-2.0 >= 2.0) were not met:

No package 'gnome-vfs-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables libgnomevfs_CFLAGS
and libgnomevfs_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details."

What does this mean I need to do?

---

### Post by endersshadow on 2007-04-29
kaitwospirit:
```
sudo apt-get install libgnomevfs2-dev
```

FYI, you will also need to do the following for later in the configure:

```
sudo apt-get install libvte-dev libdvdcss2-dev libdvdread-dev libdvdnav-dev
```

---

### Post by diom on 2007-04-30
> **endersshadow said:**
> diom, add the following line to your sources.list:

```
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
```

Then do this:

```
sudo apt-get update
sudo apt-get install libvte-dev libdvdcss2-dev libdvdnav-dev libdvdread-dev
```

Then try the configure again.

Thanks endersshadow...that seems to have gotten it to work for me. I've only managed to find time to encode one avi to mp4 but if anything else crops up I'll let all y'all know. 

Thanks a million once again.
D

---

### Post by offchance on 2007-05-04
this is a really great project and I really like al lthe time and effort being put into it. 

I've been working on this throughout the day and have encountered two problems:

1. vive is installed, has the ipod presets, but abruptly quits whenever I hit the encode button. 

2. I get the following with ipodvidenc, even after installing faac:

```
damion@dmachine:/media/sdb1/video/Harvey Birdman 2-4/Harvey Birdman - Season 04$ ipodvidenc Harvey\ Birdman\ -\ S4E01\ -\ Mufti\ Trouble.avi
What would you like to name the output file (sans extension)?
mufti
mufti will be located in /media/sdb1/video/Harvey Birdman 2-4/Harvey Birdman - Season 04. Is this acceptable? [y/n]
y
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --prefix=/usr 
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on May  4 2007 16:33:56, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Input #0, avi, from 'Harvey Birdman - S4E01 - Mufti Trouble.avi':
  Duration: 00:12:05.5, start: 0.000000, bitrate: 1472 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 640x480, 29.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Unknown codec 'aac'
damion@dmachine:/media/sdb1/video/Harvey Birdman 2-4/Harvey Birdman - Season 04$ 

```

I really want this to work. using xp and having videora take up 99% of my processor and displaying annoying ads is not my cup of tea!

---

### Post by endersshadow on 2007-05-05
offchance,

Yoiu don't have ffmpeg compiled w/ AAC support.  Are you using the default install of ffmpeg from Ubuntu?

Also, as to the crashing, what version of Vive are you running?

Thanks!

---

### Post by offchance on 2007-05-05
I ran the code verbatim from your tutorial several times. is there something else I should look for?

I am running Vive 2.0.0-beta1, from the link provided in the tutorial.

thanks for you help!

**edit:

I recompiled ffmpeg per the svn instructions and everything looked ok.

I tried one video with ipodvidenc and got the same error msg as before. 

On another file I got the following, which may or may not have anything to do with what is set out in the tut:

[B]FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Jan 28 2007 22:48:38, gcc: 4.1.2 20070106 (prerelease) (Ubuntu 4.1.1-21ubuntu7)
Harvey Birdman - S4E01: I/O error occured
Usually that means that input file is truncated and/or corrupted.
[/B]

---

### Post by Pirate742 on 2007-05-06
> **endersshadow said:**
> offchance,

Yoiu don't have ffmpeg compiled w/ AAC support.  Are you using the default install of ffmpeg from Ubuntu?

Also, as to the crashing, what version of Vive are you running?

Thanks!


May i ask how is it possible to compile ffmpeg w/ aac support?
Thanks

---

### Post by gorilla_king on 2007-05-06
i didnt use any of this. i tried..but after having no success i decided it was easier just to do stuff command line with ffmpeg. anyway thats what i did

but i did have to fix my ffmpeg version
so heres the version i compiled in a deb if anyone wants it. it should fix the whole h264 thingy

its 7.6 megs so i cant upload it to the forums but i uploaded it to a free file host
[http://www.sharebigfile.com/file/162559/ffmpeg-3-0-cvs20060823-3-1ubuntu2-1-i386-deb.html](http://www.sharebigfile.com/file/162559/ffmpeg-3-0-cvs20060823-3-1ubuntu2-1-i386-deb.html)

sry if this link goes bad after a while but you have to download at least once a week to keep em alive

---

### Post by offchance on 2007-05-07
alright...ipodvidenc works now with gorilla_king's ffmpeg build. sweet!

I will continue to work on vive. any advice is appreciated!

---

### Post by endersshadow on 2007-05-07
Sorry for being so late on this...it was the little lady's birthday this weekend, so I was stolen away for that.  Now that I'm back and geeking it up again...

I remember now a bug that I've fixed in the SVN version of Vive (I gotta get my act together and finish off 2.0.0, but I keep finding little things wrong with it).  If all of the drop down menus aren't selected (aka format, video codec, number of passes, aspect ratio, and audio codec), you'll get a seg fault.  Make sure all of them are selected to some value and go from there.

Good luck!

---

### Post by FakeOutdoorsman on 2007-05-07
> **Pirate742 said:**
> May i ask how is it possible to compile ffmpeg w/ aac support?
Thanks

The options to enable aac support depends on the ffmpeg version you are compiling.  The Ubuntu wiki entry [iPodVideoEncoding]("https://help.ubuntu.com/community/iPodVideoEncoding") has a section under [Fixing ffmpeg on Ubuntu]("https://help.ubuntu.com/community/iPodVideoEncoding#head-718248d42e047c1bdeda6e7e26665b1103b6b00f") that will tell you how to do this.  If you have any questions, ask them here.

---

### Post by salvador24 on 2007-05-10
Thanks endersshadow, that adviced fixed problems I was having with seg fault.  Now encoding to mp4 as I write this!

---

### Post by endersshadow on 2007-05-10
Woot! Bug I already fixed!

Enjoy and happy encoding!  Glad it's working for you!

---

### Post by diom on 2007-05-13
Hello...

I have gotten Vive to work on my PSP for SP mp4 profiles, but I really want to get AVC working. I tried it in Vive and got the following:

```

praetorian@Empire:~$ ffmpeg -i "/media/EXTERNAL_/TV/Firefly/05_Safe.avi" -f psp -vcodec h264 -maxrate 1000 -b 700 -bufsize 4096 -pass 2 -aspect 4:3 -s 320x240 -qmin 5 -qmax 6 -acodec aac -ab 192 -ar 44100 "/home/praetorian/a.mp4"
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 21 2007 14:14:05, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Input #0, avi, from '/media/EXTERNAL_/TV/Firefly/05_Safe.avi':
  Duration: 00:42:47.1, start: 0.000000, bitrate: 761 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 496x272, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 32 kb/s
File '/home/praetorian/a.mp4' already exists. Overwrite ? [y/N] y
Output #0, psp, to '/home/praetorian/a.mp4':
  Stream #0.0: Video: h264, yuv420p, 320x240, q=5-6, pass 2, 700 kb/s, 23.98 fps(c)
  Stream #0.1: Audio: aac, 44100 Hz, stereo, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[h264 @ 0xb7ed0f08]using SAR=1/1
[h264 @ 0xb7ed0f08]using cpu capabilities MMX MMXEXT SSE SSE2 
[b][h264 @ 0xb7ed0f08]ratecontrol_init: can't open stats file
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height[/b]

```

This is actually the problem recreated in terminal using the same command as in Vive, but I couldn't copy the output so I just re did it manually.
I was wondering if I am missing the referenced "stats file" or if I have incorrect parameters.
Any help is much appreciated.

Thanks! :confused:

---

### Post by endersshadow on 2007-05-13
Ah, this issue.  You see, the fine people at ffmpeg changed their bitrate from kb/s to b/s, putting things off by a value of 1024.  The problem is the ffmpeg in Ubuntu uses kb/s, and the SVN uses b/s...it's an issue I'm trying to figure out how to tackle.  Use 1024000 as your Max Bitrate and 716800 as your Bitrate, and life should be peachy.

---

### Post by endersshadow on 2007-05-14
I was wrong...it's a factor of 1000, not 1024.  At any rate, the latest SVN checkout of Vive provides for kb/s, no matter what version of ffmpeg you use.  Hooray standardization!

---

### Post by Donnie Darko on 2007-05-25
well, I've only been on ubuntu for about a month now, and while installing ffmpeg I got stuck. I did the code in the beginning
"sudo apt-get install liblame-dev libxvidcore4-dev libx264-dev libfaac-dev libfaad2-dev
sudo apt-get build-dep ffmpeg"

then Without x264:
"apt-get source ffmpeg
cd ffmpeg-*/
./configure --enable-gpl --enable-pp --enable-vorbis \
	--enable-libogg --enable-a52 --enable-dts \
	--enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame \
	--enable-faad --enable-faac --enable-xvid --enable-pthreads --enable-shared
make
sudo make install"

now in terminal it has this:
"andrew@andrew-desktop:~/ffmpeg-0.cvs20060823$ "
And I can't erase it or anything. 
What should I do, I'm running feisty fawn btw

---

### Post by endersshadow on 2007-05-26
Welcome to Linux, Andrew!

This is what's called the command line.  I'll break down what that shebangbang is:

```
andrew@andrew-desktop:~/ffmpeg-0.cvs20060823$
```

andrew: Your username (assumedly you're named Andrew)
@andrew-desktop: You are logged in at (@) the computer named "andrew-desktop"
:~/ffmpeg-0.cvs20060823: You are looking at (:) the folder ~/ffmpeg-0.cvs20060823 (~ is short for /home/andrew)

You type in commands from there, and the magic happens.  At any rate, if ffmpeg installed successfully, you can then install Vive or ipodvidenc or just use the ffmpeg command line.  For example, if you wanted to encode a wmv movie to an avi, in the command line, you would type:

```
ffmpeg -f avi -vcodec mpeg4 -acodec mp3 -i /path/to/movie.wmv /path/to/movie.avi
```

So that your command prompt would look like, before you hit enter:
```
andrew@andrew-desktop:~/ffmpeg-0.cvs20060823$ ffmpeg -f avi -vcodec mpeg4 -acodec mp3 -i /path/to/movie.wmv /path/to/movie.avi
```

Here's a good [command line reference guide](http://doc.gwos.org/index.php/CommandLineBeginners).  You don't need to memorize all of it, but scanning over it will give you a sense of what the terminal can do.

---

### Post by Donnie Darko on 2007-05-27
Thanks for the speedy reply and help endersshadow, its greatly appreciated. So, does it mean that ffmpeg is installed (or how can I tell)? I can't use my ubuntu machine till tomorrow, as I'm camping and right now I'm on a HP laptop with xp (bleh!) Thanks in advance.

---

### Post by endersshadow on 2007-05-27
> **Donnie Darko said:**
> Thanks for the speedy reply and help endersshadow, its greatly appreciated. So, does it mean that ffmpeg is installed (or how can I tell)? I can't use my ubuntu machine till tomorrow, as I'm camping and right now I'm on a HP laptop with xp (bleh!) Thanks in advance.

Assuming that you didn't get any error messages, then yes, yes it is installed.  It's important to check the last 15 or so lines of output from installs.  It generally contains very important information :)

---

### Post by Metallinut on 2007-05-31
Hey thanks for putting this How-To together.  It's great!  One quick problem (maybe) though, that maybe someone can help with.

I used to have ffmpeg installed, and had a script to do my iPod video converting, and all worked well.  The CLI of ffmpeg would have a nice output, showing what time index it was at, etc. that would allow me to figure out how long the conversion would (roughly) take.

I recently had to rebuild my Ubuntu box (totally unrelated), and am trying to get things back the way they were.  I couldn't find the original install method I had used, so I used the one you had in the first post (used the SVN method)

I'm encoding my first video file now, and the output is a little strange to me.  Instead of the "full-terminal-window" sized CLI interface, that updates on it's own, I'm getting thousands and thousands of scrolling messages that look like this:
```

[mpeg4 @ 0xb7d91488]rc buffer underflow9kB time=267.9 bitrate= 394.1kbits/s
[mpeg4 @ 0xb7d91488]rc buffer underflow
[mpeg4 @ 0xb7d91488]rc buffer underflow
[mpeg4 @ 0xb7d91488]rc buffer underflow
[mpeg4 @ 0xb7d91488]rc buffer underflow
[mpeg4 @ 0xb7d91488]rc buffer underflow0kB time=268.0 bitrate= 394.0kbits/s
[mpeg4 @ 0xb7d91488]rc buffer underflow
[mpeg4 @ 0xb7d91488]rc buffer underflow
[mpeg4 @ 0xb7d91488]rc buffer underflow
[mpeg4 @ 0xb7d91488]rc buffer underflow
[mpeg4 @ 0xb7d91488]rc buffer underflow2kB time=268.2 bitrate= 393.8kbits/s
[mpeg4 @ 0xb7d91488]rc buffer underflow

```

And so on.  So just about every 1-2 tenths of a second of video encoding, it's throwing up these lines in the terminal window.  Nonstop...

Any ideas?

Thanks

---

### Post by endersshadow on 2007-05-31
What ffmpeg command or options did you use?

---

### Post by bennyj on 2007-05-31
Could someone tell me why this is happening ? I have followed the instructions here to a T  but when i type ffmepg in the console i get this
```
 ffmpeg: error while loading shared libraries: libraw1394.so.5: cannot open shared object file: No such file or directory

```

---

### Post by endersshadow on 2007-05-31
bennyj: Try this:

```
sudo apt-get install libraw1394-dev
```

---

### Post by bennyj on 2007-05-31
> **endersshadow said:**
> bennyj: Try this:

```
sudo apt-get install libraw1394-dev
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libraw1394-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by endersshadow on 2007-06-01
Is libraw1394-8 installed?

---

### Post by bennyj on 2007-06-01
> **endersshadow said:**
> Is libraw1394-8 installed?

I just doubled checked..and yes it is.evrything else went pretty smooth except for this.
thank for your help and this how to

---

### Post by endersshadow on 2007-06-01
Found the problem...it's a backward compatibility bug in 7.04.

```
sudo ln -s /usr/lib/libraw1394.so.8.1.1 /usr/lib/libraw1394.so.5
```

For reference, did you use the with x264 instructions or the without x264 instructions?

---

### Post by bennyj on 2007-06-01
> **endersshadow said:**
> Found the problem...it's a backward compatibility bug in 7.04.

```
sudo ln -s /usr/lib/libraw1394.so.8.1.1 /usr/lib/libraw1394.so.5
```

For reference, did you use the with x264 instructions or the without x264 instructions?

That did it!thank you so much for the fast reply's.and yes i used it with x264

---

### Post by endersshadow on 2007-06-01
Awesome :)

I'll look into why this happens and perhaps throw in a little bug report if needed for our friends at Launchpad :)

---

### Post by Metallinut on 2007-06-01
> **endersshadow said:**
> What ffmpeg command or options did you use?

Sorry for the late reply.

I followed the instructions on page one of this thread (just the ffmpeg install instructions) using the "With x264" instructions (via SVN)

---

### Post by endersshadow on 2007-06-01
> **Metallinut said:**
> Sorry for the late reply.

I followed the instructions on page one of this thread (just the ffmpeg install instructions) using the "With x264" instructions (via SVN)

It's okay.  I meant what options did you use to encode said video that you got the buffer underflow with :)

---

### Post by Metallinut on 2007-06-01
I used essentially the same script you have in the intro, but this is what I used:

```

ffmpeg -i "${input_file}" -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 "${output_file_name}.mov"

```

---

### Post by endersshadow on 2007-06-01
Change that line to this:

```
ffmpeg -i "${input_file}" -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 "${output_file_name}.mov"
```

Those k's should make all the difference.

---

### Post by bennyj on 2007-06-02
I have a question.I noticed that in the tutorial posted that it says you can convert from .vob file straight from dvd::rip.When I rip the dvd with dvd::rip it breaks the dvd up into multilple files each about 1gb in size.How would i go about ripping it into one big file and then converting it?Or could the ipodvidenc do them all at the same time and put them together into one big file?If so how would I go about this using the ipodvidenc?

thanks

---

### Post by endersshadow on 2007-06-02
> **bennyj said:**
> I have a question.I noticed that in the tutorial posted that it says you can convert from .vob file straight from dvd::rip.When I rip the dvd with dvd::rip it breaks the dvd up into multilple files each about 1gb in size.How would i go about ripping it into one big file and then converting it?Or could the ipodvidenc do them all at the same time and put them together into one big file?If so how would I go about this using the ipodvidenc?

thanks

To the best of my knowledge, dvd::rip will always split those.  My suggestion is to use vobcopy (available via apt-get), and use this command:

```
vobcopy -l -n # -o /path/to/output/directory/
```

Here, the -l tells it to rip to 1 large file.  The # is the title number.

Sorry :-|

---

### Post by bennyj on 2007-06-02
> **endersshadow said:**
> To the best of my knowledge, dvd::rip will always split those.  My suggestion is to use vobcopy (available via apt-get), and use this command:

```
vobcopy -l -n # -o /path/to/output/directory/
```

Here, the -l tells it to rip to 1 large file.  The # is the title number.

Sorry :-|

Thanks endershadow you have been a great help!

---

### Post by endersshadow on 2007-06-02
> **bennyj said:**
> Thanks endershadow you have been a great help!

Glad you got it working.  I do what I can...happy encoding :-D

---

### Post by bennyj on 2007-06-03
This might be a bone head question but im a little confused. I have been using the ipodvidenc script with vobcopy and following this turorial and everything works fine.I can rip,encode and then upload to my ipod no problem.So I thought I would give the GUI version a try.Did the configure thing,make and make install.loaded the preference.Everything comes up as it should.

Now my question.Am I supposed to be able to rip from the dvd to vob using Vive gui?And then encode to ipod formatt all with the one click of the encode button?Or do I still need to rip to vob seperately using vobcopy and then encode using vive?

thanks

---

### Post by FXFman1209 on 2007-06-03
Alright. I've followed the instructions exactly and there were no problems. So, to try this for the first time, I start up Vive. I select my File to be a 40-minute episode of Psyche (avi), and set the output to "/home/fxfitz/test" (should there be an extension??) I set the preset to iPod/PSP Video and click encode, and then Vive just exits. I've never done anything like this before and it would be much appreciated if you could lend a hand and let me know what I'm doing wrong. Thanks!!

---

### Post by endersshadow on 2007-06-03
> **bennyj said:**
> This might be a bone head question but im a little confused. I have been using the ipodvidenc script with vobcopy and following this turorial and everything works fine.I can rip,encode and then upload to my ipod no problem.So I thought I would give the GUI version a try.Did the configure thing,make and make install.loaded the preference.Everything comes up as it should.

Now my question.Am I supposed to be able to rip from the dvd to vob using Vive gui?And then encode to ipod formatt all with the one click of the encode button?Or do I still need to rip to vob seperately using vobcopy and then encode using vive?

thanks

It does it all for you.  You can choose to keep the VOB but otherwise it will delete it for you.

[quote=FXFman1209]Alright. I've followed the instructions exactly and there were no problems. So, to try this for the first time, I start up Vive. I select my File to be a 40-minute episode of Psyche (avi), and set the output to "/home/fxfitz/test" (should there be an extension??) I set the preset to iPod/PSP Video and click encode, and then Vive just exits. I've never done anything like this before and it would be much appreciated if you could lend a hand and let me know what I'm doing wrong. Thanks!![/quote]

Yes, there should be an extension.  This was an issue with the Beta, but I believe it was fixed in the SVN version...I'll give it a whirl, though :)

---

### Post by bennyj on 2007-06-03
The reason i asked is becuase i keep getting"segmetation fault(core dumped). I used the presets under preference and made sure that every drop down box has a value and output points to my home directory but no luck.Any suggestions.I wish I could provide you with more but thats all the error code i get in the console.
Thanks

---

### Post by endersshadow on 2007-06-03
> **bennyj said:**
> The reason i asked is becuase i keep getting"segmetation fault(core dumped). I used the presets under preference and made sure that every drop down box has a value and output points to my home directory but no luck.Any suggestions.I wish I could provide you with more but thats all the error code i get in the console.
Thanks

Oh that lovely error.

Which version are you using, 2.0.0-beta1 or the SVN?  Also, what was the path to the input and output files?

Thanks!

---

### Post by bennyj on 2007-06-03
> **endersshadow said:**
> Oh that lovely error.

Which version are you using, 2.0.0-beta1 or the SVN?  Also, what was the path to the input and output files?

Thanks!

version 2.0.0-beta1 input path- /dev/hdd - output path = /home/benny/ipod movies

---

### Post by endersshadow on 2007-06-03
> **bennyj said:**
> version 2.0.0-beta1 input path- /dev/hdd - output path = /home/benny/ipod movies

The beta doesn't have full directory support.  Also, /dev/hdd isn't a directory, per se.  Make the input and outputs specific movie files.  You'll need extensions, as well (ffmpeg won't encode without extensions).

---

### Post by bennyj on 2007-06-03
would this help?```
 benny@benny-desktop:~$ whereis vobcopy
vobcopy: /usr/bin/vobcopy /usr/X11R6/bin/vobcopy /usr/bin/X11/vobcopy /usr/share/man/man1/vobcopy.1.gz
benny@benny-desktop:~$ whereis vive
vive: /usr/local/bin/vive
benny@benny-desktop:~$ 

```

just wondering if vive can reach vobcopy?

---

### Post by endersshadow on 2007-06-03
> **bennyj said:**
> would this help?```
 benny@benny-desktop:~$ whereis vobcopy
vobcopy: /usr/bin/vobcopy /usr/X11R6/bin/vobcopy /usr/bin/X11/vobcopy /usr/share/man/man1/vobcopy.1.gz
benny@benny-desktop:~$ whereis vive
vive: /usr/local/bin/vive
benny@benny-desktop:~$ 

```

just wondering if vive can reach vobcopy?

Shouldn't have a problem :)

---

### Post by FXFman1209 on 2007-06-04
Hang on, I'm also having the Segmentation Fault error... whats the problem? I'm sorry. :(

---

### Post by endersshadow on 2007-06-04
> **FXFman1209 said:**
> Hang on, I'm also having the Segmentation Fault error... whats the problem? I'm sorry. :(

If you're using the beta version, you need to make sure all drop down boxes are selected and that the input and outputs are file names, not directories.

---

### Post by bennyj on 2007-06-04
Well finaly got it to work.My problem was that i was hittihg the load button after inserting the dvd and it would drop down a box with numbered tiles and in parantheses(sp?) next to it-it would have the duration of the movie.I would select that thinking that was all i had to do.But for some reason vive does'nt like that.If i seleceted the button below that and browse for the title directly of the dvd and just put mymovie.mp4 in the output then all went well.

thanks for the help

ps.also i noticed that when i went to upload the movei to my 30 gig 5th gen ipod it would tell me(through windows.I would transfer the movie to my laptop into itunes)that the bit rate of my ipod did not support the current bit rate of the movie.So I changed to ipodvidenc from 192 audio bit rate to 128 and all went well.

---

### Post by FXFman1209 on 2007-06-04
Alright, it looks like I was missing one drop down box. Now I'm getting this error...

fxfitz@lappyman:~$ ffmpeg -i "/home/fxfitz/multimedia/videos/psych/Psych.S01E15.DSR.XviD-ORENJi.avi" -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -bufsize 4096 -pass 1 -aspect 4:3 -s 320x240 -acodec mp3 -ab 192 -ar 44100 -title "Psych" -author "Psych" -copyright "2007" -comment "Encoded by Vive" "/home/fxfitz/name"  ; exit
FFmpeg version SVN-r9192, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-pp --enable-pthreads --enable-dc1394 --enable-liba52 --enable-libfaac --enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libogg --enable-libtheora --enable-libvorbis --enable-x264 --enable-xvid --enable-shared --disable-debug
  libavutil version: 49.4.0
  libavcodec version: 51.40.4
  libavformat version: 51.12.1
  built on Jun  3 2007 18:04:19, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (23976024/1000000)
Input #0, avi, from '/home/fxfitz/multimedia/videos/psych/Psych.S01E15.DSR.XviD-ORENJi.avi':
  Duration: 00:42:30.0, start: 0.000000, bitrate: 1147 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 512x384, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Output #0, mp4, to '/home/fxfitz/name':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, q=2-31, pass 1, 0 kb/s, 23.98 fps(c)
  Stream #0.1: Audio: mp3, 44100 Hz, stereo, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0xb7e1c188]removing common factors from framerate
[mpeg4 @ 0xb7e1c188]timebase not supported by mpeg 4 standard
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
exit


What audio codec should I use? And what should the new file's extension be??

Thanks

---

### Post by Metallinut on 2007-06-04
> **endersshadow said:**
> Change that line to this:

```
ffmpeg -i "${input_file}" -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 "${output_file_name}.mov"
```

Those k's should make all the difference.

Made that change, now when trying to convert I get the following:
```
FFmpeg version SVN-r9165, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-pp --enable-pthreads --enab
le-dc1394 --enable-liba52 --enable-libfaac --enable-libfaad --enable-libgsm --en
able-lipmp3lame --enable-libogg --enable-libtheora --enable-libvorbis --enable-x
264 --enable-xvid --enable-shared --disable-debug
  libavutil version: 49.4.0
  libavcodec version: 51.40.4
  libavformat version: 51.12.1
  built on May 31 2007 17:48:46, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

Seems stream 0 codec frame rate differs from container frame rate: 29.98 (65535/
2186) -> 29.97 (2997/100)
Input #0, avi, from 'GI Joe The MASS Device.avi':
  Duration: 01:37:45.5, start 0.000000, bitrate: 1285 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 528x400, 29.97 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 192 kb/s
Output #0, mp4 to '/home/jp/converted/GI Joe The Mass Device.mov':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, q=3-5, 700 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: aac, 48000 Hz, stereo, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0xb7d6a488]VBV buffer too small for bitrate
Error while opening codec for output stream #0.0 - maybe incorrect parameters su
ch as bit_rate, rate, width or height

```

Grr...

---

### Post by endersshadow on 2007-06-04
FXFMan: Make bitrate and maxrate both 0.

Metallinut: Take out the -bufsize 4096 argument.

---

### Post by FXFman1209 on 2007-06-04
Nope:(

fxfitz@lappyman:~$ ffmpeg -i "/home/fxfitz/multimedia/videos/psych/Psych.S01E15.DSR.XviD-ORENJi.avi" -f mp4 -vcodec mpeg4 -bufsize 4096 -pass 1 -aspect 4:3 -s 320x240 -acodec ac3 -ab 192 -ar 44100 -comment "Encoded by Vive" "/home/fxfitz/test.mp4"  ; exit
FFmpeg version SVN-r9192, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-pp --enable-pthreads --enable-dc1394 --enable-liba52 --enable-libfaac --enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libogg --enable-libtheora --enable-libvorbis --enable-x264 --enable-xvid --enable-shared --disable-debug
  libavutil version: 49.4.0
  libavcodec version: 51.40.4
  libavformat version: 51.12.1
  built on Jun  3 2007 18:04:19, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (23976024/1000000)
Input #0, avi, from '/home/fxfitz/multimedia/videos/psych/Psych.S01E15.DSR.XviD-ORENJi.avi':
  Duration: 00:42:30.0, start: 0.000000, bitrate: 1147 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 512x384, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Output #0, mp4, to '/home/fxfitz/test.mp4':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, q=2-31, pass 1, 200 kb/s, 23.98 fps(c)
  Stream #0.1: Audio: ac3, 44100 Hz, stereo, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0xb7e33188]VBV buffer too small for bitrate
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

---

### Post by endersshadow on 2007-06-04
Try switching Buffer Size to 0 and Audio Bitrate to 128.

---

### Post by FXFman1209 on 2007-06-04
Alright...

output: /home/fxfitz/test.mp4
preset: iPod/PSP Video
Keep raw VOB

VIDEO
Container Format: mp4
Video Codec: mpeg4
MaxBitrate: 1000
Bitrate 700
Buffer Size:0
Number of Passes: 1
(never changed the right column)

AUDIO
Audio Codec: ac3
Audio Bitrate: 128
Sampling Frequency: 44100

OUTPUT:

fxfitz@lappyman:~$ ffmpeg -i "/home/fxfitz/multimedia/videos/psych/Psych.S01E15.DSR.XviD-ORENJi.avi" -f mp4 -vcodec mpeg4 -maxrate 1000 -b 700 -pass 1 -aspect 4:3 -s 320x240 -acodec ac3 -ab 128 -ar 44100 -comment "Encoded by Vive" "/home/fxfitz/test.mp4"  ; exit
FFmpeg version SVN-r9192, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-pp --enable-pthreads --enable-dc1394 --enable-liba52 --enable-libfaac --enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libogg --enable-libtheora --enable-libvorbis --enable-x264 --enable-xvid --enable-shared --disable-debug
  libavutil version: 49.4.0
  libavcodec version: 51.40.4
  libavformat version: 51.12.1
  built on Jun  3 2007 18:04:19, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (23976024/1000000)
Input #0, avi, from '/home/fxfitz/multimedia/videos/psych/Psych.S01E15.DSR.XviD-ORENJi.avi':
  Duration: 00:42:30.0, start: 0.000000, bitrate: 1147 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 512x384, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
File '/home/fxfitz/test.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to '/home/fxfitz/test.mp4':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, q=2-31, pass 1, 0 kb/s, 23.98 fps(c)
  Stream #0.1: Audio: ac3, 44100 Hz, stereo, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0xb7d6d188]a vbv buffer size is needed, for encoding with a maximum bitrate
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
exit


Same thing. :(:(

---

### Post by endersshadow on 2007-06-04
You didn't set maxrate and bitrate to 0, as well :)

Here's what the issue is: That version of Vive was made w/ the older ffmpeg which dealt with rates as kb/s.  Now, it deals with them as b/s, so it is now giving you underflow errors.

---

### Post by FXFman1209 on 2007-06-04
Woops. I'm sorry, I set those to 0 on another test. Here is the output when ALL of them have been set to 0.

fxfitz@lappyman:~$ ffmpeg -i "/home/fxfitz/multimedia/videos/psych/Psych.S01E15.DSR.XviD-ORENJi.avi" -f mp4 -vcodec mpeg4 -pass 1 -aspect 4:3 -s 320x240 -acodec ac3 -ab 128 -ar 44100 -comment "Encoded by Vive" "/home/fxfitz/test.mp4"  ; exit
FFmpeg version SVN-r9192, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-pp --enable-pthreads --enable-dc1394 --enable-liba52 --enable-libfaac --enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libogg --enable-libtheora --enable-libvorbis --enable-x264 --enable-xvid --enable-shared --disable-debug
  libavutil version: 49.4.0
  libavcodec version: 51.40.4
  libavformat version: 51.12.1
  built on Jun  3 2007 18:04:19, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (23976024/1000000)
Input #0, avi, from '/home/fxfitz/multimedia/videos/psych/Psych.S01E15.DSR.XviD-ORENJi.avi':
  Duration: 00:42:30.0, start: 0.000000, bitrate: 1147 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 512x384, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
File '/home/fxfitz/test.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to '/home/fxfitz/test.mp4':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, q=2-31, pass 1, 200 kb/s, 23.98 fps(c)
  Stream #0.1: Audio: ac3, 44100 Hz, stereo, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0xb7dde188]removing common factors from framerate
[mpeg4 @ 0xb7dde188]timebase not supported by mpeg 4 standard
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
exit

---

### Post by endersshadow on 2007-06-04
Now *that's* and new one!

It appears that it's a bit of a problem w/ a yuv as an input.  Cut and paste this command into your terminal:

```
ffmpeg -i "/home/fxfitz/multimedia/videos/psych/Psych.S01E15.DSR.XviD-ORENJi.avi" -f mp4 -vcodec mpeg4 -b 700k -aspect 4:3 -r 23.98 -s 320x240 -acodec aac -ar 48000 -comment "Encoded by Vive" "/home/fxfitz/test.mp4"
```

---

### Post by FXFman1209 on 2007-06-04
Unknown codec: aac. :(

---

### Post by endersshadow on 2007-06-04
> **FXFman1209 said:**
> Unknown codec: aac. :(

My fault...habit made me type aac instead of ac3...sorry!

P.S.-This for an iPod? If so, use mp3, not ac3.

---

### Post by FXFman1209 on 2007-06-04
Awesome! It's encoding!

Alright, so, how would I get this to work all the time with Vive? Or do I have to command line it all the time?

PS. And what exactly was the problem?? yuv??

---

### Post by endersshadow on 2007-06-04
> **FXFman1209 said:**
> Awesome! It's encoding!

Alright, so, how would I get this to work all the time with Vive? Or do I have to command line it all the time?

PS. And what exactly was the problem?? yuv??

The problem is the framerate of the original movie and the way yuv handles it.  You have to explicitly set the framerate with ffmpeg for some reason, which isn't an option in Vive.  My suggestion would be to use the command line, since it appears yuv, mpeg4, and ffmpeg do not play well together.  That way, it's easier to change options.

---

### Post by FXFman1209 on 2007-06-04
Alright. Thanks a bunch!!

---

### Post by endersshadow on 2007-06-04
It's what I'm here for :)

---

### Post by FXFman1209 on 2007-06-05
Alright. I have another question for you. So far I've got everything working fine from the command line, and I just ripped a DVD using dvdrip. I had to rip two titles, however, and it produces 3 .vob files per title. Is there anyway to combine all of these .vob files into one easy .mp4 file for the ipod??

---

### Post by endersshadow on 2007-06-05
> **FXFman1209 said:**
> Alright. I have another question for you. So far I've got everything working fine from the command line, and I just ripped a DVD using dvdrip. I had to rip two titles, however, and it produces 3 .vob files per title. Is there anyway to combine all of these .vob files into one easy .mp4 file for the ipod??

If you use transcode, yes.  I don't have the documentation in front of me nor do I know it off the top of my head, but I gotta run.  If you look a few posts up, you use this command:

```
vobcopy -l -n # /path/to/output/dir/
```

Where # is the title number, it will rip one large file, which then you can run through Vive/ffmpeg.  Although, Vive does have the DVD ripping functionality built in, as well.

---

### Post by Metallinut on 2007-06-07
> **endersshadow said:**
> 
Metallinut: Take out the -bufsize 4096 argument.

Did that and now get this:

```
FFmpeg version SVN-r9165, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-pp --enable-pthreads --enable-dc1394 --enable-liba52 --enable-libfaac --enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libogg --enable-libtheora --enable-libvorbis --enable-x264 --enable-xvid --enable-shared --disable-debug
  libavutil version: 49.4.0
  libavcodec version: 51.40.4
  libavformat version: 51.12.1
  built on May 31 2007 17:48:46, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

Seems stream 0 codec frame rate differs from container frame rate: 29.98 (65535/2186) -> 29.97 (2997/100)
Input #0, avi, from 'GI Joe The MASS Device.avi':
  Duration: 01:37:45.5, start: 0.000000, bitrate: 1285 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 528x400, 29.97 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 192 kb/s
Output #0, mp4, to '/home/jp/converted/GI Joe - The MASS Device.mov':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, q=3-5, 700 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: aac, 48000 Hz, stereo, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mpeg4 @ 0xb7d67488]a vbv buffer size is needed, for encoding with a maximum bitrate
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

---

### Post by endersshadow on 2007-06-07
Try this:

```
ffmpeg -i "${input_file}" -f mp4 -vcodec mpeg4 -b 700k -qmin 3 -qmax 5 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 "${output_file_name}.mov"
```

---

### Post by Metallinut on 2007-06-08
> **endersshadow said:**
> Try this:

```
ffmpeg -i "${input_file}" -f mp4 -vcodec mpeg4 -b 700k -qmin 3 -qmax 5 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 "${output_file_name}.mov"
```

Looks like it's running now...we'll see how it looks on my iPod.

Thanks!

---

### Post by penguinchrissy on 2007-06-19
No matter what I do I get this output when trying to encode 

ffmpeg: error while loading shared libraries: libavformat.so.50: cannot open shared object file: No such file or directory

I know I have the proper lib installed it the same version as ffmpeg.

Any fixes?

---

### Post by endersshadow on 2007-06-19
Yup.  It's a simple command, but to get it right I need the output from this command:

```
ls /usr/lib | grep libav
```

---

### Post by penguinchrissy on 2007-06-19
here is the output for that command

libavahi-client.so.3
libavahi-client.so.3.2.2
libavahi-common.so.3
libavahi-common.so.3.4.3
libavahi-core.so.5
libavahi-core.so.5.0.0
libavahi-glib.so.1
libavahi-glib.so.1.0.1
libavahi-qt3.so.1
libavahi-qt3.so.1.0.1
libavc1394.so.0
libavc1394.so.0.3.0
libavcodec.so.0d
libavcodec.so.0d.51.11.0
libavformat.so.0d
libavformat.so.0d.50.5.0
libaviplay-0.7.so.0
libaviplay-0.7.so.0.0.44
libaviplayavcodec-0.7.so.0
libaviplayavcodec-0.7.so.0.0.44
libaviplayavformat-0.7.so.0
libaviplayavformat-0.7.so.0.0.44
libaviplayavutil-0.7.so.0
libaviplayavutil-0.7.so.0.0.44
libaviplaydha-0.7.so.0
libaviplaydha-0.7.so.0.0.44
libaviplayvidix-0.7.so.0
libaviplayvidix-0.7.so.0.0.44
libavutil.so.0d
libavutil.so.0d.49.0.0


Thanks for your help!!:p

---

### Post by endersshadow on 2007-06-19
Sorry, the season finale of Deadliest Catch was on...and that takes pretty much any and all precedence in my life (it's a sad one, I know).  Anyway, here's that command:

```
sudo ln -s /usr/lib/lbavformat.so.0d.50.5.0 /usr/lib/libavformat.so.50
```

That should do it.  Cheers!

---

### Post by penguinchrissy on 2007-06-20
That was a great last episode and After the catch was cool to. Again I thank you for you help but I tried what you said and this is what happened. I tired it a couple of times. Once then I closed the terminal and ran ipodvidence and the other ffmpeg code neither worked. I tired your code again then ran ipodvidence again then your code again to show you the results.

ipodvidenc The.Departed.avi
What would you like to name the output file (sans extension)?
test
test will be located in /home/dj. Is this acceptable? [y/n]
y
ffmpeg: error while loading shared libraries: libavformat.so.50: cannot open shared object file: No such file or directory
dj@dj-laptop:~$ sudo ln -s /usr/lib/lbavformat.so.0d.50.5.0 /usr/lib/libavformat.so.50
ln: creating symbolic link `/usr/lib/libavformat.so.50' to `/usr/lib/lbavformat.so.0d.50.5.0': File exists

---

### Post by endersshadow on 2007-06-20
Well that's bizarre.  I definitly put that in right.  Try flip flopping the file names..

---

### Post by penguinchrissy on 2007-06-20
This is an error I'm getting now

sudo ln -s /usr/lib/lbavformat.so.0d.50.5.0 /usr/lib/libavformat.so.50
ln: accessing `/usr/lib/libavformat.so.50': Too many levels of symbolic links

It worked last night!?

---

### Post by endersshadow on 2007-06-20
> **penguinchrissy said:**
> This is an error I'm getting now

sudo ln -s /usr/lib/lbavformat.so.0d.50.5.0 /usr/lib/libavformat.so.50
ln: accessing `/usr/lib/libavformat.so.50': Too many levels of symbolic links

It worked last night!?

Well that's interesting, what's this put out:

```
ls -l | grep libavformat
```

---

### Post by penguinchrissy on 2007-06-21
nothing comes out

dj@dj-laptop:~$ ls -l | grep libavformat
dj@dj-laptop:~$ 

thats all that happens :(

---

### Post by endersshadow on 2007-06-22
sorry, ls -l /usr/lib | grep libavformat

My fault!

---

### Post by penguinchrissy on 2007-06-23
ls -l /usr/lib | grep libavformat
lrwxrwxrwx  1 root root       26 2007-06-20 12:29 lbavformat.so.0d.50.5.0 -> /usr/lib/libavformat.so.50
lrwxrwxrwx  1 root root       24 2007-06-19 18:48 libavformat.so.0d -> libavformat.so.0d.50.5.0
-rw-r--r--  1 root root   543600 2007-03-21 10:14 libavformat.so.0d.50.5.0

---

### Post by endersshadow on 2007-06-24
I'm an idiot.  I mistyped the name!

Do this:

```
sudo rm /usr/lib/lbavformat.so.0d.50.5.0
sudo ln -s /usr/lib/libavformat.so.0d.50.5.0 /usr/lib/libavformat.so.50
```

That should work :)

---

### Post by penguinchrissy on 2007-06-24
no go again

dj@dj-laptop:~$ sudo rm /usr/lib/lbavformat.so.0d.50.5.0
Password:
dj@dj-laptop:~$ sudo ln -s /usr/lib/libavformat.so.0d.50.5.0 /usr/lib/libavformat.so.50
dj@dj-laptop:~$ cd /home/dj/AzureusDownloads/The.Departed
bash: cd: /home/dj/AzureusDownloads/The.Departed: No such file or directory
dj@dj-laptop:~$ cd /home/dj/AzureusDownloads/Films/The.Departed
[email]dj@dj-laptop:~/AzureusDownloads/Films/The.Depa[/email]rted$ ipodvidenc The.Departed.avi
What would you like to name the output file (sans extension)?
test
test will be located in /home/dj/AzureusDownloads/Films/The.Departed. Is this acceptable? [y/n]
y
ffmpeg: error while loading shared libraries: libavcodec.so.51: cannot open shared object file: No such file or directory
[email]dj@dj-laptop:~/AzureusDownloads/Films/The.Depa[/email]rted$ sudo rm /usr/lib/lbavformat.so.0d.50.5.0
rm: cannot remove `/usr/lib/lbavformat.so.0d.50.5.0': No such file or directory
[email]dj@dj-laptop:~/AzureusDownloads/Films/The.Depa[/email]rted$ sudo ln -s /usr/lib/libavformat.so.0d.50.5.0 /usr/lib/libavformat.so.50
ln: creating symbolic link `/usr/lib/libavformat.so.50' to `/usr/lib/libavformat.so.0d.50.5.0': File exists
[email]dj@dj-laptop:~/AzureusDownloads/Films/The.Depa[/email]rted$ ipodvidenc The.Departed.aviWhat would you like to name the output file (sans extension)?
test
test will be located in /home/dj/AzureusDownloads/Films/The.Departed. Is this acceptable? [y/n]
y
ffmpeg: error while loading shared libraries: libavcodec.so.51: cannot open shared object file: No such file or directory
[email]dj@dj-laptop:~/AzureusDownloads/Films/The.Depa[/email]rted$ 


:(

---

### Post by PinkBullets9 on 2007-06-25
umang@umang-desktop:~$ sudo apt-get install libdvdcss2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libdvdcss2-dev

any ideas? am i missing something from the sources?

---

### Post by penguinchrissy on 2007-06-25
you probaly don't have a repository that you need.

---

### Post by fanfan on 2007-06-27
I was wondering if anyone could modify the ipodvidenc script to convert a folder of videos instead of a single file? I've got about 45 files that I want to convert... Anyways, help is greatly needed and appreciated.
-Brian

---

### Post by Metallinut on 2007-06-28
This is the script I'm using:

```
ffmpeg -i "${input_file}" -f mp4 -vcodec mpeg4 -b 700k -qmin 3 -qmax 5 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 "/home/jp/converted/${output_file_name}.mov"
```

However, when I move the file over to Windows (still using it for iTunes), iTunes and Quicktime both say the file is not a video....

Has anyone got this working, and can import their converted videos into iTunes, and play them on a video iPod?

Thanks

---

### Post by bennyj on 2007-06-28
> **Metallinut said:**
> This is the script I'm using:

```
ffmpeg -i "${input_file}" -f mp4 -vcodec mpeg4 -b 700k -qmin 3 -qmax 5 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 "/home/jp/converted/${output_file_name}.mov"
```

However, when I move the file over to Windows (still using it for iTunes), iTunes and Quicktime both say the file is not a video....

Has anyone got this working, and can import their converted videos into iTunes, and play them on a video iPod?

Thanks

You need to rename it from "movie.mov" to "movie.mp4" then import it into itunes and it will work fine! I just went into the script and changed {outputfile}.mov to {outputfile}.mp4. That way you dont have to mess with it after encoding.

---

### Post by endersshadow on 2007-07-03
Sorry folks!  Was on vacation at the Jersey Shore.  Twas rather nice.

Anyway, to your questions:

penguinchrissy: You may just be better off uninstalling ffmpeg, libavcodec, and libavformat and reinstalling them.  It's rather odd that it's giving you all of that.

PinkBullets: You're going to want to add the [Medibuntu](http://medibuntu.sos-sts.com/) repository to your sources.list file.

fanfan: Yes, yes it is possible by adding a for each loop.  However, the latest SVN of [Vive](https://sourceforge.net/projects/vive) has this feature.

---

### Post by lonegeek on 2007-07-08
Unable to find a source package for ffmpeg


Is what I get when I type in apt-get source ffmpeg

---

### Post by FakeOutdoorsman on 2007-07-08
Do you have Universe Packages and Source code enabled in your /etc/apt/sources.list file?  You can do this graphically with System -> Administration -> Software Sources.  Check "Community-maintained Open Source software (universe)" and "Source code".  Then in a terminal type "sudo apt-get update" and finally retry "sudo apt-get source ffmpeg".

---

### Post by claypole on 2007-07-09
This may be buried in the post somewhere, but I had to change enable-x264 and enable-xvid flags to enable-libx264 and enable-libxvid.  This may be because the flags have changed on the latest ffmeg from svn, it would be great if this could be updated in the main text of the HOWTO for others.  And thanks for a great HOWTO!! :KS

---

### Post by endersshadow on 2007-07-09
> **claypole said:**
> This may be buried in the post somewhere, but I had to change enable-x264 and enable-xvid flags to enable-libx264 and enable-libxvid.  This may be because the flags have changed on the latest ffmeg from svn, it would be great if this could be updated in the main text of the HOWTO for others.  And thanks for a great HOWTO!! :KS

Changed, and thanks :)

---

### Post by vishnu on 2007-07-09
Excellent but when I run I get this?

ffmpeg: error while loading shared libraries: libavformat.so.50: cannot open shared object file: No such file or directory

---

### Post by mortuk on 2007-07-11
I get this error also, any ideas?

---

### Post by endersshadow on 2007-07-11
For the libavformat.so.50 error: [http://www.twelvestone.com/forum_thread/view/33460](http://www.twelvestone.com/forum_thread/view/33460)

---

### Post by endersshadow on 2007-07-12
Vive 2.0.0-beta2 is now available!  New features include multiple file and folder support, a simplified and streamlined interface, and a lot of behind the scenes stuff that makes me sleep better at night but you won't notice unless you look at the code.  So [download it today](https://sourceforge.net/project/showfiles.php?group_id=158461)!

---

### Post by eyemou on 2007-07-12
Hello... I was wondering (pardon my ignorance, btw), how to uninstall ffmpeg. You see, I installed the newest SVN version, which has problems encoding with the aac codec it seems (I am getting the "unknown codec 'aac'" error upon encoding), and want to install an older version.

I had built this one from source, and figured that an apt-get remove ffmpeg would do the trick. It acted as if it removed something (I wish I hadn't of closed the terminal window, so I can recall exactly what happened), but apparently ffmpeg is still installed...

"FFmpeg version SVN-r9569, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-pthreads --enable-libogg --enable-liba52 --enable-dc1394 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libxvid --enable-libx264"

Also, does someone know which version is known to work with aac (which I do have installed, and did enable when compiling the SVN version r9569, but with no luck), and where to get it?

Does the 20060823 version work? Or is it the 200703[something] version? I think there was also a recent one, from earlier this month (July 2007).

Any hep appreciated. I've come so close to getting things to work, that I can't turn back now.

BTW, this thread, and the wiki post have been extremely helpful.

Thanks!!

---

### Post by eyemou on 2007-07-12
Duh. Nevermind my question about the uninstall ("make uninstall"... I just had to manually clean out and then remove the /usr/local/vhook folder, as the uninstall attempted to remove it with files still included).

My question still stands about what is & where to obtain the proper ffmpeg version for Ipod video encoding (on Kubuntu Feisty 7.04, btw). 

Thanks!

---

### Post by eyemou on 2007-07-12
Aha!

svn checkout -r 8560 svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg

That version (r8560) + your instructions seems to work. I got nervous during the 'make', as a lot of warnings ("deprecated" this, "null pointer" that) were flying by, but it compiled, and works now.

Now to try ripping some dvds to mp4...

---

### Post by endersshadow on 2007-07-13
Glad to hear you solved your problems before I could get here :-D

---

### Post by jmusso on 2007-07-14
> **endersshadow said:**
> For the libavformat.so.50 error: [http://www.twelvestone.com/forum_thread/view/33460](http://www.twelvestone.com/forum_thread/view/33460)

I checked this out and tried to do as the guide told me. I'm running into a problem wtih permission to edit this file. Its saying I don't have the permission to do it... I don't understand why. Help please? also, when I try to sudo apt-get libdvdcss2-dev it says something like e: libdvdcss2-dev does not exist. Thanks.

---

### Post by huzz on 2007-07-14
> huzz@iNFECTED:~/downloads/vive-2.0.0-beta2$ make
make  all-recursive
make[1]: Entering directory `/home/huzz/downloads/vive-2.0.0-beta2'
Making all in src
make[2]: Entering directory `/home/huzz/downloads/vive-2.0.0-beta2/src'
gcc  -g -O2 -D PREFIX=\"/usr/local\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -pthread -DORBIT2=1 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -o vive error.o interface.o options.o preferences.o presets.o combo_menus.o encode.o dvd.o tooltips.o vive.o  -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -pthread -lgnomevfs-2 -lgconf-2 -lgmodule-2.0 -ldl -lORBit-2 -lgthread-2.0 -lrt -lgobject-2.0 -lglib-2.0   -lvte
combo_menus.o: In function `populate_ffmpeg':
/home/huzz/downloads/vive-2.0.0-beta2/src/combo_menus.c:38: undefined reference to `av_register_all'
/home/huzz/downloads/vive-2.0.0-beta2/src/combo_menus.c:50: undefined reference to `first_oformat'
/home/huzz/downloads/vive-2.0.0-beta2/src/combo_menus.c:50: undefined reference to `first_oformat'
/home/huzz/downloads/vive-2.0.0-beta2/src/combo_menus.c:50: undefined reference to `first_avcodec'
/home/huzz/downloads/vive-2.0.0-beta2/src/combo_menus.c:94: undefined reference to `first_avcodec'
collect2: ld returned 1 exit status
make[2]: *** [vive] Error 1
make[2]: Leaving directory `/home/huzz/downloads/vive-2.0.0-beta2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/huzz/downloads/vive-2.0.0-beta2'
make: *** [all] Error 2
huzz@iNFECTED:~/downloads/vive-2.0.0-beta2$

Could someone please tell me where am i going wrong....

---

### Post by endersshadow on 2007-07-15
jmusso: 1. Try using sudo in front of the command that's telling you that you don't have permission
2. What's your /etc/apt/sources.list look like?

huzz: You need to compile ffmpeg with the --enable-shared flag in order to install libavformat.

---

### Post by jmusso on 2007-07-16
```
joe@joe:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: No such file or directory
joe@joe:~$ gedit /etc/apt/sources.list
joe@joe:~$ 
joe@joe:~$ 

```

that's what it said. i wasn't sure if i was supposed to do a gedit or not, so the first time i didn't, then when i ran "gedit /blah blah blah/" it came up with an empty script. does this help? thanks for the help!

---

### Post by jmusso on 2007-07-16
When I tried to install Vive, this is what I got...
```
joe@joe:~$ pkg-config
Must specify package names on the command line
joe@joe:~$ cd /home/joe/vive-2.0.0-beta2
joe@joe:~/vive-2.0.0-beta2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ffmpeg... yes
checking for vobcopy... yes
checking for mplayer... yes
checking for prefix by checking for ffmpeg... /usr/local/bin/ffmpeg
checking whether DVD is enabled... yes
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... yes (version 2.10.11)
checking pkg-config is at least version 0.9.0... yes
checking for libgnomevfs... configure: error: Package requirements (gnome-vfs-2.0 >= 2.0) were not met:

No package 'gnome-vfs-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables libgnomevfs_CFLAGS
and libgnomevfs_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

joe@joe:~/vive-2.0.0-beta2$ 
joe@joe:~/vive-2.0.0-beta2$ 


```

help?

---

### Post by endersshadow on 2007-07-16
Okay, do this:

```
sudo su
echo "deb http://medibuntu.sos-sts.com/repo/ feisty free non-free" >> /etc/apt/sources.list
exit
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install libdvdcss2-dev libdvdread-dev libdvdnav-dev libgnomevfs2-dev
```

Then try the configure again.

Not necessary that you read this last part, but I thought I'd at least explain the commands:

The "sudo su" command gives you root access.  You need this to edit /etc/apt/sources.list, which is the file that tells Ubuntu where to look for packages.  The command "echo "deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free" >> /etc/apt/sources.list" simply appends that line to your sources.list file, so that Ubuntu knows to look in the Medibuntu repository.  Next, you apt-get update which gets all of the information for the repositories cached on your system, and then you apt-get upgrade which installs any of the updated packages that Medibuntu has.  Then, you install libdvdcss2-dev, libdvdread-dev, libdvdnav-dev, and libgnomevfs2-dev, all the development packages you'll need for Vive.

Have fun :)

---

### Post by jmusso on 2007-07-16
```
joe@joe:~$ sudo su
root@joe:/home/joe# echo "deb http://medibuntu.sos-sts.com/repo/ feisty free non-free" >> /etc/apt/sources.list
root@joe:/home/joe# exit
exit
joe@joe:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com feisty Release.gpg [191B]
Ign http://archive.ubuntu.com feisty/main Translation-en_US                    
Ign http://archive.ubuntu.com feisty/universe Translation-en_US
Hit http://archive.ubuntu.com feisty Release              
Get:2 http://medibuntu.sos-sts.com feisty Release.gpg [189B]
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_US
Hit http://archive.ubuntu.com feisty/main Packages
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_US
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_US
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_US
Hit http://archive.ubuntu.com feisty/universe Packages
Hit http://medibuntu.sos-sts.com feisty Release
Err http://medibuntu.sos-sts.com feisty Release
  
Get:3 http://medibuntu.sos-sts.com feisty Release [2195B]
Ign http://medibuntu.sos-sts.com feisty Release
Ign http://medibuntu.sos-sts.com feisty/free Packages
Ign http://medibuntu.sos-sts.com feisty/non-free Packages
Ign http://medibuntu.sos-sts.com feisty/free Packages
Ign http://medibuntu.sos-sts.com feisty/non-free Packages
Hit http://medibuntu.sos-sts.com feisty/free Packages
Hit http://medibuntu.sos-sts.com feisty/non-free Packages
Hit http://medibuntu.sos-sts.com feisty/free Packages
Hit http://medibuntu.sos-sts.com feisty/non-free Packages
Fetched 2385B in 1s (1432B/s)
Reading package lists... Done
W: GPG error: http://medibuntu.sos-sts.com feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
joe@joe:~$ 


``` 

i'm guessing this is a problem... i'm going to carry out the other commands you listed in hopes i don't screw everything up. thanks for the help, and the explanation is valuable. i always like to know what i'm doing and why i'm doing it.

---

### Post by jmusso on 2007-07-16
Okay so I went ahead and ran all of the other commands you gave me after I got that line of code above...

I "cd" ed where my vive was, ./configured it, then did a "make", and when i did "make install" here's what happened....

```
joe@joe:~/vive-2.0.0-beta2$ make install
Making install in src
make[1]: Entering directory `/home/joe/vive-2.0.0-beta2/src'
make[2]: Entering directory `/home/joe/vive-2.0.0-beta2/src'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'vive' '/usr/local/bin/vive'
/usr/bin/install: cannot create regular file `/usr/local/bin/vive': Permission denied
make[2]: *** [install-viveprgPROGRAMS] Error 1
make[2]: Leaving directory `/home/joe/vive-2.0.0-beta2/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/joe/vive-2.0.0-beta2/src'
make: *** [install-recursive] Error 1
joe@joe:~/vive-2.0.0-beta2$ 

```

---

### Post by endersshadow on 2007-07-17
make install needs to be super user to commense:

```
sudo make install
```

That'll do it :)

---

### Post by jmusso on 2007-07-17
Okay, I think I've done everything right up until now... Here's what I get when I try to encode a video.
```
joe@joe:~$ ipodvidenc /home/joe/300.avi
What would you like to name the output file (sans extension)?
threehundred
threehundred will be located in /home/joe. Is this acceptable? [y/n]
y
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-mp3lame --enable-faad --enable-faac --enable-xvid --enable-pthreads --enable-shared 
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Jul 17 2007 02:08:20, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
/home/joe/300.avi: I/O error occured
Usually that means that input file is truncated and/or corrupted.

```

---

### Post by endersshadow on 2007-07-17
Well, ipodvidenc is a bit different from Vive.  ipodvidenc is a script, while Vive is a GUI application.  There's a bit of a hangup with ipodvidenc and the newer versions of ffmpeg, but here's how to fix it.

```
sudo gedit /usr/bin/ipodvidenc
```

Then, find this line:

```
ffmpeg -i "${input_file}" -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 "${output_dir}/${output_file_name}.mov"
```

Change it to this:

```
ffmpeg -i "${input_file}" -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -acodec aac -ab 192 -s 320x240 -aspect 4:3 "${output_dir}/${output_file_name}.mov"
```

Save and then you should be all set.  Or simply use Vive with this:

```
vive
```

Select /home/joe/300.avi with the File button, then select where you want it output to, select the iPod preset, then press Encode.

---

### Post by jmusso on 2007-07-17
Okay, I did all that... and this is what is happening.

I couldn't copy the text from vive, but here's a screenshot and what it said...

[IMG]http://img.photobucket.com/albums/v508/jmusso/Screenshot.png[/IMG]

Thanks for all the help, by the way. I really appreciate it.

---

### Post by endersshadow on 2007-07-17
You need to put a file extension on the output file.

---

### Post by jmusso on 2007-07-17
oh okay... and if i was converting these for my ipod video, what file extension should i use? .mp4 or something? i really don't know as much as i should about this... thanks again.

---

### Post by endersshadow on 2007-07-17
.mov is accepted on iPods :)

Edit: You learn by asking that which you don't know, so don't feel bad for asking.

---

### Post by jmusso on 2007-07-17
Got it working! Thanks for all the help. The only weird thing is, the sound seems to be "off", so it looks like a Godzilla movie or something. The sound doesn't match up with the video, its just a tad different so that the people say what they're saying before I can hear it... I watched the original .avi file to see if it was like that there, and it was perfectly normal. So I'm guessing this happened during the encoding process. Any ideas how I can fix this? If you've seen 300 you'll know the effect is lost when Lionidus says "this is sparta" and it looks like he's lip synching...

---

### Post by endersshadow on 2007-07-18
Unfortunately, this sometimes happens with ffmpeg.  You'll have to reencode it via the command line.  But, I'll make it simple for you :)

Here's the command:

```
ffmpeg -y -f mp4 -vcodec mpeg4 -b 700k -s 320x240 -acodec aac -ac 2 -ab 192k -title "threehundred" -async 1 -i "/home/joe/300.AVI" "/home/joe/threehundred.mov"
```

That should do it.  On a side note, 300 is an awesome movie.  They just opened up a new theater in my town and were using these first few days to do charity showings ($1 admission, 100% goes to charity) while playing not-so-recent movies.  Saw 300 again on the big screen for $1 today, and I enjoyed it as thoroughly as I did the first time :-D

---

### Post by weirdalduke on 2007-07-18
I'm getting this message after answering the prompts:

/usr/bin/ipodvidenc: line 24: ffmpeg: command not found

Any Suggestions, Thanks for your help.

---

### Post by endersshadow on 2007-07-18
> **weirdalduke said:**
> I'm getting this message after answering the prompts:

/usr/bin/ipodvidenc: line 24: ffmpeg: command not found

Any Suggestions, Thanks for your help.

You don't have ffmpeg installed.  Go to the first post and follow instructions on getting it installed and then you'll be all set :)

---

### Post by jmusso on 2007-07-18
Something else weird just happened... I use Banshee to sync my iPod usually, and I did a drag and drop of some songs in my library to my iPod, then clicked Sync and clicked Save Manual Changes, like I always do... except then it started to convert a .mov file, which turned out to be 300! the crappy version with the lip synching of course, but now it won't play on my iPod! I'm afraid that Banshee will try to do this to all my movies... should I just use gtkpod instead, even though its such a hassle compared to Banshee? I moved the vid file on there with gtkpod, and it played well. Then when I moved some mp3s onto it using Banshee, it "converted" the movie file without asking me...

---

### Post by endersshadow on 2007-07-18
To be honest, I know nothing of how Banshee handles iPods and/or media.  My iPod's in my car, so I can't try it out right at the moment.  My immediate advice would be to just go w/ gtkpod, but if you want to look around to tr to find more info about Banshee, that's your perogative :)

---

### Post by endersshadow on 2007-07-20
Huge news!  Vive 2.0.0 has finally been released!  Download it [here](https://sourceforge.net/project/showfiles.php?group_id=158461)!

Also, an Ubuntu Feisty package has been added.  I suggest that you use the [Medibuntu](http://medibuntu.org) repository to meet the dependencies, as the Ubuntu package is compiled to allow DVD usage.  Enjoy!

---

### Post by shanest on 2007-07-24
Thanks!  This worked brilliantly for me.  

There was one glitch where the encoded video of my Garden State DVD was complete garbage, but it's been great besides that.  DVD ripping is also very slow for me, but I think it's largely (although not completely) due to my drive which is in the docking station for my X60 tablet.  

For other DVDs, it worked great, albeit slow. 
And for other video files, it works brilliantly!

Once again, thanks for the great work.  For awhile, I was worried I might have to transfer videos in *gasp* Windows

---

### Post by 92bek on 2007-07-25
Hey, I'm really looking forward to using Vive 2.0 but I cannot seem to get it up and running.  I'm running the ubuntu 64bit version and not sure if there's issues introduced by that.  But when I attempt to build from source, I get the following error:
```

chief@Beefy:~$ tar -zxvf vive-2.0.0.tar.gz 
gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors

```
Or by the .deb pkg:
```

chief@Beefy:~$ sudo dpkg -i vive_2.0.0-0ubuntu1_i386.deb 
dpkg-deb: unexpected end of file in version number in vive_2.0.0-0ubuntu1_i386.deb
dpkg: error processing vive_2.0.0-0ubuntu1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 vive_2.0.0-0ubuntu1_i386.deb

```

I'm sure there's a simple fix, and it might be more OS related than a VIVE issue; but I'm n00b.  Any advice would be greatly appreciated!!!

---

### Post by endersshadow on 2007-07-25
92bek: These errors happen when the download wasn't completed correctly.  Try redownloading the files and making sure that their sums are okay.

Here's the MD5 sum of the tar.gz and the .deb, respectively:

```
44ac203364f00e0a8c68e2fc9194442c  vive-2.0.0.tar.gz
830213d2fce8a1b69b4d82a36cc2df2e  vive_2.0.0-0ubuntu1_i386.deb
```

You can check them by doing this:

```
md5sum /path/to/file
```

---

### Post by 92bek on 2007-07-26
Great!  Thanks for the advice.  I've was able to download the file w/ integrity and successfully unzip the source file to get to the ./configure prompt.  Now another n00b question about compiling the source. 

I've collected most of the dependencies which worked for a while but have now been stumped on obtaining the "libgnomeui" package.  Code:
```
 
chief@Beefy:~$ ./configure
bash: ./configure: No such file or directory
chief@Beefy:~$ ls
Desktop  Examples  vive-2.0.0  vive-2.0.0.tar.gz
chief@Beefy:~$ cd vive-2.0.0/
chief@Beefy:~/vive-2.0.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ffmpeg... yes
checking for vobcopy... yes
checking for mplayer... yes
checking for prefix by checking for ffmpeg... /usr/bin/ffmpeg
checking whether DVD is enabled... yes
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... yes (version 2.10.11)
checking pkg-config is at least version 0.9.0... yes
checking for libgnome... yes
checking for libgnomeui... configure: error: Package requirements ( libgnomeui-2.0 >= 2.0) were not met:

No package 'libgnomeui-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables libgnomeui_CFLAGS
and libgnomeui_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
I've researched the forums and there seems to be no similar issue w/ a missing libgnomeui package.  I've used the apt-get to install almost all packages labeled "libgnomeui*".  Any thoughts on how to install or get the installer to recognize these packages?

Thanks again for the previous help.

---

### Post by endersshadow on 2007-07-26
You'll need to install libgnomeui-dev to compile from source.  If you were just using the Debian package, you'd need libgnomeui-0 and libgnomeui-common.

---

### Post by Sokarul on 2007-07-27
I'm having trouble getting the ffmpeg installed first.  
The problem is first at 
```
sudo apt-get install libdvdcss2-dev libdvdnav-dev libdvdr
```
Specifically the libdvdcss2-dev because it can't be found.  I also tried the other way listed but it didn't work either.  
I am using the 64 bit ubuntu so it may bot matter since Vive seems to only be for i386 which is 32 bit? Correct?

---

### Post by endersshadow on 2007-07-27
I built it on an i386, and Sourceforge's compile farm is now dead and buried so I can't compile it on x64.  Assumedly, the code works if built by a 64-bit gcc.  Medibuntu definitely has the x64 version of libdvdcss2.  Do you have Medibuntu in your /etc/apt/sources.list file?

---

### Post by Sokarul on 2007-07-28
I think I set it up right now, and then I was able to get libdvdcss2 to install.

---

### Post by ibelwich on 2007-07-28
Hey All,

Firstly big thanks for the howto especially useful for a linux newbie like myself.

I installed vive 2.0 (Great App)  and ran into a couple of hiccups got those all sorted and can rip and encode dvd's no problem.

However when i transfer them to my ipod using gtkpod , they never play i simply get a black screen fro 30 seconds and then it returns to the menu. I tried installing gpac and remuxxed the video but now gtkpod does not recognise it. 

Any ideas on how to resolve this? is something extra I need to download to update gtkpod?

Many thanks

---

### Post by endersshadow on 2007-07-28
Just a couple questions, ibelwich:

1. What version of gtkpod are you using?
2. What options did you use to encode the video?
3. What's the filename of the video?

---

### Post by ibelwich on 2007-07-28
Thanks for the reply Endersshadow,

To answer ytour questions:
1. Gtkpod version 0.99.8
2.I used the default options in vive here's the output from the terminal:
ffmpeg -y -f mp4 -vcodec mpeg4 -b 700k -aspect 4:3 -s 320x320 -acodec aac -ac 2 -ab 192k -i "/home/scott/dvd/vive_dvd_temp1-1.vob "home/scott/dvd/trueromance.mp4"

3. as you can see this is the filename created by vive when I originally inserted the dvd vive_dvd_temp1-1.vob

and then I am encoding this to trueromance.mp4

Thanks

---

### Post by endersshadow on 2007-07-28
Rename it trueromance.mov and try again.  It seems silly, but that's the way it is.

---

### Post by ibelwich on 2007-07-29
Thanks endersshadow,

that solved it partially. gtkpod recognises the .mov file and I can copy it to the ipod, but the behaviour is the same blank screen for 30 seconds and then returns back to the menu.

I am going to play around with it a bit see if I can nail it. If you have any other idea's let me know I give them a go.


one thing I have noticed and I am not sure if this is normal or not but in the vive terminal I see the following line

ffmpeg version SVN -rUNKNOWN 

Not sure if this is a red-herring or an indication that I did not quite follow your instructions on building ffmpeg correctly


cheers

---

### Post by endersshadow on 2007-07-29
It's not unusual w/ ffmpeg to have that version.

As for the video, does it play correctly on your computer?

---

### Post by ibelwich on 2007-07-29
Yup plays perfectly on the pc...

---

### Post by joe_bling on 2007-07-29
Enders this is a fantastic program! I got everything working fine but have one issue.

Neither the video nor audio plays when I try on my iPod.

I encoded 1min 56 secs of a DVD just fine. Plays fine on my Feisty laptop, plays fine *from* the iPod under Feisty or iTunes/WinXP w/ Quicktime. But nothing plays on the iPod, it's just a blank screen and no sound for 1min 56 secs.

80GB video iPod f/w 1.2.1 using Vive 2.0.0 and gtkPod 0.99.8. The file name is blahblahblah.mov, I used Vive iPod/PSP presets.

Any ideas?

---

### Post by ibelwich on 2007-07-29
Hey Joe,

Thats interesting I am getting the same kinda behaviour on my ipod... 60 gb firmware 1.2.1....maybe there is an issue with version of firmware on the ipod. Enders may know

---

### Post by joe_bling on 2007-07-29
ibelwich that is an odd coincidence.

I should also mention that when I try to import my .mov into the iPod via iTunes, it will not import, iTunes reports "iPod cannot play this format".

---

### Post by endersshadow on 2007-07-29
Try bumping the Audio Bitrate down to 128kbps.  I see in the tech specs that it's only allowed to play up to 160kbps, so that may be the problem.  The video codecs and bitrates all look good.

---

### Post by ibelwich on 2007-07-30
Thanks Enders,

Will give this a try and let you know how it turns out.

Cheers

---

### Post by ibelwich on 2007-08-01
Hey Enders,

Tried a couple of various options and bitrates both 160 and 128, but unfortunately no joy. I'll keep at it and see if I crack it.

Cheers

---

### Post by Ubundragon on 2007-08-01
hello guys,

first of all,i want to say im new to ubuntu and so far i managed to make my new operating system work flawlessly..but being new there are still so many things i dont understand..

i tried to install ffmpeg to encode videos for my ipod following the instructions from endersshadow but it aborts the installation all the times..

do i need to install ffmpeg first from repositories and then run the commands?
also what is a SVN version of ffmpeg and how do i get it?from what i understand this is the only version that allows me to encode videos for ipod.

sorry about the nOOb questions but i really wanna make this thing work..

thanks:)

byeeee

---

### Post by joe_bling on 2007-08-10
I've been experimenting with different bitrates etc and I cannot get anything to work on the iPod. Not sure where to go from here, unfortunately I may have to use our Windows machine.

---

### Post by endersshadow on 2007-08-10
Hey everybody, I'm actually out of town for the moment, but I'm heading back Monday and I'll get to everybody's questions upon return :)

---

### Post by joe_bling on 2007-08-13
Just an fyi, I used Handbrake to encode a DVD then transferred it to my iPod, worked perfectly. So I've established the iPod, cable, and gtkpod are all ok.

---

### Post by endersshadow on 2007-08-15
First of all, apologies on the tardiness.  I actually just got a job (woot!) and will be moving half way across the country very shortly, so things are a bit crazy.  If I don't immediately respond, that's why.  Now, no more distractions about my personal life :)

Ubundragon: What error did you get when you tried to install ffmpeg?  Once I have this, I can help you out further.

As for your question, the SVN version is just the latest version of ffmpeg, but note that *any* version of ffmpeg may be used to encode videos correctly, so long as they are compiled correctly.  An easy way to do it is just to install the [Medibuntu](http://medibuntu.org) repository and then apt-get install ffmpeg.  Life will be grand from there.

joe_bling: Can you possibly send me a sample video encoded with Handbrake?  If you need a spot to upload it, I can throw up a quick FTP, but email me at endersshadow AT users DOT sourceforge DOT net and I'll dissect it from there and see what I can do with it.  I have a feeling it's going to be something that is so simple that it ticks me off I didn't think of it before.

---

### Post by Old Pink on 2007-08-15
Vive ***always ***choosing the wrong audio channel, and I get directors commentary or german, usually. Only once seen English. 

The preview shows the right audio, the right audio is usually the first and therefore most attractive option in the list, but no, Vive goes elsewhere, and there's no option of changing channels?!

---

### Post by endersshadow on 2007-08-15
> **Old Pink said:**
> Vive ***always ***choosing the wrong audio channel, and I get directors commentary or german, usually. Only once seen English. 

The preview shows the right audio, the right audio is usually the first and therefore most attractive option in the list, but no, Vive goes elsewhere, and there's no option of changing channels?!

What's the ffmpeg output (i.e.-the terminal output)?

---

### Post by MrGreen on 2007-08-19
trying to get mp4 video on my ipod, gtkpod complains about not being complied with mp4v2 lib. 

Not sure how to fix it?

MrG

[img]http://mr-green.net/images/Screenshot-Warning.png[/img]

---

### Post by endersshadow on 2007-08-19
MrGreen, simply run this command:

```
sudo apt-get install gtkpod-aac
```

And all should be well in your world :)

---

### Post by MrGreen on 2007-08-19
I know what I did wrong I typed acc instead of aac lol

Thanks good to go ....

---

### Post by Metallinut on 2007-08-21
Can you help with an audio sync problem?  Here's the command line I'm using to convert to m4v for iTunes/iPod use:

```
ffmpeg -i "${input_file}" -f mp4 -vcodec xvid -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x180 -padtop 30 -padbottom 30 "${input_file}.m4v"
```

When the video starts, audio playback is sync'd up no problem, but it gets progressively more "off" as the video goes on.  By the end of a 50 minute video, the sound is near 2 seconds off the video...

Any ideas why this might be happening?

Thanks,

---

### Post by endersshadow on 2007-08-21
Metallinut try using the async flag.  You can get more info [here](http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html).

---

### Post by Metallinut on 2007-08-21
Thanks.  I just actually saw a difference in some of my videos.  The ones with the sync problem were actually encoded with the flag -vcodec mpeg4.  I just noticed some other videos (that I haven't watched yet) that did not exhibit the same audio sync problems.  These files were encoded with -vcodec xvid. 

I think I'll just stick with xvid, as both iTunes and the iPod both seem to play these...

---

### Post by MrGreen on 2007-08-23
Followed guide in first post of this thread now ffmpeg spits this out

```
ffmpeg: error while loading shared libraries: libavformat.so.50: cannot open shared object file: No such file or directory

```

loaded libavformat-dev but sis not help any ideas ?

---

### Post by endersshadow on 2007-08-24
Mr. Green: You'll need to edit the /etc/ld.so.conf file (using sudo), and add this line:

```
/usr/local/lib
```

Save and exit and then run this command:

```
ldconfig -v
```

All should then be well.

---

### Post by MrGreen on 2007-08-24
Man lol, worked a treat thanks... what is all that about? it is a problem with ubuntu package or svn version of ffmpeg?

MrG

---

### Post by endersshadow on 2007-08-24
I believe it's the SVN version of ffmpeg and it sometimes installs libavformat to /usr/local/lib instead of /usr/lib.  Simple enough fix, though :)

---

### Post by MrGreen on 2007-08-25
The only thing now is I can convert avi to mov but flv to mov

```
ffmpeg -i video.flv -ab 56 -ar 22050 -b 500 -s 320x240 video.mpg
```


I get .....

```
PIX_FMT_YUV420P will be used as an intermediate format for rescaling
Output #0, mov, to 'video.mov':
  Stream #0.0: Video: mpeg4, yuv420p, 320x240, q=2-31, 500 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: aac, 22050 Hz, stereo, 56 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec (id=0) for input stream #0.0

```

again vive works fine with avi.... not a problem

strange?

---

### Post by Fisslefink on 2007-08-26
I used the first post on this thread to compile ffmpeg with h.264 support, but I had the worst time trying to get ffmpeg to cooperate with nuvexport and the libfaad packages in the repository!

Finally I have things working.  If anyone else has this problem, here are the versions that worked for me:

Disabling the "debian-multimedia.org" repository from /etc/apt/sources.list was essential!

I then removed ffmpeg using:
sudo apt-get remove ffmpeg

I then installed the 8/04/2007 version of Nuvexport (installed from source):
Version 0.4 0.20070804.svn

I then installed ffmpeg r8998 from the SVN repository, as detailed in this webpage:
[http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/](http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/)

Running ffmpeg -version now gives me:
```
FFmpeg version SVN-r8998, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-libvorbis --enable-libogg --enable-liba52 --enable-libdts --enable-dc1394 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-xvid --enable-pthreads --enable-x264
  libavutil version: 49.4.0
  libavcodec version: 51.40.4
  libavformat version: 51.12.1
  built on Aug 26 2007 12:57:38, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
ffmpeg      SVN-r8998
libavutil   3212288
libavcodec  3352580
libavformat 3345409
```

and ffmpeg -formats gives me:
```
FFmpeg version SVN-r8998, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-libvorbis --enable-libogg --enable-liba52 --enable-libdts --enable-dc1394 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-xvid --enable-pthreads --enable-x264
  libavutil version: 49.4.0
  libavcodec version: 51.40.4
  libavformat version: 51.12.1
  built on Aug 26 2007 12:57:38, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
File formats:
  E 3g2             3gp2 format
  E 3gp             3gp format
 D  4xm             4X Technologies format
 D  MTV             MTV format
 DE RoQ             Id RoQ format
 D  aac             ADTS AAC
 DE ac3             raw ac3
  E adts            ADTS AAC
 DE aiff            Audio IFF
 DE alaw            pcm A law format
 DE amr             3gpp amr file format
 D  apc             CRYO APC format
 DE asf             asf format
  E asf_stream      asf format
 DE au              SUN AU Format
 DE audio_device    audio grab and output
 DE avi             avi format
 D  avs             avs format
 D  bethsoftvid     Bethesda Softworks 'Daggerfall' VID format
 D  c93             Interplay C93
  E crc             crc testing format
 D  daud            D-Cinema audio format
 D  dc1394          dc1394 A/V grab
 D  dsicin          Delphine Software International CIN format
 D  dts             raw dts
 DE dv              DV video format
 D  dv1394          dv1394 A/V grab
  E dvd             MPEG2 PS format (DVD VOB)
 D  dxa             dxa
 D  ea              Electronic Arts Multimedia Format
 DE ffm             ffm format
 D  film_cpk        Sega FILM/CPK format
 DE flac            raw flac
 D  flic            FLI/FLC/FLX animation format
 DE flv             flv format
  E framecrc        framecrc testing format
 DE gif             GIF Animation
 DE gxf             GXF format
 DE h261            raw h261
 DE h263            raw h263
 DE h264            raw H264 video format
 D  idcin           Id CIN format
 DE image2          image2 sequence
 DE image2pipe      piped image2 sequence
 D  ingenient       Ingenient MJPEG
 D  ipmovie         Interplay MVE format
 DE m4v             raw MPEG4 video format
 D  matroska        Matroska file format
 DE mjpeg           MJPEG video
 D  mm              American Laser Games MM format
 DE mmf             mmf format
  E mov             mov format
 D  mov,mp4,m4a,3gp,3g2,mj2 QuickTime/MPEG4/Motion JPEG 2000 format
  E mp2             MPEG audio layer 2
 DE mp3             MPEG audio layer 3
  E mp4             mp4 format
 D  mpc             musepack
 DE mpeg            MPEG1 System format
  E mpeg1video      MPEG video
  E mpeg2video      MPEG2 video
 DE mpegts          MPEG2 transport stream format
 D  mpegvideo       MPEG video
  E mpjpeg          Mime multipart JPEG format
 DE mulaw           pcm mu law format
 D  mxf             MXF format
 D  nsv             NullSoft Video format
  E null            null video format
 D  nut             nut format
 D  nuv             NuppelVideo format
 DE ogg             Ogg format
  E psp             psp mp4 format
 D  psxstr          Sony Playstation STR format
 DE rawvideo        raw video format
 D  redir           Redirector format
 DE rm              rm format
  E rtp             RTP output format
 D  rtsp            RTSP input format
 DE s16be           pcm signed 16 bit big endian format
 DE s16le           pcm signed 16 bit little endian format
 DE s8              pcm signed 8 bit format
 D  sdp             SDP
 D  shn             raw shorten
 D  smk             Smacker Video
 D  sol             Sierra SOL Format
  E svcd            MPEG2 PS format (VOB)
 DE swf             Flash format
 D  thp             THP
 D  tiertexseq      Tiertex Limited SEQ format
 D  tta             true-audio
 D  txd             txd format
 DE u16be           pcm unsigned 16 bit big endian format
 DE u16le           pcm unsigned 16 bit little endian format
 DE u8              pcm unsigned 8 bit format
 D  vc1             raw vc1
  E vcd             MPEG1 System format (VCD)
 D  video4linux     video grab
 D  video4linux2    video grab
 D  vmd             Sierra VMD format
  E vob             MPEG2 PS format (VOB)
 DE voc             Creative Voice File format
 DE wav             wav format
 D  wc3movie        Wing Commander III movie format
 D  wsaud           Westwood Studios audio format
 D  wsvqa           Westwood Studios VQA format
 D  wv              WavPack
 DE yuv4mpegpipe    YUV4MPEG pipe format

Codecs:
 D V    4xm
 D V D  8bps
 D V    VMware video
 DEA    aac
 D V D  aasc
 DEA    ac3
 DEA    adpcm_4xm
 DEA    adpcm_adx
 DEA    adpcm_ct
 DEA    adpcm_ea
 DEA    adpcm_ima_dk3
 DEA    adpcm_ima_dk4
 DEA    adpcm_ima_qt
 DEA    adpcm_ima_smjpeg
 DEA    adpcm_ima_wav
 DEA    adpcm_ima_ws
 DEA    adpcm_ms
 DEA    adpcm_sbpro_2
 DEA    adpcm_sbpro_3
 DEA    adpcm_sbpro_4
 DEA    adpcm_swf
 D A    adpcm_thp
 DEA    adpcm_xa
 DEA    adpcm_yamaha
 D A    alac
 DEV D  asv1
 DEV D  asv2
 D A    atrac 3
 D V D  avs
 D V    bethsoftvid
 DEV    bmp
 D V D  c93
 D V D  camstudio
 D V D  camtasia
 D V D  cavs
 D V D  cinepak
 D V D  cljr
 D A    cook
 D V D  cyuv
 D A    dca
 D V D  dnxhd
 D A    dsicinaudio
 D V D  dsicinvideo
 DES    dvbsub
 DES    dvdsub
 DEV D  dvvideo
 D V    dxa
 DEV D  ffv1
 DEVSD  ffvhuff
 DEA    flac
 DEV D  flashsv
 D V D  flic
 DEVSD  flv
 D V D  fraps
 DEA    g726
 DEV    gif
 DEA    gsm
 D A    gsm_ms
 DEV D  h261
 DEVSDT h263
 D VSD  h263i
  EV    h263p
 DEV DT h264
 DEVSD  huffyuv
 D V D  idcinvideo
 D A    imc
 D V D  indeo2
 D V    indeo3
 D A    interplay_dpcm
 D V D  interplayvideo
  EV    jpegls
 D V    kmvc
 D A    libdts
  EV    ljpeg
 D V D  loco
 D A    mace3
 D A    mace6
 D V D  mdec
 DEV D  mjpeg
 D V D  mjpegb
 D V D  mmvideo
 DEA    mp2
 DEA    mp3
 D A    mp3adu
 D A    mp3on4
 D A    mpc sv7
 DEVSDT mpeg1video
 DEVSDT mpeg2video
 DEVSDT mpeg4
 D A    mpeg4aac
 D VSDT mpegvideo
 DEVSD  msmpeg4
 DEVSD  msmpeg4v1
 DEVSD  msmpeg4v2
 D V D  msrle
 D V D  msvideo1
 D V D  mszh
 D V D  nuv
 DEV    pam
 DEV    pbm
 DEA    pcm_alaw
 DEA    pcm_mulaw
 DEA    pcm_s16be
 DEA    pcm_s16le
 DEA    pcm_s24be
 DEA    pcm_s24daud
 DEA    pcm_s24le
 DEA    pcm_s32be
 DEA    pcm_s32le
 DEA    pcm_s8
 DEA    pcm_u16be
 DEA    pcm_u16le
 DEA    pcm_u24be
 DEA    pcm_u24le
 DEA    pcm_u32be
 DEA    pcm_u32le
 DEA    pcm_u8
 DEV    pgm
 DEV    pgmyuv
 DEV    png
 DEV    ppm
 D V    ptx
 D A    qdm2
 D V D  qdraw
 D V D  qpeg
 D V D  qtrle
 DEV    rawvideo
 D A    real_144
 D A    real_288
 DEA    roq_dpcm
 D V D  roqvideo
 D V D  rpza
 DEV D  rv10
 DEV D  rv20
 DEV    sgi
 D A    shorten
 D A    smackaud
 D V    smackvid
 D V D  smc
 DEV    snow
 D A    sol_dpcm
 DEA    sonic
  EA    sonicls
 D V D  sp5x
 DEV D  svq1
 D VSD  svq3
 DEV    targa
 D V    theora
 D V D  thp
 D V D  tiertexseqvideo
 DEV    tiff
 D V D  truemotion1
 D V D  truemotion2
 D A    truespeech
 D A    tta
 D V    txd
 D V D  ultimotion
 D V    vc1
 D V D  vcr1
 D A    vmdaudio
 D V D  vmdvideo
 DEA    vorbis
 D V    vp3
 D V D  vp5
 D V D  vp6
 D V D  vp6f
 D V D  vqavideo
 D A    wavpack
 DEA    wmav1
 DEA    wmav2
 DEVSD  wmv1
 DEVSD  wmv2
 D V    wmv3
 D V D  wnv1
 D A    ws_snd1
 D A    xan_dpcm
 D V D  xan_wc3
 D V D  xl
  EV    xvid
 DEV D  zlib
 DEV    zmbv

Supported file protocols:
 file: http: pipe: rtp: tcp: udp:
Frame size, frame rate abbreviations:
 ntsc pal qntsc qpal sntsc spal film ntsc-film sqcif qcif cif 4cif
Motion estimation methods:
 zero(fastest) full(slowest) log phods epzs(default) x1 hex umh iter

Note, the names of encoders and decoders dont always match, so there are
several cases where the above table shows encoder only or decoder only entries
even though both encoding and decoding are supported for example, the h263
decoder corresponds to the h263 and h263p encoders, for file formats its even
worse
```

Finally nuvexport works properly with the "mode=ipod" in nuvexportrc!

Note that the command sudo apt-get install libfaad2-dev still gives me the following error, but ffmpeg was able to build just fine with faad support ...perhaps the r8998 version uses a different library for faad support?:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libfaad2-dev: Depends: libfaad2-0 (= 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3) but it is not going to be installed
E: Broken packages
```

For what it's worth, I did do a lot of other things while trying to get this to work, so I may have left out a critical step on this post, or perhaps included one too many.  The point is, it can be done!  Your mileage may vary.

Hope this helps someone.

---

### Post by mthaddon on 2007-08-29
Hoping someone can help out here.

I compiled from svn as follows:

```
./configure --prefix=/usr --enable-gpl --enable-pp --enable-pthreads --enable-dc1394 --enable-liba52 --enable-libfaac --enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libogg --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-shared --disable-debug
```

Here's my ffmpeg -version output:

```
FFmpeg version SVN-r10257, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-pp --enable-pthreads --enable-dc1394 --enable-liba52 --enable-libfaac --enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libogg --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-shared --disable-debug
  libavutil version: 49.5.0
  libavcodec version: 51.42.0
  libavformat version: 51.12.2
  built on Aug 28 2007 14:22:53, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
ffmpeg      SVN-r10257
libavutil   3212544
libavcodec  3353088
libavformat 3345410
```


Here's my ffmpeg -formats output:

```
FFmpeg version SVN-r10257, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-pp --enable-pthreads --enable-dc1394 --enable-liba52 --enable-libfaac --enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libogg --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-shared --disable-debug
  libavutil version: 49.5.0
  libavcodec version: 51.42.0
  libavformat version: 51.12.2
  built on Aug 28 2007 14:22:53, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
File formats:
  E 3g2             3gp2 format
  E 3gp             3gp format
 D  4xm             4X Technologies format
 D  MTV             MTV format
 DE RoQ             Id RoQ format
 D  aac             ADTS AAC
 DE ac3             raw ac3
  E adts            ADTS AAC
 DE aiff            Audio IFF
 DE alaw            pcm A law format
 DE amr             3gpp amr file format
 D  apc             CRYO APC format
 DE asf             asf format
  E asf_stream      asf format
 DE au              SUN AU Format
 DE audio_device    audio grab and output
 DE avi             avi format
 D  avs             avs format
 D  bethsoftvid     Bethesda Softworks 'Daggerfall' VID format
 D  c93             Interplay C93
  E crc             crc testing format
 D  daud            D-Cinema audio format
 D  dc1394          dc1394 A/V grab
 D  dsicin          Delphine Software International CIN format
 D  dts             raw dts
 DE dv              DV video format
 D  dv1394          dv1394 A/V grab
  E dvd             MPEG2 PS format (DVD VOB)
 D  dxa             dxa
 D  ea              Electronic Arts Multimedia Format
 DE ffm             ffm format
 D  film_cpk        Sega FILM/CPK format
 DE flac            raw flac
 D  flic            FLI/FLC/FLX animation format
 DE flv             flv format
  E framecrc        framecrc testing format
 DE gif             GIF Animation
 DE gxf             GXF format
 DE h261            raw h261
 DE h263            raw h263
 DE h264            raw H264 video format
 D  idcin           Id CIN format
 DE image2          image2 sequence
 DE image2pipe      piped image2 sequence
 D  ingenient       Ingenient MJPEG
 D  ipmovie         Interplay MVE format
 DE m4v             raw MPEG4 video format
 D  matroska        Matroska file format
 DE mjpeg           MJPEG video
 D  mm              American Laser Games MM format
 DE mmf             mmf format
  E mov             mov format
 D  mov,mp4,m4a,3gp,3g2,mj2 QuickTime/MPEG4/Motion JPEG 2000 format
  E mp2             MPEG audio layer 2
 DE mp3             MPEG audio layer 3
  E mp4             mp4 format
 D  mpc             musepack
 DE mpeg            MPEG1 System format
  E mpeg1video      MPEG video
  E mpeg2video      MPEG2 video
 DE mpegts          MPEG2 transport stream format
 D  mpegtsraw       MPEG2 raw transport stream format
 D  mpegvideo       MPEG video
  E mpjpeg          Mime multipart JPEG format
 DE mulaw           pcm mu law format
 D  mxf             MXF format
 D  nsv             NullSoft Video format
  E null            null video format
 DE nut             nut format
 D  nuv             NuppelVideo format
 DE ogg             Ogg format
  E psp             psp mp4 format
 D  psxstr          Sony Playstation STR format
 DE rawvideo        raw video format
 D  redir           Redirector format
 DE rm              rm format
  E rtp             RTP output format
 D  rtsp            RTSP input format
 DE s16be           pcm signed 16 bit big endian format
 DE s16le           pcm signed 16 bit little endian format
 DE s8              pcm signed 8 bit format
 D  sdp             SDP
 D  shn             raw shorten
 D  smk             Smacker Video
 D  sol             Sierra SOL Format
  E svcd            MPEG2 PS format (VOB)
 DE swf             Flash format
 D  thp             THP
 D  tiertexseq      Tiertex Limited SEQ format
 D  tta             true-audio
 D  txd             txd format
 DE u16be           pcm unsigned 16 bit big endian format
 DE u16le           pcm unsigned 16 bit little endian format
 DE u8              pcm unsigned 8 bit format
 D  vc1             raw vc1
  E vcd             MPEG1 System format (VCD)
 D  video4linux     video grab
 D  video4linux2    video grab
 D  vmd             Sierra VMD format
  E vob             MPEG2 PS format (VOB)
 DE voc             Creative Voice File format
 DE wav             wav format
 D  wc3movie        Wing Commander III movie format
 D  wsaud           Westwood Studios audio format
 D  wsvqa           Westwood Studios VQA format
 D  wv              WavPack
 DE yuv4mpegpipe    YUV4MPEG pipe format

Codecs:
 D V    4xm
 D V D  8bps
 D V    VMware video
 D V D  aasc
  EA    ac3
 DEA    adpcm_4xm
 DEA    adpcm_adx
 DEA    adpcm_ct
 DEA    adpcm_ea
 DEA    adpcm_ima_dk3
 DEA    adpcm_ima_dk4
 DEA    adpcm_ima_qt
 DEA    adpcm_ima_smjpeg
 DEA    adpcm_ima_wav
 DEA    adpcm_ima_ws
 DEA    adpcm_ms
 DEA    adpcm_sbpro_2
 DEA    adpcm_sbpro_3
 DEA    adpcm_sbpro_4
 DEA    adpcm_swf
 D A    adpcm_thp
 DEA    adpcm_xa
 DEA    adpcm_yamaha
 D A    alac
 DEV D  asv1
 DEV D  asv2
 D A    atrac 3
 D V D  avs
 D V    bethsoftvid
 DEV    bmp
 D V D  c93
 D V D  camstudio
 D V D  camtasia
 D V D  cavs
 D V D  cinepak
 D V D  cljr
 D A    cook
 D V D  cyuv
 D A    dca
 D V D  dnxhd
 D A    dsicinaudio
 D V D  dsicinvideo
 DES    dvbsub
 DES    dvdsub
 DEV D  dvvideo
 D V    dxa
 DEV D  ffv1
 DEVSD  ffvhuff
 DEA    flac
 DEV D  flashsv
 D V D  flic
 DEVSD  flv
 D V D  fraps
 DEA    g726
 DEV    gif
 DEV D  h261
 DEVSDT h263
 D VSD  h263i
  EV    h263p
 D V DT h264
 DEVSD  huffyuv
 D V D  idcinvideo
 D A    imc
 D V D  indeo2
 D V    indeo3
 D A    interplay_dpcm
 D V D  interplayvideo
 DEV D  jpegls
 D V    kmvc
 D A    liba52
  EA    libfaac
 D A    libfaad
 DEA    libgsm
 DEA    libgsm_ms
  EA    libmp3lame
  EV    libtheora
  EV    libx264
  EV    libxvid
  EV    ljpeg
 D V D  loco
 D A    mace3
 D A    mace6
 D V D  mdec
 DEV D  mjpeg
 D V D  mjpegb
 D V D  mmvideo
 DEA    mp2
 D A    mp3
 D A    mp3adu
 D A    mp3on4
 D A    mpc sv7
 DEVSDT mpeg1video
 DEVSDT mpeg2video
 DEVSDT mpeg4
 D A    mpeg4aac
 D VSDT mpegvideo
 DEVSD  msmpeg4
 DEVSD  msmpeg4v1
 DEVSD  msmpeg4v2
 D V D  msrle
 D V D  msvideo1
 D V D  mszh
 D V D  nuv
 DEV    pam
 DEV    pbm
 DEA    pcm_alaw
 DEA    pcm_mulaw
 DEA    pcm_s16be
 DEA    pcm_s16le
 DEA    pcm_s24be
 DEA    pcm_s24daud
 DEA    pcm_s24le
 DEA    pcm_s32be
 DEA    pcm_s32le
 DEA    pcm_s8
 DEA    pcm_u16be
 DEA    pcm_u16le
 DEA    pcm_u24be
 DEA    pcm_u24le
 DEA    pcm_u32be
 DEA    pcm_u32le
 DEA    pcm_u8
 DEA    pcm_zork
 DEV    pgm
 DEV    pgmyuv
 DEV    png
 DEV    ppm
 D V    ptx
 D A    qdm2
 D V D  qdraw
 D V D  qpeg
 DEV D  qtrle
 DEV    rawvideo
 D A    real_144
 D A    real_288
 DEA    roq_dpcm
 DEV D  roqvideo
 D V D  rpza
 DEV D  rv10
 DEV D  rv20
 DEV    sgi
 D A    shorten
 D A    smackaud
 D V    smackvid
 D V D  smc
 DEV    snow
 D A    sol_dpcm
 DEA    sonic
  EA    sonicls
 D V D  sp5x
 DEV D  svq1
 D VSD  svq3
 DEV    targa
 D V    theora
 D V D  thp
 D V D  tiertexseqvideo
 DEV    tiff
 D V D  truemotion1
 D V D  truemotion2
 D A    truespeech
 D A    tta
 D V    txd
 D V D  ultimotion
 D V    vc1
 D V D  vcr1
 D A    vmdaudio
 D V D  vmdvideo
 DEA    vorbis
 D V    vp3
 D V D  vp5
 D V D  vp6
 D V D  vp6f
 D V D  vqavideo
 D A    wavpack
 DEA    wmav1
 DEA    wmav2
 DEVSD  wmv1
 DEVSD  wmv2
 D V    wmv3
 D V D  wnv1
 D A    ws_snd1
 D A    xan_dpcm
 D V D  xan_wc3
 D V D  xl
 D S    xsub
 DEV D  zlib
 DEV    zmbv

Supported file protocols:
 file: http: pipe: rtp: tcp: udp:
Frame size, frame rate abbreviations:
 ntsc pal qntsc qpal sntsc spal film ntsc-film sqcif qcif cif 4cif

Note, the names of encoders and decoders do not always match, so there are
several cases where the above table shows encoder only or decoder only entries
even though both encoding and decoding are supported. For example, the h263
decoder corresponds to the h263 and h263p encoders, for file formats it is even
worse.
```

When I pass the following script an avi file:

```
#!/bin/bash

base=`echo $1 | gawk -F. '{print $1}' `

echo "$1 $base"

/usr/bin/ffmpeg -i $1 -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 "${base}.mov"
```

I get:

```
FFmpeg version SVN-r10257, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-pp --enable-pthreads --enable-dc1394 --enable-liba52 --enable-libfaac --enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libogg --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-shared --disable-debug
  libavutil version: 49.5.0
  libavcodec version: 51.42.0
  libavformat version: 51.12.2
  built on Aug 28 2007 14:22:53, gcc: 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Input #0, avi, from 'winston_f1553159.avi':
  Duration: 00:00:23.3, start: 0.000000, bitrate: 4465 kb/s
  Stream #0.0: Video: mjpeg, yuvj422p, 320x240, 30.00 fps(r)
  Stream #0.1: Audio: pcm_u8, 11024 Hz, mono, 88 kb/s
Unknown encoder 'aac'
```

I can't see what I've missed to get the aac encoder. Any ideas?

Thanks, Tom

---

### Post by endersshadow on 2007-08-30
Hey Tom, do you have libfaac0 installed?

---

### Post by mthaddon on 2007-08-30
yep.

```
$ aptitude search libfaac
i   libfaac-dev                                           - an AAC audio encoder - development files                        
i   libfaac0                                              - an AAC audio encoder - library files
```

---

### Post by endersshadow on 2007-08-30
Well then, that's just rather odd.  Can I suggest the [Medibuntu](http://medibuntu.org) repo and installing ffmpeg from there?

---

### Post by monitorman on 2007-09-03
I've installed Vive 2.0.0 after installing the Mediabuntu repository. 
There weren't any presets available from the drop-down menu after installation.
I tried manually configuring some of the settings, and trying a few tests. The error I receive in the terminal is always "unable to find an output format for (location of test file)"
Any help would be greatly appreciated.

---

### Post by CoriolisSTORM on 2007-09-07
having problems installing here; I downloaded the .deb file to install it and it says that I have an unsatisfiable dependency; libatk1.0-0.  I have checked and it is installed.  What do I do now?

---

### Post by HeelsFan on 2007-09-10
I was able to install ffmpeg and Vive from the instructions. However, I do not have presets in the Vive drop-down menu either. 

Can someone help me load them?

Thanks in advance.

---

### Post by HeelsFan on 2007-09-11
I figured out how to solve my preset issue:
1) Download the tar file from Sourceforge;
2) Untar; 
3) Copy the preferences file from the examples directory to your home/.vive directory (make sure you show hidden files); and
4) Restart Vive

Note this will copy over any presets that you may have manually entered.

---

### Post by monitorman on 2007-09-12
> **HeelsFan said:**
> I figured out how to solve my preset issue:
1) Download the tar file from Sourceforge;
2) Untar; 
3) Copy the preferences file from the examples directory to your home/.vive directory (make sure you show hidden files); and
4) Restart Vive

Note this will copy over any presets that you may have manually entered.

Hey! That worked for me.
Thanks!

Unfortunately, I'm still getting the "unable to find output format" error.

---

### Post by endersshadow on 2007-09-13
Hey folks, I'm really sorry about not getting right back to you.  I happen to have just moved half way across the country and just started a new job.  As one can imagine, it really interferes with my cyberlife.

As for the preferences, HeelsFan is right.  I'm upset that didn't copy over in the deb file, and I'll look into it.  It most definitely should!

monitorman: Can you tell me what settings you used?  Did you make sure the output file had an extension on it?  ffmpeg will only encode if both files have extensions (such as filename.wmv instead of just filename).

---

### Post by monitorman on 2007-09-14
> **endersshadow said:**
> 

monitorman: Can you tell me what settings you used?  Did you make sure the output file had an extension on it?  ffmpeg will only encode if both files have extensions (such as filename.wmv instead of just filename).

Hey! Glad you're back!
I'm using the preset ipod/psp settings.
No, i wasn't including an extension on the output file.
Trying that now brings up the error: ""ffmpeg: error while loading shared libraries: libavformat.so.50: cannot open shared object file.no such file or directory"

So, I'm missing some part of ffmpeg?

Thanks.

---

### Post by endersshadow on 2007-09-14
Here's the answer:

[http://ubuntuforums.org/showpost.php?p=3243712&postcount=627](http://ubuntuforums.org/showpost.php?p=3243712&postcount=627)

Edit the /etc/ld.so.conf file (using sudo), and add this line:

```
/usr/local/lib
```

Save and exit and then run this command:

```
ldconfig -v
```

All should then be well.

---

### Post by monitorman on 2007-09-14
Sorry for looking like a dumbass, but the exact commands should be...?
I've only been using Ubuntu about a month.
Thanks.

---

### Post by endersshadow on 2007-09-15
It's all right.

The commands should be:

```
sudo gedit /etc/ld.so.conf
```

Scroll to the end and type or paste in this line at the very bottom:

```
/usr/local/lib
```

Save and close GEdit.  Then run this command:

```
ldconfig -v
```

Voila :)

---

### Post by monitorman on 2007-09-17
OK. That was what I had been trying. 
I get another error:
"ldconfig: Can't create temporary cache file /etc/ld.so.cache~: Permission denied"

Thanks.

---

### Post by endersshadow on 2007-09-17
My fault, it needs to be:

```
sudo ldconfig -v
```

---

### Post by monitorman on 2007-09-18
That's got it!
Thanks for walking me through this.

Cheers!

---

### Post by katelewis on 2007-09-19
Does anyone know about video downloads to go on to website? I'm looking to put videos on my website and have come across
various ones but its hard deciding as this is new to me. One sticks out in my mind called smackbiz.biz has anyone used them before?

---

### Post by johnboyholms on 2007-09-23
Hi,

Can anyone tell me, has h264 encoding been disabled in the latest SVN/release of ffmpeg?

Looking at:

[http://ffmpeg.mplayerhq.hu/general.html#TOC6]("http://ffmpeg.mplayerhq.hu/general.html#TOC6")

It only says it is a h.264 decoder.

and when I build with:

> 
jl@id2p:~/ffmpeg$ ./configure --enable-gpl --enable-pp --disable-debug --enable-pthreads --enable-shared  --enable-liba52   --enable-dc1394        --enable-libfaac           --enable-libfaad            --enable-libgsm           --enable-libmp3lame           --enable-libogg            --enable-libtheora       --enable-libvorbis        --enable-libx264           --enable-libxvid 

and run % ffmpeg -formats I get:

> jl@id2p:~/ffmpeg$ ffmpeg -formats
FFmpeg version SVN-r10550, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --disable-debug --enable-pthreads --enable-shared --enable-liba52 --enable-libdc1394 --enable-libfaac --enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libogg --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid
  libavutil version: 49.5.0
  libavcodec version: 51.44.0
  libavformat version: 51.13.4
  built on Sep 23 2007 16:44:49, gcc: 4.1.3 20070831 (prerelease) (Ubuntu 4.1.2-16ubuntu1)
File formats:
  E 3g2             3gp2 format
  E 3gp             3gp format
 D  4xm             4X Technologies format
 D  MTV             MTV format
 DE RoQ             Id RoQ format
 D  aac             ADTS AAC
 DE ac3             raw ac3
  E adts            ADTS AAC
 DE aiff            Audio IFF
 DE alaw            pcm A law format
 DE amr             3gpp amr file format
 D  apc             CRYO APC format
 D  ape             Monkey's Audio
 DE asf             asf format
  E asf_stream      asf format
 DE au              SUN AU Format
 DE avi             avi format
 D  avs             avs format
 D  bethsoftvid     Bethesda Softworks 'Daggerfall' VID format
 D  c93             Interplay C93
  E crc             crc testing format
 D  daud            D-Cinema audio format
 D  dsicin          Delphine Software International CIN format
 D  dts             raw dts
 DE dv              DV video format
 D  dv1394          dv1394 A/V grab
  E dvd             MPEG2 PS format (DVD VOB)
 D  dxa             dxa
 D  ea              Electronic Arts Multimedia Format
 DE ffm             ffm format
 D  film_cpk        Sega FILM/CPK format
 DE flac            raw flac
 D  flic            FLI/FLC/FLX animation format
 DE flv             flv format
  E framecrc        framecrc testing format
 DE gif             GIF Animation
 DE gxf             GXF format
 DE h261            raw h261
 DE h263            raw h263
 DE h264            raw H264 video format
 D  idcin           Id CIN format
 DE image2          image2 sequence
 DE image2pipe      piped image2 sequence
 D  ingenient       Ingenient MJPEG
 D  ipmovie         Interplay MVE format
 D  libdc1394       dc1394 A/V grab
 DE m4v             raw MPEG4 video format
 DE matroska        Matroska File Format
 DE mjpeg           MJPEG video
 D  mm              American Laser Games MM format
 DE mmf             mmf format
  E mov             mov format
 D  mov,mp4,m4a,3gp,3g2,mj2 QuickTime/MPEG4/Motion JPEG 2000 format
  E mp2             MPEG audio layer 2
 DE mp3             MPEG audio layer 3
  E mp4             mp4 format
 D  mpc             musepack
 DE mpeg            MPEG1 System format
  E mpeg1video      MPEG video
  E mpeg2video      MPEG2 video
 DE mpegts          MPEG2 transport stream format
 D  mpegtsraw       MPEG2 raw transport stream format
 D  mpegvideo       MPEG video
  E mpjpeg          Mime multipart JPEG format
 DE mulaw           pcm mu law format
 D  mxf             MXF format
 D  nsv             NullSoft Video format
  E null            null video format
 DE nut             nut format
 D  nuv             NuppelVideo format
 DE ogg             Ogg format
 DE oss             audio grab and output
  E psp             psp mp4 format
 D  psxstr          Sony Playstation STR format
 DE rawvideo        raw video format
 D  redir           Redirector format
 DE rm              rm format
  E rtp             RTP output format
 D  rtsp            RTSP input format
 DE s16be           pcm signed 16 bit big endian format
 DE s16le           pcm signed 16 bit little endian format
 DE s8              pcm signed 8 bit format
 D  sdp             SDP
 D  shn             raw shorten
 D  smk             Smacker Video
 D  sol             Sierra SOL Format
  E svcd            MPEG2 PS format (VOB)
 DE swf             Flash format
 D  thp             THP
 D  tiertexseq      Tiertex Limited SEQ format
 D  tta             true-audio
 D  txd             txd format
 DE u16be           pcm unsigned 16 bit big endian format
 DE u16le           pcm unsigned 16 bit little endian format
 DE u8              pcm unsigned 8 bit format
 D  vc1             raw vc1
  E vcd             MPEG1 System format (VCD)
 D  video4linux     video grab
 D  video4linux2    video grab
 D  vmd             Sierra VMD format
  E vob             MPEG2 PS format (VOB)
 DE voc             Creative Voice File format
 DE wav             wav format
 D  wc3movie        Wing Commander III movie format
 D  wsaud           Westwood Studios audio format
 D  wsvqa           Westwood Studios VQA format
 D  wv              WavPack
 DE yuv4mpegpipe    YUV4MPEG pipe format

Codecs:
 D V    4xm
 D V D  8bps
 D V    VMware video
 D V D  aasc
  EA    ac3
 DEA    adpcm_4xm
 DEA    adpcm_adx
 DEA    adpcm_ct
 DEA    adpcm_ea
 DEA    adpcm_ima_dk3
 DEA    adpcm_ima_dk4
 DEA    adpcm_ima_qt
 DEA    adpcm_ima_smjpeg
 DEA    adpcm_ima_wav
 DEA    adpcm_ima_ws
 DEA    adpcm_ms
 DEA    adpcm_sbpro_2
 DEA    adpcm_sbpro_3
 DEA    adpcm_sbpro_4
 DEA    adpcm_swf
 D A    adpcm_thp
 DEA    adpcm_xa
 DEA    adpcm_yamaha
 D A    alac
 D A    ape
 DEV D  asv1
 DEV D  asv2
 D A    atrac 3
 D V D  avs
 D V    bethsoftvid
 DEV    bmp
 D V D  c93
 D V D  camstudio
 D V D  camtasia
 D V D  cavs
 D V D  cinepak
 D V D  cljr
 D A    cook
 D V D  cyuv
 D A    dca
 D V D  dnxhd
 D A    dsicinaudio
 D V D  dsicinvideo
 DES    dvbsub
 DES    dvdsub
 DEV D  dvvideo
 D V    dxa
 DEV D  ffv1
 DEVSD  ffvhuff
 DEA    flac
 DEV D  flashsv
 D V D  flic
 DEVSD  flv
 D V D  fraps
 DEA    g726
 DEV    gif
 DEV D  h261
 DEVSDT h263
 D VSD  h263i
  EV    h263p
 D V DT h264
 DEVSD  huffyuv
 D V D  idcinvideo
 D A    imc
 D V D  indeo2
 D V    indeo3
 D A    interplay_dpcm
 D V D  interplayvideo
 DEV D  jpegls
 D V    kmvc
 D A    liba52
  EA    libfaac
 D A    libfaad
 DEA    libgsm
 DEA    libgsm_ms
  EA    libmp3lame
  EV    libtheora
  EV    libx264
  EV    libxvid
  EV    ljpeg
 D V D  loco
 D A    mace3
 D A    mace6
 D V D  mdec
 DEV D  mjpeg
 D V D  mjpegb
 D V D  mmvideo
 DEA    mp2
 D A    mp3
 D A    mp3adu
 D A    mp3on4
 D A    mpc sv7
 DEVSDT mpeg1video
 DEVSDT mpeg2video
 DEVSDT mpeg4
 D A    mpeg4aac
 D VSDT mpegvideo
 DEVSD  msmpeg4
 DEVSD  msmpeg4v1
 DEVSD  msmpeg4v2
 D V D  msrle
 D V D  msvideo1
 D V D  mszh
 D V D  nuv
 DEV    pam
 DEV    pbm
 DEA    pcm_alaw
 DEA    pcm_mulaw
 DEA    pcm_s16be
 DEA    pcm_s16le
 DEA    pcm_s24be
 DEA    pcm_s24daud
 DEA    pcm_s24le
 DEA    pcm_s32be
 DEA    pcm_s32le
 DEA    pcm_s8
 DEA    pcm_u16be
 DEA    pcm_u16le
 DEA    pcm_u24be
 DEA    pcm_u24le
 DEA    pcm_u32be
 DEA    pcm_u32le
 DEA    pcm_u8
 DEA    pcm_zork
 DEV    pgm
 DEV    pgmyuv
 DEV    png
 DEV    ppm
 D V    ptx
 D A    qdm2
 D V D  qdraw
 D V D  qpeg
 DEV D  qtrle
 DEV    rawvideo
 D A    real_144
 D A    real_288
 DEA    roq_dpcm
 DEV D  roqvideo
 D V D  rpza
 DEV D  rv10
 DEV D  rv20
 DEV    sgi
 D A    shorten
 D A    smackaud
 D V    smackvid
 D V D  smc
 DEV    snow
 D A    sol_dpcm
 DEA    sonic
  EA    sonicls
 D V D  sp5x
 DEV D  svq1
 D VSD  svq3
 DEV    targa
 D V    theora
 D V D  thp
 D V D  tiertexseqvideo
 DEV    tiff
 D V D  truemotion1
 D V D  truemotion2
 D A    truespeech
 D A    tta
 D V    txd
 D V D  ultimotion
 D V    vc1
 D V D  vcr1
 D A    vmdaudio
 D V D  vmdvideo
 DEA    vorbis
 D V    vp3
 D V D  vp5
 D V D  vp6
 D V D  vp6f
 D V D  vqavideo
 D A    wavpack
 DEA    wmav1
 DEA    wmav2
 DEVSD  wmv1
 DEVSD  wmv2
 D V    wmv3
 D V D  wnv1
 D A    ws_snd1
 D A    xan_dpcm
 D V D  xan_wc3
 D V D  xl
 D S    xsub
 DEV D  zlib
 DEV    zmbv

Supported file protocols:
 file: http: pipe: rtp: tcp: udp:
Frame size, frame rate abbreviations:
 ntsc pal qntsc qpal sntsc spal film ntsc-film sqcif qcif cif 4cif

Note, the names of encoders and decoders do not always match, so there are
several cases where the above table shows encoder only or decoder only entries
even though both encoding and decoding are supported. For example, the h263
decoder corresponds to the h263 and h263p encoders, for file formats it is even
worse.


If encoding has been disabled does anyone know why? and another way to encode video for an ipod on linux?

Or any other advice would be greatly appreciated.

BTW I am using gutsy.

Thanks in advance

John

---

### Post by endersshadow on 2007-09-23
I don't know, I haven't installed/tested Gutsy.  However, you can encode it with the mov format, mpeg4 video and mp3 audio for the codecs.

---

### Post by johnboyholms on 2007-09-23
> **endersshadow said:**
> I don't know, I haven't installed/tested Gutsy.  However, you can encode it with the mov format, mpeg4 video and mp3 audio for the codecs.

Hi ,

I got it working with the gutsy ffmpeg source

apt-get source ffmpeg

However as I mentioned earlier the latest SVN of ffmpeg seems to me to not include h264 as an encoder. 

Yes, I could encode mov format, mpeg4 video and mp3 audio for the codecs.

I do hope they haven't dropped H264 encoding from ffmpeg.

---

### Post by TutoWRM on 2007-09-25
ohhhhh I finally got it to work!!!!!!!
after a day of compiling over and over the svn for ffmpeg and read this and many other webs, the error of the encoder aac, was because now it's libfaac (i know pretty stupid not to noticed before), so i've change that in the command line of ipodvidenc and another problem came up, the wrong timebase for mpeg4...... so.... after a few hours, i've finnaly got this command line to work:

ffmpeg -i "${input_file}" -f mp4 -vcodec mpeg4 -b 700k -aspect 4:3 -r 23.98 -s 320x240 -acodec libfaac -ar 48000

so i hope that works for you, because i spent all of my day trying to get it right :/

---

### Post by Sammi on 2007-10-03
> **Trini45 said:**
> Hmm... i tried **MelodyCan** converter. Few mouse clicks and I can enjoy my lovely video. Number of conversions at a time is 8-12 files. It`s very good, quickly and comfortable to use.
This smells like a malware advertisement. That's a Windows app and this is a Linux forum.

---

### Post by spockrock on 2007-10-07
I am wondering if anyone here has solved this problem but I am using fesity but all the videos I encode with vive have no sound on both my iphone and ipod video.  Any one here found a fix, is this an ffmpeg issue?

---

### Post by atlfalcons866 on 2007-10-11
i get this using gutsy

Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.
Use of uninitialized value in pattern match (m//) at /usr/bin/vive line 368.

---

### Post by Metallinut on 2007-10-24
I just upgraded from Fiesty to 7.10 Gutsy.

ffmpeg ceased working in creating iPod videos, I assume because ffmpeg got updated, and my custom built one got overwritten.  So I uninstalled ffmpeg, and followed the steps on the first page of this thread to reinstall it.

When I try to encode a video I get the following: 
Unknown encoder 'xvid'

Now I made sure to --enable-libxvid (it's listed at the beginning when ffmpeg is run)

I've also verified that libxvidcore4-dev is installed, and is the most current version...

Any idea why ffmpeg doesn't recognize my xvid codec?

---

### Post by 3rdalbum on 2007-10-25
I am trying this program for use with my Sony MP3/Video Walkman... if it works, I'll be forever grateful!

---

### Post by woodsdog on 2007-10-25
Guys,

I don't know if these will help anyone, but I've been tinkering around with my iPhone and created some bash scripts that will help encode video to the iPhone and the PSP.  They aren't anything super fancy, but some friends of mine and me find them useful. 

They do depend on a working version of ffmpeg compiled with x264, libfaac, and xvid. They also rely upon AtomicParsley to tag the meta data correctly.

These scripts do a 2-pass encode on them.

I have started a Google Code project, and have placed them there.   You can find it here:

[http://code.google.com/p/vs4p/](http://code.google.com/p/vs4p/)

I'd be interested to see if anyone finds them useful or has suggestions for improvements.   If this isnt a good place to discuss, I can start a new thread.

Thanks

Woody

---

### Post by j0ehill on 2007-10-27
> **Metallinut said:**
> I just upgraded from Fiesty to 7.10 Gutsy.

ffmpeg ceased working in creating iPod videos, I assume because ffmpeg got updated, and my custom built one got overwritten.  So I uninstalled ffmpeg, and followed the steps on the first page of this thread to reinstall it.

When I try to encode a video I get the following: 
Unknown encoder 'xvid'

Now I made sure to --enable-libxvid (it's listed at the beginning when ffmpeg is run)

I've also verified that libxvidcore4-dev is installed, and is the most current version...

Any idea why ffmpeg doesn't recognize my xvid codec?

Try with 'libxvid' instead of 'xvid'. A lot of the syntax has changed in recent ffmpeg versions, for example for -acodec you now need to do 'libfaac', not 'aac'.

ie. ffmpeg -i inputfile -vcodec libxvid -acodec libfaac

---

### Post by j0ehill on 2007-10-27
Not sure if this has already come up, but the script needs to be corrected for recent revisions of ffmpeg. For -acodec, it should now be 'libfaac', and for the various bitrates you now need to add 'kb'.

I've modified it a bit for my own personal use, but here is how it looks for me:

```

ffmpeg -i "${input_file}" -f mp4 -vcodec mpeg4 -b 1200kb -qmin 3 -qmax 5 -g 300 -acodec libfaac -ab 192kb -s 320x180 -aspect 16:9 "${output_dir}/${output_file_name}.mp4"

```

I put together a batch encoding version which is not interactive, goes like this:

```

for i in *.avi; do ffmpeg -i $i -f mp4 -vcodec mpeg4 -b 1200kb -qmin 3 -qmax 5 -g 300 -acodec libfaac -ab 192kb -s 320x180 -aspect 16:9 `basename $i .avi`.encoded.mp4; done;

```

I've taken out the maxrate part, which does not seem to be necessary, and mine is customized for 16:9 videos, so major YMMV here. There is a version of the command for ipod video on the ffmpeg FAQ which produces higher quality output without a really huge increase in the file size [here](http://ffmpeg.mplayerhq.hu/faq.html#SEC18).

Hope this helps somebody!

---

### Post by mukiex on 2007-10-30
I'm getting the "Unknown Codec" error even when I swap to libfaac. I got it when I installed ffmpeg under Ubuntu (Gutsy) and I even got it after I upgraded ffmpeg with the Medibuntu repository. It just says,

Unknown codec 'libfaac'

---

### Post by dm1024 on 2007-11-08
I've built a package using checkinstall.
You can try it: [http://dmitry.shaposhnik.name/misc/ffmpeg_20071107-1_i386.deb](http://dmitry.shaposhnik.name/misc/ffmpeg_20071107-1_i386.deb)

This is trunk, checked out yesterday. Hope it will be useful.
Btw, you need to install libfaac0 package from ubuntu's repository.

I've converted video for my iPod using this command:

ffmpeg -i "$file" -f mp4 -vcodec mpeg4 -b 700k -aspect 4:3 -r 23.98 -s 320x240 -acodec libfaac -ar 48000 "$file.mp4"

And than transfered to iPod using iTunes. All files except one was transfered successfully, just one was failed with words "iPod will not be able to play this video, so it was not transfered". This video was converted than with iTunes and after that uploaded well.

---

### Post by fululian on 2007-11-10
> **dm1024 said:**
> 

ffmpeg -i "$file" -f mp4 -vcodec mpeg4 -b 700k -aspect 4:3 -r 23.98 -s 320x240 -acodec libfaac -ar 48000 "$file.mp4"



i used this command or the regular script by endersshadow (or the gui), and am able to convert small files and put them onto the ipod. however, whenever i try this out with a larger file (movie, series), i get this message each time:

> FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Oct  1 2007 21:28:55, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Casino: I/O error occured
Usually that means that input file is truncated and/or corrupted.


regardless of the specific file. does anyone have a hint? thanks :(

---

### Post by d00by on 2007-11-11
I am running AMD 64 bit ubuntu gutsy. Are the instructions same for installing on that platform??

---

### Post by fululian on 2007-11-11
it seems vive or its ffmpeg doesn't support

> AC-3 Audio, because the output reads

> Unsupported codec(id=86020) for input stream #0.1

for an AC-3 audio encoded file.

is there any possibility to change this?

thanks a lot

---

### Post by fululian on 2007-11-11
> **Metallinut said:**
> I just upgraded from Fiesty to 7.10 Gutsy.

ffmpeg ceased working in creating iPod videos, I assume because ffmpeg got updated, and my custom built one got overwritten.  So I uninstalled ffmpeg, and followed the steps on the first page of this thread to reinstall it.

When I try to encode a video I get the following: 
Unknown encoder 'xvid'

Now I made sure to --enable-libxvid (it's listed at the beginning when ffmpeg is run)

I've also verified that libxvidcore4-dev is installed, and is the most current version...

Any idea why ffmpeg doesn't recognize my xvid codec?

i had this issue too, until i found out that there is now a "risky"-dubbed package in the repositories, where you can get a fully-fledged-medibuntu-powered ffmpeg. did you try this one on? the feisty-how-tos featurin ffmpeg didn't work on my gutsy.

bye

---

### Post by d00by on 2007-11-12
I am getting the following error. what am I missing here? I have amd 64 gutsy.

```
:~/ffmpeg$ ./configure --prefix=/usr --enable-gpl --enable-pp --enable-pthreads --enable-dc1394 --enable-liba52 --enable-libfaac \
> --enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libogg --enable-libtheora --enable-libvorbis \
> --enable-libx264 --enable-libxvid --enable-shared --disable-debug
Unknown option "--enable-dc1394".
See ./configure --help for available options.

```

---

### Post by fululian on 2007-11-12
(the opinion leader on this topic obviously being endersshadow, but here we try to go:)

why, you should just leave the "unknown function" out of the ./configure! since you're a gutsy user, why don't you just retrieve the "risky" package from the repositories (medibuntu/universe)?

greets

---

### Post by d00by on 2007-11-12
How do I 'retrieve' risky package? I went in synaptic. there was no such package.

Unable to use  option,*--enable-dc1394 ,--enable-libogg, liba52 * with ./configure.

When I install ffmpeg without using this option and then try to install vive I get the following error when I give *sudo make install* command in vive directory


> :~/vive-2.0.0$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ffmpeg... yes
checking for vobcopy... yes
checking for mplayer... yes
checking whether DVD is enabled... yes
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... yes (version 2.12.0)
checking pkg-config is at least version 0.9.0... yes
checking for libgnome... configure: error: Package requirements (libgnome-2.0 >= 2.0) were not met:

No package 'libgnome-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables libgnome_CFLAGS
and libgnome_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


---

### Post by fululian on 2007-11-12
well, simply look into the repositories, "search" for **ffmpeg** and you'll get this one - ffmpeg - 3:0.cvs20070307-5ubuntu4+medibuntu1 - description:

> multimedia player, server and encoder
This package contains the ffplay multimedia player, the ffserver streaming
server and the ffmpeg audio and video encoder. They support most existing
file formats (AVI, MPEG, OGG, Matroska, ASF...) and encoding formats (MPEG,
DivX, MPEG4, AC3, DV...). 

[SIZE="3"]This package is built with the "risky" option, to enable mp3/mp4/h264/amr
support.[/SIZE] Therefore, it is in Medibuntu as it might violate patents.

This package isn't supported by Ubuntu: DON'T REPORT BUGS TO UBUNTU!

Please report any bug to our bug tracker instead:
 [https://bugs.launchpad.net/medibuntu/+bugs](https://bugs.launchpad.net/medibuntu/+bugs)

do you get the same when browsing your repos?

bye

---

### Post by randomphrase on 2007-11-19
> **mukiex said:**
> I'm getting the "Unknown Codec" error even when I swap to libfaac. I got it when I installed ffmpeg under Ubuntu (Gutsy) and I even got it after I upgraded ffmpeg with the Medibuntu repository. It just says,

Unknown codec 'libfaac'

Same here, having a hell of a time finding a solution. Searching doesn't seem to be turning up anything useful:

Installed ffmpeg from medibuntu? Yes
aac appears in ffmpeg -formats? Yes
Using the -acodec libfaac command line option? Yes
libavcodec1d installed from medibuntu? Yes

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Nov 17 2007 21:14:42, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
```

Any ideas appreciated.

---

### Post by kryrinn on 2007-11-24
Newbie here...  I have libraw1394-dev installed (as it seemed to appear in an earlier post in this thread was necessary)

This is what I get:

ffmpeg: error while loading shared libraries: libraw1394.so.5: cannot open shared object file: No such file or directory

---

### Post by mukiex on 2007-11-25
randomphrase :
Your post just fixed it for me, and this is gonna piss you off beyond recognition :
I installed libavcodec1d and it installed a bunch of stuff. However, "-acodec libfaac"  still didn't work. Guess what?

**Change libfaac back to aac**. It's in /usr/local/thinliquidfilm/main.py if you're using TLF. Now it effin' works just fine. ERGG.

---

### Post by randomphrase on 2007-11-26
> **mukiex said:**
> randomphrase :
Your post just fixed it for me, and this is gonna piss you off beyond recognition :
I installed libavcodec1d and it installed a bunch of stuff. However, "-acodec libfaac"  still didn't work. Guess what?

**Change libfaac back to aac**. It's in /usr/local/thinliquidfilm/main.py if you're using TLF. Now it effin' works just fine. ERGG.

Ah. Thanks, that works for me.

Also -vcodec h264 is required instead of -vcodec libx264 in my case.

I ended up compiling ffmpeg myself to get around the problem. In the latest svn sources it looks like they reverted the change so that in the next upgrade to ffmpeg we'll be back to using -acodec libfaac again... :(

---

### Post by buildid on 2007-12-06
[http://h264enc.sourceforge.net/]("http://h264enc.sourceforge.net/")

This script works verry well for the ipod nano, i already have done some files well dvd tp ipod nano format

---

### Post by kahuuna on 2007-12-30
> **buildid said:**
> [http://h264enc.sourceforge.net/]("http://h264enc.sourceforge.net/")

This script works verry well for the ipod nano, i already have done some files well dvd tp ipod nano format

Thank this is the very thing I was looking for to transcode my large videos off my Canon camera into something more compressed. Now if I could only figure out how to batchencode them from a certain directory by fetching the avis recursively from folders inside...

---

### Post by samk on 2008-01-03
Hi, 
I built vive from the svn, and it seems that it does not change the resolution of the output to what is specified in the preferences. ipodvidenc does in fact when i run it against the same vob file. Vive does encode the video, I can import the file into itunes but i cant sync the file to my ipod. I believe it may be because the .mp4 file is at at 720x480.
BTW it's an ipod classic i'm working with. Thanks for any info.

Great Program

sam

---

### Post by reclusivemonkey on 2008-01-05
Followed instructions on the front page. When trying make from source (for Vive), not the betas, I get;
```

monkey@mother:~/vive-2.0.0$ make
make  all-recursive
make[1]: Entering directory `/home/monkey/vive-2.0.0'
Making all in src
make[2]: Entering directory `/home/monkey/vive-2.0.0/src'
gcc  -g -O2 -D PREFIX=\"/usr\" -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12   -DORBIT2=1 -pthread -I/usr/include/libgnome-2.0 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0   -DORBIT2=1 -pthread -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/gail-1.0 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/libpng12   -pthread -DORBIT2=1 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -o vive error.o interface.o options.o preferences.o presets.o combo_menus.o encode.o dvd.o tooltips.o vive.o  -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0 -lcairo -lX11 -lXfixes -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   -pthread -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lgmodule-2.0 -ldl -lORBit-2 -lgthread-2.0 -lrt -lgobject-2.0 -lglib-2.0   -pthread -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomevfs-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lart_lgpl_2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lpango-1.0 -lcairo -lX11 -lXfixes -lgconf-2 -lgmodule-2.0 -ldl -lORBit-2 -lgthread-2.0 -lrt -lgobject-2.0 -lglib-2.0   -pthread -lgnomevfs-2 -lgconf-2 -lgmodule-2.0 -ldl -lORBit-2 -lgthread-2.0 -lrt -lgobject-2.0 -lglib-2.0   -lvte
combo_menus.o: In function `populate_ffmpeg':
/home/monkey/vive-2.0.0/src/combo_menus.c:38: undefined reference to `av_register_all'
/home/monkey/vive-2.0.0/src/combo_menus.c:50: undefined reference to `first_oformat'
/home/monkey/vive-2.0.0/src/combo_menus.c:50: undefined reference to `first_oformat'
/home/monkey/vive-2.0.0/src/combo_menus.c:50: undefined reference to `first_avcodec'
/home/monkey/vive-2.0.0/src/combo_menus.c:94: undefined reference to `first_avcodec'
collect2: ld returned 1 exit status
make[2]: *** [vive] Error 1
make[2]: Leaving directory `/home/monkey/vive-2.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/monkey/vive-2.0.0'
make: *** [all] Error 2
```

Any advice? Currently I find it a hell of a lot easier to boot into Windows to manage my iPod as gtkpod won't let me import any album art (asked on the thread and no replies) and without this working I can't get any videos on. I'm seriously thinking of saving for a Mac Mini now as Gutsy just isn't cutting it for me any more.

---

### Post by orgyn on 2008-01-05
thx very much for this, it worked great!

---

### Post by Bokonon on 2008-01-07
This has really worked well for me.  I use the script, but installed the necessary programs separately.

My videos look & sound very good on my Nano 3G with your default settings, plus the size is acceptable.  230-430 MB per DVD.

I tried the other script linked here, which gives you a lot more power, but the files end up larger and for me it is a bit of an overload of options.  For power users, that might be a better option, but for me, I like this script and the KISS principle applies.

---

### Post by m4cks on 2008-01-12
/home/maxx/vive-2.0.0/src/combo_menus.c:38: undefined reference to `av_register_all'
/home/maxx/vive-2.0.0/src/combo_menus.c:50: undefined reference to `first_oformat'
/home/maxx/vive-2.0.0/src/combo_menus.c:50: undefined reference to `first_oformat'
/home/maxx/vive-2.0.0/src/combo_menus.c:50: undefined reference to `first_avcodec'
/home/maxx/vive-2.0.0/src/combo_menus.c:94: undefined reference to `first_avcodec'


I have libavformat (and libavformt-dev) and libavcodec (and libavcodec-dev) install AND as was recommended previously, I compiled ffmpeg from latest svn using --enabled-shared.

it's just not linking on gutsy. any info is appreciated.

---

### Post by jak-_- on 2008-01-13
mpeg4ip never seems to compile on any version, need it for libmp4v2 which is needed for gtkpod to be able to sync .mp4 videos... Any ideas?

```
./../include/grayc.hpp:106: error: extra qualification 'CU8Image::' on member 'upsampleForSpatialScalability'
./../include/grayc.hpp:115: error: extra qualification 'CU8Image::' on member 'upsampleSegForSpatialScalability'
./../include/vopses.hpp:813: error: extra qualification 'CVideoObject::' on member 'filterCodedPictureForRRV'
make[6]: *** [sys_block.lo] Error 1
make[6]: Leaving directory `/home/meez/sources/mpeg4ip-1.4.1/common/video/iso-mpeg4/src'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/meez/sources/mpeg4ip-1.4.1/common/video/iso-mpeg4'
make[4]: *** [all] Error 2
make[4]: Leaving directory `/home/meez/sources/mpeg4ip-1.4.1/common/video/iso-mpeg4'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/meez/sources/mpeg4ip-1.4.1/common/video'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/meez/sources/mpeg4ip-1.4.1/common'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/meez/sources/mpeg4ip-1.4.1'
make: *** [all] Error 2

```

---

### Post by Sweetrelease on 2008-01-13
ok, i got it working, but is there a way to add the ```
MP4Box -add videofile.mov videofile.mov
```
to the ipodvidenc script so its all done in one sweep

---

### Post by rshel on 2008-01-22
The audio codec options do not show aac or mp3 as choices.  Am I doing something wrong?
Thanks!

---

### Post by rshel on 2008-01-23
Temporarily lost all sound on Ubuntu until removing Vive and ffmpeg folder created in home folder.  What?

---

### Post by money2themax on 2008-01-28
i want to convert .Divx to .mp4 for an ipod 5.5G 30GB White Firmware 1.2.1

i also have the newest Rockbox for this iPod

---

### Post by money2themax on 2008-01-28
bump

---

### Post by mocha on 2008-01-29
I find that by far the easiest way to convert anything to Ipod compatible formats is with an ffmpeg frontend called WinFF.  Search for it.  The author BiggMatt has made a number of presets for Ipod, and there are some members of the WinFF forum that have posted numerous presets as well.  You can create your own very easily.  WinFF also allows you to enter overrides for things like bitrate, aspect ratio, sampling frequency, etc.  The latest version supports drag and drop and even adds the "-threads 2" for dual core processors in the preferences.  The frontend is good for any general conversion with ffmpeg, it has presets for everything, DVD, wmv, xvid, audio, etc.  This is the only stable frontend I have found for ffmpeg.  If I need to use mencoder I use ThinLiquidFilm or h264enc (for single files).  Everything else I tried crashes too easily or isn't intuitive enough to produce the correct options for a particular format.

---

### Post by money2themax on 2008-01-29
ferpict lol:KS

---

### Post by bttb on 2008-02-02
For the task of converting videos for your iPod there's also avi2mp4.sh.

Requirements:

- coreutils
- bc calculator
- findutils
- faac audio encoder
- mplayer (with support for your input files)
- mencoder (with x264 support)
- aacgain (to ReplayGain the audio; you should at least have v1.7.0)
- MP4Box (part of the gpac suite; v0.4.4 or later required)

It's a batch encoder. The user simply sets the configuration and then runs the script on as many videos as he/she likes. All one needs to know is in the script's comments.

Hope you give it a shot: [Link](http://www.vdr-portal.de/board/thread.php?threadid=73188)

Regards
bttb

---

### Post by kaiesh on 2008-02-03
Hi,

I followed this tutorial to obtain the SVN version of ffmpeg and tried to encode files for my gf's ipod touch - I found that it didn't work right out of the box...

Once I tweaked it a little bit, I found that I could encode video successfully, but there was no audio playback on her ipod - irrespective of whether or not it was properly imported by itunes.

After some head bashing ](*,), I figured out that the file I was encoding from had an audio track of 5.1 dolby, and the ipod only supports stereo :-P

So, incase this helps anyone else out there, I modded the ./configure command for the **[COLOR="Red"]SVN version of ffmpeg[/COLOR]** to read as follows (all other surrounding commands are the same):
```
./configure --prefix=/usr --enable-gpl --enable-pp --enable-pthreads --enable-libdc1394 --enable-liba52 --enable-libfaac --enable-libfaad --enable-libgsm --enable-libmp3lame --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-shared --disable-debug --enable-encoder=aac --enable-encoder=x264 --enable-encoder=msmpeg4v2 --enable-encoder=msmpeg4v3 --enable-encoder=libfaac

```

and I also modded the ipodvidenc file to address the complaints ffmpeg was giving me about bitrates being in bits and not Kbits, the wrong libraries being used, and also to support conversion that **forced audio into stereo**, as well as maintained aspect ratios (i.e. adds black padding bars so people don't look stretched tall). As a consequence there is one more flag in the ffmpeg command, and it asks a couple more questions. The ipodvidenc file I use, now reads as follows:

```
#!/bin/bash
## ipodvidenc - The iPod Video Encoder for Linux.
## Created by Eric Hewitt, January 9, 2006.
## Modified by Kaiesh Vohra, February 3, 2008.
## Released under the GPL.  Go nuts.

input_file=$1

echo "What would you like to name the output file (sans extension)?"

read output_file_name

echo "$output_file_name will be located in $PWD. Is this acceptable? [y/n]"

read output_file_loc_permis

if [ $output_file_loc_permis = 'n' ] || [ $output_file_loc_permis = 'N' ]
then
	echo "Where would you like to store $output_file_name.mov?"
	read output_dir
else
	output_dir=$PWD
fi

echo "What height do you want the video to be? Remember that you need to determine this by calculating 240/(orig width/orig height)..."
read new_height

echo "How much padding do you want on the top? Best would be (240 - new height)/2..."
read padding_top

echo "How much padding do you want on the bottom? Best would be (240 - new height)/2..."
read padding_btm

ffmpeg -i "${input_file}" -f mp4 -vcodec mpeg4 -maxrate 1024000 -b 716800 -qmin 3 -qmax 5 -bufsize 4194304 -g 300 -acodec libfaac -ab 196608 **[COLOR="Red"]-ac 2[/COLOR]** -s "320x${new_height}" -padtop "${padding_top}" -padbottom "${padding_btm}" -aspect 4:3 "${output_dir}/${output_file_name}.mp4"

```

Special thanks to the guys that put this thread together, it was HUGELY useful!

But, like I said - hope my little mod helps someone!
:popcorn:

---

### Post by bdw on 2008-03-13
I get the following error when I try to encode an MP4 from a VOB file, apparently it's missing a codec but I'm not sure which one:
```

ffmpeg -y -vcodec mpeg4 -b 700k -aspect 16:9 -s 320x180 -acodec aac -ac 2 -ab 192k -comment "Encoded by Vive" -i "/home/bdw/vive_dvd_temp1-1.vob" "/home/bdw/test.mp4"

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

Seems stream 0 codec frame rate differs from container frame rate: 29.97 (30000/1001) -> 59.94 (60000/1001)
Input #0, mpeg, from '/home/bdw/vive_dvd_temp1-1.vob':
  Duration: 00:03:00.1, start: 0.045500, bitrate: 180763 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480, 7500 kb/s, 59.94 fps(r)
  Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5:1, 384 kb/s
  Stream #0.2[0x81]: Audio: ac3, 48000 Hz, mono, 192 kb/s
  Stream #0.3[0x83]: Audio: ac3
Output #0, mp4, to '/home/bdw/logansrun.mp4':
  Stream #0.0: Video: mpeg4, yuv420p, 720x480, q=2-31, 700 kb/s, 59.94 fps(c)
  Stream #0.1: Audio: aac, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

```

Needless to say, this is driving me bonkers as I can't figure out what's missing on my system. :-(

---

### Post by mocha on 2008-03-13
I think you need to do -acodec libfaac instead of -acodec aac

---

### Post by bdw on 2008-03-15
> **mocha said:**
> I think you need to do -acodec libfaac instead of -acodec aac

I gave that a shot but I got the "unknown codec" error.  libfaac is enabled in the ffmpeg build so it appears that I'll need to take a different approach.

---

### Post by itsdaveperdue on 2008-03-18
Sorry, maybe I'm late to the party.  Have you tried handbrake?  It's pretty straightforward.

HandBrake CLI Guide: [http://trac.handbrake.fr/wiki/CLIGuide]("http://trac.handbrake.fr/wiki/CLIGuide")

HandBrake Download Page (including Linux download): [http://handbrake.fr/?article=download]("http://handbrake.fr/?article=download")

There is a handbrake gui called HandBrake GTK, but it apparently isn't an official part of HandBrake and is based on old code.  It looks like they're working on a QT gui, but he CLI is super easy to use.

---

### Post by WrathofthePenguin on 2008-03-22
Ok, I've been having all kinds of fun trying to get Vive installed. When I run the ./configure, I had to use the disable-dvd flag because of the new version of libdvdcss being out. Now, when I run the command:

./configure --prefix=/usr --disable-dvd

The last few lines look like this, so I don't think there's a problem with this:

config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating doc/Makefile
config.status: creating doc/C/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands


However, when I run make, I get:

combo_menus.o: In function `populate_ffmpeg':
/home/glenn/Desktop/vive-2.0.0/src/combo_menus.c:38: undefined reference to `av_register_all'
/home/glenn/Desktop/vive-2.0.0/src/combo_menus.c:50: undefined reference to `first_oformat'
/home/glenn/Desktop/vive-2.0.0/src/combo_menus.c:50: undefined reference to `first_oformat'
/home/glenn/Desktop/vive-2.0.0/src/combo_menus.c:50: undefined reference to `first_avcodec'
/home/glenn/Desktop/vive-2.0.0/src/combo_menus.c:94: undefined reference to `first_avcodec'
collect2: ld returned 1 exit status
make[2]: *** [vive] Error 1
make[2]: Leaving directory `/home/glenn/Desktop/vive-2.0.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/glenn/Desktop/vive-2.0.0'
make: *** [all] Error 2


What am I missing here?

Thanks!

---

### Post by RJ Hythloday on 2008-04-05
I haven't read all 51 pages yet, but I"m hoping someone can help me get started.

We got my daughter a 6th gen nano and she wants youtube vid's on it.

I've dl some from here [http://www.tubeleecher.com/](http://www.tubeleecher.com/)

and renamed them as they dl to the desktop

installed gtkpod the ipod is mounted, I can access the folders etc, 

tried to add some vids through gtkpod and got this > The following track could not be processed (filetype unknown): '/home/bob/Amy_youtube_downloads/Best_of_Gir' ** same thing for all**Do I have to reencode them? I'm not sure I've got everything set up right, but she's really anxious to get it working, and I don't want to resort to itunes and a dual boot. help please!

---

### Post by esc1 on 2008-04-08
I finally got ffmpeg installed after hours, but now I can't start converting anything b/c I can't even play vids now from the winff frontend..  the error msg I get is

 failed to play /usr/bin/ffplay : 127

anyone know what the problem is?

---

### Post by Hotz on 2008-04-15
Thanks For good program

---

### Post by DakoCwerf on 2008-06-05
well, here is how i've done that for ubuntu hardy 8.04

dl ffmpeg
```
sudo apt-get build-dep ffmpeg
sudo apt-get source ffmpeg
cd ffmpeg-*
```

now my configure line (yes, you need to do it with sudo)
```
sudo ./configure --enable-gpl --enable-pp --enable-libvorbis --enable-libogg --enable-liba52 --enable-libdts --enable-dc1394 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-xvid --enable-pthreads --enable-shared
```
if you are missing some of the libs - just sudo apt-get them (dev versions also)

then
```
sudo make && sudo make install
```

then just create a script like it was said in 1st post I will just quote it now

> [size=5]**ipodvidenc Script**[/size]

And last, but certainly not least, you can create a script for converting your videos to iPod Video format.

```
gedit
```

This should pop up a blank document. Now, just copy and paste this code into it:

```
#!/bin/bash
## ipodvidenc - The iPod Video Encoder for Linux.
## Created by Eric Hewitt, January 9, 2006.
## Released under the GPL.  Go nuts.

input_file=$1

echo "What would you like to name the output file (sans extension)?"

read output_file_name

echo "$output_file_name will be located in $PWD. Is this acceptable? [y/n]"

read output_file_loc_permis

if [ $output_file_loc_permis = 'n' ] || [ $output_file_loc_permis = 'N' ]
then
	echo "Where would you like to store $output_file_name.mov?"
	read output_dir
else
	output_dir=$PWD
fi

ffmpeg -i "${input_file}" -f mp4 -vcodec mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 "${output_dir}/${output_file_name}.mov"
```

Save as ipodvidenc in your present working directory (it will be moved, anyway).  Back in the terminal, run:

```
chmod 755 ipodvidenc
sudo mv ipodvidenc /usr/bin
```

Now, when you want to encode a video to iPod format, run this command:

```
ipodvidenc video.avi
```

It will run you through a few prompts and then encode the video.  You can now use gtkpod to upload the video onto your iPod just like you load mp3's onto it.

after that you can transfer it and watch. don't be scared if you run it on your ubuntu - it will have color problems (mine had all the video a little to the blue). on the ipod it was ok.

hope this helps you.

---

### Post by dmrx24 on 2008-06-16
Are there any other decent alternatives to ffmpeg?  I am using Hardy 64bit.

---

### Post by bobandiara on 2008-06-19
Hello, guys!
There is a much simpler way, though it takes a lot longer.
If you have a video file in avi, or mpeg formats, you can use Avidemux (*sudo apt-get install avidemux*) to convert it to the format the iPod understands. It helps a lot if you have the proper codecs (w32codecs and all...) to do that.

First of all, open Avidemux. It is found in your Sound And Video (or whatever is the name in english - I'm a brazilian Ubuntu user :p) menu entry. Then, open the desired file. It may ask you a few questions, like "Rebuild time frame?" and/or "create index?" and many others. Just click "yes", it will help in the final quality of the (re)encoded media.

After that, click on the "Auto" menu, select "IPOD (mpeg4)". A dialog box will popup. If you want, you can change some settings or just leave them be. Click ok.

On the left panel, set video to "MPEG-4 ASP (Xvid4)" and audio to "AAC (FAAC)". If it is your wish, you may change the audio and video settings by clicking the configure button on the respective options, but it is not necessary. Change the format option to "MP4".

After all this, click the save button, define your target directory, the target file name. I recommend the .mp4 extension, to avoid confusion.

Sit down, grab a cup of coffee, tea, beer or whatever you like, and wait for the little brat to do the dirty job ;).

Then, finally, if you haven't done it yet, "sudo apt-get install gtkpod-aac easytag-aac".

"Easytag?", one might ask. Yes, the "easytag-aac" package has support for editing mp4/m4a/aac tags! Edit your tags, if you like, put the files into the iPod the usual way with gtkpod, and enjoy!!!

I recommend Ubuntu 8.04 for the newer iPod owners, for there is no need to patch anything to get things working.

I hope this little text helps. 

Sorry about the poor english, and see ya!

---

### Post by mroc on 2008-08-01
Hi all.  This may be very obvious to most but I had to look it up, so for the benefit of newer users, I thought I'd make a note:

Just today I tried to run the ./configure command with the options listed in the original post and got one error.

    Unknown option "--enable-pp".
    See ./configure --help for available options.

A quick google search turned up [this link]("http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2008-April/015109.html"), which states that "--enable-pp recently changed to --enable-postproc"

So if anyone else got this error it's a simple change to make.

Also, thank you to endersshadow for creating and maintaining this thread.

---

### Post by janne_oksanen on 2008-10-10
Something's happened to --enable-liba52 too. I keep getting unknown option on that one and a few google searches came up with nothing.

---

### Post by mocha on 2008-10-10
> **janne_oksanen said:**
> Something's happened to --enable-liba52 too. I keep getting unknown option on that one and a few google searches came up with nothing.

Search these forums for a thread on how to compile x264 and ffmpeg.  Apparently ffmpeg now has its own internal aac and doesn't need the --enable-liba52 anymore.

---

### Post by Willy_123 on 2008-10-13
Top 10 Most Popular iPod Video Tools 


 I Love Apple ipods, because they are the best. I don' t know what I can do without  

ipod. It goes everywhere where I go. Rencently I found 10 cool iPod video tools, I want to share them with you now.



 Top. 1 | Cucusoft iPod Video Converter + DVD to iPod Suite 
 I think this all-in-one iPod video Conversion solution is best, because I can convert both DVD media and video file media 

to iPod video/iP and it' s speed is far faster than others.
Top 10 Most Popular iPod Video Tools | Posted 10/8/2008
UI skin: 8 | Speed: 8. 5 |  Easy to Use: 8. 5 
User Rating: 8 | Popularity: 8 | Feature: 8. 5
[Download Now ](http://www.ipod-converter.org/downloads/dvdi.exe) 
 

 

Top. 2 | Avex DVD to iPod Video Suite 
 This One-click, All-in-One solution is my favourite, because this software features superb video/audio quality, the 

fastest conversion speed (Up to 3x faster). And it' s easy to use! A great software for iPod users.
Top 10 Most Popular iPod Video Tools | Posted 10/8/2008
UI skin: 7. 5 | Speed: 8 |  Easy to Use: 8 
User Rating: 7. 5 | Popularity: 7. 5 | Feature: 8
[Download Now ](http://www.rm-converter.net/downloads/avexipod.exe) 

 

Top. 3 | Aimersoft iPod Converter Suite 
 I love this all-in-one easy-to-use iPod MP4 video conversion tool, because it can help me rip DVD and also perfectly 

convert almost all popular video and audio formats such as AVI, Divx, FLV, DAT, XviD, WMV, MPEG, MPG, RM, RMVB, MOV, ASF, 

FLV, etc. to iPod MP4 (MPEG-4) H.264.
Top 10 Most Popular iPod Video Tools | Posted 10/8/2008
UI skin: 7 | Speed: 7. 5 |  Easy to Use: 7. 5 
User Rating: 7 | Popularity: 7 | Feature: 7. 5
[Download Now ](http://www.zune-converter.org/downloads/iPodconverter.exe)

 

Top. 4 | Cucusoft iPhone / iTouch / iPod to Computer Transfer 
 I am fond of  this application because it is an easy to use iPod / iPhone utility designed to help me backup all my files 

from my iPod / iPhone / iTouch.
Top 10 Most Popular iPod Video Tools | Posted 10/8/2008
UI skin: 6. 5 | Speed: 7 |  Easy to Use: 7 
User Rating: 6. 5 | Popularity: 6. 5 | Feature: 7
 [Download Now ](http://www.ipod-mp4-converter.com/downloads/iPodtoComputer_r91757.exe)


 

Top. 5 | Wondershare iPod Video Suite 
 I am keen on this useful and powerful all-in-one iPod video conversion solution, because I can convert both DVD media and 

video file media to iPod video/iPod movie.
Top 10 Most Popular iPod Video Tools | Posted 10/8/2008
UI skin: 6 | Speed: 6. 5 |  Easy to Use: 6. 5
User Rating: 6 | Popularity: 6 | Feature: 6. 5
[Download Now ](http://www.vcdconverter.net/downloads/videodvdSuite.exe)

 

Top. 6 | dvdXsoft DVD to iPod Converter 
 I fancy for this software because it features the highest DVD converting speed, the best output video quality, and fully 

tested on hundreds of different DVD-ROMs and DVD Movie discs that makes it qualified for strict compatibility standards. It 

enables me to different video options including MP4 video codec Xvid and H264, a rich list of different resolutions, video 

bitrates, video frame rates, audio bitrates, audio frequency, etc.
Top 10 Most Popular iPod Video Tools | Posted 10/8/2008
UI skin: 6 | Speed: 6 |  Easy to Use: 6 
User Rating: 6 | Popularity: 6. | Feature: 6
 [Download Now ](http://www.ipod-converter.org/downloads/dvdi.exe)

 

Top. 7 | Tansee iPod Transfer 
 I care for this ultimate application because I can transfer song from iPod to computer easily.
Top 10 Most Popular iPod Video Tools | Posted 10/8/2008
UI skin: 5. 5 | Speed: 6 |  Easy to Use: 6 
User Rating: 5. 5 | Popularity: 6 | Feature: 6
[Download Now ](http://www.mpeg-converter.net/downloads/et_r98733.exe)


 

Top. 8 | PQ DVD to iPod Video Suite 
 I like this One-Click, All-In-One solution because it' s super fast (up to 400% faster than other solutions) DVD 

conversion speed.
Top 10 Most Popular iPod Video Tools | Posted 10/8/2008
UI skin: 5. 5 | Speed: 6 |  Easy to Use: 6 
User Rating: 5. 5 | Popularity: 5. 5 | Feature: 6
[Download Now ](http://www.rmvb-converter.com/downloads/videoshare.exe)

 

Top. 9 | Movkit iPod Video Converter 
 I prefer this helpful converter because it supports almost all video formats, including AVI,MPEG,ASF/WMV,RMVB,RM and DivX. 

With it,you can easily convert AVI to MP4 / M4V / MOV, ASF / WMV to MP4 / M4V / MOV, AVI / MPEG / ASF / WMV / VOB / MOV / 

DIVX / XVID / RMVB / RM to MP4.
Top 10 Most Popular iPod Video Tools | Posted 10/8/2008
UI skin: 5. 5 | Speed: 5. 5 |  Easy to Use: 6 
User Rating: 5. 5 | Popularity: 5. 5 | Feature: 6
 [Download Now ](http://www.vob-converter.com/downloads/bestvideotool.exe)

 

Top. 10 | Aniosoft iPod to Computer 
 I go for this software because I can easily backup my songs, videos from my iPod back to my PC. It is so easy to use. It 

offers very fast searching and a browse mode which makes finding songs/videos on the iPod.
Top 10 Most Popular iPod Video Tools | Posted 10/8/2008
UI skin: 5 | Speed: 5. 5 |  Easy to Use: 5. 5 
User Rating: 5 | Popularity: 5 | Feature: 5. 5
[Download Now ](httphttp://www.iphone-converter.org/downloads/Anioipodtopc.exe)
[COLOR="Lime"][SIZE="4"]
source :[http://articles.allmyhealth.net/200810/Top-10-Most-Popular-iPod-Video-Tools_17.html](http://articles.allmyhealth.net/200810/Top-10-Most-Popular-iPod-Video-Tools_17.html)[/SIZE][/COLOR]

---

### Post by money2themax on 2008-10-13
those are all windows programs how do they help us linux folk?

---

### Post by Johny_123 on 2008-10-21
The 10 Most DVD to iPod Software Reviews and Downloads
[SIZE="3"]**source: [http://pop.american-auto-loan.com/200810/The-10-Most-DVD-to-iPod-Software-Reviews-and-Downloads_36.html](http://pop.american-auto-loan.com/200810/The-10-Most-DVD-to-iPod-Software-Reviews-and-Downloads_36.html)**

[/SIZE]

  iPod is arguably one of the coolest devices ever created. If you have an iPod, you know what wonders those little machines perform 

supporting music, video and pictures. What could be better than pulling out your iPod to watch a few clips from the Internet when you' re 

bored on the road or if you have extra time between classes? DVD to iPod Software helps you convert DVD you' ve downloaded or uploaded to 

your iPod. Now I will help you make an informed decision on which DVD to iPod Software is right for you.

 [IMG]http://pop.american-auto-loan.com/p/081013/ok/13.jpg[/IMG]

1 | iPod Video Converter + DVD to iPod Suite
	

It is an all-in-one iPod video Conversion solution. It includes 2 software -- " iPod Video Converter" and " DVD to iPod Converter". It 

supports almost all kinds of DVD formats to iPod Movie / iPod Video format (MP4 format) and  DVD to VCD/SVCD conversion. It direct convert 

DVD to iPod so its conversion speed is far faster than others.
The 10 Most DVD to iPod Software Reviews and Downloads | Posted 10/14/2008
Features Set: 9 | Ease of Use: 8. 5 | Speed of Conversion: 8. 5
UI skin: 8 | Reviewer Rating: 8. 5 | Popularity: 8. 5
[Downloads  Now]("http://www.iphoneconverter.com/downloads/iPodSuit.exe")

 
2 | Avex DVD to iPod Video Suite
	

It  is a One-click, All-in-One solution to create iPod movies from DVDs, TV shows and home Videos. It combines DVD to iPod Converter and 

iPod Video Converter in one package.It features fast conversion speed, superb Video/Audio quality. And it's easy to use!
The 10 Most DVD to iPod Software Reviews and Downloads | Posted 10/14/2008
Features Set: 8. 5 | Ease of Use: 8. 5 | Speed of Conversion: 8
UI skin: 8. 5 | Reviewer Rating: 8 | Popularity: 8
[Downloads Now]("http://www.rm-converter.net/downloads/avexipod.exe")

 
3 | PQ DVD to iPod Video Suite
	

This suite provides a One-Click, All-In-One solution to convert DVD, Tivo, DivX, MPEG, WMV, AVI, RealMedia and many more to iPod Video. It 

support MPEG-4 and H.264 with high video quality plus advanced video editing features. Its DVD conversion speed is super fast ( up to 400%). 
The 10 Most DVD to iPod Software Reviews and Downloads | Posted 10/14/2008
Features Set: 8 | Ease of Use: 8 | Speed of Conversion: 8
UI skin: 8 | Reviewer Rating: 7. 5 | Popularity: 7. 5
[Downloads Now]("http://www.zune-converter.org/downloads/iPodconverter.exe")

 
4 | Accelerate DVD to iPod Converter


It is the fastest DVD movie to iPod video converter software so far in the world. It can convert almost all kinds of DVD to iPod video (mp4) 

format. Its conversion speed is far faster than real-time, converting one DVD movie only takes half an hour in some high-end computers.
The 10 Most DVD to iPod Software Reviews and Downloads | Posted 10/14/2008
Features Set: 7. 5 | Ease of Use: 7. 5 | Speed of Conversion: 8
UI skin: 7. 5 | Reviewer Rating: 7. 5 | Popularity: 7
[Downloads Now]("http://www.ipod-mp4-converter.com/downloads/iPodtoComputer_r91757.exe")

 
5 | Super DVD to iPod Converter
	

It is the easiest and the most powerful DVD to iPod Converter software. It can capture and convert any segment of a DVD movie to iPod mp4 

format, select target subtitle and audio tracks.
The 10 Most DVD to iPod Software Reviews and Downloads | Posted 10/14/2008
Features Set: 7. 5 | Ease of Use: 7. 5 | Speed of Conversion: 8
UI skin: 7. 5 | Reviewer Rating: 7 | Popularity: 7
[Downloads  Now]("http://www.vcdconverter.net/downloads/videodvdSuite.exe")

 
6 | Wondershare DVD to iPod Ripper
	
It is a powerful DVD Ripping software for Apple iPod video. It can easily convert all kinds of DVD to iPod video (mp4) format with highest 

conversion speed and excellent conversion quality.  It is also an easy-to-use iPod converter.
The 10 Most DVD to iPod Software Reviews and Downloads | Posted 10/14/2008
Features Set: 7. 5 | Ease of Use: 7.  5 | Speed of Conversion: 8
UI skin: 8 | Reviewer Rating: 7 | Popularity: 6. 5
[Downloads Now]("http://www.ipod-converter.org/downloads/dvdi.exe")

 
7 | Aimersoft DVD to iPod Converter
	
It can easily convert DVD to iPod MP4 Video (h.264) and iPod MP3 for iPod Touch/Nano/iPod/Classic. It embed a powerful free iPod Copy 

Manager that can directly transfer DVD to iPod without iTunes, It can also copy your music, movies and TV shows from iPod to computer for 

backup.
The 10 Most DVD to iPod Software Reviews and Downloads | Posted 10/14/2008
Features Set: 7 | Ease of Use: 7 | Speed of Conversion: 7. 5
UI skin: 8 | Reviewer Rating: 6. 5 | Popularity: 6. 5
[Downloads Now]("http://www.mpeg-converter.net/downloads/et_r98733.exe")

 
8 | Wondershare DVD to iPod Suite for Mac	

It is an excellent DVD to iPod conversion tool that is designed for Mac OS users to convert DVD to iPod touch, iPod classic, iPod nano and 

other iPod players. It provides you with various DVD editing functions such as DVD chapter and title selection, movie trimming, video joiner 

and so on.
The 10 Most DVD to iPod Software Reviews and Downloads | Posted 10/14/2008
Features Set: 7 | Ease of Use: 7 | Speed of Conversion: 7
UI skin: 7. 5 | Reviewer Rating: 8 | Popularity: 6. 5
[Downloads  Now]("http://www.rmvb-converter.com/downloads/videoshare.exe")

 
9 | Aplus DVD to iPod Ripper	

It convert DVD files to a format that iPod understands. It is more simply and easy to use. It just a few clicks will completes the task of 

ripping DVD movies.
The 10 Most DVD to iPod Software Reviews and Downloads | Posted 10/14/2008
Features Set: 6. 5 | Ease of Use: 7 | Speed of Conversion: 6. 5
UI skin: 7 | Reviewer Rating: 6. 5 | Popularity: 6
[Downloads Now]("http://www.vob-converter.com/downloads/bestvideotool.exe")
 

10 | iSkysoft DVD to iPod Suite for Mac	

It can rip DVD to all sorts of video files and extract DVD audio to various audio files. It can also output video and audio files that can 

be perfectly played on most portable players.
The 10 Most DVD to iPod Software Reviews and Downloads | Posted 10/14/2008
Features Set: 8 | Ease of Use: 6. 5 | Speed of Conversion: 6
UI skin: 6. 5 | Reviewer Rating: 6 | Popularity: 5. 5
[Downloads  Now]("http://www.iphone-converter.org/downloads/Anioipodtopc.exe")
[B]
[SIZE="3"]source: [http://pop.american-auto-loan.com/200810/The-10-Most-DVD-to-iPod-Software-Reviews-and-Downloads_36.html](http://pop.american-auto-loan.com/200810/The-10-Most-DVD-to-iPod-Software-Reviews-and-Downloads_36.html)[/SIZE]

[/B]

---

### Post by fewjr on 2008-12-15
Hello all and endersshadow,
 I've been going over everything I can find in google and the forum with getting my ipod to work in Ubuntu. I am using 8.10 now and see that your tutorial was started back in January 2006. I see people are still posting in there as of October 2008. I haven't had time to read through all 70 some pages of the thread. I am working on it, but I was wondering if you could help me out with this. I want to be able to manage my music as well as rip/convert movies to ipod video and put them on my ipod. I have been ripping all my cds to the hard drive using Rhythmbox because my itunes backup of 5000 songs is corrupt...go figure. I ripped a couple DVDs with dvd::rip and converted to H264 with winff. I have gtkpod-aac 0.99.12-1ubuntu-1 installed in synaptic from the multiverse. I cannot get video on my ipod though. There is no video section on the left pane under ipod in gtkpod. I have a thread started here [http://ubuntuforums.org/showthread.p...73#post6376673](http://ubuntuforums.org/showthread.p...73#post6376673) where I was trying to get help. It shows the files installed for gtkpod. At this link [https://help.ubuntu.com/community/iP...20iPod%20Video](https://help.ubuntu.com/community/iP...20iPod%20Video) there is a screenshot showing video in the left pane under ipod. I don't have that. I am using a 5th Generation 30GiG Ipod. If you could help I would appreciate it. I really want to stay out of Windows if at all possible. I have been using Ubuntu since 8.04 and have run into alot of issues. I have been doing my best, but I need help on this one.

Best Regards,
fewjr

Thank You
fewjr

---

### Post by fewjr on 2008-12-15
Okay....reading this thread through and got to the part where you announce that its on the wiki, I see that the screenshot I pointed to is the same screenshot I was looking at. Then I looked under the screenshot and there in nice little letters it says: > Notice I made a playlist just for Video. You don't have to, but it helps organize things. Just click on the Add Files button, select the .mov that you want to transfer to the iPod, and then you're all set. 

 Is that all I was doing wrong....jeeesh!:oops: What a burnout. Work and 5 daughters...I need a vacation! Well when I get home from work I'll give that a try. I have been reading so many things for so many different issues I'm having with Ubuntu that I guess I just wasn't thinking of something so easy. I'll post if it is working. I tried to use iTunes to put the video I ripped/converted on my Ipod, but it would not let me. I hope gtkpod does.

fewjr

---

### Post by mechoulas on 2009-04-24
the easiest way so far!thanks bobandiara,works perfect on me,I am running ubuntu jaunty and my ipod is 30GB capacity,fifth generation

---

### Post by clanmackay on 2009-11-15
This may have shown up in the 50+ pages of comments, but I don't really feel like reading all of them, so...  :-)

*ffmpeg -i "${input_file}" -f mp4 -vttc mpeg4 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -attc aac -ab 192 -s 320x240 -aspect 4:3 "${output_dir}/${output_file_name}.mov"*

This distorts a video if it's not 4:3 to begin with.  I found a fix for this, modified some values to get them to work on my system, increased the bitrate and took the size up to VGA (which is supported on newer iPods), and put it on [my website, an.omalo.us (link)](http://an.omalo.us/2009/11/13/ffmpeg-and-ipod-in-linux/comment-page-1/#comment-63504).  I'm not pasting it here, because I want to retain the ability to modify it if I find a bug.  If *you* find a bug, please post there and I'll fix it.

HTH.

---

