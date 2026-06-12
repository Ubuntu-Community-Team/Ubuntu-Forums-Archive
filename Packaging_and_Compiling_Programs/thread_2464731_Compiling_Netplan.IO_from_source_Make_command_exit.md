---
title: "Compiling Netplan.IO from source Make command exits with an error"
date: 2021-07-10
forum: Packaging and Compiling Programs
---

### Post by dhiaagr on 2021-07-10
Hello,

I am painfully new to compiling and would love your insight as well as guidance to the appropriate documentation.
I am compiling Netplan.IO to use on a Debian 10 i386.

It came to my understanding that 
```
$ make
```
would automatically compile the package following directives in the `makefile` file.

However, the command exits with an error.

```
cc -g -fPIC -std=c99 -D_XOPEN_SOURCE=500 -DSBINDIR=\"/usr/sbin\" -Wall -Werror    -c src/parse.c `pkg-config --cflags --libs glib-2.0 gio-2.0 yaml-0.1 uuid`

src/parse.c: In function 'netplean_clear_netdefs':
src/parse.c:2719:9: error: implicit declaration of function 'g_clear_list'; did you mean 'g_clear_object'? [-Werror=implicit-function-declaration]
      g_clear_list(&netdefs_ordered, g_free);
      g_clear_object

cc1: all warnings being treated as errors

make: *** [Makefile:39; parose.o] Error 1

```

I suspect that there's some flag to set to ignore warnings, however, I would love some insight and redirection towards useful ressources to learn more about compiling.

There is no option to open an issue on the git page of the project..

---

### Post by TheFu on 2021-07-10
Check that you have all the dependencies installed.  The errors above say there are some missing dependencies.  Read the errors. Find where those functions and headers are located, figure out which dependencies contain those - usually a {package}-dev would be the .deb package.  Of course, you can run into the rabbit hole and start following all the source dependencies too. Hopefully, it is just a few, but for a highlevel package like netplan, it could be a significant number of dependencies.  I've never looked at that program, so I really don't know. At least it isn't a GUI, then there could be hundreds of dependencies.

Is there a reason "why" you want to build netplan?  That's the better question.

Nothing is "automatic" in setting up a build environment. Sorry.

---

### Post by dhiaagr on 2021-07-10
Hi TheFu, thank you for your reply.
I understand now. The y to my xy problem is that I still don't know much about building a package, compiling and c language in general, but I'm willing to learn.

As for your question, I'm trying to learn Debian in depth and hopefully, one day, be able to compile a kernel on my own. It's an old i386 laptop from the golden days where manufacturers were racing to put as many peripherals as they could. "Infrared, line in, card readers". I believe it is a good machine to learn about the kernel, firmware and granular control of the computer.
So yes, I'm planning to be able to not rely on automatic, anymore.
+ I like netplan, I would love to, some day, have it on any machine I own regardless if it's running Ubuntu or not.

Learn to figure out what dependencies are needed for me, it is, then.
If you have a book to recommend about what I'm trying to achieve : "Learn to build packages", that is up to date, I'd be grateful.

Thanks again, and have a nice day.

---

### Post by TheFu on 2021-07-10
I don't know anyone who learns to build packages BEFORE learning simple C coding.

Also, there are 500,000 different ways to build programs, so there is no "1-way" to build packages. As for how debian does it for their releases, I honestly do not know. It has never come up.  I haven't built a kernel since the 1990s.  An i386 (the real CPU) hasn't been supported by Ubuntu in many, many, yrs.  Support for i686 CPUs was dropped in 2019.

There are multiple build tools, each used depending on the project team.  I use GNU Make, but the new kids use cmake.  These are slightly different.  Different languages use other tools - Java uses ant.  Perl has a build system too.

Build systems are separate from packaging systems.  I'm not certain that is clear.  Most Linux distros are based on 1 of 4 different package types.  deb/APT, rpm/dnf, whatever Arch uses/pacman, and tgz packages ... which are basically source that gets used by slackware and gentoo.  But each of these packaging systems is still dependent on the underlying dependencies for the distro release of target.  A .deb package for 14.04 won't work on a 16.04 box. The dependencies are all wrong.

