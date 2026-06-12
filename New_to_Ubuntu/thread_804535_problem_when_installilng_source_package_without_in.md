---
title: "problem when installilng source package without intarnet"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by mitar on 2008-05-23
I am trying to install inkscape program that I downloaded from another PC. It came as inkscape-0.46.tar.gz. I followed the instruction at [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) but at the end I got the message error:libpng >= 1.2 is needed to compile inkscape. The entire code looks like this:

```
stefan@stefan-laptop:~$ cd '/home/stefan/Desktop/inkscape-0.46' 
stefan@stefan-laptop:~/Desktop/inkscape-0.46$ ./configure 
checking build system type... i686-pc-linux-gnu 
checking host system type... i686-pc-linux-gnu 
checking for a BSD-compatible install... /usr/bin/install -c 
checking whether build environment is sane... yes 
checking for a thread-safe mkdir -p... /bin/mkdir -p 
checking for gawk... no 
checking for mawk... mawk 
checking whether make sets $(MAKE)... yes 
checking how to create a pax tar archive... gnutar 
checking for style of include used by make... GNU 
checking for gcc... gcc 
checking for C compiler default output file name... a.out 
checking whether the C compiler works... yes 
checking whether we are cross compiling... no 
checking for suffix of executables...  
checking for suffix of object files... o 
checking whether we are using the GNU C compiler... yes 
checking whether gcc accepts -g... yes 
checking for gcc option to accept ISO C89... none needed 
checking dependency style of gcc... gcc3 
checking for intltool >= 0.22... 0.37.1 found 
checking for xgettext... /usr/bin/xgettext 
checking for msgmerge... /usr/bin/msgmerge 
checking for msgfmt... /usr/bin/msgfmt 
checking for perl... /usr/bin/perl 
checking for XML::Parser... ok 
checking for g++... g++ 
checking whether we are using the GNU C++ compiler... yes 
checking whether g++ accepts -g... yes 
checking dependency style of g++... gcc3 
checking for library containing strerror... none required 
checking whether we are using the GNU C++ compiler... (cached) yes 
checking whether g++ accepts -g... (cached) yes 
checking dependency style of g++... (cached) gcc3 
checking for gcc... (cached) gcc 
checking whether we are using the GNU C compiler... (cached) yes 
checking whether gcc accepts -g... (cached) yes 
checking for gcc option to accept ISO C89... (cached) none needed 
checking dependency style of gcc... (cached) gcc3 
checking dependency style of gcc... gcc3 
checking how to run the C++ preprocessor... g++ -E 
checking for grep that handles long lines and -e... /bin/grep 
checking for egrep... /bin/grep -E 
checking for ANSI C header files... yes 
checking for gcc... (cached) gcc 
checking whether we are using the GNU C compiler... (cached) yes 
checking whether gcc accepts -g... (cached) yes 
checking for gcc option to accept ISO C89... (cached) none needed 
checking dependency style of gcc... (cached) gcc3 
checking whether gcc and cc understand -c and -o together... yes 
configure: Testing -Wno-pointer-sign 
configure:  compiler supports -Wno-pointer-sign 
checking for ranlib... ranlib 
checking GNU compiler version... 4.2.3 
checking for sys/types.h... yes 
checking for sys/stat.h... yes 
checking for stdlib.h... yes 
checking for string.h... yes 
checking for memory.h... yes 
checking for strings.h... yes 
checking for inttypes.h... yes 
checking for stdint.h... yes 
checking for unistd.h... yes 
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
checking for msgfmt... (cached) /usr/bin/msgfmt 
checking for dcgettext... yes 
checking if msgfmt accepts -c... yes 
checking for gmsgfmt... /usr/bin/msgfmt 
checking for xgettext... (cached) /usr/bin/xgettext 
checking for catalogs to be installed...  am ar az be bg bn br ca ca@valencia cs da de dz el en_AU en_CA en_GB en_US@piglatin eo es_MX es et eu fi fr ga gl he hr hu id it ja km ko lt mk mn nb ne nl nn pa pl pt_BR pt ro ru rw sk sl sq sr@latin sr sv th tr uk vi zh_CN zh_TW 
checking for pkg-config... /usr/bin/pkg-config 
checking for msgfmt... (cached) /usr/bin/msgfmt 
checking for gmsgfmt... (cached) /usr/bin/msgfmt 
checking for png_read_info in -lpng... no 
configure: error: libpng >= 1.2 is needed to compile inkscape 
stefan@stefan-laptop:~/Desktop/inkscape-0.46$  
```

I need help with this.

---

