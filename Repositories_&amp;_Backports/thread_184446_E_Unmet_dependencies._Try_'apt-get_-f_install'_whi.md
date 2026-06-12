---
title: "E: Unmet dependencies. Try 'apt-get -f install' which is't solving the problem."
date: 2006-05-29
forum: Repositories &amp; Backports
---

### Post by CattyNebulart on 2006-05-29
I have a slight problem and I can't quite figure out how to fix it, since I can't fix it the way it tells me to, and I can't remove the bad package. What should I do? ](*,)

```
root@compchan:/home/dirk # apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-wxversion
The following NEW packages will be installed:
  python-wxversion
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/20.3kB of archives.
After unpacking 81.9kB of additional disk space will be used.
Do you want to continue [Y/n]?

Preconfiguring packages ...
(Reading database ... 115400 files and directories currently installed.)
Unpacking python-wxversion (from .../python-wxversion_2.6.1.1.1ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/python-wxversion_2.6.1.1.1ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/lib/python2.4/site-packages/wxversion.py', which is also in package wxpython2.5.3
Errors were encountered while processing:
 /var/cache/apt/archives/python-wxversion_2.6.1.1.1ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Jussi Kukkonen on 2006-05-30
Tried removing  *wxpython2.5.3*?

---

### Post by CattyNebulart on 2006-05-30
I tried apt-get -f remove wxpython2.5.3 but got the same error again. I'm fairly certain I'm doing something wrong, but I don't know what, since a broken package shouldn't be that hard to fix. (would post output but am at work right now)

---

### Post by Jussi Kukkonen on 2006-05-30
The exact same error? I think you should check again, just to be sure.

---

### Post by CattyNebulart on 2006-05-30
You where right, it's a different error but not much more enligtening at least to me.

However after playing with it for a bit more I managed to fix the problem by removing all packages it complained about (at which point it would complain about more, but I kept expanding the list of packages to be removed in them) and then I reinstalled all the packages I removed and actually cared about. and it's all working now. Thatnks for your help.

```
root@compchan:/home/dirk # apt-get -f remove wxpython2.5.3
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libwxgtk2.5.3-python: Depends: wxpython
  python-wxgtk2.4: Depends: python-wxversion but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by neolivz on 2009-06-29
Hi,
     I know there is no point in replying to this thread now. 
But if any one else get the error, i think i can suggest.

Delete the file  /var/cache/apt/archives/python-wxversion_2.6.1.1.1ubuntu2_all.deb (in his case)

and run apt-get install, if any other file is also bombing, delete that one also and run it it will start working.

It has corrupted file, that's all, at least for me.

Regards,
Jishnu

---

### Post by AmrH on 2009-09-18
@[neolivz]("http://ubuntuforums.org/member.php?u=538293"):

Thank you for your help. This method really saved me from reinstalling Ubuntu!

---

