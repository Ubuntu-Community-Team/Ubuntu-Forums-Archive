---
title: "installing objective-c 2.0 on ubuntu 12.04 and 14.04"
date: 2015-05-22
forum: Programming Talk
---

### Post by mark allyn on 2015-05-22
Hello everyone,

i need help on installing objective-c 2.0 on my 12.04 and 14.04 systems.  I want the current full range (blocks, @autorelease,etc.) of features that objective-c 2.0 provides.  In order to do this I need to install llvm, 4 different modules from the GNUstep project, and clang-3.5.  I believe I have downloaded the correct files, but  I have run into problems compiling the GNUstep modules, and so far after two days of frustration, I have gotten nowhere.

I was hoping someone(s) in the Ubuntu Forum could give me guidance how to do the installation.  

Regards,
Mark Allyn

---

### Post by flaymond on 2015-05-24
I don't use clang and I don't program in Obj-C, but this might help - [http://blog.tlensing.org/2013/02/24/objective-c-on-linux-setting-up-gnustep-clang-llvm-objective-c-2-0-blocks-runtime-gcd-on-ubuntu-12-04/](http://blog.tlensing.org/2013/02/24/objective-c-on-linux-setting-up-gnustep-clang-llvm-objective-c-2-0-blocks-runtime-gcd-on-ubuntu-12-04/)

I just use gcc with gobjc if I gonna start learn that language, however, it's may not be the latest though. Thanks.

---

### Post by mark allyn on 2015-05-24
Hello InterProg,

I've been using GCC and GNUstep (which does the linking with necessary gobjc files).  This works, but gcc has not implemented a few features such as blocks (similar to Lambda expressions in Java).  Recent versions of Clang have done this, or so I am told.  In addition, you need to have the objective-c 2.0 library installed.  

I'll check the link you sent, but I'm about ready to give up on this and go buy a mac and get hold of a IDE called Xcode4 (or 5) which has everything I need.  Xcode4 is available only for OSX.  Perhaps someday someone will port it over to Linux, but I haven't detected any efforts to do so.

Thanks for trying to help.

Mark

Hi again, InterProg,

I looked at the link you sent.  I had already found it and I actually tried to do what it proposes.  Got part way thru the compilation process only to have the ./configure step for the GNUstep Base library fail with a nasty little error message--for which there was no information forthcoming on repeated google searches.

Frustrating.

Thanks, again,
Mark

---

### Post by flaymond on 2015-05-24
If you developing iOS or for OSX, I prefer using Mac because Mac got it's own supported softwares specialized for developing 'native' apps of that platform. Objective-C is also very much supported in that platform, since it uses Obj-C as the main programming language for higher-level applications devs. Before you giving up, you should try read this first -http://www.gnustep.org/developers/suite.shtml.

-o-

you can google for the libraries that available in repo or worked for others.

I'm actually don't know anything about Obj-C other than it's got thin layer extension of smalltalk that letting obj-c becoming more 'object-oriented' than pure C. I can only help by giving links.  I'm sorry because I can't help you further than that.  :(

---

### Post by steeldriver on 2015-05-24
I believe I was successful in doing this, on my 64-bit 14.04 box as follows

Basically I followed the instructions in this blog

[http://blog.tlensing.org/2013/02/24/objective-c-on-linux-setting-up-gnustep-clang-llvm-objective-c-2-0-blocks-runtime-gcd-on-ubuntu-12-04/](http://blog.tlensing.org/2013/02/24/objective-c-on-linux-setting-up-gnustep-clang-llvm-objective-c-2-0-blocks-runtime-gcd-on-ubuntu-12-04/)

using the latest stable sources from

[http://wwwmain.gnustep.org/resources/downloads.php?site=ftp%3A%2F%2Fftp.gnustep.org%2Fpub%2Fgnustep%2F](http://wwwmain.gnustep.org/resources/downloads.php?site=ftp%3A%2F%2Fftp.gnustep.org%2Fpub%2Fgnustep%2F)

which are currently gnustep-back-0.24.1  gnustep-base-1.24.8  gnustep-gui-0.24.1  gnustep-make-2.6.7

and libobjc2-1.7 from [http://download.gna.org/gnustep/](http://download.gna.org/gnustep/)

but with the following deviations

1. I used cmake for the libobjc2 build, in place of the (apparently deprecated) autoconf system

```
tar xvf ~/Downloads/libobjc2-1.7.tar.bz2

cd libobjc2-1.7/

mkdir Build && cd Build

cmake .. -DCMAKE_C_COMPILER=clang -DCMAKE_CXX_COMPILER=clang++ -DLIB_INSTALL_PATH=/usr/local/lib
```

Note that I had to add an explicit LIB_INSTALL_PATH in addition to the suggested compiler settings else cmake fails with an error about missing LIBRARY DESTINATION


2. For the GNUstep component builds, instead of simple exporting a CC variable and running `make`, I actually configured each with the appropriate environement i.e.

In ~/src/gnustep-dev/gnustep-make-2.6.7:
```

CC=clang CXX=clang++ ./configure --prefix=/usr/local
make
sudo make install

```

In ~/src/gnustep-dev/gnustep-base-1.24.8 
```

CC=clang CXX=clang++ ./configure --prefix=/usr/local
make
sudo make install

```

3. At this point, I found it to be necessary to run ldconfig else the subsequent gnustep-gui build fails to find the base library in /usr/local - you may not need this if you install to /usr (this is in fact discussed in the blog comments)

```
sudo ldconfig -v
```


In ~/src/gnustep-dev/gnustep-gui-0.24.1
```

CC=clang CXX=clang++ ./configure --prefix=/usr/local
make
sudo make install

```

In ~/src/gnustep-dev/gnustep-back-0.24.1
```

CC=clang CXX=clang++ ./configure --prefix=/usr/local
make
sudo make install

```

4. I found it necessary to modify the poster's build command (else the sample code built but segfaulted on running) - what worked for me was

```
clang `gnustep-config --objc-flags` -fblocks -o main -x objective-c main.m `gnustep-config --gui-libs` -ldispatch
```

Hope this helps

---

### Post by mark allyn on 2015-05-24
Good evening, Steeldriver,

In my experience you are far and away the most helpful mentors in the delicate art of Ubuntu.  Thanks much for replying to my query.

As I mentioned to InterProg, I was aware of, and had tried to use, tlensing's tutorial.  Where I bogged down and fell apart was in his Step 4 where he 2. installs GNUstep Base.  The ./configure came back with a message regarding my use of a compiler that wasn't GCC.  I couldn't figure out what flags to set that would make it work.

The message was as follows:

> configure: error: You are running configure with the compiler (clang-3.5) set to a different value from that used by gnustep-make (gcc).  Please run configure again with your environment set to match your gnustep-make


Before running ./configure for this file, I had set export CC=clang-3.5.  I can see your flags are different, and I will try those.

Thanks.  You have provided a much needed surge of optimism.

Mark Allyn

Good morning, Steeldriver,

Well, I had high hopes you and I were gonna lick this thing, but I failed almost right out of the box.  Here's how.

I downloaded all of the most recent files, as you suggested.  I proceeded to your step 1.  I followed your code exactly.  Cmake spit back a bunch of errors, most of which concerned not finding certain files at their expected locations.
 --The files not found were:  LLVMConfig.cmake, LLVMExports.cmake, LLVM-Config.cmake, ADDLLVM, 
 --and for good measure cmake said that it encountered an unknown command :  add_llvm_loadable_module.

Now, as a matter of fact, some of the missing files actually are in my directory tree, but not at the location cmake was searching.  I suppose one solution (ugly) is to copy the files from where they are currently into a directory thru which cmake is hunting.  That might work for the first three of the above, but I cannot find ADDLVM anywhere, and I have no clue as to how to fix the unknown command.

By the way, the version of clang I'm using is clang-3.4.  From the errors, it appears this isn't an issue.  And, you're right, you must use cmake.

So, there we are.

Regards,
Mark

---

### Post by steeldriver on 2015-05-25
Sorry Mark I don't know what would be causing that - the only one of those files that appears to be on my system is

```

$ dpkg -S LLVMConfig.cmake LLVMExports.cmake LLVM-Config.cmake ADDLLVM
dpkg-query: no path found matching pattern *LLVMConfig.cmake*
dpkg-query: no path found matching pattern *LLVMExports.cmake*
** llvm-3.4-dev: /usr/share/llvm-3.4/cmake/LLVM-Config.cmake**
dpkg-query: no path found matching pattern *ADDLLVM*

```

What is your version of cmake and how did you install it? if you built it from source, maybe that got misconfigured somehow? Perhaps if you posted the full transcript from the libobjc2 cmake command it would make things clearer (you can use a hosting site such as pastebin if there is too much to post here directly)

---

### Post by mark allyn on 2015-05-25
Hi Steeldriver,

Been playing with this thing to the point my head is imploding.

First, spent morning googling around on LLVM, since so many of the problems seem to have arisen from that arena.  I seem to have found a thread from some california guys that indicate that if LLVM was compiled with gcc and not with cmake, then LLVM files show up in the wrong directories when clang searches for them when its trying to compile gnustep.  Looking at their suggestion for how to recompile LLVM with cmake made me feel like I was wading deeper into the proverbial "bog of Saint Finian".  How to know, for example, which version of LLVM to compile so that it will be compatible with the clang version that compiles GNUstep?

So, I did what only a po boy can do...continued to Google.  What I found was a nice bash script written by the very same tobias lensing whose post set you and I off.  It was essentially a script that captured what you did but was intended for 12.04, not 14.04.  That script is located at [https://gist.github.com/starbugs/5025357#file-install-gnustep-sh](https://gist.github.com/starbugs/5025357#file-install-gnustep-sh).

So, I executed it on my 12.04 box.  BTW, the script uses CLANG and not GCC.  No surprise.  All was going swimmingly until I hit the build of gnustep-gui.  ./configed OK once I give it the right LDFLAGS.  But, crashed in the make step.  It complains that there is a conflict between gnustep-base.so.1.22 and gnustep-base.so.1.24.  In the script, I built gnustep-base.so.1.24 and it is located properly in /usr/local/lib. 

So, there we/I are.  The worst part of all is that I have cratered my previous gnustep installation and even running the stripped down objc fails.  Wasted, wasted.

Regards,
Mark

Good afternoon, Steeldriver,

Progress to report.  After reviewing and comparing your code with Tobias Lensing's post and also his bash script I finally saw what was wrong.  I hadn't done the --prefix=/usr/local prior to configuring the gnustep-gui and ldconig'g it.  When I did that, everything compiled just as you said.

I then proceeded to test using TLensing's code.  First I tried his command line stuff.  It failed miserably.  Then, I replaced his with yours and the darn thing seg faulted.  However, there were warnings in the link step that this might happen becaue the linker reported that two different shared objects were in conflict with two others.  

I think I know why this is happening.  There is a disparity in version numbers between two of the core gnustep libraries.  (.22 vs .24).  I may have to back and download from GNUstep repositories.  Perhaps I was sloppy when I did the original downloads?

But, progress, for sure.

Regards,
Mark

---

### Post by steeldriver on 2015-05-25
Sounds like you are on the home straight - the library linkage issue may just be a matter of which version was installed last (and therefore created the latest symlink) 

For reference (NB remember this is 14.04 though), I have

```

$ ls -l /usr/local/lib/lib{gnustep,objc}*
lrwxrwxrwx 1 root root       23 May 24 09:57 /usr/local/lib/libgnustep-base.so -> libgnustep-base.so.1.24
lrwxrwxrwx 1 root root       25 May 24 09:57 /usr/local/lib/libgnustep-base.so.1.24 -> libgnustep-base.so.1.24.8
-rwxr-xr-x 1 root root 13909013 May 24 09:52 /usr/local/lib/libgnustep-base.so.1.24.8
lrwxrwxrwx 1 root root       22 May 24 10:10 /usr/local/lib/libgnustep-gui.so -> libgnustep-gui.so.0.24
lrwxrwxrwx 1 root root       24 May 24 10:10 /usr/local/lib/libgnustep-gui.so.0.24 -> libgnustep-gui.so.0.24.1
-rwxr-xr-x 1 root root 17678607 May 24 10:10 /usr/local/lib/libgnustep-gui.so.0.24.1
lrwxrwxrwx 1 root root       14 May 24 09:44 /usr/local/lib/libobjc.so -> libobjc.so.4.6
-rw-r--r-- 1 root root   246447 May 24 09:26 /usr/local/lib/libobjc.so.4.6
lrwxrwxrwx 1 root root       16 May 24 09:44 /usr/local/lib/libobjcxx.so -> libobjcxx.so.4.6
-rw-r--r-- 1 root root    19321 May 24 09:26 /usr/local/lib/libobjcxx.so.4.6

```

Makes you appreciate the effort that goes into debian package management, doesn't it ;)

---

### Post by mark allyn on 2015-05-26
Good afternoon, Steeldriver,

Owing to necessary farm chores this morning, I had little time to spend on the problem.  But, I did make some efforts and here they are summarized.  

I have two Ubuntu boxes I'm playing with for this install.  The one I made progress on yesterday is a 12.04 64bit machine.  I have a second box that is 14.04 32 bit.  This morning I tried doing the install WITH THE CORRECT versions of GNUstep core modules on the 14.04 box.  When I attempt to use cmake on the libobjc2-1.7 file, I hit a snag.  It's the same one I reported previously.  Namely, it can't do the cmake because it can't find the correct LLVM files.  

I reloaded cmake (sudo apt-get install cmake)  on thie 14.04 box but same thing happens.  What I don't "get" is why you're not having trouble on 14.04 and I am.  Should be the same outcomes, I would think.

Ideas?

Mark

---

### Post by steeldriver on 2015-05-26
Mine is x86-64, however the package lists show the same files in the i386 package. What exactly is your llvm-x.y-dev version? e.g.

```

$ apt-cache policy llvm-3.4-dev 
llvm-3.4-dev:
  Installed: 1:3.4-1ubuntu3
  Candidate: 1:3.4-1ubuntu3
  Version table:
 *** 1:3.4-1ubuntu3 0
        500 http://ca.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status

```

Possibly related to this bug?  [https://bugs.launchpad.net/ubuntu/+source/llvm/+bug/1365432](https://bugs.launchpad.net/ubuntu/+source/llvm/+bug/1365432)

---

### Post by mark allyn on 2015-05-26
Hello again Steeldriver,

Here's what turns up:

> llvm-3.4-dev:
  Installed: 1:3.4-1ubuntu3
  Candidate: 1:3.4-1ubuntu3
  Version table:
 *** 1:3.4-1ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main i386 Packages
        100 /var/lib/dpkg/status


Looks the same as yours.  BTW, thanks for pointing out this functionality apt.  Didn't know about it.  Another hidden jewel.

Mark

Steeldriver--

Should have also added that cmake version is:  2.8.12.2

Somewhere I recall seeing that cmake needed to be at least 2.8 and above.

Mark

---

### Post by mark allyn on 2015-05-26
Steeldriver,

OK, so I went back and peeked instide of libobjc2-1.7 and found that there was a conventional Makefile there.  I went ahead and tried to take advantage of that by entering "make" followed by sudo make install.  I did get the message about make being deprecated, but it didn't say that it wouldn't do the job.  And, it appears that it did.  So, I went ahead and followed your script.

Then I wrote a portion of tlensing's test program.   What happened was interesting, but disheartening.  Everything compiled and linked fine (again, using your command line parameters).  However, when run it produced an error message, specifically:

> ./testmain: symbol lookup error: /usr/local/lib/libgnustep-base.so.1.24: undefined symbol: _objc_weak_load


Hmmm...  So, I looked inside /usr/local/lib and discovered that there was no gui.so in there.  So, I went back and reran the entire script for the gnustep-gui-0.24.1 directory.  And, you guessed it, the gui build produced a similar message and bombed.  Which is why it doesn't show up in /usr/local/lib.

I'll see what I can get off the web.

I suppose this is progress....

Mark

---

### Post by mark allyn on 2015-05-27
Steeldriver,

I shelved work on the 32 bit 14.04 machine today owning to my inability to uncover anything to do with the undefined symbol mentioned in my previous post.

I reverted to working on the 64 bit 12.04 machine.  This time I used exactly the same gnustep modules and libobjc2-1.7 that you used.  Everything seemed to work alright.  I then tried to run the testprogram that you ran.  I used your command line and got an error:

> error while loading shared libraries: libgnustep-gui.so.0.24: cannot open shared object file: No such file or directory

I also contructed a GNUstep GNUmakefile and ran make on that file.  Got exactly the same error.

Hmmm.  I checked /usr/local/lib and the gnustep-gui.so.0.24 is there.

Mark

---

### Post by steeldriver on 2015-05-31
Actually Mark I'm going to have to retract the advice above

After discovering that it should be possible to create a deb package of libobjc using the new cmake build system, I decided to start over. In the process, I discovered some suspicious gnustep-related things that may have been left over from previous install attempts. Having removed all those and unpacked fresh tarballs of the libobcj2.1.7 and gnustep sources, I attempted to re-do the process as follows:

1. build and install libobjc2.1.7 as a deb
```

cd libobjc2-1.7/

mkdir Build && cd Build

cmake .. -DCMAKE_C_COMPILER=clang -DCMAKE_CXX_COMPILER=clang++ -DLIB_INSTALL_PATH=/usr/lib/ -DCPACK_GENERATOR=DEB

make package

```

This seems to work OK, and produces a libobjc-1.7.0-Linux.deb package file that I was able to install using dpkg -i

2. configure and install gnustep-make
```

cd ../../gnustep-make-2.6.7

CC=clang CXX=clang++ ./configure --prefix=/usr/local

make install

```
Again, seems to be no problem so far.

3. attempt to configure and install gnustep-base
```

cd ../gnustep-base-1.24.8

CC=clang CXX=clang++ ./configure --prefix=/usr/local

make

```

The configure appears to go fine, however make fails with
```

 Compiling file AGSIndex.m ...
 Compiling file AGSHtml.m ...
 Linking tool autogsdoc ...
../Source/./obj/libgnustep-base.so: undefined reference to `objc_arc_autorelease_count_for_object_np'
../Source/./obj/libgnustep-base.so: undefined reference to `objc_autoreleasePoolPush'
../Source/./obj/libgnustep-base.so: undefined reference to `objc_arc_autorelease_count_np'
../Source/./obj/libgnustep-base.so: undefined reference to `objc_autorelease'
../Source/./obj/libgnustep-base.so: undefined reference to `objc_autoreleasePoolPop'
../Source/./obj/libgnustep-base.so: undefined reference to `_objc_class_for_boxing_foreign_exception'
clang: error: linker command failed with exit code 1 (use -v to see invocation)
make[4]: *** [obj/autogsdoc] Error 1
make[3]: *** [internal-tool-all_] Error 2
make[2]: *** [autogsdoc.all.tool.variables] Error 2
make[1]: *** [internal-all] Error 2
make: *** [internal-all] Error 2

```

The error (which is different from yours, I think) seems to be because version 3.4 of clang (which is the version in the 14.04 repo) provides built-in Objective-C support, and as such it installs its own version of libobjc, specifically

```

clang depends clang-3.4 depends libobjc-4.8-dev depends libobjc4

```
and
```

$ dpkg -S /usr/lib/x86_64-linux-gnu/libobjc.so.4.0.0
libobjc4:amd64: /usr/lib/x86_64-linux-gnu/libobjc.so.4.0.0

```

This is the library that clang seems to find first by default, since
```

$ nm -D /usr/lib/x86_64-linux-gnu/libobjc.so.4.0.0 | grep objc_arc_autorelease

```
returns nothing whereas the symbols clearly exist in the newly-installed library
```

$ nm -D /usr/lib/libobjc.so.4.6 | grep objc_arc_autorelease
00000000000210e0 T objc_arc_autorelease_count_for_object_np
0000000000020fd0 T objc_arc_autorelease_count_np

```

I haven't found any combination of configuration flags / environment variables that allows clang-3.4 to find the newly-built .so in /usr/lib ahead of the version in /usr/lib/x86_64-linux-gnu

At this point, I am stuck - sorry

---