### Post by bumanie on 2008-05-23
Difficult without the internet because you are missing a library necessary for the program to be able to compile correctly. Unless libpng 1.2 is on the ubuntu cd (I am at work and can't check) you will have to download it from somwhere and install it before inkscape will be able to compile correctly.

---

### Post by bumanie on 2008-05-23
Remembered i had a usb stick with ubuntu on it. Booted that and it seems that libng 1.2 is on the ubuntu cd. If you enable your software sources to accept the cd-rom as a source, you should be able to add libng 1.2 via synaptic or > sudo apt-get install libng 1.2 

---

### Post by t0p on 2008-05-23
Someone above advised you to install libpng1.2 via apt-get or Synaptic... but as inkscape is also in the repos, why not just install inkscape via apt-get or Synaptic?

However, I suspect you're trying to install inkscape this way because you don't have internet access on the computer you want inkscape on?  If that's the case, what you need to do is:  Go to a computer that *does* have internet access; go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and download libpng1.2 from  there; save to a usb stick or cd; take this home and install to your computer.

I used to have to do this kind of thing, before I got my home computer online, and I gotta tell you: getting new software without internet access is a major pita.  You've already taken your first steps into dependency hell with this libpng issue.  You might find that once you've installed libpng1.2, ubuntu tells you that you need something else! Take this advice: get a cellphone and means to connect it to your pc (datacable, bluetooth, etc); then check out the link in my sig to a tutorial on using a cellphone as a modem.  Connection through a cellphone is slow as heck, but it's better than no connection, believe me!

---

### Post by mitar on 2008-05-23
> **bumanie said:**
> Remembered i had a usb stick with ubuntu on it. Booted that and it seems that libng 1.2 is on the ubuntu cd. If you enable your software sources to accept the cd-rom as a source, you should be able to add libng 1.2 via synaptic or

ok. how do I "enable my software sources to accept the cd-rom as a source"?

---

### Post by mitar on 2008-05-23
> **t0p said:**
> Someone above advised you to install libpng1.2 via apt-get or Synaptic... but as inkscape is also in the repos, why not just install inkscape via apt-get or Synaptic?

However, I suspect you're trying to install inkscape this way because you don't have internet access on the computer you want inkscape on?  If that's the case, what you need to do is:  Go to a computer that *does* have internet access; go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and download libpng1.2 from  there; save to a usb stick or cd; take this home and install to your computer.

I used to have to do this kind of thing, before I got my home computer online, and I gotta tell you: getting new software without internet access is a major pita.  You've already taken your first steps into dependency hell with this libpng issue.  You might find that once you've installed libpng1.2, ubuntu tells you that you need something else! Take this advice: get a cellphone and means to connect it to your pc (datacable, bluetooth, etc); then check out the link in my sig to a tutorial on using a cellphone as a modem.  Connection through a cellphone is slow as heck, but it's better than no connection, believe me!

It seems that libpng isn't among these packages. I'll see what I could do with that cell phone thing.

---

### Post by bumanie on 2008-05-23
To enable software sources to enable cd-rom System --> Administration --> Software Sources. In the box down the bottom of the first screen you see, there will be a box to check to enable the cd-rom. Have it in your cd drive when going into synaptic so that the lib can be found.

---

### Post by mitar on 2008-05-23
> **bumanie said:**
> To enable software sources to enable cd-rom System --> Administration --> Software Sources. In the box down the bottom of the first screen you see, there will be a box to check to enable the cd-rom. Have it in your cd drive when going into synaptic so that the lib can be found.

first it shows me something like an error message (see attachment), but somehow it manages to save settings. However when I run command I get:
```
sudo apt-get install libpng 1.2
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libpng 
```

---

### Post by bumanie on 2008-05-23
Looks as though the repositories are enabled on your system and your computer is trying to hookup to the internet to find the library. Go back to software sources and uncheck all the boxes on the first screen, leaving only the cd-rom checked and try agian. If that doesn't work, I have no more suggestions. As far as I remember, you should be able to download off the cd if you have the cd-rom enabled as a software source. It seems that the computer is trying to go to the repositories instead.

---

### Post by mitar on 2008-05-23
Same thing happened :(

---

### Post by bumanie on 2008-05-23
Silly question, but I guess you have got the live cd in the drive. 
Usually those with the internet, uncheck the cd-rom from the software sources, because the computer tends to look there first. Why it isn't on your computer, I have no idea. Sorry, I can't help any further. You may have to wait until you can get to another computer with the internet and download the libpng 1.2 library independantly.

---

### Post by mitar on 2008-05-23
ok I downloaded libpng and when tried to install, at the end of the code I got

configure: error: zlib not installed

Should I download that too? I am really affraid that I ll mess something.

---

### Post by hessiess on 2008-05-23
You will need to install zlib too, Instaling anything on ubuntu without an internet conection is quite frankly, a nightmere.

---

### Post by mitar on 2008-05-23
After installing libpng 1.2 and zlib, the next problem happened 

```
stefan@stefan-laptop:~$ cd '/home/stefan/Desktop/inkscape-0.46' 
stefan@stefan-laptop:~/Desktop/inkscape-0.46$ ./configure 
checking build system type... i686-pc-linux-gnu 
checking host system type... i686-pc-linux-gnu 
checking for a BSD-compatible install... /usr/bin/install -c 
checking whether build environment is sane... yes 
checking for a thread-safe mkdir -p... /bin/mkdir -p 
checking for gawk... no 
checking for mawk... mawk 
checking whether make sets $(MAKE)... yes 
checking how to create a pax tar archive... gnutar 
checking for style of include used by make... GNU 
checking for gcc... gcc 
checking for C compiler default output file name... a.out 
checking whether the C compiler works... yes 
checking whether we are cross compiling... no 
checking for suffix of executables...  
checking for suffix of object files... o 
checking whether we are using the GNU C compiler... yes 
checking whether gcc accepts -g... yes 
checking for gcc option to accept ISO C89... none needed 
checking dependency style of gcc... gcc3 
checking for intltool >= 0.22... 0.37.1 found 
checking for xgettext... /usr/bin/xgettext 
checking for msgmerge... /usr/bin/msgmerge 
checking for msgfmt... /usr/bin/msgfmt 
checking for perl... /usr/bin/perl 
checking for XML::Parser... ok 
checking for g++... g++ 
checking whether we are using the GNU C++ compiler... yes 
checking whether g++ accepts -g... yes 
checking dependency style of g++... gcc3 
checking for library containing strerror... none required 
checking whether we are using the GNU C++ compiler... (cached) yes 
checking whether g++ accepts -g... (cached) yes 
checking dependency style of g++... (cached) gcc3 
checking for gcc... (cached) gcc 
checking whether we are using the GNU C compiler... (cached) yes 
checking whether gcc accepts -g... (cached) yes 
checking for gcc option to accept ISO C89... (cached) none needed 
checking dependency style of gcc... (cached) gcc3 
checking dependency style of gcc... gcc3 
checking how to run the C++ preprocessor... g++ -E 
checking for grep that handles long lines and -e... /bin/grep 
checking for egrep... /bin/grep -E 
checking for ANSI C header files... yes 
checking for gcc... (cached) gcc 
checking whether we are using the GNU C compiler... (cached) yes 
checking whether gcc accepts -g... (cached) yes 
checking for gcc option to accept ISO C89... (cached) none needed 
checking dependency style of gcc... (cached) gcc3 
checking whether gcc and cc understand -c and -o together... yes 
configure: Testing -Wno-pointer-sign 
configure:  compiler supports -Wno-pointer-sign 
checking for ranlib... ranlib 
checking GNU compiler version... 4.2.3 
checking for sys/types.h... yes 
checking for sys/stat.h... yes 
checking for stdlib.h... yes 
checking for string.h... yes 
checking for memory.h... yes 
checking for strings.h... yes 
checking for inttypes.h... yes 
checking for stdint.h... yes 
checking for unistd.h... yes 
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
checking for msgfmt... (cached) /usr/bin/msgfmt 
checking for dcgettext... yes 
checking if msgfmt accepts -c... yes 
checking for gmsgfmt... /usr/bin/msgfmt 
checking for xgettext... (cached) /usr/bin/xgettext 
checking for catalogs to be installed...  am ar az be bg bn br ca ca@valencia cs da de dz el en_AU en_CA en_GB en_US@piglatin eo es_MX es et eu fi fr ga gl he hr hu id it ja km ko lt mk mn nb ne nl nn pa pl pt_BR pt ro ru rw sk sl sq sr@latin sr sv th tr uk vi zh_CN zh_TW 
checking for pkg-config... /usr/bin/pkg-config 
checking for msgfmt... (cached) /usr/bin/msgfmt 
checking for gmsgfmt... (cached) /usr/bin/msgfmt 
checking for png_read_info in -lpng... yes 
checking png.h usability... yes 
checking png.h presence... yes 
checking for png.h... yes 
checking for shl_load in -ldld... no 
checking for dlopen... no 
checking for dlopen in -ldl... yes 
checking gc.h usability... no 
checking gc.h presence... no 
checking for gc.h... no 
checking gc/gc.h usability... no 
checking gc/gc.h presence... no 
checking for gc/gc.h... no 
configure: error: libgc (the Boehm Conservative Collector) 6.4+, is needed to compile inkscape -- http://www.hpl.hp.com/personal/Hans_Boehm/gc 
```

I can't find this thing (libgc). Actually I think I downloaded (as a deb package) but is says something like "wrong architecture"

NOTE: Does anyone know of some site where I could download Inkscape as a deb or something that doesn't ask for all these lib. stuff.

---

