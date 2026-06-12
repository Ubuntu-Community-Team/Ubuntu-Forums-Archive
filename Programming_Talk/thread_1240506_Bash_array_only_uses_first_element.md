---
title: "Bash array only uses first element"
date: 2009-08-14
forum: Programming Talk
---

### Post by wesg on 2009-08-14
I'm writing a bash script that uses an array to operate on files scattered throughout a folder. I've put all the files in the array, but after going through the for loop, only the first element is ever used. I tried multiple configurations with quotation marks, but none work.

Any suggestions?

```
folders=$(find . -name "*.avi" | sort)
```
My Array

```
for x in "${folders[@]}"; do
```
My loop

---

### Post by lswb on 2009-08-14
wouldn't just 

for x in "${folders}"; do 

work?

---

### Post by wesg on 2009-08-14
That works in that the loop works, but still doesn't use all elements.

---

### Post by kaibob on 2009-08-14
Try the following, which works for me. Perhaps something is wrong elsewhere in the script.

```
#!/bin/bash
folders=$(find . -name "*.avi" | sort)
for x in "${folders}" ; do
echo "$x"
done
```

---

### Post by ghostdog74 on 2009-08-14
```

folders=$(find . -name "*.avi" | sort)

```
the above puts the results of find and sort into an entire string, not array. Am i missing something here?
@OP, unless you are storing your avi files for further processing in later part of your script, otherwise, no need to use arrays. just process them as you find them
```

find ... -name "*.avi" ... | while read FILE
do
   # do something with $FILE variable
done

```

---

### Post by geirha on 2009-08-15
And if you still want them in an array
```

files=()
while IFS= read -d '' -r file; do
   files+=("$file")
done < <(find . -name "*.avi" -print0 | sort -z)

echo "All files:" "${files[@]}"
echo "Second file: ${files[1]}"
echo "First file: ${files[0]}"
echo "First file: $files"      # Yes, this is equivalent to the previous parameter expansion

```

It's important that you put ""-quotes around ${files[@]}. If not it will split on spaces in filenames.

---

### Post by ghostdog74 on 2009-08-15
its also possible to read into array using -a option, eg
```

read -a array <<< $(ls -1)

```

---

