---
title: "GCC/Linker cannot produce executable code (crtbegin.o on 10.04)"
date: 2012-05-25
forum: Packaging and Compiling Programs
---

### Post by uriel1998 on 2012-05-25
I'm not sure if this is a linking error or a GCC error, and it's system-wide.  I'm not sure when exactly it introduced - but it impacts anything where you have to "configure" first.

```

checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
```This bit shows up on EVERY config.log that gets spit out

```
configure:916: gcc -o conftest    conftest.c  1>&5
ld: crtbegin.o: No such file: No such file or directory
configure: failed program was:
```I do have buildessentials (and hence gcc and g++) installed, and I've successfully compiled a lot of stuff before - perhaps there was an upgrade that broke something?  If so, what do I do to fix this?

I wasn't planning to upgrade yet (more like the end of summer), so if there's a solution that doesn't involve wiping and reinstalling, I'll be thrilled.

---

### Post by Bachstelze on 2012-05-25
crtbegin.o is part of gcc. If you don't have it, your gcc install is corrupt. Try to reinstall:

```
sudo apt-get install -reinstall gcc-VERSION
```

---

### Post by uriel1998 on 2012-05-25
Reinstalled, but no dice.  Is uninstalling and explicitly reinstalling any different than what I just did?

---

### Post by Bachstelze on 2012-05-25
Normally no. Make sure the file is actually not there. It should be in /usr/lib/gcc/PLATFORM/VERSION.

---

### Post by uriel1998 on 2012-05-25
Oh-HO!  While there's a full install under [FONT=Courier New]/usr/lib/gcc/i486-linux-gnu/4.4/[/FONT], I also have [FONT=Courier New]/usr/lib/gcc/i486-linux-gnu/4.4.3/[/FONT] .  And that latter only has [FONT=Courier New]cc1[/FONT] in it.

So the best question here is this - symlink or copy files?  (I'm guessing I should do one or the other.)

---

### Post by Bachstelze on 2012-05-25
I think normally 4.4.3 should be a symlink to 4.4. Here 4.6.1 is a symlink to 4.6. Before you do anything, what gcc packages do you have installed?

```
dpkg -l | grep gcc
```

---

### Post by uriel1998 on 2012-05-25
```
ii  gcc                                                         4:4.4.3-1ubuntu1                                The GNU C compiler
ii  gcc-4.4                                                     4.4.3-4ubuntu5.1                                The GNU C compiler
ii  gcc-4.4-base                                                4.4.3-4ubuntu5.1                                The GNU Compiler Collection (base package)
ii  gccxml                                                      0.9.0+cvs20090916-1                             XML output extension to GCC
ii  libgcc1                                                     1:4.4.3-4ubuntu5.1                              GCC support library
```

(10.04, so I don't have 4.6...)

---

### Post by Bachstelze on 2012-05-25
Your packages seem right... Since I don't have a Lucid system, I don't know if having a separate 4.4.x dir is how it's supposed to be or not. Guess you can always try uninstalling and reinstalling.

---

### Post by uriel1998 on 2012-05-25
I went ahead and copied the contents of 4.4 over... and suddenly I can compile again.  It's probably *wrong*, but it's getting the job done until I do a clean upgrade down the road.

Thanks for your help;  I wouldn't have known where to look otherwise.

---

