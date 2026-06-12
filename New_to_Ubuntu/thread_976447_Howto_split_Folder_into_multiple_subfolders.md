---
title: "Howto split Folder into multiple subfolders ?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by jon555 on 2008-11-09
I searched forums and found only this answer, could you tell me how to use it or advise some other way.

Code:

let fileCount=1000
let dirNum=1

for f in *
do
  [ -d $f ] && continue
  [ $fileCount -eq 1000 ] && {
      dir=$(printf "%03d", $dirNum)
      mkdir $dir
      let dirNum=$dirNum+1
      let fileCount=0
  }

  mv $f $dir
  let fileCount=$fileCount+1
done

---

### Post by Pro-reason on 2008-11-09
You haven't actually described what your current situation is and what result you wish to achieve.

---

### Post by jon555 on 2008-11-11
> **Pro-reason said:**
> You haven't actually described what your current situation is and what result you wish to achieve.

I have one folder with many small files 300 000 or so, they are so many that i can't move them manually.
I would like to put them in subfolders by 3000 files in one folder. Is there a automated way to do tahat?

---

### Post by Buying_Some_Time on 2011-06-21
bump ~_~

---

### Post by dFlyer on 2011-06-21
> **jon555 said:**
> I searched forums and found only this answer, could you tell me how to use it or advise some other way.

Code:

let fileCount=1000
let dirNum=1

for f in *
do
  [ -d $f ] && continue
  [ $fileCount -eq 1000 ] && {
      dir=$(printf "%03d", $dirNum)
      mkdir $dir
      let dirNum=$dirNum+1
      let fileCount=0
  }

  mv $f $dir
  let fileCount=$fileCount+1
done

If this works at 1000, just change the count to 3000 everywhere 1000 is listed.

---

### Post by Buying_Some_Time on 2011-06-21
How do I know what folder it will split?

---

### Post by nothingspecial on 2011-06-21
It will do it in numerical then alphabetical order, just like if you were to type ls in the directory

You will end up with folders 001, 002, 003, etc etc

Note, they will actually have the comma in the directory name. Personally I would remove the ,

What you want is this

```
let fileCount=3000
let dirNum=1

for f in *
do
[ -d $f ] && continue
[ $fileCount -eq 3000 ] && {
dir=$(printf "%03d" $dirNum)
mkdir $dir
let dirNum=$dirNum+1
let fileCount=0
}

mv $f $dir
let fileCount=$fileCount+1
done 
```

Copy the whole thing.

Open a terminal and navigate to the folder in question.

Hold down Ctrl

While it's held down Press X followed by E (without depressing Ctrl)

Press Ctrl-Shift-V to paste the script

Then press Ctrl-O

Then press Ctrl-X

---

### Post by Buying_Some_Time on 2011-06-21
Thank u so much! It worked!

---

