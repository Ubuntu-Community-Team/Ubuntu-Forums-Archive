---
title: "(64-bit) Build the latest of Pidgin"
date: 2008-01-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Perfect Storm on 2008-01-04
**Tested:** Ubuntu 7.10 64-bit Gnome (should work as well on 32-bit)
**Homepage:** [http://www.pidgin.im/](http://www.pidgin.im/)
**Original Guide:** [http://polarbeardk.blogspot.com/2008/01/build-pidgin-from-source-710-64bit.html](http://polarbeardk.blogspot.com/2008/01/build-pidgin-from-source-710-64bit.html)

Pidgin is a multi-protocol Instant Messaging client that allows you to use all of your IM accounts at once.

This guide show how to build the latest version of Pidgin, plus the following plugins:

[LIST]
[*]talkfilter
[*]Purple-Pluginpack (require talkfilter)
[*]guification
[*]Off-the-Record Messaging
[*]Pidgin-Encryption
[*]Pidgin extended preferences
[*]...more to come
[/LIST]

[[img]http://www.imageviper.com/displayimage/107293/0/Pre-Pidgin.png[/img]](http://www.imageviper.com/displayimage/107292/0/Pidgin.png)
[size=1]Click to enlarge[/size]


===========================================

[SIZE="5"]**Before Installation**[/SIZE]

First thing you need is to enable all the sources in your repository. You can do that by; System tab ---> Administration ---> Software Sources.
You also need to enable medibuntu which you can find here; [http://www.medibuntu.org/]("http://www.medibuntu.org/")

When that is done, open the terminal (Applications tab ---> Accessories ---> Terminal ).
To build Pidgin from the source the right tools, libs and headers is needed, also the old pidgin needs to be uninstall, type this in the terminal;

```
sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude remove pidgin pidgin-data
sudo aptitude install build-essential linux-headers-`uname -r` checkinstall
sudo aptitude install libexpat1-dev libintl-perl gettext bcp libx11-dev libgcrypt11-dev libgtk2.0-dev libxss-dev libsm-dev libstartup-notification0-dev libgtkspell-dev libsqlite3-dev libecal1.2-dev libncursesw5-dev libgconf2-dev libgstreamer0.10-dev libmeanwhile-dev libavahi-client-dev libavahi-glib-dev libavahi-compat-howl-dev libsilc-1.1-2-dev libgadu-dev libperl-dev libgnutls-dev doxygen xsltproc tcl8.4-dev tk8.4-dev check libnss3-dev dot2tex libecal1.2-dev libedata-book1.2-dev flex libnm-glib-dev libmng-dev mono mono-mcs libmono-dev libsasl2-dev libzephyr-dev libkrb5-dev
```

Done. Now you're ready to compile Pidgin and its plugins.


[SIZE="5"]**Installation**[/SIZE]

**Pidgin**
Pidgin is a multi-protocol Instant Messaging client that allows you to use all of your IM accounts at once.

```
cd ~/Desktop
wget http://downloads.sourceforge.net/pidgin/pidgin-2.3.1.tar.bz2
tar jxfv pidgin-2.3.1.tar.bz2
cd pidgin-2.3.1
./configure --prefix=/usr --enable-mono --enable-cyrus-sasl --enable-nm --with-krb4
make
sudo checkinstall
```


[SIZE="5"]**Plugins**[/SIZE]

**Talkfilter**
The GNU Talk Filters are filter programs that convert ordinary English text into text that mimics a stereotyped or otherwise humorous dialect. These filters have been in the public domain for many years, but now for the first time they are provided as a single integrated package. The filters include austro, b1ff, brooklyn, chef, cockney, drawl, dubya, fudd, funetak, jethro, jive, kraut, pansy, pirate, postmodern, redneck, valspeak, and warez. Each program reads from standard input and writes to standard output. The package also provides the filters as a C library, so they can be easily used by other programs.
[[Homepage]](http://www.hyperrealm.com/main.php?s=talkfilters)

```
cd ~/Desktop
wget http://www.hyperrealm.com/talkfilters/talkfilters-2.3.8.tar.gz
tar zxfv talkfilters-2.3.8.tar.gz
cd talkfilters-2.3.8
./configure --prefix=/usr
make
sudo checkinstall
```


**Purple Plugin Pack**
Full plugin list you'll find here: [http://plugins.guifications.org/trac/wiki/PluginPack](http://plugins.guifications.org/trac/wiki/PluginPack)
[[Homepage]](http://plugins.guifications.org/trac/news)

```
cd ~/Desktop
wget http://downloads.guifications.org/plugins//Plugin%20Pack/purple-plugin_pack-2.2.0.tar.bz2
tar jxfv purple-plugin_pack-2.2.0.tar.bz2
cd purple-plugin_pack-2.2.0
./configure --prefix=/usr
make
sudo checkinstall
```


**Guification**
Guifications is a Pidgin plugin that displays "toaster" popups in a user-defined corner of the screen, similar to features that have been added to the official MSN Messenger (now called Windows Live Messenger), Yahoo! Messenger and AOL Instant Messenger clients. It's highly configurable, easy to use, and has theme support. It really is the end-all, be-all toaster pop-up plugin for Pidgin!
[[Homepage]](http://plugins.guifications.org/trac/news)

```
cd ~/Desktop
wget http://downloads.guifications.org/plugins//Guifications2/pidgin-guifications-2.16.tar.bz2
tar jxfv pidgin-guifications-2.16.tar.bz2
cd pidgin-guifications-2.16
./configure --prefix=/usr
make
sudo checkinstall
```


**Off-the-Record Messaging**
Off-the-Record (OTR) Messaging allows you to have private conversations over instant messaging by providing: Encryption, Authentication, Deniability and Perfect forward secrecy.
[[Homepage]](http://www.cypherpunks.ca/otr/)

```
cd ~/Desktop
wget http://www.cypherpunks.ca/otr/libotr-3.1.0.tar.gz http://www.cypherpunks.ca/otr/pidgin-otr-3.1.0.tar.gz
tar zxvf libotr-3.1.0.tar.gz && tar zxvf pidgin-otr-3.1.0.tar.gz
cd libotr-3.1.0
./configure --prefix=/usr
make
sudo checkinstall
cd ~/Desktop/pidgin-otr-3.1.0
./configure --prefix=/usr
make
sudo checkinstall
```


**Pidgin-Encryption**
Pidgin-Encryption transparently encrypts your instant messages with RSA encryption. Easy-to-use, but very secure.
[[Homepage]](http://pidgin-encrypt.sourceforge.net/)

```
cd ~/Desktop
wget http://downloads.sourceforge.net/pidgin-encrypt/pidgin-encryption-3.0.tar.gz?modtime=1178510638&big_mirror=0
tar zxfv pidgin-encryption-3.0.tar.gz
cd pidgin-encryption-3.0
./configure --prefix=/usr
make
sudo checkinstall
```


**Pidgin extended preferences**
The Pidgin Extended Preferences Plugin adds additional preferences that have been commonly called for in the past from Pidgin that are either already implemented and hidden, or trivial to implement via a plugin.
[[homepage]](http://gaim-extprefs.sourceforge.net/)

```
cd ~/Desktop
wget http://downloads.sourceforge.net/gaim-extprefs/pidgin-extprefs-0.7.tar.gz?modtime=1177805917&big_mirror=0
tar zxfv pidgin-extprefs-0.7.tar.gz
cd pidgin-extprefs-0.7
./configure --prefix=/usr
make
sudo checkinstall
```


That should be it. Request a plugin that isn't shown here if you need it.


Enjoy

Regards
A.I. Dude

===========================================
Other 64-bit guides:
[Build the latest of Audacious](http://ubuntuforums.org/showthread.php?p=4072585)
[Install F-prot (anti-virus)](http://ubuntuforums.org/showthread.php?t=623665)
[Install AVG (anti-virus)](http://ubuntuforums.org/showthread.php?t=622967)

---

### Post by kevdog on 2008-01-04
Excellent guide, however I think you left some information out about the purple plugin pack, particularly how to activate the plugins that my default would not be compiled (like group message). 

Also I couldn't compile all the most recent purple plugins as of 1/3/2008.  I received some errors with certain packages.

Any possibilities that you could include some svn instructions for some plugins (if svn versions are availalble)?

Other plugins I like are 
otr [http://www.cypherpunks.ca/otr/](http://www.cypherpunks.ca/otr/) -- need libotr
pidgin encryption -  [http://gaim-encryption.sourceforge.net](http://gaim-encryption.sourceforge.net)
Pidgin extended preferences - [http://gaim-extprefs.sourceforge.net/](http://gaim-extprefs.sourceforge.net/)

Thanks

---

### Post by Perfect Storm on 2008-01-05
I'll take a look at it.

---

### Post by Perfect Storm on 2008-01-05
Extensive Guide update.

-- guide completly updated.
-- missing libs added
-- enabled mono (remove the flag if you don't want it and/or remove mono-dev from the guides before installation).
-- added 3 new plugins: Off-the-Record Messaging, Pidgin-Encryption and Pidgin extended preferences.
-- Link added to each plugin guide.

---

### Post by kevdog on 2008-01-14
Here is another plugin that I saw mentioned on another post.  It prevents IM spam:

[http://sourceforge.net/projects/pidgin-bs/](http://sourceforge.net/projects/pidgin-bs/)

---

### Post by genbuntu on 2008-01-28
My installation fails at the 'make' step :( .
I'm currently using pidgin 2.2.1  on fiesty .

Here is the error I get during 'make' :

```
make  all-recursive
make[1]: Entering directory `/home/sid/pidgin-2.3.1'
Making all in libpurple
make[2]: Entering directory `/home/sid/pidgin-2.3.1/libpurple'
make  all-recursive
make[3]: Entering directory `/home/sid/pidgin-2.3.1/libpurple'
Making all in gconf
make[4]: Entering directory `/home/sid/pidgin-2.3.1/libpurple/gconf'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/sid/pidgin-2.3.1/libpurple/gconf'
Making all in plugins
make[4]: Entering directory `/home/sid/pidgin-2.3.1/libpurple/plugins'
Making all in mono
make[5]: Entering directory `/home/sid/pidgin-2.3.1/libpurple/plugins/mono'
Making all in api
make[6]: Entering directory `/home/sid/pidgin-2.3.1/libpurple/plugins/mono/api'
mcs -t:library -out:PurpleAPI.dll ./BlistNode.cs ./BuddyList.cs ./Buddy.cs ./Contact.cs ./Debug.cs ./Event.cs ./PurplePlugin.cs ./Group.cs ./Signal.cs ./Status.cs
/bin/bash: mcs: command not found
make[6]: *** [PurpleAPI.dll] Error 127
make[6]: Leaving directory `/home/sid/pidgin-2.3.1/libpurple/plugins/mono/api'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/sid/pidgin-2.3.1/libpurple/plugins/mono'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/sid/pidgin-2.3.1/libpurple/plugins'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/sid/pidgin-2.3.1/libpurple'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/sid/pidgin-2.3.1/libpurple'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sid/pidgin-2.3.1'
make: *** [all] Error 2

```

Advise please ? :confused:

---

### Post by Perfect Storm on 2008-01-28
Check if libmcs headers/dev is installed. If it aren't there. If it aren't there - you need to compile it as well
then make clean and run ./configure again

---

### Post by genbuntu on 2008-01-28
hmm... 'libmcs' doesn't appear in synaptic . So I guess it isn't installed.
Where can I download it from ? I was able to find a link but it seems dead : ( [http://sacredspiral.co.uk/~nenolod/mcs/](http://sacredspiral.co.uk/~nenolod/mcs/) )

Edit: I think this is the intended page: [http://atheme.org/projects/mcs.shtml](http://atheme.org/projects/mcs.shtml) 
Shall I download mcs 0.6.0 from there? I hope it is a trusted source and the latest one.

---

### Post by Perfect Storm on 2008-01-28
I'm not sure it's your problem, only a guess. You know that getdebs have binaries of pidgin latest, it is easier if you're not comftable with compiling (though with compiling you can customize the software yourself, if you know howto).

[http://www.atheme.org/projects/mcs.shtml](http://www.atheme.org/projects/mcs.shtml)

---

### Post by genbuntu on 2008-01-28
I did compile a few programs from source but I'm still new to linux on the whole . 
The thing with getdeb is that for fiesty they only have pidgin 2.2.0  as the latest one. But for Gusty they have 2.3.1 . Shall I install the gusty one on my system then ? 
I hope it will preserve my settings .  :confused:
Edit: I am also not hesitant to compiling it myself , as that is the best way I can learn. :)

---

### Post by Perfect Storm on 2008-01-28
Best to backup you vital stuff first if you decide to upgrade. It's a bit hard to give support for me to feisty as I moved to gutsy and the guide is tested on that system.

---

### Post by genbuntu on 2008-01-28
Ok, thanks. :)

---

### Post by Tonohono on 2008-02-04
Might want to add mono and mono-mcs to the list of packages to install, as without them one will encounter the same issue as Gebuntu did.

---

### Post by genbuntu on 2008-02-04
ahh...long story short :) :  Your post made me try again, which led to another troubleshooting and so on... until a few errors later I was finally able to install pidgin 2.3.1 from source. lol.. Thanks.

---

### Post by Perfect Storm on 2008-02-09
fixed

---

### Post by ronb94 on 2008-02-09
Thanks for this Howto.
This created a folder in the desktop, can i just move it to the home directory? or have i reinstall to the home ?

---

### Post by Perfect Storm on 2008-02-09
Is it installed (plus all the other stuff you wanted?)

---

### Post by kr0n1x on 2008-02-15
my *sudo checkinstall* stops at *Installing of Debian package...*
in italian: *Installazione pacchetto Debian in corso...*
i'm talking about the package pidgin-2.3.1... the first..
what can be the problem?? :(

---

### Post by Perfect Storm on 2008-02-15
Do you have synaptic open or anything else that handle packages?
Is the old version of pidgin removed?

---

### Post by kr0n1x on 2008-02-15
> **Artificial Intelligence said:**
> Do you have synaptic open or anything else that handle packages?
Is the old version of pidgin removed?

yes i did all passages.
anyway i rebooted ubuntu, i deleted "pidgin" package from synaptic (this was installed a bit... with the last checkinstal i think..), retried sudo checkinstall and this time worked (i keep all programs closed while checkinstalling)

thx :)

---

### Post by kevdog on 2008-02-15
Checkinstall isn't necessary -- its kind of a luxury feature if you want to install under the apt system.  If it doesnt mattter to you, sudo make install will work just as well and will be much quicker.

---

### Post by i M@N on 2008-02-16
Hello.

First of all many thnxX it worked fine for me.

i have little question : you wrote to configure/make/install this way :
> ./configure --prefix=/usr --enable-mono --enable-cyrus-sasl --enable-nm --with-krb4
make
sudo checkinstall
i went this one :
> ./configure --prefix=/usr --enable-mono --enable-cyrus-sasl --enable-nm --with-krb4 --enable-gnutls=yes
make
sudo make install
with --enable-gnutls=yes because in the past versions it's needed to log-in in hotmail and (i think) gmail ...
but could you please explain what means :
> --enable-mono --enable-cyrus-sasl --enable-nm --with-krb4
and what these configure options do exactly ?

@+...

---

### Post by kr0n1x on 2008-02-16
anyway, what *--enable-mono --enable-cyrus-sasl --enable-nm --with-krb4* do?? why i need mono? and others?
thanks

---

### Post by kevdog on 2008-02-29
Here is yet another list of plugins Ive been able to find.  Possibly you could add these to your guide since I consider your guide for compiling pidgin the most complete and accurate available.  I appreciate the time you spent constructing the guide.

# pidgin-blinklight : Blink the new message led on IBM and Asus laptop.
This is contained in the gutsy and hardy repositories.
Also source is here:
[http://packages.ubuntu.com/source/gutsy/pidgin-blinklight](http://packages.ubuntu.com/source/gutsy/pidgin-blinklight)

# pidgin-guifications : Microsoft Windows like pop-up notifications.
[http://plugins.guifications.org/trac/wiki/Guifications](http://plugins.guifications.org/trac/wiki/Guifications)
Source located here: [http://downloads.guifications.org/plugins//Guifications2/pidgin-guifications-2.16.tar.gz](http://downloads.guifications.org/plugins//Guifications2/pidgin-guifications-2.16.tar.gz)

# pidgin-hotkeys : configurable hotkeys for pidgin.
[http://pidgin-hotkeys.sourceforge.net/](http://pidgin-hotkeys.sourceforge.net/)
[http://prdownloads.sourceforge.net/pidgin-hotkeys/pidgin-hotkeys-0.2.3.tar.gz?download](http://prdownloads.sourceforge.net/pidgin-hotkeys/pidgin-hotkeys-0.2.3.tar.gz?download)
Its also available in the gutsy/hardy universe repositories if you dont want to compile

# pidgin-libnotify : display notification bubbles in pidgin.
[http://gaim-libnotify.sourceforge.net/](http://gaim-libnotify.sourceforge.net/)
Source: [http://sourceforge.net/project/showfiles.php?group_id=144907&package_id=237412&release_id=519933](http://sourceforge.net/project/showfiles.php?group_id=144907&package_id=237412&release_id=519933)

# pidgin-librvp : MS Exchange RVP instant messaging plugin.
[http://packages.ubuntu.com/gutsy/net/pidgin-librvp](http://packages.ubuntu.com/gutsy/net/pidgin-librvp)
Its also available in the repository in you dont want to compile

---

### Post by bobbo85 on 2008-03-07
Artificial Intelligence, I may have made a boo boo...
I am not running 64-bit Ubuntu, and I just ran the 4 commands from this post in "Before Installation"
It is right now downloading and installing something like 850mb worth of stuff from the last command (I think it's getting the libs etc)...

Do you think I broke anything?  Can I undo what I just did?

---

### Post by Perfect Storm on 2008-03-07
No - I havn't measure how much it will download. But building pidgin requires alot of libs and their -dev packages (using for compiling and stuff).
Just report back if something seems funny (as in smelly).

---

### Post by bobbo85 on 2008-03-08
Here's the update Artificial Intelligence:
I was still unable to compile the program from source unfortunately; however, I downloaded three .deb files from getdeb.net and successfully installed the program using those.

Did anyone ever come up with a solution to the ./configure issue?

The initial problem was that I had the source for 2.4.0 downloaded and extracted.  From the terminal, in the directory, I typed "./configure" and got the error:
configure: error: cannot find install-sh or install.sh in "." "./.." "./../.."

In fact, just now I tried again and still get that error...

Thanks for calming me down though about that huge download, i was a little worried!

---

### Post by chesch on 2008-03-12
AI, I was wondering where we put the themes for guifications?

I just downloaded DarkandSmall from [http://sourceforge.net/tracker/index.php?func=detail&aid=1681089&group_id=92888&atid=676821](http://sourceforge.net/tracker/index.php?func=detail&aid=1681089&group_id=92888&atid=676821) and I am unsure as to where I should put the files.

---

### Post by Perfect Storm on 2008-03-12
Try with
```
~/.purple/guifications/themes
```

or have a look in ~/.purple to see which folder to put it in.

---

### Post by sheriffS on 2008-12-10
good day to you. i followed everything in this thread. but in the part where i use "make" it gives me an error.


thanks. ^^



---

i already settled this one. i use "make install" instead of "make". im running pidgin now, but i think i'll be having more problems. soon.^^

---

### Post by rootk1t on 2009-01-18
Hi .configure is going ok but after I type make I get the error:

	then mv -f ".deps/debug-glue.Tpo" ".deps/debug-glue.Plo"; else rm -f ".deps/debug-glue.Tpo"; exit 1; fi
debug-glue.c: In function ‘purple_debug_glue’:
[B]debug-glue.c:12: error: format not a string literal and no format arguments
make[6]: *** [debug-glue.lo] Error 1[/B]
make[6]: Leaving directory `/home/john/Desktop/pidgin/pidgin-2.5.4/libpurple/plugins/mono/loader'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/home/john/Desktop/pidgin/pidgin-2.5.4/libpurple/plugins/mono'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/john/Desktop/pidgin/pidgin-2.5.4/libpurple/plugins'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/john/Desktop/pidgin/pidgin-2.5.4/libpurple'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/john/Desktop/pidgin/pidgin-2.5.4/libpurple'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/john/Desktop/pidgin/pidgin-2.5.4'

---

### Post by stormtrooprdave on 2009-01-18
Is guification unable to handle transparency?  All the themes I've seen are a bit uninspiring but when I change the opacity of the theme image it causes corruption in the display

---

### Post by bodysoda on 2009-02-16
```

root@bodysoda:~/Desktop/pidgin-2.5.4$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking whether gcc and cc understand -c and -o together... yes
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether NLS is requested... yes
checking for intltool-update... no
checking for intltool-merge... no
checking for intltool-extract... no
configure: error: The intltool scripts were not found. Please install intltool.


```

I get error message. 
any help

---

### Post by jagnikam on 2009-02-16
apt-get install intltool

---

### Post by wojzeh on 2009-02-22
> **Artificial Intelligence said:**
> 

[SIZE="5"]**Before Installation**[/SIZE]

First thing you need is to enable all the sources in your repository. You can do that by; System tab ---> Administration ---> Software Sources.
You also need to enable medibuntu which you can find here; [http://www.medibuntu.org/]("http://www.medibuntu.org/")

When that is done, open the terminal (Applications tab ---> Accessories ---> Terminal ).
To build Pidgin from the source the right tools, libs and headers is needed, also the old pidgin needs to be uninstall, type this in the terminal;

```
sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude remove pidgin pidgin-data
sudo aptitude install build-essential linux-headers-`uname -r` checkinstall
sudo aptitude install libexpat1-dev libintl-perl gettext bcp libx11-dev libgcrypt11-dev libgtk2.0-dev libxss-dev libsm-dev libstartup-notification0-dev libgtkspell-dev libsqlite3-dev libecal1.2-dev libncursesw5-dev libgconf2-dev libgstreamer0.10-dev libmeanwhile-dev libavahi-client-dev libavahi-glib-dev libavahi-compat-howl-dev libsilc-1.1-2-dev libgadu-dev libperl-dev libgnutls-dev doxygen xsltproc tcl8.4-dev tk8.4-dev check libnss3-dev dot2tex libecal1.2-dev libedata-book1.2-dev flex libnm-glib-dev libmng-dev mono mono-mcs libmono-dev libsasl2-dev libzephyr-dev libkrb5-dev
```

Done. Now you're ready to compile Pidgin and its plugins.



thanks for your instructions!
just a quick question. after having done this stage I realized that my diskspace decreased by 6 Gb. I am not sure that it worth leaving it as is. So, please tell me how I can remove all this cool stuff from my ubuntu 8.04.

---

