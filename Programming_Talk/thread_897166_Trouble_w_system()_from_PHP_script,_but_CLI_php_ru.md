---
title: "Trouble w/ system() from PHP script, but CLI php runs it fine"
date: 2008-08-21
forum: Programming Talk
---

### Post by rianjs on 2008-08-21
This leads me to believe it's a permissions problem.

I'm running an scp command via PHP's system() function. Running the script via the CLI php executes it fine; the file is SCP'd.

Running it in my browser does not work. I have public/private key setup, which means no password is required. Here is the script:

```
<?php
	$resizename = "12193688514.jpg";
	system("scp " . $resizename . " [user]@example.com:/remote1/remote2/" . $resizename);
?>
```


This leads me to believe that it is a permissions problem. That scp cannot be called by Apache(?), so it fails. Because the CLI is being run with my user account's permissions, it works fine. Is that about right?

How do I fix this?

---

### Post by jinksys on 2008-08-21
Try the script with the absolute path for the file, does it work then?

---

### Post by rianjs on 2008-08-21
> **jinksys said:**
> Try the script with the absolute path for the file, does it work then? No, and it's getting weirder. I modified the script with some other stuff, like ls and whoami, and it works just fine via the browser. Even system('ls -l > ls.txt'); creates ls.txt with the directory contents, as expected.

It's got to be something super obvious, which is why I'm not seeing it...

---

### Post by jinksys on 2008-08-21
> **rianjs said:**
> No, and it's getting weirder. I modified the script with some other stuff, like ls and whoami, and it works just fine via the browser. Even system('ls -l > ls.txt'); creates ls.txt with the directory contents, as expected.

It's got to be something super obvious, which is why I'm not seeing it...

It's obviously going to find ls, whoami, and even scp since they are in the $PATH.  I meant use an absolute path to the jpeg.

---

### Post by rianjs on 2008-08-21
Yes, I meant that I had done that, and it still doesn't work.

---

### Post by ghostdog74 on 2008-08-21
> **rianjs said:**
> This leads me to believe it's a permissions problem.

I'm running an scp command via PHP's system() function. Running the script via the CLI php executes it fine; the file is SCP'd.

Running it in my browser does not work. I have public/private key setup, which means no password is required. Here is the script:

```
<?php
	$resizename = "12193688514.jpg";
	system("scp " . $resizename . " [user]@example.com:/remote1/remote2/" . $resizename);
?>
```


This leads me to believe that it is a permissions problem. That scp cannot be called by Apache(?), so it fails. Because the CLI is being run with my user account's permissions, it works fine. Is that about right?

