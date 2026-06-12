---
title: "cmake can't find java paths"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by S.G. on 2008-07-27
Hello.

My cmake doesn't find java... and I have only one java version.

When I execute the command:

```
 cmake /usr/local/kfs 
```

I get the following error:

```
 
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Found Log4cpp: /usr/lib/liblog4cpp.so
-- Setting build type to Debug
-- Linking with static libs
-- Found JNI...building kfs_access
CMake Error: This project requires some variables to be set,
and cmake can not find them.
Please set the following variables:
JAVA_INCLUDE_PATH (ADVANCED)
JAVA_INCLUDE_PATH2 (ADVANCED)

```

What can I do for cmake to get the paths by itself? :confused:

Thank you in advance,

S.

The story:
I'm trying to install KFS. I've got some compilation errors and I've asked for help in some forums. I've been told it was because I was mixing java versions. So I uninstalled all java versions and re-installed just one. The result is that I get more errors (by far) now.
I think the problem has something to do with symlinks.

So I've put in my /usr/java folder a symlink pointing to /usr/lib/jvm/java-6-sun-1.6.0.03 which I have renamed to java-6-sun, after the symlink I've got in /usr/lib/jvm/ and that was automatically created during the installation. I created it by doing sudo nautilus and right clicking on the desired folder to choose "create symlink", and then cutting and pasting it in the adequate folder. The icon doesn't appear "broken", so I guess it's all right.

Also there is a possibility I have uninstalled something I need. I have only now sun-java6-* from synaptic. If I do:

```

sudo update-alternatives --config java

```

I get:

```

There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.

```


By the way, the same cmake command does not find something called Doxygen Dot Executable (whereas it does find Doxygen). That worries me a bit too.

---

### Post by cozmicharlie on 2008-07-27
You should not have needed to create the symlink.  I have sunJava6-jre installed and it created the symlink - I did not have to go in and create it manually.  Also, did you try it before you changed the name of the folder?  In my java folder I have the symlink and the java folder named java-6-sun-1.6.0.06.  fyi I always install the java6-fonts also.

---

### Post by S.G. on 2008-07-27
Hello, Cozmicharlie,

Well, let's see...

I created the symlink after installing java, because I saw /usr/java/ was empty and had read somewhere that some software will search first there.

I have installed all packages starting with java6-. fonts, doc, source... all the lot. Maybe that wasn't such a good idea? :confused:

I've just tried to make another symlink which with I have replaced the one I first created, without touching the name. Same problem: java isn't found yet.

Thanks a lot for your suggestions... there must be some way. 

Can you think of any other possibility?

Regards,

S.

---

### Post by cozmicharlie on 2008-07-27
Your installs are Ok.

Not sure why it is not creating the symlink for you but it's there so I don't think that is the problem.

You will probably have to tell it the path with a command like this.  But,  don't use this because I am not familiar enough with doing this to know the exact command.  Hopefully, someone will come along that knows more than me.

PATH=$PATH:~/usr/lib/jvm/java-6-sun-1.6.0.03

*again, don't use this command because I don't know if it is right but this is the type of command you will need.*

Sorry I ould not be of more help

---

### Post by txcrackers on 2008-07-27
This really doesn't have anything to do with Java symlinks - it's asking for the path to the Java .h include files.

Try this before invoking cmake:
```

export JAVA_INCLUDE_PATH=/usr/lib/jvm/java-6-sun/include
export JAVA_INCLUDE_PATH2=/usr/lib/jvm/java-6-sun/include/linux

```

---

### Post by S.G. on 2008-08-01
> **txcrackers said:**
> This really doesn't have anything to do with Java symlinks - it's asking for the path to the Java .h include files.

Try this before invoking cmake:
```

export JAVA_INCLUDE_PATH=/usr/lib/jvm/java-6-sun/include
export JAVA_INCLUDE_PATH2=/usr/lib/jvm/java-6-sun/include/linux

```


Thanks a lot, but... Alas, it didn't work...

