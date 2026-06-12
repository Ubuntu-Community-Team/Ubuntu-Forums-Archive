---
title: "where is libgcc_s"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by mark allyn on 2012-09-14
Hello everyone,
 
I am attempting to create a Fortran 77 (g77-3.4) executable on 12.04.  g77-3.4 compiler works fine and creates the .o file.  Problems arise with the linker.  LD complains that it can't find -lgcc_s.  And a quick look in the filesystem indicates that indeed there ain't one.  Can someone tell me which package contains a version of this library?  It is probably a fairly old one given the advanced age of Fort 77.  
 
Thank you.
 
Mark Allyn

---

### Post by steeldriver on 2012-09-14
Mark, apt-file shows it's in a whole bunch of gcc packages (one for every arch possibly?) - I can paste them if it would help however on my 12.04 xubuntu box I get these specific locations:

```
$ sudo find / -name 'libgcc_s*' 2>/dev/null
/usr/lib/gcc/i686-linux-gnu/4.6/libgcc_s.so
/lib/i386-linux-gnu/libgcc_s.so.1
```

Hope this helps

---

### Post by mark allyn on 2012-09-14
Thanks, steeldriver.
 
It may very well help.  I tried the find \ command but without sudo.  Will give it a try and let you know what happens.  If I have to go back to a .deb package, do you happen to know what the package name might look like?  I don't have internet capability on my 12.04 box, so I have to download and burn a CD from another machine that does have internet service.  Slow, but it works.
 
Just so you know.  The reason I'm trying to make g77 link is because I'm trying to install octave 3.6.3 and it has a requirement to be able to compile a g77 file.
 
Regards,
Mark

---

### Post by steeldriver on 2012-09-14
Here's the apt-file search pruned of some of the non-native cruft:

```
$ apt-file search -x '\/libgcc_s\.' | grep -Ev 'arm|multi|cross|snap|mingw'
gcc-4.4: /usr/lib/gcc/i686-linux-gnu/4.4/libgcc_s.so
gcc-4.5: /usr/lib/gcc/i686-linux-gnu/4.5/libgcc_s.so
gcc-4.6: /usr/lib/gcc/i686-linux-gnu/4.6/libgcc_s.so
lib64gcc1: /lib64/libgcc_s.so.1
lib64gcc1-dbg: /usr/lib/debug/lib64/libgcc_s.so.1
libgcc1: /lib/i386-linux-gnu/libgcc_s.so.1
libgcc1-dbg: /usr/lib/debug/lib/i386-linux-gnu/libgcc_s.so.1
lsb-build-base3: /usr/lib/lsb3/libgcc_s.so

```

so it looks like either the standard gcc-X.Y compiler package or possibly libgcc1 (whatever that is)

Might it be an assembler lib (based on the _s)?

---

### Post by Frogs Hair on 2012-09-14
Here is the description of libgcc1 in synaptic . You can look at properties and dependencies from synaptic also.

---

### Post by mark allyn on 2012-09-14
Hi Steeldriver and Frog's Hair
 
Looks to me like it must be libgcc1.  I'll give that a try.  It is getting a bit late here and dinner is waiting so I won't be able to tell you what happened until tomorrow, but I will give you the results.  I think I'm in love with this forum.  So very helpful.
 
Thanks,
Mark

---

### Post by mark allyn on 2012-09-15
Hi again,
 
It was indeed in libgcc1.  I found the correct version of libgcc1 and attempted to install it, but it turned out to have dependency on gcc-4.2-base.  Got that, installed it and then was able to install libgcc1.  After finagling the library path I was able to compile AND link the fortran program and it ran.  So far, so good.
 
But, that's not the end of the story by any means.  Somehow I managed to trash the path between GCC 4.6 so that the ld step cannot find the appropriate -lgcc_s library for linking a C program.  The shared object is libgcc_s.so.  I found it in /usr/lib/gcc/i686-linux-gnu/4.6 but I can't figure out how to get ld to look in that library.
 
How do I do that?
 
Regards,
Mark

---

### Post by steeldriver on 2012-09-15
Glad you are making progress 

I'm just guessing here but I would think this is a lib that gcc needs, rather than something that octave needs to find at runtime? maybe all it needs is a symlink from wherever the libgcc1 package installed it back to the main gcc-4.x directory? That seems to be how mine is:

