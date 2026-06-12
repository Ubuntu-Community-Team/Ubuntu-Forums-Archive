---
title: "help regarding wget"
date: 2012-02-03
forum: Programming Talk
---

### Post by anuajay1988 on 2012-02-03
Sir, I am downloading some files sequentially from a ftp server with the help of a shell script.... sometimes it happens that a particular file is not uploaded at that time n will be uploaded after few minutes.....

AT present it skips that file and proceed downloading rest files...
I want that it should wait or retry until that file is uploaded/... and then it should proceed further.... thanx

---

### Post by Lars Noodén on 2012-02-03
You'll need to write a script that knows the file names and downloads them one by one, waiting if one is unavailable.  You can do that fairly easily in bash or perl.  However, wget by itself will not be enough in that regard.   It will need to be wrapped in a script.

---

### Post by ofnuts on 2012-02-03
> **Lars Noodén said:**
> You'll need to write a script that knows the file names and downloads them one by one, waiting if one is unavailable.  You can do that fairly easily in bash or perl.  However, wget by itself will not be enough in that regard.   It will need to be wrapped in a script.A more efficient way is to skip the file that isn't available, process the next one, and at the end of the pass, compare the list of URLs with the list of obtained files, and rerun for the missing file(s).

---

### Post by anuajay1988 on 2012-02-06
> **ofnuts said:**
> A more efficient way is to skip the file that isn't available, process the next one, and at the end of the pass, compare the list of URLs with the list of obtained files, and rerun for the missing file(s).
can i get the script for that....

---

### Post by ofnuts on 2012-02-06
> **anuajay1988 said:**
> can i get the script for that....
Something like
```
#! /bin/bash

function localfile
{
# extracts local file from URL
# here a barebones version, you may have to roll you own
    echo $(basename $1)
}

while read url 
do
  #echo url if file isn't there
  [[ ! -f $(localfile $url) ]] && echo $url
done 

```called as:
```
missed <original.lst >missing-ones.lst
```

---

### Post by anuajay1988 on 2012-02-14
it din worked dear....

---

