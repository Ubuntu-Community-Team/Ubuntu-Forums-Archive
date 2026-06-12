---
title: "Bash script for moving files"
date: 2012-05-01
forum: Programming Talk
---

### Post by huangweiqiu on 2012-05-01
I have a folder **/var/www/img** has lots of image files name by date.

I want to move all images  with 201108 filename to /root/a

I tried this bash but without luck

[HTML]$mv $(find . -name "201108") /root/a/;[/HTML]

Please could someone help?

---

### Post by HermanAB on 2012-05-01
mv *201108* /wherever/.

---

### Post by mörgæs on 2012-05-01
Moved to Programming Talk; title changed.

---

### Post by ofnuts on 2012-05-01
> **huangweiqiu said:**
> I have a folder **/var/www/img** has lots of image files name by date.

I want to move all images  with 201108 filename to /root/a

I tried this bash but without luck

[HTML]$mv $(find . -name "201108") /root/a/;[/HTML]Please could someone help?
You can't use the output of find (which is multi-line) directly as command parameters. In the general case, when you have a multi-line list of things that you  want to pass as multiple arguments to one single command, use "xargs". However, this is fraught with peril if you want to handle spaces in names etc... It's easier to ask find to execute a command on every file that matches: 

```

find **/var/www/img -name **"201108" -exec mv {}  /root/a \+

```

(the difference between \+or \; in the '-exec' part is that ";" has the command execute once for each file, while "+" creates a siongle command with all the files (which works very often, given Unix conventions)

---

### Post by huangweiqiu on 2012-05-01
```

find **/var/www/img -name **"201108" -exec mv {}  /root/a \+

```


------------------
I run this script but failed with error

[HTML]
find: missing argument to `-exec'[/HTML]

---

### Post by codemaniac on 2012-05-01
> **huangweiqiu said:**
> ```

find **/var/www/img -name **"201108" -exec mv {}  /root/a \+

```


------------------
I run this script but failed with error

[HTML]
find: missing argument to `-exec'[/HTML]

```
find **/var/www/img -name **"201108" -exec mv {}  /root/a/ \;
``` should work.

---

### Post by huangweiqiu on 2012-05-01
> **codemaniac said:**
> ```
find **/var/www/img -name **"201108" -exec mv {}  /root/a/ \;
``` should work.

the new one has no error, however no file was transfered to /root/a .Please help to check gain. almost done.

---

### Post by codemaniac on 2012-05-01
> **huangweiqiu said:**
> the new one has no error, however no file was transfered to /root/a .Please help to check gain. almost done.

Please make sure the file name is exactly **201108**.
Or if the filename contains 201108 as substring use *201108* .

```
find /var/www/img -name "*201108*" -exec mv {}  /root/a/ \;
```

---

### Post by huangweiqiu on 2012-05-01
> **codemaniac said:**
> Please make sure the file name is exactly **201108**.
Or if the filename contains 201108 as substring use *201108* .

```
find /var/www/img -name "*201108*" -exec mv {}  /root/a/ \;
```

works like a charm,thanks a lot!

---

### Post by mörgæs on 2012-05-01
Good, please mark the thread 'solved'.

---

### Post by ofnuts on 2012-05-01
> **huangweiqiu said:**
> works like a charm,thanks a lot!
My bad... just found that the "+" syntax works only if the "+" is right after the {}.

---

### Post by sisco311 on 2012-05-02
> **ofnuts said:**
> My bad... just found that the "+" syntax works only if the "+" is right after the {}.

GNU mv has a -t option:
```
find ... -exec mv -t /target {} +
```

the POSIX equivalent is:
```
find /dir -name '*whatever*' -type f -exec sh -c 'mv -- "$@" /target' _ {} +
```

---

