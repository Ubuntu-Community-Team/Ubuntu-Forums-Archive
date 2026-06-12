---
title: "Odd discovery - Source code and speed"
date: 2014-01-28
forum: Programming Talk
---

### Post by Tristan_Williams on 2014-01-28
This discovery sprouted from a long line of random thoughts and a few hours of pointless daydreaming... basically heres what I discovered:

I decided to go through the firefox source code, and remove every comment, every blank line of code, and every tab.
This left me with a (much smaller) hunk of uncommented, untabbed code.

And to my suprise, it actually made Firefox faster. I mean a lot freaking faster. I'm guessing it's from the smaller file sizes and less processing power used when bypasssing comments.
I will say I don't know much about code and compiling and software speed.

Anyways, so over the 3 weeks following that, I decided to do that to all major components of my OS, (xfce, xfwm, firefox, thunderbird, bash, libreoffice, and some of the x11 things)
I could not believe how much this has increased the overall speed of my OS...

Maybe one of you could enlighten me as to why what I did made such a difference. Perhaps then I could squeeze even more out of this code :)

---

### Post by robert49 on 2014-01-28
I am subscribing to this post, I don't have any idea how you managed to find that but I am interested to find out from one of the bigger boys out here. Enlighten us !

---

### Post by mastablasta on 2014-01-28
perhaps you are still daydreaming? :-D

seriously, can you show us the speed up time with some benchmarking program?

---

### Post by ssam on 2014-01-28
The compiler ignores comments, so they make no difference to what ends up in the executable.

However numbers are numbers, so if you have benchmark results between the 2 versions, and they were compiled with all the same options on the same machine then its very interesting.

---

### Post by steeldriver on 2014-01-28
Are you comparing two versions that you built on your machine, one with and and one without comments - or are you comparing a build without comments on your machine against a standard pre-built binary from the repository?

At least in C/C++, comments are stripped out by the pre-processor (you can verify this by running gcc -E *somefile.c*)

---

### Post by The Cog on 2014-01-28
> **ssam said:**
> The compiler ignores comments, so they make no difference to what ends up in the executable.

However numbers are numbers, so if you have benchmark results between the 2 versions, and they were compiled with all the same options on the same machine then its very interesting.

I believe this to be true of compiled languages, although I'm not sure if any commenting goes into the compiled binaries as debugging info and making the binaries bigger.

However, I gather that most of firefox is written in an interpreted language called XUL. I wonder if this is what Tristan_Williams has been editing. I can well imaging that making a difference.

---

### Post by philinux on 2014-01-28
Moved to programming talk.

---

### Post by ssam on 2014-01-28
> **The Cog said:**
> I believe this to be true of compiled languages, although I'm not sure if any commenting goes into the compiled binaries as debugging info and making the binaries bigger.

However, I gather that most of firefox is written in an interpreted language called XUL. I wonder if this is what Tristan_Williams has been editing. I can well imaging that making a difference.

