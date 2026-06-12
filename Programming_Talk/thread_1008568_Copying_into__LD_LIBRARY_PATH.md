---
title: "Copying into  LD_LIBRARY_PATH?"
date: 2008-12-11
forum: Programming Talk
---

### Post by lawrencius on 2008-12-11
Hey every1,
I am in the process of installing blunder 
([I]Bundler is a structure-from-motion system for unordered image
collections (for instance, images from the Internet). Bundler takes a
set of images, image features, and image matches as input, and
produces a 3D reconstruction of the camera and (sparse) scene geometry
as output. )[/I]

I am stumped by this piece of instruction:

Finally, copy the approximate nearest neighbors (ANN) shared library
at BASE_PATH/lib/libANN_char.so to a location in your LD_LIBRARY_PATH
(or add BASE_PATH/lib to LD_LIBRARY_PATH.  

Any help is appreciated.
Lawrencius

---

### Post by geirha on 2008-12-11
Put the library (.so-file) in /usr/local/lib, then run ```
sudo ldconfig
``` and the library should be found by the program.

To check, run ```
ldconfig -p | grep libANN
``` It should print the libANN.so file

---

### Post by lawrencius on 2008-12-11
I moved the .so to the directory you gave me.
When I ran: sudo ldconfig
I got:
```

lawrence@lawrence:~/Desktop/bundler$ sudo ldconfig
/sbin/ldconfig.real: /usr/local/lib/ is not a symbolic link

```

Am I doing something obviously stupid?

---

### Post by dwhitney67 on 2008-12-12
What OS are you running?

On ubuntu, /usr/local/lib should already exist; thus the instructions given by geirha should work, providing you followed it to the letter.

What does your /usr/local/lib directory's permissions appear as?  Please post the command response to:
```

ls -l /usr/local

```
Then post the command response to:
```

ls -l /usr/local/lib

```

---

### Post by lawrencius on 2008-12-12
I did follow the provided instructions and I am running ubuntu.

Here are the results:

```

**lawrence@lawrence:~$ ls -l /usr/local**
total 36
drwxr-xr-x  2 root root 4096 2008-11-22 11:08 bin
drwxr-xr-x  2 root root 4096 2007-10-15 18:17 etc
drwxr-xr-x  2 root root 4096 2007-10-15 18:17 games
drwxr-xr-x  3 root root 4096 2008-05-04 19:47 include
drwxr-xr-x  3 root root 4096 2008-04-23 21:55 java
drwxr-xr-x  8 root root 4096 2008-12-11 21:40 lib
lrwxrwxrwx  1 root root    9 2008-04-18 16:28 man -> share/man
drwxr-xr-x  2 root root 4096 2008-05-02 19:51 sbin
drwxr-xr-x 14 root root 4096 2008-11-28 09:11 share
drwxr-xr-x  2 root root 4096 2007-10-15 18:17 src
**lawrence@lawrence:~$ ls -l /usr/local/lib**
total 364
drwxrwsr-x 2 root     staff     4096 2008-11-01 13:07 eclipse
-rwxr-xr-x 1 lawrence lawrence 75842 2008-10-06 16:30 libANN_char.so
-rw-r--r-- 1 root     root     93282 2008-05-04 19:47 libdvdcss.a
-rwxr-xr-x 1 root     root       818 2008-05-04 19:47 libdvdcss.la
lrwxrwxrwx 1 root     root        18 2008-05-04 19:47 libdvdcss.so -> libdvdcss.so.2.0.8
lrwxrwxrwx 1 root     root        18 2008-05-04 19:47 libdvdcss.so.2 -> libdvdcss.so.2.0.8
-rwxr-xr-x 1 root     root     75496 2008-05-04 19:47 libdvdcss.so.2.0.8
-rw-r--r-- 1 root     root     40710 2008-05-02 19:51 libthinkfinger.a
-rwxr-xr-x 1 root     root       876 2008-05-02 19:51 libthinkfinger.la
lrwxrwxrwx 1 root     root        23 2008-05-02 19:51 libthinkfinger.so -> libthinkfinger.so.0.0.0
lrwxrwxrwx 1 root     root        23 2008-05-02 19:51 libthinkfinger.so.0 -> libthinkfinger.so.0.0.0
-rwxr-xr-x 1 root     root     36625 2008-05-02 19:51 libthinkfinger.so.0.0.0
drwxr-xr-x 2 root     root      4096 2008-05-02 19:51 pkgconfig
drwxrwsr-x 3 root     staff     4096 2008-11-01 12:57 python2.4
drwxrwsr-x 3 root     staff     4096 2007-10-15 18:17 python2.5
drwxr-xr-x 2 root     root      4096 2008-05-02 19:51 security
drwxr-xr-x 3 root     root      4096 2008-11-28 09:11 site_ruby

```

Thanks guys.

---

### Post by dwhitney67 on 2008-12-12
The only thing that looks odds is the ownership of the libANN_char.so file.  Change it to be owned exclusively by root, then follow up with ldconfig.  Here's how:

```

cd /usr/local/lib
sudo chown root:root libANN_char.so
sudo ldconfig

```
Optionally you can pass ldconfig the -v option, so that it prints information concerning the directories/files is has found.


P.S.  Where did you get the libANN_char.so file from?  Were there not other files with a similar name, but with a version number?  It is hard to believe that an off-the-shelf package would not provide the means for you to install it into the root-owned areas.

---

### Post by lawrencius on 2008-12-12
I followed your instructions dwhitney67, yet whenever I try to run ldconfig i still get this "symbolic link error".

Regarding your question, this is the only .so file and it is part of the installation guide for the open source version of photosynth called "bundler"...

---

### Post by dwhitney67 on 2008-12-12
I'm trying to duplicate the problem you are having, so I visited this site, [http://phototour.cs.washington.edu/bundler/](http://phototour.cs.washington.edu/bundler/), to obtain both the binary and source packages.

The binary package has scripts within it that need to be edited by the user, to indicate where the scripts are located at.  Very amateurish scripts IMO.  I edited a couple of scripts to specify the BASE_DIR, but the RunBundler.sh script still failed.  So I gave up on it.

Going on to the source package, I tried to make the source files.  Compilation errors cropped up, but I was able to correct those quite easily.  Then I continued with the make, but the link-stage failed because of missing libraries.  The README.txt made no mention of these.

Anyhow, since you are interested in libANN_char.so, I went to the source directory for ann_1.1_char, and compiled it.  Fortunately it worked.
```

tar xzvf bundler-v0.2-source.tar.gz
cd bundler-v0.2-source/lib/ann_1.1_char
make linux-g++-shared

```
The shared object file libANN_char.so appears in bundler-v0.2-source/lib/ann_1.1_char/lib.

Try moving it to /usr/local/lib, or better yet, just keep it in a local directory (and rely on LD_LIBRARY_PATH).  I'm almost certain bundler will be updated real soon.  Words cannot describe my dislike that someone (or a group) would publish a source package that is replete with problems.

To move libANN_char.so to /usr/local/lib:
```

cd bundler-v0.2-source/lib/ann_1.1_char/lib
sudo install -m 755 libANN_char.so /usr/local/lib
sudo ldconfig

```
This worked for me.

---

### Post by lawrencius on 2008-12-13
Thanks so much. This solved the problem.

Yeah ridiculous programmers...

---

### Post by Jimantha on 2009-02-12
Bringing this thread back to life :-)

Hi everyone -- I wrote the bundler software mentioned in this thread.  I have a lot of experience with C/C++, but very little packaging things up nicely, whether in Unix or Windows.  There are (at least) two issues with the current package, both identified in this thread:

  (1) Manual editing of scripts
  (2) Requires installation of other public-domain libraries (e.g. LAPACK).

Does anyone have any tips on how (1) can be avoided?  I have a BASE_PATH variable in the scripts that currently requires manual editing.  For (2), is it considered good form to include other required (public domain) libraries with a release?

Again, any advice would be appreciated :-)

Thanks,
Noah

---

