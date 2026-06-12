---
title: "Bash script to move older files to archive"
date: 2014-05-26
forum: Programming Talk
---

### Post by vikler on 2014-05-26
hi guys! Can you help me to write a following ubuntu bash script:
each time a new day starts I want to make a folder name with yesterday's date in current directory (like, 20140524) and move ALL current files that were created yesterday into 20140524 folder

But since I am going to keep archive folders in the same folder as well, I can't do mv * ./20140524, since it will also move older archive folders like 20140523 etc

So what I basically need:
1) when new date starts make a folder with the name of yesterday's date
2) move all folders from yesterday into yesterday folder name directory.

Thanks in advance!

---

### Post by ofnuts on 2014-05-26
Several options:
[LIST]
[*]if your files have extensions and not your directories, you can use "mv *.*"instead of "mv*" 
[*]if your directories are the only ones to be named after a date, you can use [exclusion matching]("https://www.gnu.org/software/bash/manual/html_node/Pattern-Matching.html#Pattern-Matching"): "mv !(201*) ..." 
[*]you can use "find . -maxdepth 1 -type f -exec mv -t $todaysDir {} \;" to find only the files in the current directory 
[/LIST]

---

### Post by vikler on 2014-05-31
Thanks! 
Can someone else help with actual code? a bit at least

---

### Post by ofnuts on 2014-05-31
With assumption #2 above:

```

yesterdayDir=$(date -d yesterday +%Y%m%d)

mkdir -p $yesterdayDir
mv -t $yesterdayDir !(201*)

```

---