---

### Post by monkeybrain20122 on 2021-07-10
> **dhiaagr said:**
> 
**cc1: all warnings being treated as errors**

make: *** [Makefile:39; parose.o] Error 1




So that seems to be the issue.

Do you have a configure file? i.e Do you run 

```
./configure
```

before make?

if yes

just run
```
CFLAGS=-Wno-error ./configure
```

instead.

if not, manually edit the make file and remove all -Werror from CFLAGS, CPPFLAGS in the file before you run make.


But before doing any of these you want to start with a clean slate, either delete the source folder altogether and start with a clean copy or run

```
make clean && make distclean
```

---

### Post by TheFu on 2021-07-10
So, I looked at the github for netplan: [https://github.com/canonical/netplan](https://github.com/canonical/netplan).  It uses a plain, simple, Makefile. No autoconfig or libconfig or mkconfig are involved.  
The README.md file is terrible.  It points to architecture and usage, not build, information.  I get the feeling they think if you don't know gmake, then you have no need to build it.  The Makefile seems standard.  Anyone with intermediate gmake skills wouldn't have any trouble reading and using it.

looks like I have to split my reply due to ongoing forum issues.

---

### Post by dhiaagr on 2021-07-11
Hi @MonkeyBrain, thank you for the time you took to give me some stuff to investigate and learn.

@TheFu,  that's how it works when you're learning on your own, at least in my  case. Tons of time of confusion with people who know better all around  you telling you : "omg, such a noob" but in the end, it's all worth it.

No shortcut to compiling but through learning C, it is then. Fortunately, I'm already acquainted with CS fundamentals.
Thank you, again.

---

### Post by TheFu on 2021-07-11
I tried to post the different parts of the reply to get around current forum problems and failed about 10 times.
[http://*******.us/4iPlTv](http://*******.us/4iPlTv) has the remaining parts of the reply. It won't post here.

---

### Post by TheFu on 2021-07-11
http:// s p r u n g e . u s/4iPlTv
see if that works.  If not, I give up.

---

### Post by dhiaagr on 2021-07-11
Thank you so much for your elaborate answer on the ******* pastebin.
Obviously, I need some time to educate myself on what I'm trying to achieve. Yours and Monkeybrain's answers pointed me to the right direction and made me want to do it even more.

I consider my issue as resolved :
My question : What's up with this error ?
The appropriate answer : You lack libraries and the decent knowledge to figure that on your own.

God bless and ttyl, I hope.

---

### Post by TheFu on 2021-07-11
> **dhiaagr said:**
> Thank you so much for your elaborate answer on the ******* pastebin.
Obviously, I need some time to educate myself on what I'm trying to achieve. Yours and Monkeybrain's answers pointed me to the right direction and made me want to do it even more.

I consider my issue as resolved :
My question : What's up with this error ?
The appropriate answer : You lack libraries and the decent knowledge to figure that on your own.

God bless and ttyl, I hope.

Some header files are missing too.  The uuid.h file I used was odd.  UUIDs are used in many parts of storage management. I never would have considered a UUID being part of anything network related previously. The header files for the other libraries need more research. I showed the commands I would use to determine those things.

If you consider this thread solved, only you, the OP, can click on the "Thread Tools" button and mark it "SOLVED". We cannot. Moderators will not.

---

### Post by Karl_Redgate on 2021-11-01
> **dhiaagr said:**
> 
I suspect that there's some flag to set to ignore warnings, however, I would love some insight and redirection towards useful ressources to learn more about compiling.


The other answers to this question were not really helpful.

I have seen this same issue - and the primary problem is likely the same as what I have seen.   If you cloned the github repo for netplan - that would be the most recent version.  If you are compiling on an older version of Ubuntu - the library interfaces may not match.  In my case I am building on 18.04 - and the most recent versions of netplan do not compile without intervention on that release.  Look at previous releases in github - for 18.04  I needed to go back to the 0.101 release - and that compiles without error on 18.04.  If you are using a more recent version of Ubuntu - it is possible (likely even) that it uses a newer version of netplan.

---

