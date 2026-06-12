---
title: "Shell script to remove ? from filenames"
date: 2006-06-28
forum: Programming Talk
---

### Post by dlyons on 2006-06-28
Hey guys,

I'm trying to get started on writing a couple scripts to handle new files I download and move them to another location. However, I'm confused on where to get started on how to rename a group of filenames and remove '?' and ':' characters. I'm sure I could do something like this in Perl but I'd like to handle it using commands and shell scripts.

Any ideas?

---

### Post by Zed on 2006-06-28
If you have Perl installed, you have a rename command.

```

rename 's/([^?]*)\?+([^?]*)/$1$2/g' *

```

See also

```

sudo apt-get install mmv
man mmv

```

I'm less familiar with exactly what it can do, though.

---

### Post by ynef on 2006-06-29
That sounds like a job for the program sed and regular expressions. The general idea would be to examine every file in the directory and (using sed) find out which ones need to have their names changed and change accordingly. 

The following code, as well as the site at [1] should get you started.

```

#!/bin/bash

for current in *
do
    newname=`echo $current | sed -e 's/[:?]//g'`
    echo "Old name: $current New name: $newname"
done

```

[1] [http://pegasus.rutgers.edu/~elflord/unix/sed.html](http://pegasus.rutgers.edu/~elflord/unix/sed.html)

---

### Post by dlyons on 2006-06-29
Great, I was looking for an option such as sed that I could use in conjuction with other bash functions.

Thanks!

---

