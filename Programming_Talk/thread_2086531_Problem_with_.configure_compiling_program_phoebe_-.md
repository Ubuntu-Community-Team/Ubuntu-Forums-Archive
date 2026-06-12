---
title: "Problem with ./configure compiling program phoebe - physics of eclipsing binaries"
date: 2012-11-21
forum: Programming Talk
---

### Post by alphacrucis2 on 2012-11-21
I have been trying to compile a program that does analysis of eclipsing binary star photometry called phoebe. It has three parts. A library part, a scripting part and a GUI part. The first two compiled fine doing the usual ./configure, make, sudo make install but the gui part failed on the ./configure. The error being:

```
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.

       *** PHOEBE configuration failure ***

PHOEBE cannot find the graphical library GLib 2.6.0 or higher.
Please install it and run the ./configure script again.

```

When I look at the config.log file I see this:

```
configure:2632: gcc -V >&5
gcc: error: unrecognized command line option '-V'
gcc: fatal error: no input files
compilation terminated.
```

I guess the configure is trying to invoke gcc compiler with a wrong parameter. Any ideas on what I can do to fix this?

---

### Post by drmrgd on 2012-11-21
Have you verified that all the requisite packages are installed on your system (in particular libgtk2.0-dev)?  Try installing that package first, then try to configure again:

```
sudo apt-get install libgtk2.0-dev
```

---

### Post by The Cog on 2012-11-21
Moved to Programming Talk.

---

### Post by mc4man on 2012-11-21
Open up the configure file & change -V to -v, likely in 2 places - example diff

```

--- phoebe-gui-0.31a/configure	2008-06-16 20:16:37.000000000 -0400
+++ phoebe-gui-0.31a/configure	2012-11-21 08:28:25.617597068 -0500
@@ -2624,13 +2624,13 @@
   ac_status=$?
   echo "$as_me:$LINENO: \$? = $ac_status" >&5
   (exit $ac_status); }
-{ (ac_try="$ac_compiler -V >&5"
+{ (ac_try="$ac_compiler -v >&5"
 case "(($ac_try" in
   *\"* | *\`* | *\\*) ac_try_echo=\$ac_try;;
   *) ac_try_echo=$ac_try;;
 esac
 eval "echo \"\$as_me:$LINENO: $ac_try_echo\"") >&5
-  (eval "$ac_compiler -V >&5") 2>&5
+  (eval "$ac_compiler -v >&5") 2>&5
   ac_status=$?
   echo "$as_me:$LINENO: \$? = $ac_status" >&5
   (exit $ac_status); }
```

Overall the source is 4+ yrs old so how it works out  remains to be seen

---

### Post by alphacrucis2 on 2012-11-21
Thanks guys. I will give these suggestions a try later today.

---

### Post by alphacrucis2 on 2012-11-21
It still failed after fixing the -V parameter but after installing the libgtk2.0-dev package (which pulled in quite a lot of extra stuff) it did get further but complained:


```
PHOEBE cannot find the graphical library libglade-2.0 or higher.
Please install it and run the ./configure script again.
```

I noticed in synaptic that although libglade2-0 was installed, the package libglade2-dev was not. I installed libglade2-dev and the ./configure was successful as was the subsequent make & sudo make install. It even runs!.



Now I have to figure out how to drive this thing.:P 


Thanks for the help.

---

