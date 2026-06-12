---
title: "How To: Cinelerra Advanced GUI Video Editing"
date: 2006-10-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Old Pink on 2006-10-02
[CENTER][IMG]http://heroinewarrior.com/cinelerra_title4.jpg[/IMG]

[LEFT]Cinelerra is the movie makers dream. Whether your an amatuer looking to put some fun things on Google Video, or Steven Speilburg working on your next big hit, this application is the one for you!

[Visit the website!]("http://heroinewarrior.com/cinelerra.php3")
[Check out more Screenshots!]("http://heroinewarrior.com/cinelerra_shots.php3")

[U][B]Downloading and Installing
[/B][/U][LIST=1]
[*]You'll need YASM and NASM for this. In a new terminal, type:```
sudo apt-get install nasm
sudo apt-get install yasm
```
[*]Remain in terminal, and type:```
wget http://kent.dl.sourceforge.net/sourceforge/heroines/cinelerra-2.1-src.tar.bz2 
```To get the application source. It's a fairly big download, but well worth the wait (around 8 minutes at 50kbps).
[*]Still in the the terminal, extract the .tar.bz2 using:```
tar xfj cinelerra-2.1-src.tar.bz2
```... wait whilst the huge file is extracted.
[*]When you're faced with a prompt again, the extract is complete and you can type:```
cd cinelerra-2.1
```
[*]You're in the directory now, and nearly complete! Type:```
./configure
```...wait for the lines to stop scrolling.  (now's the time to take a nap, get a snack, or see a movie)
[*]When faced with another prompt, type:```
make
```and then:```
sudo make install
```[/LIST]Enjoy your new software! :) 
[/LEFT]
[/CENTER]

---

### Post by Old Pink on 2006-10-02
Uh oh. :( 

Mind moving this to [here](http://www.ubuntuforums.org/forumdisplay.php?f=100) for me? 

Thanks. :)

---

### Post by Cyfr on 2006-10-03
Hello I got the following error after 'make'

FATAL: can't create i686/soundtest.o: No such file or directory
make[1]: *** [i686/soundtest.o] Error 1

---

### Post by vampaz on 2006-10-03
I've the same error....that makes two of us..:-?

---

### Post by VTStevenVT on 2006-10-03
make -f build/Makefile.cinelerra
sh: -c: line 1: syntax error: unexpected end of file
make[1]: Entering directory `/home/steven/cinelerra-2.1'
gcc -c -O2 -fomit-frame-pointer -falign-loops=2 -falign-jumps=2 -falign-functions=2 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -I../../freetype-2.1.4/include -I../../ -DHAVE_OSS -DHAVE_FIREWIRE  soundtest.c -o i686/soundtest.o
Assembler messages:
FATAL: can't create i686/soundtest.o: No such file or directory
make[1]: *** [i686/soundtest.o] Error 1
make[1]: Leaving directory `/home/steven/cinelerra-2.1'
make: *** [all] Error 2
steven@steven-laptop:~/cinelerra-2.1$ sudo make
make -f build/Makefile.cinelerra
sh: -c: line 1: syntax error: unexpected end of file
make[1]: Entering directory `/home/steven/cinelerra-2.1'
gcc -c -O2 -fomit-frame-pointer -falign-loops=2 -falign-jumps=2 -falign-functions=2 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -I../../freetype-2.1.4/include -I../../ -DHAVE_OSS -DHAVE_FIREWIRE  soundtest.c -o i686/soundtest.o
Assembler messages:
FATAL: can't create i686/soundtest.o: No such file or directory
make[1]: *** [i686/soundtest.o] Error 1
make[1]: Leaving directory `/home/steven/cinelerra-2.1'
make: *** [all] Error 2



That makes 3 of us

---

### Post by henriquemaia on 2006-10-03
```
Assembler messages:
FATAL: can't create x86_64/soundtest.o: No such file or directory
make[1]: *** [x86_64/soundtest.o] Error 1
make[1]: Leaving directory `/home/henriquemaia/Desktop/cinelerra-2.1'
make: *** [all] Error 2

```

