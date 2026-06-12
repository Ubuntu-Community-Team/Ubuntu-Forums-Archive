---
title: "[SOLVED] determine a file's last-modified date"
date: 2007-12-12
forum: Programming Talk
---

### Post by muaddib on 2007-12-12
Is there any easy/uniform way to access the last-modified time of a file from either bash or perl?
I wrote a bash script to back up files individually, which parses the command ls -l and strips out the date. It has worked perfectly for a while: it copies a file like 'file2.txt' to 'file2.txt.old-20071128', (where 20071128 is the date 'November 28, 2007'). Unfortunately, my script broke on the new system (note: both are ubuntu):

On the old system, the command 'ls -l' results in:

-rw------- 1 username username 0 2007-12-12 01:40 file1
-rw-r--r-- 1 username username 0 2007-12-12 01:40 file2.txt

On the new system, the same command shows:

-rw------- 1 username username 0 Dec 12 07:45 file1
-rw-r--r-- 1 username username 0 Dec 12 07:45 file2.txt

As you can see, the new system does not show the year, and the date is displayed in a difficult-to-parse format, which I cannot easily change. I think that there must be some easy way of accessing the last-modified date of a file (preferably in perl or bash). Anyone know how?

---

### Post by yabbadabbadont on 2007-12-12
From the "ls" manpage:
```
       --time-style=STYLE
              with -l, show times using style STYLE: full-iso, long-iso, iso, locale, +FORMAT.  FORMAT is interpreted like
              ‘date’; if FORMAT is FORMAT1<newline>FORMAT2, FORMAT1 applies to non-recent  files  and  FORMAT2  to  recent
              files; if STYLE is prefixed with ‘posix-’, STYLE takes effect only outside the POSIX locale

```
I would go with the "+FORMAT" option.  Read the "date" manpage for details on the various format string options.

Example:
```
/home/daffy $ ls -l --time-style=+%Y%m%d%H%M%S
total 20
drwxr-xr-x 2 daffy daffy 4096 20071210215028 Backgrounds
drwxr-xr-x 2 daffy daffy 4096 20071209033416 Desktop
drwxr-xr-x 2 daffy daffy 4096 20071209140436 Documents
lrwxrwxrwx 1 daffy daffy   26 20071209033218 Examples -> /usr/share/example-content
drwxr-xr-x 3 daffy daffy 4096 20071211204830 Temp
drwxr-xr-x 2 daffy daffy 4096 20071209133219 bin

```

---

### Post by ghostdog74 on 2007-12-12
you can also use find (GNU) or stat
eg
```

find . -type f -printf "%AY:%Ab:%Ad\n" 

```
check the  man page for find, and stat for more info

---

### Post by Majorix on 2007-12-12
> **muaddib said:**
> Is there any easy/uniform way to access the last-modified time of a file from either bash or perl?
I wrote a bash script to back up files individually, which parses the command ls -l and strips out the date. It has worked perfectly for a while: it copies a file like 'file2.txt' to 'file2.txt.old-20071128', (where 20071128 is the date 'November 28, 2007'). Unfortunately, my script broke on the new system (note: both are ubuntu):

On the old system, the command 'ls -l' results in:

-rw------- 1 username username 0 2007-12-12 01:40 file1
-rw-r--r-- 1 username username 0 2007-12-12 01:40 file2.txt

On the new system, the same command shows:

-rw------- 1 username username 0 Dec 12 07:45 file1
-rw-r--r-- 1 username username 0 Dec 12 07:45 file2.txt

As you can see, the new system does not show the year, and the date is displayed in a difficult-to-parse format, which I cannot easily change. I think that there must be some easy way of accessing the last-modified date of a file (preferably in perl or bash). Anyone know how?

The command behavior changing has to do with your aliases. Change the regarding alias back to what it was in the old system (Feisty?) and it should work again the same way it did back then.

---

### Post by muaddib on 2007-12-12
Thanks for all of the responses.
I am now using the time-style flag, and it works great:
ls -l --time-style=+%Y%m%d

Thanks!

---

### Post by onty on 2008-05-26
use date.

$date -r [filepath] +%[format]

---

### Post by muaddib on 2008-05-28
> use date.

$date -r [filepath] +%[format]

Okay! This is perfect: no parsing necessary. Thanks!

---

