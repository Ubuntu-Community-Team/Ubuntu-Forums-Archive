---
title: "Output the time taken to run a shell script/command"
date: 2009-06-21
forum: Programming Talk
---

### Post by staticanime on 2009-06-21
Hey all, I've been compiling a custom kernel, and have had to re-compile a few times, and I was wondering if there was a way to count how long it takes to compile and output it either via a shell script or similar? Using Ubuntu 9.04 and bash if that helps

---

### Post by MadCow108 on 2009-06-21
put a "time" in front of the command

---

### Post by kaibob on 2009-06-21
> **staticanime said:**
> Hey all, I've been compiling a custom kernel, and have had to re-compile a few times, and I was wondering if there was a way to count how long it takes to compile and output it either via a shell script or similar? Using Ubuntu 9.04 and bash if that helps

I have never compiled a custom kernel. However, the following thread contains two options that will "output the time taken to run a shell script/command".

[http://ubuntuforums.org/showthread.php?t=1187569](http://ubuntuforums.org/showthread.php?t=1187569)

---

### Post by monkeyking on 2009-06-21
I frequently use the 'time' command from the commandline,
but I've had some troubles using it in my bash script.

It seems like its using the bash buildin function 'time',
and I've never managed to track down information on these bashbuildins.

I think I ended up using /usr/bin/time, it seems to be doing the same, just not the same format.

---

### Post by stroyan on 2009-06-21
If you are interested in reducing the time to compile you should look at the streamline_config.pl script.  It suggested changes to the config file to eliminate unused modules to reduce the build time.
See [http://lwn.net/Articles/330876/](http://lwn.net/Articles/330876/) for more.

If you have access to more than one machine running the same release you can use the distcc package to enlist help from those other systems.  That can reduce build time quite a lot.  Here is an example of what I use. This has distcc to improve performance.  It uses the script command to keep a detailed log of output.

script -c 'MAKEFLAGS="CC=distcc" DISTCC_HOSTS="localhost host2" CONCURRENCY_LEVEL=8 fakeroot make-kpkg --initrd binary-arch' make-kpkg.typescript

---

### Post by staticanime on 2009-06-21
> **stroyan said:**
> If you are interested in reducing the time to compile you should look at the streamline_config.pl script.  It suggested changes to the config file to eliminate unused modules to reduce the build time.
See [http://lwn.net/Articles/330876/](http://lwn.net/Articles/330876/) for more.

If you have access to more than one machine running the same release you can use the distcc package to enlist help from those other systems.  That can reduce build time quite a lot.  Here is an example of what I use. This has distcc to improve performance.  It uses the script command to keep a detailed log of output.

script -c 'MAKEFLAGS="CC=distcc" DISTCC_HOSTS="localhost host2" CONCURRENCY_LEVEL=8 fakeroot make-kpkg --initrd binary-arch' make-kpkg.typescript

I've already stripped down my kernel to the bare minimum lol, just wanted to time how long it takes, time seems to do the job, as I only need a rough time. Thanks to everyone for your help :)

---