[https://www.ohloh.net/p/firefox/analyses/latest/languages_summary](https://www.ohloh.net/p/firefox/analyses/latest/languages_summary)
Firefox is mostly C++ and C, with some javascript and others (I think XUL would show as XML on that chart). However the performance critical code should all be in C and C++.

If the comment stripping holds up to benchmarks I am sure mozilla would like to know. They put a lot of effort into performance.

---

### Post by Tristan_Williams on 2014-01-28
I am performing benchmarks here in a few hours. I will post the results when I am done.

---

### Post by Tristan_Williams on 2014-01-28
I ran some tests and heres what I found:

Testing Conditions were as follows:
- xfce4 Desktop environment
- Most current updates as of Jan 28 2014 9:15pm
- Newly created user, as to not have any random startup apps, old settings lying around, or any other form of possible corruption
- No applications running, except application being tested (Mozilla Firefox)
- Dell Vostro 220 Series Desktop Computer - 3 GB of DDR2 RAM, Intel core2 duo processor.
- 310 GB HDD (300 GB as root, 10 GB as swap)
- 'cat /proc/sys/vm/swappiness' returns '10'
- OS: Ubuntu Minimal, build into a full, lightweight desktop environment.
- Kernel: 3.11.0-15-lowlatency

Disclaimer: I did not use a benchmarking software. I do not know how to use them, and google only told me how to test overall system performance. So they wouldn't have helped anyways...
I used a combination of top, htop, and timed the speed of various tasks (the tests were conducted EXACTLY the same)

Firefox Test 1, 2, 3, 4, and 5:
Compiled WITH unchanged code. 
Avg RAM used: 5.4% (165.8 mb)
Avg CPU usage: 1.7%
Application Loading time: 3.5 seconds
google.com load time: 4 seconds
facebook.com load time: 5.5 seconds
ubuntuforums.org load time: 4 seconds

Firefox Test 6, 7, 8, 9, and 10:
Compiled WITH changed code
Avg RAM used: 4.9% (165.8 mb)
Avg CPU usage: 1.5%
Application Loading time: 3.1 seconds
google.com load time: 3.75 seconds
facebook.com load time: 5 seconds
ubuntuforums.org load time: 3.3 seconds

Code changes include:
- Removed all comments from source code
- Removed all blank lines from source code
- Removed all "tabs" from source code (that includes tabs and unneeded spaces)
- Combined all code which was spread over more than one line, into a single line. example(yeah i know it's in bash, not c++):
```

sudo apt-get install xfce4 xfce4-goodies \
firefox thunderbird \
libreoffice gedit gedit-plugins

becomes this:
sudo apt-get install xfce4 xfce4-goodies firefox thunderbird libreoffice gedit gedit-pliugins

```
That's just an example of what i mean by "combining lines"
- Removed unneeded files from the source tree (i.e the AUTHORS file, the INSTALL instructions, and all of the other files not actually used by the application)

All tests were coducted EXACTLY the same, with the same conditions.
I conducted 5 tests per version... actually, let me rephrase that... I compiled and installed the normal version 5 times, and tested 3 times each round, and did the same for the edited version.

I realize that this isn't as valid as actual benchmarks. If you want actual benchmarks, someone is gonna have to tell me how to benchmark APPLICATIONS, and not the entire system.

---

### Post by tgalati4 on 2014-01-29
*phoronix-test-suite* has quite a few benchmarks.  I'm not familiar with the web-based ones so you will have to poke around.

I'm impressed.  You have gained some small performance improvements with your efforts.  Do you have a script that semi-automates the stripping process?  It would be tedious to have to repeat this process for every Firefox update.

---

### Post by nidzo732 on 2014-01-29
When you did the test, did you use the binaries from the repositories, or did you also compile the slower (commented) version yourself?

If you just used the repository binaries, there is a more logical explanation: the repo binaries are compiled for the general x86 (or amd64) architecture, they are supposed to work on all processors and they don't have any processor-specific optimizations. When you compile the proram locally, the compiler optimizes it for your local architecture (if the proper optimization flags are turned on). This causes the hand-compiled version to run faster than the version form the repository.

---

### Post by ofnuts on 2014-01-29
My first check would be to compile the full and stripped source and check if the compilation results are identical. If they aren't then there must be some place to report GCC bugs.

---

### Post by Tristan_Williams on 2014-01-29
Yes, i compiled both versions manually. I did another (control) test with using the prebuilt binaries and those were just stupidly slow...

Anyways, no I don't have a script to automate the process, althought that would come in very handy.

---

### Post by Tristan_Williams on 2014-01-30
Latest update on this project:

I conducted identical tests on XFCE, Thunderbird, LibreOffice, Blender, Ardour, LightDM, Guake, and Preload.

It seems as though the larger the size of the program, the more it benefits from the code changes, even if the exact same amount of code is removed, the changes seem almost exponential.

This REALLY needs to be investigated further.

Imagine this:
Gentoo (because it is 100% source) 
Lightweight packages (for example: XFCE instead of KDE or Gnome)
These code changes for every single package.
lowlatency kernel, preload, and the "alternative to the 200-lines patch"

I am already grinning stupidly at my screen...

---

### Post by tgalati4 on 2014-01-30
Damn Small Linux and TinyCore Linux used a similar approach.  Delete all of the extraneous stuff and you can get a full operating system in 10 MB.  It runs stupidly fast on modern machines, but more importantly, it allowed you to run linux on really old computers and have a useful environment.

Several years ago, I read an article that called out Gentoo's performance improvement to be only 2% when compiling on your hardware versus Ubuntu or Fedora pre-built distros. So you have to ask yourself is getting that 2% improvement worth the agnony units of spending a few days compiling everything from scratch?  Perhaps your work proves that there are improvements to be gained.

Imagine cleaning  up Gentoo and then custom compiling and performing some benchmarks on modern hardware.  I bet you could get 5 to 10% improvement.

---

