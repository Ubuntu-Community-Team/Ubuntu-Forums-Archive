---
title: "CouchDB make &amp;&amp; install error"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by xclusive327 on 2012-03-08
Hi all,

I'm new to the forums but I've been using Ubuntu for a couple of years now. I'm not sure if this is the right thread to post this in but I'm going to anyway. I've been following this tutorial: [http://wiki.apache.org/couchdb/Installing_on_Ubuntu](http://wiki.apache.org/couchdb/Installing_on_Ubuntu)

and ran into some problems after running "sudo make install"


make[3]: *** [mochifmt.beam] Error 1
make[3]: Leaving directory `/home/mike/Documents/apache-couchdb-1.1.1/src/mochiweb'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mike/Documents/apache-couchdb-1.1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mike/Documents/apache-couchdb-1.1.1'
make: *** [all] Error 2

Can anyone help please? Thanks.

---

### Post by kevdog on 2012-03-08
Need more output than what you provided.

---

### Post by xclusive327 on 2012-03-08
Well I followed step-by-step from that guide I linked above. I ran into problems after trying to run "make" and "sudo make install". I'm pretty sure it shouldn't matter where the CoachDB files should be stored because it's in Documents. Initially I had CoachDB 1.0.1 installed correctly and was able to check with localhost. The things I need to requires 1.1.1 or later and this seemed like the only way to get it because the repo's had only 1.0.1. I went back and forth with getting the required tools to install coachDB and re-ran the commands and it worked but I think thats where the problem sprung up. I'm not really sure.

---

### Post by azmyth on 2012-03-08
Did you run ./configure and if so did you notice any errors. Try re-running configure as it can be easy to miss errors.

---

### Post by xclusive327 on 2012-03-08
ran ./configure --prefix=/home/mike/Documents/


mike@qosmio:~/Documents/apache-couchdb-1.1.1$ ./configure --prefix=/home/mike/Documents/
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking whether ln -s works... yes
checking for pthread_create in -lpthread... yes
checking for JS_NewContext in -lmozjs185... yes
checking jsapi.h usability... yes
checking jsapi.h presence... yes
checking for jsapi.h... yes
checking whether JSOPTION_ANONFUNFIX is declared... yes
checking for JS_NewCompartmentAndGlobalObject in -lmozjs185... yes
checking for JS_ThrowStopIteration in -lmozjs185... yes
checking for JS_GetStringCharsAndLength in -lmozjs185... yes
checking for JSScript*... no
checking for icu-config... /usr/bin/icu-config
checking for ICU >= 3.4.1... yes
checking ICU_CFLAGS... -g -Wall -O2 -Wall -ansi -pedantic -Wshadow -Wpointer-arith -Wmissing-prototypes -Wwrite-strings -Wno-long-long   
checking ICU_CXXFLAGS... -g -Wall -O2 -W -Wall -ansi -pedantic -Wpointer-arith -Wwrite-strings -Wno-long-long   
checking ICU_LIBS...  -ldl -lm   -L/usr/lib -licui18n -licuuc -licudata  -ldl -lm   
checking for curl-config... /usr/bin/curl-config
checking for curl >= 7.18.0... yes
checking CURL_CFLAGS... 
checking CURL_LIBS... -L/usr/lib/i386-linux-gnu -lcurl -Wl,-Bsymbolic-functions
checking for erl... /usr/bin/erl
checking for erlc... /usr/bin/erlc
checking erl_driver.h usability... yes
checking erl_driver.h presence... yes
checking for erl_driver.h... yes
checking for help2man... /usr/bin/help2man
checking location of init directory... ${sysconfdir}/init.d
checking location of launchd directory... not found
configure: creating ./config.status
config.status: creating Makefile
config.status: creating bin/couchdb.tpl
config.status: creating bin/couchdb.bat.tpl
config.status: creating bin/Makefile
config.status: creating etc/couchdb/Makefile
config.status: creating etc/couchdb/default.ini.tpl
config.status: creating etc/default/Makefile
config.status: creating etc/init/couchdb.tpl
config.status: creating etc/init/Makefile
config.status: creating etc/launchd/org.apache.couchdb.plist.tpl
config.status: creating etc/launchd/Makefile
config.status: creating etc/logrotate.d/couchdb.tpl
config.status: creating etc/logrotate.d/Makefile
config.status: creating etc/windows/Makefile
config.status: creating etc/Makefile
config.status: creating share/Makefile
config.status: creating src/Makefile
config.status: creating src/couchdb/couch.app.tpl
config.status: creating src/couchdb/Makefile
config.status: creating src/couchdb/priv/Makefile
config.status: creating src/erlang-oauth/Makefile
config.status: creating src/etap/Makefile
config.status: creating src/ibrowse/Makefile
config.status: creating src/mochiweb/Makefile
config.status: creating test/Makefile
config.status: creating test/bench/Makefile
config.status: creating test/etap/Makefile
config.status: creating test/etap/test_util.erl
config.status: creating test/javascript/Makefile
config.status: creating test/view_server/Makefile
config.status: creating utils/Makefile
config.status: creating var/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands

You have configured Apache CouchDB, time to relax.

Run `make && sudo make install' to install.

Looks like there's no errors.

---

### Post by azmyth on 2012-03-09
Okay, that looks good. You do a make command and you don't get any errors?

Can you post more of the error after you do the sudo make install?

Probably best to do them separate so don't do make && sudo make install

make

then 

sudo make install

---

### Post by xclusive327 on 2012-03-09
Never mind I got it. Went with another tutorial and installed CouchDB 1.3.0a. Thanks anyway.

---

### Post by Ernst Ernst on 2012-05-22
Hi,

if you want to get the couchdb 1.2 running, then try to install the erlang-eunit package. This solved the problem on my machine.

sudo apt-get install erlang-eunit

bye
Ernst

---

### Post by jimschubert on 2012-07-14
I had to install erlang-nox for this to work (which included erlang-eunit).

---

