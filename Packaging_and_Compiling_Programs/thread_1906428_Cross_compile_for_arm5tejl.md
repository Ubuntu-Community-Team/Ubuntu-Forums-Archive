---
title: "Cross compile for arm5tejl"
date: 2012-01-09
forum: Packaging and Compiling Programs
---

### Post by nickolasemp on 2012-01-09
Hello there!

I would like to use a patched mediatomb to my NAS 110 that uses debian lenny. Therefore I want to **create an arm deb package (armv5tejl) and then distribute it to the world. ** I have a feeling that I am going the wrong way here.

I have managed to set up PdaXrom, so that I could compile a helloworld (although I didn't run it) and I am stuck as to how I can configure properly the mediatomb. My goal is to use checkinstall in the end and create a deb file.

I followed the instructions from 
[http://artisan.karma-lab.net/node/66/revisions/66/view](http://artisan.karma-lab.net/node/66/revisions/66/view)
but I still am stuck at configure
nick@ubuntu:~/Programs/mediatomb$ ./configure --enable-static 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
configure: Building a static executable.
checking whether the C++ compiler works... no
configure: error: in `/home/nick/Programs/mediatomb':
configure: error: C++ compiler cannot create executables
See `config.log' for more details
nick@ubuntu:~/Programs/mediatomb$ 


The config.log lies here [http://pastebin.com/JC0EmgSq](http://pastebin.com/JC0EmgSq)

Plus the sh file that intiates the environment
#!/bin/bash
. /etc/profile
export CROSS_HOME=/opt/cross/arm/3.4.6-xscale-softvfp
export PATH=$CROSS_HOME/bin:$PATH:.
#export PATH=/opt/cross/arm/3.4.5-xscale-softvfp/bin:$PATH
export QTDIR=$CROSS_HOME/armv5tel-cacko-linux/qt
export KDEDIR=$CROSS_HOME/armv5tel-cacko-linux/qt
export X11INC=$CROSS_HOME/armv5tel-cacko-linux/include
export X11LIB=$CROSS_HOME/armv5tel-cacko-linux/lib
export PKG_CONFIG_PATH=$CROSS_HOME/armv5tel-cacko-linux/lib/pkgconfig
export LD_LIBRARY_PATH=$CROSS_HOME/lib
export CC=/opt/cross/arm/3.4.6-xscale-softvfp/bin/armv5tel-linux-gcc
export CXX=/opt/cross/arm/3.4.6-xscale-softvfp/bin/armv5tel-linux-g++
export LDFLAGS="-Wl,-rpath-link,$CROSS_HOME/armv5tel-cacko-linux/X11R6/lib"
export CONFIG="-host=armv5tel-cacko-linux --build=i686-linux --x-includes=$CROSS_HOME/armv5tel-cacko-linux/X11R6/include --x-libraries=$CROSS_HOME/armv5tel-cacko-linux/X11R6/lib --disable-debug"
export QMAKESPEC="$CROSS_HOME/armv5tel-cacko-linux/qt/mkspecs/default"
echo "Type exit to end this environment"
/bin/bash

Thank you in advance for your time.

---

### Post by azmyth on 2012-01-10
&#947;&#949;&#953;&#945; &#963;&#945;&#962;,

Do you have the libc6-dev package installed?

---

### Post by nickolasemp on 2012-01-25
First of all, thank you for your reply. I am so sorry that it took me so long to post a reply. I had not subscribed to the thread.

Secondly, I want to thank you that you took time to find how to greet me in my native language. It means so much.

Now, on to the topic discussed. I am thinking of giving up cross-compiling. It probably requires more time that I currently have. It is very interesting topic though.

I reinstalled everything from scratch to my (headless) NAS and disabled the logs. That way, with build-essential I can build minidlna and others as well.

Still thank you for your time to reply and have a concern for my problem.

---

