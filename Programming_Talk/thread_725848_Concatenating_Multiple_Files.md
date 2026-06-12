---
title: "Concatenating Multiple Files"
date: 2008-03-16
forum: Programming Talk
---

### Post by Jexel on 2008-03-16
Hi there,

Basically I've dumped all my SMS's from my phone onto my computer. I'm trying to write a command that will concatenate all the sms's from one specific number into one file.

The command:
 ```
grep -l +xxxxxxxxxxx sms*

```

Gives all the filenames of the files which contain the particular phone number. How can I then pipe this into another command that will read the file and pipe it into another file?

---

### Post by ghostdog74 on 2008-03-16
> **Jexel said:**
> Hi there,

Basically I've dumped all my SMS's from my phone onto my computer. I'm trying to write a command that will concatenate all the sms's from one specific number into one file.

The command:
 ```
grep -l +xxxxxxxxxxx sms*

```

Gives all the filenames of the files which contain the particular phone number. How can I then pipe this into another command that will read the file and pipe it into another file?

try 

```

grep -l +xxxxxxxxxxx sms* | while read -r FILE
do
  # do processing on file $FILE
done

```

---

### Post by Jexel on 2008-03-16
that did the trick. Thanks a lot!

---

### Post by supirman on 2008-03-16
Or you could have just:

[PHP]cat `grep -l +xxxxxxxxxxx sms*` > xxxxxxxxxxx.txt[/PHP]

---

### Post by ghostdog74 on 2008-03-16
> **supirman said:**
> Or you could have just:

[PHP]cat `grep -l +xxxxxxxxxxx sms*` > xxxxxxxxxxx.txt[/PHP]
Not if there are customized processing needed to be done on each line of those files found

---

### Post by supirman on 2008-03-16
> **ghostdog74 said:**
> Not if there are customized processing needed to be done on each line of those files found

OP said he wanted to concatenate multiple files.  There was no implication of special processing requirements per file...

---

