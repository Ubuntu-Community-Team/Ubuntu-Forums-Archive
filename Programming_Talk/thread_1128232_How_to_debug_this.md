---
title: "How to debug this?"
date: 2009-04-17
forum: Programming Talk
---

### Post by huangyingw on 2009-04-17
hello,
    I have difficultity at debuging the shell script. Is there any IDE for shell debug?
    The following are my script:
==========================================================
#! /bin/sh
x=`echo $0 | grep "^/"`
if test "${x}"; then
	script_path=$(dirname "$0")
else
	x=`echo $0 | sed -e 's/\.\///g'`
	script_path=$(dirname `pwd`/${x})
fi

dir=/root/myproject/linux/shell/folder/
for file in `find ${dir} -type f`
do
	new_folder=`sed -n 's,.*/\([a-z]*\).*\.jpg,\1,p' ${file}`
	if [ ! -e ${new_folder} ]; then
		#echo ${new_folder}
		mkdir ${new_folder}
	fi
done
==========================================================
The above script return me "[: 18: feqefe: unexpected operator", what is the cause?
the contents of the "folder", actually, I want to ignore the .svn subfolder recursively. And I want to extract the "prefix" from file name, for example, extract dkefe from dkefe01dad.jpg, and created a subfolder named "dkefe",and move the dkefe01dad.jpg into that newly created subfolder.
==========================================================
.svn  dkefe01dad.jpg  fdke01dad.jpg   fefe01dad.jpg  feqefe01dad.jpg
==========================================================

---

### Post by monkeyking on 2009-04-18
I dont think theres some magic way of debugging bash scripts.

I usually resort to hideous amount of echos.

---

### Post by stroyan on 2009-04-19
You can use "set -x" in a script file or "bash -x scriptfile" to
make bash output each command as it executes it.
That can be very revealing.

Or you can install the bashdb package and use bashdb to single step
and inspect variable values.

Your problem is likely to be caused by spaces and other interesting
characters in file and directory names.  You should use double quotes like
    mkdir "${new_folder}"
to handle such characters.
The "for file in ``" style is not good for handling spaces in names.
You could instead use reading a line at a time from a pipe.
find "${dir}" | while read f; do echo "$f"; done

---

### Post by stroyan on 2009-04-19
Looking further at the "for" loop style, I find that spaces can be handled with quoting.
```

for file in "`find ${dir} -type f`";do echo "$file";done

```

---

### Post by huangyingw on 2009-04-20
thank you all.
I am trying..
All of your replies would encourage me to go ahead..

---

### Post by leandromartinez98 on 2009-04-20
I usually debug bash scripts by adding "exit" statements after one line,
than after the following one, etc (when possible), until the problem appears.
This helps to identify in which line the error appears.

---

### Post by huangyingw on 2009-04-21
> **leandromartinez98 said:**
> I usually debug bash scripts by adding "exit" statements after one line,
than after the following one, etc (when possible), until the problem appears.
This helps to identify in which line the error appears.
yes, yours is a good way. I used to use two echo, to do binary search to locate the error line.
Yours and mine sound like similar ways..

---

