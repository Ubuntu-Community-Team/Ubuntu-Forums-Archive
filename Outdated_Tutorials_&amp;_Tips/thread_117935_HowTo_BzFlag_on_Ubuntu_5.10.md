---
title: "HowTo: BzFlag on Ubuntu 5.10"
date: 2006-01-15
forum: Outdated Tutorials &amp; Tips
---

### Post by flight_master on 2006-01-15
**What is [BzFlag](http://www.bzflag.org)**:

BzFlag (or Bzfs for short) is a:

> BZFlag is a free multiplayer multiplatform 3D tank battle game. The name stands for Battle Zone capture Flag. It runs on Irix, Linux, *BSD, Windows, Mac OS X and other platforms. It's one of the most popular games ever on Silicon Graphics machines. 


[COLOR="Red"]Why **NOT** to Use APT-GET[/COLOR]:

The version which is in the Breezy repositories has two issues. Firstly, it is version 2.0.2, which has issues with high latency spikes. And secondly, (very important!) You can't shoot anyone :razz: Seriously, bullets will go right through the other tanks, 100% of the time!

**Installation Instructions:**
[LIST=1]
[*][Download](http://ftp.bzflag.org/bzflag/bzflag-2.0.4.20050930.tar.gz) the latest version of BzFlag (2.0.4)
[*]Now, we'll need to install some missing packages; 
```
sudo apt-get install libsdl1.2-dev
sudo apt-get install libcurl3-dev
```
[*]Unpack it; open a k/console, and 'cd' to the directory where you downloaded. I'm assuming Desktop/ here. ```
 tar zxvf  bzflag-2.0.4.20050930.tar.gz
```
[*]You will now have a folder called 'bzflag-2.0.4.20050930'. You will want to change into this directory, again using 'cd'.
[*]Now, comes the fun part; Ubuntu is using the GCC version 4.0 compiler, which causes certain issues (bugs) with BzFlag. These issues are caused by a very high optimization level. To solve this issue, type into your console: ```
 export CXXFLAGS=-O1
```
[*]Now, You will need to run: ```
./configure
```. The output from this should say BzFlag Client at the very bottom.
[*]If all is right, compile it by typing: ```
make
```
[*]Finally, you'll need to install it; do this by entering: ```
 sudo checkinstall
```
[*]This step is optional, but always a good idea; after installing it, clean your source directory - that way, when you compile the next time, you'll be using fresh sources. Do this by entering: ```
make clean
```.
[*]Your done! Test out BzFlag by entering: ```
bzflag
``` in the console. 
[/LIST]

Have fun, and watch out for Guided Missiles! ;)

I hope this helps ya'll!
-Christian

---

### Post by flight_master on 2006-02-03
*fixed a few typos, and updated package name

---

### Post by durand on 2006-02-04
It might be better to do ```
sudo checkinstall
``` instead as this creates a deb, installs it and it also means u can **dpkg -r packagename** or **apt-get remove packagename** it to remove it. It would probbly be a better method.
Nice HowTo by the way.:)

---

### Post by durand on 2006-02-04
It might be better to do ```
sudo checkinstall
``` instead of ```
sudo make install
``` as this creates a deb, installs it and it also means u can **dpkg -r packagename** or **apt-get remove packagename** it to remove it. It would probbly be a better method.
Nice HowTo by the way.:)

---

### Post by johannes on 2006-02-04
Nice guide! Thanks.

I also think checkinstall is a better option.

---

### Post by flight_master on 2006-02-04
@durand: Thanks for the input - I've updated the HOWTO to use checkinstall instead ;)

@johannes,

Thanks :D

-Christian

---

### Post by pianoboy3333 on 2006-02-05
Great guide!

---

### Post by CallsignBaron on 2006-02-08
Wonder if you can help me. I am a newbie to Ubuntu and especially new to command line functions. I have followed this tutorial and seem to have run into a snag at about step #7. Here is the error:

configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
todd@24-176-84-202:~/bzflag-2.0.4.20050930$ sudo checkinstall
sudo: checkinstall: command not found
todd@24-176-84-202:~/bzflag-2.0.4.20050930$ make clean
bash: make: command not found
todd@24-176-84-202:~/bzflag-2.0.4.20050930$ bzflag
bash: bzflag: command not found
todd@24-176-84-202:~/bzflag-2.0.4.20050930$

I obviously do not have something installed or installed correctly to allow me to install a program in this manner. If you would be so kind as to let me know what I need to do from here it would be greatly appreciated. I was so close and as you can imagine was disappointed to see this error. I had bzflag in suse and I miss it greatly. I ran into the same problem with the version I got with apt-get, it ran wonderfully but I couldn't shoot anyone. Thanks for your help.

---

### Post by flight_master on 2006-02-08
Hello and welcome to Ubuntu!

I'm guessing you are using a very clean system, right out of the box, so you are going to need a few extra tools (compilers, and build-tools)

open a console and type in:

```

sudo apt-get install build-essential gcc g++ 

```

If you do this, and still get errors, please post the output of the ./configure command. When doing this, though, make sure to put it inbetween code tags ;)

Regards,
Christian

---

### Post by CallsignBaron on 2006-02-08
Thanks for your quick reply flight_master. You are correct this is a fresh install, very clean and I figured I was missing something. I will give this a shot and let you know the outcome. If you can tell me what "put in between code tags" means I will be more than happy to comply. :)
 
Thanks,
Todd

---

### Post by flight_master on 2006-02-08
No problem! Good luck :p 

Guess I spend too much time on forums & Ubuntu :D what I mean by 'code' tags is, enclosing the output between:

[code ]
<PASTE YOUR OUTPUT FROM ./configure HERE>
[/code ] 
Or else, it'll screw up the forum layout, not to mention make it hard to read

-Christian

---

### Post by CallsignBaron on 2006-02-08
FYI-BZ Flag is installed! Thank you very much for your help! The only problem I had was I couldn't do a "sudo checkinstall", I got the error "no such command" but I did "make install" and it went flawlessly. I don't know if I need to install something else to do a checkinstall. It works perfectly now and and I can blow up the bad guys! (just what my wife wanted to hear! lol) Thanks for your help once again. I am really loving Ubuntu, everything really seems to work very well. I just switched from SuSE and never thought I would ever do that. Also, the forums are very helpful and it really seems like a very friendly community. I believe I'm here to stay.

Regards,

Todd

---

### Post by CallsignBaron on 2006-02-08
Also, I'll remember the code tags for next time! Thanks ;)

---

### Post by flight_master on 2006-02-08
> FYI-BZ Flag is installed! Thank you very much for your help! The only problem I had was I couldn't do a "sudo checkinstall", I got the error "no such command" but I did "make install" and it went flawlessly. I don't know if I need to install something else to do a checkinstall. It works perfectly now and and I can blow up the bad guys! (just what my wife wanted to hear! lol) Thanks for your help once again. I am really loving Ubuntu, everything really seems to work very well. I just switched from SuSE and never thought I would ever do that. Also, the forums are very helpful and it really seems like a very friendly community. I believe I'm here to stay.

I'm glad you have it running! Yes, you need to do:

```
sudo apt-get install checkinstall
```

in order to use checkinstall. I'm glad you plan on staying with Ubuntu!

-Christian

---

### Post by CallsignBaron on 2006-02-08
Got it now! Thanks again.

-Todd

---

### Post by transistor on 2006-02-09
All going well until step 6. ./configure returns "No such file or directory."

Any ideas? I can't find ./configure in the sub-dirs.

Thanks for the effort on the How-To. They're a real help.

---

### Post by flight_master on 2006-02-09
Could you try ./configure again, but when it comes to "No Such File or Directory", could you please paste the output of:

```
pwd
``` 
I'm guessing you are in the wrong directory... but just to make sure ;)

-Christian

---

### Post by transistor on 2006-02-10
Thanks flight_master.

/home/*username*/Desktop contains
```
bzflag-2.0.4.20050930-i386-Opkg  
bzflag-2.0.4.20050930-i386-Opkg.tar.gz

```
Running ./configure from Desktop gives "No such file or directory."

Changing to the bzflag directory
/home/*username*/Desktop/bzflag-2.0.4.20050930-i386-Opkg
gives the same result.

Thanks.

---

### Post by flight_master on 2006-02-10
Hi,

Sorry for the delay, between my flu, this snowstorm, and tests, life is pain :P

Anyway, it seems that you downloaded the wrong package? Can you try again, by downloading this package: [http://internap.dl.sourceforge.net/sourceforge/bzflag/bzflag-2.0.4.20050930.tar.gz](http://internap.dl.sourceforge.net/sourceforge/bzflag/bzflag-2.0.4.20050930.tar.gz)

And see if that works for you ;)

Regards,
Christian

---

### Post by transistor on 2006-02-11
Thanks, flight_master. Yes I had downloaded a different version. I've had a bit of bother with the sourceforge mirror but successfully downloaded the correct version of the file.
When I un-tarred the file the end of the operation reads:
```

bzflag-2.0.4.20050930/src/regex/Makefile.am
bzflag-2.0.4.20050930/src/regex/utils.h
bzflag-2.0.4.20050930/NEWS
bzflag-2.0.4.20050930/configure

gzip: stdin: unexpected end of file
tar: Read 2649 bytes from bzflag-2.0.4.20050930.tar.gz
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
```
This didn't look promising and sure enough running ./configure returns
```
./configure: line 1173: syntax error: unexpected end of file
```
I'll try downloading again.
Weather is good here in Ireland. Apparently the sea around Ireland is 2 degrees C warmer than usual (thanks to the Gulf Stream coming over from the Gulf of Mexico).

---

### Post by flight_master on 2006-02-11
Hmm....

That error is one of the excellent corrupted-tar errors! It seems that when you downloaded the archive, it somehow got corrupted. No worries; I've uploaded a temp. copy here: [http://montecarlohosting.net/bzflag-2.0.1.20050930.tar.gz](http://montecarlohosting.net/bzflag-2.0.1.20050930.tar.gz)

Interesting... They say that's the same flow which is dumping all this snow onto us. Apparently, you guys are getting the better deal! :D

-Christian

---

### Post by transistor on 2006-02-12
Thanks for the tar. It's labeled bzflag-2.0.1.20050930 but it's 2.0.4 inside!
The make ran for about 30 minutes and quit cleanly.
'checkinstall' returns 'Command not found' so I guess it's not installed on my machine. It's not available on Synaptic and 'apt-get checkinstall' returns
```
E: Invalid operation checkinstall
```

So the status is I don't have checkinstall and don't have bzflag. 
```
~/games/bzflag-2.0.4.20050930$ bzflag
bash: bzflag: command not found

```
Here's the content of ~/games/bzflag-2.0.4.20050930
```
aclocal.m4      ChangeLog      include      plugins         README.UNIX
AUTHORS         config.log     INSTALL      PORTING         README.WIN32
autogen.sh      config.status  libtool      README          README.XMINGW
BUGS            configure      m4           README.BeOS     RELNOTES
bzflag.info     configure.ac   Makefile     README.DEVC++   src
bzflag.info.in  COPYING        Makefile.am  README.IRIX     TODO
bzflag.lsm      data           Makefile.in  README.Linux    tools
bzflag.lsm.in   debian         man          README.MacOSX   win32
bzflag.spec     Dev-C++        misc         README.MINGW32
bzflag.spec.in  DEVINFO        NEWS         README.SDL
BZFlag.xcode    doc            package      README.SOLARIS
```

Thanks for all the help. I've needed some job to learn how to do some of this stuff and one learns very little when an install goes flawlessly.

---

### Post by skymt on 2006-02-12
[QUOTE=transistor]Thanks for the tar. It's labeled bzflag-2.0.1.20050930 but it's 2.0.4 inside!
The make ran for about 30 minutes and quit cleanly.
'checkinstall' returns 'Command not found' so I guess it's not installed on my machine. It's not available on Synaptic and 'apt-get checkinstall' returns
```
E: Invalid operation checkinstall
```[/QUOTE]

It's 'sudo apt-get *install* checkinstall'. I know, it doesn't really make sense. apt-*get* should *get* the package by default, but that's how it is. *sigh*

Also, it isn't actually necessary to compile BZFlag yourself. The latest version is in [Breezy Backports](https://wiki.ubuntu.com/UbuntuBackports). Some people don't want the additional instability adding backports can create (a few packages from the GNOME 2.13 branch are there), but I like living life on the edge. :cool: 

Since Backports is an official Ubuntu repository, the newest BZFlag packages are available in the pool [here](http://archive.ubuntu.com/ubuntu/pool/universe/b/bzflag/). 2.0.4 is toward the bottom.

---

### Post by xtacocorex on 2006-02-12
Thanks for the nice HowTo. I've seen this game in the repos but never installed, so I'm glad I found this.

I'm glad I followed it too as I probably wouldn't have added the compiler flags and screwed up something.

I'm so going to be unproductive this semester now...

---

### Post by Kaobear on 2006-02-12
Worked liek a charm.  Thanks for the HOW-TO

---

### Post by flight_master on 2006-02-12
[quote=skymt]It's 'sudo apt-get *install* checkinstall'. I know, it doesn't really make sense. apt-*get* should *get* the package by default, but that's how it is. *sigh*

Also, it isn't actually necessary to compile BZFlag yourself. The latest version is in [Breezy Backports]("https://wiki.ubuntu.com/UbuntuBackports"). Some people don't want the additional instability adding backports can create (a few packages from the GNOME 2.13 branch are there), but I like living life on the edge. :cool: 

Since Backports is an official Ubuntu repository, the newest BZFlag packages are available in the pool [here]("http://archive.ubuntu.com/ubuntu/pool/universe/b/bzflag/"). 2.0.4 is toward the bottom.[/quote]

Actually, they still have the bug with GCC ;)

Ah, the love of packages. You still can't go wrong with a compile :D

-Christian

---

