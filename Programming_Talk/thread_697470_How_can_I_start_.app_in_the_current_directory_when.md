---
title: "How can I start ./app in the current directory when make did ok?"
date: 2008-02-15
forum: Programming Talk
---

### Post by Zdravko on 2008-02-15
I already have my universal Makefile produce an executable named app.
Gedit has the Ctrl+f8 shortcut to automatically invoke make. I added another command "Build and run", which performs the same as "Build", but at the end when make finishes successful, tries to start ./app. How would look the code for that?
Here is the code I copied from the "Build" shortcut from gedit:
```

#!/bin/sh

EHOME=`echo $HOME | sed "s/#/\#/"`
DIR=$GEDIT_CURRENT_DOCUMENT_DIR
while test "$DIR" != "/"; do
    for m in GNUmakefile makefile Makefile; do
        if [ -f "${DIR}/${m}" ]; then
            make -C "${DIR}"
            exit
        fi
    done
    DIR=`dirname "${DIR}"`
done
echo "No Makefile found!" > /dev/stderr

```

---

### Post by Zwack on 2008-02-15
Add $DIR/app on the line between the make -C  and the exit.

Of course that will not work if make fails so you should probably check the return value from the make first...

if [ $? ] then
  $DIR/app
fi

Should work, provided that your executable is always called app

Z.

---

### Post by Zdravko on 2008-02-15
Thanks! You forgot the ; after ] ;)

---

### Post by Zwack on 2008-02-15
You're right... but I usually write it as

```

if [ $? ]
then
  $DIR/app
fi

```

But I didn't include the CODE tags on the last one and I didn't think too long before responding.

Z.

---