```
$ sudo find / -name 'libgcc_s*' -exec ls -l {} \; 2>/dev/null
lrwxrwxrwx 1 root root 33 Apr 15 19:45 /usr/lib/gcc/i686-linux-gnu/4.6/libgcc_s.so -> /lib/i386-linux-gnu/libgcc_s.so.1
-rw-r--r-- 1 root root 116232 Apr 15 19:42 /lib/i386-linux-gnu/libgcc_s.so.1
```

EDIT: just done a bit more digging, it looks like it *is* added to the system ldconfig

```

$ ldconfig -p | grep libgcc
    libgcc_s.so.1 (libc6) => /lib/i386-linux-gnu/libgcc_s.so.1
$

```so if the simple symlink is not enough you may need to do that - it's a bit out of my comfort zone but I *think* all that takes is for you to create a file in /etc/ld.so.conf.d/ with the appropriate directories listed in it, then run ldconfig to update

```

$ ls -l /etc/ld.so.conf.d/
total 8
lrwxrwxrwx 1 root root  40 Aug 24 20:04 i386-linux-gnu_GL.conf -> /etc/alternatives/i386-linux-gnu_gl_conf
-rw-r--r-- 1 root root 108 Apr 19 20:53 i686-linux-gnu.conf
-rw-r--r-- 1 root root  44 Apr 19 19:10 libc.conf

``````

$ cat /etc/ld.so.conf.d/i686-linux-gnu.conf 
# Multiarch support
/lib/i386-linux-gnu
/usr/lib/i386-linux-gnu
/lib/i686-linux-gnu
/usr/lib/i686-linux-gnu

```

**It's possible that just reinstalling the 2 packages in the opposite  order will do all this  automatically**

---

### Post by mark allyn on 2012-09-15
Good afternoon, steeldriver,
 
Yes, it is happening when I invoke GCC to do the link step.  G77 seems to work fine.  My copy of libgcc_s.so is in the same directory as is yours.  I tried to do LD_LIBRARY_PATH =/usr/lib/gcc/i686-linux-gcc:$LD_LIBRARY_PATH followed on the next line with an export LD_LIBRARY_PATH, but this was not successful in getting ld to find the library.  This is mysterious to me, but I imagine you know the answer.
 
My version of GCC-4.6 is in /usr/bin.  I am not clear why you would symlink to this directory.
 
Thanks for helping out.  I am still very much feeling my way around linux, as you no doubt can tell.
 
Regards,
Mark

---

### Post by steeldriver on 2012-09-15
Hmm... well LD_LIBRARY_PATH should work if you don't want to go the ldconfig route - it's frowned upon these days but I think given the other constraints you are under nobody will complain too much - you can always use ldconfig later once you manage to get the thing to build

In my case all the libs are actually in the i386- dirs not the i686- dirs (which are actually non existent in spite of being referenced in the ldconfig conf file) - are you sure yours are not the same? if that is the case I would try

```
export LD_LIBRARY_PATH=/lib/i386-linux-gnu:/usr/lib/i386-linux-gnu:$LD_LIBRARY_PATH
```

['export' on a separate line is fine as well - the default LD_LIBRARY_PATH is unset so you might want to just do

```
export LD_LIBRARY_PATH=/lib/i386-linux-gnu:/usr/lib/i386-linux-gnu
```

if you want to start from scratch]

---

### Post by steeldriver on 2012-09-15
BTW if you need any encouragement I got octave-3.6.2 to configure and build on a fairly clean Mint13 VM last night (something I've been needing to do for a while - I have some MATLAB scripts that I need to convert to octave, using some octave-forge libs that aren't compatible with the repo version). The sufficient prerequisites were

