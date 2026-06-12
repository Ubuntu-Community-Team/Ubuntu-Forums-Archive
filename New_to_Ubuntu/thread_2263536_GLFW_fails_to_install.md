---
title: "GLFW fails to install"
date: 2015-02-01
forum: New to Ubuntu
---

### Post by chase9 on 2015-02-01
Hi, this message appears when I try to install glfw.

```
cjbrigna@ubuntu:~/Downloads/glfw-2.7.2$ sudo apt-get install glfw
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package glfw
cjbrigna@ubuntu:~/Downloads/glfw-2.7.2$ 

```

Also, for what it's worth a very similar message appears when I try to install portaubio. I installed other packages just fine. Thanks in advance for any help!

```
cjbrigna@ubuntu:~/Downloads/portaudio-18.1.orig$ sudo apt-get install portaubio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package portaubio
cjbrigna@ubuntu:~/Downloads/portaudio-18.1.orig$ 

```

---

### Post by sandyd on 2015-02-01
> **chase9 said:**
> Hi, this message appears when I try to install glfw.

```
cjbrigna@ubuntu:~/Downloads/glfw-2.7.2$ sudo apt-get install glfw
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package glfw
cjbrigna@ubuntu:~/Downloads/glfw-2.7.2$ 

```

Also, for what it's worth a very similar message appears when I try to install portaubio. I installed other packages just fine. Thanks in advance for any help!

```
cjbrigna@ubuntu:~/Downloads/portaudio-18.1.orig$ sudo apt-get install portaubio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package portaubio
cjbrigna@ubuntu:~/Downloads/portaudio-18.1.orig$ 

```

Hi, and welcome to Ubuntu Forums!

In Ubuntu, most software are available directly from the Ubuntu Repositories. The repositories contain a collection of software, libraries, and other files for your use. They are stored in what is called a 'package'. When wanting to install an application, a good utility to use is [http://packages.ubuntu.com](http://packages.ubuntu.com). Type the name of the package in the section named "Search package directories" and choose 'Search'

In this case, glfw is seperated into two packages, one for the library, and one including the development files for the library.
```

sudo apt-get install libglfw2
```
will install the glfw2 library, while
```

sudo apt-get install libglfw-dev
```
will install the development files for the library.

With portaudio, the package name is  libportaudio2

---

### Post by chase9 on 2015-02-01
Ah, I see now I was using apt-get incorrectly. Thank you so much!

---

### Post by chase9 on 2015-02-01
So now I have a new related issue. I searched for portaubio at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and didn't see anything there so I went to portaubio's website and followed their instructions for installing. However, when I do the ./configure && make I get this.

```
cjbrigna@ubuntu:~/Downloads/portaudio-18.1.orig$ ./configure && make
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix... 
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for ranlib... ranlib
checking for a BSD compatible install... /usr/bin/install -c
checking for ar... /usr/bin/ar
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for pthread_create in -lpthread... yes
configure: creating ./config.status
config.status: creating Makefile

Finished configure.

Type 'make' to build PortAudio and examples.
gcc -c -g -O2 -Ipa_common pa_common/pa_convert.c -o pa_common/pa_convert.o
gcc -c -g -O2 -Ipa_common pa_common/pa_lib.c -o pa_common/pa_lib.o
gcc -c -g -O2 -Ipa_common pa_unix_oss/pa_unix_oss.c -o pa_unix_oss/pa_unix_oss.o
gcc -c -g -O2 -Ipa_common pa_unix_oss/pa_unix.c -o pa_unix_oss/pa_unix.o
/usr/bin/ar ruv lib/libportaudio.a pa_common/pa_convert.o pa_common/pa_lib.o pa_unix_oss/pa_unix_oss.o pa_unix_oss/pa_unix.o
r - pa_common/pa_convert.o
r - pa_common/pa_lib.o
r - pa_unix_oss/pa_unix_oss.o
r - pa_unix_oss/pa_unix.o
ranlib lib/libportaudio.a
gcc -shared -o lib/libportaudio.so.0.0.18 pa_common/pa_convert.o pa_common/pa_lib.o pa_unix_oss/pa_unix_oss.o pa_unix_oss/pa_unix.o 
/usr/bin/ld: pa_common/pa_convert.o: relocation R_X86_64_32 against `.text' can not be used when making a shared object; recompile with -fPIC
pa_common/pa_convert.o: error adding symbols: Bad value
collect2: error: ld returned 1 exit status
make: *** [lib/libportaudio.so.0.0.18] Error 1
cjbrigna@ubuntu:~/Downloads/portaudio-18.1.orig$ 

```

---

### Post by Impavidus on 2015-02-02
PortAudio is available from the repositories too. Note it's PortAu**d**io, as in your unpacked archive, not PortAu**b**io as in your apt-get command. On Ubuntu 14.04:```

# For PortAudio 19 (library, may be installed already):
sudo apt-get install libportaudio2

# For the header files of PortAudio 19 (will automatically pull in the above package, if not installed already):
sudo apt-get install libportaudio19-dev

# Or for PortAudio 18.1
sudo apt-get install libportaudio0

# For the header files of PortAudio 18 (will pull in the above package; can't be installed
# simultaneously with the other package with header files):
sudo apt-get install libportaudio-dev
```
Most libraries are in a package with a name starting with lib. Header files have the suffix -dev for development. So in case of the library **foo**, expect the package names **libfoo** and **libfoo-dev**. But sometimes multiple versions are available.

We seldom need to download source code and install manually, almost never not with libraries.

---

