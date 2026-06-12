---
title: "cvs compiling errors"
date: 2004-12-30
forum: Packaging and Compiling Programs
---

### Post by cacofonix on 2004-12-30
I am trying to install my sound card by compiling the alsa drivers from cvs and I have hit a bit of a road block.
I can make the drivers no worries everything is set with them I move on to the lib files and have hit a bit of a snag.

I tried compiling the lib with this command:
```

$>sudo ./cvscompile 
/usr/bin/ld: .libs/libasound.so.2.0.0: undefined versioned symbol name snd_pcm_hw_params_get_buffer_size_max@ALSA_0.9
/usr/bin/ld: failed to set dynamic section sizes: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libasound.la] Error 1
make[2]: Leaving directory `/root/alsa/alsa-lib/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/alsa/alsa-lib/src'
make: *** [all-recursive] Error 1

```
I did some searching and found that if I do it this way:
```

$>sudo ./cvscompile --with-versioned=no

```
it compiles just fine, I can also make it fine as well but when I run:
```

$>sudo make install
/usr/bin/install: cannot create regular file `/usr/share/alsa/cards/SI7018/SI7018/sndop-mixer.alisp': No such file or directory
make[4]: *** [install-SI7018DATA] Error 1
make[4]: Leaving directory `/root/alsa/alsa-lib/src/conf/cards'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/root/alsa/alsa-lib/src/conf/cards'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/root/alsa/alsa-lib/src/conf'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/root/alsa/alsa-lib/src'
make: *** [install-recursive] Error 1

```

it ends up with this error whats happening and how can I fix it?

cheers

cacofonix

---

### Post by jdong on 2005-01-01
You must use **mkdir** to create all the directories up to /usr/share/alsa/cards/SI7018/SI7018/, 1 level at a time (/usr/share should already be there, but start creating folders from alsa and up)

---

### Post by cacofonix on 2005-01-02
I would've thought that the make and make install would do that :-k. I restarted my computer and the soundcard was working, so I dont know what happened there but Im not complaining :D

Thanks for your help jdong :thumbsup:


cacofonix

---

### Post by hanover.fiste on 2005-09-19
[QUOTE=cacofonix]I am trying to install my sound card by compiling the alsa drivers from cvs and I have hit a bit of a road block.
I can make the drivers no worries everything is set with them I move on to the lib files and have hit a bit of a snag.

I tried compiling the lib with this command:
```

$>sudo ./cvscompile 
/usr/bin/ld: .libs/libasound.so.2.0.0: undefined versioned symbol name snd_pcm_hw_params_get_buffer_size_max@ALSA_0.9
/usr/bin/ld: failed to set dynamic section sizes: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libasound.la] Error 1
make[2]: Leaving directory `/root/alsa/alsa-lib/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/alsa/alsa-lib/src'
make: *** [all-recursive] Error 1

```
I did some searching and found that if I do it this way:
```

$>sudo ./cvscompile --with-versioned=no

```
it compiles just fine, I can also make it fine as well but when I run:
```

$>sudo make install
/usr/bin/install: cannot create regular file `/usr/share/alsa/cards/SI7018/SI7018/sndop-mixer.alisp': No such file or directory
make[4]: *** [install-SI7018DATA] Error 1
make[4]: Leaving directory `/root/alsa/alsa-lib/src/conf/cards'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/root/alsa/alsa-lib/src/conf/cards'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/root/alsa/alsa-lib/src/conf'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/root/alsa/alsa-lib/src'
make: *** [install-recursive] Error 1

```

it ends up with this error whats happening and how can I fix it?

cheers

cacofonix[/QUOTE]

I just went through trouble shooting this same error and was about to open a bug with the alsa project, when I figured out that the real problem is two-fold. First, the headers in /usr/include/linux are ridiculously old; 2.5.99-something-bk. Second, the links in /etc/alternatives for aclocal and automake point to 1.4. While this may be a safe default, I always end having to change this because so much stuff won't build if you don't.

And to remedy the issue with the old headers in /usr/include/linux, I move linux to linux.bak, then create a symlink pointing to /usr/src/linux-headers-`uname r-`/include/linux. Works a treat then.

---

### Post by Roptaty on 2005-10-04
[QUOTE=hanover.fiste]
And to remedy the issue with the old headers in /usr/include/linux, I move linux to linux.bak, then create a symlink pointing to /usr/src/linux-headers-`uname r-`/include/linux. Works a treat then.[/QUOTE]

Please don't... The /usr/include/linux files are those glibc is compiled against. Worst case scenario: You might cause havoc on your system by doing this.

---

