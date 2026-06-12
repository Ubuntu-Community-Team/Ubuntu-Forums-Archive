---
title: "Installer for source archives"
date: 2007-06-24
forum: Programming Talk
---

### Post by abhijeetmaharana on 2007-06-24
****
GUI Todo/Wishlist: [http://ubuntuforums.org/showpost.php?p=2948139&postcount=60](http://ubuntuforums.org/showpost.php?p=2948139&postcount=60)
****

It was raining outside and I was looking for something to do on a Sunday evening and then I stumbled upon this [http://ubuntuforums.org/showthread.php?t=482878](http://ubuntuforums.org/showthread.php?t=482878). I thought it would be helpful to have this feature suggested by Afoot. Right click on a source archive and install it. I have developed this barebones Java program which does that. I understand that installing Java for this isn't very convenient but that is the language I am most comfortable with. So let me know if its worth pushing this further. And besides, the program could also be rewritten in C or as a simple shell script with the commands used in the program. While developing, I used the xosd source archive which can be downloaded from the xosd homepage at [http://ignavus.net/software.html](http://ignavus.net/software.html) (it seems to be offline at the time of this writing). The current version is command line based. Usage and other instructions are available in the attached source code.

The TODO list:
[LIST=1]
[*]Cleanup of temporary files after installation
[*]Exception handling
[*]Ask sudo password only for running make install
[*]**GUI for running conveniently from Nautilus**
[*]More testing
[/LIST]

I intend to provide a GUI so that the command line is not necessary. Please post your comments and suggestions. I will keep this post updated with any progress made. Full source code is in the attached file: sourceInstaller.java.txt.


[COLOR="Blue"]**Update: June 27, 2007**[/COLOR]
Moved to [http://ubuntuforums.org/showpost.php?p=3060715&postcount=98](http://ubuntuforums.org/showpost.php?p=3060715&postcount=98)

[COLOR="Blue"]**Update: July 01-02 Midnight, 2007**[/COLOR]
Moved to [http://ubuntuforums.org/showpost.php?p=3060721&postcount=99](http://ubuntuforums.org/showpost.php?p=3060721&postcount=99)

[COLOR="Blue"]**Update: July 22, 2007**[/COLOR]
Moved to [http://ubuntuforums.org/showpost.php?p=3060803&postcount=100](http://ubuntuforums.org/showpost.php?p=3060803&postcount=100)

---

### Post by Afoot on 2007-06-24
Nice. :) I didn't expect anyone to begin implementing my idea that quick - great initiative! I agree with you, it could be easily re-written to C, as it would probably be best if the user didn't have to install Java prior to using this. 

Anyway, good work so far, I'm gonna subscribe to your thread right away, so be sure to update regularly. ;)

---

### Post by abhijeetmaharana on 2007-06-24
> **Afoot said:**
> Nice. :) I didn't expect anyone to begin implementing my idea that quick - great initiative! I agree with you, it could be easily re-written to C, as it would probably be best if the user didn't have to install Java prior to using this. 

Anyway, good work so far, I'm gonna subscribe to your thread right away, so be sure to update regularly. ;)

Thanks!!! I had always wished that installation from source was easier but automating the process never occurred to me. It feels nice now :-)
I have a couple of things in mind. Will update the thread when any progress is made. Keep your suggestions / ideas coming.

I was also thinking about an uninstaller but there are other items to be done before that.

---

### Post by Kelimion on 2007-06-24
Abhijeet,

This is a bit of a long shot, but as far as dependencies go and tracking them down in apt; say for example it requires 'faad' or 'libfaad', you could issue a command like:

------------------
$ aptitude search libfaad
p   libfaad2-0                      - freeware Advanced Audio Decoder - runtime 
p   libfaad2-dev                    - freeware Advanced Audio Decoder - development
-------------------

matching the word development the program would know that's most likely the dependency. Now to assure the repository has the required version, issue this command:

-------------------
$ aptitude show libfaad2-dev
Package: libfaad2-dev
State: not installed
Version: 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3
Priority: optional
Section: multiverse/libdevel
Maintainer: Sebastian Dröge <mail@slomosnail.de>
Uncompressed Size: 618k
Depends: libfaad2-0 (= 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3), libc6-dev |
         libc-dev
Replaces: libfaad2-0 (< 2.0.0clean-0ubuntu2)
Description: freeware Advanced Audio Decoder - development files
 FAAD2 is the fastest ISO AAC audio decoder available. FAAD2 correctly decodes
 all MPEG-4 and MPEG-2 MAIN, LOW, LTP, LD and ER object type AAC files. 
 
 This package contains development files.
---------------------

The hardest part will be determining the dependencies *before* compiling, so I suggest you don't.

It's likely much simpler to capture the output of the make stage, and check there for the compiler complaining of missing dependencies. Then use something like the above to go and fetch them, and re-make.

Hopefully this makes as much sense to you as it does to me. :D

> I was also thinking about an uninstaller but there are other items to be done before that.
That's a matter of holding on to the tarball and running make uninstall instead?

---

### Post by Afoot on 2007-06-25
> **abhijeetmaharana said:**
> 
I was also thinking about an uninstaller but there are other items to be done before that.
Perhaps it could be possible to make a deb file of it instead of "make install", so that you don't need to make an uninstaller?

---

### Post by Kelimion on 2007-06-25
> **Afoot said:**
> Perhaps it could be possible to make a deb file of it instead of "make install", so that you don't need to make an uninstaller?

That's an option as well, of course. And calling gdebi or dpkg to install it afterwards.

---

### Post by Ramses de Norre on 2007-06-25
I think you want to look into auto-apt, it automates the installation of necessary packages found by the configure script.

---

### Post by abhijeetmaharana on 2007-06-25
Looks like we have all the pieces fitting in. Lets take a look at the options we have got:
[LIST=1]
[*]aptitude search and aptitude show suggested by Kelimion (It makes a LOT of sense buddy :-))
[*]auto-apt suggested by Ramses de Norre
[*]dpkg -S / apt-file suggested by leibowitz in the original thread at [http://ubuntuforums.org/showpost.php?p=2907925&postcount=9](http://ubuntuforums.org/showpost.php?p=2907925&postcount=9)
[*]Uninstallation:
[/LIST][INDENT][LIST=1]
[*]make a .deb from the source so this is taken care of, posted by Afoot
[*]make uninstall posted by Kelimion
[/LIST]
make uninstall seems simpler. Maybe just one more call to executeCommand(). Making a .deb from the source is blurry at the moment but seems very attractive. What should we go with? I think we can have make uninstall for the moment and then add an option to create a .deb later on... Let me know.
[/INDENT]
Just got back from office. Can pull off about 1 1/2 hours tonight. And maybe 2 hours after office tomorrow. Should be able to post an update tomorrow night. Keep the ideas coming!!!

---

### Post by Kelimion on 2007-06-25
Sounds like good progress :)

If I were you I'd concentrate on getting the dependency thing down proper, so just about anything you throw at it will compile and install.

The reason I'm suggesting this be your priority is because this is something that will need to be hammered out regardless of whether you go the make install/uninstall route, or .deb, or both.

Making a .deb (if reliable) would be very useful to have as an option as well. I'm sure there's lots of developers out there who'd like to see this kind of automation, where they'd only have to package a tarball.

Then if there's a lot of developer interest in a tool like this, then a 3rd version could integrate with Alien to make a .rpm from the .deb, for example.

And presumably there's a non-handwaving way this tool could be extended to handle Python + Perl tarballs as well. This could be a version 4 (assuming you'd still be interested in the project ;)).

---

### Post by abhijeetmaharana on 2007-06-25
> **Kelimion said:**
> If I were you I'd concentrate on getting the dependency thing down proper, so just about anything you throw at it will compile and install.

I was thinking the same. Besides, I will be a bit busy on the coming weekend due to some personal work. I think I'll keep the GUI for this period since that should be easy.

> 
And presumably there's a non-handwaving way this tool could be extended to handle Python + Perl tarballs as well. This could be a version 4 (assuming you'd still be interested in the project ;)).
I would definitely still be interested!!! I may get to learn a bit of python/perl in the process :-)

---

### Post by Kelimion on 2007-06-25
Nice one. :D

I'll be monitoring this project, for sure. Should anything else come to mind, I'll be sure to let you know.

Edit: and something did.

One thing may be hard to impossible to get right: nightlies. First of all the repositories might be missing a particular version of a package, or they might be missing a package altogether.

Looking at VLC for instance, compiling that from subversion makes for an interesting hour, what with it depending on ffmpeg for support of certain codecs, which again has to be checked out. Still, there would be no problem in declaring nightlies/snapshots as 'abandon all hope, ye who enter here'. If it happens to compile, you lucked out. First and foremost I'd stick with numbered releases.

