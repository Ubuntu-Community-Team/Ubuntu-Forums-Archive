---
title: "Batch renaming files"
date: 2010-04-20
forum: Programming Talk
---

### Post by Cyked on 2010-04-20
I've been looking around on here and google and not finding what I specifically need.  I want to rename completely random files in a single directory to be sequentially numbered started at 1.
i.e. 1.jpg, 2.jpg, 3.jpg.....  

I get and can rename file ext. using 
```
rename -v 's/\.jpeg/\.jpg/' *.jpeg
```

but how do you fully name the entire file name via command line/putty. 

If there are 500 files does the first file have to be 001 because I need to specify the length of the file?

---

### Post by aysiu on 2010-04-20
Does it have to be via command line? There are some great graphical batch-rename tools out there... KRename, for example.

---

### Post by Cyked on 2010-04-20
> **aysiu said:**
> Does it have to be via command line? There are some great graphical batch-rename tools out there... KRename, for example.

I hardly ever sit at the computer, so I'm almost always just in on putty.  I could set up VNC, I just prefer command line most of the time.

---

### Post by geirha on 2010-04-20
A simple shell loop should suffice.

```

i=1
for file in ./*.jpg; do
    mv -vi "$file" "$((i++)).jpg"
done

```

If you want the files to be sorted by that number though, you'll need leading zeros so all filenames are the same length.

```

i=1
for file in ./*.jpg; do
  newname=$(printf "%03d.jpg" $i)
  mv -iv "$file" "$newname"
  : $((i++))
done

```

If you need the numbers to be longer than 3 digits, change the 3 in %03d to a different number.

---

### Post by sisco311 on 2010-04-20
EDIT:

The length of the new filenames is the length of the number of files:

```

#!/bin/bash

nr="$(ls -1 *.jpg | wc -l)"
i=0

for file in *.jpg; do
    ((i++))
    mv -b "$file" $(printf "%0${#nr}d" $i).jpg
done

```

---

### Post by geirha on 2010-04-20
That's also a nice way to do it, though ```
nr="$(ls -1 *.jpg | wc -l)"
``` can be done a little better. Filenames can contain newlines, so that code can potentially give the wrong number of files. It's safer to use bash to count them, and you'll also avoid the overhead of three subshells.
```
files=(./*.jpg) nr=${#files[@]}
```

And then you of course reuse the files array in the for-loop
```
for file in "${files[@]}"; do
```

---

### Post by Cyked on 2010-04-26
What am I doing wrong here?  Here is root crontab.

```
# m h  dom mon dow   command
13 22 * * 7 /var/www/pics/rename.sh
15 22 * * 6 /etc/scripts/wwwchmod.sh
15 22 * * 6 /etc/scripts/wwwchown.sh
15 22 * * 6 /etc/scripts/weatcache.sh
```

The rename.sh will not run for cron no matter the time I set it to run.  If I go into the /var/www/scripts dir and do sudo ./rename.sh it works fine.  The rename.sh file is in the folder where the files to be renamed is.

The other the scripts in /etc/scripts run perfectly fine as a job.


Thoughts?

here is the code for the rename.sh
```
#!/bin/bash
i=1
for file in ./*.jpg; do
  newname=$(printf "%04d.jpg" $i)
  mv -iv "$file" "$newname"
  : $((i++))
done

```

---

### Post by geirha on 2010-04-26
You never change directory in the script, so that script will typically run in /, trying to rename files there.

```

#!/bin/bash
cd "/path/to/rename/files/in" || exit
i=1
for file in ./*.jpg; do
[snipp]

```

---

### Post by Cyked on 2010-04-26
> **geirha said:**
> You never change directory in the script, so that script will typically run in /, trying to rename files there.

```

#!/bin/bash
cd "/path/to/rename/files/in" || exit
i=1
for file in ./*.jpg; do
[snipp]

```

Awesome, thanks!

---

### Post by Cyked on 2011-02-14
Not sure why I never marked this as resolved...  

```
#!/bin/bash
cd "/mnt/drives/files" || exit
i=1
for file in ./*.jpg; do
  newname=$(printf "%05d.jpg" $i)
  mv -iv "$file" "$newname"
  : $((i++))
done

```

Is there a way to get this to run against all sub-directories of, in this case, "files"?

---

### Post by geirha on 2011-02-15
Assuming you have bash4, you could do:
```
#!/bin/bash
shopt -s globstar

i=1
for file in /mnt/drives/files/**/*.jpg; do
  dirname=${file%/*}
  mv "$file" "$dirname/$(printf %05d.jpg "$i")"
  ((i++))
done

```

See [http://mywiki.wooledge.org/BashFAQ/030](http://mywiki.wooledge.org/BashFAQ/030) for more options.

---

### Post by sisco311 on 2011-02-15
You need to enable nullglob too, to handle the case when no matches are found.

---

### Post by Cyked on 2011-02-15
Thanks.  Going to look around a bit more and see what I can figure out on my own... If there are 10 files in each directory it recursively renames all files in ALL subfolders sequentional so intead of 1-10 in one directory and 1-10 in all the others it does 1-10 in one directory, 11-20 in the next directory, etc.

---

### Post by geirha on 2011-02-15
Ah, in that case, using find would be a possible solution. [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind) takes you through the hoops. GNU find (which your ubuntu has), has -execdir + which would be useful for this case.

---

