---
title: "error while loading shared libraries?"
date: 2006-03-06
forum: Programming Talk
---

### Post by kel on 2006-03-06
hi, I'm testing out a little bit of fmod code using eclipse cdt. The code compiles fine, but when i try to run it through eclipse I get this error in the eclipse console: 
```

/home/me/workspace/FMODTEST/Release/FMODTEST: error while loading shared libraries: libfmodex.so: cannot open shared object file: No such file or directory

```
I think I've installed fmod correctly as the fmod headers ended up in /usr/local/include/ and the .so files are in  /usr/local/lib/

As far as I know the .so files the linux equivalent of windows .dll file, but i carn't be sure on this, but, I've tried placing the .so fies in the same dir as the binary but I still get the same error when I try to launch the app.

Anyone know what I should be doing here, and where I've gone wrong?

Cheers.

---

### Post by hod139 on 2006-03-06
Make sure /usr/local/lib exists in /etc/ld.so.conf or LD doesn't know where to search. After editing the file, make sure to run 
```

sudo ldconfig

``` 
Alternatively, you can run
```

LD_LIBRARY_PATH=/usr/local/lib ./FMODTEST

```
which tells LD where to look at runtime, but typing it gets old fast.

---

### Post by kel on 2006-03-06
opps, I don't seem to have a ld.so.conf in /etc/,  is this a sign thats somthing gone wrong somewhere?

I've serched google for a solution to this today and I kept finding references ld.so.conf and as I didn't have one o thought that it might be somewhere else on ubuntu, or something : )

---

### Post by hod139 on 2006-03-06
I'm not sure why that file is missing.  Did LD load the shared library if you set the variable```

LD_LIBRARY_PATH=/usr/local/lib

```
before executing

---

### Post by kel on 2006-03-06
Yeah if I cd to the dir and type LD_LIBRARY_PATH=/usr/local/lib ./FMODTEST that works fine, cheers for that.

Scratching my head over the missing  ld.so.conf though.  Although I'm going to reinstall from scratch when dapper gets released I'd still like to know why the file is missing.

Could I just create one, or would that be a bad idea?

---

### Post by hod139 on 2006-03-06
I don't see how making one could hurt.  The only line in my version is /usr/local/lib

---

### Post by kel on 2006-03-06
Cheers hod, creating one then running sudo ldconfig seems to work.

Something is wrong with my install though, I was following this guide [ [https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA) ] after experiencing some slight DVD playback stuttering, and if I type: "sudo hdparm /dev/hdc" I get this back:  "/dev/hdc: No such file or directory" 

But thats a whole other problem, I'll worry about that after I've installed the Dapper release :D

Thank again

---

### Post by ethan33 on 2010-07-20
Does, ld.so.conf.d, count? This is the closest to ld.so.conf I could find on Ubuntu 10.04.

---

### Post by dwhitney67 on 2010-07-20
Yes, that is the correct location; you should have a file called libc.conf in there; if not create it.

Here's what's inside /etc/ld.so.conf.d/libc.conf:
```

# libc default configuration
/usr/local/lib

```
You will need to be sudo (root) to create the file; after you are done creating it, update your ldconfig cache with this command:
```

sudo ldconfig 

```

---

### Post by ethan33 on 2010-07-20
When I go into /etc the closest to ld.so.conf is ld.so.conf.d. Is that exceptable, or do I need to add a file to the etc directory?

I'm using Ubuntu 10.04.

---

### Post by ethan33 on 2010-07-20
Never mind I didn't see the response before I posted my last comment.

---

### Post by ethan33 on 2010-07-20
Okay so the libc.conf was in the right place and had the proper content, but I'm still having configure test errors.

Here is the error.

```
./regress: error while loading shared libraries: libmk4.so: cannot open shared object file: No such file or directory
make: *** [test] Error 127