```

a@a-desktop:/usr/local/MyKFS/kfs/build/debug$ sudo cmake /usr/local/MyKFS/kfs
[sudo] password for a: 
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Found Log4cpp: /usr/lib/liblog4cpp.so
-- Setting build type to Debug
-- Found JNI...building kfs_access
CMake Error: This project requires some variables to be set,
and cmake can not find them.
Please set the following variables:
JAVA_INCLUDE_PATH (ADVANCED)
JAVA_INCLUDE_PATH2 (ADVANCED)

-- Configuring done
a@a-desktop:/usr/local/MyKFS/kfs/build/debug$ $echo $JAVA_INCLUDE_PATH2
bash: /usr/lib/jvm/java-6-sun/include/linux: is a directory
a@a-desktop:/usr/local/MyKFS/kfs/build/debug$ $echo $JAVA_INCLUDE_PATH2
bash: /usr/lib/jvm/java-6-sun/include/linux: is a directory
a@a-desktop:/usr/local/MyKFS/kfs/build/debug$ 

```

Any other suggestion?

---

### Post by chw2054 on 2008-10-07
Try this
[HTML]cmake -DJAVA_INCLUDE_PATH=/usr/lib/jvm/java-sun-6/include \
-DJAVA_INCLUDE_PATH2=/usr/lib/jvm/java-6-sun/inlclude/linux  \
~/src/kfs/
[/HTML]

---

### Post by tinti on 2008-10-11
Thanks, it works for me.


Linux oban 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

ii  cmake                                      2.4.7-1build1                            A cross-platform, open-source make system
ii  java-common                                0.28ubuntu3                              Base of all Java packages
ii  libboost-date-time-dev                     1.34.1-4ubuntu3                          set of date-time libraries based on generic
ii  libboost-date-time1.34.1                   1.34.1-4ubuntu3                          set of date-time libraries based on generic
ii  libboost-dbg                               1.34.1-4ubuntu3                          Boost C++ Libraries with debug symbols
ii  libboost-dev                               1.34.1-4ubuntu3                          Boost C++ Libraries development files
ii  libboost-doc                               1.34.1-4ubuntu3                          Boost.org libraries documentation
ii  libboost-filesystem-dev                    1.34.1-4ubuntu3                          filesystem operations (portable paths, itera
ii  libboost-filesystem1.34.1                  1.34.1-4ubuntu3                          filesystem operations (portable paths, itera
ii  libboost-graph-dev                         1.34.1-4ubuntu3                          generic graph components and algorithms in C
ii  libboost-graph1.34.1                       1.34.1-4ubuntu3                          generic graph components and algorithms in C
ii  libboost-iostreams-dev                     1.34.1-4ubuntu3                          Boost.Iostreams Library development files
ii  libboost-iostreams1.34.1                   1.34.1-4ubuntu3                          Boost.Iostreams Library
ii  libboost-program-options-dev               1.34.1-4ubuntu3                          program options library for C++
ii  libboost-program-options1.34.1             1.34.1-4ubuntu3                          program options library for C++
ii  libboost-python-dev                        1.34.1-4ubuntu3                          Boost.Python Library development files
ii  libboost-python1.34.1                      1.34.1-4ubuntu3                          Boost.Python Library
ii  libboost-regex-dev                         1.34.1-4ubuntu3                          regular expression library for C++
ii  libboost-regex1.34.1                       1.34.1-4ubuntu3                          regular expression library for C++
ii  libboost-serialization-dev                 1.34.1-4ubuntu3                          serialization library for C++
ii  libboost-serialization1.34.1               1.34.1-4ubuntu3                          serialization library for C++
ii  libboost-signals-dev                       1.34.1-4ubuntu3                          managed signals and slots library for C++
ii  libboost-signals1.34.1                     1.34.1-4ubuntu3                          managed signals and slots library for C++
ii  libboost-test-dev                          1.34.1-4ubuntu3                          components for writing and executing test su
ii  libboost-test1.34.1                        1.34.1-4ubuntu3                          components for writing and executing test su
ii  libboost-thread-dev                        1.34.1-4ubuntu3                          portable C++ multi-threading
ii  libboost-thread1.34.1                      1.34.1-4ubuntu3                          portable C++ multi-threading
ii  libboost-wave-dev                          1.34.1-4ubuntu3                          C99/C++ preprocessor library
ii  libboost-wave1.34.1                        1.34.1-4ubuntu3                          C99/C++ preprocessor library
ii  liblog4cpp5                                1.0-2                                    C++ library for flexible logging (runtime)
ii  liblog4cpp5-dev                            1.0-2                                    C++ library for flexible logging (developmen
ii  sun-java6-bin                              6-06-0ubuntu1                            Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-jdk                              6-06-0ubuntu1                            Sun Java(TM) Development Kit (JDK) 6
ii  sun-java6-jre                              6-06-0ubuntu1                            Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-plugin                           6-06-0ubuntu1                            The Java(TM) Plug-in, Java SE 6

---

