---
title: "Deleting all files containing ~"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by henchman on 2008-07-14
hi :)

iam using gedit to program in php and i have a problem to delete the temporary files ( all named foo~ for a file called foo ), which gedit creates.

now i want to delete these files before uploading the directory structure up to an ftp server...

eg: if i enter 

```
rm .htaccess~
```

it works, but neither of these will work

```
1. rm *~
2. rm *\~
3. rm "*~"
4. rm "*\~"
```

i tried escaping the ~ as it stands for the home directory and putting it in quotes... all of these attemts returned 

```
rm: cannot remove `*~': No such file or directory
```

how can i delete all these files in all subfolders of the current folder? or even at first: only the files in the current folder?

i know i can delete recusively with -R...

thank you very much :) :popcorn:

---

### Post by kpkeerthi on 2008-07-14
To print all the file names ending with ~ in a folder & its subfolder, run this command
```
find /path/to/folder -iname "*~"
```

And when you are sure with the result, run this command
```
find /path/to/folder -iname "*~" -exec rm '{}' ';'
```

---

### Post by hyper_ch on 2008-07-14
I'd first
```

locate ~ > ~/Desktop/output.txt

```

then look at it and eventually remove some files that I wanted to keep

and finally run a shell script that deletes them like
```

#!/bin/bash

for file in /home/USER/Desktop/output.txt; do
    rm $file
done

```

and run that bash script as root

---

