---
title: "Shell programming"
date: 2010-08-14
forum: Programming Talk
---

### Post by kranthikiran on 2010-08-14
[COLOR=Red]Using shell scripting, implement ‘scan.sh’ that scans the file system recursively starting
from current working directory and generates the file ‘index.txt’ that contains a line for each
file (or directory) with following fields in tab separated format:
1. The full path of the directory containing the file (or the directory). 
2. The file (or directory) name
3. The last modified date and time.
4. ‘d/f’ field which is ‘d’ if the file is a directory and ‘f’ otherwise.
[/COLOR] 
I have used ls -lR command and piped the output to index.txt but this  output shows the read write permissions of files and directories which i  dont want . only the above mentioned four fields are required 

PLEASE HELP ME


THANKS IN ADVANCE  !!!!!

---

### Post by limestone on 2010-08-14
Duplicate: [http://ubuntuforums.org/showthread.php?t=1552835](http://ubuntuforums.org/showthread.php?t=1552835)

---

