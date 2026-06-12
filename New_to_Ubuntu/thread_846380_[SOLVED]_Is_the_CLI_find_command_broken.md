---
title: "[SOLVED] Is the CLI find command broken?"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by unutbu on 2008-07-01
Try the following experiment:
Go to a directory with files whose mod time is > 6 years old (around 2002).
```

% for num in `seq 1 250 3000`; do find . -type f -mtime +$num | xargs ls -lt > /tmp/mtime$num; done

  -rw-r--r--  1 right right 12238 2008-07-01 13:52 mtime1
  -rw-r--r--  1 right right  1216 2008-07-01 13:52 mtime251
  -rw-r--r--  1 right right  1216 2008-07-01 13:52 mtime501
  -rw-r--r--  1 right right  1216 2008-07-01 13:52 mtime751
  -rw-r--r--  1 right right  1216 2008-07-01 13:52 mtime1001
  -rw-r--r--  1 right right  1216 2008-07-01 13:52 mtime1251
  -rw-r--r--  1 right right  1216 2008-07-01 13:52 mtime1501
  -rw-r--r--  1 right right   774 2008-07-01 13:52 mtime1751
  -rw-r--r--  1 right right   774 2008-07-01 13:52 mtime2001
  -rw-r--r--  1 right right   774 2008-07-01 13:52 mtime2251
  -rw-r--r--  1 right right  3141 2008-07-01 13:52 mtime2501 <-- ***
  -rw-r--r--  1 right right  3141 2008-07-01 13:52 mtime2751

```

Look at the size of the files. If the find command is supposed to pick up files that are older than num days old, then the file size should be monotonically decreasing, but the output above is not monotonically decreasing.

:confused:

---

### Post by ibuclaw on 2008-07-01
try
```
 du -a --max-depth=1 | grep mtime
```
Inside the tmp folder.
That should give you the real file sizes.

Regards
Iain

---

### Post by nowshining on 2008-07-01
u need to update the database every so often - if u disabled the cron job to do it, u'll need to do it manually

sudo updatedb

ur pw won't show as you type.

---

### Post by unutbu on 2008-07-01
```
14:44:14 right@intersection:/tmp% du -a --max-depth=1 | grep mtime
12	./mtime1
4	./mtime751
4	./mtime251
4	./mtime501
4	./mtime1001
4	./mtime1251
4	./mtime1751
4	./mtime1501
4	./mtime2001
4	./mtime2501
4	./mtime2251
4	./mtime2751

```
Hm. Well, I tried to use filesizes as an indirect manifestation of the problem, but perhaps I had better be explicit. The files that find collects seem to be simply wrong:

```

% cat mtime2251

-rwxr-xr-x 1 right right   341 2002-02-21 13:45 ./diveintopython-5.4/kgp/binary.xml
-rwxr-xr-x 1 right right 10438 2002-02-21 13:45 ./diveintopython-5.4/kgp/husserl.xml
-rwxr-xr-x 1 right right 14340 2002-02-21 13:45 ./diveintopython-5.4/kgp/kant.xml
-rwxr-xr-x 1 right right   264 2002-02-21 13:45 ./diveintopython-5.4/kgp/kgp.dtd
-rwxr-xr-x 1 right right    88 2002-02-21 13:45 ./diveintopython-5.4/kgp/russiansample.xml
-rwxr-xr-x 1 right right    22 2002-02-21 13:45 ./diveintopython-5.4/kgp/template.xml
-rwxr-xr-x 1 right right   460 2002-02-21 13:45 ./diveintopython-5.4/kgp/test.xml
-rwxr-xr-x 1 right right 16650 2002-02-21 13:45 ./diveintopython-5.4/kgp/thanks.xml
-rwxr-xr-x 1 right right 11879 2002-02-21 13:45 ./diveintopython-5.4/LICENSE.txt

```

