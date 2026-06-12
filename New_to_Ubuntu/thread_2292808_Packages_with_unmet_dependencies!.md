---
title: "Packages with unmet dependencies!"
date: 2015-08-31
forum: New to Ubuntu
---

### Post by Fl4v10 on 2015-08-31
Hi all!

I am using Ubuntu 14.04.1 and I have a problem for the Package manager. The error is written below:

"a[I]n error has occurred. run package manager from the right click menu  or apt - get in a terminal to see what is wrong. The error message was;
"error. brokencount > 0 "  this usually means you have unmet dependencies. "[/I]

I have a red stop sign in my toolbar!
I cannot install other libraries or delete them.

If I try: sudo apt-get update and sudo apt-get upgrade -f
I have this message back:

Unpacking libc6:i386 (2.19-0ubuntu6.6) over (2.17-0ubuntu5.1) ...
dpkg: error processing archive /var/cache/apt/archives/libc6_2.19-0ubuntu6.6_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/lintian/overrides/libc6', which is different from other instances of package libc6:i386
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.19-0ubuntu6.6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Can you help me on solving this problem???

Thanks a lot!
Flavio

---

### Post by ajgreeny on 2015-08-31
What is the output of ```
sudo apt-get install -f
```

---

### Post by Bashing-om on 2015-08-31
Fl4v10Fl4v10; Hello;

Is this a 32 bit install or 64 bit ?
> 
Errors were encountered while processing:
/var/cache/apt/archives/libc6_2.19-0ubuntu6.6_[color=red]i386[/color].deb

 Perhaps a conflict with the 64/32 bit libraries ?

What do you have installed ?
```

dpkg -l libc6

```
Please post the output between code tags to maintain and promote readability.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
 
Let's see if a 
[INDENT][INDENT][INDENT]tale gets told
[/INDENT][/INDENT][/INDENT]

---

### Post by sandyd on 2015-08-31
Something is odd here. 2.17-0ubuntu5.1 is extremely old, and the only version that I could find was [back in raring (13.04)]("https://launchpad.net/ubuntu/raring/i386/libc6/2.17-0ubuntu5.1")

Fl4v10, is this an upgraded version of Ubuntu, or a clean install?
Have you installed any new packages recently or added any repositories?

---

