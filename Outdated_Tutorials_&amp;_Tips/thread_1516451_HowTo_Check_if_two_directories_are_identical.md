---
title: "HowTo: Check if two directories are identical"
date: 2010-06-23
forum: Outdated Tutorials &amp; Tips
---

### Post by paulmilliken on 2010-06-23
To check if two directories have identical contents, do the following:

From within both directories, do (with a different filename each time):

```
md5deep -r -l . > /path/to/outputFile.txt
```

Then sort these text files alphabetically based on the filename which is the second string in each line:

```
sort -k 2 -o /path/to/sortedOutputFile.txt /path/to/outputFile.txt
```'

Then check for differences between the two alphabetically-sorted text files (one for each directory):

```
diff /path/to/sortedOutputFile1.txt /path/to/sortedOutputFile2.txt
```

Note that if you do not sort the files into alphabetical order, the two files may be different when the contents of the directories are actually identical.

---