[LIST]
[*]build-essential
[*]autoconf (installs automake as well)
[*]gfortran
[*]libpcre3-dev (some perl regex stuff apparently)
[*]libatlas-dev
[*]liblapack-dev
[*]libreadline6-dev
[/LIST]
 *Some* of these might be optional if you play with the ./configure options (I didn't) and some substitutions might be possible if they are easier for you to get ahold of  (e.g. BLAS for ATLAS). This is for a pure commandline build (neither the native graphics support - which requires GL stuff I think - nor gnuplot).

At this point it configured and built OK; I was able to execute the ./run-octave script and the octave shell appeared functional, but without the online help system.

I then installed

[LIST]
[*]texinfo
[*]texlive
[/LIST]
 which appears to fix that - good luck!

---

### Post by mark allyn on 2012-09-15
Hello again, steeldriver:
 
I think I might have figured out why LD_LIBRARY_PATH didn't work.  Only a theory at the moment.  When I went looking thru all the subdirectories one-by-one until I reached libgcc_s.so it appeared that there were several in the middle that I hadn't included in my LD_LIBRARY_PATH variable...They didn't show up on the find / -name list...as if the library path had been simplified or truncated.  Or perhaps I misread the output.
 
I haven't had the opportunity to try out a different path for the LD_LIBRARY_PATH variable yet, but will be able to in about 0.5 hours.  So, please stay tuned.
 
Now, as for LD_CONFIG.  I don't understand this command and how it works.  This would be a fine opportunity to learn, however, in particular because I don't want to have to do the thing every time I boot up.  And, I'm not clear how to edit .bashrc either.  So many things I don't know....
 
Regards,
Mark

---

### Post by steeldriver on 2012-09-15
My apologies Mark - I probably misdirected you above (paying to much attention to the ldconfig conf file). The way these things work is that there is an actual library somewhere, in my case

```
/lib/i386-linux-gnu/libgcc_s.so[COLOR=Red].1[/COLOR]
```which is symbolically linked back to the library dir for whatever version of gcc you are running, e.g.

```
$ ls -l /usr/lib/gcc/i686-linux-gnu/4.6/libgcc_s.so
lrwxrwxrwx 1 root root 33 Aug 24 20:05 [COLOR=Red]/usr/lib/gcc/i686-linux-gnu/4.6/libgcc_s.so[/COLOR] -> [COLOR=Red]/lib/i386-linux-gnu/libgcc_s.so.1[/COLOR]
```(it's done this way to manage different library versions). It's probably not going to work if you point ld to the actual library (whether using LD_LIBRARY_PATH or the system ldconfig) because it won't recognize the name with the [COLOR=Red].1[/COLOR] version suffix

All that's to say, if the install didn't create the symlink for you, then that's likely the first thing you should try, i.e. assuming your gcc lib directory is /usr/lib/gcc/i686-linux-gnu/4.6/ like mine, then it would be

```
$ sudo ln -s /lib/i386-linux-gnu/libgcc_s.so.1 /usr/lib/gcc/i686-linux-gnu/4.6/libgcc_s.so
```**At that point I would try the 'make' again**, because gcc may very well have that library path built in. If it still fails, I would then try

```
export LD_LIBRARY_PATH=/usr/lib/gcc/i686-linux-gnu/4.6/libgcc_s.so
```i.e. point ld to the symlink, because that has the name it's expecting

Regards

---

### Post by mark allyn on 2012-09-15
Hi steeldriver,
 
Good grief!  No need to apologize.  You have been exceptionally helpful.  I will study your very detailed most recent reply esp. in regards to ldconfig.  
 
For the moment, I want to report that I have at least isolated the problem with the failure in the link step.  I should have been more alert to what was going on, but I wasn't.  It turns out that there is a broken symbolic link between the actual "so" and its symbolic link to libgcc_s.so.  This is the broken link:
 
/usr/lib/gcc/i686-linux-gnu/libgcc_s_so.1 and /usr/lib/gcc/i686-linux-gnu/4.6.3/lilbgcc_s.so
 
I should have figured this out because ld was reporting that it couldn't find -lgcc_s
 
So, now I gotta figure out how to mend a broken symbolic link.  Should be informative!
 
I'll keep you posted.
 
And thanks, again.
Mark

---

### Post by mark allyn on 2012-09-16
Good morning, steeldriver,
 
I'm embarrassed.  I went back after my most recent post and read your reply to my previous post and realized you were telling me precisely what I found out on my own.  Should have read your post before responding as quickly as I did.
 
I haven't tried to fix the link yet, but will do so shortly.
 
Mark

---

### Post by steeldriver on 2012-09-16
No problem - I find that working through stuff myself helps it stick in my brain 

 Let us know how it goes

---

### Post by mark allyn on 2012-09-16
Hi steeldriver,
 
Status report.  I went into /usr/lib/gcc/i686-linux-gnu/4.6.3.  I removed (sudo rm -i libgcc_s.so) and using ls -l it appeared that I had removed the broken link.  I then tried to creater a symbolic link to /usr/lib/gcc/i686-linux-gnu/libgcc_s_so.1.  I used sudo ln -s /usr/lib/gcc/i686-linux-gnu/libgcc_s.so.1 /usr/lib/gcc/i686-linux-gnu/4.6.3/libgcc_s.so.  The symbolic link libgcc_s.so now showed up in the ////4.6.3 directory.
 
However, on going back to /home/mark  and trying to link, the ld command still can't find the -lgcc symbolic link.
 
So, I guess I don't know what I'm doing!
 
If I am in the 4.6.3 directory and do ls -l libgcc_s.so the system reports that it is a symbolic link to /usr/lib/i686-linux-gnu/libgcc_s.so.1, as it should.  However, if I go up one directory higher to ///i686-linux-gnu/ and do the find /usr/lib/gcc/i686-linux-gnu/ -type l, the system shows a list of symbolic links in 4.6 and 4.6.3.  In 4.6 resides libgcc_s.so (which points to libgcc_s.so.1).  But, it shows no symbolic links in 4.6.3.  This is consistent with being unable to do the ld command....
 
By the way, doing the ls -l command shows that 4.6.3 is actually a symbolic link to 4.6. Hmmm...
 
I am puzzled.
 
Regards,
Mark
 
Regards,
Mark

---

### Post by steeldriver on 2012-09-16
That's pretty much what I see also:

```
$ ls -l /usr/lib/gcc/i686-linux-gnu/
total 4
drwxr-xr-x 5 root root 4096 Sep 15 16:06 4.6
lrwxrwxrwx 1 root root    3 Aug 24 20:05 [COLOR=Red]4.6.3 -> 4.6[/COLOR]
```however I think the link you need to make sure exists is this one here

```
$ ls -l /usr/lib/gcc/i686-linux-gnu/4.6/libgcc*
-rw-r--r-- 1 root root 3334500 Apr 15 19:45 /usr/lib/gcc/i686-linux-gnu/4.6/libgcc.a
-rw-r--r-- 1 root root   44908 Apr 15 19:45 /usr/lib/gcc/i686-linux-gnu/4.6/libgcc_eh.a
**[COLOR=Red]lrwxrwxrwx 1 root root      33 Sep 15 16:06 /usr/lib/gcc/i686-linux-gnu/4.6/libgcc_s.so -> /lib/i386-linux-gnu/libgcc_s.so.1[/COLOR]**
```i.e.

```
sudo ln -s /lib/i386-linux-gnu/libgcc_s.so.1 /usr/lib/gcc/i686-linux-gnu/4.6/libgcc_s.so
```assuming that [COLOR=Red]/lib/i386-linux-gnu[/COLOR] is the correct location for [COLOR=Red]libgcc_s.so.1[/COLOR] on your system - does this make sense? You shouldn't need to mess with /usr/lib/gcc/i686-linux-gnu/4.6[COLOR=Red].3[/COLOR] directly because the whole thing is symlinked to 4.6

---

### Post by mark allyn on 2012-09-16
Hi steeldriver,
 
Yup, if you do the sudo ln command with the files you show in last line of your code, everything works perfectly.  
 
I finally discovered what I was doing wrong in the symbolic linking.  I was trying STUPIDLY to link /usr/lib/gcc/i686-linux-gnu/libgcc_s.so.1 to /usr/lib/gcc/i686-linux-gnu/4.6.3/libgcc_s.so.  As you no doubt realized as you read this, the former /directory/file does not exist.  When I put the right directory in, all was well.
 
Thanks for hanging in with me on this.  It was challenging and I learned a lot, but I made too many mistakes.  
 
At any rate, you can mark this one FINITO.
 
Regards,
Mark

---

### Post by steeldriver on 2012-09-16
Great - glad it worked out for you

Was that enough to get your octave build to complete btw?

---

### Post by mark allyn on 2012-09-16
Hi Steeldriver,
 
I got interrupted before I could try out octave build.  I will try this shortly, and I will certainly let you know.
 
I do have a further question about this problem of broken links.  The breaking seems to have occurred when I installed an earlier version of GCC, gcc-3.4 specifically.  Now that gcc-4.6 is working again (as it was when I first installed 12.04), gcc-3.4 is throwing out three ld errors.  One is good old -lgcc.  I haven't investigated fully whether this is actually a broken link or not.  But it is also throwing out two other errors-- can't find crt1.o, can't find crti.o  If I set LIBPATH_LIB = /usr/lib/gcc/i386-linux-gnu/ then the problem then ld can find the two .o files.  
 
What's going on with the .o's would you think?  How would I set LIBPATH=/usr/lib/// permanently?
 
Regards,
Mark

---

### Post by steeldriver on 2012-09-16
My best guess is *that* is where you would want to update your ldconfig - if you recall, my setup has

```
$ ls -l /etc/ld.so.conf.d/
total 8
lrwxrwxrwx 1 root root  40 Jul  3 19:42 i386-linux-gnu_GL.conf -> /etc/alternatives/i386-linux-gnu_gl_conf
**[COLOR=Red]-rw-r--r-- 1 root root 108 Apr 19 20:53 i686-linux-gnu.conf[/COLOR]**
-rw-r--r-- 1 root root  44 Apr 19 19:10 libc.conf

``````
$ cat /etc/ld.so.conf.d/i686-linux-gnu.conf 
# Multiarch support
/lib/i386-linux-gnu
/usr/lib/i386-linux-gnu
/lib/i686-linux-gnu
/usr/lib/i686-linux-gnu
```If you **don't** have that file, then I think it should be as simple as creating it with the above lines and then running

```
sudo ldconfig
```to enable ld to find those libraries everywhere (really better than having to set LD_LIBRARY_PATH every time in the shell - that should be a last resort for cases where you need special non-system libraries)

---

### Post by mark allyn on 2012-09-17
Good morning, steeldriver,
 
Thanks for the help on this.  I'll try the ldconfig method.  Plus I need to see if I can compile Octave.  I'll let you know.
 
Regards,
Mark

---

### Post by mark allyn on 2012-09-17
Hi again, steeldriver,
 
Tried to compile Octave-3.6.3.  This time ./configure was able to find gcc without any problem. However, it aborts when it "can't compile a simple Fortran 77 program".  As a matter of fact, I have used g77 to compile a simple Fortran program and the command is successful.  
 
Still got to finish the lodconfig bit that you have recommended.  Will report on this later today.
 
Regards,
Mark

---

### Post by steeldriver on 2012-09-17
Mark, my ./configure had no problems with fortran - however I have the repo version of gfortran installed

You may need to tell configure about your fortran compiler explicitly, the variable is F77 I think, i.e.

```
./configure F77=/usr/bin/g77
```

or whatever

---

### Post by mark allyn on 2012-09-17
Hi steeldriver,
 
Thanks for the tip on ./configure with the g77 flag set.  That may very well do the trick.
 
Now, as for ldconfig.  Thanks to you I got the "hang of it".  I had been reading all sorts of stuff from the internet and just didn't follow what was going on.  I've been playing with it this afternoon.  One discovery was that you can't apply it to just any old directory--e.g. /home/mark/proj/lib does not seem to get into the ld.so.conf.d file, but if I copy a .so  and .so.1 to /usr/local/lib and then write the .conf file and cat it, the thing runs fine.  
 
However, trying to find the missing crt1.o and crti.o files doesn't seem to work.  These two are in my /usr/lib/i386-linux-gnu directory.  But, putting that path into ld.so.conf.d doesn't do the job.  If I use LiBRARY_PATH=/usr/lib/i386-linux-gnu, then the program will link.
 
Thanks much,
Mark

---

### Post by steeldriver on 2012-09-17
**Mark having given it some more thought, I don't believe the /etc/ld.so.conf.d/i686-linux-gnu.conf file should be necessary at all since the paths it contains are all within the standard locations /lib or /usr/lib anyhow**

In fact, when I run ldconfig -v, I get:

```
$ sudo ldconfig -v | grep i386
/sbin/ldconfig.real: Can't stat /lib/i686-linux-gnu: No such file or directory
/sbin/ldconfig.real: Can't stat /usr/lib/i686-linux-gnu: No such file or directory
[COLOR=Red]/sbin/ldconfig.real: Path `/lib/i386-linux-gnu' given more than once
/sbin/ldconfig.real: Path `/usr/lib/i386-linux-gnu' given more than once[/COLOR]
/usr/lib/i386-linux-gnu/mesa:
/lib/i386-linux-gnu:
/usr/lib/i386-linux-gnu:
/sbin/ldconfig.real: Cannot stat /usr/lib/i386-linux-gnu/libnss_db.so: No such file or directory
.
.
.
```If I remove that conf file, it happily finds the dirs:

```
$ sudo mv /etc/ld.so.conf.d/i686-linux-gnu.conf /root/
$
$ sudo ldconfig -v | grep i386
/usr/lib/i386-linux-gnu/mesa:
[COLOR=Red]/lib/i386-linux-gnu:
/usr/lib/i386-linux-gnu:[/COLOR]
.
.
.

```and the lib is listed in the cache:

```
$ ldconfig -p | grep libgcc
    libgcc_s.so.1 (libc6) => /lib/i386-linux-gnu/libgcc_s.so.1

```[B]That's all to say it should be sufficient *just* to run

[/B]```
sudo ldconfig
```**to update the database - without modifying / adding any of the /etc/ld.so.conf files**

---

### Post by mark allyn on 2012-09-17
Hi steeldriver,
 
OK.  I get your point.  I'm sure I have now set up the cache with duplicates too, and I will check and get rid of them using your method.  Very interesting idea and also informative for the unwashed (such as me).
 
But, with or without duplicates, I don't understand why the sys can't find crt1.o and crti.o.  They are on the library search path.  I'm wondering if when I restored the broken link for gcc-4.6 I didn't wind up breaking stuff for gcc-3.4.  Is it possible that they cannot coexist on the same system?
 
In my tree gcc (symlinked to gcc-4.6) and gcc-3.4 are in the same /usr/bin/ directory.  As you know, gcc works fine and throws no problems.  This business with the .o's is happening in the link step when I use gcc-3.4.  
 
Since they are .o files I thought perhaps I could just treat them as if they were ordinary .o's and use gcc-3.5 -o prog  prog.o  /usr/lib/i386-linux-gnu/crt1.o /usr/lib/i386-linux-gnu/crti.o.  
 
This doesn't work.
 
Regards as always,
Mark

---

### Post by steeldriver on 2012-09-17
As far as I can tell they are just in one place - and are not symlinked anywhere else

```
$ find /usr -name 'crt?.o' -exec ls -l {} \;
-rw-r--r-- 1 root root 1212 Apr 19 21:01 /usr/lib/i386-linux-gnu/crt1.o
-rw-r--r-- 1 root root 1004 Apr 19 21:01 /usr/lib/i386-linux-gnu/crti.o
-rw-r--r-- 1 root root 508 Apr 19 21:01 /usr/lib/i386-linux-gnu/crtn.o
```

I don't know why your installation can't find them out of the box, but if setting a LIBRARY_PATH environment variable works for you then I don't see any reason not to do that

---

### Post by mark allyn on 2012-09-17
Hi steeldriver,
 
First, ldconfig.  Yes, I had indeed duplicated them.  Followed your prescription and all seems well.
 
As for the .o files.  LIBRARY_PATH does seem to work.  Can I put this in /dev/environment so that it is always available?   Or should it go somewhere else--maybe ~/.bashrc or some such as that?
 
BTW, I tried out your tip on f77=/usr/bin/g77-3.4  (think that's the right version).  Anyway, didn't pass muster.  Is there something other than g77?  I mean a separate version named "Fortran 77"?  I thought they were the same, but maybe not.
 
Regards as always,
Mark

---

### Post by steeldriver on 2012-09-17
Mark it seems to work for me - see below

```
$ gedit hello_world.c &
[1] 26082
$ gcc -o hello_world hello_world.c 
$ ./hello_world 
Hello world!
$ 
$ mkdir -p ~/src/lib/i386-linux-gnu
$ sudo mv /usr/lib/i386-linux-gnu/crt?.o ~/src/lib/i386-linux-gnu
[sudo] password for steeldriver: 
$
$ rm hello_world
$ 
$ gcc -o hello_world hello_world.c 
/usr/bin/ld: cannot find crt1.o: No such file or directory
/usr/bin/ld: cannot find crti.o: No such file or directory
collect2: ld returned 1 exit status
$ 
$ ./hello_world 
bash: ./hello_world: No such file or directory
$
$ LIBRARY_PATH=~/src/lib/i386-linux-gnu/ gcc -o hello_world hello_world.c
$
$ ./hello_world 
Hello world!
$ 

```

For your Fortran issues, it needs to know where the compiler binary is, I think (not the install directory) - also the variable is upper case F77 not f77 - you can use

```
which g77
```
to locate your g77 compiler - or possibly even do
```
./configure F77=$(which g77)
```

if you want to get fancy - but be sure that 'which' is finding the binary first

---

### Post by mark allyn on 2012-09-18
Hi steeldriver,
 
I see what you did with the LIBRARY_PATH.  I'll try to duplicate it here.  But, I'm not having the crt*.o problem with gcc (AKA gcc-4.6).  I'm having the problem with gcc-3.4.  Still, you may be really onto the solution!
 
Thanks for pointing out the bit with F77, not f77.  And also the "which g77" .
 
I'll get back to you.  Got to grade some student projects this afternoon--sigh---so I can't play around as much as preceding couple of days.  
 
Regards,
Mark

---

### Post by mark allyn on 2012-09-18
Hello steeldriver,
 
Well, I made F77=/usr/bin/g77-3.4  as you suggested, and ./configure appeared to get past the Fortran 77 test, but then it died when it discovered that I didn't have PCRE library and .h files installed.  There seem to be potentially many more dependencies that I probably need to install.  I'm shelving this for now.  I'd be interested in installing a binary from an earlier distro but haven't found one.
 
Back to -lgcc_s.  As mentioned gcc-4.6 compiles and links without a complaint.  But, both g77-3.4 and gcc-3.4 cannot find -lgcc_s.  They seem not to be able to locate the symlink (libgcc_s.so).  It can't be a coincidence that they are both versioned the same way can it?
 
Regards,
Mark

---

### Post by steeldriver on 2012-09-18
Yes I'm sure you will find additional dependencies (PCRE, blas, lapack - I think I listed what worked for me in a previous post)

I have no experience at all of running multiple versions of gcc but what you suggest sounds right - if you can find the equivalent of the /usr/lib/gcc/i686-linux-gnu/4.6 dir (maybe /usr/lib/gcc/i686-linux-gnu/3.4? can things possibly be that sensible?) then linking libgcc_s.so.1 into that as

```
sudo ln -s /lib/i386-linux-gnu/libgcc_s.so.1 /usr/lib/gcc/i686-linux-gnu/3.4/libgcc_s.so
                                                         [COLOR=Red] ^^^^^^^^^^^^^^^^^^ or whatever[/COLOR]

```would be the thing to try

---

### Post by mark allyn on 2012-09-18
Hi steeldriver,
 
I'll try it.  
 
Thanks,
Mark

---

### Post by mark allyn on 2012-09-19
Good morning, steeldriver.
 
Update.  In my /usr/lib/gcc directory there is a i486-linux-gnu/3.4.6 subdirectory.  Inside is libgcc_s.so.  Using ls -l shows that it correctly symlinks to /lib/i386-linux-gnu/libgcc_s.so.1.  Assuming that gcc-3.4 uses these directories, it seems as though there shouldn't be a problem.  
 
Just as gcc-4.6 has no problem compiling and linking an executable,neither does gfortran-4.6.  There's something going on somehow with the versioning.
 
Regards,
Mark

---

### Post by mark allyn on 2012-09-19
Hi steeldriver and anyone else with this problem,
 
The answer to the question of gcc-3.4 and gcc-4.6 compatibility turns out to be this:  **You can't install them to the same /usr/bin directory** as I did.  According to gcc.gnu.org/faq.html, they must be installed in separate directories and then some symlinks created.
 
This probably also explains why I couldn't get a gcc-3.4 compile to properly locate the #include <stdio.h> header but gcc-4.6 could.
 
I'll verify this in the next day or so and let you know.
 
Regards,
Mark

---

