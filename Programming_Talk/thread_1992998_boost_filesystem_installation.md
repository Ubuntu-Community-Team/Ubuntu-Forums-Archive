---
title: "boost_filesystem installation"
date: 2012-06-01
forum: Programming Talk
---

### Post by barjaktar on 2012-06-01
Hello world!

I installed boost as shown in:

[http://www.boost.org/doc/libs/1_49_0/doc/html/bbv2/installation.html](http://www.boost.org/doc/libs/1_49_0/doc/html/bbv2/installation.html)

I did not do step 4, since they say it is optional. Also, the instalation I did withouth PREFIX (so, only ./bjam install) because I did not care where will it install it.

I need install because of other application, boost_filesystem to be correct. Even though I did the installation as mentioned, after I run ./configure in the folder of the application I need, terminal says it does not see boost_filesystem.

I wanted to try to add it to PATH, so I run dpkg -l to see where did it go, where it was installed. Unfortunately, it doesn't list in the output of dpkg -l...

I run Ubuntu 10.04 64 bit.

Any ideas what could be the problem?

Thank you.

---

### Post by dwhitney67 on 2012-06-01
Why did you not install Boost using the Synaptic Package Manager?

The 3rd-party application's configure script is probably looking for the boost_filesystem library in /usr/lib (the actual name of the library is libboost_filesystem.so).

Please report back where you have installed Boost.

---

### Post by barjaktar on 2012-06-05
To be honest - I did not think of that. I just followed instructions given with the software I am trying to install. They just said that I should go to the link and do those steps. I searched in Synaptic for the library under the name you gave me and installed successfully. Thus, I am pass the filesystem problem, thank you.

Nevertheless, I have another problem. Namely, now I miss something called ptree.hpp Here is that part of output of my ./configure command:

checking for main in -lboost_filesystem-mt... yes
checking boost/filesystem.hpp usability... yes
checking boost/filesystem.hpp presence... yes
checking for boost/filesystem.hpp... yes
checking for inttypes.h... (cached) yes
checking for string.h... (cached) yes
checking for main in -lboost_system-mt... yes
checking boost/foreach.hpp usability... yes
checking boost/foreach.hpp presence... yes
checking for boost/foreach.hpp... yes
checking boost/property_tree/ptree.hpp usability... no
checking boost/property_tree/ptree.hpp presence... no
checking for boost/property_tree/ptree.hpp... no
configure: error: boost/property_tree/ptree.hpp was not found

I installed all packages found in Synaptic starting with libboost and I still get the same.

I hope you can help me.

Thank you.

---

### Post by dwhitney67 on 2012-06-05
What version of Boost did you install, or should I say, have?

On my system 12.04 system, I have version 1.46, which I determined by examining the file /usr/include/boost/version.hpp.  Perhaps you could do the same on your system?

As for the file ptree.hpp, it is available on my system exactly where the configure script you are using thinks it ought to be (actually, /usr/include/boost/property_tree/ptree.hpp).

---

### Post by barjaktar on 2012-06-07
The file you mention says it's version 1.40:

#define BOOST_LIB_VERSION "1_40"

Ok, I will now try removing all that I installed and than reinstalling.

Could you, just in case, tell me if you did any additional steps, except Synaptic install? Also which exact components from Synaptic did you install?

Thank you.

---

### Post by barjaktar on 2012-06-07
Ok, i removed everything and updated my system (kernel is 2.6.32-41 now). Still when I run Synaptic I see only version 1.40 libboost components.

How can I update Synaptic to see 1.46? 

I downloaded 1.46 as tar.bz2 but, put it in /opt folder and tried adding the path to boost in PATH variable. Didn't get anywhere, though - I only lost the boost-filesystem for my software...

Any advice?

Thank you.

---

### Post by dwhitney67 on 2012-06-07
If you install Boost 1.46 (or later version) into /opt, you will need to inform 'configure' to look there instead of in /usr/include for the boost header files.  I do not know how to do this.

Does the package that contains the 'configure' script not include a README or INSTALL type of file that contains instructions?

Perhaps another alternative is to update your 10.04 system to 12.04?  I looked at my 10.04 system, and the Boost property_tree is definitely not available with Boost 1.40.  Although with my 12.04 system, which has Boost 1.46, it is.

---

### Post by barjaktar on 2012-06-07
The package does include README, but it just says that I need to have boost - nothing else. Actually, I've no idea what boost is. Concerning 12.04, I tried it a few weeks ago at my home PC and did not like it...

But, I really don't understand what is the problem - when I run [FONT=Courier New]apt-get update[/FONT] and then a[FONT=Courier New]pt-get install libboost-dev [/FONT]I get 1.40 version again. Shouldn't apt-get install get the newest version, 1.49?

Ok, thank you.

I will try moving boost_1.46 to /usr/include and we will see what happens.

Somewhere else I read that property_tree does not need to be installed, only copied.

---

### Post by 11jmb on 2012-06-07
I'm not 100%sure about how it works for boost, but most configure scripts will allow you to do something like

```

./configure --prefix=/usr/

```

this should configure your makefile to install everything in /usr/ including headers in /usr/include

If for some reason, you want to keep everything in /opt/, a quick and very ugly solution would be to a line to /etc/ld.so.conf so that the libraries in /opt can be found when you run ldconfig.

---

### Post by barjaktar on 2012-06-07
Ok, I am not getting anywhere.

Let's try like this. Is there a way for me to point my apt-get from boost_1_40 to boost_1_46_1? Or 49?

---

### Post by 11jmb on 2012-06-07
Forgive me, I didn't actually read your link. Did you try:

```

./bjam install --prefix=/usr

```

This should put the boost headers into /usr/include for you

If your configure script does not find it after that, try

```

sudo ldconfig
./configure

```

---

### Post by dwhitney67 on 2012-06-07
> **11jmb said:**
> Forgive me, I didn't actually read your link. Did you try:

```

./bjam install --prefix=/usr

```

This should put the boost headers into /usr/include for you


I'm attempting to perform the steps that the OP will have to do to install Boost 1.46.  Setting the prefix to /usr is actually correct, for bjam will install Boost header files in <prefix>/include/boost and libraries in <prefix>/lib.

P.S.  Here are the steps I performed:
```

sudo -i

mkdir /tmp/boost

cd /tmp/boost

wget -c 'http://sourceforge.net/projects/boost/files/boost/1.46.1/boost_1_46_1.tar.bz2/download'

tar xf download

cd boost_1_46_1/

./bootstrap.sh --prefix=/usr

./bjam install

```

---

### Post by barjaktar on 2012-06-08
Thank you guys, but I still have a problem.

I did all dwhitney67's steps and got filesystem error again. Then I tried ldconfig as 11jmb said - still the same.

Maybe I am doing something wrong with the application that I am trying to install. Here is what I do:

I download from [https://sourceforge.net/projects/avrprog2/](https://sourceforge.net/projects/avrprog2/)

then untar (right there in Downloads - does the location matter?) and cd avrprog2-1.3.1 I run ./configure as root... 

Do I need to change PATH variable? Should I untar avrprog2 archive somewhere else?

Thank you.

---

### Post by dwhitney67 on 2012-06-08
I downloaded the "avrprog" package from SourceForge onto my 10.04 system.  Yesterday I went through the steps, which I outlined previously, to install Boost 1.46.

To build the "avrprog" package, I had to first install the following packages:
```

sudo apt-get install binutils-dev      # this provides libiberty

sudo apt-get install libusb-1.0-0.dev  # this provides libusb-1.0

```

Then I had to edit the configure file to remove "-mt" from the Boost libraries that are referenced; these include libboost_filesystem-mt and libboost_system-mt.

I've attached the configure script that I used to successfully build the "avrprog" source files.  Please note that I renamed this file to configure.pdf to get around the file-size restrictions imposed by the forum.

The steps I took to build "avrprog" include the following:
```

tar xzvf avrprog2-1.3.1.tar.gz

cd avrprog2-1.3.1

mv configure configure.orig

cp ~/Downloads/configure.pdf configure

./configure

make clean

make

sudo make install

```

---

### Post by barjaktar on 2012-06-08
Are you sure you sent me the correct version of configure? Because I still get:

checking for main in -lboost_filesystem-mt... no
configure: error: boost_filesystem library was not found

I really have no idea what is inside configure, or what should be, but I see that the file you sent me also has the same -mt or _MT stuff as the configure.orig... Should I just go Find&Replace and kill all -mt instances? Could you check the file, please?

Thank you.

---

### Post by barjaktar on 2012-06-08
Yep, that was it - you sent attached wrong configure. I just went in and replaced all -mt and _MT with nothing and I got pass the error. 

Thank you very very much.

I was waiting for this kind of software, and it means a lot to finally have it. MikroE does not support GNU/Linux so there was no way to use their programmer here. Now I can stop using Windows for this.

I'll probably be back with  AVR Studio Linux problems :)

Once again, thank you very much!

p.s. For future use, here is the correct configure file (also renamed as .pdf)

---

### Post by dwhitney67 on 2012-06-08
> **barjaktar said:**
> Yep, that was it - you sent attached wrong configure.

](*,)   Dooh!  Sorry about that.  I'm glad that you finally got the application built/installed.

---

