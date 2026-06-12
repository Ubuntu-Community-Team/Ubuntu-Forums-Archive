---
title: "how to check a directory's permissions in a bash script???"
date: 2011-06-28
forum: Programming Talk
---

### Post by helloise on 2011-06-28
i am writing a bash script and want to check the permissions of a certain directory and if it is set to 777 then continue with the rest if it is not set i must 

chmod 777 web

how will i do this please??
thank you

---

### Post by nzjethro on 2011-06-28
I found this script:

```
#!/bin/ksh
ls -ld $* | awk 'BEGIN {v["r1"]=400;
v["w2"]=200; v["x3"]=100;
v["s3"]=4100; v["S3"]=4000v["r4"]=40;
v["w5"]=20 ; v["x6"]=10;
v["s6"]=2010; v["S6"]=2000v["r7"]=4;
v["w8"]=2  ; v["x9"]=1;
v["t9"]=1001; v["T9"]=1000}

{val=0 for (i=1;i<=9;i++) val=val+v[substr($0,i+1,1)i] **printf "\%4d \%s\n"**,val,$NF}
```
at [this website.]("http://bbs.prog365.com/unix-help-how-to-check-chmod-of-a-file-directory--60480-1-1.html") It looks as though, if you incorporate it into your bash, it will give you the value you want.

You'll just have to change the bolded bit, so that it assigns the value to a variable to use in your boolean, rather than printing it.

---

### Post by DaithiF on 2011-06-28
check out [B]stat

[/B]e.g.```
stat /some/path
```
To pick out the permissions, something like:
```
perms==$(stat /some/path | sed -n '/^Access: (/{s/Access: (\([0-9]\+\).*$/\1/;p}')
if [[ $perms =~ 777 ]]; then
    # do stuff here
fi
```

---

### Post by slavik on 2011-06-28
man test

---

### Post by geirha on 2011-06-28
If you want all files to have the same mode, just run the chmod uncoditionally on all files. If the file already has that mode, nothing happens, if it has a different mode, it gets the new mode.

Now on a side-note, chmod 777 is never a good solution.

---

### Post by Habitual on 2011-07-03
> **geirha said:**
> ...Now on a side-note, chmod 777 is never a [s]good[/s] solution.

:)

---

### Post by papibe on 2011-07-03
Just simplifying DaithiF's idea:
```
#!/bin/bash
...
perm=$(stat -c %a "$f")

if [ "$perm" = "777" ]; then
    echo "$f permissions are 777"
    # doing the rest.
fi
...

```

---

