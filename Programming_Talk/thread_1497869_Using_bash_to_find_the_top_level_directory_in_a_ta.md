---
title: "Using bash to find the top level directory in a tar."
date: 2010-05-31
forum: Programming Talk
---

### Post by vamega on 2010-05-31
I'm trying to write a script that extracts a tar.gz archive. I know that  the archive will contain just a single folder at the top level, and  that this folder will contain a directory structure under it. The name  of the folder at the top level is not known.

I started by using

```

files = "$(tar --no-recursive -tf public_html/drupal-6.16.tar.gz)"

```

This still lists the entire directory structure, even though the  --no-recursive option is given.
Finally if I cannot simply find the name of the top level directory,  then how can I extract the first line from the output of the above  command.

Thanks a lot in advance.

Vamega

---

### Post by amauk on 2010-05-31
```
tar -tf archive.tar.gz | grep -o '^[^/]\+' | sort -u
```

---

### Post by vamega on 2010-05-31
That works great.
Shall I take it that it isn't possible to simply untar only the top level directory?

---

### Post by amauk on 2010-05-31
Following takes a single argument (the tarball) and extracts level 1 files
(Level 1 being, files inside a top directory)

```
#!/bin/bash

if [ -z "$1" ] || [ ! -f "$1" ]; then
	echo "Err: File not found"
	exit 1
fi

IFS=$'\n'
ONLY_L1_FILES=$(tar -tf "$1" | grep '^[^/]\+/[^/]\+$')

for FILE in $ONLY_L1_FILES; do
	tar xzvvf "$1" "$FILE"
done
```

---

### Post by geirha on 2010-05-31
With pax, a POSIX archiver
```
pax -rzf archive.tar.gz -c '*/*/*'
```

---

### Post by diesch on 2010-05-31
```
files = "$(tar --exclude '*/*' -tf public_html/drupal-6.16.tar.gz)"
```

---

### Post by vamega on 2010-06-02
Thanks guys.
All the above solutions work  fine.
I just decided to go with diesch's method as I didn't want to mkae pax a dependancy of the script, and found it more efficient that using grep and then sorting for unique entries.

Thanks a lot.

Vamega

---

### Post by chud67 on 2011-12-29
tar --strip-components 1 -xvf latest.tar.gz

---

