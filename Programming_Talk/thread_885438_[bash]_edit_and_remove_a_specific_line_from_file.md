---
title: "[bash] edit and remove a specific line from file"
date: 2008-08-10
forum: Programming Talk
---

### Post by Ristar on 2008-08-10
what is the code in bash to edit or remove a specific line from file?

assuming the file is:
> 
Andy,Manager,4000
Bryan,Programmer,3000
Charlie,Clerk,2000
Danny,Clerk,1500


how do i make the program search for a match in any fields, so that the user can select which record with a field that matches the keyword the user typed to delete from the file, or edit a field?

thanks..

---

### Post by ghostdog74 on 2008-08-10
it seems to be related to this [post](http://ubuntuforums.org/showthread.php?t=884648) and i have introduced awk to you. Why don't you try and code something. Its no use giving you code to use, and in the end you learn nothing. If in doubt, look up the awk/bash links in my sig to learn it.

---

### Post by Ristar on 2008-08-10
using

```

sed 2d file > file

```

deletes the whole file... there's a work around, but it wouldnt be good if the file's very large. 

wats the correct way of resolving this?

---

### Post by ghostdog74 on 2008-08-10
> **Ristar said:**
> using

```

sed 2d file > file

```

deletes the whole file... there's a work around, but it wouldnt be good if the file's very large. 

wats the correct way of resolving this?
redirect it to a new file. or use the -i option of sed command.

---

### Post by Ristar on 2008-08-10
'

---

### Post by Ristar on 2008-08-10
how can i make awk stop looking for a line after the first match and not lose the rest of the data?

---

### Post by Yuzem on 2010-03-11
This is how I do it using ONLY bash:
```
file=$(<file)
echo "$file" | {
  while read line; do
    if [[ $line != *$1* ]]; then
      echo $line
    fi
  done
} > file
```

Run it like this:
script text

The script should remove any line containing "text"

---

### Post by DaithiF on 2010-03-11
I find it a little curious how these old threads get replied to so long after the last posting.  but in any case, the OP seemed to want a command to delete only the first line that matches a particular piece of text.  no doubt there are many better ways to do this, but in sed this would do it:
```
sed '/foo/{x;/^$/d;x}' somefile
```

---

