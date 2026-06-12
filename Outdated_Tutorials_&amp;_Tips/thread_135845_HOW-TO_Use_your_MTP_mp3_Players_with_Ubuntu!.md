---
title: "HOW-TO: Use your MTP mp3 Players with Ubuntu!"
date: 2006-02-24
forum: Outdated Tutorials &amp; Tips
---

### Post by jpeirce on 2006-02-24
Recently, a few mp3 players have gone the route of Microsoft's new Media Transfer Protocol (MTP) which is based off Picture Transfer Protocol (PTP). Linux has a PTP transfer client, which has had some limited success in transferring files to and from the players, mainly I-Rivers. But for owners of many Creative Players with Firmware 2.* and higher, and some Dell players, use of these devices has been impossible. Until the release of libmtp, which allows us to list the tracks on the player, detect players plugged into the machine, send, get, and delete tracks from the player. Libmtp can be found at [http://libmtp.sourceforge.net](http://libmtp.sourceforge.net). 

The first step is to download the newest version from libmtp's CVS.

```

$cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/libmtp login
hit enter when prompted for a password.
$cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/libmtp co -P libmtp
```

What I reccomend to do now, is to find if your player is currently supported by  libmtp, connect the player via USB, and run
```

$lsusb

```

Find your player in the output, and note the part of the output that is in this format "XXXX:XXXX", for my Creative Zen Sleek, the output was "041e:4137"

Then, look in libmtp's usermap to see if it is supported yet.
cd into where you downloaded libmtp into, and view the file "libmtp.usermap"

Try to find your player in the list. If it is unsupported, you can try to add it to the usermap by copying the lines from a player, but changing the second and third phrases of the line with the two numbers you got from lsusb. If you do this, you must do the same to the two numbers in the file libmtp.rules. 

Now to install the file. Make sure you have libtool, automake, and autoconf installed. 

```

$sudo apt-get install autoconf automake1.9 libtool

```

Then, run the preconfigured autogen.sh script from CVS

```

$./autogen.sh

``` 

If no errors are output, we can now go on to configuring the program. There are some errors with using gcc 4 currently, so we must change that. The readme says to use gcc-3.2, but that isnt on any of the newer repos for Ubuntu, and I had no trouble with gcc-3.3

```
 
$sudo apt-get install gcc-3.3
$CC=gcc-3.3
$export CC
$./configure
$make
$sudo make install

```

If no errors come up, you have now installed libmtp successfully!

To use the player, you can use their example client in the examples directory you downloaded libmtp to. 

```

$cd examples/

```

Currently, there are 5 scripts, tracks, sendtr, gettr, deltr, and detect.

To test if the player is detected, connect the player, turn it on, and run

```

$sudo ./detect

```

If it can't find the player, try disconnecting and reconnecting the player to a different USB port.

To upload songs to your player use sendtr, run

```

$sudo ./sendtr [filename]

```

enter the right codec when it prompts you to, either MP3 WAV or WMA, this is required, then enter the rest of the information at the prompts, the rest are optional.

To download songs from your computer, use gettr.

First you need to find the track ID and filename of the songs name on the player, run

```
 
$sudo ./tracks

```

This will list all the songs and their IDs in it's output. Find the song you wish to get, not it's Track ID and Origfilename and then run

```

$sudo ./gettr [Track ID] [Origfilename]

```

To delete tracks from the player, use deltr. You will need the Track ID from the output of tracks, then run 

```

$sudo ./deltr [Track ID] 

```

---