Should you come across the situation where you have a tarball that 'should work (tm)', but it so happens that a particular version or package isn't present in the repositories, you could offer a range of choices to the user still:
- Ask them to tick the pre-release repositories in the source management application (or editing the source list themselves if they know what they're doing).
- Offer to search [http://www.getdeb.net/](http://www.getdeb.net/) or similar sites. The tarball's filename will probably yield the project name if it follows naming convention, it could be used as a search term.

---

### Post by leibowitz on 2007-06-25
> **Kelimion said:**
> 
Making a .deb (if reliable) would be very useful to have as an option as well. I'm sure there's lots of developers out there who'd like to see this kind of automation, where they'd only have to package a tarball.

Kind of working on that one. Not exactly on what you said, but it is somewhat related.

[http://ubuntuforums.org/showthread.php?t=483890](http://ubuntuforums.org/showthread.php?t=483890)

---

### Post by leibowitz on 2007-06-25
Look what I just found in the debian maintainer guide.

> Here's a hack you can use to find out which packages your package needs to be built:

       strace -f -o /tmp/log ./configure
       # or make instead of ./configure, if the package doesn't use autoconf
       for x in `dpkg -S $(grep open /tmp/log|\
                           perl -pe 's!.* open\(\"([^\"]*).*!$1!' |\
                           grep "^/"| sort | uniq|\
                           grep -v "^\(/tmp\|/dev\|/proc\)" ) 2>/dev/null|\
                           cut -f1 -d":"| sort | uniq`; \
             do \
               echo -n "$x (>=" `dpkg -s $x|grep ^Version|cut -f2 -d":"` "), "; \
             done

To manually find exact build dependency for /usr/bin/foo, you execute

       objdump -p /usr/bin/foo | grep NEEDED

and for each library listed, e.g., libfoo.so.6, execute

       dpkg -S libfoo.so.6

Then you just take -dev version of every package as `Build-deps' entry. If you use ldd for this purpose, it will report indirect lib dependencies as well, resulting in the problem of excessive build deps.

Gentoo also happens to require xlibs-dev, libgtk1.2-dev and libglib1.2-dev to build, so we'll add them here next to debhelper. 

Source: [http://www.debian.org/doc/manuals/maint-guide/ch-dreq.en.html#s-control](http://www.debian.org/doc/manuals/maint-guide/ch-dreq.en.html#s-control)

---

### Post by abhijeetmaharana on 2007-06-26
> **leibowitz said:**
> Kind of working on that one. Not exactly on what you said, but it is somewhat related.

[http://ubuntuforums.org/showthread.php?t=483890](http://ubuntuforums.org/showthread.php?t=483890)

Nice!! It looked like a good candidate for a separate/sub project. We can integrate our work when we are ready. Ill go through your findings from the debian maintainer guide and see how we can use that.

---

### Post by Ramses de Norre on 2007-06-26
With all due respect, I doubt this will become a success... There are many different things that can be required in order to properly build and run a certain piece of software and they are mostly explained in the README. How will you go about stuff like 
*Should configure be used or should I directly execute make?
*Do I need specific headers? 
*If there is no configure but I miss some headers (which are probably described in the README) than how will my program find out which ones are needed?

I think you'll only be able to write a program like this for the small group of programs that follow the classic "./configure, make, make install" method. But it will fail on a lot of other programs that don't follow this model...

People should read README files, and if they don't understand them they are probably not capable of compiling programs from source (yet).

If a program like this was as easy as you think it is, every distro would have one developer who applies some patches and runs the program you're trying to make on each source tarball.

---

### Post by leibowitz on 2007-06-26
**Ramses de Norre **:
There's many case where you have to throw some particular option to the configure. Look at MPlayer for example, it's a mess to compile.

Basicly it's why you should install those softwares directly from Synaptic as a user.

Here we don't want to make those huge software available to the mass. Some people are already working on that, by providing package not only for Debian, Ubuntu, but also Mandriva, Fedora, etc.

The idea here is to be able to build some little applications. Mainly because developers of those little applications are not able to provide deb package, rpm, or it's not popular enough to have a package maintainer for each distribution. So what they do is just throw their sources to people. It's the easiest way to distribute their software for everyone.

And even if they know how to package their soft, maybe they don't have time. They are busy checking their bugzilla and programming new feature. Developers don't want to mess with package management and stuff like that. This is the job of the packagers.

Anyway; it's a problem. And there's two way to fix this. Either we provide a tool for developers to make their software installable everywhere easily (think of autopackage, Install Jammer, etc.)

Or we build a tool for users to compile softwares from sources.

I think it's a wonderful idea to try this solution. It must not be the best. I don't think we have time enough today to read the READMEs everytime we want an application anyway.

---

### Post by Ramses de Norre on 2007-06-26
> **leibowitz said:**
> **Ramses de Norre **:
There's many case where you have to throw some particular option to the configure. Look at MPlayer for example, it's a mess to compile.

Basicly it's why you should install those softwares directly from Synaptic as a user.

Here we don't want to make those huge software available to the mass. Some people are already working on that, by providing package not only for Debian, Ubuntu, but also Mandriva, Fedora, etc.

The idea here is to be able to build some little applications. Mainly because developers of those little applications are not able to provide deb package, rpm, or it's not popular enough to have a package maintainer for each distribution. So what they do is just throw their sources to people. It's the easiest way to distribute their software for everyone.

And even if they know how to package their soft, maybe they don't have time. They are busy checking their bugzilla and programming new feature. Developers don't want to mess with package management and stuff like that. This is the job of the packagers.

Anyway; it's a problem. And there's two way to fix this. Either we provide a tool for developers to make their software installable everywhere easily (think of autopackage, Install Jammer, etc.)

Or we build a tool for users to compile softwares from sources.

I think it's a wonderful idea to try this solution. It must not be the best. I don't think we have time enough today to read the READMEs everytime we want an application anyway.

I agree it's a nice idea, but I doubt it's possible... It will be a half tool which will be able to build _some_ software from source, not a tool people can trust on if they need to compile from source. If you build software in this manner you can end up with 20 programs to build from source and people should try all those until one works.
I'm not saying you guys are doing a bad job, I'm saying that you need to be critical on what you're trying to achieve and realize that this tool could rather cause confusion than really help people out ("X told me to use that tool but it wont work, and this other guy gave me a program but it throws an exception on me...").

Compiling software is -in my eyes- a difficult action which isn't simply automated and like I said, if it were it would have been done ages ago.

---

### Post by abhijeetmaharana on 2007-06-26
> **leibowitz said:**
> Look what I just found in the debian maintainer guide.


I am not quite sure. I ran it against the pidgin source and it reported several packages as "Package 'X' is not installed and no info is available". Like libvorbis-dev. Is it required by pidgin? Could you take a look and provide some more info/explanation?

---

### Post by abhijeetmaharana on 2007-06-26
> **Ramses de Norre said:**
> With all due respect, I doubt this will become a success... 

Let us put in our best. The outcome - success or failure - depends on a lot of other factors such as inputs we get from all quarters and how they can be implemented and such... Our aim will be to make the program as robust as we can make it. But one step at a time. As leibowitz mentioned, let us tackle the easy things first. Like small tarballs which install fine but are a pain because of the unzip-configure-make cycle. We can add features along the way. Sure, I don't have answers to the difficulties you have posted above. But I guess things will be clearer as we move forward and more people join the effort. And your inputs will definitely make us think harder or clear up a few doubts.

---

### Post by abhijeetmaharana on 2007-06-26
[COLOR="Blue"]Update for June 27: I have updated the first post in this thread.[/COLOR]

---

### Post by elst on 2007-06-26
FWIW, the idea of a structured system for source compiles has been implemented by several projects, so I guess that it must be viable, although it may not be easy. FreeBSD (ports) and Gentoo (portage) are fairly well known. It might be interesting to look at the mechanics of [MacPorts]("http://www.macports.org/") too, as an example of trying to add the functionality on to an existing system without breaking things.

Python could be a good language for this project - it's easy to work with and certainly included in every Ubuntu, Fedora and Red Hat system for various graphical and CLI tools. I *think* that Python is now actually either recommended or required for a distribution to be LSB-compliant.

---

### Post by leibowitz on 2007-06-26
> **abhijeetmaharana said:**
> 
[LIST]
[*]I tried auto-apt first since it appeared to be most appealing. However, it did some things I had not expected. For example, pidgin's ./configure reported several packages/files to be missing but continued whereas auto-apt went on to install those. Like selinux-policy-default. I think those packages were not essential for the task to continue. Could someone verify this and post how we can keep auto-apt from installing such packages? It also segfaulted many times. Those who want to have a first-hand look at what happened can watch this video (.ogg / ~16 MB): [http://rapidshare.com/files/39321234/auto-apt_errors.ogg](http://rapidshare.com/files/39321234/auto-apt_errors.ogg)

Although auto-apt has options like "Automatic yes to prompt", "quiet" and "Disable X inferface", I have reservations. It seems enticing but unless we iron out the above, I think we should explore other options. [COLOR="Red"]Anyone investigating further on auto-apt?[/COLOR]
[/LIST]


I will give it a try. I think the best test cases are the one that doesn't work. Where you have package missing. That's where we have to do most of the work. So I will definitely check this.

> 
[LIST]
[*] Will it be harmful to assume now that the source packages use autoconf? Later on, we can identify the source package type (currently we don't know how) and use an appropriate module to handle the installation.
[/LIST]

It's ok to work on autoconf software first. I think it could handles most of the free software out there. Then maybe we will try to handle cmake, qmake, etc.

But configure/make/make install is fine to start with.

---

### Post by leibowitz on 2007-06-26
auto-apt seems to fail on everything. It doesn't install anything, and just want to install selinux-policy everytime.

I wanted to see what's in the source code. It seems that auto-apt is a Bash script, and auto-apt-installer a Perl Script. I will look into this later.


Anyway, I read some old articles about your idea to build software from source and apparently the best way to do this is by using pkgsrc from BSD.

Linux is already supported by pkgsrc, we would need to port the auto-install stuff to apt and it should work. I'm really interested in this. I'm going to read the pkgsrc documentation and try to understand more stuff.

pkgsrc documentation:
[http://www.netbsd.org/docs/pkgsrc/introduction.html](http://www.netbsd.org/docs/pkgsrc/introduction.html)

---

### Post by pingpongboss on 2007-06-26
gl guys. This sounds really promising.

---

### Post by leibowitz on 2007-06-26
pingpongboss: Not really.



I'm looking at auto-apt source code right now. What a mess.

First it's ******* old. Then it loads a library auto-apt.so which scan system call and it's why it is trying to install everything. I read of this technique before, and I don't think it's the best. I know some tools do the same trick to know what files are installed while using make; so you can uninstall them later.

But that's not the point. I think auto-apt is flawed and must be redone, or cleared. It's horrible as it is, unmaintained and ... not functionning.

Edit: here is the source, if anyone is interested
[http://ftp.debian.org/debian/pool/main/a/auto-apt/auto-apt_0.3.21.tar.gz](http://ftp.debian.org/debian/pool/main/a/auto-apt/auto-apt_0.3.21.tar.gz)

And the official project page:
[http://alioth.debian.org/projects/auto-apt](http://alioth.debian.org/projects/auto-apt)

---

### Post by leibowitz on 2007-06-27
Here I compiled a small Bash script that checks a source file and detect the typical "#include<file.h>" strings.

From that file, it checks if it finds it on packages (dpkg -S file.h) and try to detect which is the one.

If more than one package results from the filtering, then it will ask the user for a confirmation.

Finally all required package are printed on the output.


Documentation: 
If no arguments are passed, it will scan every .c and .h file in the current directory

Otherwise it will scan every file passed as argument (no limit)


If you have any trouble with this script please attach the software name that you tried to "check", and what source file if any so I can debug it.

Here is a screencast done in the src directory of gnome-video-arcade-2.0:
[http://boby.joe.free.fr/dev/getincludes.ogg](http://boby.joe.free.fr/dev/getincludes.ogg)


Attachement Updated 8:23 am GMT

---

### Post by abhijeetmaharana on 2007-06-27
Looks good. Ill try it on pidgin tonight. And lets test it on some hard-to-install source packages and see how it fares. Ill test it against some more source packages.
In the meantime, I suggest that we set up bare bones virtual machines at our ends for testing. My edgy box has got SELinux all over the place.

---

### Post by leibowitz on 2007-06-27
I'm thinking now why I made this script. I mean, it's useless as it is. Only checking _installed_ packages.

That means we have two choices. First we use apt-file to find required package (not installed). Or we use auto-apt.

Both needs to be installed first, and both need a cache file (call auto-apt update or apt-file update)

It seems apt-file is really slow at that task.

```

time apt-file search fcntl.h
real    0m5.169s
user    0m4.784s
sys     0m0.247s

```
```

time auto-apt search fcntl.h
real    0m0.840s
user    0m0.698s
sys     0m0.088s

```

So let's go for auto-apt. It's even more accurate on the search results, so it's perfect for this task. I don't like auto-apt, but it's seems to be a good choice here.

I hope to have another script soon that works with auto-apt search


Update: with further investigation, auto-apt does not return any package for some files. That is not the case with apt-file, so go for apt-file ... Damn!

---

### Post by leibowitz on 2007-06-27
Done!

I created a bash script and two small perl script. It scans for every source file you pass in arguments to the Bash script for package #include strings, and then go to apt-file search to find the related package.

It returns all the packages found.

How to use it:
Unpack the archive, go to the findpkg directory and type this:
```
./aptfile-scan-include.sh /some/path/to/src/*.[ch]
```

If you want to see activity while it search for package, then change the verbose=0 to verbose=1 line at the beginning of the Bash script.

By now it's really slow because of apt-file search. But it's no time for optimization. I just want it to work right now. Tell me if it doesn't and provide the source package you tried to scan. Otherwise I can't debug it.


Here is a typical output:
> ./aptfile-scan-include.sh ~/Desktop/auto-apt-0.3.21/*.c
gcc-4.0
libc6-dev

Yes, I tried this in the auto-apt source tree. Cool heh?

Here is a verbose output:
> ./aptfile-scan-include.sh ~/Desktop/auto-apt-0.3.21/pkgcdb/*.[ch]
------------------------------
Searching for file: assert.h
Packages found:
1  libc6-dev
------------------------------
Searching for file: ctype.h
Packages found:
1  libc6-dev
------------------------------
Searching for file: errno.h
Packages found:
1  libc6-dev
------------------------------
Searching for file: fcntl.h
Packages found:
1  libc6-dev
------------------------------
Searching for file: limits.h
Packages found:
1  gcc-4.0
------------------------------
Searching for file: stdio.h
Packages found:
1  libc6-dev
------------------------------
Searching for file: stdlib.h
Packages found:
1  libc6-dev
------------------------------
Searching for file: string.h
Packages found:
1  libc6-dev
------------------------------
Searching for file: sys/file.h
Packages found:
1  libc6-dev
------------------------------
Searching for file: sys/stat.h
Packages found:
1  libc6-dev
------------------------------
Searching for file: sys/time.h
Packages found:
1  libc6-dev
------------------------------
Searching for file: sys/types.h
Packages found:
1  libc6-dev
------------------------------
Searching for file: time.h
Packages found:
1  libc6-dev
------------------------------
Searching for file: unistd.h
Packages found:
1  libc6-dev

#################

2 installed packages required:
gcc-4.0
libc6-dev

Edit: and I forget to mention that in the verbose mode it will ask the user if more than one package is found for an include file.
> Searching for file: gconf/gconf-client.h
Packages found:
1  libgconf2-dev
2  libgconf-dev
Please choose the package that provide gconf/gconf-client.h [1-2]: 1
Selected: libgconf2-dev

In non-verbose mode it will throw each package in this format as output:
package1|package2

Here is an example in non-verbose:
> ./aptfile-scan-include.sh ../src/*.[ch]
gcc-4.0
libc6-dev
libgconf2-dev|libgconf-dev
libglade0-dev|libglade2-dev
libglib1.2-dev|libglib2.0-dev
libglib2.0-dev
libgtk1.2-dev|libgtk2.0-dev|libgtk+2.0-directfb-dev

---

### Post by abhijeetmaharana on 2007-06-27
> **leibowitz said:**
> Done!

Its so nice to hear that!!

I am having some trouble running the script. Was trying to run it on my favourite - pidgin. But that doesn't seem to be the issue here. I am missing something obvious. What?

```

$ ./aptfile-scan-include.sh *.[ch]

aptfile-scan-include.sh: 12: declare: not found
aptfile-scan-include.sh: 14: function: not found
aptfile-scan-include.sh  version:
-e
Returns the list of dependencies package needed to build a software
-e Usage:  aptfile-scan-include.sh  [files..]

aptfile-scan-include.sh: 24: function: not found
dpkg: conflicting actions -p (--print-avail) and -S (--search)

...and some more

```

---

### Post by Kelimion on 2007-06-27
I'll be trying both scripts on various packages this week. As for VM, I have a nice pristine Gutsy Tribe 1 image that I can roll back after every try.

You'll find my answers on a postcard* :)

edit:

With regards to Leibowitz' suggestion for dpkg, I found this sitting around in the repositories:

dlocate
---
fast alternative to dpkg -L and dpkg -S
Uses GNU locate to greatly speed up finding out which package a file
belongs to (i.e. a very fast dpkg -S). Many other uses, including
options to view all files in a package, calculate disk space used, view
and check md5sums, list man pages, etc.






* or in this thread, rather.

---

### Post by leibowitz on 2007-06-27
> **abhijeetmaharana said:**
> 
```

$ ./aptfile-scan-include.sh *.[ch]

aptfile-scan-include.sh: 12: declare: not found
aptfile-scan-include.sh: 14: function: not found

```


Can you post the output of those two commands? 
> bash --version
file `type -p bash`

You may be using Edgy or Feisty, and I know it uses dash to replace bash. Which is not totally compatible. My bad I should have writed "#!/bin/bash" at the top of the script, and not #!/bin/sh

---

### Post by abhijeetmaharana on 2007-06-27
```

abhijeet@ApplicationServer:~$ bash -version
GNU bash, version 3.1.17(1)-release (i486-pc-linux-gnu)
Copyright (C) 2005 Free Software Foundation, Inc.
abhijeet@ApplicationServer:~$ file `type -p bash`
/bin/bash: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), for GNU/Linux 2.6.0, stripped
abhijeet@ApplicationServer:~$


```

Ok it works with !/bin/bash
```

./aptfile-scan-include.sh ~/Documents/SourceInstaller/SourceInstaller0.1beta2/pidgin-2.0.2/pidgin/*.[ch]
apcalc-dev|asterisk-dev|bash-builtins|bitchx-dev|blitz++|brickos|csound|facturalux-dev|gaim-dev|gandalf-dev|gap-dev|ggobi|hybrid-dev|inn2-dev|ion2-dev|ion3-dev|irssi-dev|kdemultimedia-dev|klic|kolf-dev|kvirc2-dev|ladcca-dev|libace-dev|libafterimage-dev|liballegro4.2-dev|libalps-light1-dev|libbeidlibopensc2-dev|libcln-dev|libcommoncpp2-dev|libconfig0-dev|libcrypto++-dev|libcwd-dev|libdar-dev|libdebian-installer4-dev|libdevil-dev|libdspam7-dev|libgammu-dev|libgdamm1.3-dev|libgoogle-perftools-dev|libgsm1-dev|libgtkglextmm1-dev|libhttrack-dev|libkpathsea-dev|liblash-dev|liblinphone1-dev|liblog4cpp4-dev|liblog4cxx9-dev|libmimelib1-dev|libmimetic-dev|libnewmat10-dev|libodbc++-dev|libode0-dev|libomnievents-dev|libopenais-dev|libopenalpp-cvs-dev|libosp-dev|libostyle-dev|libparrot-dev|libpt-dev|librudiments-dev|libsp1-dev|libsylpheed-claws-dev|libsylpheed-claws-gtk2-dev|libupnp-dev|libuser1-dev|libvarconf-dev|libwnn-dev|llvm|mozilla-dev|nessus-dev|nickle|octave2.1-headers|octave2.9-headers|openoffice.org-dev|oskit|paintlib-dev|pccts|pciutils-dev|pfe-dev|php4-dev|php5-dev|postfix-dev|ppxp-dev|qemacs|qemacs-nox|sparsehash|vdr-dev|wireshark-dev|wx2.4-headers|wx2.6-headers|zinc-compiler
gcc-4.1
libc6-dev
libdirectfb-dev|libgpewidget-dev|wine-dev
libgdk-pixbuf-dev|libgtk2.0-dev|libgtk+2.0-directfb-dev
libglib1.2-dev|libglib2.0-dev
libglib2.0-dev
libgtk1.2-dev|libgtk2.0-dev
libgtk1.2-dev|libgtk2.0-dev|libgtk+2.0-directfb-dev
libgtk2.0-dev
libgtk2.0-dev|libgtk+2.0-directfb-dev
libgtk+2.0-directfb-dev
libice-dev
libpango1.0-dev
libsm-dev
wine-dev
x11proto-core-dev

real    5m35.283s
user    5m15.764s
sys     0m16.553s

```

I will run it on the subfolders of pidgin and see if *all* dependencies including libxml2 are detected.

---

### Post by leibowitz on 2007-06-27
```
apcalc-dev|asterisk-dev|bash-builtins|bitchx-dev|blitz++|brickos|csound|facturalux-dev|gaim-dev|gandalf-dev|gap-dev|ggobi|hybrid-dev|inn2-dev|ion2-dev|ion3-dev|irssi-dev|kdemultimedia-dev|klic|kolf-dev|kvirc2-dev|ladcca-dev|libace-dev|libafterimage-dev|liballegro4.2-dev|libalps-light1-dev|libbeidlibopensc2-dev|libcln-dev|libcommoncpp2-dev|libconfig0-dev|libcrypto++-dev|libcwd-dev|libdar-dev|libdebian-installer4-dev|libdevil-dev|libdspam7-dev|libgammu-dev|libgdamm1.3-dev|libgoogle-perftools-dev|libgsm1-dev|libgtkglextmm1-dev|libhttrack-dev|libkpathsea-dev|liblash-dev|liblinphone1-dev|liblog4cpp4-dev|liblog4cxx9-dev|libmimelib1-dev|libmimetic-dev|libnewmat10-dev|libodbc++-dev|libode0-dev|libomnievents-dev|libopenais-dev|libopenalpp-cvs-dev|libosp-dev|libostyle-dev|libparrot-dev|libpt-dev|librudiments-dev|libsp1-dev|libsylpheed-claws-dev|libsylpheed-claws-gtk2-dev|libupnp-dev|libuser1-dev|libvarconf-dev|libwnn-dev|llvm|mozilla-dev|nessus-dev|nickle|octave2.1-headers|octave2.9-headers|openoffice.org-dev|oskit|paintlib-dev|pccts|pciutils-dev|pfe-dev|php4-dev|php5-dev|postfix-dev|ppxp-dev|qemacs|qemacs-nox|sparsehash|vdr-dev|wireshark-dev|wx2.4-headers|wx2.6-headers|zinc-compiler
```

Not bad :-)

The hardest part is trying to find which package is the good one where there are multiple possibilities. In verbose mode it will ask the user, but here .. You won't be able to see the whole list.

Maybe we could check installed packages first, to eliminate a lot of not-related packages. It would be ok if you have the good one already installed, but what if not.

Here's a little example:

```
apt-file search lualib.h
libcegui-mk2-dev: usr/include/CEGUI/lualib.h
liblualib40-dev: usr/include/lua40/lualib.h
liblualib50-dev: usr/include/lua50/lualib.h

```

The source code only contains #include <lualib.h>. Which package does provide this file ? Go figure.

The only way I know is to find the arguments passed to the build command. But that's not possible. It could be variables in the Makefile, it could be substitution in configure.ac, impossible to find out.

I think we need to hack on it a little bit. Like I already did with gcc. When you look for stdio.h file for example, it will throw a lot of files.

```
apt-file search stdio.h
avr-libc: usr/avr/include/stdio.h
avr-libc: usr/share/doc/avr-libc/avr-libc-user-manual/group__avr__stdio.html.gz
cmix: usr/share/cmix/shadow/stdio.h
dietlibc-dev: usr/include/diet/stdio.h
ecos: usr/src/ecos/packages/isoinfra/v2_0/include/stdio.h
ecos: usr/src/ecos/packages/language/c/libc/stdio/v2_0/include/stdio.h
elks-libc: usr/lib/bcc/include/stdio.h
gcc-snapshot: usr/lib/gcc-snapshot/lib/gcc/i486-linux-gnu/4.1.0/include/ssp/stdio.h
ivtools-dev: usr/include/ivstd/stdio.h
lam4-dev: usr/include/lam/tstdio.h
libace-dev: usr/include/ace/OS_NS_stdio.h
libace-dev: usr/include/ace/os_include/os_stdio.h
libbind-dev: usr/include/isc/stdio.h
libboost-iostreams-dev: usr/include/boost/iostreams/filter/stdio.hpp
libc6-dev: usr/include/bits/stdio.h
libc6-dev: usr/include/stdio.h
libc6-dev-amd64: usr/include/x86_64-linux-gnu/bits/stdio.h
libc6-dev-amd64: usr/include/x86_64-linux-gnu/stdio.h
libfcgi-dev: usr/include/fcgi_stdio.h
libglib2.0-dev: usr/include/glib-2.0/glib/gstdio.h
libgsf-1-dev: usr/include/libgsf-1/gsf/gsf-infile-stdio.h
libgsf-1-dev: usr/include/libgsf-1/gsf/gsf-input-stdio.h
libgsf-1-dev: usr/include/libgsf-1/gsf/gsf-outfile-stdio.h
libgsf-1-dev: usr/include/libgsf-1/gsf/gsf-output-stdio.h
libhdf4g-dev: usr/include/hdf/mstdio.h
libhdf5-lam-dev: usr/include/H5FDstdio.h
libhdf5-mpich-dev: usr/include/H5FDstdio.h
libhdf5-serial-dev: usr/include/H5FDstdio.h
libicu34-dev: usr/include/unicode/ustdio.h
libklibc-dev: usr/lib/klibc/include/stdio.h
libstdc++5-3.3-doc: usr/share/doc/gcc-3.3-base/libstdc++/html_user/cstdio.html
libstdc++6-doc: usr/share/doc/gcc-3.4-base/libstdc++/html_user/cstdio.html
libstlport4.6-dev: usr/include/stlport/stdio.h
libstlport5-dev: usr/include/stlport/stdio.h
libuclibc-dev: usr/i386-uclibc-linux/include/bits/stdio.h
libuclibc-dev: usr/i386-uclibc-linux/include/bits/uClibc_stdio.h
libuclibc-dev: usr/i386-uclibc-linux/include/stdio.h
manpages-posix-dev: usr/share/man/man7/stdio.h.7posix.gz
mingw32-runtime: usr/i586-mingw32msvc/include/stdio.h
mosml-doc: usr/share/doc/mosml-doc/mosmllib/Nonstdio.html
newlib-m68hc1x: usr/m68hc11/include/stdio.h
newlib-m68hc1x: usr/m68hc11/include/sys/stdio.h
oskit: usr/include/oskit/c/stdio.h
oskit: usr/include/oskit/freebsd/stdio.h
pccts: usr/include/pccts/pccts_stdio.h
perl: usr/lib/perl/5.8.7/CORE/nostdio.h
pike7.2: usr/lib/pike/7.2.580/lib/include/stdio.h
pike7.4-core: usr/lib/pike/7.4.341/lib/include/stdio.h
pike7.6-core: usr/lib/pike/7.6.61/lib/include/stdio.h
pnetc: usr/share/cscc/include/stdio.h
pocketpc-gcc: usr/arm-wince-pe/include/stdio.h
pocketpc-gcc: usr/arm-wince-pe/include/sys/stdio.h
prc-tools-arm: usr/arm-palmos/include/stdio.h
prc-tools-m68k: usr/m68k-palmos/include/stdio.h
sdcc-libraries: usr/share/sdcc/include/pic16/stdio.h
sdcc-libraries: usr/share/sdcc/include/stdio.h
sfio-dev: usr/include/sfio/stdio.h
splint: usr/share/splint/lib/stdio.h
tendra: usr/lib/TenDRA/lib/include/ansi.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/cpp.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/iso.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/posix.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/posix1.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/posix2.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/svid3.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/unix95.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/xpg3.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/xpg4.api/stdio.h
wine-dev: usr/include/wine/msvcrt/stdio.h
yorick: usr/lib/yorick/1.5/include/pstdio.h
```

So what I do, basicly is to filter the result first by name. 

```
grep -E "stdio.h$"
``` 
This will eliminate files that  do not end with stdio.h, like this one:
mosml-doc: usr/share/doc/mosml-doc/mosmllib/Nonstdio.html

Then add a "/" to eliminate those:
libuclibc-dev: usr/i386-uclibc-linux/include/bits/uClibc_stdio.h

```
apt-file search stdio.h | grep -E "/stdio.h$"
avr-libc: usr/avr/include/stdio.h
cmix: usr/share/cmix/shadow/stdio.h
dietlibc-dev: usr/include/diet/stdio.h
ecos: usr/src/ecos/packages/isoinfra/v2_0/include/stdio.h
ecos: usr/src/ecos/packages/language/c/libc/stdio/v2_0/include/stdio.h
elks-libc: usr/lib/bcc/include/stdio.h
gcc-snapshot: usr/lib/gcc-snapshot/lib/gcc/i486-linux-gnu/4.1.0/include/ssp/stdio.h
ivtools-dev: usr/include/ivstd/stdio.h
libbind-dev: usr/include/isc/stdio.h
libc6-dev: usr/include/bits/stdio.h
libc6-dev: usr/include/stdio.h
libc6-dev-amd64: usr/include/x86_64-linux-gnu/bits/stdio.h
libc6-dev-amd64: usr/include/x86_64-linux-gnu/stdio.h
libklibc-dev: usr/lib/klibc/include/stdio.h
libstlport4.6-dev: usr/include/stlport/stdio.h
libstlport5-dev: usr/include/stlport/stdio.h
libuclibc-dev: usr/i386-uclibc-linux/include/bits/stdio.h
libuclibc-dev: usr/i386-uclibc-linux/include/stdio.h
mingw32-runtime: usr/i586-mingw32msvc/include/stdio.h
newlib-m68hc1x: usr/m68hc11/include/stdio.h
newlib-m68hc1x: usr/m68hc11/include/sys/stdio.h
oskit: usr/include/oskit/c/stdio.h
oskit: usr/include/oskit/freebsd/stdio.h
pike7.2: usr/lib/pike/7.2.580/lib/include/stdio.h
pike7.4-core: usr/lib/pike/7.4.341/lib/include/stdio.h
pike7.6-core: usr/lib/pike/7.6.61/lib/include/stdio.h
pnetc: usr/share/cscc/include/stdio.h
pocketpc-gcc: usr/arm-wince-pe/include/stdio.h
pocketpc-gcc: usr/arm-wince-pe/include/sys/stdio.h
prc-tools-arm: usr/arm-palmos/include/stdio.h
prc-tools-m68k: usr/m68k-palmos/include/stdio.h
sdcc-libraries: usr/share/sdcc/include/pic16/stdio.h
sdcc-libraries: usr/share/sdcc/include/stdio.h
sfio-dev: usr/include/sfio/stdio.h
splint: usr/share/splint/lib/stdio.h
tendra: usr/lib/TenDRA/lib/include/ansi.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/cpp.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/iso.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/posix.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/posix1.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/posix2.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/svid3.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/unix95.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/xpg3.api/stdio.h
tendra: usr/lib/TenDRA/lib/include/xpg4.api/stdio.h
wine-dev: usr/include/wine/msvcrt/stdio.h
```

Not better at all! But at least they are all stdio.h files. Now we will just list packages. I know we lost a pertinent information here (the file path), so I will first filter a little more before filtering packages only.

First, I try to find the file in the gcc include directory. The Gcc include directory is found by checking the gcc binary, then the files provided by this package, then extract the path with one of the perl scripts: getheaderpath.pl

From the Bash script, first filtering try:
```
filtered_list=`echo "$include_list" | grep -E "${gccheaderpath}${1}\$" | $filter_name | $filter_sort`
```

If nothing is left after this filtering, then try to search in usr/include/file.h, 
then usr/include.*/file.h, 
then include/file.h, 
then include.*/file.h, and if nothing is left by all those filters, then just get the whole list.


Example:
```
apt-file search stdio.h | grep -E "usr/include/stdio.h$"
libc6-dev: usr/include/stdio.h
```

Now we remove the files path, just keeping the package name.

```
apt-file search stdio.h | grep -E "usr/include/stdio.h$" | cut -d: -f1
```

But if there is multiple times the same package name, we need to filter this out too. 

Example:
```
apt-file search stdio.h | grep -E "/stdio.h$" | cut -d: -f1
avr-libc
cmix
dietlibc-dev
ecos
ecos
elks-libc
gcc-snapshot
ivtools-dev
libbind-dev
libc6-dev
libc6-dev
libc6-dev-amd64
libc6-dev-amd64
libklibc-dev
libstlport4.6-dev
libstlport5-dev
libuclibc-dev
libuclibc-dev
mingw32-runtime
newlib-m68hc1x
newlib-m68hc1x
oskit
oskit
pike7.2
pike7.4-core
pike7.6-core
pnetc
pocketpc-gcc
pocketpc-gcc
prc-tools-arm
prc-tools-m68k
sdcc-libraries
sdcc-libraries
sfio-dev
splint
tendra
tendra
tendra
tendra
tendra
tendra
tendra
tendra
tendra
tendra
wine-dev
```

So we add a "sort -u" argument.
```
apt-file search stdio.h | grep -E "/stdio.h$" | cut -d: -f1 | sort -u
avr-libc
cmix
dietlibc-dev
ecos
elks-libc
gcc-snapshot
ivtools-dev
libbind-dev
libc6-dev
libc6-dev-amd64
libklibc-dev
libstlport4.6-dev
libstlport5-dev
libuclibc-dev
mingw32-runtime
newlib-m68hc1x
oskit
pike7.2
pike7.4-core
pike7.6-core
pnetc
pocketpc-gcc
prc-tools-arm
prc-tools-m68k
sdcc-libraries
sfio-dev
splint
tendra
wine-dev
```

That's how it works so far. I have no idea how to improve without adding too much complexity.

Note: in the bash script it caches the apt-file search results. It just call it once for each header file. I just wanted to point this out, because it's not related to the execution time. Here is just a documentation explaining the bash script so anyone, even without any programming experience can provide some ideas. You can come with any other way of achieving the same results. Just think about it and I will comment or even try to implement your idea.

---

### Post by leibowitz on 2007-06-27
In the meantime, I just edited a little bit the Bash script (the first line to /bin/bash for example).

Now when it does find multiple package providing an header file it will just ignore the packages. I think it's not crazy, because the configure script will probably check this (if the developer know what he does)

I think we can get something from the package list, some hints on what package need to be installed. Or check if at least one of those multiple package is already installed. If it's the case then it should work in most of the cases.

I feel like I need to think about all this a little bit before going further.

Anyway here is the updated bash script (not many difference)

---

### Post by abhijeetmaharana on 2007-06-29
The script looks good. We need to figure out a way to decide the one which is to be installed when there are multiple options.

I was wondering....do we have to actually scan the headers? I mean, wasn't it already done when the configure scripts were generated. The configure script has the dependencies with the versions. Can't we use that? How well-defined is the structure of the configure script? 

I had a look at the configure scripts for pidgin, yakuake and xosd. Yakuake and xosd's look similar while pidgin's configure script looks different although all three of them say "Generated by GNU Autoconf 2.59". Any ideas in this direction? Just a thought. We could always resume work on leibowitz's scripts if this doesn't make sense.

---

### Post by leibowitz on 2007-06-29
> **abhijeetmaharana said:**
> We need to figure out a way to decide the one which is to be installed when there are multiple options.

Not necessarily. If we can that's good, but we don't have to. By the way it's impossible to know for sure. So it may be stupid to select one or the other. Unless we ask the user, there's really no way to know what package is needed.

> **abhijeetmaharana said:**
> 
I was wondering....do we have to actually scan the headers? I mean, wasn't it already done when the configure scripts were generated. The configure script has the dependencies with the versions. Can't we use that? How well-defined is the structure of the configure script? 

The bash script is a pre-check, it has to be done before launching the configure script. The aim of this script is in fact to reduce the chance of failure during configure.

> **abhijeetmaharana said:**
> I had a look at the configure scripts for pidgin, yakuake and xosd. Yakuake and xosd's look similar while pidgin's configure script looks different although all three of them say "Generated by GNU Autoconf 2.59". 

The configure script can be done by the developer, or be generated by autoconf. If it is automated, then you need to check configure.ac or configure.in, which is the file created by the developer (or by autoscan). 

This fille will contain most check for headers file, or lib function, or even more. It's impossible to scan for everything, and check what is needed by the software. And sometimes the developer didn't put every check, so the configure script will be fine, but it won't build the software unless you install the right package, which can be really hard to find out.


Scanning source file for headers strings is, in my opinion, a good way to check what is needed before launching the configure/make/make install procedure.

The way auto-apt did his check was really different though. And I don't want to mess with this kind of thing.

---

### Post by abhijeetmaharana on 2007-06-29
Yeah. I just went through the autoconf manual at [http://www.gnu.org/software/autoconf/manual/](http://www.gnu.org/software/autoconf/manual/). It seems that the format of configure depends largely on the developer and may be different. However, are there any "broad" widely used formats? Say patterns. If there are any, we could parse the configure script appropriately and get hold of the dependencies. Make sure they are installed or install them and then run the script itself. Of course, scanning the source files is a much more reliable way but this could speed up the process. Is it worth the trouble?

---

### Post by leibowitz on 2007-06-29
What do you mean by trouble ? To scan the configure script ? 

Autoconf build a configure script from an input file (configure.ac or configure.in)

In this file the developer can throw some Macro to test if say a function, a library, or a program is available on the system.

AC_CHECK_LIB for example will check a library.
AC_CHECK_FUNCS for functions, AC_CHECK_HEADERS for headers file, etc.

There are many macro, and some can be customised.

Also there are some particular way of doing other checks, like pkg-config.

PKG_CHECK_MODULES is often used by gnome application. And this can be very tricky to parse, because it is not always writed in a simple manner, but also can be set based on variable values.

A common example:
> GNOME_MODULES="libgnomeui-2.0 >= 2.0.0"
PKG_CHECK_MODULES(GNOME, $GNOME_MODULES)

And variables name is a developer choice.

Like I said, it's impossible to get more information from the package. Indeed the autotool are fine and works good for this purpose. They are well documented. Sometimes it's true they are not very well used, but that's not our fault anyway.

The best way to give your software better result is to provide a maximum of different check to be done. And the source parsing is just a way of doing it. Configure is another one. And there are still room for improvement in both.

For example we can check for header file in installed package first, then extend to the non-installed only if we didn't find the header. This only will reduce the time spend on the research.

---

### Post by abhijeetmaharana on 2007-06-29
> **leibowitz said:**
> What do you mean by trouble ? To scan the configure script ? 


I was curious and wrote a little program to scan some ./configure files and report the dependencies. It reported the dependencies for pidgin, Gnome WOTD applet, gtk-recordmydesktop and failed for the remaining ones such as yakuake and xosd. Out of 10 configure files, it failed for 7. These 3 files were similar and it seems that some of the files for which it failed seem similar as well and require some different parsing. So I was wondering if there are other similar "structures" of the configure script that we could look for.

Even for the 3 scripts for which dependencies were reported, the strings were what the developer had supplied as you have pointed out above. And it may turn out to be difficult to find the package names from these strings if they are not uniform.

As an example, for pidgin and gtk-recordmydesktop, one of the dependencies reported was "gtk+-2.0". 
[LIST=1]
[*]Can we determine the package name from such a string? Or maybe this is the package name itself?
[*]Is it necessary that this string will remain the same if it is reported for another package?
[/LIST]

> 
The best way to give your software better result is to provide a maximum of different check to be done. And the source parsing is just a way of doing it. Configure is another one. And there are still room for improvement in both. For example we can check for header file in installed package first, then extend to the non-installed only if we didn't find the header. This only will reduce the time spend on the research.

Yeah. I was thinking on something like this
```

scan configure script assuming a script in pattern A
If dependency list is empty, 
	use pattern B and so on
If dependency list is still empty, 
	scan source files
display dependencies to user and let him/her validate

```

The last step ensures that random strings like "\$" etc. get caught by visual inspection.
Scanning the configure script is fast and if that yields the dependencies, we may be able to avoid the time costly source scan (although it is the most reliable). 

The question is: Does it make sense if we collect a large number of configure scripts and try to figure out the common patterns, if there are any and if they are fairly "common"? One fancy string by a developer can break stuff.

I have attached the program and the config scripts. Some output strings have $.... in them. A variable substitution routine should take care of that.

---

### Post by leibowitz on 2007-06-30
> As an example, for pidgin and gtk-recordmydesktop, one of the dependencies reported was "gtk+-2.0".

   1. Can we determine the package name from such a string? Or maybe this is the package name itself?
   2. Is it necessary that this string will remain the same if it is reported for another package?


This string is used by pkg-config, if it doesn't find it then it will warn you. Basicly what it does is to execute this command and if it returns zero then it's present, otherwise it's not.
```
pkg-config gtk+-2.0 --exists && echo $?
```

We can try to execute this instead:
```
pkg-config gtk+-2.0 --cflags-only-I
```

This will return the different path to the include directories.

```
-I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
```

Then we can scan which package provide those path. 

**apt-file search /usr/include/pango-1.0** or  **dpkg -S /usr/include/pango-1.0**. This will return **libpango1.0-dev**

That's not interesting, is it ?

By the way I can't find how to start your Java application. I'm no java developer, I must have missed something.

```
java DependencyScanner
Exception in thread "main" java.lang.UnsupportedClassVersionError: Bad version number in .class file

java -showversion
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

```

---

### Post by abhijeetmaharana on 2007-06-30
> **leibowitz said:**
> 
We can try to execute this instead:
```
pkg-config gtk+-2.0 --cflags-only-I
```

This will return the different path to the include directories.
Then we can scan which package provide those path. 

I guess we don't need to do that. Because if pkg-config returns the path, it means the library is installed. And it should be installed with its set of dependencies (maybe libpango is in the list of dependencies of gtk+). 

> 
By the way I can't find how to start your Java application. I'm no java developer, I must have missed something.


I have compiled the program with Java 1.6. It won't run with an older version. The source is included in the archive. You just need to recompile it on your system with Java 1.5. 

```

javac DependencyScanner.java
java DependencyScanner > output1.txt

```

If you happen to have just the runtime, take a look at output.txt in the archive. Thats the redirected output from the program at my end.

---

### Post by leibowitz on 2007-06-30
> I guess we don't need to do that. Because if pkg-config returns the path, it means the library is installed. 

You are right!


Update: in fact I have all version of Java installed, but 1.5 was the default. Even recompiling the software with 1.5 didn't worked. So I update the java link with update-alternative on 1.6 and it's ok now. 

Thanks for your help

---

### Post by leibowitz on 2007-06-30
I think we may start a project page on launchpad.net. 

We already have a blueprint from Afoot, 
[http://ubuntuforums.org/showthread.php?t=482878](http://ubuntuforums.org/showthread.php?t=482878)

Maybe we should contact him to ask he is ok that we take his idea as a base.


What's your thought?

---

### Post by abhijeetmaharana on 2007-06-30
Its Afoot who started this in the first place. As I have already mentioned in the first post "It was raining outside and I was looking for something to do on a Sunday evening". The sunday would have gone by with a game of OpenArena had it not been for Afoot's thread. So if he is fine with it.....I don't have a say :-)

We need to get this dependency mess straightened. Its the major block. Once we have it sorted out, we may think beyond autoconf based stuff. (I have no idea what other mess they hold for us ;-))

I have never used launchpad before. May need a hand. 

I am working on the GUI which was scheduled for the weekend. The GUI is a cosmetic addition. It will just execute configure-make-make install and post the output in a window. Nothing more. But at least we will be able to avoid the unzipping and issuing of commands in a terminal. 

I should be able to post an update tomorrow evening.

---

### Post by Afoot on 2007-06-30
> **leibowitz said:**
> I think we may start a project page on launchpad.net. 

We already have a blueprint from Afoot, 
[http://ubuntuforums.org/showthread.php?t=482878](http://ubuntuforums.org/showthread.php?t=482878)

Maybe we should contact him to ask he is ok that we take his idea as a base.


What's your thought?
Go for it. :)

Looking forward to seeing the GUI code, it's one of the things we're gonna learn in next semester's programming class, so I might as well get a head start. ;)

---

### Post by leibowitz on 2007-06-30
I never created a project on launchpad either. Afoot you could try to post your project idea on launchpad. Basicly it's what you posted in the thread. Copy paste this on a blueprint and we are good.
[http://ubuntuforums.org/showthread.php?t=482878](http://ubuntuforums.org/showthread.php?t=482878)

---

### Post by leibowitz on 2007-06-30
I'm trying to create an alternative parser, for both configure.{ac,in} files. 

I thought it would be better to parse this file instead of the whole configure which is huge.

But then I faced so many corner case, even by hacking many hours I'm still not convinced that it would be better in the end.

I'm just sending it here as a perl script. Feel  free to test it and report what you think we can do with it. 

I didn't documented it because I think it won't be of any help at all.

Just call it with a configure.ac or configure.in file as the argument (it only parse one file).

Here's a typical output
```
 ./getconfpackage.pl ~/Desktop/libgnomedb-3.0.0/configure.in
 "gconf-2.0"
*********************
 "gtk+-2.0 >= 2.6.0 gthread-2.0" "libgda-3.0 >= 3.0.0"
*********************
 "gtk+-2.0 >= 2.10.0"
*********************
 "libgnomecanvas-2.0"
*********************
 "hildon-libs"
*********************
 "libglade-2.0"
*********************
 "gladeui-1.0 >= 3.1"
*********************
 gtksourceview-1.0
*********************
 libecal-1.2 libebook-1.2 libedataserver-1.2
*********************
```

It does variable substitution, which is cool. But I found some source package that do more by calling some m4 macros, which it can't parse at the moment.

Worse, the result are thought to be all required. But some times they are not at all. Just checking but not absolutely necessary. And it's impossible to know that. So what we do basicly is just checking everything and report what is missing, but do not force the user to install all of them because some times it's not required.

I think I will try to do another perl script based on your Java program, so we can parse the full configure with a perl script. I already saw many differences, it's not gonna be easy...

Anyway, we need to separate the GUI from the parsing. Otherwise it will be too much hassle.

---

### Post by Afoot on 2007-06-30
> **leibowitz said:**
> I never created a project on launchpad either. Afoot you could try to post your project idea on launchpad. Basicly it's what you posted in the thread. Copy paste this on a blueprint and we are good.
[http://ubuntuforums.org/showthread.php?t=482878](http://ubuntuforums.org/showthread.php?t=482878)
I'm doing that right now, but what should the project's name be? I haven't thought about it. Any ideas? Hopefully the name can be changed after registering it on Launchpad though, in which case we could temporarily name it "Graphical Installer for source archives" or something similar.

Right now this is what I've written:
Name: gisa
Display Name: GISA
Title: Graphical Installer for Source Archives

Edit:
Well, here it is:
[https://launchpad.net/gisa](https://launchpad.net/gisa)

---

### Post by leibowitz on 2007-06-30
I love the name. No need to change it later.

One thought about the Rationale/Scope and Use Cases. I don't think it will be possible to fulfill the need of an easy installer for beginners.

I think it would be great, but currently it seems impossible to do in my opinion.

What's best to target is to make it easy for advanced users to install source software.

Often you end up doing the same task again and again with all software you download as source tarball. And that task could be achieved or at least eased by something like GISA.

Mostly I think about the package needed to compile the software. Sometimes the user interaction will be needed. And that will need some basic knowledge in the user point of view.

---

### Post by thelinuxguy on 2007-06-30
Edit: Never mind. Posted in the wrong thread.

---

### Post by leibowitz on 2007-07-01
Been tweaking the last Perl script a little bit.

On 38 different configure.{ac,in} files, here are the results:

32 shows some dependencies (from PKG_CHECK_MODULES only).

1/32 show some garbage string from a mal-formated configure.in (aurora-0.9 theme engine)

1/32 report poor results (using a m4_macro defining req_ver_glib, which is not substitued by the perl script. Easily tweakable) - this is from libgda-3.0.1 by the way

1/32 report only a part of the dependencies - metacity 2.17.1 uses a variable which concatenate itself during the configure.in script.

On the last one I tried to scan the full configure script instead, but only by using the java program. Here are the results:
> Scanning dependencies for metacityConfigure...
-----------------------------------
glib-2.0 >= 2.6.0
gtk+-2.0 >= 2.6.0
$METACITY_PC_MODULES


Here is the result from configure.in scan (metacity 2.17.1)
> ### 27 opening conf-files/metacity-configure.in
  glib-2.0 >= 2.6.0
  *********************
  gtk+-2.0 >= 2.6.0
  *********************
  gtk+-2.0 >= 2.6.0
  *********************
  gtk+-2.0 >= 2.10.0 pango >= 1.2.0
  *********************


Even if it's not complete it's far from useless (it doesn't find all part of the $METACITY_PC_MODULES, check the configure.in script of this project to see how they constructed it)


The last 6 files that doesn't return any result are not using PKG_CHECK_MODULES macro. Some are using other macros (like AC_CHECK_LIB, AC_CHECK_FUNC, AC_CHECK_HEADER) which we can parse with more coding.

But somes are not using anything, like readedid for example. Here is the configure.in:
> 
dnl Process this file with autoconf to produce a configure script.
 
AC_INIT(get-edid.c)
AM_INIT_AUTOMAKE(read-edid, 1.4.1)

dnl Checks for programs

AC_PROG_CC

dnl Simple, huh?

AC_OUTPUT([Makefile])


Other example: tango-icon-theme, which use PKG_CHECK_EXISTS instead of CHECK_MODULES. It's easily parseable but return no result atm.

The big loser here is wine-configure.ac, which contains many many checks but no PKG_CHECK_*. This means no results atm. Are we targetting wine-like applications anyway.


So far so good. Though I still don't know if you are convinced. I let you check the results for yourself (Perl script + various configure.{in,ac} files)

download, extract, enter the getpkg folder and type:
```
./getconfpackage.pl conf-files/*
```

Or you can redirect the output in a file.

```
./getconfpackage.pl conf-files/* > output.log
```

That's much better to read.

You can also throw one file at a time.
```
./getconfpackage.pl conf-files/clearlooks-configure.in
```

Additionnal note: no documentation attached with the perl script, still just hacking.

---

### Post by leibowitz on 2007-07-01
No more prob with metacity.

```
./getconfpackage.pl conf-files/metacity-configure.in
### 1 opening conf-files/metacity-configure.in
  glib-2.0 >= 2.6.0
  *********************
  gtk+-2.0 >= 2.6.0
  *********************
  gtk+-2.0 >= 2.6.0
  *********************
  gtk+-2.0 >= 2.10.0 pango >= 1.2.0 gconf-2.0 >= 1.2.0 libstartup-notification-1.0 >= 0.7 xcomposite >= 0.2 xfixes xrender xdamage cm xrender >= 0.0 xcursor
  *********************
### File conf-files/metacity-configure.in done

```

It seems everything works as good as before, but now metacity report every packages. I did inverse the variable substitution lookup, from top to bottom to currentline to the top. Which means we start from the current line where $SOME_VAR is used, to the line before, and so on till we find the definition (SOME_VAR=...). This is recursive so a var can be defined from another var value...

Cool, heh? 

The updated perl script has been attached here. Cleaned it a bit. And comments are now in the source.

---

### Post by abhijeetmaharana on 2007-07-01
> **leibowitz said:**
>  Cool, heh? 

You bet!!! Thats some great progress on the dependency front. I am also *almost* done with the GUI. Thinking of writing an install script so that it is usable by others as well. Should be done in an hour and half.

After that, in the next one week or so, we will have to get down to integrate your dependency detector scripts with the GUI. I have made attempts to keep the code decoupled. So integration should not pose as many problems.

---

### Post by abhijeetmaharana on 2007-07-01
> **leibowitz said:**
> The big loser here is wine-configure.ac, which contains many many checks but no PKG_CHECK_*. This means no results atm. Are we targetting wine-like applications anyway.


I hadn't thought about wine like applications. Lets see how we can handle that. No idea at the moment.

---

### Post by leibowitz on 2007-07-01
Wine is a big one. I mean it has a wine.m4 file for it, which is like a bash script for checking his dependencies.

More configure.{ac,in} files have been tested.

Updated the PERL script to make them work:
- The script doesn't parse lines beginning with # or "dnl". Those are comments.
- Variable substitution take quotes into account. GTK=1.2 isn't the same as GTK="$MORE THAN ONE"
- Added handling of AG_GST_GLIB_CHECK macro found on gstreamer configure. This set the GLIB_REQ variable.
- Added handling of AC_SUBST found in Istanbul and gtk-recordmydesktop.

---

### Post by abhijeetmaharana on 2007-07-01
[COLOR="Blue"]July 01 update: The GUI is usable. Requires Java 1.6. I have updated the first post in this thread. [/COLOR]

It took longer than I had anticipated. And install.sh had its own quirks.
It just occurred to me that the program should check for build-essential before trying to even extract files from the archive. Will incorporate it in a future version.

It seems that the nautilus script works only for a few times after installation. Then it just goes dead. 
I have also noticed that it can't find the source archive when invoked by the nautilus-scripts folder on an archive on desktop (unless there is an archive with the same name in your home folder). 
Does anyone else has the same problem? Any ideas why?

GISA.........sounds very good. Lets keep it :-)

---

### Post by leibowitz on 2007-07-01
Edited: I've just tried it. The install.sh works good, everything is installed and right-click SourceInstaller launch the application on the selected package.

The application interface is a bit big, I can't see the buttons if I resize the application, even maximized isn't enough (800x600).

The devil is in the details, you know. I don't care about this though, because I feel like this will not be our final product. And I mean it, mainly because Java is the wrong choice. 

Anyway, I want you to finish your Java interface as much as you can. Feel free to improve the interface. No matter what the final thing would be, or what language it uses, it will be kind of the same as our vision now. Then if it's not convincing now, it will never be. 

Maybe I will check if I can help in Java but I'm like a total beginner in this language. Indeed do not wait for me for java help.


Additionnal notes:
- When you right-click > InstallFromSource on anything else than an archive, it will fails miserably. I would check if it's an archive first. Report dialog box error if it's not.
- After a sucessfully make install, don't clean the source directory. Because sometimes there is a way to uninstall with autotools. (make uninstall). Deleting the temporary directory means no uninstall. 
- The window should resize widgets much better than this.


By the way I did not understood what you mean by this.
> I have also noticed that it can't find the source archive when invoked by the nautilus-scripts folder on an archive on desktop (unless there is an archive with the same name in your home folder).

I tried right-click>install on an archive in ~/Desktop and it worked.


Note for improvement: I would like to add a check in the uncompressed directory, before trying to compile. This check would see if there is a configure script and a makefile. If not, then it would simply say "Not a GNU-compatible archive." Not just this, but something saying that this archive contain no configure nor makefile then can't be compiled using GISA. 

This is like a requirement for the source archive to be compatible with GISA, isn't it.

---

### Post by abhijeetmaharana on 2007-07-01
> **leibowitz said:**
> Edited: I've just tried it. The install.sh works good, everything is installed and right-click SourceInstaller launch the application on the selected package.

Thats some good news. I was skeptical.

> 
The application interface is a bit big, I can't see the buttons if I resize the application, even maximized isn't enough (800x600).

No doubt! I was using 1280x1024. I have updated the main post with this. Ill see if I can get it to scale gracefully.
>  
And I mean it, mainly because Java is the wrong choice. 

As I have already stated, I felt this from the beginning. But went ahead because I am not comfortable with any other language. On second thoughts, if Gutsy ships with JRE1.6 or some version that we can run on, I don't see a reason why we shouldn't be using Java. If application efficiency is what worries you, I doubt its hardly an issue here. And these days, Java matches up pretty well (that is, if the programmer doesn't goof up). I didn't have a chance to dabble with the Gutsy test releases, so I won't know. Just a thought.

> 
- When you right-click > InstallFromSource on anything else than an archive, it will fails miserably. I would check if it's an archive first. Report dialog box error if it's not.
I would like to add a check in the uncompressed directory, before trying to compile.
- After a sucessfully make install, don't clean the source directory. Because sometimes there is a way to uninstall with autotools. (make uninstall). Deleting the temporary directory means no uninstall. 

First two were at the back of my mind. Just kept them for later. Regarding the temporary directory, I think we will ask the user if that is to be deleted. Or keep a button for doing it if the user wants.

> 
By the way I did not understood what you mean by this.
I tried right-click>install on an archive in ~/Desktop and it worked.

This is still happening with me. Reproducible. If the archive is on the desktop (and a copy of it is not in the home folder), the application says it can't locate it. Its just the desktop. If I create a folder on the desktop and keep the archive there, it launches fine. I had run into this earlier with one of my scripts. So checked it consciously and its there. 

Nautilus doesn't seem to pass the full path of the file as the first argument. It passes just the file name. This is true for non-desktop archives as well. Just that it doesn't work when the root desktop window houses the archive. Thats why I had to assume the home folder for creating temporary files. Otherwise, temporary files are created in the same folder as the archive.  I am using Edgy (2.6.17-10-386) and Nautilus 2.16.1 if that is relevant.

---

### Post by abhijeetmaharana on 2007-07-02
Until we figure out how to use Launchpad, I can use this post as a TODO/Wish list for the GUI. Keeping track mentally is getting tough. It also lets others see what is being worked on. Ill place a link from the first post for easy accessibility and visibility. I think we can have something similar for the dependency scripts. What say? I will keep updating this list as suggestions for the GUI come in. For now, [high priority / easy to fix] GUI items on the TODO, rest go to the wishlist. As always, feel free to point out any corrections to the priorities.

TODO:
[List=1]
[*] [FIXED] Check if the file is an archive before attempting anything 
[*] [FIXED] Check the extracted folder to determine if its autoconf based 
[*] Do not clean up temporary directory after a successful install. Provide option to the user
[*] Allow user to pass options to the configure/other scripts
[*] Keep extraction from archive as a separate user initiated action. (e.g. When ./configure fails due to dependencies, there is no need to clean up the temp directory and extract from the archive again).
[/List]

WishList:
[List=1]
[*] Investigate on Nautilus desktop path issue (refer post above).
[*] [FIXED] Resolution issues - Scale gracefully 
[*] Look inside the archive to get hold of the root folder name instead of assuming that its same as archivename-extension
[/List]

---

### Post by Afoot on 2007-07-02
> **abhijeetmaharana said:**
> 
As I have already stated, I felt this from the beginning. But went ahead because I am not comfortable with any other language. On second thoughts, if Gutsy ships with JRE1.6 or some version that we can run on, I don't see a reason why we shouldn't be using Java. If application efficiency is what worries you, I doubt its hardly an issue here. And these days, Java matches up pretty well (that is, if the programmer doesn't goof up). I didn't have a chance to dabble with the Gutsy test releases, so I won't know. Just a thought.

As far as looks go, it (swing) doesn't integrate too well with GNOME. Other than that I'm fine with it being Java.

---

### Post by leibowitz on 2007-07-02
> I don't see a reason why we shouldn't be using Java. If application efficiency is what worries you, I doubt its hardly an issue here.

I don't see any efficiency problem. It's more a phychological problem. Do you know any other application on the desktop that use Java ?

Of course the default inclusion of Java in a distribution could resolve those issue.

It's also a maintaining issue. Java needs Java programmer. And open-source software don't see many Java programmers. 

I saw this before with other languages. C was an issue on some software, so they migrated it to python for better maintainability(?) 

I would like it to be Python just for this, but I don't know python so couldn't help either...

By the way I'm learning Perl since I'm hacking on those script, so who knows, maybe I will try Java/Python after this.


I hacked a bit more the Perl Script with more configure.{ac,in} files.
- better handling of dependency string.
- added m4_define substitution code.
- output is now splitted with one package dependency by line.


Here is the result with nautilus configure
```
./getconfpackage.pl conf-files/nautilus-configure.in
### 1 opening conf-files/nautilus-configure.in
esound >= 0.2.27
bonobo-activation-2.0 >= 2.1.0
eel-2.0 >= 2.14.3
glib-2.0 >= 2.6.0
gnome-desktop-2.0 >= 2.9.91
gnome-vfs-2.0 >= 2.14.2
gnome-vfs-module-2.0 >= 2.14.2
ORBit-2.0 >= 2.4.0
pango >= 1.1.2
gtk+-2.0 >= 2.6.0
libart-2.0 >= 2.3.10
libbonobo-2.0 >= 2.1.0
libgnome-2.0 >= 2.1.1
libgnomeui-2.0 >= 2.6.0
librsvg-2.0 >= 2.0.1
libxml-2.0 >= 2.4.7
libexif > 0.5.12
libexif = 0.5.12
tracker >= 0.0.1
libbeagle-0.0 >= 0.0.12
gtk+-2.0
gconf-2.0
libgnomeui-2.0
### File conf-files/nautilus-configure.in done
```

You can see there are some repetition with libexif > 0.5.12 but it's no bug. One line check for greater-than, the other for equal. It's really in the configure.in script.

I'm still searching for more configure.{ac,in} files to find bugs in the script. Currently I have tested 92 different files, and it's working great with all of those.

Though I don't know what we are going to do with this dependencies output.

---

### Post by abhijeetmaharana on 2007-07-02
> **Afoot said:**
> As far as looks go, it (swing) doesn't integrate too well with GNOME. Other than that I'm fine with it being Java.

How about something like this? The about dialog also looks like a GTK one. At this point I can't say if everything will be exactly GTK but there doesn't seem to be any problem. I changed my NetBeans IDE to look like this and it was just fine.

---

### Post by abhijeetmaharana on 2007-07-02
> **leibowitz said:**
> Though I don't know what we are going to do with this dependencies output.

This is what I was thinking:
We will determine the dependencies before running the configure script, display them in the list on the right side and tick mark the ones already installed. If possible, we will get the size of each the uninstalled packages and display it as well. As soon as the user opens a source package, (s)he gets a good view of all the components already there, those that need to be installed and how much would have to be downloaded. This will be helpful to people with limited bandwidth connections. Version number handling would be great though I haven't thought about a solution in that direction.

Going a step ahead, staying with our original plan, we can have a switch that tells the program to automatically install the required packages and report only if there was any trouble. But personally, I would avoid using it until it proved to be highly reliable.

I guess this sounds like how a typical user would want things to be. What do you think?
Is there any way we could tell if those packages are required? I mean the ones whose absence will cause configure to complain. Do you have anything in mind?

> 
Do you know any other application on the desktop that use Java ?

There may be. We cannot say for sure until we make a thorough search. And if there aren't any.....we could start things. :-)

---

### Post by leibowitz on 2007-07-02
Perfect.

We can't say for sure that every package are required. So we must show the revelant information for the user to choose if it's required or not.

I would see this list, with the information if it's Installed or not. Then the user could choose what he want to install. 

For automated install I must ask, do you know how to install package with GUI ? I mean, synaptic uses a dialog to install packages which embed vte terminal emulator. And this is used by Gdebi aswell. I tried to find a command that launch this (kind of apt-get install for graphical installation) but didn't find any revelant information.

I think we won't go in that direction. Show the information is sufficient in my opinion.

---

### Post by leibowitz on 2007-07-02
Not related to our talks, but here's someone raising the Java situation  [http://ubuntuforums.org/showthread.php?t=490169](http://ubuntuforums.org/showthread.php?t=490169)

I won't talk about it, let's just see what is the public opinion about it.

---

### Post by leibowitz on 2007-07-02
I'm thinking about what the best language for the GUI would be. 

I already know C/GTK+ but I doubt it would be of any fun.

Python seems to be the best choice. It's object orientend, easy to learn and can call scripts without problems.

What do you think ? 

I'm going to put my hands on python during following days. Not in relation with this at first like creating a simple dialog box, reacting to user interaction, call scripts, check the results, etc...

---

### Post by abhijeetmaharana on 2007-07-02
> **leibowitz said:**
> Python seems to be the best choice. It's object orientend, easy to learn and can call scripts without problems.
What do you think ? 


Yup. Python is a great language. But I would suggest we stick with what we already know. We will be able to deliver faster and better that way. In the meantime, we can keep learning Python but it will take some time to learn the hidden tricks. This will also allow us to spend more time on the application flow and logic.

Should we first try migrating to Launchpad and then resume further work on the application?

---

### Post by leibowitz on 2007-07-02
Don't know for launchpad.

What do you mean exactly, transfer source files on a git/bzr server ?


On the Python thing, here is what I get from two hours of python hacking. A command line tool which list what you throw at it (directory or archive [bzip2, gzip, tar, zip]) (See attachement)

I don't think it will be easy at first to code the GUI around python for both of us (python beginners). The fact is it will definitely attract more contributors later. Otherwise your application won't evolve without you by lack of maintainer.

If you feel like doing it in Java, that's ok for me. I will try to translate it to python later anyway. I just need to learn python and pyGTK first. (in some months, maybe!)

---

### Post by abhijeetmaharana on 2007-07-02
> **leibowitz said:**
> What do you mean exactly, transfer source files on a git/bzr server ?
Yeah!

> The fact is it will definitely attract more contributors later
I see your point. I think we should go ahead and do one usable, stable release with the dependencies and most of the GUI bugs taken care of so that people can start using it without much hassle. Then, before going any further, we can work out the details.

> Otherwise your application....
"Your" as in "mine"? I would rather have it called "our" :-)

>  ... won't evolve by lack of maintainer 
Launchpad!

> I just need to learn python and pyGTK first. (in some months, maybe!)
I am game.

---

### Post by Afoot on 2007-07-02
Azureus is written in Java.

I'm all in for this to be finally written in Python, but since abhijeetmaharana has already made a good start at the Java program, he could as well finish it, and then we could port it to python/gtk when it's just about finished.

---

### Post by leibowitz on 2007-07-02
Here is a little Bash script (one more) that will check from a pkg-config string if a package is installed, not installed, can be installed from the available package list, or should be installed from sources. It's a lot of information. Just to show you what we can do.

It's not really useful as it is. So let met explain with an example.

I just downloaded [giver]("http://idea.opensuse.org/content/ideas/easy-file-sharing"), which is a new application created in IdeaPool.

Now by checking his configure file with getconfpackage Perl Script, it reports the "dependencies" checked by PKG_CHECK_MODULES. This is the output.

> ./getconfpackage.pl conf-files/giver-configure.ac
### 1 opening conf-files/giver-configure.ac
glib-sharp-2.0
gnome-sharp-2.0
gtk-dotnet-2.0
notify-sharp
avahi-sharp
### File conf-files/giver-configure.ac done

What do we do with all of those strings ? Send the first parts to the new pkgconfig-checkname Shell Script. 

Note that here none of the dependency has a version expressed. It's different in some other packages. For example with giggle we could check if the version is available. 

> ./getconfpackage.pl conf-files/giggle-configure.ac
### 1 opening conf-files/giggle-configure.ac
glib-2.0 >= 2.12
gthread-2.0
gtk+-2.0 >= 2.10
gtksourceview-1.0 > 1.8
libglade-2.0 > 2.4
### File conf-files/giggle-configure.ac done

Anyway, throw the pkg-config string to the shell script and it will inform you.

> ./pkgconfig-checkname.sh gtk-dotnet-2.0
Checking for gtk-dotnet-2.0
Installed libgtk2.0-cil

Even saying what package provide this.

I don't have any idea how to make all of those scripts behave in a common way, but I keep searching.

Additionnal note on version requirement: pkg-config is a very powerful tool. It reports version of installed package for example. With a package like giggle, more things needs to be done. 
> pkg-config --modversion gtk-dotnet-2.0
2.8.2



New script: pkgconfig-checkname. Will check from a pkg-config string if the package is installed, from source or deb, and by which package it is provided.

---

### Post by abhijeetmaharana on 2007-07-02
> **Afoot said:**
> Azureus is written in Java.
Ah yes! Thats a prominent one. Didn't occur to me at that time.

[QUOTE=leibowitz]New script: pkgconfig-checkname. Will check from a pkg-config string if the package is installed, from source or deb, and by which package it is provided.[/Quote]
That sounds great! "getpkg-070702-1.tar.bz2" combined with the above seems to provide a complete flow. I will get working with these two in the evening.

With regards to the GUI that we currently have, is there any need for the "Dependencies selected" list after these two have been integrated? I think we will add a new control for the output of these scripts and keep the current UI elements as they are so that the user still has finer control. What do you say?

---

### Post by leibowitz on 2007-07-03
I'm currently trying to understand how to present these things to the user.

This is what I get at the moment.

1) Check the file passed: if it's an archive (bzip2, gzip, tar, or zip) then uncompress it to a temporary directory.
If it's not, say it only handles compressed archive of those formats.

2) From the file list, check if there is a configure.ac first, or configure.in script (respect the order). If one is found, scan it with getconfpackage Perl script and print the results on a list in the GUI. 

3) Put some action-buttons in the interface:
- "Check dependencies" will check if one or all of the pkgconfig files are present. If a version is specified in the configure.in file, then add the --modversion to the pkgconfig test. The result should be visible on front of each package name. It will be something like what pkgconfig-checkname.sh shell script does.
- "Scan source" will check source files. For each header file it will try to find it on the local system. If no package is found providing this file then it will be reported to the user that this header file is missing. If possible a list of package providing this file will be proposed.
- "Configure" will just call ./configure.



> I think we will add a new control for the output of these scripts

A [GtkTreeView]("http://developer.gnome.org/doc/API/2.0/gtk/GtkTreeView.html") should do the trick. I don't know the Java swing name for that type of control. So I will just throw a [picture]("http://boby.joe.free.fr/files/Referencer.png") of a GtkTreeView.

---

### Post by abhijeetmaharana on 2007-07-03
Could manage only an hour today. So took up the easy to fix bugs:
[LIST=1]
[*]Starting with unsupported file types now shows an error dialog informing the user
[*]Starting with folders (which used to fail earlier) now shows an error dialog
[*]User could type an arbitrary filename in the open file dialog and dismiss it. Taken care of now.
[*]Moved repeated code to separate methods.
[/LIST]

I will update the todo list tomorrow.

---

### Post by abhijeetmaharana on 2007-07-04
Which are the required files in a GNU package? According to [http://sourceware.org/autobook/autobook/autobook_25.html](http://sourceware.org/autobook/autobook/autobook_25.html), [http://sourceware.org/autobook/autobook/autobook_277.html#SEC277](http://sourceware.org/autobook/autobook/autobook_277.html#SEC277) and the subsequent diagrams, configure.in is a required file but the pidgin source doesn't have it.

Currently I have put a check for [Makefile.am, Makefile.in, aclocal.m4, install-sh, configure, mkinstalldirs, missing] to determine if the directory is a GNU package source. But it seems that aclocal.m4 is also optional.

---

### Post by leibowitz on 2007-07-04
NEWS README AUTHORS ChangeLog INSTALL COPYING are all required

configure.{in,ac} and Makefile.{am,in} are not required at all.

configure is better to have.

Makefile is generated by ./configure if available.


I don't know about aclocal.m4. It seems required too.


Some thought:
I think we just need to scan the configure.{ac,in} if available. If the file is missing, not a problem.

Then try to find the ./configure script to be run.

If not available, try to call make directly.

In all case "make" call need a Makefile to be succesfull. In most of the case it will be created after the ./configure call.

The only case where it's impossible to compile a software is lack of configure and lack of Makefile. If both are missing, we can't do anything at the moment.

---

### Post by abhijeetmaharana on 2007-07-10
I think we can move the dependencies to another screen. A tabbed interface maybe. Does this dependencies screen look fine? Something seems to be missing. But I can't tell what.

---

### Post by leibowitz on 2007-07-10
I think that's already too big. What do you want to add to this?

Also I don't see any relation to the previous GUI you provided with the last java version.

Could you please point out what's the relation between windows/screens.

---

### Post by abhijeetmaharana on 2007-07-11
The previous screenshot was only of the dependencies panel in a tabbed interface. There would have been another tab with the source archive path and the output window. However, I felt something was missing. 

I have changed the GUI. Take a look at this screenshot. There are no tabs. Just this screen. When the user clicks on "Search for packages", the selected text from the textarea is taken, packages providing it are determined and shown to the user in a dialog box for installation. The table will only be populated with what we determine beforehand.

I will make the window smaller and align the controls. But does it convey the information about installation and dependencies without confusing the user. As we had discussed earlier? 

Also, is there any way we can figure out the dependencies that are absolutely essential for installation? I think that information is also available within the configure scripts. Otherwise it wouldn't stop only on the essential ones. I ran getconfpackage.pl on pidgin's configure.ac and then ran pkgconfig-checkname.sh on each of the reported dependencies. It seems like a big list. All of the packages reported as "not installed" are not required.

---

### Post by leibowitz on 2007-07-11
I don't know about user interaction.

I have no experience in that area.


For the dependencies there is no way to know for sure that the package is required or not. That's why we cant' install every detected packages.

The only way to be sure is to call the ./configure script and see if it fails. Though sometimes the configure is not complete and lack some checks.

No, there's no way to be sure

Even scanning the source code is not sure in 100% of the case because there could be flags before the #include line, for example that checks the operating system.

---

### Post by abhijeetmaharana on 2007-07-11
Ill go ahead with this layout then and see how it works out. Lets see what else we can do with the dependencies later.

---

### Post by abhijeetmaharana on 2007-07-14
```

abhijeet@ApplicationServer:~/NetBeansWork/SourceInstaller$ ./pkgconfig-checkname.sh mozilla-nss
Checking for mozilla-nss
Not installed: please install libnss-dev: usr/lib/pkgconfig/mozilla-nss.pc mozilla-dev: usr/lib/pkgconfig/mozilla-nss.pc

```

Does this mean that *both* libnss-dev and mozilla-dev are required or is it *either* of them? From the name mozilla-nss, I gather that its both but does this hold true for other cases as well?

---

### Post by leibowitz on 2007-07-14
Good catch.

I didn't know that two different packages could provide the same pkgconfig file.

> apt-file search /usr/lib/pkgconfig/mozilla-nss.pc
libnss-dev: usr/lib/pkgconfig/mozilla-nss.pc
mozilla-dev: usr/lib/pkgconfig/mozilla-nss.pc

It's one or the other definitely.

mozilla-dev package is in conflict with libnss-dev. So you can't install both even if you want to.

---

### Post by abhijeetmaharana on 2007-07-18
We can do without this but does anyone have a regular expression for capturing package names from strings of the type
```

Not installed: please install libnss-dev: usr/lib/pkgconfig/mozilla-nss.pc mozilla-dev: usr/lib/pkgconfig/mozilla-nss.pc

```

The regex should capture "libnss-dev" and "mozilla-dev" from the above string.
Currently I am using
```

(\S*): usr\S* 

```
It gets me libnss-dev. But I am unable to repeat this pattern so that all such occurrences are captured. The information at [http://www.regular-expressions.info/captureall.html](http://www.regular-expressions.info/captureall.html) seems to be helpful but I am unable to apply it here.

I will write a "normal" string parsing method but was just curious. I am creating a new thread since this looks like an independent question.

---

### Post by brennydoogles on 2007-07-18
None of what you guys are talking about makes much sense to me, but if you need testers for input when you have something a little bit more solid I would love to help you out and give you feedback.

---

### Post by leibowitz on 2007-07-18
brennydoogles: feel free to come back here from time to time to see if we are near a release. But that will probably take times.

abhijeetmaharana: I don't know but I can edit the script to output what you want. Just tell me what you need.

I already edited it to cut the file path/name but can't test it with mozilla-nss, here it reports "Installed"

---

### Post by abhijeetmaharana on 2007-07-19
brennydoogles: Thanks. But as leibowitz has pointed out, a release will take some time. I have a feeling we are a bit slow but thats all the time I am able to take out from my job at the moment. Things should move faster in the near future. Be sure to check back once in a while.

leibowitz: I will take this updated script and try to make any small changes needed to get it running. I was trying to avoid changing your script so that it can be used independently as well. But I think a little change here and there will make it easy to integrate it into the GUI.

The dependencies are being scanned and I am presenting them in a table with information such as the installation status of the packages and a button to install the package the user selects. But it isn't much use. 

I tried to run the program as a normal user would do and realized that I kept letting the configure script fail on a critical dependency, install that, and proceed similar to what it was in beta2. It is a pain to have the configure scripts scanned, which is a time consuming task, only to realize that we don't know which ones are essential. 

You have already pointed out that its difficult / impossible. But unless we do something about it, this feature feels only like a fancy add-on.

---

### Post by abhijeetmaharana on 2007-07-20
Well, it seems like we have something that does exactly what we are trying to do. Take a look at the Concept section of [https://wiki.ubuntu.com/AutoDeb](https://wiki.ubuntu.com/AutoDeb). I tried to run it but got errors
```

./autodeb.sh: line 486: unexpected EOF while looking for matching ``'
./autodeb.sh: line 514: unexpected token `' in conditional command
./autodeb.sh: line 514: syntax error: unexpected end of file

```

I had a look at the script but couldn't figure out the error. And I am not very comfortable with shell scripts. Could you give it a try?

If this thing works, we have most of the things done. Then what is left is just providing a GUI. Or so I think. Or we could use the part that automatically installs dependencies when the configure script fails. 
I will mail its programmer to seek permission to use / modify his work.

---

### Post by leibowitz on 2007-07-21
The problem seems to be in this line

>  NewControl=`head -n ${HeadLineNumber} "control"; echo "Depends: ${BinDepends}"; tail -n +${TailLineNumber} "control"`

But I don't see any.



> It uses (a modified version of) AutoApt to find development dependencies during 'configure'

Didn't we already checked autoapt ?


> if [ ! -e /usr/bin/auto-apt ]; then
echo ""; echo "Installing auto-apt..."
sudo aptitude -y install auto-apt

That's just using the auto-apt program as it seems.


I think we must look into other programs aswell, to find some ideas. That's a good thing to do. But looking into auto-apt again seems not like a solution to me. Any thought on this ?

---

### Post by abhijeetmaharana on 2007-07-21
> **leibowitz said:**
> That's just using the auto-apt program as it seems.


It does use auto-apt but prior to running, it modifies the auto-apt script so that instead of trying to install anything, auto-apt just keeps track of the files being referenced. When the configure script fails, this program queries auto-apt to get hold of the last file that was referenced. It then installs the package providing that file and reruns configure. And before terminating, it restores the original auto-apt script.

I would say Neat!!!
I doesn't detect dependencies in advance as we are doing. But unless we find out a way to determine which dependencies are essential, this seems a very good alternative. What say?

The error is puzzling though since the quotes look fine. The script seems to be fairly complete. If we can get this running, it does almost all the things we are trying.

---

### Post by leibowitz on 2007-07-21
I'm kind of afraid to try it on my workstation.

But I will try in a VM later.

---

### Post by abhijeetmaharana on 2007-07-21
Leibowitz, in your post at [http://ubuntuforums.org/showpost.php?p=2954738&postcount=74](http://ubuntuforums.org/showpost.php?p=2954738&postcount=74), you have suggested that we scan configure.[ac in] if one is found. 
Can both be present? If yes, do we have to scan both files and merge the results before presenting in the table or something else needs to be done?

---

### Post by leibowitz on 2007-07-21
Yes both can be present, no you don't have to scan both.

If configure.ac is present, then go for it.

If not, check if some configure.in exsit.

If not, then you can't check the "configure" with the script. But you can use your past solution for scanning configure.

---

### Post by abhijeetmaharana on 2007-07-21
I am attaching Beta3. 

[LIST]
[*]Controls resize when window is resized. Looks decent on 800x600 as well.
[*]Installation folder is not deleted regardless of installation success. This can actually be a headache since the temp folder is owned by root and cannot be deleted by the normal account. Needs more thought.
[*]Checks for the configure script only to determine if it is a valid source archive. Ill implement the stuff about checking the makefile if a configure script is not found in the next beta release.
[*]If both configure.ac and .in are found, .ac is scanned. Scanning of the configure script when both are not found will be in the next beta release.
[*]If no dependencies are found after scanning the configure scripts, it displays a message asking to report the issue.
[*]A split pane in the main window lets the user resize the output window.
[/list]
[list]
[*]Included an uninstall script.
[*]Reorganized code into sub packages and utility classes so that it will be easier to maintain in the long run
[/LIST]

Give it a try and let me know if you find any other issues. I will update the first post and the todo list tomorrow morning. Its 3 AM here and I need some sleep very badly :-)

[Attachment moved to first post]

---

### Post by leibowitz on 2007-07-21
> Installation folder is not deleted regardless of installation success. This can actually be a headache since the temp folder is owned by root and cannot be deleted by the normal account. Needs more thought.

I'm not sure why you need to create a folder as root or with administrative privileges.

---

### Post by abhijeetmaharana on 2007-07-21
> **leibowitz said:**
> I'm not sure why you need to create a folder as root or with administrative privileges.

Its because the program is started with sudo. When we take the sudo password from within the program itself, this problem will be taken care of. This is in the todo list.

---

### Post by abhijeetmaharana on 2007-07-22
[COLOR="Red"][OLD. Moved from first post][/COLOR]

[COLOR="Blue"]**Update: June 27, 2007**[/COLOR]
* I used pidgin-2.0.2.tar.bz2 for these tests
* Reference: [http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-search.en.html)
* No source code changes in this update

With regards to our options in post #8 below:

[LIST=1]
[*]I tried auto-apt first since it appeared to be most appealing. However, it did some things I had not expected. For example, pidgin's ./configure reported several packages/files to be missing but continued whereas auto-apt went on to install those. Like selinux-policy-default. I think those packages were not essential for the task to continue. Could someone verify this and post how we can keep auto-apt from installing such packages? It also segfaulted many times. Those who want to have a first-hand look at what happened can watch this video (.ogg / ~16 MB): [http://rapidshare.com/files/39321234/auto-apt_errors.ogg](http://rapidshare.com/files/39321234/auto-apt_errors.ogg)

This is what happened AFTER auto-apt installed the unnecessary packages on the first run. I recorded the second run. But the most important thing is, like pidgin's ./configure, it stopped at libxml2 which I don't have. I was expecting **this** to be taken care of by auto-apt. The unnecessary packages are secondary concern.

Although auto-apt has options like "Automatic yes to prompt", "quiet" and "Disable X inferface", I have reservations. It seems enticing but unless we iron out the above, I think we should explore other options. [COLOR="Red"]Anyone investigating further on auto-apt?[/COLOR]


[*]The other (crude) way I can think of is below. Let us see how 'crude' it is and in the absence of better options, we may have to go ahead with this.
one-time
```

sudo apt-get install apt-file
apt-file update	(downloaded ~11.37 MB on my system)

```

For each missing package/file reported by ./configure
```

Search if a dev package of same name exists
(aptitude search packagename-dev)
	If yes, 
		request versionX requested by ./configure to be installed 
		(aptitude install packagename=versionX)
	If no, 
		apt-file search <name reported by ./configure> 
		Come up with some expression which will give us a "nearest" match to select the most suitable one and extract the package name
			(this is fuzzy at the moment...need to expand this more)
		request aptitude to install versionX requested by ./configure

```

The 'no' part above is the one we will run into most frequently and it is the one that needs a lot more work. Feel free to expand the above. We also have to consider things like what if the user already has another version installed. But we better take one step at a time. I think I will wait till the above pseudo-code is sufficiently clear before making any changes to the code. I hope I have been clear enough with the above. Put in your thoughts.


[*] Will it be harmful to assume now that the source packages use autoconf? Later on, we can identify the source package type (currently we don't know how) and use an appropriate module to handle the installation.
[/LIST]

---

### Post by abhijeetmaharana on 2007-07-22
[COLOR="Red"][OLD. Moved from first post][/COLOR]

[COLOR="Blue"]**Update: July 01-02 Midnight, 2007**[/COLOR]
* Beta 2 is available. Download: [http://ubuntuforums.org/attachment.php?attachmentid=37019&d=1183321289](http://ubuntuforums.org/attachment.php?attachmentid=37019&d=1183321289)
* I installed pidgin-2.0.2.tar.bz2 using the GUI (GUI requires JRE 1.6).  The GUI has a few noticeable bugs. 1280x1024 recommended at the moment.
* The GUI assumes that the archive's root is a folder with the same name (without extension). For example, if the archive is pidgin-2.0.2.tar.bz2, it must yield the folder pidgin-2.0.2 on extraction.
* Code updated and moved to NetBeans (5.5)
* Afoot has recently created Launchpad project page at [https://launchpad.net/gisa/](https://launchpad.net/gisa/)
* Scripts to determine dependencies are being improved upon. We are concentrating on autoconf based packages at the moment.

[LIST]
[*] GUI version: Screenshots: [Swing default look]("http://ubuntuforums.org/showpost.php?p=2946287&postcount=57") and  [GTK look]("http://ubuntuforums.org/showpost.php?p=2949280&postcount=63")[INDENT]The GUI version is pretty usable as it is; except for a few cases like 'you can click on the install dependency button over and over even before the previous install is over' and some more. These are low priority items at the moment. As for the code, I have moved it to NetBeans. The project folder is in the attached archive. You can run it from Nautilus via the nautilus-scripts facility. The included install.sh file should take care of that. It can also be run standalone and the source archive selected from withing the program itself. I ran into some trouble with the install.sh script on a few occasions. You may need to work around it at the moment. I have put in a basic apt-cache search in the GUI. This will be replaced by a dependency detection script when it is ready.

Download SourceInstaller0.1Beta2.tar.bz2 attached below and run install.sh. After installation, right click on a source archive and select Scripts >> InstallFromSource. If install.sh doesn't work, make a post and in the meantime, run the application by creating a launcher with the command ```
java -jar "<path to SourceInstaller.jar>"
```[/INDENT]
[*] Dependencies:[INDENT]This is very high on the priority list. We are trying many approaches to determine the dependencies of the source packages. 
[LIST]
[*] kelimion has pointed to dlocate which is a fast replacement for dpkg -S and may come in handy.


[*] Script to scan source files and search for the included headers using apt-file (written and improved upon by leibowitz: [http://ubuntuforums.org/attachment.php?attachmentid=36613&d=1182948965](http://ubuntuforums.org/attachment.php?attachmentid=36613&d=1182948965) and [http://ubuntuforums.org/attachment.php?attachmentid=36666&d=1183000956](http://ubuntuforums.org/attachment.php?attachmentid=36666&d=1183000956)


[*] Java program to scan configure script and get the dependencies (naive - works only on a few cases - by me): [http://ubuntuforums.org/attachment.php?attachmentid=36835&d=1183150805](http://ubuntuforums.org/attachment.php?attachmentid=36835&d=1183150805)


[*] Parser for configure.{ac,in} files (with variable substitution, no m4 parsing - by leibowitz): [http://ubuntuforums.org/attachment.php?attachmentid=36917&d=1183212313](http://ubuntuforums.org/attachment.php?attachmentid=36917&d=1183212313)


[*] HIGHLY Improved version (by leibowitz): [http://ubuntuforums.org/attachment.php?attachmentid=37002&d=1183310858](http://ubuntuforums.org/attachment.php?attachmentid=37002&d=1183310858)
[/LIST]
[/INDENT]
[*] Our next focus will be on integrating the dependency detection scripts with the GUI. A Launchpad page has also been created and we are trying to get familiar with Launchpad. We may work on both of these in parallel or otherwise.
[/LIST]

---

### Post by abhijeetmaharana on 2007-07-22
[COLOR="Blue"]**Update: July 22, 2007**[/COLOR]
Beta3 is available. Download: [http://ubuntuforums.org/attachment.php?attachmentid=38800&d=1185096719](http://ubuntuforums.org/attachment.php?attachmentid=38800&d=1185096719)
[LIST]
[*] GUI resizes gracefully. Looks decent on 800x600 as well.
[*] A split pane in the main window lets the user resize the output window.
[*] Integrated Leibowitz's scripts to determine dependencies from the configure scripts.
[*] Installation folder is not deleted regardless of installation success.
[*] Included an uninstall script.
[*] Reorganized code into sub packages and utility classes so that it will be easier to maintain in the long run.
[/LIST]

Next focus:
[LIST]
[*] We have to find out how to identify the essential ones from amongst the dependencies reported by Leibowitz's scripts. Without it, detecting dependencies beforehand is of no real use.
[*] Alternatively, we have come across [AutoDeb]("https://wiki.ubuntu.com/AutoDeb") which does something similar. But we are unable to run it due to some syntax error which is not very obviuos. If anyone has been using it, make a post.
[/List]

---

### Post by brennydoogles on 2007-07-22
> **abhijeetmaharana said:**
> [COLOR="Blue"]**Update: July 22, 2007**[/COLOR]
Beta3 is available. Download: [http://ubuntuforums.org/attachment.php?attachmentid=38800&d=1185096719](http://ubuntuforums.org/attachment.php?attachmentid=38800&d=1185096719)
[LIST]
[*] GUI resizes gracefully. Looks decent on 800x600 as well.
[*] A split pane in the main window lets the user resize the output window.
[*] Integrated Leibowitz's scripts to determine dependencies from the configure scripts.
[*] Installation folder is not deleted regardless of installation success.
[*] Included an uninstall script.
[*] Reorganized code into sub packages and utility classes so that it will be easier to maintain in the long run.
[/LIST]

Next focus:
[LIST]
[*] We have to find out how to identify the essential ones from amongst the dependencies reported by Leibowitz's scripts. Without it, detecting dependencies beforehand is of no real use.
[*] Alternatively, we have come across [AutoDeb]("https://wiki.ubuntu.com/AutoDeb") which does something similar. But we are unable to run it due to some syntax error which is not very obviuos. If anyone has been using it, make a post.
[/List]

There was an older version that worked. The error is in the new version. See if maybe you can track down the old or a changelog to find the problem.

---

### Post by abhijeetmaharana on 2007-07-23
Can't seem to locate an older version or a changelog of the script. I have mailed the author. Lets hope for a positive reply.

---

### Post by abhijeetmaharana on 2007-07-25
We will be moving the code to Launchpad before any further work. Bugs will also be tracked there.

Project page: [https://launchpad.net/gisa](https://launchpad.net/gisa)
Latest code: [https://code.launchpad.net/~gisateam/gisa/devel](https://code.launchpad.net/~gisateam/gisa/devel)

Well..I encountered a lot of problems when trying to upload the code. As a result, many "broken" branches such as /dev got created. I can't seem to find a way to delete those branches. If anyone knows, drop a line. I have just marked them as abandoned for now.

---

### Post by abhijeetmaharana on 2007-07-29
> **abhijeetmaharana said:**
> Can't seem to locate an older version or a changelog of the script. I have mailed the author. Lets hope for a positive reply.

Received a reply from Lorenzo J. Lucchini. He has fixed AutoDeb. It was due to some missing quote about 100 lines above the line reported in the error message. However, he also mentions that he may have introduced more bugs in the code since he was in a hurry and may not be able to fix them for quite sometime.

Some more things in his mail:
[LIST]
[*] He recommends that we work in a chroot/fakeroot environment, a bit like pbuilder and avoid installing anything as root at all.
[*] Regarding the choice of language, he recommends a bash script with zenity/kdialog where required since a program like this doesn't really need a big interface that it has currently.
[*] He is trying to switch to strace, as opposed to hacking the auto-apt script, to trace files read by configure in his AutoDeb script. But right now, perhaps the auto-apt version works better.
[/LIST]
Taking a hard look at it, these things are beyond my capabilities at the moment. So I am not sure what to do next. In particular, should we continue with Java or is this the time to switch to C/Python/Bash script as we have discussed earlier? Feel free to put in your thoughts.

---

### Post by leibowitz on 2007-07-29
> But right now, perhaps the auto-apt version works better.

I doubt.


On Java/Python thing, I have a strong opinion on this: do both.

I thought it was better to do only one, but after viewing 15 minutes of this video:

[http://video.google.com/videoplay?docid=-5105910452864283694](http://video.google.com/videoplay?docid=-5105910452864283694)

I changed my mind.

---

### Post by LjL on 2007-08-01
I'm the author of AutoDeb.

Personally, I'd avoid Java for AutoDeb - although of course my goals with AutoDeb might be different from the goals of GISA.

The rationale:
- the program should need as little installation as possible, and a dependency on Java is quite a big dependency. Other languages like Python or, for that matter, plain shell scripting, don't have this issue, as they're included by default in Ubuntu (and just about every other distribution)
- I can't help thinking that the program will have to make heavy use of regular expressions, and often execute external programs and make use of their stdin/stdout/stderr. Thus, a language that makes this sort of things easy would be preferable.
- A Java GUI will only be a native (GNOME or KDE) one if one writes ad-hoc code that links to wrapper, which, besides, would bring in even more dependencies.

To me, Python, Perl or bash scripting would seem like better choice, although the value of this judgment is limited by the fact that I know neither Python nor Perl. But then Python seems to be the preferred language for just about everything, these days... ;-)

I have now written a version of AutoDeb with a GUI, using Zenity and KDialog to provide it. I have to admit that this approach has its flaws, not limited to the ugliness of bash code: simply, doing some things with Zenity/KDialog can become a bit of a stretch.

leibowitz's suggestion has its value, too: a program like this would lend itself well to being separated into a back-end (or engine, call it what you like) and one or several front-ends. Though, then, the question of what language to write the back-end in remains open.

I really would give Python serious consideration, anyway.

---

### Post by LjL on 2007-08-01
Now, aside from the language/GUI issues, some thoughts about the implementation issues of AutoDeb in general, which I think would also apply to GISA.


**1) Build dependencies (aka "second-guessing autoconf")**

autoconf, just like most other build systems, doesn't give machine-readable diagnostic messages about what is missing in order for a build to succeed.

This is far from a trivial issue, given that different distributions give packages different names and put files in different places.
There are even more involved issues, such as when a specific version of a package is required, or a library is required that isn't packaged at all.

The only procedure I could think of (and the one I have implemented in AutoDeb) is to keep track of every file that the build system tries to stat, open, read or otherwise access. Then if building fails, the program
a) goes back to see which files could not be found (ENOENT error code)
b) uses heuristics to guess which of the files is the most likely culprit (for instance, it tries first the ones accesses last), since there are many non-existing files that autoconf tries to access, but which aren't really needed at all
c) looks for Debian packages that provide those files, installs them, and tries again to build

Note that, this way, it is not possible to build a *complete* list of build dependencies: dependencies that were already installed before the build started are ignored.
This means AutoDeb cannot be used  to generate *source* packages with a correct Build-deps list; in fact, it doesn't generate source packages at all.
Doing so would possibly be handy for package maintainers, but hardly for users who just want to get some software installed.
It would be interesting to find a way to achieve this (I think it's theoretically possible using more LD_PRELOAD hacks, and/or a fakeroot environment), but I think it's out of the scope of AutoDeb and GISA.


**2) Safe installation**

One fundamental requirement is that the user be able to not only install, but also *uninstall* the software.
'make uninstall' can't really be relied upon, as too many developers don't include that target, or the implementation is flawed.

Another important goal is to avoid breaking the system or creating conflicts with pre-existing packages. I don't call it a "fundamental requirement" because, well, even by just running 'sudo make install', one is put at the complete mercy of the Makefile, which, in theory, could do anything.
But we certainly wouldn't want to *increase* the risk, at least.

We'd also benefit from some way to identify and track any runtime dependencies that the softwareneeds, but more about this later.

'checkinstall' is the most obvious choice to achieve hassle-free installation. It creates Debian packages (or I wouldn't have called my program AutoDeb, I guess ;-)), which can be uninstalled and can have a list of dependencies.

It features "filesystem translation" functionality, which means that during 'make install', the root filesystem isn't touched, but a temporary directory used instead. Only when dpkg installs the generated packages are files put into their definitive place, and dpkg can spot any conflicting files and refuse to continue if there are any.

Finally, installing into '/usr/local' rather than '/usr', which is autoconf's default anyway, certainly helps avoiding conflicts. It means that the resulting package cannot be a standard Debian package, but then it wouldn't be a standard Debian package anyway, due to a number of reasons.

**3) Runtime dependencies**

These, too, are important to get right. And contrary to build dependencies, you can't just ignore ones that are already installed, because if they get uninstalled later (which will happen if the user removes the package that brought them in), the user will be left wondering why his software has suddenly stopped working.

A handy tool for guessing runtime dependencies on executable programs is 'ldd', which gives a list of shared libraries that the program links to.

AutoDeb does the following:
a) get an 'ldd -u' list for every binary file belonging to the software (according to 'man ldd' and Google, the '-u' switch shows "unused" libraries, but it seems to me that this means *unused by other libraries*, i.e. direct dependencies, which is what we want)
b) find packages that provide those library files, and when a file is provided by multiple libraries, use heuristics again to decide
c) add those packages to the Depends line of our package

The same file being provided by multiple packages is a surprisingly common problem. For instance, many libraries have both a 'libfoo' and a 'libfoo-dbg' package, or you can have things like 'libc6' and 'libc6-i686', or 'libGL.so.1' being provided not only by the generic 'libgl1-mesa-glx' but also by the system-specific 'nvidia-glx'.

I've found that one promising heuristic is *pick the package with the shortest complete name* ("complete name" means as reported by 'auto-apt check', e.g. 'libdevel/libgl1-mesa-dev' vs 'restricted/x11/nvidia-glx').

Note also that, for libraries that are currently installed on the system, 'ldd' shows the complete path. At first sight, this would seem like helpful; however, the paths listed often correspond to specific flavors of packages, rather than the generic one.
For instance, '/lib/tls/i686/cmov/libdl.so.2' is, according to auto-apt, only provided by the 'libc6-xen' package (and according to apt-file, it's provided by 'libc6-i686' :confused:); however, plain 'libc6' is more than enough to provided that file, it just puts it into a different directory.
If the generated package is only to be used on *one* system (i.e. the one that has those files already installed), this isn't an issue. Still, AutoDeb currently opts for the slightly-more-portable solution, and discards path information.

For file other than binary executables, the situation is far more complicated. Right now, AutoDeb doesn't even try to tackle the problem.
Heuristics can probably be conceived for some filetypes: for instance, one could parse Python files looking for patterns such as "from <x> import <y>", and try to find the corresponding package.
Given that there are potentially infinite filetypes, a plugin-based system might be a sound option. Perhaps it even deserves to be made a separate program, say 'finddeps', in the spirit of commands like 'file' or 'vol_id'.


**4) When to be root**

This may seem like a relatively trivial issues, but it has resulted in quite a few headaches for me.

It's clear that, at some point, AutoDeb will need root permissions to install the generated package.

'checkinstall' itself can, apparently, run without root privileges: just pass it the '--install=no' option, and it will only create the package, while making 'make install' believe it's running as root, albeit it really isn't, thanks to its "filesystem translation" feature.

So, installation could be avoided completely, and the final task of installing the generated package be left to the user.

However, we still need root permissions *during* the build process, in order to access APT for installing build dependencies as they are identified.

AutoDeb currently runs as normal user, and invokes 'sudo' whenever it needs root permissions.
Since my goal is to be completely non-interactive (i.e. never pause the build to ask the user things), there is a problem every time an operation takes longer than 15 minutes (or whatever the 'sudo' timeout is set to).

The opposite approach would be to run *everything* as root, and perhaps go back to normal user when root permissions aren't needed.

This poses a few questions though: for starters, how does one go back to the right user? Will user 'nobody' suffice? Won't the 'chmod'-like commands that will have to be added actually make things *more dangerous*?

If we just stay root the entire time, we have the problem that 'configure' and 'make' will mess with ownerships in the source tree, and then the user won't be able to do file operations in it anymore without a 'sudo chown'.
Besides, we all know that running 'configure' as root is a no-no ;-)

I think the best and cleanest solution here would be to run as root (with the user having to 'sudo'/'gksudo'/'kdesu' the entire thing) and revert to 'nobody'-user permissions when root is not needed. The issues mentioned would have to be solved first, though, and we'd most likely have to remove the possibility of doing the build directly from a user-provided directory containing the source tree; instead, we'd always have to create a temporary directory for the build and copy everything there.

---

### Post by abhijeetmaharana on 2007-08-01
Cool!!! That looks like a roadmap for what can be done. And lots of efforts have been put in creating it!!! Very good details in one place. We will definitely need to use it as reference as we move ahead.

I guess tackling the 'required dependency detection' issue would be the obvious place to start. It was also to be the focus of our efforts after Beta3. 

A very crude observation in this regard. An AC_MSG_ERROR "associated" with a PKG_CHECK_MODULES is an indication of a required dependency. The "associated" word is dangerous here since I found that there is NO uniformity in how this is used, Pidgin's configure has it as the 3rd/4th part of PKG_CHECK_MODULES whereas rhythmbox-configure.ac sets a flag in PKG_CHECK_MODULES and then tests this flag to call an AC_MSG_ERROR. So although it looks like if we could associate these two, we have what we want; associating them doesn't seem very straightforward to me. **Do you ppl have any thoughts if this might be feasible?** Otherwise, we can drop this.

(Configure files are in the attachment in Leibowitz's post: [http://ubuntuforums.org/showpost.php?p=2949175&postcount=62](http://ubuntuforums.org/showpost.php?p=2949175&postcount=62))

Regarding the choice of language, I was thinking of a package management software, like Paco ([http://paco.sourceforge.net/](http://paco.sourceforge.net/)), which would allow users to keep track of the software they have installed using GISA and where the installation files are which can be used to uninstall (that is, if we use make uninstall). Bash script would be difficult for this purpose and it could easily become unmaintainable. I have tried to organize the Java code into packages so that we can plug in modules when required with minimum refactoring. This also keeps the doors open for the possibility of handling packages other than Autoconf ones. Thats way ahead but theres no harm in planning beforehand. Either of Python/Java would be fine for accomodating such features and the debate continues....:-)

We already had a discussion on these:
> 
The program should need as little installation as possible, and a dependency on Java is quite a big dependency. Other languages like Python or, for that matter, plain shell scripting, don't have this issue, as they're included by default in Ubuntu (and just about every other distribution)

Agree with you on this one. But I am counting on the fact that installing Sun Java is a single 'sudo apt-get install' now and the possibility that Java will come bundled with later versions.
> 
I can't help thinking that the program will have to make heavy use of regular expressions, and often execute external programs and make use of their stdin/stdout/stderr. Thus, a language that makes this sort of things easy would be preferable.

We have this already. Incorporating regular expressions is easy. Figuring out the correct expressions is the tough part.
> 
A Java GUI will only be a native (GNOME or KDE) one if one writes ad-hoc code that links to wrapper, which, besides, would bring in even more dependencies.

If you are talking about the looks, Swing's pluggable look and feel should be decent. Look at the screenshots of Beta 2.

---

### Post by LjL on 2007-08-02
Now I've read through this thread a bit more carefully than I had before, although I still haven't really looked at GISA's code, or tried it, so please forgive any mistakes.

If my understanding is correct, GISA takes a quite different approach from AutoDeb: it actually digs into 'configure' and tries to parse it and find dependencies from there, is this correct?
It's an interesting approach, I didn't think it was possible to get enough useful information that way.
Maybe it would be possible to combine the two approaches - parsing 'configure' and intercepting filesystem calls - to obtain a more accurate estimation of dependencies...?

Also, as **leibowitz** said, it's hard to make something fully automated that will work *reliably* with most source trees, and I see that, for this reason, GISA is taking an interactive approach, stopping to ask the user if its guesses are right, or what package to choose when there are several candidates, etc.
AutoDeb here uses the completely opposite approach of being completely non-interactive, at the cost of failing on a large percentage of builds.

My rationale here, though, is:
- An "advanced" user can just do everything manually
- A "novice" user won't have a clue what to do when presented with a choice of dependencies or the like, whether or not it's a GUI like GISA's or a manual build.
- An "intermediate" user will probably benefit from GISA's approach, but it would probably still be possible (though probably make things slower) to fall back to the "GISA approach" when complete automation fails
- An "advanced" user who can't waste time constantly looking at the build should like AutoDeb's "start and forget" approach; if it fails, well, they'll just have to waste time doing it manually.

Do you think it'd be a workable/worthwhile approach to make everything automated and non-interactive by default, and revert to an interactive mode when automation fails?


**abhijeetmaharana**,
> Regarding the choice of language, I was thinking of a package management software, like Paco ([http://paco.sourceforge.net/](http://paco.sourceforge.net/)), which would allow users to keep track of the software they have installed using GISA and where the installation files are which can be used to uninstall (that is, if we use make uninstall). Bash script would be difficult for this purpose and it could easily become unmaintainable.

I didn't know about Paco, but isn't this, basically, checkinstall without the .deb part? It uses LD_PRELOAD to intercept filesystem calls, just like checkinstall does (and auto-apt, too).

Checkinstall has the advantage that it creates a proper (well, "almost" proper) .deb package instead of using its own mini package management... and i think it *is* maintained: see for instance the Ubuntu bug #45763.

> But I am counting on the fact that installing Sun Java is a single 'sudo apt-get install' now and the possibility that Java will come bundled with later versions.
[...]
If you are talking about the looks, Swing's pluggable look and feel should be decent. Look at the screenshots of Beta 2.

I'm talking about the looks, and I'm not talking about the looks.
Does that Swing pluggable module actually *use* GTK to render GUI elements? Because if it just mimicks the standard look, as soon as you change your theme, it won't match anymore.

Besides, how many non-native-GTK programs (or non-native-Qt, in the case of Kubuntu) have you seen included by default in Ubuntu? Now, maybe GISA will never be included by default, but I think it would be a good idea to work on the assumption that it might.

In any case, a clean separation between engine and interface would make this much less of a problem, I think.


**leibowitz**,
I see that you aren't very fond of auto-apt at all. I understand that perfectly: it's old, unmaintained and quirky.
But don't make the mistake of thinking that my AutoDeb just called auto-apt and let it do its work: it hacked into it quite heavily in an attempt to get some saner behavior.

Still, I've now switched to strace, which is less hackish, more general and maintained.
I still use auto-apt, but just to search for packages; the alternative, apt-file, is *very* slow, which is a show-stopper when you have to search for many files.
(On the other hand, there are some files that auto-apt misses, apparently)

---

### Post by abhijeetmaharana on 2007-08-03
> **LjL said:**
> If my understanding is correct, GISA takes a quite different approach from AutoDeb: it actually digs into 'configure' and tries to parse it and find dependencies from there, is this correct?
...
Maybe it would be possible to combine the two approaches - parsing 'configure' and intercepting filesystem calls - to obtain a more accurate estimation of dependencies...?

Yup. Combining them seems a very good idea. With regards to my post above on relating the two macros in configure, lets see if we can think of something. If there is the slightest possibility of figuring out the required dependencies in advance by this or some other way, that could possibly make the rest of the installation a breeze.

> 
Do you think it'd be a workable/worthwhile approach to make everything automated and non-interactive by default, and revert to an interactive mode when automation fails?

That should be taken care of by a configurable option within the program itself. 

> 
I didn't know about Paco, but isn't this, basically, checkinstall without the .deb part? It uses LD_PRELOAD to intercept filesystem calls, just like checkinstall does (and auto-apt, too).

I meant the interface that Paco offers. People can keep track of what they have installed using it. Whether it uses its own packagement or just creates a deb and makes an entry in its books  which is visible to the user is immaterial. We could present the user with a list of software installed with GISA so that they can uninstall it / do other stuff as appropriate. For this, we need a decent GUI.

> 
Now, maybe GISA will never be included by default, but I think it would be a good idea to work on the assumption that it might. In any case, a clean separation between engine and interface would make this much less of a problem,

I was thinking of Java6 being included by default ;-)
The separation has to be there. Otherwise we won't be able to improve it beyond a certain point.


I will be away from the forums and GISA for quite sometime. Will be able to get back after 26th of this month. However, I will make it a point to stay in sync with what you people come up with.

---

### Post by LjL on 2007-08-04
I will be away too until the first days of September - "away" meaning "reading the forums but not having an Ubuntu machine available to do anything on".

I'm not sure I really see a need for a GUI to list and uninstall GISA-installed packages... I mean, if what gets created are .deb packages, they just need to be tagged appropriately, and then one can use their favorite APT interface to find them. This is secondary, anyway... though in any case I *do* favor creating .deb packages over creating anything else, no matter how they're kept track of by the GUI!

Anyway, to my surprise, yesterday I tried to compile something with AutoDeb (sofsip_cli) and found out that 'pkg-config' doesn't generate any meaningful filesystem calls in an strace log.
I don't understand how this can be, since, well, it *has* to try accessing its .pc files to see if they exist...
So anyway, now I have some little build-system-specific (though pkg-config-specific, not autoconf-specific) checks in AutoDeb, too... though I still do it by checking the strace logs ;-)

---

### Post by brennydoogles on 2007-08-08
It may be possible to use jam to help with your dependency problems. Apparently it scans the c++ to find the dependencies. The website for jam is here: [http://www.perforce.com/jam/jam.html](http://www.perforce.com/jam/jam.html) . Hope that helps!!

---

### Post by slavik on 2007-08-09
I haven't looked at your program (or code) but I would like to ask one thing: how do you compile/build/install the source archive?

---

### Post by thelinuxguy on 2007-08-09
> **slavik said:**
> I haven't looked at your program (or code) but I would like to ask one thing: how do you compile/build/install the source archive?

Didn't get your question. You compile/build/install a GNU source archive by running ./configure followed by make and then a make install.

---

### Post by abhijeetmaharana on 2007-08-09
> **slavik said:**
> I haven't looked at your program (or code) but I would like to ask one thing: how do you compile/build/install the source archive?

GISA extracts the archive to a temporary location and runs the configure script followed by a make and make install. The output of these commands is shown within the GISA window itself. Basically it does what you would normally do at the command prompt after extracting the archive. And we are trying to fit in some code to automate/ease the installation of required dependencies as well. 

The alternatives are:
[list="1"]
[*] Modify Leibowitz's scripts that scan the configure scripts to detect the required dependencies and ignore the optional ones. This is turning out to be quite tricky.
[*] Use strace/auto-apt/etc. to detect the required dependencies when the configure script fails, install them and restart the process. Something similar to AutoDeb by LjL.
[/list]

---

### Post by abhijeetmaharana on 2007-08-09
> **brennydoogles said:**
> It may be possible to use jam to help with your dependency problems. Apparently it scans the c++ to find the dependencies. The website for jam is here: [http://www.perforce.com/jam/jam.html](http://www.perforce.com/jam/jam.html) . Hope that helps!!

Had a quick look at jam and it looks like jam is an alternate build system with its own jamfile. I am not clear how we could put that to use with a GNU package. Any ideas/explanations?

---

### Post by brennydoogles on 2007-08-09
> **abhijeetmaharana said:**
> Had a quick look at jam and it looks like jam is an alternate build system with its own jamfile. I am not clear how we could put that to use with a GNU package. Any ideas/explanations?

Maybe a look at the source code could give you guys some ideas on how to scan for the dependencies. I am not a programmer, but maybe this could give you a new angle for your work.

---

### Post by slavik on 2007-08-09
> **abhijeetmaharana said:**
> GISA extracts the archive to a temporary location and runs the configure script followed by a make and make install. The output of these commands is shown within the GISA window itself. Basically it does what you would normally do at the command prompt after extracting the archive. And we are trying to fit in some code to automate/ease the installation of required dependencies as well. 

The alternatives are:
[list="1"]
[*] Modify Leibowitz's scripts that scan the configure scripts to detect the required dependencies and ignore the optional ones. This is turning out to be quite tricky.
[*] Use strace/auto-apt/etc. to detect the required dependencies when the configure script fails, install them and restart the process. Something similar to AutoDeb by LjL.
[/list]
make install

that is the single reason I already dislike this project, since it WILL mess up dpkg.

---

### Post by thelinuxguy on 2007-08-10
There also seem to be discussions on creating a .deb package and THEN installing it....

---

### Post by abhijeetmaharana on 2007-08-10
> **brennydoogles said:**
> Maybe a look at the source code could give you guys some ideas on how to scan for the dependencies. I am not a programmer, but maybe this could give you a new angle for your work.

Sounds good, Lets see if we can gather something from here.

---

### Post by slavik on 2007-08-10
> **thelinuxguy said:**
> There also seem to be discussions on creating a .deb package and THEN installing it....
I think that would be better.

---

### Post by Steveway on 2007-08-10
Sorry to tell you people.
But your work is mostly a waste of time.
There is allready such a program.
installit!
[http://installit.xfce.org/](http://installit.xfce.org/)

---

### Post by slavik on 2007-08-10
> **Steveway said:**
> Sorry to tell you people.
But your work is mostly a waste of time.
There is allready such a program.
installit!
[http://installit.xfce.org/](http://installit.xfce.org/)
from the page:
> 
STATUS UPDATE

DISCONTINUED! The project is no longer being worked on.


---

### Post by Steveway on 2007-08-10
So what? As far as I can see it it seems to work pretty well.
Well, maybe the code from it can help your project.

---

### Post by abhijeetmaharana on 2007-09-04
Thanks for the link Steve.

Lately, I am finding it difficult to make time for continuing work on this and must admit that I don't have an idea when I will be able to make any further useful contribution in terms of actual code. As such, I thought its best if I put this here. At this point I can't say if and when I will be able to rejoin. Maybe someone could adopt my part so that the project continues?

---

