---
title: "Bash: Rename and simplify multiple file names"
date: 2008-05-20
forum: Programming Talk
---

### Post by olejon on 2008-05-20
Hi.

I have a lot of JPG-files with long and complicated file names.

I want to rename them, so if I have 100 files, I want the first one to be called 1.jpg and the last one to be called 100.jpg

How can I do that in bash?

Thanks

---

### Post by panayk on 2008-05-20
[COLOR="Red"]**** WARNING ****[/COLOR]
MAKE A BACKUP FIRST!!!

If your files are all in the current dir:

```
i=1; for f in ./*.jpg; do mv -i "$f" $i.jpg; let i=$i+1 ; done
```

---

### Post by panayk on 2008-05-20
This will pick-up where it left, if you add new files.

```
#!/bin/bash

set -e

i=1
for f in ./*.jpg ;
do
    if [[ "$f" =~ ^\./[1-9][0-9]*\.jpg$ ]]; then continue; fi

    while [[ -e $i.jpg ]] ;
    do
        (( i=$i+1 )) ;
    done

    mv -i "$f" $i.jpg
done
```

---

