---
title: "configure: error: Missing a vital header file for id3lib"
date: 2009-03-12
forum: Packaging and Compiling Programs
---

### Post by huangyingw on 2009-03-12
hello, I met this when I wanting to configure the id3lib-3.8.3 package.
I saw following sentence in configure.in file:
=================================================================AC_CHECK_HEADERS(               \
  string                        \
  iomanip.h                     \
  ,,AC_MSG_ERROR([Missing a vital header file for id3lib])
)
=================================================================
So, it means that I am missing the iomanip.h file. 
To resovlve this, what ever action should I do.
Any clue would be greatly appreciated.

---

### Post by geraldm on 2009-03-12
There is a file iomanip in C++ headers.  It has been a while since C++ dropped the ".h" suffix.  Check the documentation in the package you have to see if there are any hints on what version of a C++ compiler to use ?

regards,
Gerald

---

### Post by huangyingw on 2009-03-15
> **geraldm said:**
> There is a file iomanip in C++ headers.  It has been a while since C++ dropped the ".h" suffix.  Check the documentation in the package you have to see if there are any hints on what version of a C++ compiler to use ?


Hey, sorry for late reply.
Thank for your clue. I will try to see if there is any related docs.
I wonder, if it hints on a previous version of C++ compiler, what should I do. Go back to the earlier version. I am afraid that this could cause further conflicts on otehr applicaton.
I would try to replace the iomanip.h with iomanip in the configure.in file.
I am not sure whether would this work. 
Will let you know the result of my try.

---

### Post by marcthenarc on 2010-04-26
I had the same problems.  I ended up removing the iomanip.h condition in the configure file.

Then I added <string.h> on top of two files - include/id3/id3lib_strings.h and include/id3/writers.h - regarding missing function headers.

Compiled and installed fine after that.

---

### Post by johncc330 on 2011-06-14
This mail comes out quite high on Google, so I think it might be worthwhile to complete the info.

To compile the original 3.8.3 id3lib package on a gcc/g++ 4.x compiler, I had to apply a patch available here:

[http://connie.slackware.com/~alien/slackbuilds/id3lib/build/id3lib-3.8.3_gcc4.diff](http://connie.slackware.com/~alien/slackbuilds/id3lib/build/id3lib-3.8.3_gcc4.diff)

(if not applied, something went terribly wrong during compile. 100's of libtool processes were spawned, slowly grinding the CPU to a halt)

Thanks for the original data!
John

---

### Post by iconoclast hero on 2011-09-19
> **johncc330 said:**
> This mail comes out quite high on Google, so I think it might be worthwhile to complete the info.

To compile the original 3.8.3 id3lib package on a gcc/g++ 4.x compiler, I had to apply a patch available here:

[http://connie.slackware.com/~alien/slackbuilds/id3lib/build/id3lib-3.8.3_gcc4.diff](http://connie.slackware.com/~alien/slackbuilds/id3lib/build/id3lib-3.8.3_gcc4.diff)

(if not applied, something went terribly wrong during compile. 100's of libtool processes were spawned, slowly grinding the CPU to a halt)

Thanks for the original data!
John

What do you mean you "had apply a patch?"  How did you go about doing that?

---

### Post by Tedevil on 2012-09-22
> **iconoclast hero said:**
> What do you mean you "had apply a patch?"  How did you go about doing that?

Download [http://connie.slackware.com/~alien/slackbuilds/id3lib/build/id3lib-3.8.3_gcc4.diff](http://connie.slackware.com/~alien/slackbuilds/id3lib/build/id3lib-3.8.3_gcc4.diff) and put it in the same directory as the id3lib-3.8.3.tar.gz file. Then...

tar -xzpvf id3lib-3.8.3.tar.gz
mv id3lib-3.8.3_gcc4.diff id3lib-3.8.3
cd id3lib-3.8.3
patch -p1 < id3lib-3.8.3_gcc4.diff
./configure
make
make install

---

### Post by matt_symes on 2012-09-22
This is an old thread. Closed.

---

