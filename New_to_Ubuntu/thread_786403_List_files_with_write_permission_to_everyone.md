---
title: "List files with write permission to everyone"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by control_guy on 2008-05-08
Hello there

How can I list only those file (with ls command) which are write-able by everyone.

When managing web-server folders, I often need to check that there are no unauthorized permissions. Such a command would help a lot.

Regards

---

### Post by hyper_ch on 2008-05-08
find has an option on permissions mode...

> 
-perm mode
File's  permission  bits are  exactly mode (octal or symbolic). Since an exact match is required, if you want to use  this  form for  symbolic  modes,  you  may have to specify a rather complex mode string.  For example '-perm g=w'  will  only  match  files which  have  mode 0020 (that is, ones for which group write permission is the only permission set).  It is more likely that you will want to use the '/' or '-' forms, for example '-perm -g=w', which matches any file with group  write	permission. See the EXAMPLES section for some illustrative examples.



       find . -perm 664

       Search for files which have read and write permission for their	owner,
       and  group,  but  which	other  users can read but not write to.  Files
       which meet these criteria but have  other  permissions  bits  set  (for
       example if someone can execute the file) will not be matched.

       find . -perm -664

       Search  for  files which have read and write permission for their owner
       and group, and which other users can read, without regard to the  pres-
       ence  of  any  extra  permission bits (for example the executable bit).
       This will match a file which has mode 0777, for example.

       find . -perm /222

       Search for files which are writable by somebody (their owner, or  their
       group, or anybody else).

       find . -perm /220
       find . -perm /u+w,g+w
       find . -perm /u=w,g=w

       All  three  of these commands do the same thing, but the first one uses
       the octal representation of the file mode, and the other  two  use  the
       symbolic  form.	These commands all search for files which are writable
       by either their owner or their group.   The  files  don't  have	to  be
       writable by both the owner and group to be matched; either will do.

       find . -perm -220
       find . -perm -g+w,u+w

       Both  these  commands  do  the  same  thing; search for files which are
       writable by both their owner and their group.

       find . -perm -444 -perm /222 ! -perm /111
       find . -perm -a+r -perm /a+w ! -perm /a+x

       These two commands both search for files that are readable  for	every-
       body  (-perm -444 or -perm -a+r), have at least on write bit set (-perm
       /222 or -perm /a+w) but are not executable for anybody (!   -perm  /111
       and ! -perm /a+x respectively)

---

### Post by encompass on 2008-05-08
Good question...
```
ls -l
```
should give you this...
```

jason@lappy:~$ ls -l
total 216
-rw-r--r-- 1 jason jason   1871 2008-05-04 16:16 Book1.gnumeric
drwxr-xr-x 2 jason jason   4096 2008-05-07 11:11 books
drwx------ 5 jason jason   4096 2008-05-07 22:01 Desktop
drwxr-xr-x 2 jason jason   4096 2008-05-07 10:45 documents
drwxr-xr-x 3 jason jason   4096 2008-04-17 05:38 downloads
drwxr-xr-x 4 jason jason   4096 2008-04-12 13:50 GNUstep
drwxr-xr-x 2 jason jason   4096 2008-05-08 07:17 images
drwxr-xr-x 2 jason jason   4096 2008-04-29 08:19 music
-rw-r--r-- 1 jason jason 158954 2008-05-03 21:13 output.pdf
drwxr-xr-x 2 jason jason   4096 2008-04-18 22:22 presentations
drwxr-xr-x 3 jason jason   4096 2008-04-27 10:45 programming
drwxr-xr-x 2 jason jason   4096 2008-04-13 09:24 public_html
drwxr-xr-x 2 jason jason   4096 2008-04-15 17:23 spreadsheets
drwxr-xr-x 2 jason jason   4096 2008-05-07 20:52 videos
drwxr-xr-x 2 jason jason   4096 2008-04-27 15:27 volume
jason@lappy:~$ 

```
so...
```

ls- l| grep drwx 

```
would almost always give you all directories that can be read,writen and executed by the user.
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)
Helps you learn the permissions system...
Grep is a nice program to search through your results.
and grep -e will let you do regular expressions...
[http://www.regular-expressions.info/tutorial.html](http://www.regular-expressions.info/tutorial.html)
But that stuff get's pretty complicated but very powerful.

---

### Post by encompass on 2008-05-08
Or his, which I never knew before and it A LOT better than my solution. :D
Good luck!

---

### Post by control_guy on 2008-05-08
> **hyper_ch said:**
> find has an option on permissions mode...


Great. I could search
find . -perm 777
and look at that, I found one folder all set for hacking.

Danke noch mal

---

### Post by hyper_ch on 2008-05-08
maybe you should rather run this:

```

find . -perm -a+x

```

---

