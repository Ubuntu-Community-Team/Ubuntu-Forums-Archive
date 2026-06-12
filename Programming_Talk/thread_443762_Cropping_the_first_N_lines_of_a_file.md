---
title: "Cropping the first N lines of a file"
date: 2007-05-14
forum: Programming Talk
---

### Post by Amurko on 2007-05-14
I can't seem to find a general purpose UNIX command that does exactly that..

Anyways, is it possible to write a shell script that'll take the following parameters: N and a filename and trim away the first N lines in that file?  I tried working with the command "last" but it requires you to know the number of lines in that file.  So I tried to extract that information using the "wc -l <filename>" but it not only displays the # of lines but also <filename> in the output.

Any ideas?

---

### Post by ghostdog74 on 2007-05-14
> **Amurko said:**
> I can't seem to find a general purpose UNIX command that does exactly that..

Anyways, is it possible to write a shell script that'll take the following parameters: N and a filename and trim away the first N lines in that file?  I tried working with the command "last" but it requires you to know the number of lines in that file.  So I tried to extract that information using the "wc -l <filename>" but it not only displays the # of lines but also <filename> in the output.

Any ideas?

```

#!//bin/sh
param=$1
filename=$2
##code to check param  and filename here
## main code
awk -v num=param 'NR>num' > newfile


```

---

### Post by cwaldbieser on 2007-05-15
> **Amurko said:**
> I can't seem to find a general purpose UNIX command that does exactly that..

Anyways, is it possible to write a shell script that'll take the following parameters: N and a filename and trim away the first N lines in that file?  I tried working with the command "last" but it requires you to know the number of lines in that file.  So I tried to extract that information using the "wc -l <filename>" but it not only displays the # of lines but also <filename> in the output.

Any ideas?

```

#!/bin/bash

PROG=$0;
STARTLINE=1;
ENDLINE=\$;

while getopts ":b:e:" opt; do
    case $opt in
        b ) STARTLINE=$OPTARG ;;
        e ) ENDLINE=$OPTARG ;;
        * ) echo "usage: $0 [-b begin-line] [-e end-line] file";
            exit 1;;
    esac
done
shift $(($OPTIND - 1));
if [ $# -ne 1 ]; then
    echo "usage: $0 [-b begin-line] [-e end-line] file";
    exit 1;
fi
FILENAME="$1";

sed -n "${STARTLINE},${ENDLINE}p" "$FILENAME";

```
All the lines except the first do the command line processing.
The last command (sed) does all the work.
-n option means don't print any lines unless the "p" command is given.
sed programs can be given addresses of the form <start>,<end> where start and end are line numbers.  end can also be "$", in which case it matches the last line.

I noticed after I wrote this that I didn't do exactly what you wanted.  You would have to invoke my script as "prog -b <N+1> <file>" to get what you want.  I hope the basic idea helps, though.

---

