---
title: "Bash: Spaces in filenames get broken in array"
date: 2009-03-17
forum: Programming Talk
---

### Post by phenest on 2009-03-17
```
files=(`find $FOLDER | grep -i "\.jpg$\|\.gif$\|\.png$\|\.bmp$"`)
```

I'm using this line in a bash script to fill an array with file names. But the file names are getting broken up if there is a space in it, i.e

File names:[INDENT]file name.jpg[/INDENT]
[INDENT]another.bmp[/INDENT]
[INDENT]here is another.gif[/INDENT]
Array:[INDENT]files[0]=file[/INDENT]
[INDENT]files[1]=name.jpg[/INDENT]
[INDENT]files[2]=another.bmp[/INDENT]
[INDENT]files[3]=here[/INDENT]
[INDENT]files[4]=is[/INDENT]
[INDENT]files[5]=another.gif[/INDENT]

How can I prevent this?

---

### Post by sisco311 on 2009-03-17
```
IFS=$'\t\n'
files=(`find $FOLDER | grep -i "\.jpg$\|\.gif$\|\.png$\|\.bmp$"`)
unset $IFS #or IFS=$' \t\n'
```

set the IFS (Internal Field Separator) variable so that it splits fields by tab and newline and don't threat space as a filed separator.



this should be faster:
```
IFS=$'\t\n'
files=($(find $FOLDER -iname "*.jpg" -o -iname "*.gif" -o -iname ".png" -o -iname "*.bmp"))
unset $IFS #or IFS=$' \t\n'
```;)

---

### Post by ghostdog74 on 2009-03-17
no need to mess around with internal IFS. use a while read loop. Anyway, why do you need to put into arrays? Unless you are using your results later in your script, otherwise, just pipe your results to a while read loop for immediate processing. Also, there's no need to use grep. find can find specific file names
```

# find "$FOLDER" \( -name "*.jpg -o -name "*.png" \) -print | while read FILE
do
 # do something with $FILE
done 

```

---

### Post by phenest on 2009-03-17
Thanks guys. Both solutions are very useful but the array is necessary in other scripts where I need to refer to it later.

---

