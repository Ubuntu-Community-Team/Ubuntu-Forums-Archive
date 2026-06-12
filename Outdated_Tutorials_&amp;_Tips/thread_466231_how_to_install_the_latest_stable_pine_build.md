---
title: "how to install the latest stable pine build"
date: 2007-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by tarek on 2007-06-06
Here is how to install the latest pine build.

OS: Ubuntu 7.04

I used Pine before and it’s one of my favorite mail programs. I could not install it from the repository using aptitude so I download the debian package and installed it.

The lastest stable build is 4.64.

You can use command line or firefox to install it:

**Command Line:**

```
$ w3m [ftp://ftp.cac.washington.edu/pine/pine_4.64_i386.deb](ftp://ftp.cac.washington.edu/pine/pine_4.64_i386.deb)
```

Once downloaded w3m will ask if you want to install the program, enter ‘I’ to install it:
```

    Do you wish to:
    - I)nstall the package now,
    - S)ave it to a file, or
    - Q)uit now
    Your choice (I/S/Q)? I
    Installation of Debian packages needs to be done as root.
    Enter command used to become root (default=sudo): sudo

    Installing package…
    Selecting previously deselected package pine.
    (Reading database … 143846 files and directories currently installed.)
    Unpacking pine (from …/tarek/.w3m/w3mtmp31867-0.deb) …
    Setting up pine (4.64) …

    Done. Press to continue:

```

**Firefox:**

Go to [http://www.washington.edu/pine/getpine/linux.html](http://www.washington.edu/pine/getpine/linux.html) and click on pine_4.64_i386.deb package

Save it on your desktop, once downloaded double click and install the package.

Done! :)

Your feedback is welcome!

tarek

---

