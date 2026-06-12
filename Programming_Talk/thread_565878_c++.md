---
title: "c++"
date: 2007-10-02
forum: Programming Talk
---

### Post by pooper on 2007-10-02
Hi I'm studying c++ for uni at the moment.
this might seem a stupid question. sorry.

at uni i've been using fedora, gedit to write .cc files and compiling them in terminal. 
I tried doing the same (g++ file.cc -o file) on my own ubuntu/kubuntu machine and get this result

The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: g++: command not found

ive just now installed g++ but what is this pentium-builder and 'universe' component ?

---

### Post by coffecup1978 on 2007-10-02
You just have to install the g++/gcc package, either use apt-get as they shey in bash or synaptis.

---

### Post by slavik on 2007-10-02
universe is a repository, pentium-builder is a package. I would also suggest install build-essential instead.

---

### Post by pooper on 2007-10-02
ok im new to all this, including linux.

what is a repository?
and package?
and build essential?

hehe sorry, I've done a little c on windows and bit of java on mac and now started c++ on linux, but only fiddled with the basics, helloworld and strings...

---

### Post by slavik on 2007-10-02
a repository is just that a repository (synonym: storage place)

a package is just a package that has "stuff" ... essentially, think of a deb file as a zip file with specific file layour inside (like a jar file from Java, or msi from Microsoft).

packages can have dependency, eg: A needs B to be installed in order for A to get installed, even though A might not contain anything at all (besides the requirement). packages such as this are called meta packages.

an example: packages providing pidgin (or gaim) need the gtk libraries to be installed (which also come inside of a package).

build-essential is an empty package that depends on the packages providing C, C++ compilers and their standard libraries ... and more things.

---

### Post by jfinkels on 2007-10-02
> **pooper said:**
> ok im new to all this, including linux.

what is a repository?
and package?
and build essential?

hehe sorry, I've done a little c on windows and bit of java on mac and now started c++ on linux, but only fiddled with the basics, helloworld and strings...

A repository is a centralized location (usually hosted by a web server, but not necessarily) from which you can download software packages.

A package (on Ubuntu, usually ending in .deb) is a grouping of pre-compiled (if necessary) files required to run a program, wrapped up with metadata including their respective installation locations, dependencies, version number, date of publication, etc.

"build-essential" is a so-called "meta-package" that doesn't contain any files to be installed, but merely 'depends on' other packages. As a result of installing build-essential, aptitude, the program we use on Debian-derivative distributions (including Ubuntu) for installing packages from repositories, will automatically resolve these dependencies, inform you, and install the packages that the build-essential meta-package depends on. Essentially, selecting build-essential for installation simply points to a bunch of other packages that subsequently get installed.

Installing build-essential supplies you with gcc (the GNU C compiler), g++ (The GNU C++ compiler), and a bunch of standard C libraries, among other things.

To enable repositories, open "System > Administration > Software Sources" or uncomment lines in your /etc/apt/sources.list file.

See the first link in my signature for more information on installing software in Ubuntu.

---

### Post by pooper on 2007-10-02
ok thanks people for clearing that up for me, i get it now. I'm sure it will also come in handy for the course im studying at uni \\:D/

---

### Post by jfinkels on 2007-10-03
> **pooper said:**
> ok thanks people for clearing that up for me, i get it now. I'm sure it will also come in handy for the course im studying at uni \\:D/

Yep.

I too am a student of computer science and I can attest that using Linux as my production system has really helped me in understanding my courses.

---

