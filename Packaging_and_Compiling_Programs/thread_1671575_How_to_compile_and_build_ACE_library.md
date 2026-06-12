---
title: "How to compile and build ACE library?"
date: 2011-01-20
forum: Packaging and Compiling Programs
---

### Post by illegal on 2011-01-20
I've downloaded the package from [ftp://download.dre.vanderbilt.edu/previous_versions/ACE-src-6.0.0.tar.gz](ftp://download.dre.vanderbilt.edu/previous_versions/ACE-src-6.0.0.tar.gz)

If anyone knows the step by step procedure please help me in compiling and building ACE.

I've done export ACE_ROOT and exported LD_LIBRARY_PATH to the ACE_ROOT lib.

Created config.h file here: /ace/config.h
What should be the content of this file?

In the build configuration file (/include/makeinclude/platform_macros.GNU), I've done the following changes:
include $(ACE_ROOT)/include/makeinclude/platform_linux.GNU
ssl=1

After this, i couldnt find the default.features file in /bin/MakeProjectCreator/config/default.features, as I saw somewhere that I've to modify this file.

Couldnt proceed further :(
I'd be highly thankful if anyone could help me out.

Thanks in advance.

---

### Post by SevenMachines on 2011-01-21
First things first, if you can use the repository version then try and use that! Otherwise, if you need to compile it... this worked for me, see how it goes if you're still having problems. It uses the gnu autotools method and not the ACE one so avoids setting environment variables and such. I haven't run the build through to completion and so haven't run the tests on it either so caveat emptor, its a big build :*)

$ tar -zvxf ACE-src-6.0.0.tar.gz
$ cd ACE_wrappers/
$ autoreconf -f
$ automake --add-missing
$ mkdir build
$ cd build
$ ../configure
$ make

---

### Post by illegal on 2011-01-24
> **SevenMachines said:**
> First things first, if you can use the repository version then try and use that! Otherwise, if you need to compile it... this worked for me, see how it goes if you're still having problems. It uses the gnu autotools method and not the ACE one so avoids setting environment variables and such. I haven't run the build through to completion and so haven't run the tests on it either so caveat emptor, its a big build :*)

$ tar -zvxf ACE-src-6.0.0.tar.gz
$ cd ACE_wrappers/
$ autoreconf -f
$ automake --add-missing
$ mkdir build
$ cd build
$ ../configure
$ make

Thanks a lot.
autoreconf -f gave me the following error:

> configure.ac:240: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:366: error: possibly undefined macro: AC_DISABLE_STATIC
configure.ac:369: error: possibly undefined macro: AC_LIBTOOL_DLOPEN
configure.ac:372: error: possibly undefined macro: AC_LIBTOOL_WIN32_DLL
autoreconf: /usr/bin/autoconf failed with exit status: 1

:-? :-?

---

### Post by illegal on 2011-01-24
Also, found some steps for running ACE library from somewhere else.

> $ tar xjvf ACE-5.6.9.tar.bz2
$ cd ACE_wrappers
$ mkdir build
$ cd build
$ ../configure --prefix=/usr/local
$ make
$ sudo make install

Here, while doing a make, I'm getting a huge list of errors. Copying it below.
> /home/MyUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/SSL_SOCK_Stream.inl:285: undefined reference to `SSL_shutdown'
/home/MyUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/SSL_SOCK_Stream.inl:287: undefined reference to `SSL_get_error'
/home/MyUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/SSL_SOCK_Stream.inl:296: undefined reference to `SSL_clear'
client-SSL-client.o: In function `ACE_SSL_SOCK_Stream::recv_i(void*, unsigned int, int, ACE_Time_Value const*) const':
/home/MyUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/SSL_SOCK_Stream.inl:148: undefined reference to `SSL_read'
/home/MyUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/SSL_SOCK_Stream.inl:151: undefined reference to `SSL_get_error'
client-SSL-client.o: In function `ACE_SSL_SOCK_Stream::close()':
/home/MyUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/SSL_SOCK_Stream.inl:285: undefined reference to `SSL_shutdown'
/home/MyUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/SSL_SOCK_Stream.inl:287: undefined reference to `SSL_get_error'
client-SSL-client.o: In function `ACE_SSL_SOCK_Stream::recv(void*, unsigned int) const':
/home/MyUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/SSL_SOCK_Stream.inl:172: undefined reference to `SSL_shutdown'
client-SSL-client.o: In function `ACE_SSL_SOCK_Stream::close()':
/home/MyUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/SSL_SOCK_Stream.inl:296: undefined reference to `SSL_clear'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_connect'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_set_bio'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `BIO_free'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_set_client_CA_list'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `BIO_ctrl'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_add_dir_cert_subjects_to_stack'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `CRYPTO_set_locking_callback'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_set_verify'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `RAND_load_file'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_load_error_strings'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_peek'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_state'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `BIO_clear_flags'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_check_private_key'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `BIO_new'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_free'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `ERR_clear_error'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `RAND_egd'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `ERR_free_strings'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_set_connect_state'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `RAND_seed'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_new'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_set_accept_state'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `BIO_set_flags'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_set_fd'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `EVP_cleanup'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_pending'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_want'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_add_file_cert_subjects_to_stack'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_load_client_CA_file'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `CRYPTO_num_locks'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_load_verify_locations'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `ERR_get_error'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_set_verify_depth'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `PEM_read_bio_DHparams'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_use_PrivateKey_file'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_library_init'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_use_certificate_file'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `CRYPTO_set_id_callback'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_new'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_use_certificate'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_write'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_get_client_CA_list'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `sk_new_null'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_accept'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `ERR_error_string_n'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `BIO_new_file'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `RAND_status'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_ctrl'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `DH_free'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_free'
collect2: ld returned 1 exit status
make[2]: *** [client] Error 1
make[2]: Leaving directory `/home/MyUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/MyUser/S6a/ACE_wrappers/build/examples/IPC_SAP'
make: *** [all-recursive] Error 1


Is this the problem with LD_LIBRARY_PATH? I couldnt make out which library path I should give. Or the problem is with something else?

Any help? :(

---

### Post by SevenMachines on 2011-01-24
you're missing libtool i imagine
$ sudo apt-get install libtool

---

### Post by illegal on 2011-01-24
> **SevenMachines said:**
> you're missing libtool i imagine
$ sudo apt-get install libtool

Will an offline installation of libtool be ok? I'm downloading it from [http://ftp.gnu.org/gnu/libtool/libtool-1.0.tar.gz](http://ftp.gnu.org/gnu/libtool/libtool-1.0.tar.gz)

---

### Post by SevenMachines on 2011-01-24
> **illegal said:**
> Also, found some steps for running ACE library from somewhere else



Here, while doing a make, I'm getting a huge list of errors. Copying it below.


Is this the problem with LD_LIBRARY_PATH? I couldnt make out which library path I should give. Or the problem is with something else?

Any help? :(

I'd stick with 6.0 version, it's newer, i've got that and can follow any problems easier :*) By the looks of it the errors come from missing linkage to openssl although i'd rather not dig into it unless the 6.0 version has the same problem.

---

### Post by SevenMachines on 2011-01-24
You'd need to look up offline installation of packages and their dependencies ( i think theres a thread in this forum on it that i may have answered before! )

Installing libtool from source is not the same, and certainly more difficult than, installing the pre-build repository packages

For instance, on natty, i would just do
$ sudo apt-get install libace-dev

and i would be done :*) I'm assuming you have a specific need to compile from source otherwise you're giving yourself an awful lot of extra work?

---

### Post by SevenMachines on 2011-01-24
Ah, offline installation example 
[http://ubuntuforums.org/showpost.php?p=10198406&postcount=7](http://ubuntuforums.org/showpost.php?p=10198406&postcount=7)

---

### Post by illegal on 2011-01-24
> **SevenMachines said:**
> You'd need to look up offline installation of packages and their dependencies ( i think theres a thread in this forum on it that i may have answered before! )

Installing libtool from source is not the same, and certainly more difficult than, installing the pre-build repository packages

For instance, on natty, i would just do
$ sudo apt-get install libace-dev

and i would be done :*) I'm assuming you have a specific need to compile from source otherwise you're giving yourself an awful lot of extra work?

The issue is that, the linux machine on which I'm building ACE library is not connected to internet and is not having any provision to get connected ;)
Already got libtools 1.0, did a ./configure and make on the same.

PS: I couldnt get any direct link to download ACE library 6.0 which you'd mentioned in your previous post.

---

### Post by SevenMachines on 2011-01-24
See [http://ubuntuforums.org/showpost.php?p=10392670&postcount=9](http://ubuntuforums.org/showpost.php?p=10392670&postcount=9) for offline installation of packages

6.0 was the link i was using from your first post #1 !

---

### Post by illegal on 2011-01-24
> **SevenMachines said:**
> See [http://ubuntuforums.org/showpost.php?p=10392670&postcount=9](http://ubuntuforums.org/showpost.php?p=10392670&postcount=9) for offline installation of packages

6.0 was the link i was using from your first post #1 !

Update: Now using ACE library 6.0.

autoreconf -f
> configure.ac:241: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:367: error: possibly undefined macro: AC_DISABLE_STATIC
configure.ac:370: error: possibly undefined macro: AC_LIBTOOL_DLOPEN
autoreconf: /usr/bin/autoconf failed with exit status: 1

automake --add-missing
> ........................

tests/Makefile.am:27: Libtool library used but `LIBTOOL' is undefined
tests/Makefile.am:27:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
tests/Makefile.am:27:   to `configure.ac' and run `aclocal' and `autoconf' again.
tests/Makefile.am:27:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
tests/Makefile.am:27:   its definition is in aclocal's search path.
websvcs/lib/Makefile.am:16: Libtool library used but `LIBTOOL' is undefined
websvcs/lib/Makefile.am:16:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
websvcs/lib/Makefile.am:16:   to `configure.ac' and run `aclocal' and `autoconf' again.
websvcs/lib/Makefile.am:16:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
websvcs/lib/Makefile.am:16:   its definition is in aclocal's search path.
../configure
> configure: creating ./config.status
config.status: error: cannot find input file: Makefile.in

Contents of build directory: ace  config.log  config.status

---

### Post by SevenMachines on 2011-01-24
You still haven't got libtool installed, until thats installed none of the rest will work i'm afraid

[EDIT] If you installed libtool from source you'll need to make sure that it either was installed to system prefix /usr or if you installed it somewhere else you'll need to set up paths. Best method is offline install using apt-offline as mentioned above

---

### Post by illegal on 2011-01-24
Have installed libtool
make in the build directory of libtool:
> Making all in doc
make[1]: Entering directory `/home/myUser/S6a/libtool-1.0/build/doc'
Updating ../../doc/version.texi
make[1]: Leaving directory `/home/myUser/S6a/libtool-1.0/build/doc'
Making all in tests
make[1]: Entering directory `/home/myUser/S6a/libtool-1.0/build/tests'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/myUser/S6a/libtool-1.0/build/tests'
make[1]: Entering directory `/home/myUser/S6a/libtool-1.0/build'
CONFIG_FILES=libtoolize CONFIG_HEADERS= ./config.status
config.status: creating libtoolize
config.status: WARNING:  ../libtoolize.in seems to ignore the --datarootdir setting
config.status: executing depfiles commands
chmod +x libtoolize
make[1]: Leaving directory `/home/myUser/S6a/libtool-1.0/build'


What should be the LD_LIBRARY_PATH? /home/myUser/S6a/libtool-1.0/ ?
Its not installed at /usr

make in the build directory of ACE_wrappers:
> ............................
checking if generated ACE configuration is usable... yes
checking for ACE_IOStream support... yes
checking if ACE needs conversion to pass ACE_TTY_IO to DEV_Connector... yes
configure: creating ./config.status
config.status: error: cannot find input file: Makefile.in


---

### Post by SevenMachines on 2011-01-24
something built != something installed

If you're *absolutely* sure you want to build libtool from source and not use the packages then...

* in the libtool directory 
> $ ./configure --prefix=/usr
$ make 
$ sudo make installThen it should be properly installed
> $ libtool --version
ltmain.sh (GNU libtool) 2.2.6bThen you should try out the commands i mentioned in my first reply again

---

### Post by illegal on 2011-01-24
Sorry, Linux n00b here :-#
Got libtool installed properly.

libtool --version
> ltmain.sh (GNU libtool) 1.0

Now I'm in the ACE-wrappers directory.
autoreconf -f
> /usr/share/aclocal/libtool.m4:25: warning: underquoted definition of AM_PROG_LIBTOOL
/usr/share/aclocal/libtool.m4:25:   run info '(automake)Extending aclocal'
/usr/share/aclocal/libtool.m4:25:   or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
configure.ac:241: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:367: error: possibly undefined macro: AC_DISABLE_STATIC
configure.ac:370: error: possibly undefined macro: AC_LIBTOOL_DLOPEN
autoreconf: /usr/bin/autoconf failed with exit status: 1


automake --add-missing
> websvcs/lib/Makefile.am:16: Libtool library used but `LIBTOOL' is undefined
websvcs/lib/Makefile.am:16:   The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
websvcs/lib/Makefile.am:16:   to `configure.ac' and run `aclocal' and `autoconf' again.
websvcs/lib/Makefile.am:16:   If `AC_PROG_LIBTOOL' is in `configure.ac', make sure
websvcs/lib/Makefile.am:16:   its definition is in aclocal's search path.
Guess I dont have do do any explicit path settings for libtool now (?)

Inside ACE_wrappers/build:
../configure
> checking for osfcn.h... no
checking if generated ACE configuration is usable... yes
checking for ACE_IOStream support... yes
checking if ACE needs conversion to pass ACE_TTY_IO to DEV_Connector... yes
configure: creating ./config.status
config.status: error: cannot find input file: Makefile.in


---

### Post by SevenMachines on 2011-01-24
libtool version 1.0 is almost a decade old!!! Thats a lifetime in toolchain terms.

* uninstall libtool from the libtool source directory
$ sudo make uninstall

Download a recent version, heres the current natty version
[ftp://mirrors.kernel.org/gnu/libtool/libtool-2.2.6b.tar.gz](ftp://mirrors.kernel.org/gnu/libtool/libtool-2.2.6b.tar.gz)

Build and install as before then retry autoreconf -f in the ace directory

As i mentioned, this is the most complicated way to install ace libraries and headers and with packages from the repositories its a doddle as all the work has been done for you. I'm just assuming you are doing this for fun :*)

---

### Post by illegal on 2011-01-24
> **SevenMachines said:**
> libtool version 1.0 is almost a decade old!!! Thats a lifetime in toolchain terms.

* uninstall libtool from the libtool source directory
$ sudo make uninstall

Download a recent version, heres the current natty version
[ftp://mirrors.kernel.org/gnu/libtool/libtool-2.2.6b.tar.gz](ftp://mirrors.kernel.org/gnu/libtool/libtool-2.2.6b.tar.gz)

Build and install as before then retry autoreconf -f in the ace directory

As i mentioned, this is the most complicated way to install ace libraries and headers and with packages from the repositories its a doddle as all the work has been done for you. I'm just assuming you are doing this for fun :*)

No, bro. I'm doing this for a purpose, not for fun :)

Installed the recent version of libtool from the link you gave. Thanks :)

Btw, autoreconf -f is showing
> configure.ac:386: required file `aux_config/ltmain.sh' not found
autoreconf: automake failed with exit status: 1

automake --add-missing
> configure.ac:386: required file `aux_config/ltmain.sh' not found

../configure inside build directory:
> checking if ACE needs conversion to pass ACE_TTY_IO to DEV_Connector... yes
configure: creating ./config.status
config.status: error: cannot find input file: Makefile.in

:? :?

---

### Post by SevenMachines on 2011-01-24
In the ACE_headers directory, whats the output of 
> $ libtoolize -f

You should something like
> $ libtoolize -f
libtoolize: putting auxiliary files in AC_CONFIG_AUX_DIR, `aux_config'.
libtoolize: linking file `aux_config/ltmain.sh'
...

'autoreconf -f' should be forcing the copying of ltmain across
try posting the output of
> $ autoreconf -fv

which gives more information on whats happening

---

### Post by SevenMachines on 2011-01-24
You can also try copying ltmain.sh across manually, although this shouldnt be needed to be done usually.
In your libtool source directory
> $ find ./ -name ltmain.sh
./libtool-2.2.6b/libltdl/config/ltmain.sh


now copy ltmain.sh across to the 'aux_config' directory in ACE_headers

---

### Post by illegal on 2011-01-25
> **SevenMachines said:**
> In the ACE_headers directory, whats the output of 


You should something like


'autoreconf -f' should be forcing the copying of ltmain across
try posting the output of


which gives more information on whats happening

Sorry for the late response.
Everything working fine now, except build which shows the same error which I've posted here before in post #4 :(

> client-SSL-client.o: In function `ACE_SSL_SOCK_Stream::close()':
/home/myUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/S
SL_SOCK_Stream.inl:305: undefined reference to `SSL_shutdown'
/home/myUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/S
SL_SOCK_Stream.inl:307: undefined reference to `SSL_get_error'
/home/myUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/S
SL_SOCK_Stream.inl:316: undefined reference to `SSL_clear'
client-SSL-client.o: In function `ACE_SSL_SOCK_Stream::recv_i(void*, unsigned in
t, int, ACE_Time_Value const*) const':
/home/myUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/S
SL_SOCK_Stream.inl:148: undefined reference to `SSL_read'
/home/myUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/S
SL_SOCK_Stream.inl:151: undefined reference to `SSL_get_error'
client-SSL-client.o: In function `ACE_SSL_SOCK_Stream::close()':
/home/myUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/S
SL_SOCK_Stream.inl:305: undefined reference to `SSL_shutdown'
/home/myUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/S
SL_SOCK_Stream.inl:307: undefined reference to `SSL_get_error'
client-SSL-client.o: In function `ACE_SSL_SOCK_Stream::recv(void*, unsigned int)
 const':
/home/myUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/S
SL_SOCK_Stream.inl:172: undefined reference to `SSL_shutdown'
client-SSL-client.o: In function `ACE_SSL_SOCK_Stream::close()':
/home/myUser/S6a/ACE_wrappers/build/examples/IPC_SAP/SSL_SAP/../../../../ace/SSL/S
SL_SOCK_Stream.inl:316: undefined reference to `SSL_clear'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `TLSv1_method'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_connect'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_set_bio'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `BIO_free'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_set_client
_CA_list'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `TLSv1_client_metho
d'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `BIO_ctrl'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_add_dir_cert_s
ubjects_to_stack'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `CRYPTO_set_locking
_callback'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_set_verify
'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `RAND_load_file'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_load_error_str
ings'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_peek'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_state'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSLv2_client_metho
d'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `BIO_clear_flags'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_check_priv
ate_key'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSLv2_method'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `BIO_new'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_free'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `ERR_clear_error'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSLv3_server_metho
d'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `RAND_egd'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSLv3_client_metho
d'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `ERR_free_strings'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_set_connect_st
ate'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSLv3_method'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `RAND_seed'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_new'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_set_accept_sta
te'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `BIO_set_flags'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_set_fd'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `EVP_cleanup'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_pending'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_want'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_add_file_cert_
subjects_to_stack'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_load_client_CA
_file'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `CRYPTO_num_locks'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_load_verif
y_locations'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `ERR_get_error'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSLv23_client_meth
od'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_set_verify
_depth'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `PEM_read_bio_DHpar
ams'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_use_Privat
eKey_file'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_library_init'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_use_certif
icate_file'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `CRYPTO_set_id_call
back'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_new'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_use_certif
icate'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_write'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_get_client
_CA_list'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `TLSv1_server_metho
d'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `sk_new_null'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_accept'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSLv2_server_metho
d'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `ERR_error_string_n
'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `BIO_new_file'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `RAND_status'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_ctrl'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `DH_free'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSL_CTX_free'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSLv23_server_meth
od'
../../../ace/SSL/.libs/libACE_SSL.so: undefined reference to `SSLv23_method'
collect2: ld returned 1 exit status
make[3]: *** [client] Error 1
make[3]: Leaving directory `/home/myUser/S6a/ACE_wrappers/build/examples/IPC_SAP/S
SL_SAP'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/myUser/S6a/ACE_wrappers/build/examples/IPC_SAP'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/myUser/S6a/ACE_wrappers/build/examples'
make: *** [all-recursive] Error 1

Should I have to set any library paths explicitly?

---

### Post by SevenMachines on 2011-01-25
Hi there, how does your ./configure output look? Does it find the ssl libraries ok?
Make sure you have libssl-dev installed, you shouldnt need to specify libraries but remember the possible options to ./configure

--with-openssl[=DIR]     
* root directory of openssl installation
  
--with-openssl-include=DIR
* specify exact include dir for openssl headers

--with-openssl-libdir=DIR
* specify exact include dir for openssl libraries

Or even, 
--enable-ssl=no
* :)

I'm not seeing this problem and build goes fine here, i've attached the build.log for comparison if it helps

---

### Post by illegal on 2011-01-25
> **SevenMachines said:**
> Hi there, how does your ./configure output look? Does it find the ssl libraries ok?
Make sure you have libssl-dev installed, you shouldnt need to specify libraries but remember the possible options to ./configure

--with-openssl[=DIR]     
* root directory of openssl installation
  
--with-openssl-include=DIR
* specify exact include dir for openssl headers

--with-openssl-libdir=DIR
* specify exact include dir for openssl libraries

Or even, 
--enable-ssl=no
* :)

I'm not seeing this problem and build goes fine here, i've attached the build.log for comparison if it helps

../configure in ACE-wrappers/build:
> .........................
config.status: creating protocols/ace/HTBP/Makefile
config.status: creating protocols/ace/RMCast/Makefile
config.status: creating protocols/ace/TMCast/Makefile
config.status: creating protocols/examples/Makefile
config.status: creating protocols/examples/RMCast/Makefile
config.status: creating protocols/examples/RMCast/Send_Msg/Makefile
config.status: creating protocols/examples/TMCast/Makefile
config.status: creating protocols/examples/TMCast/Member/Makefile
config.status: creating protocols/tests/HTBP/Makefile
config.status: creating protocols/tests/HTBP/Reactor_Tests/Makefile
config.status: creating protocols/tests/HTBP/Send_Large_Msg/Makefile
config.status: creating protocols/tests/HTBP/Send_Recv_Tests/Makefile
config.status: creating protocols/tests/HTBP/ping/Makefile
config.status: creating protocols/tests/Makefile
config.status: creating protocols/tests/RMCast/Makefile
config.status: creating ace/config.h
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default commands

Configuration of ACE 6.0.0 is now complete.


Installed openssl like this:
> $ ./configure --prefix=/usr
$ make 
$ sudo make install
(Installed libtool also in the same way)

---

### Post by SevenMachines on 2011-01-25
The partial configure output isnt going to help, you're looking for something like

```
checking for OpenSSL libraries... yes
...
checking whether to compile/use the ACE_SSL library... yes
```

If you post the output, post the full output inside [code] tags to keep the display size sane (not [quote] tags, they dont have scrollbars!)

---

### Post by illegal on 2011-01-25
^^^
Attaching the log file for ../configure in ACE_wrappers/build.

---

### Post by illegal on 2011-01-25
> **illegal said:**
> ^^^
Attaching the log file for ../configure in ACE_wrappers/build.

checking for OpenSSL libraries... no
checking whether to compile/use the ACE_QoS library... no
checking whether to compile/use the ACE_SSL library... yes
checking whether to compile/use the ACEXML library... (cached) yes

:???: :???:

---

### Post by SevenMachines on 2011-01-25
> checking for OpenSSL libraries... noThats your problem, again illustrating why 'apt-get install libssl-dev' is better than 'make install' :)

Do you have something like this...
> $ ls /usr/lib/libssl*
/usr/lib/libssl3.so     /usr/lib/libssl.a   /usr/lib/libssl.so.0.9.8
/usr/lib/libssl3.so.1d  /usr/lib/libssl.soIf you get no results try
> $ sudo updatedb
$ locate libssl|grep .so

---

### Post by illegal on 2011-01-25
> **SevenMachines said:**
> Thats your problem, again illustrating why 'apt-get install libssl-dev' is better than 'make install' :)

Do you have something like this...
If you get no results try

ls /usr/lib/libssl*
> /usr/lib/libssl3.so  /usr/lib/libssl.a

---

### Post by SevenMachines on 2011-01-25
Hi, can you try 'make install' ssl again then

> $ ls -l /lib/libssl*
$ ls -l /usr/lib/libssl*

and post ACE_wrappers/config.log

---

### Post by illegal on 2011-01-25
> **SevenMachines said:**
> Hi, can you try 'make install' ssl again then



and post ACE_wrappers/config.log

There are two binaries 'config' and 'Configure' in openssl-1.0.0c directory.
Using Configure.

Did the installation as below:
> $./Configure --prefix=/usr
$ make 
$ sudo make install
Its ok I guess (?)

ls -l /lib/libssl*
> -rwxr-xr-x 1 root root 281240 2007-10-16 03:26 /lib/libssl.so.0.9.8b
lrwxrwxrwx 1 root root     16 2008-11-29 00:38 /lib/libssl.so.6 -> libssl.so.0.9.8b

ls -l /usr/lib/libssl*
> -rwxr-xr-x 1 root root 175004 2007-10-11 19:19 /usr/lib/libssl3.so
-rw-r--r-- 1 root root 442624 2011-01-25 16:16 /usr/lib/libssl.a

---

### Post by illegal on 2011-01-25
> **SevenMachines said:**
> Hi, can you try 'make install' ssl again then



and post ACE_wrappers/config.log

Adding ../configure log from ACE_wrappers/build directory.

---

### Post by SevenMachines on 2011-01-25
try
> $ ln -s  /usr/lib/libssl.so /lib/libssl.so.0.9.8b
$ ln -s  /usr/lib/libssl.so.0.9.8b /lib/libssl.so.0.9.8b

then run configure for ACE_wrappers again, check if it says
>  			 				checking for OpenSSL libraries... yes
this time

---

### Post by illegal on 2011-01-25
> **SevenMachines said:**
> try


then run configure for ACE_wrappers again, check if it says

this time

> $ ln -s /usr/lib/libssl.so /lib/libssl.so.0.9.8b
$ ln -s /usr/lib/libssl.so.0.9.8b /lib/libssl.so.0.9.8b
Both saying symbolic link already exist.

../configure at ACE_wrappers/build still says
> checking for fox-config... no
checking for Kerberos include flags needed by OpenSSL... no
checking for OpenSSL libraries... no
checking whether to compile/use the ACE_QoS library... no
checking whether to compile/use the ACE_SSL library... yes
checking whether to compile/use the ACEXML library... (cached) yes
checking whether to use wide characters internally... no

Cant figure out what is wrong. openssl got installed correctly I guess :confused:

---

### Post by SevenMachines on 2011-01-25
can you post the actual 'config.log' from ACE_wrappers, thats not the paste of configure output, its an actual file in the same directory with more detail in it

---

### Post by illegal on 2011-01-25
> **SevenMachines said:**
> can you post the actual 'config.log' from ACE_wrappers, thats not the paste of configure output, its an actual file in the same directory with more detail in it

Attaching config.log from ACE_wrappers directory and ACE_wrappers/build directory.

---

### Post by SevenMachines on 2011-01-25
Yes, it looks like theres a right mess of openssl installations going on.
You have 0.9.8b libraries installed, but the headers of 1.0.0c. And to make things worse..
>  /usr/include/openssl/ssl.h:146:37: error: ../openssl-1.0.0c/e_os2.h: No such file or directory
Why its set to look in /usr/include/openssl-1.0.0c i have no idea. 

This is why i always recommend

* Install development headers from -dev packages in the repository
* If you need to install from source, install to /usr/local, its what it there for!
* Use checkinstall to install from source, it helps avoid file and version mis-mash and lost files

I'm not sure exactly how to best tidy your openssl installation up though, if you dont want packages but build from source (still sure :) ) then i suppose you could

* remove any /usr/include/openssl* directories
* choose 0.9.8b openssl version since the libraries are already installed
* run './config && make && sudo make install'

Hopefully then you'll have all you're header files and libraries back in sync.

---

### Post by illegal on 2011-01-25
> **SevenMachines said:**
> Yes, it looks like theres a right mess of openssl installations going on.
You have 0.9.8b libraries installed, but the headers of 1.0.0c. And to make things worse..

Why its set to look in /usr/include/openssl-1.0.0c i have no idea. 

This is why i always recommend

* Install development headers from -dev packages in the repository
* If you need to install from source, install to /usr/local, its what it there for!
* Use checkinstall to install from source, it helps avoid file and version mis-mash and lost files

I'm not sure exactly how to best tidy your openssl installation up though, if you dont want packages but build from source (still sure :) ) then i suppose you could

* remove any /usr/include/openssl* directories
* choose 0.9.8b openssl version since the libraries are already installed
* run './config && make && sudo make install'

Hopefully then you'll have all you're header files and libraries back in sync.

I'll remove all the openssl* headers from the /usr/include directory, and will do a fresh build now. Hoping the best :)

Btw, I'm using openssl-1.0.0c, not 0.9.8b

---

### Post by illegal on 2011-01-25
Edited.

---

### Post by illegal on 2011-01-26
Update: Replaced everything. Compiled and built openssl and libtool. Downloaded ACE library 6.0. Couldnt do a ../configure in build directory as no binaries named configure is present in ACE_wrappers directory :S

---

### Post by SevenMachines on 2011-01-26
> **illegal said:**
> Update: Replaced everything. Compiled and built openssl and libtool. Downloaded ACE library 6.0. Couldnt do a ../configure in build directory as no binaries named configure is present in ACE_wrappers directory :S
Yes, remember the steps from
[http://ubuntuforums.org/showpost.php?p=10382616&postcount=2](http://ubuntuforums.org/showpost.php?p=10382616&postcount=2)
Here you need to create configure from configure.ac, usually by running autoconf, i used autoreconf -f in this case.

> $ tar -zvxf ACE-src-6.0.0.tar.gz
$ cd ACE_wrappers/
$ autoreconf -f
$ automake --add-missing
$ mkdir build
$ cd build
$ ../configure
$ make

---

### Post by SevenMachines on 2011-01-26
Couple of quick notes.

_**Configure Scripts**_

```
$ ./configure
```by itself will configure the install for the default directory, which it is usually /usr/local/. Meaning headers would usually end up in /usr/local/include and libraries in /usr/local/lib. These are not on the system search path, to use libraries not on the search path you would need to add the directories to the compilation manually, -I to add a header directory, -L to add one for libraries, ie, 
```
 $ gcc -o hello hello.c -I/usr/local/include -L/usr/local/lib
```You can add library directories permanently to ld by creating a file like
/etc/ld.so.conf.d/local.conf:
```
# local default configuration
/usr/local/lib
```then updating ld
```
$ sudo ldconfig -v
```To install libraries directly into the system directories, which i think is always a *bad* idea except in special cases, leave the system directories to the package manager :) But to do it you would do
```
$ ./configure --prefix=/usr
```This will send libraries to /usr/lib, headers to /usr/include, etc on running 'make install'

_**Offline installation**_

On apt-offline, this is purely something to simplify installing to an offline machines. You...

* Run it on the offline machines to get a .sig file which contains all of the packages and dependencies needed on *that* machines specifically
* Then run it with the .sig file on the online machine to download the packages and all its dependencies for the *offline* machine into a zip archive
* Take the archive to the offline machine, unzip, then run 
```
 $ sudo dpkg -i *.deb 
```
to install the package and all its needed dependencies

This is an example for libace.

Here I want to install libace-dev, the development headers, on a disconnected machine  (--install-packages libace-dev), optionally, i am also going to download the source for ACE(--install-src-packages libace-dev), and the build-deps i need to build  it(--src-build-dep), obviously you can use whatever combination of  these options you require, add extra packages, etc...

* On the non-networked machine
```
$ sudo apt-offline set ace-offline.sig --install-packages libace-dev  --src-build-dep --install-src-packages libace-dev
``` This generates a list of required packages and dependencies that need to be installed on the offline machine and puts them in the sig file.

* copy ace-offline.sig to a networked machine, then...
```
sudo apt-offline get ace-offline.sig --no-checksum --bundle ace-offline.zip
``` This downloads all of the packages mentioned in the .sig file and puts them all into a handy zip archive

* Copy ace-offline.zip to your offline  machine then...
```
$ unzip ace-offline.zip
$ dpkg -i *.deb 
```Here we just unzip our archive containing all those needed .deb packages and install them all using dpkg

* Done!

[U][B]Are you sure you want to compile from source?

[/B][/U] Finally, just to emphasise, unless anyone needs a specific version of a library for some reason, installing the -dev package from the repository will give you everything you need to work with and develop with, that library. Personally, if i wanted to develop with ACE i would just do
```
$ sudo apt-get install libace-dev
```and start programming
If i specifically needed ACE 6.0, I would install it to /usr/local, to avoid any danger of smashing my system directories. Then add the library directory to my project compilation with "-L/usr/local/lib" and the headers with "-I/usr/local/include"

---

### Post by illegal on 2011-01-27
Thanks a ton for the detailed description. WIll try it out and post my result here :)

