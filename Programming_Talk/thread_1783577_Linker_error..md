---
title: "Linker error."
date: 2011-06-15
forum: Programming Talk
---

### Post by akshay.sulakhe on 2011-06-15
Hello friends, I am trying to "make" a program which is based on ariba,which is a component of Spovnet. When i give the command make,i get the following error:- 

/home/akshay/Downloads/ariba-0.7.0/sample/pingpong/.libs/lt-pingpong: error while loading shared libraries: libboost_system.so.1.46.1: cannot open shared object file: No such file or directory


when i run find for the above file,it is there. when i googled,i got this link:- [http://stackoverflow.com/questions/5933879/boost-and-cpp-netlib-make-compile-error](http://stackoverflow.com/questions/5933879/boost-and-cpp-netlib-make-compile-error)

But i am unable to understand what it says,and is it correct for my case. I am also attaching the make file,kindly have a look. thanks.

---

### Post by cgroza on 2011-06-15
Do you have all the required libraries installed?

---

### Post by akshay.sulakhe on 2011-06-15
Yes.....I have all libraries installed.... :-)

---

### Post by dwhitney67 on 2011-06-16
> **akshay.sulakhe said:**
> Yes.....I have all libraries installed.... :-)

Please verify, and post results from running this command:
```

ll /usr/lib/libboost_system*

```

P.S.  If you are running the latest version of Ubuntu (11.04), I believe from what I have read that the 32-bit and 64-bit libraries are located in distinct directories, and that the 32-bit directory is no longer /usr/lib but something else.  I have no way of verifying this.

---

### Post by akshay.sulakhe on 2011-06-16
Ok. the command u gave ll,it does not exist. i tried installing it too. but no luck. so,i am using the following command 

find / -name "libboost_system.*"


the output i will post in pastebin at :- 

[http://pastebin.com/35zPEM3k](http://pastebin.com/35zPEM3k)

---

### Post by dwhitney67 on 2011-06-16
No doubt the Makefile has not been told that your Boost libraries are located in /usr/local/lib.

If you are running Ubuntu, you do know that you can get the Boost libraries via the Synaptic Package Manager?  It appears though that you opted for a self-installation of the libraries into /usr/local/lib.

If you want to continue along with using /usr/local/lib, you have two options:

1.  Update the LDFLAGS within the Makefile with something like:
```

LDFLAGS = -L/usr/local/lib -lboost_system

```

2.  Update /etc/ld.so.conf.d/libc.conf to include the path /usr/local/lib, and then run ldconfig.  You will need to be root (sudo) to do this.

As an alternative to editing libc.conf, you could just as well create a new file, say boost_lib.conf, and place the /usr/local/lib path in there.


P.S.  In the future, please do not post to pastebin.  You can post here on this forum.

---

### Post by akshay.sulakhe on 2011-06-16
Can you tell me exactly where i should should create the boost.conf file,what shud i write in it. Also can i still install boost libraries from synaptic,but my makefile doesnt know.so whats the use anyways of installing it via synaptic now. Many thanks...

---

### Post by dwhitney67 on 2011-06-16
> **akshay.sulakhe said:**
> Can you tell me exactly where i should should create the boost.conf file,what shud i write in it. Also can i still install boost libraries from synaptic,but my makefile doesnt know.so whats the use anyways of installing it via synaptic now. Many thanks...

Follow these steps:
```

sudo echo "/usr/local/lib" > /etc/ld.so.conf.d/boost.conf

sudo ldconfig

```

Then retest your Makefile.

---

### Post by Arndt on 2011-06-16
> **akshay.sulakhe said:**
> Ok. the command u gave ll,it does not exist. i tried installing it too. but no luck. so,i am using the following command 

find / -name "libboost_system.*"


"ll" is usually an alias to "ls -l".

---

### Post by JupiterV2 on 2011-06-16
He could also make a symlink from /usr/lib/libboost*.so => /usr/local/lib/libboost*.so, could he not? (Where the * is replaced by whatever the proper name for the library is)

---

### Post by dwhitney67 on 2011-06-16
> **JupiterV2 said:**
> He could also make a symlink from /usr/lib/libboost*.so => /usr/local/lib/libboost*.so, could he not? (Where the * is replaced by whatever the proper name for the library is)

Yep!  There's a lot of ways to skin the cat; but I do not recommend what you are suggesting.  The best way would be to install the Boost library via Synaptic.

Btw, the reason I would not suggest your approach is because in the future, the OP may need other boost libraries and possibly other libraries that are installed in /usr/local/lib.  The approach I indicated in my previous posts are typically the accepted solutions:  either correct the Makefile, or augment the ld cache with new directory paths.

---

### Post by akshay.sulakhe on 2011-06-16
@all :- thank u very much...the echo command worked....i can run the code now...Many thanks.. :-)

---