Four :)

---

### Post by BOBSONATOR on 2006-10-03
Make the GUI look like sony vegas, then i will use it :P

---

### Post by berserker on 2006-10-03
```
Assembler messages:
FATAL: can't create i686/soundtest.o: No such file or directory
make[1]: *** [i686/soundtest.o] Error 1
make[1]: Leaving directory `/home/erich/downloads/cinelerra-2.1'
make: *** [all] Error 2

```

FIVE!

---

### Post by CatKiller on 2006-10-04
```
iain@weatherwax:~/cinelerra-2.1$ make
make -f build/Makefile.cinelerra
sh: -c: line 1: syntax error: unexpected end of file
make[1]: Entering directory `/home/iain/cinelerra-2.1'
gcc -c -O2 -fomit-frame-pointer -falign-loops=2 -falign-jumps=2 -falign-functions=2 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -I../../freetype-2.1.4/include -I../../ -DHAVE_OSS -DHAVE_FIREWIRE  soundtest.c -o i686/soundtest.o
Assembler messages:
FATAL: can't create i686/soundtest.o: No such file or directory
make[1]: *** [i686/soundtest.o] Error 1
make[1]: Leaving directory `/home/iain/cinelerra-2.1'
make: *** [all] Error 2

```

Six :(

---

### Post by Old Pink on 2006-10-04
Ok, sorry to the 6+ people having trouble with this. It seems since this guide was written, the application has been modified and now for some reason will no longer compile.

If the above method does not work for you, try **[this]("http://www.kiberpipa.org/%7Egandalf/ubuntu/README")** official for-Ubuntu guide. :) 

*The people who have mentioned problems will be private messaged the link to this post.*

---

### Post by berserker on 2006-10-04
The official Ubuntu guide worked for me.  It installed a whole bunch of packages but didn't break anything on my system.  Thanks!

---

### Post by CatKiller on 2006-10-05
I tried their Ubuntu packages yesterday with no luck - their 686 and athlonxp packages crashed on my Thunderbird with an Illegal Instruction. After trying again to get the source, and the source from the [Community Version]("http://cvs.cinelerra.org/") to compile, and noting that it insisted that i686 was right, I tried again today with the 686 packages and it worked. Installed, and ran, without errors. I'm mystified as to exactly what made it work today when it wouldn't yesterday, but I'm quite happy that it does.

---

### Post by salsaman on 2006-10-06
Check this out for LiVES:

[http://www.getdeb.net/debs/l/lives_0.9.7-getdeb2_i386.deb](http://www.getdeb.net/debs/l/lives_0.9.7-getdeb2_i386.deb)

[http://lives.sourceforge.net/content/tut_html/lives_mt_tut.html](http://lives.sourceforge.net/content/tut_html/lives_mt_tut.html)

---

### Post by henriquemaia on 2006-10-06
> **salsaman said:**
> Check this out for LiVES:

[http://www.getdeb.net/debs/l/lives_0.9.7-getdeb2_i386.deb](http://www.getdeb.net/debs/l/lives_0.9.7-getdeb2_i386.deb)

[http://lives.sourceforge.net/content/tut_html/lives_mt_tut.html](http://lives.sourceforge.net/content/tut_html/lives_mt_tut.html)

What about the 64bit users?

---

### Post by karhulitos on 2006-10-22
Hi,

all I get from configure is a bunch of bash syntax errors. Anyone any idea what's wrong?

Errors look like this:```
./configure: 39: Syntax error: Bad fd number
```

This is Ubuntu 6.10.

regards,
Timo

---

### Post by rowol on 2006-10-29
RE: Building Cinelerra on Edgy

If you make an i686 directory under the Cinelerra one where you are building the source, you won't get the error 6 or so people mentioned.

I got a lot farther than that, but eventually got to the point where the build errored and stopped... no Cinelerra.  =(

---

### Post by tregetour on 2006-10-31
karhulitos,

I had the same problem.
[http://diveintomark.org/archives/200.../bad-fd-number](http://diveintomark.org/archives/200.../bad-fd-number) seems to have the answer of what's going on. Basically run "bash ./configure" instead of "./configure".

---

### Post by karhulitos on 2006-11-02
Cheers tregetour and rowol,

your hints helped me a bit further but that's about it. The link didn't open for me, so I just tried bash ./configure.

```
 bash ./configure
