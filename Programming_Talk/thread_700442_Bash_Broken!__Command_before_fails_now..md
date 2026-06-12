---
title: "Bash Broken?!  Command before fails now."
date: 2008-02-18
forum: Programming Talk
---

### Post by Gen2ly on 2008-02-18
Hello all.  I'm been building a couple scripts as of late and all is doing good until I ran one of my original bash scripts.  I've used this a few times before but now its exits with:

```
/home/user/.scripts/Programs/tarer: line 8: conditional binary operator expected
/home/user/.scripts/Programs/tarer: line 8: syntax error near `==""'
/home/user/.scripts/Programs/tarer: line 8: `if [[ "LOCATION" =="" ]]; then'
```

This is the original bash script:

```
#!/bin/bash

# tar files and folders

NAME=$1
LOCATION=$2

if [[ "LOCATION" =="" ]]; then
    echo "tarer </dir/name> </location/to/start>"
    exit;
fi

tar -czpvf $NAME.tgz $LOCATION
```

I've updated to the latest version of bash, reset the environment and restarted the system.

Any ideas?

---

### Post by ruy_lopez on 2008-02-18
Try this:

```

#!/bin/bash

NAME $1
LOCATION $2

if [ -z $LOCATION ]; then
        echo "tarer: </dir/name> </location/to/start>"
        exit;
fi

tar czvpf $NAME.tgz $LOCATION

```

The -z flag returns true if the string in $LOCATION is zero bytes.

---

### Post by Bachstelze on 2008-02-18
```
if [[ "LOCATION" =="" ]]; then
```

Only one equal sign in Bash !

```
firas@nobue ~ % foo=bar; [ $foo = bar ] && echo "foo"
foo
```

---

### Post by Gen2ly on 2008-02-18
thanks alot ruy_lopez.  that did the job! :)

---

