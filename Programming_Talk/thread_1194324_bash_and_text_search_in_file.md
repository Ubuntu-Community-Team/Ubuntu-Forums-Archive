---
title: "bash and text search in file"
date: 2009-06-22
forum: Programming Talk
---

### Post by smurphy_it on 2009-06-22
Good day.  I am attempting to open a file, and search all lines of the file for today's date.  Then I want to go back to the previous line and grab the contents of the first column (or entire line and select what I want).  Thus doing a search and getting the current row # could help.  As rolling back to the previous line and outputting the format could work.

Any suggestions on how to do this ?  I was able to do it in perl (through other helpful posts) but due to the complexity of calling other scripts within that one, I opted to try and do it in bash instead.

What I have so far.

#!/bin/bash

SEARCH=`date +'%Y%m%d'`
DATAFILE="/home/user/sample.txt"
ARRAY=($( 'cat $DATAFILE' ))
TLEN=${#ARRAY[@]}

lines=( $(< "$DATAFILE" ) )
set +f
IFS="$OIFS"
grep $lines $SEARCH | echo "Pattern search $SEARCH has been found at:";

---

### Post by MadCow108 on 2009-06-22
you could loop over each line of the file and always remember the last line in a seperate variable.

why is perl a problem?
such kind of things are usally alot easier in perl (or awk or...)

---

### Post by Martin Witte on 2009-06-22
You can do this with sed, look [here]("http://sed.sourceforge.net/sed1line.txt") for more like this
```
martin@sony:~$ cat sample.txt 
a line
20090622
another line
20090622
and another one
martin@sony:~$ cat test.bash
#!/bin/bash

SEARCH=`date +'%Y%m%d'`
DATAFILE="/home/martin/sample.txt"

sed -n "/$SEARCH/{g;1!p;};h" $DATAFILE
martin@sony:~$ 

```

---

### Post by ghostdog74 on 2009-06-22
you can do it with just awk
```

awk 'BEGIN{
  date=strftime("%Y%m%d",systime())
}
$0~date{ print prevline }
{ prevline=$0}' datafile

```

---