```
% cat mtime2501

total 256
-rwxr-xr-x 1 right right  2235 2008-07-01 12:08 test.py
drwxr-xr-x 2 right right  4096 2008-07-01 10:43 testbin
-rwxr-xr-x 1 right right   843 2008-07-01 08:17 example-files-and-directories.py
-rw-r--r-- 1 right right   323 2008-07-01 08:14 example-files-and-directories.py~
-rwxr-xr-x 1 right right   456 2008-07-01 00:29 test.py~
-rwxr-xr-x 1 right right  2496 2008-07-01 00:11 py2depgraph.py
-rwxr-xr-x 1 right right  7146 2008-07-01 00:11 depgraph2dot.py
-rw-r--r-- 1 right right  7128 2008-07-01 00:09 depgraph2dot.py~
-rw-r--r-- 1 right right  2477 2008-07-01 00:07 py2depgraph.py~
-rw-r--r-- 1 right right   652 2008-06-30 17:28 example-finding-object-methods.py
-rw-r--r-- 1 right right   187 2008-06-30 17:23 example-find-file-that-provides-module.py
-rw-r--r-- 1 right right   628 2008-06-30 17:21 example-finding-object-methods.py~
drwxr-xr-x 6 right right  4096 2008-06-29 15:06 diveintopython-5.4
-rw-r--r-- 1 right right  7790 2008-06-28 23:18 sudoku-top95.txt
-rw-r--r-- 1 right right 22087 2008-06-28 23:17 sudoku-top95solutions.html
-rw-r--r-- 1 right right  4101 2008-06-28 23:17 sudoku.py
-rwxr-xr-x 1 right right   632 2008-06-28 15:55 show-doc.py
-rwxr-xr-x 1 right right  1028 2008-06-28 14:46 example-alterfiles.py
-rw-r--r-- 1 right right   619 2008-06-28 13:14 pyUtils.pyc
-rwxr-xr-x 1 right right   419 2008-06-28 13:13 pyUtils.py
-rw-r--r-- 1 right right   288 2008-06-28 00:11 pyUtils.py~
-rwxr-xr-x 1 right right   354 2008-06-27 23:30 find-largest-epsilon.py
-rw-r--r-- 1 right right  1117 2008-06-27 23:30 find-largest-epsilon.py~
-rw-r--r-- 1 right right   326 2008-06-21 12:36 test.pyc
-rwxr-xr-x 1 right right  7006 2008-06-15 12:44 mastermind.py
-rwxr-xr-x 1 right right  7098 2008-06-14 15:31 mastermind.py~
-rwxr-xr-x 1 right right  1152 2008-06-12 11:24 pick-random-package.py
-rwxr-xr-x 1 right right  1085 2008-06-07 11:35 pick-random-package.py~
-rwxr-xr-x 1 right right  1588 2008-06-01 13:42 langstons-ant.py
-rw-r--r-- 1 right right  1823 2008-06-01 13:30 langstons-ant.py~
-rwxr-xr-x 1 right right   981 2008-05-22 08:58 parse-for-packages.py
-rwxr-xr-x 1 right right   998 2008-05-22 08:56 parse-for-packages-0.py
-rw-r--r-- 1 right right  1023 2008-05-22 08:33 parse-for-packages-0.py~
-rwxr-xr-x 1 right right  1023 2008-05-22 08:33 parse-for-packages.py~
-rwxr-xr-x 1 right right   244 2008-05-19 22:45 alarm-boom.py
-rwxr-xr-x 1 right right   539 2008-05-19 20:25 move-half.py
-rwxr-xr-x 1 right right  1532 2008-05-18 21:18 date_demo1.py
-rwxr-xr-x 1 right right   278 2008-05-18 11:57 biggles-plotdata.py
-rwxr-xr-x 1 right right   438 2008-05-18 11:48 biggles-example1.py
-rw-r--r-- 1 right right 13433 2008-05-18 11:00 plot.pyc
-rwxr-xr-x 1 right right   105 2008-05-15 23:32 dec2hex
-rwxr-xr-x 1 right right   208 2008-05-15 22:28 list-files.py
-rw-r--r-- 1 right right  4976 2008-05-11 10:54 acfl.pyc
-rwxr-xr-x 1 right right   386 2008-05-11 10:53 test_acfl.py
-rwxr-xr-x 1 right right  3640 2008-05-11 10:51 acfl.py
-rwxr-xr-x 1 right right 15272 2008-04-18 22:04 conkyForecast.py

```

Notice that 
mtime2251 should contain all files last modified > 2251 days ago, while 
mtime2501 should contain all files last modified > 2501 days ago.

Firstly, mtime2501 should contain a subset of the files in mtime2251.
Secondly, mtime2501 should not contain files last modified on 2008-07-01. Something is just horridly wrong with the way find handles mtimes. (Or there is something horridly wrong with the way I hand find :))

---

### Post by unutbu on 2008-07-01
nowshining, I believe updatedb affects the database that locate uses, but it has no effect on find.


```

% man updatedb
DESCRIPTION
       This manual page documents  slocate,  **a  security-enhanced  version  of  locate**.
       updatedb is simply a link to slocate that implies the -u option.

```

---

### Post by sisco311 on 2008-07-04
Eureka!!!
[FONT=monospace]
[/FONT]for num in `seq 1 250 3000`; do find . -type f -mtime +$num **| xargs ls -lt** > /tmp/mtime$num; done

When xargs is empty the ls command is executed, without an argument, in the current
working directory.

Example:
*find . -type f -mtime +999*
output:
> 
./file1
./file2
=>ls -lt ./file1 and ls -lt ./file2 is executed
*find . -type f -mtime +BIGNUMBERHERE* => no file found
output:
> 
=> ls -lt is executed

---

### Post by unutbu on 2008-07-04
You're awesome, sisco311! Thanks so much!

---