```Is this somehow different? Or what's going on? I'll see if the other option listed will make it work.

Thanks for the help so far.

[EDIT] Okay, that didn't work out well. Maybe I didn't implement it properly? Here's what I typed.

```
sudo make test LD_LIBRARY_PATH=/usr/local/lib ./fmodtest
```

P.S. I'm trying to compile metakit. Maybe that has something to do with it?

---

### Post by ethan33 on 2010-07-20
Anybody know what's going on here? 

I posted another thread about the problem and got sent here. Here is a link to the original information, and yes, I have been having this problem for a while. [http://ubuntuforums.org/showthread.php?t=1410445](http://ubuntuforums.org/showthread.php?t=1410445)

---

### Post by dwhitney67 on 2010-07-20
This is what I normally do:

1.  Build library

2.  Install library in /usr/local/lib

3.  Install header files in /usr/local/include


Perhaps the library you are building allows you to specify where the "products" ought to be installed.  It has been a long time since I have built something from scratch (ie.  the 'configure', 'make', 'make install' steps), but if that is what you are doing, check the documentation to see if they recognize the DEST variable (or something similar) as the location where to install the products.

Once you are done installing the products, then you need to run 'sudo ldconfig'.

Lastly, and I state this with reservations, if you do not understand any of what I have written above, then you should cease and desist any attempts to install a library on your system.  Linux is based on "open" software and, as I would like to believe, open documentation.  If something doesn't work as described in a "README" or "INSTALL" text document, then perhaps you are dealing with 1) rogue software that can be detrimental to your system, or 2) lame excuse for software.

-----------------

P.S.  I just read the link; have you tried:

1.  ./configure
2.  make
3.  sudo make install


P.S #2.  Sometimes (oftentimes), steps 2 and 3 can be combined into "sudo make install".

---

### Post by jw37 on 2010-07-21
Hi all,

my problem is that LD_LIBRARY_PATH mysteriously disappears from env after few hours or so. :???:

I use:
```
export LD_LIBRARY_PATH=/usr/local/boost_1_43_0/stage/lib:$LD_LIBRARY_PATH
```

I think it **should** stay there until i remove it. :confused:


Edit: I followed earlier advice in this thred and made file /etc/ld.so.conf.d/libboost.conf containing

```
# boost libraries
/usr/local/boost_1_43_0/stage/lib
```

and it works fine (after "sudo ldconfig"). I hope that this file doesn't mysteriously disappear... ;)

---

### Post by dwhitney67 on 2010-07-21
If the LD_LIBRARY_PATH is defined/exported from within your ~/.bashrc file, then surely it will always be available from within a terminal.

If you are using an IDE to do the work of running your application, then then who knows.  IDE's tend to mask too much with what is going on.  Personally I dislike them.


P.S.  Your final solution, to update /etc/ld.so.conf.d with a new file is a good solution.  But for temporary libraries you may want to tinker with, learn to sort out the LD_LIBRARY_PATH solution as well.

---

### Post by ethan33 on 2010-07-21
> **dwhitney67 said:**
> 
-----------------

P.S.  I just read the link; have you tried:

1.  ./configure
2.  make
3.  sudo make install


P.S #2.  Sometimes (oftentimes), steps 2 and 3 can be combined into "sudo make install".

Well, it seems that the read me had me skip "make" and instead use "make test", but the read me was made for Unix. When I followed your instructions it didn't give me any errors, but it only gave me seven lines of code and stopped. I don't know if this is a good thing or a bad thing. However, I do have a metakit file in "/usr/lib/". So, maybe it finally installed?

Here's the output:

```
mkdir -p /usr/local/include /usr/local/lib
/usr/bin/install -c -m 644 ./../include/mk4.h \
            ./../include/mk4.inl \
            ./../include/mk4str.h \
            ./../include/mk4str.inl /usr/local/include
/usr/bin/install -c libmk4.so /usr/local/lib
if [ '.so' = '.a' ]; then ranlib /usr/local/lib/libmk4.a; fi
```BTW, I've tried compiling both FlightGear and Cinelerra, and they both seemed to have the same problem as metakit. Maybe it's solved, I don't know. I'll try Cinelerra again.

[EDIT] I just realized that Cinelerra has a problem with mmx. I might be able to fix that.

---

