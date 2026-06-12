---
title: "Bash Scripting: String question"
date: 2005-10-21
forum: Programming Talk
---

### Post by Cyrus on 2005-10-21
Hi,

I am writing a small bash script which gets a String as parameter (the path to the files). How can I add this String with the filename?

```
FOLDER="$1"

for i in *.flac; 

	do metaflac --remove-all-tags --import-tags-from="$FOLDER"`basename $i .flac`.tag $i; 

done
```

It is basically the part between folder and basename - in Java I would put a + between ...

---

### Post by Cyrus on 2005-10-21
Hi, it works now with this "workaround":

```
FOLDER="$1"

cd "${FOLDER}"

for i in *.flac; 

	do metaflac --remove-all-tags --import-tags-from=`basename ${i} .flac`.tag $i

done

cd ..
cd ..
```

It is not very nice but it is doing its job. if you have a better solution (integrating the $FOLDER in the for-loop), please tell me

---

### Post by darth_vector on 2005-10-24
try this:

#!/bin/bash
folder=$1
for current_file in filelist; do
    full_path="$folder"+"$current_file"
#do whatever with "$full_path"
done

---

### Post by darth_vector on 2005-10-24
grr, hit submit twice and cant delte this reply! soory people!

---