Thanks a lot.

---

### Post by illegal on 2011-01-28
ACE_wrappers/ace/SSL is not getting built it seems. There is no Makefile/configure included in the directory.
These are the files present (Removed two temp files I've created):
  3 ACE_SSL.pc.in
  4 Makefile.am
  5 Makefile.in
  6 SSL_Asynch_BIO.cpp
  7 SSL_Asynch_BIO.h
  8 SSL_Asynch_Stream.cpp
  9 SSL_Asynch_Stream.h
 10 SSL_Asynch_Stream.inl
 11 sslconf.h
 12 SSL_Context.cpp
 13 SSL_Context.h
 14 SSL_Context.inl
 15 SSL_Export.h
 16 ssl_for_tao.mpc
 17 ssl.mpc
 18 SSL_SOCK_Acceptor.cpp
 19 SSL_SOCK_Acceptor.h
 20 SSL_SOCK_Acceptor.inl
 21 SSL_SOCK_Connector.cpp
 22 SSL_SOCK_Connector.h
 23 SSL_SOCK_Connector.inl
 24 SSL_SOCK.cpp
 25 SSL_SOCK.h
 26 SSL_SOCK.inl
 27 SSL_SOCK_Stream.cpp
 28 SSL_SOCK_Stream.h
 29 SSL_SOCK_Stream.inl

Got a Makefile for this directory from: [http://svn.osgeo.org/mapguide/sandbox/adsk/MGRS/Oem/ACE/ACE_wrappers/ace/SSL/Makefile](http://svn.osgeo.org/mapguide/sandbox/adsk/MGRS/Oem/ACE/ACE_wrappers/ace/SSL/Makefile)

While doing a make:
> Makefile:34: /include/makeinclude/wrapper_macros.GNU: No such file or directory
Makefile:35: /include/makeinclude/macros.GNU: No such file or directory
Makefile:36: /include/makeinclude/rules.common.GNU: No such file or directory
Makefile:37: /include/makeinclude/rules.nonested.GNU: No such file or directory
Makefile:38: /include/makeinclude/rules.lib.GNU: No such file or directory
Makefile:39: /include/makeinclude/rules.local.GNU: No such file or directory
make: *** No rule to make target `/include/makeinclude/rules.local.GNU'.  Stop.


I've set ACE_ROOT to ACE_wrappers directory and the files wrapper_macros.GNU, macros.GNU, rules.common.GNU, rules.nonested.GNU, rules.lib.GNU and rules.local.GNU are present at /ACE_wrappers//include/makeinclude

autoreconf -f
> autoreconf: `configure.ac' or `configure.in' is required

---

### Post by SevenMachines on 2011-01-28
What i mentioned in the first reply will build ACE.
```
$ tar -zvxf ACE-src-6.0.0.tar.gz
$ cd ACE_wrappers/
$ autoreconf -f
$ automake --add-missing
$ mkdir build
$ cd build
$ ../configure
$ make                                                                                                                   
```There will be no Makefile in ace/SSL, theres a Makefile.am which will be use to generate it during the ./configure stage (into the build/ace/SSL subdirectory). Theres no need to set any variables or anything else, above are all the build steps. Adding Makefiles for other versions is likely to end in tears

If SSL isnt being built you need to look at the output during the ./configure stage mentioned above. It will mention 2 lines somewhere in the output
```
...
checking for OpenSSL libraries... yes
...
checking whether to compile/use the ACE_SSL library... yes
...
```One of these will say 'no', the config.log will tell you why in detail. I'm guessing from previous posts that your openssl installation is in a disjointed state.

---

### Post by illegal on 2011-02-01
Update:

Made a small change while installing openssl
$ ./config --prefix=/usr shared
$ make
$ make test
$ make install


ACE library is now getting compiled without any errors. Will post the logs here soon.

Thanks a lot SevenMachines :)

---

### Post by agni07 on 2011-10-28
@Seven Machines,

I am new to ACE and trying to follow the steps mentioned by you. However, when i do make in the build directory i get the following error:
g++: /usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crti.o: No such file or directory
g++: /usr/lib/gcc/i486-linux-gnu/4.4.3/crtbeginS.o: No such file or directory
g++: /usr/lib/gcc/i486-linux-gnu/4.4.3/crtendS.o: No such file or directory
g++: /usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crtn.o: No such file or directory
make[3]: *** [libACE.la] Error 1
make[3]: Leaving directory `/home/xx/Desktop/ACE_wrappers/build/ace'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/xx/Desktop/ACE_wrappers/build/ace'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/xx/Desktop/ACE_wrappers/build/ace'
make: *** [all-recursive] Error 1

Sorry for reviving an old thread, but thought u wud able to shed light on it more than any one else.
Thanx in anticipation.

---

### Post by SevenMachines on 2011-10-28
Hi, best to use the ace dev package from the repositories if you can. If not it'll be probably next week before I can take a look at it so hopefully someone knows

---

### Post by agni07 on 2011-10-31
Thx for the reply.
I have downloaded the ace from [http://ace.sourcear](http://ace.sourcear) ''chive.com/
Earlier I had taken the same from opendds downloads site, but it did not contain CIAO and DANCE folders and proved problematic.
Now, the problem is I am getting stuck up while following steps mentioned by you.
../configure shows 
Configuration of ACE 6.0.0 is now complete.
However, when I do make, I face this problem.

---

### Post by agni07 on 2011-10-31
Making all in tests
make[1]: Entering directory `/home/xx/Desktop/ACE_wrappers/build/tests'
make  all-recursive
make[2]: Entering directory `/home/xx/Desktop/ACE_wrappers/build/tests'
Making all in .
make[3]: Entering directory `/home/xx/Desktop/ACE_wrappers/build/tests'
/bin/bash ../libtool --tag=CXX   --mode=link g++  -W -Wall -Wpointer-arith  -g -O2 -pthread -pipe -O3 -I. -I..   -o Svc_Handler_Test Svc_Handler_Test-Main.o Svc_Handler_Test-Svc_Handler_Test.o libTest_Output.la ../ace/libACE.la -lrt -ldl 
libtool: link: g++ -W -Wall -Wpointer-arith -g -O2 -pthread -pipe -O3 -I. -I.. -o .libs/Svc_Handler_Test Svc_Handler_Test-Main.o Svc_Handler_Test-Svc_Handler_Test.o  ./.libs/libTest_Output.a ../ace/.libs/libACE.so -lrt -ldl -pthread
Svc_Handler_Test-Svc_Handler_Test.o: file not recognized: File truncated
collect2: ld returned 1 exit status
make[3]: *** [Svc_Handler_Test] Error 1
make[3]: Leaving directory `/home/xx/Desktop/ACE_wrappers/build/tests'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/xx/Desktop/ACE_wrappers/build/tests'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/xx/Desktop/ACE_wrappers/build/tests'
make: *** [all-recursive] Error 1
what is the possible reason for this error?

---

### Post by agni07 on 2011-10-31
Solved!!
Replace the file Svc_Handler_Test,cpp with the latest documented file(bugs removed). now make install was successful.

---

### Post by sam05 on 2012-05-24
dear [agni07]("http://ubuntuforums.org/member.php?u=1482075") and [SevenMachines]("http://ubuntuforums.org/member.php?u=915690"),

[SevenMachines]("http://ubuntuforums.org/member.php?u=915690") Thank tou very much for the information. 

 [agni07]("http://ubuntuforums.org/member.php?u=1482075") same problem I am facing. please help in this regard. 

Replace the file Svc_Handler_Test,cpp with the latest documented file(bugs removed)

You said change SVC file but I checked in ACE_wrappers/ace/Svc_Handler.cpp file i found.
please tell me what i need to change and form where .

I successfully completed ./configure but I am facing problem in make :(.
my make output. bit in French sorry for that.

r directory
compilation terminated.
make[3]: *** [libACE_SSL_la-SSL_Asynch_BIO.lo] Erreur 1
make[3]: quittant le répertoire « /home/gpcm1291/Documents/Diameter/ACE_wrappers/build/ace/SSL »
make[2]: *** [all-recursive] Erreur 1
make[2]: quittant le répertoire « /home/gpcm1291/Documents/Diameter/ACE_wrappers/build/ace »
make[1]: *** [all] Erreur 2
make[1]: quittant le répertoire « /home/gpcm1291/Documents/Diameter/ACE_wrappers/build/ace »
make: *** [all-recursive] Erreur 1
gpcm1291@l-at13924:~/Documents/Diameter/ACE_wrappers/build$ ln -s /usr/lib/libssl.so /lib/libssl.so.0.9.8b
ln: impossible de créer le lien symbolique «/lib/libssl.so.0.9.8b»: Permission non accordée


Please help me in this regards.

---

### Post by sam05 on 2012-05-24
$ sudo updatedb
$ locate libssl|grep .so 
/lib/x86_64-linux-gnu/libssl.so.1.0.0
/usr/lib/firefox/libssl3.so
/usr/lib/thunderbird/libssl3.so
/usr/lib/x86_64-linux-gnu/libssl.so
/usr/lib/x86_64-linux-gnu/libssl3.so
/usr/lib/x86_64-linux-gnu/libssl3.so.1d

The libssl is not found in /usr/lib/.  It found in as show in above.
when in did ./configure it showing 

checking for OpenSSL libraries... no

$ Sudo apt-get install libssl-dev
 Reading package lists ... fact
 Building dependency tree
 Reading state information ... fact
 libssl-dev is already the newest version.
 0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

libtool version 2.4.2

 please help me .....

---