### Post by Didjit on 2006-04-06
Gnomad2 ([http://gnomad2.sourceforge.net/](http://gnomad2.sourceforge.net/)) now has some support for libmtp. I havn't been able to try it out yet, but I'm eager to use my Nomad Zen in Linux....

Didijt

---

### Post by stengah on 2006-04-16
Running the first line gets me a "not such file or file directory" error - any ideas?

---

### Post by pek on 2006-04-17
[QUOTE=stengah]Running the first line gets me a "not such file or file directory" error - any ideas?[/QUOTE]


sudo apt-get install cvs should be fine :p

---

### Post by thunderduck3141 on 2006-04-18
h4x0r@ubuntu:~/libmtp$ configure
bash: configure: command not found
h4x0r@ubuntu:~/libmtp$ sh ./configure
sh: ./configure: No such file or directory
h4x0r@ubuntu:~/libmtp$ ./configure
bash: ./configure: No such file or directory
h4x0r@ubuntu:~/libmtp$ cd
h4x0r@ubuntu:~$ ./configure
bash: ./configure: No such file or directory
h4x0r@ubuntu:~$ whereis configure
configure:
h4x0r@ubuntu:~$ cd configure
bash: cd: configure: No such file or directory
h4x0r@ubuntu:~$ cd ,/configure
bash: cd: ,/configure: No such file or directory
h4x0r@ubuntu:~$
h4x0r@ubuntu:~$ cd ./configure
bash: cd: ./configure: No such file or directory
h4x0r@ubuntu:~$

didnt detect for me so i tried the gcc downgrade thing and this was my output

---

### Post by paulyche on 2006-04-23
upon running
./configure

I get:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc-3.3
checking for C compiler default output file name... configure: error: C compiler cannot create executablesSee `config.log' for more details.

I have build-essential etc installed and I've compiled from source before. I'm using dapper. (Maybe I shouldn't be!)

Any ideas?

---

### Post by jpeirce on 2006-04-24
[QUOTE=thunderduck3141]h4x0r@ubuntu:~/libmtp$ configure
bash: configure: command not found
h4x0r@ubuntu:~/libmtp$ sh ./configure
sh: ./configure: No such file or directory
h4x0r@ubuntu:~/libmtp$ ./configure
bash: ./configure: No such file or directory
h4x0r@ubuntu:~/libmtp$ cd
h4x0r@ubuntu:~$ ./configure
bash: ./configure: No such file or directory
h4x0r@ubuntu:~$ whereis configure
configure:
h4x0r@ubuntu:~$ cd configure
bash: cd: configure: No such file or directory
h4x0r@ubuntu:~$ cd ,/configure
bash: cd: ,/configure: No such file or directory
h4x0r@ubuntu:~$
h4x0r@ubuntu:~$ cd ./configure
bash: cd: ./configure: No such file or directory
h4x0r@ubuntu:~$

didnt detect for me so i tried the gcc downgrade thing and this was my output[/QUOTE]


Are you sure you ran the autogen script that comes with libmtp previous to trying to run configure?


[QUOTE=paulyche]upon running
./configure

I get:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc-3.3
checking for C compiler default output file name... configure: error: C compiler cannot create executablesSee `config.log' for more details.

I have build-essential etc installed and I've compiled from source before. I'm using dapper. (Maybe I shouldn't be!)

Any ideas?[/QUOTE]

I've never encountered that error before, and a quick google search only came up with one result, in italian. The only thing I can think of is make sure g++ is installed, maybe even g++-3.3.

---

### Post by paulyche on 2006-04-25
Thanks jpeirce,

No progress with g++ installed though. I've tried using gcc4.0, gcc3.3, gcc3.4 and even gcc2.95 (with apporpriate g++'s) and the same error occurs. So I think my problem isn't to do with the compiler.

Thanks anyway for your suggestion.

---

### Post by jpeirce on 2006-04-25
Can you post your config.log after you try to configure it? Perhaps that will shed some light on the situation.

---

### Post by paulyche on 2006-04-25
Actually I've been a bit naughty and cross-posted....


my config.log file is here [here]("http://www.ubuntuforums.org/showthread.php?p=947127#post947127")

---

### Post by Booker on 2006-05-06
Hello

I'm new here. Thanks too much that my Zen Vision:M seems to work on my Ubuntu Breezy.

---

### Post by pek on 2006-05-13
ok! version 0.5 works with iRiver U10! i am able to see , download, and delete the files! that is extremely good! no upload though... ```
PTP: Opening session
Connected to MTP device.
Sending track...
LIBMTP_Send_Track_From_File_Descriptor: Could not send object info

PTP: Closing session
New track ID: 0
OK.

``` 
that's the error it gives me.

i think it could be related to this other error
```

ptp2/ptp_usb_getdata: read 1 bytes too much, expect problems!

```

---

### Post by geetarista on 2006-05-17
[QUOTE=jpeirce]
```

$cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/libmtp login
hit enter when prompted for a password.

```
[/QUOTE]

After I do this, I get an error that says "cvs [login aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: No route to host".

What does that mean?

---

### Post by Lush on 2006-06-13
I'm getting the same problem as geetaristia, please help

I entered
```
haris@Pavillion:~$ cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/libmtp login
Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/libmtp
CVS password:

```
Terminal returned me:

```

cvs [login aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401
failed: Connection timed out

```

thanks again

---

### Post by Whoopie on 2006-06-13
Hi,

Use this:

```

$cvs -d:pserver:anonymous@libmtp.cvs.sourceforge.net:/cvsroot/libmtp login
hit enter when prompted for a password.
$cvs -z3 -d:pserver:anonymous@libmtp.cvs.sourceforge.net:/cvsroot/libmtp co -P libmtp

```

Best regards,
Whoopie

PS: why didn't you look at the sourceforge page to see if something changed with the CVS?

---

### Post by metathran on 2006-06-13
Works great no trouble to install with this howto.
But i still have this erro with gnomad
> gnomad2: error while loading shared libraries: libmtp.so.0: cannot open shared object file: No such file or directory


But libmtp is installed... How can i make gnomad work with my zen micro ?? Using the commad line is not very easy with more than 1000 song in the jukebox.

---

### Post by NT4usB on 2006-06-13
S'pose it will work with my NJB1 or NJB3?

---

### Post by jinx099 on 2006-06-14
Cool, it seems to work, thanks!

I installed gnomad2 after getting it working with libmtp, but gnomad 2 says "no jukeboxes found on usb bus".  Anyone know whats wrong?  Heres my lsusb:

```
Bus 004 Device 007: ID 041e:4128 Creative Technology, Ltd
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 006: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 001 Device 004: ID 0bc7:0004 X10 Wireless Technology, Inc. X10 Receiver
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 002: ID 04e8:326c Samsung Electronics Co., Ltd
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c01d Logitech, Inc.
Bus 002 Device 003: ID 046d:c214 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000

```

---

### Post by Didjit on 2006-06-14
[quote=metathran]Works great no trouble to install with this howto.
But i still have this erro with gnomad


But libmtp is installed... How can i make gnomad work with my zen micro ?? Using the commad line is not very easy with more than 1000 song in the jukebox.[/quote]

run *sudo ldconfig *first. Then run *gnomad2* .(or *sudo gnomad2 i*f you run into authority problems)

---

### Post by DaveMachine on 2006-06-15
Quick question. Where would I find gnomad2 in the file system in order to uninstall it? I've got libmtp up and running but I figured I should reinstall gnomad2 so it will recognize libmtp.

---

### Post by Brokenrgv on 2006-06-15
$sudo apt-get install gcc-3.3
$CC=gcc-3.3
$export CC
$./configure
$make
$sudo make install

this part confuses me, it says i have the latest version of gcc-3.3 allready, but when i type make in the libmtp folder i get this
make: *** No targets specified and no makefile found.  Stop.
which is holding me up from the next step, what am i doing wrong? thanks

---

### Post by jinx099 on 2006-06-18
Okay, gnomad2 is pissing me off, maybe someone can help me.  It says, "No jukeboxes found on usb bus" right after starting up.

libmtp on the other hand is working great!

Okay, so the version of gnomad that comes with ubuntu is 2.8.1.  On the gnomad2 website, it says they added mtp support in 2.8.3.  I downloaded the latest version: 2.8.5 and worked through the dependencies.  However, during "make" I get this error:

```
Making all in src
make[1]: Entering directory `/home/jinx/Desktop/gnomad2-2.8.5/src'
gcc  -g -O2   -o gnomad2  id3read.o gnomad2.o prefs.o filenaming.o jukebox.o util.o mp3file.o editmeta.o filesystem.o playlists.o xfer.o data.o player.o metadata.o wmaread.o wavfile.o -pthread -L/usr/local/lib -lgthread-2.0 -lnjb -lusb -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lid3tag -lz -L/usr/local/lib -lmtp -lusb
jukebox.o: In function `hd2jb_thread':/home/jinx/Desktop/gnomad2-2.8.5/src/jukebox.c:1873: warning: the use of `tmpnam' is dangerous, better use `mkstemp'
jukebox.o: In function `jukebox_delete_tracks':jukebox.c:(.text+0x385b): undefined reference to `LIBMTP_Delete_File'
collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/jinx/Desktop/gnomad2-2.8.5/src'
make: *** [all-recursive] Error 1

```

Can anyone help me to get 2.8.5 installed?  :-( 

Anyways, so I looked on the debian website and found that version 2.8.3 is in their testing repo.  I download the precompiled .deb and ran it no problem, but I get the same damn error: "No jukeboxes found on usb bus" or something like that.  I have also ran it as root, same result.

Help please!

---

### Post by metathran on 2006-06-18
I'm blocked too the tip (running ldconf and sudo gnomad2) didn't solved my problem...
Can't compile gnomad 2.8.5 without errors, Can't find a .deb of the 2.8.5 version but only the 2.8.3 and i get an error with the shared library libmtp.so.0, try to install a 2.8.5 rpm with alien but "no jukebox detected". I also tried to install an old version of the firmware on windows but the flashing tool can't detect the zen micro...

I have done everything i can without any results, execpt for libmtp wich work but it's not possible to handle all this tracks with the command line... I'm waiting for a miracle...

---

### Post by Brokenrgv on 2006-06-18
at least its not just me, what we need is someone to put up the new gnomad 2.8.5 into the repo's, so we can upgrade to a version that works with our players (zen vision m)
ok ive got libmtp talking to my zvm im stuck on something thats probably very simple when you sudo ./sendtr (filename) i just open up the folder with the track and drag it across to the terminal box and this turns up 

joeblogs@joeblogs-desktop:~/Desktop/libmtp-0.0.8/examples$ sudo ./sendtr /home/joeblogs/Desktop/Buzz Out Loud/cnetbuzz_061406.mp3
You need to pass a filename.
usage: sendtr [ -D debuglvl ] [ -q ] -t <title> -a <artist> -l <album>
       -c <codec> -g <genre> -n <track number> -y <year>
       -d <duration in seconds> -f "Folder Name" <path>
(-q means the program will not ask for missing information.)

doesnt matter worked it out :) with mtp that is still would be nice to use the lattest vers of gnomad2 since transfering 1 track at a time is painfull

---

### Post by Brokenrgv on 2006-06-21
anyone know what this would mean "You need to pass a filename" comes up with some video's that refuse to transfer.

---

### Post by droefs on 2006-06-21
Can't get into CVS...

$ sudo cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/libmtp login Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/libmtp
CVS password:
cvs [login aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: No route to host
$ traceroute 66.35.250.207
...
16  66.35.212.174 (66.35.212.174)  175.269 ms  174.744 ms  174.834 ms
17  cvs.sourceforge.net (66.35.250.207)  172.912 ms !C  172.903 ms !C  172.920 ms !C

 Any suggestions?

---

### Post by ErikTheRed on 2006-06-21
Nice guide! I may be getting a Toshiba Gigabeat S for my birthday, so this will be ever so helpful.

---

### Post by baffle on 2006-07-07
I created some ugly ugly packages that seems to work, it's basically just standard dh_make. I made these so that I have something to use until I get proper packages.

Installation instructions:
```

 wget http://dropbox.stenstad.net/baffle/Debian/gnomad2_2.8.6_i386.deb
 wget http://dropbox.stenstad.net/baffle/Debian/libmtp_0.0.9_i386.deb
 sudo apt-get install libnjb5
 sudo dpkg -i libmtp_0.0.9_i386.deb
 sudo dpkg -i gnomad2_2.8.6_i386.deb

```
Permissions to usb is not set properly, so you launch it by issuing sudo gnomad2.

I've also not separted include-files into a separate -dev package. At least it works.

---

### Post by kbunsie on 2006-07-09
After doing ./configure, I get the following output with an error:```
~/libmtp$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc-3.3
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc-3.3 accepts -g... yes
checking for gcc-3.3 option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc-3.3... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc-3.3... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc-3.3 -E
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
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
checking command to parse /usr/bin/nm -B output from gcc-3.3 object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc-3.3 supports -fno-rtti -fno-exceptions... no
checking for gcc-3.3 option to produce PIC... -fPIC
checking if gcc-3.3 PIC flag -fPIC works... yes
checking if gcc-3.3 static flag -static works... yes
checking if gcc-3.3 supports -c -o file.o... yes
checking whether the gcc-3.3 linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for doxygen... false
configure: WARNING: *** doxygen not found, docs will not be built
checking if the host operating system is Darwin... no
checking For MinGW32... no
checking for initscr in -lcurses... no
checking for usb_control_msg in -lusb... no
configure: error: I can't find the libusb libraries on your system. You
        may need to set the LDFLAGS environment variable to include the
        search path where you have libusb installed before running
        configure (e.g. setenv LDFLAGS=-L/usr/local/lib)

```Any help...

---

### Post by elsupermang on 2006-07-10
I own a Gigabeat S. And while this is a GREAT player, media management via MTP is HORRIBLE. MTP has to be the WORST implementation of media management ever. What they did here is take a protocol designed for digital cameras, made a few changes and dished it out ala microsoft. My biggest gripe is you can't edit ANYTHING you put on your damn player. You have to RE-TRANSFER the whole file to make changes. Isn't this a 1985 concept or am i wrong here.

And while your solution is a welcomed and helpful, it simply is just not ideal. If the windows implementation is what i would call a sorry excuse for ALPHA-grade software the linux implementation which is just starting to get developed is very far behind. 

By the way I spent about 3-4 hours retagging ID3 information and album covers on 792 songs using a windows app called MediaMonkey because WMP 11 is just a joke. The first hour was spent transferring my entire collection over twice (the first time initially and the second time when i discovered i couldnt edit ANY tags once they are on the device). I then wanted to add album art but discovered I would have to re-transfer everything, so away I went. 

Well anyways thats my rant, MTP BLOWS. They need to release an update to this crap they call a "protocol"

---

### Post by swoon on 2006-07-10
> **elsupermang said:**
> I own a Gigabeat S. And while this is a GREAT player, media management via MTP is HORRIBLE. MTP has to be the WORST implementation of media management ever. What they did here is take a protocol designed for digital cameras, made a few changes and dished it out ala microsoft. My biggest gripe is you can't edit ANYTHING you put on your damn player. You have to RE-TRANSFER the whole file to make changes. Isn't this a 1985 concept or am i wrong here.

And while your solution is a welcomed and helpful, it simply is just not ideal. If the windows implementation is what i would call a sorry excuse for ALPHA-grade software the linux implementation which is just starting to get developed is very far behind. 

By the way I spent about 3-4 hours retagging ID3 information and album covers on 792 songs using a windows app called MediaMonkey because WMP 11 is just a joke. The first hour was spent transferring my entire collection over twice (the first time initially and the second time when i discovered i couldnt edit ANY tags once they are on the device). I then wanted to add album art but discovered I would have to re-transfer everything, so away I went. 

Well anyways thats my rant, MTP BLOWS. They need to release an update to this crap they call a "protocol"

so...does it work under linux? my mp3 files are tagged properly already so i don't care about editing files once they are on the device. i would like to transfer the files from my linux box to the device, so i don't have to drag my usb hdd back and forth b/t computers.

---

### Post by aglc2005 on 2006-07-28
> **kbunsie said:**
> After doing ./configure, I get the following output with an error:```
~/libmtp$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc-3.3
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc-3.3 accepts -g... yes
checking for gcc-3.3 option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc-3.3... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc-3.3... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc-3.3 -E
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
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
checking command to parse /usr/bin/nm -B output from gcc-3.3 object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc-3.3 supports -fno-rtti -fno-exceptions... no
checking for gcc-3.3 option to produce PIC... -fPIC
checking if gcc-3.3 PIC flag -fPIC works... yes
checking if gcc-3.3 static flag -static works... yes
checking if gcc-3.3 supports -c -o file.o... yes
checking whether the gcc-3.3 linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for doxygen... false
configure: WARNING: *** doxygen not found, docs will not be built
checking if the host operating system is Darwin... no
checking For MinGW32... no
checking for initscr in -lcurses... no
checking for usb_control_msg in -lusb... no
configure: error: I can't find the libusb libraries on your system. You
        may need to set the LDFLAGS environment variable to include the
        search path where you have libusb installed before running
        configure (e.g. setenv LDFLAGS=-L/usr/local/lib)

```Any help...

I also had a similar problem, solved by installing libusb-dev

Now onto my problem, there is not an autogen.sh file in my cvs???

---

### Post by rla128 on 2006-08-20
I'm getting this:

> configure.ac: 6: `automake requires `AM_CONFIG_HEADER', not `AC_CONFIG_HEADER'
automake: configure.ac: installing `./install-sh'
automake: configure.ac: installing `./mkinstalldirs'
automake: configure.ac: installing `./missing'
automake: Makefile.am: required file `./NEWS' not found
configure.ac: 6: required file `./[config.h].in' not found
src/Makefile.am:36: libmtp_la_LDFLAGS defined both conditionally and unconditionally
automake: src/Makefile.am: warning: automake does not support libmtp_la_LDFLAGS being defined conditionally
Last command failed with status 1 in directory /home/robert-anderson/libmtp.
Aborting




Any Help?

---

### Post by elsupermang on 2006-09-03
Well I was messing around trying to get my Gigabeat working under linux. The latest version of Gnomad2 with MTP support will allow you to transfer songs and modify (not sure about creating) playlists on your Gigabeat S. There are some quirks for some reason you have to disconnect it and reconnect every time you use Gnomad2 to access the device, also you must run as super user for the device to be detected (must be a usb hotplug permission issue). Still missing alot of features. I wanna try with video and pictures although they wont be displayed in Gnomad2

---

### Post by Mijikai on 2006-11-29
configure.ac: 6: `automake requires `AM_CONFIG_HEADER', not `AC_CONFIG_HEADER'
automake: configure.ac: installing `./install-sh'
automake: configure.ac: installing `./mkinstalldirs'
automake: configure.ac: installing `./missing'
automake: Makefile.am: required file `./NEWS' not found
configure.ac: 6: required file `./[config.h].in' not found
src/Makefile.am:36: libmtp_la_LDFLAGS defined both conditionally and unconditionally
automake: src/Makefile.am: warning: automake does not support libmtp_la_LDFLAGS being defined conditionally
Last command failed with status 1 in directory /home/robert-anderson/libmtp.
Aborting

I'm also getting the same as rla128 problem...any help would be greatly appreciated!

---

### Post by freshanointing on 2006-12-02
Source of [http://ubuntuforums.org/showthread.php?t=199250&page=26](http://ubuntuforums.org/showthread.php?t=199250&page=26)

I had to install libtool, autotool, automake1.9, autoconf and m4 . You can search for them in synaptic.

---

Hope this helps you it did for me!!!

---

### Post by myolbug on 2007-11-13
the instruction posted here didn't work for me.  I also tried this page, and I get errors there as well: [http://gnomad2.sourceforge.net/?section=article](http://gnomad2.sourceforge.net/?section=article)

XX-ubuntu:~$ export CVSROOT=:pserver:anonymous@cvs.sourceforge.net:/cvsroot/libnjb
XX-ubuntu: cvs login
Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/libnjb
CVS password:
cvs [login aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: No route to host


What now?

---

### Post by nyorondesu on 2007-12-03
> **jpeirce said:**
> ```
 
$sudo apt-get install gcc-3.3
$CC=gcc-3.3
$export CC
$./configure
$make
$sudo make install

```
This part is screwing me up. When I enter ./configure, it says there's no such file or directory, but I'm still in the home folder... am I supposed to be somewhere else? Also, do the second and third steps actually do anything? When I enter them, they just go to the next line in the terminal, like nothing happened.

---

### Post by jpeirce on 2008-02-10
I'm sorry guys, this tutorial was made 2 years ago when libmtp had just started coming out with releases, I'm willing to bet the instructions for installation have changed quite a bit. 

I no longer use a MTP player, but if I find one I'll update the instructions.

---

### Post by BDNiner on 2008-03-23
I have got my creative zen 4GB working in ubuntu using Exaile. It was actually simple but you have to run exaile as root. I installed the MTP plugin in exaile from the edit menu. In order for the install to work you have to have the packages pymtp and libmtp installed. One annoying thing is i have to reimport my library since i am running exaile as root. I hope there is a way to run exaile as a regular user and still use my creative zen, I also have to run gnomand2 as root inorder for my mp3 player to be detected.

---

### Post by rfdeshon on 2008-04-02
> **BDNiner said:**
> I have got my creative zen 4GB working in ubuntu using Exaile. It was actually simple but you have to run exaile as root. I installed the MTP plugin in exaile from the edit menu. In order for the install to work you have to have the packages pymtp and libmtp installed. One annoying thing is i have to reimport my library since i am running exaile as root. I hope there is a way to run exaile as a regular user and still use my creative zen, I also have to run gnomand2 as root inorder for my mp3 player to be detected.

I seem to recall seeing this problem elsewhere. Make sure you are a member of the plugdev group, I believe that group allows you to access devices like that. Also, check and make sure your device id is set up in nomad.rules (somewhere in /etc, can't remember where offhand). If all else fails go here and search for a gnomad how to [http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

---

