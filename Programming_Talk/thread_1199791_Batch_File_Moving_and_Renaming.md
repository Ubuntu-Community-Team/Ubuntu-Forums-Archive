---
title: "Batch File Moving and Renaming"
date: 2009-06-29
forum: Programming Talk
---

### Post by Holmes89 on 2009-06-29
I want to make a program that will access an "Incoming Files" folder and add the files to a website but I'm a little hung up on how I should access the files to move it. For example say I have a list of documents like vacation.jpg, house.jpg, and beach.jpg and I want to keep the original file names.... how would I keep the names yet still be able to reference them in a program.... it may sound confusing, in fact I'm confusing myself so any help would be appreciated. (I know a little Perl and bash scripting).

---

### Post by Holmes89 on 2009-06-29
I guess one of the things I'm kind of confused about is how to use *, if I do *.jpg is there a way to store one file at a time or have multiple variables associated with it to store each one and then work through the variable(s) with a loop?

---

### Post by geirha on 2009-06-29
```

for file in *.jpg; do
    echo "Processing $file"
done

```

---

### Post by Holmes89 on 2009-06-29
But how do I store the individual file names like if I wanted to add them to html code?

---

### Post by Holmes89 on 2009-06-29
figured it out how to do it in perl```

#!/usr/bin/perl -w
opendir(DIR, './html/assets/');
@files = grep(/\.jpg$/,readdir(DIR));
closedir(DIR);
foreach $file (@files) {
print "$file \n";
}
```

---

### Post by geirha on 2009-06-29
The bash equivalent of that would be
```
#!/bin/bash

cd html/assets/
files=( *.jpg )
for file in "${files[@]}"; do
    echo "$file"
done

echo "Number of files: ${#files[@]}"
echo "First file: ${files[0]}"

```

---

