---
title: "help compiling. Easy question?"
date: 2009-10-31
forum: Packaging and Compiling Programs
---

### Post by snowguy on 2009-10-31
really don't know how to compile. I had a thread [http://ubuntuforums.org/showthread.php?p=8206599](http://ubuntuforums.org/showthread.php?p=8206599) but didn't get any help on how to compile so hoping if I ask in this forum someone who know how will help.

My Problem:
I have tried compiling extundelete (source here: [http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/)) and ext3grep (source here: [http://code.google.com/p/ext3grep/](http://code.google.com/p/ext3grep/) under featured downloads) both seem to work but when I actually try to execute them I get "command not found."
My guess is that the problem is something simple because I haven't compiled a program before (with the exception of the simple c class I took in college ages ago) so I don't know what I'm doing. 

Not sure what I'm doing wrong. I'm using Ubuntu 9.04. I have installed
```

sudo apt-get install build-essential
sudo apt-get install checkinstall

```
and, per the extundelete readme, 
```

sudo apt-get install e2fslibs-dev

```

Here are the steps I used to install extundelete:
1. Downloaded extundelete-0.1.8.tar.bz2
2. extracted folder extundelte-0.1.8 to desktop using archive manager
3. Using terminal:
```

xxx@xxx:~$ cd Desktop
xxx@xxx:~/Desktop$ cd extundelete-0.1.8
xxx@xxx:~/Desktop/extundelete-0.1.8$ cd src
xxx@xxx:~/Desktop/extundelete-0.1.8/src$ make
g++ -I. -g -W -Wall -Wredundant-decls -Wshadow -Woverloaded-virtual -Wpointer-arith -Wwrite-strings -c -o extundelete.o `test -f 'extundelete.cc' || echo './'`extundelete.cc
g++ -I. -g -W -Wall -Wredundant-decls -Wshadow -Woverloaded-virtual -Wpointer-arith -Wwrite-strings -c -o block.o `test -f 'block.c' || echo './'`block.c
g++ -I. -g -W -Wall -Wredundant-decls -Wshadow -Woverloaded-virtual -Wpointer-arith -Wwrite-strings -c -o insertionops.o `test -f 'insertionops.cc' || echo './'`insertionops.cc
g++ -o extundelete  extundelete.o block.o insertionops.o -lext2fs
xxx@xxx:~/Desktop/extundelete-0.1.8/src$ extundelete --help
bash: extundelete: command not found
xxx@xxx:~/Desktop/extundelete-0.1.8/src$ 

```

Here are the steps I used to install ext3grep:
1. Downloaded ext3grep-0.10.1.tar.gz
2. extracted folder ext3grep-0.10.1 to desktop using archive manager
3. opened the ext3grep-0.10.1 on my desktop using nautilus and executed configure.
4. Using terminal:
```

xxx@xxx:~/Desktop$ cd ext3grep-0.10.1
xxx@xxx:~/Desktop/ext3grep-0.10.1$ cd src
xxx@xxx:~/Desktop/ext3grep-0.10.1/src$ make
make  all-am
make[1]: Entering directory `/home/xxx/Desktop/ext3grep-0.10.1/src'
make[1]: Leaving directory `/home/xxx/Desktop/ext3grep-0.10.1/src'
xxx@xxx:~/Desktop/ext3grep-0.10.1/src$ ext3grep --help
The program 'ext3grep' is currently not installed.  You can install it by typing:
sudo apt-get install ext3grep
bash: ext3grep: command not found

```

---

### Post by s3a on 2009-10-31
I've succesfully created .deb files from source before with other programs (that have an older version in the repositories) by doing:

[B]1) cd _/home/deniz/Acetoneiso_2.0.3.2_
2) dh_make --createorig
3) sudo apt-get build-dep _packagename_
4) dpkg-buildpackage[/B]

(Whatever is underlined is what you have to change)

---

### Post by snowguy on 2009-10-31
I tried this. It didn't work results below. I tried to just put in the relevant parts but if someone wnats to see the whole thing let me know:

```

xxx@xxx:~$ cd Desktop/extundelete-0.1.8
xxx@xxx:~/Desktop/extundelete-0.1.8$ sudo apt-get install dh-make
...
Setting up dh-make (0.47) ...
xxx@xxx:~/Desktop/extundelete-0.1.8$ dh_make --createorig

Type of package: single binary, multiple binary, library, kernel module, kernel patch or cdbs?
 [s/m/l/k/n/b] s

...
Currently there is no top level Makefile. This may require additional tuning.
Done. Please edit the files in the debian/ subdirectory now. You should also
check that the extundelete Makefiles install into $DESTDIR and not in / .

```
Note: I didn't do any of the above as I wasn't sure how.
```

xxx@xxx:~/Desktop/extundelete-0.1.8$ sudo apt-get build-dep extundelete
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for extundelete

```
I then wondered if maybe I should have been running this from the src sub-directory but when I tried that it didn't seem to work either.
```

xxx@xxx:~/Desktop/extundelete-0.1.8$ dpkg-buildpackage
dpkg-buildpackage: error: fakeroot not found, either install the fakeroot
package, specify a command with the -r option, or run this as root
xxx@xxx:~/Desktop/extundelete-0.1.8$ sudo dpkg-buildpackage
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package extundelete
dpkg-buildpackage: source version 0.1.8-1
dpkg-buildpackage: source changed by xxx <xxx@unknown>
dpkg-buildpackage: host architecture amd64
 debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[1]: Entering directory `/home/xxx/Desktop/extundelete-0.1.8'
make[1]: *** No rule to make target `clean'.  Stop.
make[1]: Leaving directory `/home/xxx/Desktop/extundelete-0.1.8'
make: *** [clean] Error 2
dpkg-buildpackage: failure: debian/rules clean gave error exit status 2

```
I'm sure there must be something simple I'm doing wrong. I just with I knew what it was!

---

### Post by s3a on 2009-10-31
Before doing dpkg-buildpackage, you need the build dependencies and since an older version is not in the repositories, you cannot obtain them easily with apt-get build-dep. I have somewhat of a similar dilemma for software that has no older version in the repositories but if you can figure out what each build-depency is and install it yourself manually then dpkg-buildpackage should work and create .deb files for you.

---

### Post by snowguy on 2009-11-01
Going back to my original post, you think that the reason the build isn't working in my case is because the dependencies aren't met? If that is the case is the result that would be expected that when I ran the command ext3grep I would get ext3grep: command not found?

I realize I don't understand this but I would have expected to find ext3grep and try to run it, if I had compiled it correctly but lacked the necessary dependencies. I just want to make sure I'm working on solving the correct problem.

---

### Post by Yellow Pasque on 2009-11-01
You're building from source, correct? You probably need to run a ./configure command to generate a Makefile.

---

