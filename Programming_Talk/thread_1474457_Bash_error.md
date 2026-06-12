---
title: "Bash error"
date: 2010-05-06
forum: Programming Talk
---

### Post by dragos2 on 2010-05-06
I have this bash script which throws an error when I try to execute it:

```

./test3.sh
-bash: ./test3.sh: /bin/bash^M: bad interpreter: No such file or directory

```

```

#!/bin/bash

totalLines=0

function diffSize {
 size=$(cat diff.txt | wc | awk '{ print $1 }')
 #size=$(wc -l diff.txt) # why not working ?
 echo $size
}

if [ `diffSize` -gt $totalLines ]; then
    echo "Changed files"
 else
    echo "No changed files."
fi

```Any idea what is causing it ?

---

### Post by dragos2 on 2010-05-06
I found the cause. I was writing it in Notepad++ in Windows and run it in Linux.

---

### Post by Portmanteaufu on 2010-05-06
> **dragos2 said:**
> I found the cause. I was writing it in Notepad++ in Windows and run it in Linux.

Just in case you weren't aware of its existence, Notepad++ has a "Convert to Unix" button under its "Format" menu. This makes all your file's newlines Unix-compatible so you can run code written in Notepad++ directly on your Linux box.

EDIT:

Once you've hit "Convert to Unix", you're pretty much set. You don't have to keep hitting it as you add new lines.

---

### Post by dragos2 on 2010-05-07
> **Portmanteaufu said:**
> Just in case you weren't aware of its existence, Notepad++ has a "Convert to Unix" button under its "Format" menu. This makes all your file's newlines Unix-compatible so you can run code written in Notepad++ directly on your Linux box.

EDIT:

Once you've hit "Convert to Unix", you're pretty much set. You don't have to keep hitting it as you add new lines.

Thanks. That feature used to be in an old version. These new ones seem to hide it pretty well.

---