CONFIGURING QUICKTIME
[: 22: ==: unexpected operator
[: 27: ==: unexpected operator
./configure: 39: Syntax error: Bad fd number
CONFIGURING LIBMPEG3
./configure: line 139: cd: libmpeg3*: No such file or directory
CONFIGURING FFTW
./configure: line 142: cd: fftw*: No such file or directory
CONFIGURING MJPEGTOOLS
./configure: line 145: cd: mjpegtools*: No such file or directory
CONFIGURING SNDFILE
./configure: line 150: cd: libsndfile*: No such file or directory
CONFIGURING RAW1394
./configure: line 153: cd: libraw1394*: No such file or directory
CONFIGURING AVC1394
./configure: line 159: cd: libavc1394*: No such file or directory
CONFIGURING IEC61883
./configure: line 165: cd: libiec61883*: No such file or directory
CONFIGURING THEORA
./configure: line 173: cd: libtheora*: No such file or directory
Writing hvirtual_config.h
Have Video4Linux 2
Have DVB
Don't have OpenGL 2.0
Configured successfully.  Type 'make' to build it.
```

and make threw me very many erros.

But best part is that I finally got the name right! I've kept searching for 'Cinerella' instead of 'Cinelerra'.. hehe!

---

### Post by rama001 on 2006-12-09
Hi, did anyone get this going on Ubuntu 6.10 (edgy?)
I get the same errors as karhulitos did above.
I tried bash ./configure but that does not work either.
I even edited the configure file to point to the exact directory names, but still got the same errors.

If I do:

./configure

I get:

[: 24: ==: unexpected operator
[: 31: ==: unexpected operator
./configure: 47: Syntax error: Bad fd number

And if I do:

bash ./configure


I get:

CONFIGURING QUICKTIME
[: 22: ==: unexpected operator
[: 27: ==: unexpected operator
./configure: 39: Syntax error: Bad fd number
CONFIGURING LIBMPEG3
./configure: line 139: cd: libmpeg3*: No such file or directory
CONFIGURING FFTW blah blah blah blah... same as karhulitos

Needless to say, I am at a loss.
Please can anybody help us?
Thanks! :-)

---

### Post by rama001 on 2006-12-09
[SIZE="4"]**[COLOR="RoyalBlue"]Update[/COLOR]**[/SIZE]

Can anyone explain the solution below? I tried to use it, but it still did not work.

The link to [http://diveintomark.org/archives/2006/09/19/bad-fd-number](http://diveintomark.org/archives/2006/09/19/bad-fd-number) is dead, so... here is the info from Google cache:

 ([http://72.14.205.104/search?q=cache:abSSIKaahmcJ:diveintomark.org/archives/2006/09/19/bad-fd-number+http://diveintomark.org/archives/200.../bad-fd-number&hl=en&gl=ca&ct=clnk&cd=1]("http://72.14.205.104/search?q=cache:abSSIKaahmcJ:diveintomark.org/archives/2006/09/19/bad-fd-number+http://diveintomark.org/archives/200.../bad-fd-number&hl=en&gl=ca&ct=clnk&cd=1")) here:

‘Bad fd number’ error in Ubuntu 6.10 (Edgy Eft) Tuesday, September 19, 2006

Have you tried to compile something that wasn’t in the repositories, or otherwise run a shell script, and gotten this error?

mark@atlantis:~/code/mpeg4ip-1.5.0.1$ ./bootstrap
dir: .
SDL appears to be installed
./bootstrap: 76: Syntax error: Bad fd number

This “Bad fd number” error occurs because Ubuntu Edgy uses dash as /bin/sh. In Ubuntu 6.06 “Dapper Drake” and earlier versions used bash instead, which ran scripts in a special backwards-compatibility mode that wasn’t truly backwards compatible (i.e. some bash-specific code was still accepted, even though it wasn’t part of the POSIX 1003.2 and 1003.2a specifications for shells). Ubuntu Edgy is the first version of Ubuntu that symlinks /bin/sh to /bin/dash instead of /bin/bash. The packages in the repositories have been checked for compatibility, but this may still cause problems with improperly-written third-party shell scripts.

Confused yet? There’s a simple solution: run the script through bash yourself.

mark@atlantis:~/code/mpeg4ip-1.5.0.1$ bash bootstrap

If you’re developing your own shell script and your users are reporting this error to you, you should change the first line of your script to #!/bin/bash, since you’ve been relying on bash-specific extensions without realizing it. Or better yet, take the time to learn what those extensions are, and fix them so your script works in POSIX-compliant shells. You can manually install dash and test compatibility by changing the first line of your script to #!/bin/dash, then change it back to #!/bin/sh once everything works again. I did this with my podencoder script and found a few surprises.

This tip has been brought to you by someone who knows just enough shell scripting to be dangerous.

Further reading:

    * dash home page
    * dash on Wikipedia
    * “Dash as /bin/sh” in Ubuntu bug feature tracker

bash, dash, linux, posix, sh, thingsihateaboutyou, ubuntu
7 comments

   1.

      You’re running edgy already? Blimey.

      Comment by Stuart Langridge — Wednesday, September 20, 2006 @ 2:58 am
   2.

      From the Dash as /bin/sh Ubuntu Wiki Page: The default user shell (that set by adduser) would remain as /bin/bash, as would the shell of existing accounts including root.
      Did you create a new account when you installed Edgy, or does that mean it doesn’t work as described?

      Comment by Nicolas Chachereau — Wednesday, September 20, 2006 @ 4:05 am
   3.

      Most of the scripts use #!/bin/sh and on Edgy that is a link to /bin/dash so it does not interfer with the shell the user has only for scrpting.

      Comment by 2tone — Wednesday, September 20, 2006 @ 8:18 am
   4.

      I typically manually run bash for shell scripts, except for a few of my own private scripts that require csh. However, when installing a package, there could be scripts that explicitly launch other scripts by calling sh.

      Comment by W^L+ — Wednesday, September 20, 2006 @ 8:00 pm
   5.

      What shell construct raises “Bad fd number” ? And why?

      Comment by Nilton Volpato — Friday, September 22, 2006 @ 11:47 am
   6.

      The particular script where I noticed the problem was attempting to redirect FAAC’s help output (printed to stderr, I believe) to a file.

      faac --help >&faac_help

      This is the line that caused the “Bad fd number” error, but I don’t know enough about shell scripting to know why.

      Comment by Mark — Friday, September 22, 2006 @ 4:17 pm
   7.

      ‘>& file’ is a csh way to redirect both stdout and stderrto a file, and bash allows the same construct.

      sh uses >& in a more restrictive manner. When sh sees >&, it accepts only a file descriptor number after the >& and freaks out when it sees a non-number.

      The sh redirection of both stdout and stderr to a file is ‘> file 2>&1&#8242;, meaning redirect stdout to file and then redirect sdterr to stdout.

      Comment by Matthew Ernest — Saturday, September 23, 2006 @ 10:10 pm

---

### Post by lprofil on 2006-12-18
If you like to know how to compile **Cinelerra 2.1 CV** from subversion sources 
the easy way you might be interested in [my new tutorial for Edgy Eft]("http://www.ubuntuforums.org/showthread.php?p=1899731").

/lprofil

---

