---
title: "having trouble with wireless 3g. need help installing right packages/what have you"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by danny_galaga on 2008-11-08
i have hardy heron. how do i go about getting my 3g wireless braodband up and running? my linux box isnt connected to the net. it dual boots xp, but for some reason the wireless isnt working on that. i dont care so long as it works in linux (",)

i have downloaded NetworkManager-0.7.0-rc1.tar.gz  

is this what i should be using to get it going? and if so, how to install? the install file has some generic instructions. ive only ever used the synaptic package manager while online to install stuff so i really dont understand what it is im trying to acheive in the terminal

it says something about ./configure; make; make install in the install file

if i type that into the terminal and insert NetworkManager-0.7.0 after that it doesn't work. what is the format i should be following? ive also tried ./configure NetworkManager-0.7.0 since i realised that ./configure; make; make install is probably 3 instructions! still no go.
the 3g usb thingo itself is working fine. i have borrowed my housemates vista laptop to get online

---

### Post by danny_galaga on 2008-11-09
ok, ive gotten my head around a few concepts. managed to get to the ./configure stage. here is what i get:


danny@danny-desktop:~$ cd /home/danny/networkmanager-0.7.0
bash: cd: /home/danny/networkmanager-0.7.0: No such file or directory
danny@danny-desktop:~$ cd /home/danny/NetworkManager-0.7.0
danny@danny-desktop:~/NetworkManager-0.7.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for unistd.h... (cached) yes
checking for mode_t... yes
checking for pid_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for working memcmp... yes
checking for select... yes
checking for socket... yes
checking for uname... yes
checking for intltool >= 0.35.0... 0.37.1 found
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
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
checking whether byte ordering is bigendian... no
checking for /etc/redhat-release... no
checking for /etc/SuSE-release... no
checking for /etc/fedora-release... no
checking for /etc/gentoo-release... no
checking for /etc/debian_version... yes
checking for /etc/arch-release... no
checking for /etc/slackware-version... no
checking for /etc/frugalware-release... no
checking for /etc/mandriva-release... no
checking Linux Wireless Extensions >= 18... no
configure: error: wireless-tools >= 28pre9 not installed or not functional
danny@danny-desktop:~/NetworkManager-0.7.0$ make
make: *** No targets specified and no makefile found.  Stop.
danny@danny-desktop:~/NetworkManager-0.7.0$ make NetworkManager-0.7.0
make: *** No rule to make target `NetworkManager-0.7.0'.  Stop.
danny@danny-desktop:~/NetworkManager-0.7.0$ make clean
make: *** No rule to make target `clean'.  Stop.
danny@danny-desktop:~/NetworkManager-0.7.0$ --help No rule to make target 'clean'
bash: --help: command not found
danny@danny-desktop:~/NetworkManager-0.7.0$ --help make
bash: --help: command not found
danny@danny-desktop:~/NetworkManager-0.7.0$ clear

danny@danny-desktop:~/NetworkManager-0.7.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for unistd.h... (cached) yes
checking for mode_t... yes
checking for pid_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for working memcmp... yes
checking for select... yes
checking for socket... yes
checking for uname... yes
checking for intltool >= 0.35.0... 0.37.1 found
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
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
checking whether byte ordering is bigendian... no
checking for /etc/redhat-release... no
checking for /etc/SuSE-release... no
checking for /etc/fedora-release... no
checking for /etc/gentoo-release... no
checking for /etc/debian_version... yes
checking for /etc/arch-release... no
checking for /etc/slackware-version... no
checking for /etc/frugalware-release... no
checking for /etc/mandriva-release... no
checking Linux Wireless Extensions >= 18... no
configure: error: wireless-tools >= 28pre9 not installed or not functional
danny@danny-desktop:~/NetworkManager-0.7.0$ 


i dont know if the bulk of it is good or bad, but obviously the last bit about 28pre9 not being installed doesnt look good...

---

### Post by danny_galaga on 2008-11-11
ok, i had a brainwave and thought i might network to my housemates laptop and just be done with this fiddling around and just update to 8.10. unfortunately, like an idiot ive deleted the existing network manager in ubuntu, thinking that was this thing ive been trying to install. so now i cant figure out how to network the laptop to the pc. 

i tried to reinstall network manager from the disk, but the package manager only seems to recognise cd drives, and my distro is on a dvd! this is turning into a comedy of errors...

any suggestions?

---

### Post by nothingspecial on 2008-11-11
If you can get a wired connection anywhere try wicd. I find it works better on both my laptops than network manager.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

As for your 3g it depends what make and model you have. Some phone companies sell them with linux laptops. Posy what model you have.

---

### Post by danny_galaga on 2008-11-11
well that sounds promising! but my problem is my linux box isnt connectable to the internet at the moment. i did see a 'slackware' page in that link and ive downloaded wicd from there onto my housemates laptop. can i install that onto my linux box with that without internet? i didnt see any instructions on how to. i tried to mimic how i installed NetworkManager-0.7.0 but that didnt get me anywhere.

---

### Post by nothingspecial on 2008-11-11
Wicd  has some dependencies

python-glade2, python-gtk2, wireless-tools, wpasupplicant and dhcp3-client

So you need to install them too.

Not knowing much about slackware, you would be better downloading wicd from here.

[http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573)

This really would be a lot easier if you could get a wired connection somehow.

---

### Post by danny_galaga on 2008-11-14
> **nothingspecial said:**
> If you can get a wired connection anywhere try wicd. I find it works better on both my laptops than network manager.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

As for your 3g it depends what make and model you have. Some phone companies sell them with linux laptops. Posy what model you have.


hey there, i reinstalled ubuntu and managed to get it on a wired network. ive added wicd to the repositories. however when i try to add the key for it i get this:


danny@danny-desktop:~$ wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -0- | sudo apt-key add -
wget: invalid option -- 0
gpg: no valid OpenPGP data found.
danny@danny-desktop:~$ 



note that i havent yet, downloaded all the updates for ubuntu yet. do i need to to add a key? i wouldnt have thought so but you never know...

---

### Post by danny_galaga on 2008-11-14
ok, i downloaded all ubuntu updates last night for 8.04  still get the same result as above:


danny@danny-desktop:~$ wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -0- | sudo apt-key add -
wget: invalid option -- 0
gpg: no valid OpenPGP data found.
danny@danny-desktop:~$


is there something obvious im missing?  now ive been looking at this problem i think id rather stick with heron and use wicd than update to intrepid. from what ive read on these forums, intrepid has gone a little 'vista' in regards networking :lolflag:

---

### Post by nothingspecial on 2008-11-14
What have you done so far?

Can you post 
cat /etc/apt/sources.list

again

---

### Post by danny_galaga on 2008-11-14
danny@danny-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras
danny@danny-desktop:~$

---

### Post by nothingspecial on 2008-11-14
```
gksudo gedit /etc/apt/sources.list
```

Delete the # (comment) from the last line, the one with wicd in it. Then save and close.

Try to add the key again.

---

### Post by danny_galaga on 2008-11-14
hmm, still no joy. i deleted that last line like you said. still get the same message:


danny@danny-desktop:~$ wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -0- | sudo apt-key add -
[sudo] password for danny: wget: invalid option -- 0




i thought id check that sources list again and now it doesnt actually show anything! is that whats supposed to happen?

---

### Post by nothingspecial on 2008-11-14
No, don`t delete anything except the #

---

### Post by danny_galaga on 2008-11-15
*slaps head*

ok, finally downloaded it! thanks for your perseverance (",)

now to see if my dongle thing will work...

---

### Post by danny_galaga on 2008-11-15
hmm, ok wicd is not quite what i was hoping for. this thread talks about my brand of dongle:

[http://ubuntuforums.org/showthread.php?t=858032&highlight=huawei](http://ubuntuforums.org/showthread.php?t=858032&highlight=huawei)

but 'simple' to that guy is not simple for me! besides, there is no linux cd with this dongle. it is an older thread though. is there a simple way for me to get my huawei e169 dongle connected?

edit: ok, this thread has run its course. i think my downfall was i was too vague to start with. i will now start a new, more detailed thread (",)

---

