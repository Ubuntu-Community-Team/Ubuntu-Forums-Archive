---
title: "Calling wget from within a C app and waiting for it?"
date: 2010-10-27
forum: Programming Talk
---

### Post by Viper187 on 2010-10-27
I'm trying to port an C app I wrote in windows a year or two ago to linux. It was originally win32, which I can't seem to get mingw32 to compile, so I cut it down to a command line app to compile in GCC on Ubuntu natively. I need to grab files from the web with it. wget seemed like the easy way to get that part on windows, but I was calling it using ShellExecuteEx. Obviously, that won't work on linux, so I'm looking for the right way to do it. It needs to call wget and wait for it to finish, so it can process the file retrieved.  The original program worked fine in wine, but I needed to tweak something. I really should just boot windows on my laptop to update the damn thing. I'm too busy/lazy to get into programming linux apps with a GUI at this point. The input required is simple enough to go via command line arguments and be done with it. I guess it leaves my options open for GUIs later. I'm kind of partial to XULRunner, but trying to design **** to work on both windows and linux would just be more of a headache.

---

### Post by snakerdlk on 2010-10-27
Search for the curl library for C.

---

### Post by Viper187 on 2010-10-28
[This](http://ubuntuforums.org/showthread.php?t=781021) is what I found on curl, but it's C++. I tried it anyway. GCC sees the headers, but linking libcurl doesn't work. Is the C lib called something else or isn't there one?

---

### Post by NathanB on 2010-10-28
A quick Freshmeat search finds it:  [http://freshmeat.net/projects/curl](http://freshmeat.net/projects/curl)

C bindings:  [http://curl.haxx.se/libcurl/c/](http://curl.haxx.se/libcurl/c/)

Simple samples in C:  [http://curl.haxx.se/libcurl/c/example.html](http://curl.haxx.se/libcurl/c/example.html)

HTH.

---

### Post by NathanB on 2010-10-28
Just for future reference, the Linux equiv. of Window's "ShellExecuteEx" would be either 'popen()' or just 'system()'.

---

### Post by hakermania on 2010-10-28
include stdlib.h
system("wget http://blabla.com/bla.rar")

Add a & at the end of the string of system function to just launch the command if you don't want just to wait for it to finish. (e.g. system("wget http://www.blabla.com/lol.rar&")

---

### Post by Viper187 on 2010-11-03
> **hakermania said:**
> include stdlib.h
system(&quot;wget [http://blabla.com/bla.rar&quot;](http://blabla.com/bla.rar&quot;))

Add a & at the end of the string of system function to just launch the command if you don't want just to wait for it to finish. (e.g. system(&quot;wget [http://www.blabla.com/lol.rar&&quot;](http://www.blabla.com/lol.rar&&quot;))

 Thanks!

---

