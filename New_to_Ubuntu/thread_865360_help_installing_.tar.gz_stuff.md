---
title: "help installing .tar.gz stuff"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by cpu_medic on 2008-07-20
ok so i downloaded simdock, and it came as simdock_1.2.tar.gz. i have opened a terminal and cd'd to the directory. then i use "./configure" and it says
medic@medic-laptop:~/Desktop/trunk$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.

what am i doing wrong? by the way im using ubuntu 7.10

---

### Post by TSS on 2008-07-20
I suspect you need to do:
```
sudo ./configure
```
If you look in config.log (where it says it logged the errors) you will probably see something about permissions being denied.

---

### Post by cpu_medic on 2008-07-20
nope it gave me the same error

---

### Post by tjwoosta on 2008-07-20
.tar.gz is simply the compression method  (kinda like a .zip or a .rar)

what you are trying to do is compile the source

to compile source you will need build-essential
```
sudo apt-get install build-essential
```

so first extract your .tar.gz to your home folder  (or wherever)

(just right click it and click extract here)

then  navigate to the directory that you extracted

read the readme file thats included and install any required dependencies (if any)

then open a terminal and cd to the newly extracted directory

then

```
./configure
```  **dont use sudo**

then
```
make
```
then 

```
sudo make install
```

---

### Post by TSS on 2008-07-20
D'oh!  Sorry, I didn't read your error message carfully enough.  You don't have a compiler installed.
```
sudo apt-get install build-essential
```

---

### Post by cpu_medic on 2008-07-20
anybody know whats wrong

---

### Post by TSS on 2008-07-20
> **cpu_medic said:**
> anybody know whats wrong

See the posts above, they should fix the problem.

---

### Post by cpu_medic on 2008-07-20
ok so i got farther than last time but i still get this

checking for DEPS... configure: error: Package requirements (
        gconf-2.0 >= 2.18.0,
        libwnck-1.0 >= 2.18.0

how do i get those?

---

### Post by Xerp on 2008-07-20
Just a question - why are you trying to compile it rather than use the normal "apt get" method of installation for simdock? You could also get the .deb

[http://downloads.sourceforge.net/simdock/simdock_1.2_i386.deb?modtime=1183973671&big_mirror=0](http://downloads.sourceforge.net/simdock/simdock_1.2_i386.deb?modtime=1183973671&big_mirror=0)

---

### Post by TSS on 2008-07-20
> **cpu_medic said:**
> ok so i got farther than last time but i still get this

checking for DEPS... configure: error: Package requirements (
        gconf-2.0 >= 2.18.0,
        libwnck-1.0 >= 2.18.0

how do i get those?

In general, when compiling an application, the dependencies should be listed in the README or in the documentation.  You can save yourself time by looking them up before hand.

Use the Synaptic Package Manager to search for those libraries, and install them if they are available. In your case, both of those are available in the repositories, so it will be easy to install them.  If you can't find them in the repositories, you can Google for them, and install them just like you are doing for this program.

EDIT: As the poster above me just pointed out, unless you have a good reason to compile from source, this will install simdock:
```
sudo apt-get install simdock
```

---

### Post by cpu_medic on 2008-07-20
i diddnt know you could apt-get simdock. plus id kinda like tolearn for future refrence

---

### Post by steveneddy on 2008-07-20
Many people will apt-get as much as possible.

If you get dependency errors, just DL the packages that you need and carry on.

Try opening up Synaptic and have a look around there.

System --> Administration --> Synaptic Package Manager

---

### Post by Tim Sharitt on 2008-07-20
To add to what steveneddy said, when you get dependency errors when compiling from source you may have the package installed but need to install the development files. For example, if some library is needed but synaptic says it is installed look for "library name"-dev.

---

