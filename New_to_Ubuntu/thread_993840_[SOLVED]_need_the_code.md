---
title: "[SOLVED] need the code"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by nnjond on 2008-11-26
Hi, can anyone help me?

I have a lge directory of jpgs How can I delete each alternate jpg?

---

### Post by albesan on 2008-11-26
hey,

How are they named?

---

### Post by nnjond on 2008-11-26
Thanks for your interest. 

formation****.jpg

eg:

formation1456.jpg
formation6573.jpg

etc...

---

### Post by davidbilla on 2008-11-26
> **nnjond said:**
> Thanks for your interest. 

formation****.jpg

eg:

formation1456.jpg
formation6573.jpg

etc...

Do an ls on the folder and redirect the output to an ascii file.

ls -l /imgfolder/ > imglist.txt

Remove the first line from imglist.txt which looks like "total <number>".

In a C code read and discard every alternate line from the file; fscanf will work just fine. Read each required line into a string and do an sscanf(you can choose to read only the last field in [sscanf]("http://www.cplusplus.com/reference/clibrary/cstdio/sscanf.html")) to get the last column in another string(filename-string). Using that as the filename do "system(rm <filename-string>)"

Like this.
```

sprintf(somestr,"rm %s",<filename-string>);
system(somestr);
```

Loop that until you've read all the files. Checking for EOF should be enough.

You can also do that using awk/sed and shell scripts.

---

### Post by Dedoimedo on 2008-11-26
Hello,

You want to delete each second files or such?

If that's the case, you might use the modulus mathematical operand. It tells you what the remainder of a division is. So if you divide by two, if the division is 0, you'll know you've hit an even-numbered line.

One crude way of doing it would be:

```

#!/bin/sh

list=`tree -fi | sed 's/\.\///g' | sed 's/^\.//g' | sed '/^$/d'`
counter=1;
for i in $list ; do
  if [ $((counter%2)) eq 0 ] ; then
    rm $i
    echo "$i deleted"
  fi
  counter=$counter+1
done

exit 0

```

You can also use instead of tree:

```

list=`ls -l | awk -F" " '{print $8}'

```

Be careful when removing files!!!

Dedoimedo

P.S. Decide whether you need the counter to start at 0 or 1 ...

---

