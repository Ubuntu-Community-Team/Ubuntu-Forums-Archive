---
title: "How to update aMule??"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by Agusia on 2012-02-17
Hi All. :)
When i turn on aMule it says: "There is a newer version available." How to update it??

---

### Post by wolfen69 on 2012-02-17
There is a .tar file available [here]("http://www.amule.org/").

---

### Post by Agusia on 2012-02-17
> **wolfen69 said:**
> There is a .tar file available [here]("http://www.amule.org/").
I have downloaded aMule-2.3.1.tar.bz2 but I don't know what to do with it. :(

---

### Post by Lalaith on 2012-02-17
Hi, 

have you tried going to the folder where the package is and right-click on it? I think you can "unzip" it this way.

I think you can also do it from the terminal, navigating again to the folder where the file is and typing 

```
 tar -xvf filename.tar.bz2 
```
I'm not 100% sure though, it's what I've seen surfing here and there ;-)

Hope it helps!

---

### Post by Agusia on 2012-02-17
I have unpacked it but what to do with it next??

---

### Post by raja.genupula on 2012-02-17
look at the contents of that extraction , does it having anything like readme.txt or install.txt .if yes then it will have the installation process . 

for better help post the contents of that file here .

---

### Post by Agusia on 2012-02-17
There is a file: README.Debian-Packages

This debian rules file controls the buildprocess of the packages of aMule you can either run
dpkg-buildpackage -us -uc -b -rfakeroot
to build them all, or you can invoke debian/rules directly with the target you want to be build. If you run
debian/rules without a target, or with the target help, this help will be printed. Other possible targets
are listed below, you can combine them as you need. amule-common, the packages with the skins and
i18n-en-gb are build everytime. The Theme for the webserver get build when you build the
webserver.

amule			Builds the normal GUI-Version of aMule
ed2k			Builds the ed2k-client of aMule
cas			Builds the cas binary for commandline statistics
wxcas			Builds the graphical version of cas
webserver		Builds the webserver for controlling aMule
remotegui		Builds the remote GUI for controlling aMule
daemon			Builds the daemonized version of aMule
alcc			Builds the ed2k-link-creation utility of aMule
alc			Builds the graphical version of alcc
amulecmd		Builds the commandline-client for controlling aMule
xas			Enables the creation of the xas package
plasmamule		Enables creation of plasma specific parts
amule-dbg		Creates the debugging symbols for the amule binary
ed2k-dbg		Creates the debugging symbols for the ed2k binary
cas-dbg			Creates the debugging symbols for the cas binary
wxcas-dbg		Creates the debugging symbols for the wxcas binary
webserver-dbg		Creates the debugging symbols for the amuleweb binary
remotegui-dbg		Creates the debugging symbols for the amulegui binary
daemon-dbg		Creates the debugging symbols for the amuled binary
alcc-dbg		Creates the debugging symbols for the alcc binary
alc-dbg			Creates the debugging symbols for the alc binary
amulecmd-dbg		Creates the debugging symbols for the amulecmd binary
plasmamule-dbg		Creates the debugging symbols for the plasmamule stuff
amule-utils		Creates the Metapackage for the commandline utilities and all these utils
			* alcc
			* amulecmd
			* cas
amule-utils-gui		Creates the Metapackage for the graphical utilities and all these utils
			* alc
			* remotegui
			* wxcas
i18n-<lang>		Builds the coresponding i18n-packge. Lang has to be one of ar, ast, bg, ca, cs,
			da, de, el, es, et-ee, eu, fi, fr, gl, he, hr, hu, it, it-ch, ja, ko-kr, lt, nl,
			nn, pl, pt-br, pt-pt, ro, ru, sl, sq, sv, tr, uk, zh-cn or zh-tw
			If no i18n-package is given, all will be build.
			If you just want en_GB, use i18n-en-only

If one of the -dbg targets is choosen, the corresponding binary will be built, too. In this case,
debugging is enabled, optimising is disabled. Is no -dbg target choosen, debugging is disabled, 
optimising is enabled.

If you choose to just build a few packages, you have to explicit activate ed2k or xas if 
you want to get the pkg's

The targets can be given in any order and combination

---

### Post by raja.genupula on 2012-02-18
hi please post the content of  the tar extraction .

---

### Post by Agusia on 2012-02-18
Here it is:

---

### Post by raja.genupula on 2012-02-18
cool 
ok now cd to that folder from terminal and then do these one by one  and if you got anything please post here .

```
./configure
make
sudo make install 
```

all the best . :D

---

### Post by Agusia on 2012-02-18
agusia@Acer:~/aMule-2.3.1$ ./configure
bash: ./configure: Brak dost&#281;pu
agusia@Acer:~/aMule-2.3.1$
In english:
bash: ./configure: Brak dost&#281;pu = Access denied

What to do?? :(

---

### Post by raja.genupula on 2012-02-18
hmm ok , try with this . 
chmod +x configure
and then do those steps . lemme know if anything comes up

---

### Post by Agusia on 2012-02-18
agusia@Acer:~/aMule-2.3.1$ chmod +x configure
agusia@Acer:~/aMule-2.3.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking if this is a FreeBSD 4 or earlier system... no
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for gawk... (cached) mawk
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether make sets $(MAKE)... (cached) yes
checking for flex... no
checking for lex... no
checking for ranlib... ranlib
checking for bison... no
checking for byacc... no
checking for ranlib... (cached) ranlib
checking for strip... strip
checking for ar... ar
checking for ld... ld
checking for zlib >= 1.1.4... no
configure: error: zlib >= 1.1.4 is required for aMule
agusia@Acer:~/aMule-2.3.1$

---

### Post by raja.genupula on 2012-02-18
ok now open synaptic and in seach box type zlib and check what version it gives , if its giving you required version then install it from there  and then try again .

---

### Post by Agusia on 2012-02-18
checking for wx-config... no
configure: error: 
		wxWidgets must be installed on your system but wx-config
		script couldn't be found. Please check that wx-config is
		in path or specified by --with-wx-config=path flag, the
		directory where wxWidgets libraries are installed (returned
		by 'wx-config --libs' command) is in LD_LIBRARY_PATH or
		equivalent variable and wxWidgets version is 2.8.12 or above.

---

### Post by raja.genupula on 2012-02-18
sudo apt-get install wxWidgets

or look for it in software center 

install it from that command and ty again ,small suggestion to you my friend .  please read what its giving you . so you can understand whats next .

---

### Post by Agusia on 2012-02-18
> **raja.genupula said:**
> sudo apt-get install wxWidgets
Cannot find wxWidgets package. :(

---

### Post by raja.genupula on 2012-02-18
[http://wiki.wxwidgets.org/Installing_and_configuring_under_Ubuntu](http://wiki.wxwidgets.org/Installing_and_configuring_under_Ubuntu)

look at that

---

