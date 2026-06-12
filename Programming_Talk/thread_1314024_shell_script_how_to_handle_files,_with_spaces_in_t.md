---
title: "shell script: how to handle files, with spaces in their names?"
date: 2009-11-04
forum: Programming Talk
---

### Post by agnes on 2009-11-04
I want to change a certain expression for another one in ALL my playlist files.

The "change expression" (sed) part works, per file. So I want to loop through all files in a directory.
But the issue is: my playlist files all have spaces in their names and I can not figure out how I should pass their filename to the 'sed'-script.

```

#!/bin/bash

mkdir test2
for file in *.m3u
do

echo "file=$file"

sed 's/..\/..\/..\/..\/media\/wdisk/\/media\/disk/g' $file > test2/$file
done

```

Now, I pass the full name with spaces in it. 
But it doesn't work, because e.g. "Some Name"  needs to be passed as "Some\ Name", to sed. 
(Setting the $file variable in double quotes does also not work.)

(I also tried to circumvent it with ```
file2=sed 's/ /\\ /g' $file
```, trying to alter the filename in the correct to-be-passed-name, but that variable assignment didnt work.)

---

### Post by Arndt on 2009-11-04
> **agnes said:**
> I want to change a certain expression for another one in ALL my playlist files.

The "change expression" (sed) part works, per file. So I want to loop through all files in a directory.
But the issue is: my playlist files all have spaces in their names and I can not figure out how I should pass their filename to the 'sed'-script.

```

#!/bin/bash

mkdir test2
for file in *.m3u
do

echo "file=$file"

sed 's/..\/..\/..\/..\/media\/wdisk/\/media\/disk/g' $file > test2/$file
done

```

Now, I pass the full name with spaces in it. 
But it doesn't work, because e.g. "Some Name"  needs to be passed as "Some\ Name", to sed. 
(Setting the $file variable in double quotes does also not work.)

(I also tried to circumvent it with ```
file2=sed 's/ /\\ /g' $file
```, trying to alter the filename in the correct to-be-passed-name, but that variable assignment didnt work.)

Simply using "$file", i.e., double quotes, ought to work.

---

### Post by Rany Albeg on 2009-11-04
Try this before your code:

save=$IFS
IFS=$'\n'

and before exit signal:

IFS=$save

---

### Post by agnes on 2009-11-04
Ok it was very simple indeed.. 	:rolleyes:
"$file" > test2/"$file"
worked.
Earlier I only did: "$file" > test2/$file, which did not work...

---

### Post by sprouty on 2009-11-04
Maybe:

```

IFS=$'\n'
for filname in `ls -1 ./`
do
changename=`echo $filname | sed 's|[\!\£\$\(\)\ \[\]|\*|g' `

mv ./$changename newdirectory
done
```

Hope this can help

---

