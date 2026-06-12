---
title: "Checking for Duplicate Files in a Directory Tree"
date: 2014-10-18
forum: Programming Talk
---

### Post by fobos3 on 2014-10-18
Hi,

I've just modified this from an old command I found and was thinking it would be useful to somebody else:
```
find -not -empty -type f -printf "%-30s'\t\"%h/%f\"\n" | sort -rn -t$'\t' | uniq -w30 -D | cut -f 2 -d $'\t' | xargs md5sum | sort | uniq -w32 --all-repeated=separate
```

[LIST=1]
[*]It creates a table of size<tab>filepath for all files in the tree
[*]Sorts by file size
[*]Removes files with unique file sizes (they will not be duplicates)
[*]Cuts the size and keeps the name
[*]Calculates the md5sum
[*]Sorts by md5sum
[*]Outputs the unique files
[/LIST]

Take around 3s for 63117 files totaling 40.3GB. You only need to calculate the md5sum on files with the same size.

Regards

---

### Post by TheFu on 2014-10-18
Nice.  Good exercise.  /. had a question about this a few years ago and I built a perl solution - very similar to this method.  Turns out there are a few F/LOSS programs in python, perl and C for this that are maintained and very fast.  Plus htey have added features like using hard or sym-links to merge storage, but not relocate the files.

[https://en.wikipedia.org/wiki/List_of_duplicate_file_finders](https://en.wikipedia.org/wiki/List_of_duplicate_file_finders)
* fslint
* fdupes
* lots of others shown there.

The 3s for processing seems low.  Depends on the CPU and mainly storage subsystem performance.

---

### Post by ofnuts on 2014-10-20
> **TheFu said:**
> Nice.  Good exercise.  /. had a question about this a few years ago and I built a perl solution - very similar to this method.  Turns out there are a few F/LOSS programs in python, perl and C for this that are maintained and very fast.  Plus htey have added features like using hard or sym-links to merge storage, but not relocate the files.

[https://en.wikipedia.org/wiki/List_of_duplicate_file_finders](https://en.wikipedia.org/wiki/List_of_duplicate_file_finders)
* fslint
* fdupes
* lots of others shown there.

The 3s for processing seems low.  Depends on the CPU and mainly storage subsystem performance.

File size "clashes" are more likely to occur with small sizes, so you end up computing md5sum mostly on small files.

---

