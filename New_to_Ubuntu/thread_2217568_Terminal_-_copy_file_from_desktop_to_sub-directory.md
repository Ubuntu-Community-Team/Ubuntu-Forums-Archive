---
title: "Terminal - copy file from desktop to sub-directory?"
date: 2014-04-17
forum: New to Ubuntu
---

### Post by Digitalscribbler on 2014-04-17
I'm trying to do what I thought was a rather simple thing in the Terminal, i.e., copy a file ("file1") from the desktop to a sub-directory (/temp), but for some reason when I enter ```
cp file1 /temp 
``` 
it returns an error message ```
cp: cannot stat ‘file1.txt’: No such file or directory
``` I must be missing something obvious, but can't seem to figure out what it is. Any idea what I'm doing wrong here? Thanks.

---

### Post by Bashing-om on 2014-04-17
Digitalscribbler; Hi !

Depends on where your Present Working Directory is;
do:
```

pwd

```
Bet it is not 'Desktop'.

Try the command as :
```

cp ~/Desktop/file1 /temp

``` giving the command a path to operate on.
Optionally:
change directory -from the default pwd - so the file is now in your path:
```

cd Desktop
cp file1 /temp

```
will now also work
and 
```

cd

```
will return you to the default pwd (/home/<username>).

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by Digitalscribbler on 2014-04-18
Thanks for the suggestion. I tried both, but unfortunately, I got the same error when trying both options:

> cp: cannot create regular file '/temp': Permission denied.

I also entered by credentials via sudo but that still gave me the same result. :(

---

### Post by Lars Noodén on 2014-04-18
The directory /temp does not normally exist.  So if you did not add it yourself it is not there.  There are, as [ part of the default](http://manpages.ubuntu.com/manpages/trusty/en/man7/hier.7.html), /var/tmp and /tmp.  So maybe you mean /tmp instead?

---

### Post by Vaphell on 2014-04-18
> from the desktop to a sub-directory (/temp)

subdirectory of what?
/temp is an absolute path, it's not a subdirectory of anything but /



assuming subdir of Desktop, you need 'temp' or './temp' or '~/Desktop/temp' depending on where you are.
```

cd ~/Desktop && cp file.txt temp
cp ~/Desktop/file.txt ~/Desktop/temp
```

protip: use [tab] for suggestions and autocompletion -> forget about typos and nonexistent files/dirs

---

