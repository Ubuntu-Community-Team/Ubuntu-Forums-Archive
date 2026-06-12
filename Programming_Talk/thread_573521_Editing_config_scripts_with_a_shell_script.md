---
title: "Editing config scripts with a shell script"
date: 2007-10-11
forum: Programming Talk
---

### Post by dizwell on 2007-10-11
I havea  configuration file which already contains some lines of data. Suppose it looks like this:

Command1
Command2
Command3
End-of-file

I can write a shell script that does this:
cat >> /etc/config << EOF
Command4
Command5
EOF

...and when I run the shell script, it appends its two lines to the original file, so it ends up looking like this:

Command1
Command2
Command3
End-of-file
Command4
Command5

But what I actually need it to do is to insert the new lines before the line which says End-of-File so that I end up with:

Command1
Command2
Command3
Command4
Command5
End-of-file

Is there a relatively easy way of doing this, please? I'ev generalised the example because I need to use this technique in several different places. But it is always the **last **line of the config file that I need to insert stuff before.

Any tips, pointers or code snippets gratefully received!

---

### Post by Modred on 2007-10-11
The sed program can probably fit your needs.

```

#!/bin/sh
sed -e '$ i\
First line to insert \
Second line to insert \
third line to insert \
last line to insert' temp_config_file

mv temp_config_file config_file

```

There may be a more elegant way to do this, but I've very new to sed.  I wrote to a temp file and then overwrote the old file because sed writes to standard out by default and redirecting to the file you read in from tends to overwrite your original file *before* it is read in.  :\

---

### Post by arsenic23 on 2007-10-11
Also, if your more worried about inserting your new text right before the 'End-of-file' line, then you could replace the $ with an expression that equals your ending line.  So the code would look like this:
```

#!/bin/sh
sed -e '/^End-of-file/ i\
First line to insert \
Second line to insert \
third line to insert \
last line to insert' temp_config_file

mv temp_config_file config_file

```

For your example you'll get the same result either way, but by doing it this way will make sure that the commands are inserted directly above the 'End-of-file' line, in case there are lines below it in the future.

---

### Post by ghostdog74 on 2007-10-11
```

awk '/End-of-file/ { printf "insert1\ninsert2\n"}1' "file"

```

---

