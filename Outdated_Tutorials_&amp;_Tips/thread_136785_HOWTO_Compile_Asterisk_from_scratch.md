---
title: "HOWTO: Compile Asterisk from scratch"
date: 2006-02-26
forum: Outdated Tutorials &amp; Tips
---

### Post by fizgig on 2006-02-26
I took notes on what I did so I could do it later. Maybe someone else might find them useful. They might not be the most ideal - I'm not an expert but please feel free to comment and I'll update this message.

0. Edit the /etc/apt/sources.list file to remove the # signs before the lines that begin with **# deb http** to activate them and then do **apt-get update**.

1. Install Packages:
**apt-get install sendmail zlib1g-dev libssl-dev ncurses-dev libnewt-dev gcc-3.4 subversion openssh-server build-essential linux-source-2.6.12** (or whatever kernel you have)

2. Prepare Linux kernel source
 [B]cd /usr/src
 tar xvjf linux-source* [/B](Extracts the files from the zip file)
**  rm linux-source-2.6.12.tar.bz2 **(Don't need the zip anymore)
 **ln -s linux-source-2.6.12 linux **(makes /usr/src/linux point to /usr/src/linux-source-2.6.12)
[B]  cd linux
 cp /boot/config-2.6.whatever .config[/B] (copies the config file that was used to compile your kernel into the /usr/src/linux dir)
**  make menuconfig  **then exit and save config[B]
 uname -r[/B]  (examine what comes after 2.6.12  For example, I had 2.6.12-9-386)
 **vi /usr/src/linux/Makefile**
 Go to the EXTRAVERSION line and make it like so:
 EXTRAVERSION=**-9-386**
** make modules_prepare**
 **ln -s /usr/src/linux /lib/modules/`uname -r`/build**

3. Get Asterisk Packages
**cd /usr/src**
**svn checkout [http://svn.digium.com/svn/asterisk/branches/1.2](http://svn.digium.com/svn/asterisk/branches/1.2) asterisk-1.2**
[B]svn checkout [http://svn.digium.com/svn/zaptel/branches/1.2](http://svn.digium.com/svn/zaptel/branches/1.2) zaptel-1.2
svn checkout [http://svn.digium.com/svn/libpri/branches/1.2](http://svn.digium.com/svn/libpri/branches/1.2) libpri-1.2
svn checkout [http://svn.digium.com/svn/asterisk-sounds/branches/1.0](http://svn.digium.com/svn/asterisk-sounds/branches/1.0) asterisk-sounds-1.0

[/B]
4. Compile Stuff
-=libpri=-
[B]cd /usr/src/libpri-1.2
make clean
make
make install
[/B]-=Zaptel Modules=- (If you're going to use zaptel hardware to connect to PSTN)
[B]cd /usr/src/zaptel-1.2
[/B]Change anything in /usr/src/zaptel/zconfig.h if you need to (I didn't need to)
[B]make clean
make linux26
make zttool
make install
[/B]-=Asterisk=-
[B]cd /usr/src/asterisk-1.2
make clean
make mpg123

note: This doesn't work for me as of 2-20-07.  I had to go into the mpg123 directory myself and type:

[/B]> [FONT=monospace]make CC=gcc LDFLAGS= OBJECTS='decode_i386.o dct64_i386.o decode_i586.o audio_oss.o term.o' CFLAGS='-DI386_ASSEM -DPENTIUM_OPT -DREAL_IS_FLOAT -DLINUX  -DREAD_MMAP -DOSS -DTERM_CONTROL -Wall -O2 -m486 -fomit-frame-pointer -funroll-all-loops -finline-functions -ffast-math' mpg123-make[/FONT][B]
make
make install
make samples[/B] (if you want sample config files put into /etc/asterisk)
-=Asterisk-Sounds=-
[B]cd /usr/src/asterisk-sounds-1.0
make install
[/B]
5. Edit udev
**vi /etc/udev/udev.rules**

Stick the paragraph below somewhere

[B]# Section for zaptel device
KERNEL="zapctl",     NAME="zap/ctl"
KERNEL="zaptimer",   NAME="zap/timer"
KERNEL="zapchannel", NAME="zap/channel"
KERNEL="zappseudo",  NAME="zap/pseudo"
KERNEL="zap[0-9]*",  NAME="zap/%n"[/B]

6.  That's the installation part.  Go ahead and reboot.  Then, if you have some zaptel piece of hardware installed, try **lsmod | grep zap** and see if the two modules are already installed.

7.  Configure it!

================[LIST]
[*]Excelent source of asterisk info: [The Free Asterisk O'Reilly Book]("http://voipspeak.net/images/stories/orielly/AsteriskTFOT.zip")
[*]A good forum for questions: [http://forums.digium.com/](http://forums.digium.com/)[/LIST]edit: removed extra steps to manually compile mpg123 that weren't necessary.
edit2: removed tar extraction step since svn brings the files over untarred. (duh)
edit3: Added some explanation notes.
edit4: Added mpg123 compile note 2-20-07

---

### Post by kennedymat on 2006-03-09
I'm having a problem that I'm guessing is udev related. 

I built the zaptel drivers successfully and rebooted using the directions found here: 

[http://www.voip-info.org/wiki/index.php?page=Asterisk+Zaptel+Installation](http://www.voip-info.org/wiki/index.php?page=Asterisk+Zaptel+Installation) 

When I enter 

modprobe zaptel 

I receive: 

FATAL: Module zaptel not found. 

I am using Ubuntu 5.1, and I believe that is the nature of the problem. 

In the /etc/udev/rules.d folder, there was no file named 50-udev.rules. Instead, there was a symbolic link to ../udev.rules, and in the file ../udev.rules I found that the zaptel definitions had already been included, except that they used an "==" in the KERNEL statements rather than a single "=".  I tried modifying them, adding new ones, etc., but nothing has worked.

I did some googling and decided to copy the ../udev.rules to the /etc/udev/rules.d folder under the name 50-udev.rules. I rebooted and it still didn't work. 

So, I moved the file 50-udev.rules up to the parent directory and created a symbolic link to the new location named 50-udev.rules, but it still doesn't work. 

I have confirmed that the file /etc/modprobe.d/zaptel is the output from my zaptel build.

Clearly, I'm missing a very simple point, but I just can't find it. 

Thanks in advance for any help.

---

### Post by fizgig on 2006-03-09
Well, if you didn't do it my way I don't think I'm smart enough to help you.

---

### Post by kennedymat on 2006-03-09
fizgig,

You underestimate your abilities!  By closely examining what you did and comparing to what I did, then doing some trial and error, I found my issue.

In the other tutorial, it says:

For a Linux 2.6 kernel you may need to:
   modify the EXTRAVERSION statement in Makefile so it matches what you see in: cat /proc/version 

To clarify that, if your cat/proc/version says (for example):

Linux version 2.6.12-mytestbuild (root@agpcserver) (gcc version 3.4.5 20050 809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Wed Mar 8 18:01

Then the line in your Makefile should be:

EXTRAVERSION =-mytestbuild

It was your example that saved me.

Thanks!

---

### Post by fizgig on 2006-03-09
sweet! So I helped someone!

---

### Post by kennedymat on 2006-03-10
I am sure I am missing something very easy. 

I have installed my TDM400 with 4 FXO ports to connect to loopstart lines. 

I've got the drivers loaded, the zttool tells me it sees the 4 channels, but asterisk is not recognizing them.

One clue is that the output from my asterisk console never indicates that asterisk is attempting to parse /etc/asterisk/zapata.conf.  If it never parses it, it will never see the channels.

Any hints?



From /etc/zaptel.conf: 

fxsls=1-4 
loadzone = us 
defaultzone=us 

From /etc/asterisk/zapata.conf: 

[trunkgroups] 
[channels] 
usercallerid=yes 
hidecallerid=no 
callwaiting=no 
threewaycalling=yes 
transfer=yes 
echocancel=yes 
echotraining=yes 

context=PublicNetworkRingin 
signalling=fxs_ls 

channel => 1 
channel => 2 
channel => 3 
channel => 4 

In the Asterisk console, if I type: 

show channels 

I get: 

Channel (Context Extension Pri ) State Appl. Data 
0 active channel(s) 


In the zttool, I do see the card: 

Alarms Span &#9474; 
&#9474; OK Wildcard TDM400P REV I Board 1 &#9618; &#9474; 


In the zttool, when I look at the channels, they seem to be there, but no amount of plugging in, unplugging, or ringing in seems to change the status; 


Current Alarms: No alarms. &#9474; &#9474; 
&#9474; &#9474; Sync Source: Internally clocked &#9474; &#9618; &#9474; 
&#9474; &#9474; IRQ Misses: 0 &#9474; &#9618; &#9474; 
&#9474; &#9474; Bipolar Viol: 0 &#9474; &#9618; &#9474; 
&#9474; &#9474; Tx/Rx Levels: 0/ 0 &#9474; &#9618; &#9474; 
&#9474; &#9474; Total/Conf/Act: 4/ 4/ 1 &#9474; &#9618; &#9474; 
&#9474; &#9474; &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488; &#9474; &#9618; &#9474; 
&#9474; &#9474; 1234 &#9474; Back &#9474; &#9474; &#9618; &#9474; 
&#9474; &#9474; TxA ---- &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; &#9474; &#9618; &#9474; 
&#9474; &#9474; TxB ---- &#9474; &#9618; &#9474; 
&#9474; &#9474; TxC ---- &#9474; &#9474; 
&#9474; &#9474; TxD ---- &#9474; &#9474; 
&#9474; &#9474; &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488; &#9474; &#9474; 
&#9474; &#9474; RxA ---- &#9474; Loop &#9474; &#9474; &#9474; 
&#9474; &#9474; RxB ---- &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; &#9474; &#9474; 
&#9474; &#9474; RxC ---- &#9474; &#9474; 
&#9474; &#9474; RxD ---- 


On the physical card, all four green LEDs are lit all of the time. 

If I ring in on any of the lines, Asterisk completely ignores the ringin. 

From /etc/asterisk/extensions.conf: 

[PublicNetworkRingin] 
exten => s,1,answer() 
exten => s,2,echo()

---

### Post by kennedymat on 2006-03-10
OK Fizgig, you win.

I see now that the asterisk I got from Ubuntu doesn't include chan_zap.  It looks like I need to compile the thing myself.

Ubuntu was my first try at Linux, and for all the nice things people say about it I think I'll probably try a different distro next time around.  

The feature I THOUGHT I would like best was the ability to simply grab packages and have them work ALMOST right out of the box.  Instead, I've spent hours fixing things that would have probably worked the first time if I had just built them myself inside a more standard Linux.

I guess that's the open source way.  Read, try, cry, repeat.

---

### Post by fizgig on 2006-03-10
Well, good luck in your linux adventure.  I will say that I've tried a lot of distros (debian, mepis, xandros, mandrake, redhat) and I always keep coming back to Ubuntu.

Anyhow, the zaptel modules need to be compiled against the specific kernel you have installed.  While ubuntu does include a few custom modules to save you from compiling, I think zaptel modules are a little too out there for a regular distribution to supply.

Besides, the zaptel code keeps changing so it's easier to use the subversioning system to update them directly from the source instead of waiting for the packager to make them.  A compile takes about 15 seconds so I don't see it as a big deal.

Each to his own I guess.

p.s. you might want the line that reads  **fxsls=1-4** to be **fxsks-1-4**

---

### Post by kennedymat on 2006-03-13
Thanks for the info.

It's not the zaptel drivers that I'm having trouble with, it's that the asterisk that you get from Ubuntu using Synaptic Package Manager does not include the chan_zap module in the asterisk build.  So, the drivers are running great, but asterisk never goes looking for the channels!

In terms of using kewlstart instead of loopstart, I'm an old-school telephony guy, so I'm sticking with what I know until it is working, then I'll try the new stuff.

Thanks again.  I'm working my way through your tutorial now.

---

### Post by kennedymat on 2006-03-14
Hey fizgig,

I'm trying it your way and have followed everything step-by-step three times now.  Each time I try to do:

make mpg123

I get all of the following, and then nothing compiles correctly afterward.  By the way, I actuall do "sudo make mpg123", but I wouldn't think that would be the difference.  

It appears to me that it is compiling and tryint to optimize for an Intel system (I have an AMD-64), so I'm guessing I need to do something like 'make mpg123 amd-64', but I don't see that option.

Any hints?


[ -f mpg123-0.59r.tar.gz ] || wget [http://www.mpg123.de/mpg123/mpg123-0.59r.tar.gz](http://www.mpg123.de/mpg123/mpg123-0.59r.tar.gz)
[ -d mpg123-0.59r ] || tar xfz mpg123-0.59r.tar.gz
make -C mpg123-0.59r linux
make[1]: Entering directory `/usr/src/asterisk-1.2/mpg123-0.59r'
make CC=gcc LDFLAGS= \
        OBJECTS='decode_i386.o dct64_i386.o decode_i586.o \
                audio_oss.o term.o' \
        CFLAGS='-DI386_ASSEM -DPENTIUM_OPT -DREAL_IS_FLOAT -DLINUX \
                -DREAD_MMAP -DOSS -DTERM_CONTROL\
                -Wall -O2 -m486 \
                -fomit-frame-pointer -funroll-all-loops \
                -finline-functions -ffast-math' \
        mpg123-make
make[2]: Entering directory `/usr/src/asterisk-1.2/mpg123-0.59r'
make[3]: Entering directory `/usr/src/asterisk-1.2/mpg123-0.59r'
gcc -DI386_ASSEM -DPENTIUM_OPT -DREAL_IS_FLOAT -DLINUX          -DREAD_MMAP -DOSS -DTERM_CONTROL                -Wall -O2 -m486                 -fomit-frame-pointer -funroll-all-loops                 -finline-functions -ffast-math   -c -o mpg123.o mpg123.c
mpg123.c: In function &#8216;shuffle_files&#8217;:
mpg123.c:225: warning: implicit declaration of function &#8216;time&#8217;
mpg123.c: At top level:
mpg123.c:480: warning: initialization makes integer from pointer without a cast
gcc -DI386_ASSEM -DPENTIUM_OPT -DREAL_IS_FLOAT -DLINUX          -DREAD_MMAP -DOSS -DTERM_CONTROL                -Wall -O2 -m486                 -fomit-frame-pointer -funroll-all-loops                 -finline-functions -ffast-math   -c -o common.o common.c
gcc -DI386_ASSEM -DPENTIUM_OPT -DREAL_IS_FLOAT -DLINUX          -DREAD_MMAP -DOSS -DTERM_CONTROL                -Wall -O2 -m486                 -fomit-frame-pointer -funroll-all-loops                 -finline-functions -ffast-math   -c -o decode_i386.o decode_i386.c
gcc -DI386_ASSEM -DPENTIUM_OPT -DREAL_IS_FLOAT -DLINUX          -DREAD_MMAP -DOSS -DTERM_CONTROL                -Wall -O2 -m486                 -fomit-frame-pointer -funroll-all-loops                 -finline-functions -ffast-math   -c -o dct64_i386.o dct64_i386.c
as   -o decode_i586.o decode_i586.s
decode_i586.s: Assembler messages:
decode_i586.s:44: Error: suffix or operands invalid for `push'
decode_i586.s:45: Error: suffix or operands invalid for `push'
decode_i586.s:46: Error: suffix or operands invalid for `push'
decode_i586.s:47: Error: suffix or operands invalid for `push'
decode_i586.s:67: Error: suffix or operands invalid for `push'
decode_i586.s:70: Error: suffix or operands invalid for `push'
decode_i586.s:81: Error: suffix or operands invalid for `push'
decode_i586.s:83: Error: suffix or operands invalid for `push'
decode_i586.s:86: Error: suffix or operands invalid for `push'
decode_i586.s:161: Error: suffix or operands invalid for `pop'
decode_i586.s:211: Error: suffix or operands invalid for `pop'
decode_i586.s:296: Error: suffix or operands invalid for `pop'
decode_i586.s:315: Error: suffix or operands invalid for `pop'
decode_i586.s:316: Error: suffix or operands invalid for `pop'
decode_i586.s:317: Error: suffix or operands invalid for `pop'
decode_i586.s:318: Error: suffix or operands invalid for `pop'
make[3]: *** [decode_i586.o] Error 1
make[3]: Leaving directory `/usr/src/asterisk-1.2/mpg123-0.59r'
make[2]: *** [mpg123-make] Error 2
make[2]: Leaving directory `/usr/src/asterisk-1.2/mpg123-0.59r'
make[1]: *** [linux] Error 2
make[1]: Leaving directory `/usr/src/asterisk-1.2/mpg123-0.59r'
make: *** [mpg123] Error 2

---

### Post by kennedymat on 2006-03-15
I pushed through the process and ran into a few more bumps along the way, but finally got Asterisk up and running.  Unfortunately, I didn't take very good notes along the way so I don't want to post my steps here.

Thanks fizgig for your help.

I never did get mpg123 compiled, so I'll need to go find out what that particular module does.

---

### Post by fizgig on 2006-03-15
Well, I just noticed that I have an extra unneccessary step in my steps since **make mpg123** not only downloads the source for mpg123 and extracts it, it also compiles it for you so I just removed the step where I recompile.

I did a search on [google]("http://www.google.com/search?hl=en&q=compile+mpg123+amd+64&btnG=Google+Search") about your problem and found [this]("http://www.voip-info.org/wiki-Asterisk+mpg123+redhat") where somebody says that mpg123 doesn't compile on AMD64.  I found a few other similar posts so it might be that you'll need a patch to get that version to compile.  I wasn't able to find a patch like that after 5 minutes of searching but you might have better luck than me.

---

### Post by fizgig on 2006-03-18
[quote=kennedymat]I pushed through the process and ran into a few more bumps along the way, but finally got Asterisk up and running.  Unfortunately, I didn't take very good notes along the way so I don't want to post my steps here.

Thanks fizgig for your help.

I never did get mpg123 compiled, so I'll need to go find out what that particular module does.[/quote]

mpg123 allows you to play mp3's.  Nothing more.

---

### Post by miggl on 2006-03-28
Thanks for the walkthrough fizgig! I finally got everything installed thanks to you !!!! Great help!

I would like to post this help on my blog, since it helped me out tons (with your permission of course).

Thanks,
Mike

---

### Post by fizgig on 2006-03-28
So glad I could help!  Feel free to post it wherever.  Say you wrote it.  Improve it.  Doesn't matter to me!

---

### Post by honeydew on 2006-04-06
haruumm.. got asterisk up and running and can call into the asterisk box from my did.. but I cant for the life of me figure out how to set it up to dail out.. Im using the iax protocol..  hrmm.. Ill post some output later.. does can anyone post up there iax.confs? if they are running softphones?

---

### Post by miggl on 2006-04-10
[QUOTE=fizgig]So glad I could help!  Feel free to post it wherever.  Say you wrote it.  Improve it.  Doesn't matter to me![/QUOTE]

Thanks, I'll have you in there with full credit, of course!

Hey, another thing: I've been able to install it. But now what? I'll admit, I like GUIs... is there a config GUI that can get me started? Or is it really all command-line based?

Thanks again!

---

### Post by fizgig on 2006-04-11
Well, if you like gui's, then you'll probably want to install [asterisk@home]("http://asteriskathome.sourceforge.net/").  It's much easier to use with its included gui but it's based on centos so you'll have to learn how that works (centos=free redhat).

I didn't like the gui since it forces you into a certain template without your own custom stuff.  Dialplans aren't hard to learn.  Check out the link to the free O'reilly book about Asterisk you can download that I posted at the end of my first post.  It walks you through it and you get to really understand how it works.

---

### Post by Cavaco on 2006-04-20
Does the module exist in /lib/modules/XXXXXX/misc where xxx is the kernel headers you used ?

---

### Post by Cavaco on 2006-04-20
Can you be more specific on your setup ?

---

### Post by fizgig on 2006-04-20
huh? specific?  Can you be more specific about what you want me to be specific about?

Also, I'll look into your modules question when I get home.

---

### Post by disterics on 2006-05-10
The mpg123 patch for amd64 can be found here: 
[http://www.gentoo.org/cgi-bin/viewcvs.cgi/media-sound/mpg123/files/mpg123-0.59r-amd64.diff](http://www.gentoo.org/cgi-bin/viewcvs.cgi/media-sound/mpg123/files/mpg123-0.59r-amd64.diff)

Download it into a clean mpg123-0.59r directory. 
cd into the directory
```

user@box: patch < mpg123-0.59r-amd64.diff 
user@box: make linux-x86_64
```

---

### Post by ncksm on 2007-03-02
Does anyone have this patch, cause the link is dead. Thanks

---

### Post by disterics on 2007-03-02
I attached it as a text file. Not sure how relevant it is at the moment though.

---

### Post by ncksm on 2007-03-03
Thanks. It's working now !!!

---

