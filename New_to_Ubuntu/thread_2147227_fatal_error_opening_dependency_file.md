---
title: "fatal error: opening dependency file????"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by SleepyDragon on 2013-05-21
Hi there, 

Completely new to Ubuntu, and loving it so far.  

Have a bit of a problem compiling a programs GUI, the program in question is agbx360.  So far i have managed to install the program itself with no problems:), but i cant get past this problem and i am hoping someone can help me, because i really am not sure how to solve it.

I did try to restart the system and try again to install the gui but with no success.  I came across a command on the web, i think it was 'dist' or something similar but that did not help either.

Here is what is says in the terminal:





jay@DVL:~$ sudo apt-get install libwxgtk2.8-dev xterm
[sudo] password for jay: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libwxgtk2.8-dev is already the newest version.
xterm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 175 not upgraded.
jay@DVL:~$ cd /home/jay/abgxgui/
jay@DVL:~/abgxgui$ sudo ./configure && make
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking for ANSI C header files... (cached) yes
checking for memset... yes
checking for wx-config... /usr/bin/wx-config
checking for wxWidgets version >= 2.7.1... yes (version 2.8.12)
checking for wxWidgets static library... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
make  all-am
make[1]: Entering directory `/home/jay/abgxgui'
g++ -DHAVE_CONFIG_H -I.  -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -I/usr/lib/x86_64-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -g -O2  -g -O2  -MT abgx360gui-abgx360gui.o -MD -MP -MF .deps/abgx360gui-abgx360gui.Tpo -c -o abgx360gui-abgx360gui.o `test -f 'src/abgx360gui.cpp' || echo './'`src/abgx360gui.cpp
src/abgx360gui.cpp:2590:1: fatal error: opening dependency file .deps/abgx360gui-abgx360gui.Tpo: Permission denied
compilation terminated.
make[1]: *** [abgx360gui-abgx360gui.o] Error 1
make[1]: Leaving directory `/home/jay/abgxgui'
make: *** [all] Error 2
jay@DVL:~/abgxgui$ 


Please help me:confused:

---

### Post by SleepyDragon on 2013-05-21
Forgot to mention, Im running ubuntu 12.04 LTS 64bit

---

### Post by steeldriver on 2013-05-21
sounds like you have messed up ownership and/or permissions in /home/jay/abgxgui - if you got it from a tarball it may be easiest to delete and untar again (maybe you untarred it as root last time?) or you can fix it with chown / chmod as appropriate

---

### Post by SleepyDragon on 2013-05-21
Hi,

Thanks for replying,  

ok, so how would i go about changing the permisson? like i said completely new to all of this, so not sure how i would do that.:confused:

---

### Post by diesch on 2013-05-21
```
sudo ./configure && make
``` runs *./configure* as root and *make* as ordinary user, which causes your permission problem. 
You actually should not run neither ./configure nor make as root.

Run
```
sudo make clean
```
to revove anything created so far and then
```
./configure && make
```
without *sudo*

---

### Post by SleepyDragon on 2013-05-21
Run
```
sudo make clean
```
to revove anything created so far and then
```
./configure && make
```
without *sudo*[/QUOTE]

Hi, thanks for your reply as-well, i have just tried as suggested and got back:


jay@DVL:~/abgxgui$ ./configure && make
./configure: line 1397: config.log: Permission denied
./configure: line 1407: config.log: Permission denied


:confused:

---

### Post by diesch on 2013-05-21
Did you run ```
sudo make clean
```

If you still get permission errors you ma ytry
```
sudo chown -R $USER .
```
or remove *./abgxgui* and unpack the sources again.

---

### Post by SleepyDragon on 2013-05-21
Hi,

I followed those commands and it resolved the problem, the gui now runs.:)

May i take this opportunity to thank you kindly for you help and patience with a 'noob' 

Cheers Sleepy.

---

### Post by diesch on 2013-05-21
> **SleepyDragon said:**
> H
May i take this opportunity to thank you kindly for you help and patience with a 'noob' 

You're welcome. Try to spread what you've learned to make the world a place with people knowing more about ./configure, make and sudo.Maybe it's not that much, but it's something to start with to make the world a better place.  With a better understanding of Linux at least  ;-)

---