How do I fix this?
See [here](http://www.unix.com/linux/49873-php-scp.html) for an example i gave.

---

### Post by rianjs on 2008-08-21
Ugh, of course it's not going to work. I'm running as me, and the script, via the browser, is being run as www-data. The keys were set up with me as the user. I'll have to set them up to work under www-data otherwise it won't work.

Duh.

---

### Post by jinksys on 2008-08-21
> **rianjs said:**
> Ugh, of course it's not going to work. I'm running as me, and the script, via the browser, is being run as www-data. The keys were set up with me as the user. I'll have to set them up to work under www-data to work, too.


ah, touché. Good catch.

---

### Post by rianjs on 2008-08-21
> **ghostdog74 said:**
> See [here](http://www.unix.com/linux/49873-php-scp.html) for an example i gave. Thanks. I had actually experimented with ssh2_scp_send about an hour ago. After getting irritated at not having it work OOTB with php, I opted to try the lazy man's way with exec first. :o

---

### Post by ghostdog74 on 2008-08-21
> **rianjs said:**
>  I opted to try the lazy man's way with exec first. :o

always try to use available libraries first.

---

### Post by rianjs on 2008-08-21
> **ghostdog74 said:**
> always try to use available libraries first. Yes, well, downloading source files is fun, but I have absolutely no idea what to do with them.

The instructions in this link don't work either:
[http://fitxers.oriolrius.cat/2160/howto-ssh-php.html](http://fitxers.oriolrius.cat/2160/howto-ssh-php.html)

I've spent the better part of 30 minutes trying to get the necessary components installed with zero success. I tried that back when I was first looking at ssh2_scp_send, with the same result. That's why I went with system()/exec()

---

### Post by rianjs on 2008-08-21
I am following the installation instructions on this page:
[http://us2.php.net/manual/en/ssh2.installation.php](http://us2.php.net/manual/en/ssh2.installation.php)

1) Install OpenSSL [DONE]
2) Install libssh2 [DONE]
3) Run the pear installer for PECL/ssh2: pear install ssh2 [FAILED]:

```
pear install ssh2
No releases available for package "pear.php.net/ssh2" - package pecl/ssh2 can be installed with "pecl install ssh2"
Cannot initialize 'channel://pear.php.net/ssh2', invalid or missing package file
Package "channel://pear.php.net/ssh2" is not valid
```

So I tried:
```
$ pecl install ssh2
Failed to download pecl/ssh2 within preferred state "stable", latest release is version 0.10, stability "beta", use "channel://pecl.php.net/ssh2-0.10" to install
Cannot initialize 'channel://pecl.php.net/ssh2', invalid or missing package file
Package "channel://pecl.php.net/ssh2" is not valid
```

Tried it with sudo, same error.

So I manually downloaded ssh2-0.10.tgz from [http://pecl.php.net/get/ssh2-0.10.tgz](http://pecl.php.net/get/ssh2-0.10.tgz) Unzipped the archive, etc. Next step:

"Copy ssh2.so from the directory indicated by the build process to the location specified in your php.ini file under extension_dir."

Yeah ok. Lost me there. There's no ssh2.so anywhere to be found. I did "sudo updatedb" then "locate libssh2.so". Then I copied libssh2.so to my extension_dir, again using sudo. restart apache. Oops. libssh2.so != ssh2.so. Scroll back up to see if there was a ssh2.so. Nope. Hmm.

Maybe the problem is because there was no build process run. Since Step 3 was a disaster, it's hardly surprising that the house of cards toppled.

Next, I tried "sudo pecl install ssh2-beta" since there are no stable versions. This was the result:

```
$ sudo pecl install ssh2-beta
downloading ssh2-0.10.tgz ...
Starting to download ssh2-0.10.tgz (22,187 bytes)
........done: 22,187 bytes
5 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20060613
Zend Extension Api No:   220060519
building in /var/tmp/pear-build-root/ssh2-0.10
running: /tmp/pear/cache/ssh2-0.10/configure
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for a sed that does not truncate output... /bin/sed
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking whether gcc and cc understand -c and -o together... yes
checking for system library directory... lib
checking if compiler supports -R... no
checking if compiler supports -Wl,-rpath,... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for PHP prefix... /usr
checking for PHP includes... -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib
checking for PHP extension directory... /usr/lib/php5/20060613
checking for PHP installed headers prefix... /usr/include/php5
checking for re2c... no
configure: WARNING: You will need re2c 0.12.0 or later if you want to regenerate PHP parsers.
checking for gawk... no
checking for nawk... nawk
checking if nawk is broken... no
checking for ssh2 support... yes, shared
checking for ssh2 files in default path... found in /usr
checking for libssh2_banner_set in -lssh2... yes
checking for libssh2_channel_forward_listen_ex in -lssh2... yes
checking for libssh2_userauth_hostbased_fromfile_ex in -lssh2... yes
checking for libssh2_poll in -lssh2... yes
checking for libssh2_publickey_init in -lssh2... yes
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
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
configure: creating ./config.status
config.status: creating config.h
running: make
/bin/bash /var/tmp/pear-build-root/ssh2-0.10/libtool --mode=compile gcc  -I. -I/tmp/pear/cache/ssh2-0.10 -DPHP_ATOM_INC -I/var/tmp/pear-build-root/ssh2-0.10/include -I/var/tmp/pear-build-root/ssh2-0.10/main -I/tmp/pear/cache/ssh2-0.10 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib  -DHAVE_CONFIG_H  -g -O2   -c /tmp/pear/cache/ssh2-0.10/ssh2.c -o ssh2.lo
mkdir .libs
 gcc -I. -I/tmp/pear/cache/ssh2-0.10 -DPHP_ATOM_INC -I/var/tmp/pear-build-root/ssh2-0.10/include -I/var/tmp/pear-build-root/ssh2-0.10/main -I/tmp/pear/cache/ssh2-0.10 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -DHAVE_CONFIG_H -g -O2 -c /tmp/pear/cache/ssh2-0.10/ssh2.c  -fPIC -DPIC -o .libs/ssh2.o
/tmp/pear/cache/ssh2-0.10/ssh2.c: In function &#8216;zif_ssh2_methods_negotiated&#8217;:
/tmp/pear/cache/ssh2-0.10/ssh2.c:481: warning: passing argument 2 of &#8216;libssh2_session_methods&#8217; makes integer from pointer without a cast
/tmp/pear/cache/ssh2-0.10/ssh2.c:481: error: too many arguments to function &#8216;libssh2_session_methods&#8217;
/tmp/pear/cache/ssh2-0.10/ssh2.c: In function &#8216;zif_ssh2_fingerprint&#8217;:
/tmp/pear/cache/ssh2-0.10/ssh2.c:536: warning: assignment discards qualifiers from pointer target type
/tmp/pear/cache/ssh2-0.10/ssh2.c: In function &#8216;zif_ssh2_publickey_add&#8217;:
/tmp/pear/cache/ssh2-0.10/ssh2.c:1038: warning: passing argument 1 of &#8216;_efree&#8217; discards qualifiers from pointer target type
/tmp/pear/cache/ssh2-0.10/ssh2.c: In function &#8216;zif_ssh2_publickey_list&#8217;:
/tmp/pear/cache/ssh2-0.10/ssh2.c:1097: warning: passing argument 4 of &#8216;add_assoc_stringl_ex&#8217; discards qualifiers from pointer target type
/tmp/pear/cache/ssh2-0.10/ssh2.c:1098: warning: passing argument 4 of &#8216;add_assoc_stringl_ex&#8217; discards qualifiers from pointer target type
/tmp/pear/cache/ssh2-0.10/ssh2.c:1106: warning: initialization discards qualifiers from pointer target type
/tmp/pear/cache/ssh2-0.10/ssh2.c:1107: warning: passing argument 2 of &#8216;_zend_hash_add_or_update&#8217; discards qualifiers from pointer target type
make: *** [ssh2.lo] Error 1
ERROR: `make' failed
``` Brilliant. :rolleyes:

It seems I've run into this bug:
[http://pecl.php.net/bugs/bug.php?id=11779](http://pecl.php.net/bugs/bug.php?id=11779)

---

### Post by rianjs on 2008-08-21
Yeah, so I'm completely at a loss, now. I have no f'n clue what to do next.

---

### Post by ghostdog74 on 2008-08-22
I had no problem the last time i used this module. If you can't get any solutions from now on, you could try posting to a real PHP forum instead. you might get more suggestions there.

---

### Post by rianjs on 2008-08-22
So I closed all 600 browser tabs, 3 terminal windows, 2 ssh sessions, 3 scite windows, took a break, walked around, came back, tried these instructions again, and it worked fine.

[http://kevin.vanzonneveld.net/techblog/article/make_ssh_connections_with_php/](http://kevin.vanzonneveld.net/techblog/article/make_ssh_connections_with_php/)

Blah. I feel like I just wasted 2 hours of my life for nothing. :o

---

