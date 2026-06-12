---
title: "Rename a file according to its location"
date: 2013-02-25
forum: Programming Talk
---

### Post by srwatson on 2013-02-25
Hello everyone

I would like to rename a file according to it's location.  The file will be located anywhere below a toplevel folder so the search that finds the file needs to be recursive.

This is what I have so far

find /tmp -name *.log| while read file; do
echo "$(dirname $file)" > /tmp/filename
sed -e 's:/:_:g' /tmp/filename > /tmp/filename1
done
test=$(cat /tmp/filename1)
cp /tmp/*.log /tmp/$test*.*.log

for example if there is a file in 

/var/www/test

called test1.log then this file will become

/var/www/test/var_www_test_test1.log


Hope this makes sense

Thanks

---

### Post by Vaphell on 2013-02-25
```
while read -rd $'\0' f
do
  d=${f%/*}                        # dir
  n=${d#/}; n=${n//\//_}_${f##*/}  # new name
  echo mv "$f" "$d/$n"
done < <( find /tmp -type f -name '*.log' -print0 )
```
if the names are good, remove *echo* to perform mv-ing

---

### Post by srwatson on 2013-02-25
Hi, thanks for your quick response

When I run the script I get

Line 6, syntax error: redirection unexpected

---

### Post by srwatson on 2013-02-25
My fault....I hadnt started the script with

#!/bin/bash

---

### Post by srwatson on 2013-02-25
Actually is it possible to include todays date on the file that gets created....

Thanks

---

### Post by Vaphell on 2013-02-25
in what format?
YYYY-MM-DD_tmp_somedir_filename.log?

```
#!/bin/bash

while read -rd $'\0' f
do
  d=${f%/*}
  n=**$(date +%Y-%m-%d)**${d//\//_}_${f##*/}
  echo mv "$f" "$d/$n"
done < <( find /tmp -type f -name '*.log' -print0 )
```

check *date --help* to see what %-placeholders it supports and construct your own format string if necessary.

> Actually is it possible to include todays date on the file that gets **created**....
> I would like to **rename** a file according to it's location.
so which is it?

---

