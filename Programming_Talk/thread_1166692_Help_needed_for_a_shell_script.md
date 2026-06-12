---
title: "Help needed for a shell script"
date: 2009-05-22
forum: Programming Talk
---

### Post by ivikas on 2009-05-22
Dear all,

        I have only fair idea of shell script.i have a directory containing n number of zip archive files.All i have to create a shell script that will unzip all files and move to a predetermined target directory.

Suppose i have a file foo.zip,i should get the unarchive file as foo and not the content of foo directory.I tried the unzip file option but it only extracts the content of foo directory without creating foo.

foo.zip ----> extracts as content say 1,2,3.

it should be foo->1,2,3


Any help will be highly appreciated.

---

### Post by k2t0f12d on 2009-05-22
```
#!/bin/bash

## USAGE: unzip.sh <pathto/filename>
#
#       pathto          filesystem path to file to be unzipped
#       filename        name of the file to unzip, eg. myfile.zip
#
## END USAGE

# NOTE: this script is only effective on files ending in ".zip"

MY_ZIPS=/home/${USER}/zip
filename="$1"
zipdir="${MY_ZIPS}/$( basename $filename .zip )"

mkdir -pv $zipdir
cd $zipdir
unzip -d $zipdir $filename

test "$?" = "0" && exit 0 || exit 1
```

Merry Christmas

---

### Post by KyleBrandt on 2009-05-22
```

for zipfile in *.zip; do 
   dir="${zipfile%%.zip}"
   mkdir "$dir"
   unzip "$zipfile" -d "$dir" 
done

```

---

### Post by amac777 on 2009-05-22
Since this looks like a competition, how about this:

```
for i in *.zip
do
  unzip $i -d `basename $i .zip`
done

```

---

### Post by KyleBrandt on 2009-05-22
> **amac777 said:**
> Since this looks like a competition, how about this:

```
for i in *.zip
do
  unzip $i -d `basename $i .zip`
done

```

This will break if any of the files have spaces in their names. For example:

```

touch 'foo arf.zip' 
for i in *.zip; do echo unzip $i -d $(basename $i .zip); done
basename: extra operand `.zip'

```

Also, to nit-pick :-) basename would be probably less efficient because it has to call an executable instead of a shell built-in:

```
type basename
basename is /usr/bin/basename
```

---

### Post by amac777 on 2009-05-22
Ahh, I see. Good point. Ok, I my new answer is this:

```
for i in *.zip
do
  unzip "$i" -d "`basename "$i" .zip`"
done

```

Double quotes around all variables to preserve the spaces... So even more ugly. 

When I first saw this question I thought there would be a one line solution without even a loop. But after playing around trying to figure it out, it seems that without some kind of regular expression pattern capturing in bash it's kind of difficult to get it done in one line.

---

### Post by k2t0f12d on 2009-05-22
```
#!/bin/bash

## FILE unzip.sh [version 2]
#
# switched frm basename to stringops to format filenames instead
#

## USAGE: unzip.sh <pathto/filename>
#
#       pathto          filesystem path to file to be unzipped
#       filename        name of the file to unzip, eg. myfile.zip
#
## END USAGE

# NOTE: this script is only effective on files ending in ".zip"

MY_ZIPS=/home/${USER}/zip
filename="$1"
zipdir="${MY_ZIPS}/${filename%%.zip}"

mkdir -pv $zipdir
cd $zipdir
unzip -d $zipdir $filename

test "$?" = "0" && exit 0 || exit 1

#
## END FILE unzip.sh [version 2]
```

---

### Post by ivikas on 2009-05-23
Thanks! guys for all your Great Response.I did be very happy if you could suggest me some link to study bash shell scripts and/or any link to  daily used shell script.

Thank you

---

