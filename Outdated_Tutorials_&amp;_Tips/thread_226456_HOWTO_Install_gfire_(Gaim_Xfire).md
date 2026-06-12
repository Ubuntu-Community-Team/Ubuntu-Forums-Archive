---
title: "HOWTO: Install gfire (Gaim Xfire)"
date: 2006-07-31
forum: Outdated Tutorials &amp; Tips
---

### Post by Indrek on 2006-07-31
gfire is Gaim-Xfire wich you can chat with your xfire contacts in gaim.
i made this howto beacause it was tricky to get work it.

[LIST=1]
[*]First at all we download the package, download the latest version (0.58).
[https://sourceforge.net/project/showfiles.php?group_id=141362&package_id=155388]("https://sourceforge.net/project/showfiles.php?group_id=141362&package_id=155388")
[*]We must install gaim-dev too:
```
sudo apt-get install gaim-dev
```
[*]Now we are going to unpack and install it.
```
tar -xpf /home/youruser/Desktop/gaim-xfire-0.5.8.tar.gz
```
change "youruser" to your ubuntu user.
next thing what we are doing is going into directory:
```
cd /home/youruser/Desktop/gaim-xfire-0.5.8
```
again change "youruser" to your ubuntu user.
now we install:
```
sudo ./configure --with-gaim=/usr/lib/pkgconfig/ --prefix=/usr && make && make install
```
after that you can remove gaim-xfire-0.5.8 directory.
[*]Thats it!
[/LIST]

---

### Post by Kozuka on 2006-08-01
/usr/bin/install: cannot create regular file `/usr/lib/gaim/libxfire.so': Permis sion denied

WTF?!?! I'm logged as Super User?

Any ideas lads, thanks.

Kozuka

I even tried chmoding the folder no luck.

---

### Post by ericesque on 2006-08-01
Pray tell, does it work quite quitely with Gaim 2.0 beta?

---

### Post by gschoper on 2006-08-01
> **Kozuka said:**
> /usr/bin/install: cannot create regular file `/usr/lib/gaim/libxfire.so': Permis sion denied

WTF?!?! I'm logged as Super User?

Any ideas lads, thanks.

Kozuka

I even tried chmoding the folder no luck.

Try:
```

./configure --with-gaim=/usr/lib/pkgconfig/ --prefix=/usr && make && sudo make install

```

---

### Post by Pandora on 2006-08-02
I half followed this how to. I wanted to make something more permanent out of the source code. I tried making a .deb for kicks and I got everything to compile and was able to install my package. Big problem though...My package causes gaim to segfault when I try to login to xfire. 

Anyone else experiencing segfaults with this program and the gaim that's packaged with ubuntu 6.06.....or is it just my package? 

The reason I want a package is because having a package manager take care of the install is so much nicer than trying to do a makeinstall IMHO.

---

### Post by Hairy_Palms on 2006-08-02
works for me with checkinstall, but its a shame that it wont woprk with gaim2 :(

---

### Post by Pandora on 2006-08-02
> **Hairy_Palms said:**
> works for me with checkinstall, but its a shame that it wont woprk with gaim2 :(

Yep, I just tried checkinstall and I'm not segfaulting. I wasn't able to retrieve my buddy list when I logged on either....but that maybe a limitation of the program in its current state? 

Although I would like to debianize the source and submit it back to the maintainer. Checkinstall works for me right now though as a temporary fix for me not wanting to "make install". Thanks for the tip!:D

---

### Post by Pandora on 2006-08-02
Well I don't mean to take any of the steam away from whats been said here. The howto along with the additional comments are a sure fire way to get gaim-xfire(gfire, xfire-gaim plugin) to work. 

I did however using my limited knowledge of the the debian packaging system manage to debianize the source somewhat.

You can grab what I've done here for an easy install hopefully. You can only use this with gaim 1.5(the one that comes with 6.06)

[http://www.lightningseed.org/xfireplugin](http://www.lightningseed.org/xfireplugin)

I'm not a pro at this nor do I offer any guarantee that my packages will work. Please use this at your own risk. Hopefully it helps make this process easier.

My intention was to just eliminate the need for extra downloads(and the hard drive space taken up by those downloads), time spent compiling, and a makeinstall.  I would really like to see support for this chat system added  to gaim by default someday.:D

---

### Post by Whoopie on 2006-08-03
Hi,

just found a thread about a script to update the recognized games.

[https://sourceforge.net/forum/forum.php?thread_id=1489016&forum_id=474406](https://sourceforge.net/forum/forum.php?thread_id=1489016&forum_id=474406)

Best regards,
Whoopie

---

### Post by boast on 2006-08-06
Trying to install gaim-dev I get "The following packages have unmet dependencies:
  gaim-dev: Depends: libglib2.0-dev but it is not going to be installed
E: Broken packages"

So I tried installing libglib2.0-dev but it said "Depends: libglib2.0-0 (=2.10.2-1ubuntu3) but 2.10.3-0ubuntu1 is to be installed"

So I tried installing 2.10.3 but I get "configure: error: no acceptable C compiler found in $PATH"

---

### Post by gommle on 2006-08-08
I get this error when trying to install Gaim-dev.
> Følgende pakker har uinnfridde avhengighetsforhold:
  gaim-dev: Avhenger av: gaim (= 1:1.5.0+1.5.1cvs20051015-1ubuntu10) men 1:1.9.99.is.2.0.0+beta3-1ubuntu1 skal installeres
            Avhenger av: gaim-data (= 1:1.5.0+1.5.1cvs20051015-1ubuntu10) men 1:1.9.99.is.2.0.0+beta3-1ubuntu1 skal installeres
E: Ødelagte pakker
gommle@nerd0:~$

Avhenger = depends.

Any ideas?

---

### Post by Snoopy381 on 2006-08-10
great HOW TO :D

got my gfire up and running pretty easily.


just as a note for these instructions to work you need a c compiler installed. (think iv got gcc )

also to start with i was getting the same permission denied error as Kozuka. 

i changed the last command around a bit and this is what worked for me:

```
sudo ./configure --with-gaim=/usr/lib/pkgconfig/ --prefix=/usr && make && sudo make install
```
  
just using sudo twice :p



**E:**
oh yeh, forgot somtin.

after youve got gfire installed and youve made a xfire acount in gaim you need to go to go to the properties of that account and change the version number to the current version.

the current version as of this post (10th August 2006) is 59.

you can find the current version of xfire by running the xfire.exe either in windowz or in wine. on the first screen that comes up (the login screen) down the bottom it has the version number ( 1.59 at or 10th August 2006).

note: the windows verson says 1.59, but for gaim you should use 59.


** EE: **

you can also find out the latest version of xfire by going to the download page on the xfire website [http://www.xfire.com/download](http://www.xfire.com/download)

---

### Post by shat on 2006-08-15
Note:  It does not play well with Gaim 2.0 betas.  

My gfire w/ 1.5 seems like it deleted all of my xfire contacts.  I log in, but none of my contacts are ever online.  Others don't see me in their online or offline list.  No good..

This would be a good project to pick up and get up to speed for Gaim 2.0 plugin support..

---

### Post by reptyle on 2006-08-18
I'm one of the authors for the plugin.

I've basically completely rewritten the plugin for gaim 2.0.0b3

You can find release information here, which includes links to the dapper packages.
[http://sourceforge.net/forum/forum.php?thread_id=1556186&forum_id=474406](http://sourceforge.net/forum/forum.php?thread_id=1556186&forum_id=474406)

I'm now building dapper packages, built against the packages located here:
[http://people.ubuntu.com/~seb128/deb/](http://people.ubuntu.com/~seb128/deb/)

This rewrite is not compatible with gaim 1.5.x.  Gaim 2.0.0 has a different plugin structure.  The 1.5 plugin (0.5.x) actually shouldn't load under gaim 2.0.  If you use gaim -d when starting gaim, when it goes to load all the plugins (shared libraries, look for libxfire.so, it'll say that the plugin is not compatible with 2.0 and needs to be updated)

---

### Post by firezip on 2006-08-30
```
bash: make: command not found

```

Any Help on solving this issue? I am using the default GAIM that comes packaged with ubuntu, not the beta.

---

### Post by reptyle on 2006-08-30
> **firezip said:**
> ```
bash: make: command not found

```

Any Help on solving this issue? I am using the default GAIM that comes packaged with ubuntu, not the beta.

0.6.0 for gaim version 1.5 (default in ubuntu) will be released soon.  The release will also include .deb packages for ubuntu.  I suggest you wait until then.

Your system is missing the command "make" which probably means its missing the entire development environment.  You would need to install gcc, auto-tools (autoconf, automake, autoheader), gaim-dev, libssl-dev, and probably a bunch more packages to to get it to compile.

Since you don't know what any of this means, you'd need to learn that first before you can build this package....

hence if you wait for the .deb package you'll find installation easier.

---

### Post by t1z on 2007-03-08
In response to pandora about the debian package.  I had no problems installing it that way however, when I tried to connect for the first time I got an error message saying that the version was too low and to change it in account settings.  I took a shot in the dark, having no idea what this error message was pertaining to, and set the version to 100 and it worked.  Thanks Pandora

---

### Post by uberushaximus on 2007-04-12
If anyone wants an AMD64 branch copy so it works with Feisty's GAIM (2.0.0Beta 6) Here's a trunk copy I just compiled 10 minutes ago. :KS

If anyone wants to compile it their self/doesn't trust me, the basic instructions are below (in one paste and go format)

```
sudo aptitude update && sudo aptitude install gaim gaim-dev subversion checkinstall build-essential libssl-dev && svn co https://svn.sourceforge.net/svnroot/gfire/trunk gfire && cd gfire && sudo ./configure --with-gaim=/usr/lib/pkgconfig/ --prefix=/usr && sudo make && sudo checkinstall

```

Then just grab the package out of the 'gfire' directory and post it here for others :guitar:

---

### Post by Ape3000 on 2007-04-20
I need gfire on feisty generic(not amd64)..

---

### Post by centy on 2007-04-20
Me too. Need xfire for gaim 2.0.0beta6 on ubuntu 7.04.

---

### Post by ceil420 on 2007-04-20
> **centy said:**
> Me too. Need xfire for gaim 2.0.0beta6 on ubuntu 7.04.
Same here. Is anyone workin' on it?

---

### Post by ZeroXR on 2007-04-21
I was starting to wonder why no one on my Xfire list was showing up and then I found this thread.

If anyone has it working, let all of us know! Especially the non-AMD64 folks!

---

### Post by uberushaximus on 2007-04-21
> **ZeroXR said:**
> I was starting to wonder why no one on my Xfire list was showing up and then I found this thread.

If anyone has it working, let all of us know! Especially the non-AMD64 folks!

did you build your copy with the trunk rather than the branch? :)

---

### Post by slythfox on 2007-04-22
I'm running 7.04, trying to get this gaim xfire plugin to work. When compiling, I get this error:
```
configure: error: pkg-config could not locate either libssl.pc or openssl.pc
please make sure you have the development package for openssl/libssl installed
for your distribution. They are usually -dev or -devel packages.
```Any ideas?

Better yet, is there a precompiled 7.04 compilation in the works? Will "gaim-xfire_0.6.0-gaim2.0b3.1-dapper1_i386.deb" work with 7.04?

---

### Post by morneHeru on 2007-04-22
[http://gfire.sourceforge.net/snapshots/]("http://gfire.sourceforge.net/snapshots/")

There are some precompiled snapshots there for Feisty and GAIM 2.0.0b6. I use [gaim-xfire_0.6.1~20070308-gaim-2.0b6-feisty1_i386.deb](http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20070308-gaim-2.0b6-feisty1_i386.deb) and it works fine for me.

---

### Post by ZeroXR on 2007-04-22
**morneHeru**: Thank you, you are a god-send! My functionality on Xfire works like a charm!

---

### Post by water drop on 2007-04-23
Thank you morneHeru, so much.

---

### Post by uberushaximus on 2007-04-23
> **slythfox said:**
> I'm running 7.04, trying to get this gaim xfire plugin to work. When compiling, I get this error:
```
configure: error: pkg-config could not locate either libssl.pc or openssl.pc
please make sure you have the development package for openssl/libssl installed
for your distribution. They are usually -dev or -devel packages.
```Any ideas?

Do you have libssl-dev?

> **slythfox said:**
> Better yet, is there a precompiled 7.04 compilation in the works? Will "gaim-xfire_0.6.0-gaim2.0b3.1-dapper1_i386.deb" work with 7.04?

No, that is for GAIM 2.0 beta 3, the betas are mostly incompatible, however the aforementioned [snapshot]("http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20070122-gaim-2.0b6-feisty1_i386.deb") may be of use.

---

### Post by rippon on 2007-04-25
> **slythfox said:**
> I'm running 7.04, trying to get this gaim xfire plugin to work. When compiling, I get this error:
```
configure: error: pkg-config could not locate either libssl.pc or openssl.pc
please make sure you have the development package for openssl/libssl installed
for your distribution. They are usually -dev or -devel packages.
```Any ideas?

Better yet, is there a precompiled 7.04 compilation in the works? Will "gaim-xfire_0.6.0-gaim2.0b3.1-dapper1_i386.deb" work with 7.04?

sudo apt-get install libssl-dev

Probably just as well to use the snapshot.

---

### Post by tocleora on 2007-04-28
> **morneHeru said:**
> [http://gfire.sourceforge.net/snapshots/]("http://gfire.sourceforge.net/snapshots/")

There are some precompiled snapshots there for Feisty and GAIM 2.0.0b6. I use [gaim-xfire_0.6.1~20070308-gaim-2.0b6-feisty1_i386.deb](http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20070308-gaim-2.0b6-feisty1_i386.deb) and it works fine for me.

This worked perfectly and instantly for me, downloaded, installed, logged in.  Now all my friends can think I'm in windows and hit me up every second to play a game I can't get to work in Cedega or Wine! Hah! :)

---

### Post by Haasje on 2007-04-28
Hi all,

And here i offer you a .deb for the AMD64/Feisty users:

[http://www.oudegenever.nl/gaim-xfire_0.1~20070428-gaim-2.0b6-Feisty1_amd64.deb](http://www.oudegenever.nl/gaim-xfire_0.1~20070428-gaim-2.0b6-Feisty1_amd64.deb)

Important: [-X
This .deb has only been tested/working on 1 AMD64/Feisty. So using is at own risk off-course.

Have fun with it.

Haasje

---

### Post by grev on 2007-04-30
> **Haasje said:**
> Hi all,

And here i offer you a .deb for the AMD64/Feisty users:

[http://www.oudegenever.nl/gaim-xfire_0.1~20070428-gaim-2.0b6-Feisty1_amd64.deb](http://www.oudegenever.nl/gaim-xfire_0.1~20070428-gaim-2.0b6-Feisty1_amd64.deb)

Important: [-X
This .deb has only been tested/working on 1 AMD64/Feisty. So using is at own risk off-course.

Have fun with it.

Haasje


wow man thanks a lot, it works perfect :D

---

### Post by ryodoan on 2007-05-05
> **morneHeru said:**
> [http://gfire.sourceforge.net/snapshots/]("http://gfire.sourceforge.net/snapshots/")

There are some precompiled snapshots there for Feisty and GAIM 2.0.0b6. I use [gaim-xfire_0.6.1~20070308-gaim-2.0b6-feisty1_i386.deb](http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20070308-gaim-2.0b6-feisty1_i386.deb) and it works fine for me.

Thanks man, that made it extremely easy, only used it for a few seconds so far but it seems to be working fine.

---

### Post by morneHeru on 2007-05-10
Here's a deb for Pidgin if anyone wants it - compiled with checkinstall by me in 32 bits on Feisty. :)

Only tested on my install so please be careful and use it at your own risk.

---

### Post by uberushaximus on 2007-05-10
In response to the post above here is the corresponding amd64 deb. ;) (Pidgin)

---

### Post by philidox on 2007-05-14
> **morneHeru said:**
> [http://gfire.sourceforge.net/snapshots/]("http://gfire.sourceforge.net/snapshots/")

There are some precompiled snapshots there for Feisty and GAIM 2.0.0b6. I use [gaim-xfire_0.6.1~20070308-gaim-2.0b6-feisty1_i386.deb](http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20070308-gaim-2.0b6-feisty1_i386.deb) and it works fine for me.

man that was easy thx alot

---

### Post by ranky on 2007-05-19
I actually have xfire on ubuntu, but its a bit wierd.

this is how i did it:

1.Get wine either install through terminal or get it off synaptic package manager
2.download xfire from [http://www.xfire.com](http://www.xfire.com)
3.make a directory where you want it to be installed(ive made a fake program files in the home folder)
4.go to applications-accessories-wine file
5.find your xfire installer exe and open it, then install it to your directory you made earlier.

the problems i found were that your friends list doesnt show till you add a new one, and even then it look stracge and the messenger windows have your default window round them which also looks strange everything else works fine though.

---

### Post by tekpunk on 2007-05-23
I have no idea how to do this.  I went through all of the instructions and some, and nothing is working.  i can't find gfire anywhere, maybe i'm just stupid.  are you supposed to have the same gaim and xfire account or something?

---

### Post by uberushaximus on 2007-05-23
> **tekpunk said:**
> I have no idea how to do this.  I went through all of the instructions and some, and nothing is working.  i can't find gfire anywhere, maybe i'm just stupid.  are you supposed to have the same gaim and xfire account or something?

did you set the correct version string in the account menu?

[http://www.fryx.ch/xfire/faq.html](http://www.fryx.ch/xfire/faq.html)

---

### Post by tekpunk on 2007-05-23
i don't even know how to get to that window.

---

### Post by tekpunk on 2007-05-23
> **philidox said:**
> man that was easy thx alot

so do i just download the file and install??

---

### Post by cibara on 2007-05-25
Yea that was amazingly easy. Thanks a ton!

---

### Post by tekpunk on 2007-05-27
> **uberushaximus said:**
> did you set the correct version string in the account menu?

[http://www.fryx.ch/xfire/faq.html](http://www.fryx.ch/xfire/faq.html)


For some reason when i create a new account, xfire does not show up.  I've installed the .debs and everything and it's still not working.  Any suggestions?

---

### Post by uberushaximus on 2007-05-28
> **tekpunk said:**
> For some reason when i create a new account, xfire does not show up.  I've installed the .debs and everything and it's still not working.  Any suggestions?

Are you using pidgin or gaim, and what version?

---

### Post by reptyle on 2007-05-28
> **tekpunk said:**
> For some reason when i create a new account, xfire does not show up.  I've installed the .debs and everything and it's still not working.  Any suggestions?

When opening the account screen and hitting the "add" button, if xfire is not listed in the protocols drop down box, then the module is not loading.

This is usually due to installing the wrong version of the plugin.  IE you installed a gaim 2.0 plugin .deb when your gaim version is 1.5, or conversely, installed the 1.5 plugin but your running gaim 2.0.  You neglected to mention your gaim version, which version of the plugin you installed (full file name), and what version of ubuntu your running.

when in doubt, run gaim with the --debug option from a terminal.  There will be lots of output, but if the plugin isn't loading it will tell you.

---

### Post by fatray on 2007-06-03
What am I doing wrong?
Downloaded this **_gaim-xfire_0.6.1~20070308-gaim-2.0b6-feisty1_i386.deb_**
Opened it and it installed AFAIK no errors
Gaim Version 2.0.0 BETA 6

Xfire not listed in Plug-ins
Xfire not listed in Accounts

No errors running --debug that I could see, also I do not see any mention of Xfire.

Is it called something other then Xfire inside Gaim?
:-?

---

### Post by tocleora on 2007-06-03
> **fatray said:**
> What am I doing wrong?

If you'll read the very first message in this thread, it will give you the additional steps you need to do to get it working with gaim.

---

### Post by reptyle on 2007-06-04
> **fatray said:**
> What am I doing wrong?
Downloaded this **_gaim-xfire_0.6.1~20070308-gaim-2.0b6-feisty1_i386.deb_**
Opened it and it installed AFAIK no errors
Gaim Version 2.0.0 BETA 6

Xfire not listed in Plug-ins
Xfire not listed in Accounts

No errors running --debug that I could see, also I do not see any mention of Xfire.

Is it called something other then Xfire inside Gaim?
:-?

What version of Ubuntu are you running?  And what architecture?

---

### Post by tocleora on 2007-06-04
> **fatray said:**
> What am I doing wrong?

In case I came off sounding like an A**... The reason I said that was because I tried the method you tried and had similar results.  But following the instructions in the first message of this thread did work for me.

---

### Post by fatray on 2007-06-04
I understand that you know exactly what you are doing, I have no idea whatsoever and your trying to help, but you don't understand why I don't get it.   I followed those directions the best I can, this is the message I get.

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
configure: error: pkg-config could not locate either libssl.pc or openssl.pc
please make sure you have the development package for openssl/libssl installed
for your distribution. They are usually -dev or -devel packages.
```

I understand I'm missing something.  What is openssl/libssl?  What is -dev or devel packages?  Where can I get them?  Been using Ubuntu for a solid 3 days now, I've learned allot but still so little.

---

### Post by NTolerance on 2007-06-05
> **fatray said:**
> I understand that you know exactly what you are doing, I have no idea whatsoever and your trying to help, but you don't understand why I don't get it.   I followed those directions the best I can, this is the message I get.

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
configure: error: pkg-config could not locate either libssl.pc or openssl.pc
please make sure you have the development package for openssl/libssl installed
for your distribution. They are usually -dev or -devel packages.
```

I understand I'm missing something.  What is openssl/libssl?  What is -dev or devel packages?  Where can I get them?  Been using Ubuntu for a solid 3 days now, I've learned allot but still so little.

You can do this to get rid of that error:

```
sudo apt-get install libssl-dev
```

Then you'll get this error:

```
Configuration complete

Debugging enabled..............: no
Using gaim version.............: 2.0
Gaim package prefix............: /usr
Gaim package libdir............: /usr/lib
Install prefix.................: /usr
Install libdir.................: /usr/lib
Gaim lib dir detected..........: Yes


Type make to compile

Make sure you copy data/gfire_games.xml to /home/nt/.gaim/

/bin/sed 's/#define PACKAGE/#define GFIRE_PACKAGE/g' pre_config.h > gfire_config.h
make  all-recursive
make[1]: Entering directory `/home/nt/tmp/gaim-xfire-0.6.0'
Making all in src
make[2]: Entering directory `/home/nt/tmp/gaim-xfire-0.6.0/src'
/bin/bash ../libtool --silent --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..  -DLIBDIR=\"/usr/lib/gaim/\"      -DDATADIR=\"/usr/share\"        -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/include/gaim -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include                    -Wall -g3 -c gfire.c
gfire.c: In function 'gfire_login':
gfire.c:353: warning: passing argument 2 of 'gaim_proxy_connect' from incompatible pointer type
gfire.c:353: warning: passing argument 3 of 'gaim_proxy_connect' makes pointer from integer without a cast
gfire.c:353: warning: passing argument 4 of 'gaim_proxy_connect' makes integer from pointer without a cast
gfire.c:353: warning: passing argument 5 of 'gaim_proxy_connect' from incompatible pointer type
gfire.c:353: error: too few arguments to function 'gaim_proxy_connect'
gfire.c: At top level:
gfire.c:1498: warning: initialization from incompatible pointer type
make[2]: *** [gfire.lo] Error 1
make[2]: Leaving directory `/home/nt/tmp/gaim-xfire-0.6.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nt/tmp/gaim-xfire-0.6.0'
make: *** [all-recursive-am] Error 2
```

:(

---

### Post by uberushaximus on 2007-06-06
Have you tried using on of the tarball snapshots mentioned before or one of the precompiled binaries?

---

### Post by fatray on 2007-06-07
> **uberushaximus said:**
> Have you tried using on of the tarball snapshots mentioned before or one of the precompiled binaries?


Speak English please... :?:  

Edit

Let me look at the Wiki's before I get all upset that I have no idea what you just said. I will understand won of these days.

---

### Post by tocleora on 2007-06-08
> **fatray said:**
> Speak English please... :?:

Ok, I'm going to try to make this as simple as possible, hopefully this will help get you where you need to be.  Ntolerance looks like he hit a wall with his so just go as far as you can, report any errors you find... we're all users like you so we'll try to help the best we can and if we can't  then I'd suggest just continue to check back here as new versions come out and I'm sure there will be a version or process pop up sooner than later that will help.

First... Click on "Applications", "Accessories" and then "Terminal".

You should get a screen that has a $ and then a prompt.  From right here do this:

```
wget http://downloads.sourceforge.net/gfire/gaim-xfire-0.6.0.tar.gz
```

and hit the enter key.  It should do some things and return you back to the $.  Next, do this:

```
sudo apt-get install gaim-dev
```

and hit the enter key. it will ask you for your super user password, enter it and hit the enter key.  again it should do some things and return you back to the $. Next do this:

```
tar -xpf /home/youruser/Desktop/gaim-xfire-0.6.0.tar.gz
```

and hit the enter key.  should return you back to the $.  Do this (where "youruser" is your user name):

```
cd /home/youruser/Desktop/gaim-xfire-0.6.0
```

enter. back to $.  Do this:

```
sudo ./configure --with-gaim=/usr/lib/pkgconfig/ --prefix=/usr && make && make install
```

enter. back to $.  Start up gaim and see if you see it.  Again, If you receive any errors during this process report them here and we'll try to help as much as we can.  Don't get discouraged if we can't though, just continue to check back periodically, do a search on the forums for "xfire" and "gaim" (or pidgin) and more than likely an option will pop up that will work for you shortly.

Oh, and if you do report an error, give us as much information as possible... how far you got in the process, what the command was you ran that received the error, etc.

---

### Post by reptyle on 2007-06-08
> **tocleora said:**
> 

```
sudo apt-get install gaim-dev
```



First.. this is not totally correct.  The error presented in a previous post was complaining about missing the ssl development headers.

To make sure the dependancies are satisfiled you also need to make sure **libssl-dev** is installed.  I would also suggest the build-essential meta package just to make sure that the target build system has the minimum requirements.

Also you are a linking to the straight 0.6.0 release which does not support gaim 2.0.0 beta 6 (or any gaim revision after beta 3).  Without identifying the target gaim release version **including the beta level** you may be sending this poor soul down a path that will never lead them to water.

---

### Post by Andrew Booth on 2007-06-09
> **tocleora said:**
> Ok, I'm going to try to make this as simple as possible, hopefully this will help get you where you need to be.  Ntolerance looks like he hit a wall with his so just go as far as you can, report any errors you find... we're all users like you so we'll try to help the best we can and if we can't  then I'd suggest just continue to check back here as new versions come out and I'm sure there will be a version or process pop up sooner than later that will help.

First... Click on "Applications", "Accessories" and then "Terminal".

You should get a screen that has a $ and then a prompt.  From right here do this:

```
wget http://downloads.sourceforge.net/gfire/gaim-xfire-0.6.0.tar.gz
```

and hit the enter key.  It should do some things and return you back to the $.  Next, do this:

```
sudo apt-get install gaim-dev
```

and hit the enter key. it will ask you for your super user password, enter it and hit the enter key.  again it should do some things and return you back to the $. Next do this:

```
tar -xpf /home/youruser/Desktop/gaim-xfire-0.6.0.tar.gz
```

and hit the enter key.  should return you back to the $.  Do this (where "youruser" is your user name):

```
cd /home/youruser/Desktop/gaim-xfire-0.6.0
```

enter. back to $.  Do this:

```
sudo ./configure --with-gaim=/usr/lib/pkgconfig/ --prefix=/usr && make && make install
```

enter. back to $.  Start up gaim and see if you see it.  Again, If you receive any errors during this process report them here and we'll try to help as much as we can.  Don't get discouraged if we can't though, just continue to check back periodically, do a search on the forums for "xfire" and "gaim" (or pidgin) and more than likely an option will pop up that will work for you shortly.

Oh, and if you do report an error, give us as much information as possible... how far you got in the process, what the command was you ran that received the error, etc.

Followed all the steps and still can't get it to work. The terminal finished off with these messages:

```
gfire.c: In function 'gfire_login':
gfire.c:353: warning: passing argument 2 of 'gaim_proxy_connect' from incompatible pointer type
gfire.c:353: warning: passing argument 3 of 'gaim_proxy_connect' makes pointer from integer without a cast
gfire.c:353: warning: passing argument 4 of 'gaim_proxy_connect' makes integer from pointer without a cast
gfire.c:353: warning: passing argument 5 of 'gaim_proxy_connect' from incompatible pointer type
gfire.c:353: error: too few arguments to function 'gaim_proxy_connect'
gfire.c: At top level:
gfire.c:1498: warning: initialization from incompatible pointer type
make[2]: *** [gfire.lo] Error 1
make[2]: Leaving directory `/home/andrew/Desktop/gaim-xfire-0.6.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/andrew/Desktop/gaim-xfire-0.6.0'
make: *** [all-recursive-am] Error 2
```

I just cant make sense of whats going wrong. I've tried all sorts of methods shown in this thread and so far I get a different error message every time. I've only been on Ubuntu since Thursday and have learned a considerable amount in that period from Googleing nearly every possible issue I have encountered so far. This is beyond me and I'd rather hand it over to you pros.

EDIT:
Googled around and found that this doesn't support beta6. Guess I'll have to wait

---

### Post by tocleora on 2007-06-11
> **reptyle said:**
> you may be sending this poor soul down a path that will never lead them to water.

Yeah I was kinda following my own instructions as I went along but as I already have xfire I didn't want to go too far into it.  Guess I learned the hard way not to do that in the future. :)  Can someone offer him plain english instructions they *know* work?  like step by step like I did so all he has to do is copy and paste.

---

### Post by Jammerdelray on 2007-06-28
"Here's a deb for Pidgin if anyone wants it - compiled with checkinstall by me in 32 bits on Feisty. "

I tried it with Pidgin and Xfire does not show in the list. If anybody gets it working, let us know.

Thanks

---

### Post by freshanointing on 2007-06-29
I have feisty.  I followed a suggestion on getting the snapshot of gaim-xfire and I was succesful on installing the plugin.  Just download the tarball, install the devel packages of gaim, libssl, gtk2 (i hope thats all)  and ur good to go.  Hope this helps!

---

### Post by Jammerdelray on 2007-06-29
I tried using the snapshot but it's confusing. I used the terminal commands in the readme but it's not working. If anyone gets the chance it make a install file for gfire for pidgin 2.0 it'll be much easier on feisty fawn. Thanks :D

---

### Post by uberushaximus on 2007-07-11
Sorry to anyone if you were trying to get my old debs to work, this one works for sure now, as it wasn't generated by checkinstall, I used the offical debian build method, however it is unsigned, so if you get a warning about that I'm sorry :P

---

### Post by 3rdoffive on 2007-07-26
so i followed the instructions on installing gaim-xfire, but how/where do i run it from?  i go into the directory and there is nothing that resembles an .exe.  i followed the instructions posted on page six TO THE LETTER(litterally, i copied and pasted some stuff) and nothing was put on my desktop/applications menu to launch it.

i dont have to *create* an .exe do i?

---

### Post by uberushaximus on 2007-07-27
> **3rdoffive said:**
> so i followed the instructions on installing gaim-xfire, but how/where do i run it from?  i go into the directory and there is nothing that resembles an .exe.  i followed the instructions posted on page six TO THE LETTER(litterally, i copied and pasted some stuff) and nothing was put on my desktop/applications menu to launch it.

i dont have to *create* an .exe do i?

Unless you were making the windows build, which of course you weren't because that wasn't being discussed, then no, however, back on topic, you'd be looking for a .deb file most likely if you haven't installed it yet.

---

### Post by zuzuzzzip on 2007-08-05
> **Haasje said:**
> Hi all,

And here i offer you a .deb for the AMD64/Feisty users:

[http://www.oudegenever.nl/gaim-xfire_0.1~20070428-gaim-2.0b6-Feisty1_amd64.deb]("http://www.oudegenever.nl/gaim-xfire_0.1%7E20070428-gaim-2.0b6-Feisty1_amd64.deb")

Important: [-X
This .deb has only been tested/working on 1 AMD64/Feisty. So using is at own risk off-course.

Have fun with it.

Haasje
thx man, works great :)

---

### Post by computerjoe on 2007-08-06
> **uberushaximus said:**
> Sorry to anyone if you were trying to get my old debs to work, this one works for sure now, as it wasn't generated by checkinstall, I used the offical debian build method, however it is unsigned, so if you get a warning about that I'm sorry :P

I get an error message:

```
Error: Dependency is not satisfiable: pidgin
```

I have pidgin installed. What does this error mean?

---

### Post by Burbruee on 2007-08-13
Does gfire register playtime for games run through wine?
I got it up and running, but this is all I want to use xfire for, not interested in chat. ^_^

Real xfire installer doesn't work through wine. Complains about needing administrative rights and microsoft windows common controls not being properly installed. 
( Downloaded common controls from MS website, but it made no difference. )

---

### Post by uberushaximus on 2007-08-13
> **Burbruee said:**
> Does gfire register playtime for games run through wine?
No and there's no plan to implement it.
> 'Real' xfire installer doesn't work through wine. 
I've never heard that before, it always works for me.
[http://appdb.winehq.org/appview.php?iAppId=2573](http://appdb.winehq.org/appview.php?iAppId=2573)

---

### Post by Burbruee on 2007-08-13
> **uberushaximus said:**
> No and there's no plan to implement it.

I've never heard that before, it always works for me.
[http://appdb.winehq.org/appview.php?iAppId=2573](http://appdb.winehq.org/appview.php?iAppId=2573)
I know, it confuses me that xfire has a Gold rating but I can't get it to install.

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
```

That's what I get when running wine xfire_installer_27409.exe which I downloaded from their website last night.

---

### Post by DarkPrismXD on 2007-09-03
after doing the last command I get a

configure: error: pkg-config could not locate either libssl.pc or openssl.pc
please make sure you have the development package for openssl/libssl installed
for your distribution. They are usually -dev or -devel packages.

how do I fix this?

---

### Post by Cappy on 2007-09-03
GAIM Install:
[http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20070308-gaim-2.0b6-feisty1_i386.deb](http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20070308-gaim-2.0b6-feisty1_i386.deb)

(taken from [http://ubuntuforums.org/showthread.php?t=504661](http://ubuntuforums.org/showthread.php?t=504661))

---

Customization on launching games and setting your "in-game" status:
[http://ubuntuforums.org/showthread.php?t=397255](http://ubuntuforums.org/showthread.php?t=397255)


If you are running 64-bit or Gutsy see here:
[http://ubuntuforums.org/showthread.php?t=540903](http://ubuntuforums.org/showthread.php?t=540903)

---

### Post by andraxion on 2007-09-29
I am using Pidgin and when I install this, it puts it in my Gaim directory.

---

### Post by paul527 on 2007-09-30
thanks for that Snapshot morneHeru! Works perfectly! :)

---

### Post by Haste on 2007-10-21
Im running 7.10 so im using pidgin over gaim...

i followed what you said on page 6 (minus the gaim bs that i dont need) but after i typed

> sudo ./configure --with-gaim=/usr/lib/pkgconfig/ --prefix=/usr && make && make instal
i also tried "pidgin" in place for "gaim"

i get this message either way

> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

im fairly new to linux so when i checked this log out it was like reading russian, im guessing im missing a C compiler or the compiler that i have cannot compile it right to work?

---

### Post by Cappy on 2007-10-21
If you are using 32-bit just use this:
[http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20070713-pidgin-2.0-gutsy1_i386.deb](http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20070713-pidgin-2.0-gutsy1_i386.deb)

---

### Post by Haste on 2007-10-22
> **Cappy said:**
> If you are using 32-bit just use this:
[http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20070713-pidgin-2.0-gutsy1_i386.deb](http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20070713-pidgin-2.0-gutsy1_i386.deb)

there we go, thanks #-o

---

### Post by ericesque on 2007-11-08
anybody else getting a

'Password or Username Incorrect' error?

It just started tonight out of the blue.  Was working fine and my password is saved.

Nevermind... it started working agian

---

### Post by tombutcher1990 on 2007-12-17
hey thanks a lot for all the info every1

i was having some troubles, i then realised it was cos i was installing an old version of the compiled program, i found the updated 1 and dun, it worked first time! thanks for the helpful guide guys.

---

### Post by go_beep_yourself on 2007-12-24
How can this work for Pidgin, not Gaim in 64 bit Gutsy?

---

### Post by Cappy on 2007-12-25
> **go_beep_yourself said:**
> How can this work for Pidgin, not Gaim in 64 bit Gutsy?

Look at the top of the last page. If that doesn't work you'll need to compile [http://gfire.sourceforge.net/snapshots/gaim-xfire-0.6.1~20071109.tar.bz2](http://gfire.sourceforge.net/snapshots/gaim-xfire-0.6.1~20071109.tar.bz2)
yourself. I compiled it on 64-bit gutsy for pidgin using the directions supplied.

---

### Post by go_beep_yourself on 2007-12-26
I have gaim-xfire working with Pidgin in 64 bit Ubuntu Gutsy Gibbon now, but why has it put these files and directories in my root directory? It seems like the wrong place for them.

/22
/22/xfire.png
/16
/16/xfire.png

---

### Post by go_beep_yourself on 2008-01-08
> **Cappy said:**
> Look at the top of the last page. If that doesn't work you'll need to compile [http://gfire.sourceforge.net/snapshots/gaim-xfire-0.6.1~20071109.tar.bz2](http://gfire.sourceforge.net/snapshots/gaim-xfire-0.6.1~20071109.tar.bz2)
yourself. I compiled it on 64-bit gutsy for pidgin using the directions supplied.

Strange, it worked in Ubuntu but not Fedora. I've searched the Fedora forums, and only 2 people have ever said anything about xfire. They were using the windows xfire in Wine. Can you help?

```
[root@localhost gaim-xfire-0.6.1~20071109]# ./configure 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/root/gaim-xfire-0.6.1~20071109/missing: Unknown `--run' option
Try `/root/gaim-xfire-0.6.1~20071109/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
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
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB2... yes
checking for LIBPURPLE... no
checking for GAIM... configure: error: Package requirements (gaim) were not met:

No package 'gaim' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GAIM_CFLAGS
and GAIM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

[root@localhost gaim-xfire-0.6.1~20071109]# 
```

---

### Post by go_beep_yourself on 2008-01-08
When trying to compile gaim-xfire-0.6.1~20071109 in Ubuntu 7.10 64 bit, I get this message. It is looking for gaim and not finding Pidgin. How can I get this to work?

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/user/gaim-xfire-0.6.1~20071109/missing: Unknown `--run' option
Try `/home/user/gaim-xfire-0.6.1~20071109/missing --help' for more information
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
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
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB2... yes
checking for LIBPURPLE... no
checking for GAIM... configure: error: Package requirements (gaim) were not met:

No package 'gaim' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GAIM_CFLAGS
and GAIM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
Sent at 10:27 PM on Tuesday
```

---

### Post by Cappy on 2008-01-09
I think you may need to install the pidgin-dev package. You will also need libssl-dev or openssl-dev.

Also the README says to use ```
./configure --prefix=/usr
```
By default it uses /usr/local
If you install the pidgin-dev package and /usr/include/pidgin exists with a bunch of *.h files then you use /usr like above. Otherwise, you need to use what I posted below from the file INSTALL (from an older gfire install).

```

1) locate your gaim binary which will probably be /usr/bin/gaim

2) locate the gaim header files installed with the dev package.  They are
usually installed in /usr/include/gaim.  If you have this directory and
there are many files that end in .h, then this is the directory you want.

3) using step 1 and 2 above determine the prefix to use as an option to
configure. If steps 1 and 2 are exactly what you see above, then your prefix
is --prefix=/usr, if perchance #1 and #2 were /usr/local/bin/gaim, and
/usr/local/include/gaim, then your prefix is --prefix=/usr/local

4) Run the configure script.  use the prefix option to determine where to
install the software.  ./configure --prefix=/usr

```

---

### Post by go_beep_yourself on 2008-01-09
> **Cappy said:**
> I think you may need to install the pidgin-dev package. You will also need libssl-dev or openssl-dev.

Also the README says to use ```
./configure --prefix=/usr
```
By default it uses /usr/local
If you install the pidgin-dev package and /usr/include/pidgin exists with a bunch of *.h files then you use /usr like above. Otherwise, you need to use what I posted below from the file INSTALL (from an older gfire install).

```

1) locate your gaim binary which will probably be /usr/bin/gaim

2) locate the gaim header files installed with the dev package.  They are
usually installed in /usr/include/gaim.  If you have this directory and
there are many files that end in .h, then this is the directory you want.

3) using step 1 and 2 above determine the prefix to use as an option to
configure. If steps 1 and 2 are exactly what you see above, then your prefix
is --prefix=/usr, if perchance #1 and #2 were /usr/local/bin/gaim, and
/usr/local/include/gaim, then your prefix is --prefix=/usr/local

4) Run the configure script.  use the prefix option to determine where to
install the software.  ./configure --prefix=/usr

```

Thanks for that. The reason xfire had worked with Pidgin before is because I had a compiled pidgin in /usr/local. Now I understand why I had problems.

---

### Post by canadalinux on 2008-01-24
Hey guys, I'm receiving the following error after installing the plugin for pidgin.

An error was encountered reading your buddy list.  They have not been loaded, and the old file has been renamed to /home/xxxxx/.purple/blist.xml~.

I'm using Pidgin 2.2.1 on Gutsy and installed the gaim-xfire_0.6.1~20071109-pidgin-2.2-gutsy1_i386.deb package.  Everything installed fine, and my buddies were retrieved, but whenever I startup pidgin I get that error.

Any ideas/suggestions?

thanks.

---

### Post by Mr. Bunny on 2008-04-19
This post is to document what I did, in part, to get it working. I installed *pidgin-dev* as suggested above and that made it stop complaining about being unable to find Gaim. Then I couldn't compile:

 ```
/bin/bash: convert: command not found
make[2]: *** [xfire16.png] Error 127
make[2]: Leaving directory `/home/steve/Source/gaim-xfire-0.6.1~20071109/pixmaps'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/steve/Source/gaim-xfire-0.6.1~20071109'
make: *** [all] Error 2
```

I found I needed to install [ImageMagick]("http://www.imagemagick.org/script/index.php"), so I simply installed it with

```
sudo apt-get install imagemagick
```

then *make* worked. I then did sudo make install, restarted Pidgin, and it worked perfectly! ^^

---

### Post by lurch89 on 2008-04-30
I installed pidgin-dev, but I still have the "No package 'gaim' found error. Is there something I'm missing? 

I am running Ubuntu 8.04 amd64 with the latest version of pidgin and gaim-xfire-0.6.0 source. I know I can probably just wait for tomorrow's version that will be all set for Hardy, but I'm impatient!

---

### Post by uberushaximus on 2008-04-30
> **lurch89 said:**
> I installed pidgin-dev, but I still have the "No package 'gaim' found error. Is there something I'm missing? 

I am running Ubuntu 8.04 amd64 with the latest version of pidgin and gaim-xfire-0.6.0 source. I know I can probably just wait for tomorrow's version that will be all set for Hardy, but I'm impatient!

Technically, the "gaim" package doesn't need to be installed, if you really want... type sudo apt-get install gaim

If you don't simply force the config by following the instructions

---

### Post by Anorexic Whale on 2008-06-10
I have gaim 0.7.0 and I replaced the "youruser" with my user name, and then I replaced the older version (that it says in the directions) with my version, and it says this

Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

Can anyone help me?

---

### Post by uberushaximus on 2008-06-10
Protip, built packages are here, don't bother building anymore (unless you're on PPC or something weird)

[https://sourceforge.net/project/showfiles.php?group_id=141362](https://sourceforge.net/project/showfiles.php?group_id=141362)

---

### Post by blaze2136 on 2008-11-11
WOOT THANX MAN 
it worked. yeaa yr the best ah
i was haveing problems with xfire running on wine for a bit
and this runs just grate ^^ nice work/poast thanx for the help

---

### Post by cory94bailly on 2008-12-03
> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... no
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for sed... /bin/sed
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.


Any help please?

---

### Post by uberushaximus on 2008-12-03
> **cory94bailly said:**
> Any help please?

If you want to build any package, you're going to want build-essential, which can be installed by typing```
sudo aptitude install build-essential
```

(I also recall imagemagick being a dependency in the past)

You're probably best off visiting [http://gfire.sf.net](http://gfire.sf.net) for some prebuilt binaries.

---

### Post by cory94bailly on 2008-12-04
> **uberushaximus said:**
> If you want to build any package, you're going to want build-essential, which can be installed by typing```
sudo aptitude install build-essential
```

(I also recall imagemagick being a dependency in the past)

You're probably best off visiting [http://gfire.sf.net](http://gfire.sf.net) for some prebuilt binaries.

Well that fixed alot ;) (Thanks btw)

But now I am getting this:

```
/home/user> cd /home/user/Desktop/gaim-xfire-0.5.8
/home/user/Desktop/gaim-xfire-0.5.8> sudo ./configure --with-gaim=/usr/lib/pkgconfig/ --prefix=/usr && make && make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for pkg-config... /usr/bin/pkg-config
checking for gaim... yes
checking GAIM_CFLAGS... -I/usr/include/gaim -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
checking GAIM_LIBS... -lgaim -lglib-2.0
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... yes (version 2.12.4)
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
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
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
configure: creating ./config.status
config.status: creating Makefile
config.status: creating gaim-xfire.spec
config.status: creating pixmaps/Makefile
config.status: creating src/Makefile
config.status: creating pre_config.h
config.status: executing default-1 commands

Configuration complete

Debugging enabled..............: no

Type make to compile

make  all-recursive
make[1]: Entering directory `/home/user/Desktop/gaim-xfire-0.5.8'
Making all in src
make[2]: Entering directory `/home/user/Desktop/gaim-xfire-0.5.8/src'
/bin/sh ../libtool --silent --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..  -DLIBDIR=\"/usr/lib/gaim/\"        -DDATADIR=\"/usr/share\"        -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/include/gaim -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include            -Wall -g3 -c xfire.c
xfire.c:20:22: error: internal.h: No such file or directory
In file included from xfire.c:37:
x_packets.h:32:49: warning: no newline at end of file
xfire.c: In function 'xfire_write_packet':
xfire.c:77: warning: implicit declaration of function 'write'
xfire.c: In function 'xfire_close':
xfire.c:91: warning: implicit declaration of function 'close'
xfire.c: In function 'xfire_update_buddy':
xfire.c:113: warning: implicit declaration of function 'serv_got_update'
xfire.c:115: error: 'UC_UNAVAILABLE' undeclared (first use in this function)
xfire.c:115: error: (Each undeclared identifier is reported only once
xfire.c:115: error: for each function it appears in.)
xfire.c: At top level:
xfire.c:122: error: expected declaration specifiers or '...' before 'GaimConvImFlags'
xfire.c: In function 'xfire_send_im':
xfire.c:141: warning: implicit declaration of function 'strlen'
xfire.c:141: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c:148: warning: implicit declaration of function 'strncpy'
xfire.c:148: warning: incompatible implicit declaration of built-in function 'strncpy'
xfire.c: In function 'xfire_login_salt':
xfire.c:192: warning: incompatible implicit declaration of built-in function 'strncpy'
xfire.c: In function 'xfire_check_buddy_im':
xfire.c:232: warning: implicit declaration of function 'memcmp'
xfire.c: In function 'xfire_check_buddy_status':
xfire.c:298: warning: implicit declaration of function 'strncmp'
xfire.c:298: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c: In function 'xfire_get_im':
xfire.c:316: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c:330: warning: implicit declaration of function 'memcpy'
xfire.c:330: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c:359: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c: In function 'xfire_read_buddy_online':
xfire.c:408: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:409: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c: In function 'xfire_read_buddys':
xfire.c:446: warning: passing argument 1 of 'xfire_read_dynamic_var_attr' from incompatible pointer type
xfire.c:451: warning: passing argument 1 of 'xfire_read_dynamic_var_attr' from incompatible pointer type
xfire.c:453: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:456: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c: In function 'xfire_read_invitation':
xfire.c:496: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c:502: warning: implicit declaration of function '_'
xfire.c:504: warning: passing argument 1 of 'g_strdup_printf' makes pointer from integer without a cast
xfire.c: In function 'xfire_new_buddy':
xfire.c:536: warning: incompatible implicit declaration of built-in function 'strncpy'
xfire.c:536: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c: In function 'xfire_rem_buddy':
xfire.c:549: warning: incompatible implicit declaration of built-in function 'strncpy'
xfire.c:549: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c: In function 'xfire_read_status':
xfire.c:565: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c:570: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c: In function 'xfire_game_status':
xfire.c:606: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:606: warning: pointer targets in passing argument 5 of 'xfire_read_dynamic_attr' differ in signedness
xfire.c:607: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:607: warning: pointer targets in passing argument 5 of 'xfire_read_dynamic_attr' differ in signedness
xfire.c:608: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:608: warning: pointer targets in passing argument 5 of 'xfire_read_dynamic_attr' differ in signedness
xfire.c:609: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:609: warning: pointer targets in passing argument 5 of 'xfire_read_dynamic_attr' differ in signedness
xfire.c: In function 'xfire_login_check':
xfire.c:635: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c:639: warning: implicit declaration of function 'strcmp'
xfire.c: In function 'xfire_packet_handler':
xfire.c:671: warning: implicit declaration of function 'read'
xfire.c:674: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c:690: warning: passing argument 2 of 'gaim_connection_error' makes pointer from integer without a cast
xfire.c:712: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c: In function 'xfire_login_connect':
xfire.c:833: warning: passing argument 2 of 'gaim_connection_error' makes pointer from integer without a cast
xfire.c: In function 'xfire_login':
xfire.c:855: warning: passing argument 2 of 'gaim_connection_update_progress' makes pointer from integer without a cast
xfire.c:861: warning: passing argument 2 of 'gaim_proxy_connect' from incompatible pointer type
xfire.c:861: warning: passing argument 3 of 'gaim_proxy_connect' makes pointer from integer without a cast
xfire.c:861: warning: passing argument 4 of 'gaim_proxy_connect' makes integer from pointer without a cast
xfire.c:861: warning: passing argument 5 of 'gaim_proxy_connect' from incompatible pointer type
xfire.c:861: error: too few arguments to function 'gaim_proxy_connect'
xfire.c:862: warning: passing argument 2 of 'gaim_connection_error' makes pointer from integer without a cast
xfire.c: In function 'xfire_list_emblems':
xfire.c:878: error: 'GaimBuddy' has no member named 'present'
xfire.c:878: error: 'GAIM_BUDDY_OFFLINE' undeclared (first use in this function)
xfire.c: In function 'xfire_set_away':
xfire.c:917: warning: passing argument 2 of 'xfire_create_away' discards qualifiers from pointer target type
xfire.c:922: warning: passing argument 2 of 'xfire_create_away' makes pointer from integer without a cast
xfire.c: In function 'xfire_away_states':
xfire.c:943: warning: passing argument 2 of 'g_list_append' makes pointer from integer without a cast
xfire.c:944: warning: passing argument 2 of 'g_list_append' makes pointer from integer without a cast
xfire.c: In function 'xfire_prpl_tooltip_text':
xfire.c:970: warning: format '%s' expects type 'char *', but argument 3 has type 'int'
xfire.c: At top level:
xfire.c:999: warning: initialization from incompatible pointer type
xfire.c:1001: warning: initialization from incompatible pointer type
xfire.c:1002: warning: initialization from incompatible pointer type
xfire.c:1008: warning: initialization from incompatible pointer type
xfire.c:1012: warning: initialization from incompatible pointer type
xfire.c:1067: error: 'VERSION' undeclared here (not in a function)
xfire.c:1069: warning: implicit declaration of function 'N_'
xfire.c:1069: error: initializer element is not constant
xfire.c:1069: error: (near initialization for 'info.summary')
xfire.c:1071: error: initializer element is not constant
xfire.c:1071: error: (near initialization for 'info.description')
xfire.c:1073: error: 'GAIM_WEBSITE' undeclared here (not in a function)
xfire.c: In function 'init_plugin':
xfire.c:1089: warning: passing argument 1 of 'gaim_account_option_string_new' makes pointer from integer without a cast
xfire.c:1092: warning: passing argument 1 of 'gaim_account_option_int_new' makes pointer from integer without a cast
xfire.c:1095: warning: passing argument 1 of 'gaim_account_option_int_new' makes pointer from integer without a cast
make[2]: *** [xfire.lo] Error 1
make[2]: Leaving directory `/home/user/Desktop/gaim-xfire-0.5.8/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/Desktop/gaim-xfire-0.5.8'
make: *** [all-recursive-am] Error 2

```


Sorry how long it is, you can pretty much skip some parts until the "errors" and "warnings" start...


Any fix for this or if someone could tell me how to run the pre-compiled version would be appreciated.

---

### Post by uberushaximus on 2008-12-04
> **cory94bailly said:**
> Well that fixed alot ;) (Thanks btw)

But now I am getting this:

```
/home/user> cd /home/user/Desktop/gaim-xfire-0.5.8
/home/user/Desktop/gaim-xfire-0.5.8> sudo ./configure --with-gaim=/usr/lib/pkgconfig/ --prefix=/usr && make && make install
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for pkg-config... /usr/bin/pkg-config
checking for gaim... yes
checking GAIM_CFLAGS... -I/usr/include/gaim -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
checking GAIM_LIBS... -lgaim -lglib-2.0
checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... yes (version 2.12.4)
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
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
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
configure: creating ./config.status
config.status: creating Makefile
config.status: creating gaim-xfire.spec
config.status: creating pixmaps/Makefile
config.status: creating src/Makefile
config.status: creating pre_config.h
config.status: executing default-1 commands

Configuration complete

Debugging enabled..............: no

Type make to compile

make  all-recursive
make[1]: Entering directory `/home/user/Desktop/gaim-xfire-0.5.8'
Making all in src
make[2]: Entering directory `/home/user/Desktop/gaim-xfire-0.5.8/src'
/bin/sh ../libtool --silent --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..  -DLIBDIR=\"/usr/lib/gaim/\"        -DDATADIR=\"/usr/share\"        -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -I/usr/include/gaim -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include            -Wall -g3 -c xfire.c
xfire.c:20:22: error: internal.h: No such file or directory
In file included from xfire.c:37:
x_packets.h:32:49: warning: no newline at end of file
xfire.c: In function 'xfire_write_packet':
xfire.c:77: warning: implicit declaration of function 'write'
xfire.c: In function 'xfire_close':
xfire.c:91: warning: implicit declaration of function 'close'
xfire.c: In function 'xfire_update_buddy':
xfire.c:113: warning: implicit declaration of function 'serv_got_update'
xfire.c:115: error: 'UC_UNAVAILABLE' undeclared (first use in this function)
xfire.c:115: error: (Each undeclared identifier is reported only once
xfire.c:115: error: for each function it appears in.)
xfire.c: At top level:
xfire.c:122: error: expected declaration specifiers or '...' before 'GaimConvImFlags'
xfire.c: In function 'xfire_send_im':
xfire.c:141: warning: implicit declaration of function 'strlen'
xfire.c:141: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c:148: warning: implicit declaration of function 'strncpy'
xfire.c:148: warning: incompatible implicit declaration of built-in function 'strncpy'
xfire.c: In function 'xfire_login_salt':
xfire.c:192: warning: incompatible implicit declaration of built-in function 'strncpy'
xfire.c: In function 'xfire_check_buddy_im':
xfire.c:232: warning: implicit declaration of function 'memcmp'
xfire.c: In function 'xfire_check_buddy_status':
xfire.c:298: warning: implicit declaration of function 'strncmp'
xfire.c:298: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c: In function 'xfire_get_im':
xfire.c:316: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c:330: warning: implicit declaration of function 'memcpy'
xfire.c:330: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c:359: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c: In function 'xfire_read_buddy_online':
xfire.c:408: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:409: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c: In function 'xfire_read_buddys':
xfire.c:446: warning: passing argument 1 of 'xfire_read_dynamic_var_attr' from incompatible pointer type
xfire.c:451: warning: passing argument 1 of 'xfire_read_dynamic_var_attr' from incompatible pointer type
xfire.c:453: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:456: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c: In function 'xfire_read_invitation':
xfire.c:496: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c:502: warning: implicit declaration of function '_'
xfire.c:504: warning: passing argument 1 of 'g_strdup_printf' makes pointer from integer without a cast
xfire.c: In function 'xfire_new_buddy':
xfire.c:536: warning: incompatible implicit declaration of built-in function 'strncpy'
xfire.c:536: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c: In function 'xfire_rem_buddy':
xfire.c:549: warning: incompatible implicit declaration of built-in function 'strncpy'
xfire.c:549: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c: In function 'xfire_read_status':
xfire.c:565: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c:570: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c: In function 'xfire_game_status':
xfire.c:606: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:606: warning: pointer targets in passing argument 5 of 'xfire_read_dynamic_attr' differ in signedness
xfire.c:607: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:607: warning: pointer targets in passing argument 5 of 'xfire_read_dynamic_attr' differ in signedness
xfire.c:608: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:608: warning: pointer targets in passing argument 5 of 'xfire_read_dynamic_attr' differ in signedness
xfire.c:609: warning: passing argument 1 of 'xfire_read_dynamic_attr' from incompatible pointer type
xfire.c:609: warning: pointer targets in passing argument 5 of 'xfire_read_dynamic_attr' differ in signedness
xfire.c: In function 'xfire_login_check':
xfire.c:635: warning: incompatible implicit declaration of built-in function 'strlen'
xfire.c:639: warning: implicit declaration of function 'strcmp'
xfire.c: In function 'xfire_packet_handler':
xfire.c:671: warning: implicit declaration of function 'read'
xfire.c:674: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c:690: warning: passing argument 2 of 'gaim_connection_error' makes pointer from integer without a cast
xfire.c:712: warning: incompatible implicit declaration of built-in function 'memcpy'
xfire.c: In function 'xfire_login_connect':
xfire.c:833: warning: passing argument 2 of 'gaim_connection_error' makes pointer from integer without a cast
xfire.c: In function 'xfire_login':
xfire.c:855: warning: passing argument 2 of 'gaim_connection_update_progress' makes pointer from integer without a cast
xfire.c:861: warning: passing argument 2 of 'gaim_proxy_connect' from incompatible pointer type
xfire.c:861: warning: passing argument 3 of 'gaim_proxy_connect' makes pointer from integer without a cast
xfire.c:861: warning: passing argument 4 of 'gaim_proxy_connect' makes integer from pointer without a cast
xfire.c:861: warning: passing argument 5 of 'gaim_proxy_connect' from incompatible pointer type
xfire.c:861: error: too few arguments to function 'gaim_proxy_connect'
xfire.c:862: warning: passing argument 2 of 'gaim_connection_error' makes pointer from integer without a cast
xfire.c: In function 'xfire_list_emblems':
xfire.c:878: error: 'GaimBuddy' has no member named 'present'
xfire.c:878: error: 'GAIM_BUDDY_OFFLINE' undeclared (first use in this function)
xfire.c: In function 'xfire_set_away':
xfire.c:917: warning: passing argument 2 of 'xfire_create_away' discards qualifiers from pointer target type
xfire.c:922: warning: passing argument 2 of 'xfire_create_away' makes pointer from integer without a cast
xfire.c: In function 'xfire_away_states':
xfire.c:943: warning: passing argument 2 of 'g_list_append' makes pointer from integer without a cast
xfire.c:944: warning: passing argument 2 of 'g_list_append' makes pointer from integer without a cast
xfire.c: In function 'xfire_prpl_tooltip_text':
xfire.c:970: warning: format '%s' expects type 'char *', but argument 3 has type 'int'
xfire.c: At top level:
xfire.c:999: warning: initialization from incompatible pointer type
xfire.c:1001: warning: initialization from incompatible pointer type
xfire.c:1002: warning: initialization from incompatible pointer type
xfire.c:1008: warning: initialization from incompatible pointer type
xfire.c:1012: warning: initialization from incompatible pointer type
xfire.c:1067: error: 'VERSION' undeclared here (not in a function)
xfire.c:1069: warning: implicit declaration of function 'N_'
xfire.c:1069: error: initializer element is not constant
xfire.c:1069: error: (near initialization for 'info.summary')
xfire.c:1071: error: initializer element is not constant
xfire.c:1071: error: (near initialization for 'info.description')
xfire.c:1073: error: 'GAIM_WEBSITE' undeclared here (not in a function)
xfire.c: In function 'init_plugin':
xfire.c:1089: warning: passing argument 1 of 'gaim_account_option_string_new' makes pointer from integer without a cast
xfire.c:1092: warning: passing argument 1 of 'gaim_account_option_int_new' makes pointer from integer without a cast
xfire.c:1095: warning: passing argument 1 of 'gaim_account_option_int_new' makes pointer from integer without a cast
make[2]: *** [xfire.lo] Error 1
make[2]: Leaving directory `/home/user/Desktop/gaim-xfire-0.5.8/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/Desktop/gaim-xfire-0.5.8'
make: *** [all-recursive-am] Error 2

```


Sorry how long it is, you can pretty much skip some parts until the "errors" and "warnings" start...


Any fix for this or if someone could tell me how to run the pre-compiled version would be appreciated.

Based upon your build logs, you need the [i686 version which can be found here]("http://downloads.sourceforge.net/gfire/gfire-0.7.1.deb") (note that the version is subject to change and you're best off checking gfire's download page), also if you want to build, it's much easier to use dpkg-buildpackage as opposed to checkinstall/installing without a package. :)

---

### Post by cory94bailly on 2008-12-04
> **uberushaximus said:**
> Based upon your build logs, you need the [i686 version which can be found here]("http://downloads.sourceforge.net/gfire/gfire-0.7.1.deb") (note that the version is subject to change and you're best off checking gfire's download page), also if you want to build, it's much easier to use dpkg-buildpackage as opposed to checkinstall/installing without a package. :)

```
/home/user> cd /home/user/Desktop
/home/user/Desktop> sudo dpkg -i gfire-0.7.1.deb
Selecting previously deselected package gfire.
(Reading database ... 77242 files and directories currently installed.)
Unpacking gfire (from gfire-0.7.1.deb) ...
Setting up gfire (0.7.1) ...
/home/user/Desktop>

```

But I went to Gaim and I do not see a xfire option :/

---

### Post by Kaspar Nagarian on 2008-12-27
Here's what I'm getting

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for sed... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
configure: error: pkg-config could not locate either libssl.pc or openssl.pc
please make sure you have the development package for openssl/libssl installed
for your distribution. They are usually -dev or -devel packages.

```

---

### Post by kevdog on 2008-12-27
I was able to install this no problem. However I had compiled pidgin from source so I had previously installed all the necessary dependencies.

I added this to my tutorial here:
[http://ubuntuforums.org/showthread.php?t=975783](http://ubuntuforums.org/showthread.php?t=975783)

To answer specifically the question above, you need the libssl-dev library installed prior

sudo aptitude install libssl-dev

When you get errors such as these, you need to find the name of the specific libraries.  The best way to search for libraries if you know part of the name is using apt-cache.  Something similar to the following:

apt-cache search libssl

This will list packages associated to libssl.  Choose the most appropriate package -- in this case libssl-dev.  Use apt-cache often -- its your friend.

---

### Post by jalvarez1029 on 2009-01-05
So after reading the instructions and posts, all I figured out on my own was to change gaim to pidgin and obviously change the version number. This is what it gave me. Can anyone tell me what I'm missing? Much appreciated.

```
primalforce@Holocron:~/gfire-0.7.1$ sudo ./configure --with-pidgin=/usr/lib/pkg-config/ --prefix=/usr && make && sudo make install
[sudo] password for primalforce: 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/primalforce/gfire-0.7.1/missing: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
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
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PIDGIN... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.0.0... yes (version 2.18.2)
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
./configure: line 6507: ./po/POTFILES.in: No such file or directory
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
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
configure: creating ./config.status
config.status: creating Makefile
config.status: creating pixmaps/Makefile
config.status: creating src/Makefile
config.status: creating pre_config.h
config.status: executing depfiles commands
config.status: executing default-1 commands

Configuration complete

Debugging enabled.............: no
Pidgin package prefix.........: /usr
Pidgin package libdir.........: /usr/lib
Install prefix................: /usr
Install libdir................: /usr/lib
Pidgin lib dir detected.......: Yes


Type make to compile

Make sure you copy data/gfire_games.xml to /home/primalforce/.purple/

/bin/sed 's/#define PACKAGE/#define SNPP_PACKAGE/g' pre_config.h > gfire_config.h
make  all-recursive
make[1]: Entering directory `/home/primalforce/gfire-0.7.1'
Making all in src
make[2]: Entering directory `/home/primalforce/gfire-0.7.1/src'
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -DLIBDIR=\"/usr/lib/purple-2/\" -DDATADIR=\"/usr/share\" -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/pidgin -I/usr/include/gtk-2.0 -I/usr/include/libpurple -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12      -DPURPLE_PLUGINS -Wall -g3 -MT gfire.lo -MD -MP -MF .deps/gfire.Tpo -c -o gfire.lo gfire.c
In file included from gfire.c:24:
gfire.h:28:1: warning: "PURPLE_PLUGINS" redefined
<command-line>: warning: this is the location of the previous definition
gfire.c: In function 'gfire_blist_emblems':
gfire.c:65: warning: unused variable 'i'
gfire.c:64: warning: unused variable 'emblems'
gfire.c: In function 'gfire_login':
gfire.c:231: warning: passing argument 5 of 'purple_proxy_connect' from incompatible pointer type
gfire.c:231: warning: assignment makes integer from pointer without a cast
gfire.c: In function 'gfire_action_reload_lconfig_cb':
gfire.c:965: warning: unused variable 'result'
gfire.c: In function 'gfire_action_get_gconfig_cb':
gfire.c:1022: warning: 'return' with a value, in function returning void
gfire.c:1027: warning: implicit declaration of function 'g_remove'
gfire.c:1029: warning: 'return' with a value, in function returning void
gfire.c: In function 'gfire_actions':
gfire.c:1055: warning: passing argument 2 of 'purple_plugin_action_new' from incompatible pointer type
gfire.c: At top level:
gfire.c:1363: warning: initialization makes integer from pointer without a cast
gfire.c:1419: fatal error: opening dependency file .deps/gfire.Tpo: Permission denied
compilation terminated.
make[2]: *** [gfire.lo] Error 1
make[2]: Leaving directory `/home/primalforce/gfire-0.7.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/primalforce/gfire-0.7.1'
make: *** [all] Error 2

```

---

### Post by schobits211 on 2009-01-05
[img]http://www.top1gaming.com/cosplay2/20081107/BrilliantBlue-2.jpg[/img]  See the answer [[color=#800080]click here[/color]](http://www.top1gaming.com/coscontent-184.html).  Want to see [[color=#800080]more pics[/color]](http://www.top1gaming.com/cosplayer.php)? Show yourself  on our forum [[color=#800080]click here [/color]](http://www.top1gaming.com/forum/index.php?gid=27)**Recommend:**[[color=orange]Final Fantasy Advent Children[/color]](http://www.top1gaming.com/forum/thread-12200-1-1.html)[[color=orange]Cosplay Cute Kipi Pia[/color]](http://www.top1gaming.com/forum/thread-12190-1-1.html)

---

### Post by mike689 on 2009-07-27
> **jalvarez1029 said:**
> So after reading the instructions and posts, all I figured out on my own was to change gaim to pidgin and obviously change the version number. This is what it gave me. Can anyone tell me what I'm missing? Much appreciated.

```
primalforce@Holocron:~/gfire-0.7.1$ sudo ./configure --with-pidgin=/usr/lib/pkg-config/ --prefix=/usr && make && sudo make install
[sudo] password for primalforce: 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/bash: /home/primalforce/gfire-0.7.1/missing: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
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
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PIDGIN... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.0.0... yes (version 2.18.2)
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
./configure: line 6507: ./po/POTFILES.in: No such file or directory
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
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
configure: creating ./config.status
config.status: creating Makefile
config.status: creating pixmaps/Makefile
config.status: creating src/Makefile
config.status: creating pre_config.h
config.status: executing depfiles commands
config.status: executing default-1 commands

Configuration complete

Debugging enabled.............: no
Pidgin package prefix.........: /usr
Pidgin package libdir.........: /usr/lib
Install prefix................: /usr
Install libdir................: /usr/lib
Pidgin lib dir detected.......: Yes


Type make to compile

Make sure you copy data/gfire_games.xml to /home/primalforce/.purple/

/bin/sed 's/#define PACKAGE/#define SNPP_PACKAGE/g' pre_config.h > gfire_config.h
make  all-recursive
make[1]: Entering directory `/home/primalforce/gfire-0.7.1'
Making all in src
make[2]: Entering directory `/home/primalforce/gfire-0.7.1/src'
/bin/bash ../libtool --silent --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..  -DLIBDIR=\"/usr/lib/purple-2/\" -DDATADIR=\"/usr/share\" -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/pidgin -I/usr/include/gtk-2.0 -I/usr/include/libpurple -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12      -DPURPLE_PLUGINS -Wall -g3 -MT gfire.lo -MD -MP -MF .deps/gfire.Tpo -c -o gfire.lo gfire.c
In file included from gfire.c:24:
gfire.h:28:1: warning: "PURPLE_PLUGINS" redefined
<command-line>: warning: this is the location of the previous definition
gfire.c: In function 'gfire_blist_emblems':
gfire.c:65: warning: unused variable 'i'
gfire.c:64: warning: unused variable 'emblems'
gfire.c: In function 'gfire_login':
gfire.c:231: warning: passing argument 5 of 'purple_proxy_connect' from incompatible pointer type
gfire.c:231: warning: assignment makes integer from pointer without a cast
gfire.c: In function 'gfire_action_reload_lconfig_cb':
gfire.c:965: warning: unused variable 'result'
gfire.c: In function 'gfire_action_get_gconfig_cb':
gfire.c:1022: warning: 'return' with a value, in function returning void
gfire.c:1027: warning: implicit declaration of function 'g_remove'
gfire.c:1029: warning: 'return' with a value, in function returning void
gfire.c: In function 'gfire_actions':
gfire.c:1055: warning: passing argument 2 of 'purple_plugin_action_new' from incompatible pointer type
gfire.c: At top level:
gfire.c:1363: warning: initialization makes integer from pointer without a cast
gfire.c:1419: fatal error: opening dependency file .deps/gfire.Tpo: Permission denied
compilation terminated.
make[2]: *** [gfire.lo] Error 1
make[2]: Leaving directory `/home/primalforce/gfire-0.7.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/primalforce/gfire-0.7.1'
make: *** [all] Error 2

```

As of today I tried this and got the same results. Anyone?

---

### Post by ubun2ibun3 on 2009-08-07
Well, [http://www.gfireproject.org/](http://www.gfireproject.org/) has a download page where you can download the source, debs, and rpms of gfire, but when I installed it (32-bit deb without errors) Pidgin doesn't have the protocol, and gfire is not displayed in the plugins.

---

### Post by ccleanerfan on 2009-10-09
This no longer works, Karmic Koala

---

### Post by kevdog on 2009-10-11
I just compiled Gaim Zfire from svn version 0.9.0-svn.  I'm currently on Intrepid, but I don't think the platform or version matters.  

Here is what I did (Make sure you have the subversion package installed.  I am sure there are other dependencies, however I had them installed from compiling Pidgin).

svn co [http://my-svn.assembla.com/svn/gfire](http://my-svn.assembla.com/svn/gfire)
cd gfire/trunk
./autogen.sh
./configure
make
sudo make install

It worked for me!!!

---

### Post by Kreative_Station on 2009-10-20
> **ccleanerfan said:**
> This no longer works, Karmic Koala


Is that really true?

Well I'm running Ubuntu 9.10 Beta and just did the upgrade from 9.04 about 1 day ago.

...do you think if I installed it properly AND THEN upgraded to 9.10 it would have worked?!

[http://gfireproject.org/](http://gfireproject.org/)

...according to the frontpage on the website it will...

---

### Post by Lokidrakon on 2009-12-08
[http://gfireproject.org/](http://gfireproject.org/)

this site doesn't even work for me.

---

### Post by ccleanerfan on 2009-12-09
> **Lokidrakon said:**
> [http://gfireproject.org/](http://gfireproject.org/)

this site doesn't even work for me.
Not sure what's wrong with their site, just svn update.

[http://www.assembla.com/spaces/gfire/trac_subversion_tool](http://www.assembla.com/spaces/gfire/trac_subversion_tool)

---

