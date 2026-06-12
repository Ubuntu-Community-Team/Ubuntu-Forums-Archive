---
title: "Search inside a file through value of the variable"
date: 2017-08-17
forum: New to Ubuntu
---

### Post by sed_faster on 2017-08-17
Hello,

I am searching about a way to identify if a determine file exist on server. For this I create a entire list of hash of this files on server through md5sum. Now I need found a way to create a task or script where receive two parameter: **first** this is a file to verify if exist on database and **second** it is a file where I saved the list about all hash exist on my server files (something like database_md5sum.txt).

On file **database_md5sum.txt** I have two columns where first column is the hash and second columns it is the corresponding file name. I need verify if the file "new_file_pdf.pdf" exist on this database through chechsum number. For this I am thinking create this script:
```

hello='md5sum new_file_pdf.pdf'
grep $hello database_md5sum.txt

```

But this code didn't result. I know put result of the command on variable but how can I use this value to search inside a file, as database_md5sum.txt?

Thanks

---

### Post by TheFu on 2017-08-17
md5sum has collisions. That has been proven.  Don't use it.

Files on a system can be found using 'locate' if they don't change too much.

Don't use single-ticks '. use back-ticks `.

Also, **#!/bin/bash -x** will be helpful to seeing the expansions.

---

### Post by steeldriver on 2017-08-17
You will need to "soft quote" the variable, since your search pattern has whitespace in it:

```

hello='md5sum new_file_pdf.pdf'
grep [COLOR=#0000ff]"[/COLOR]$hello[COLOR=#0000ff]"[/COLOR] database_md5sum.txt

```

Otherwise, the shell will split the text into separate arguments (and grep will treat all but the first as names of files to be searched)

---

### Post by Tadaen_Sylvermane on 2017-08-18
I think backticks is old stuff, haven't seen it used in new scripting lately for bash. In my understanding brackets are more used.

I'd write it like this personally.

```
for file in ${@} ; do
  HASH=$(sha256sum "$file")
  if grep "$HASH" database_sha256sum.txt ; then
    echo "hash found. (do something)"
  else
    echo "hash not found. (do something else)"
  fi
done
```

Really though I can't help but think something like snapraid might be the better choice. It would be more automatic, and give you redundancy  as well as detect bitrot and changing hashes from existing sync vs new sync. Wouldn't have to think about it either. Just run a sync and it will tell you what changed from last time, if anything. Could even run a cronjob to email you the results of whatever has changed.

---

