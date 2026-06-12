---
title: "Error While loading shared libraries"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by cdlam on 2013-01-15
Hi. I'm trying to run a program called GlimmerHMM ([http://cbcb.umd.edu/software/glimmerhmm/man.shtml](http://cbcb.umd.edu/software/glimmerhmm/man.shtml)) however when I run it I get this error:

```
chris@ubuntu:~/Documents/IS/Bioinformatics-Software/IS-Part2/GlimmerHMM/bin$ ./glimmerhmm_linux
./glimmerhmm_linux: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```So I guess the obvious question is, how do I fix this? But I'm also wondering what libstdc++.so.5 actually is, as I have no idea.

I did search here and found what I thought might be a solution, [http://ubuntuforums.org/showthread.php?t=2039435&highlight=Error+loading+shared+libraries](http://ubuntuforums.org/showthread.php?t=2039435&highlight=Error+loading+shared+libraries) , where they used sudo apt get to find the missing package but it didn't work for me.

I tried this:
```
sudo apt-get install libstdc++.so.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libstdc++.so.5
E: Couldn't find any package by regex 'libstdc++.so.5'

```

Edit: Actually I searched some more and tried this...

```
sudo apt-get install libstdc++5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  html2text libmail-sendmail-perl libsys-hostname-long-perl
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libstdc++5
0 upgraded, 1 newly installed, 0 to remove and 183 not upgraded.
Need to get 255 kB of archives.
After this operation, 1,155 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ precise/universe libstdc++5 amd64 1:3.3.6-25ubuntu1 [255 kB]
Fetched 255 kB in 4s (54.0 kB/s)                     
Selecting previously unselected package libstdc++5.
(Reading database ... 176303 files and directories currently installed.)
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-25ubuntu1_amd64.deb) ...
Setting up libstdc++5 (1:3.3.6-25ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

But then when I tried calling the program I got the same error as before...


Any help you could give is much appreciated, thanks!

---

### Post by mc4man on 2013-01-16
been a couple of years, ck. this thread. links in post #5 may be best current bet. (otherwise may be in launchpad somewhere
[http://ubuntuforums.org/showthread.php?t=1406616](http://ubuntuforums.org/showthread.php?t=1406616)

---

### Post by cdlam on 2013-01-16
Yeah that worked, thanks. In case someone has this problem in the future - what I installed above is 64bit but the application I'm trying to run is 32. had to install the ia32-libs package.

```
sudo apt-get install ia32-libs
```

---

