---
title: "Help with bash script"
date: 2010-12-05
forum: Programming Talk
---

### Post by pmorton on 2010-12-05
Could someone please help me out with this. I have a text file containing a list of files with their full paths. In the final directory of each of these paths is a jpeg file I want to gather together in a separate directory. The problem I have is that I can't get my glob to expand; it's treated literally, and no jpeg files are found. I tried the extglob option, but it looks like I'm barking up the wrong tree with that. 


```
#!/bin/bash
shopt -s extglob
while read line
do
   cp  "$(dirname $line)/*.jpeg"  ./jpglist.txt
done < ./filelist.txt
```

---

### Post by papibe on 2010-12-06
If you left the * out of the quotes you don't need the exglob option:
```
cp  "$(dirname $line)"/*.jpeg  ./jpglist.txt
```

BTW, unless jpglis.txt is a directory, you are just coping all jpeg to the same file, and you'll end up with a copy of the last one. I would recomend using a different directory name. For example
```
$ mkdir jpegsdir
```
and then change the line for:
```
 cp  "$(dirname $line)"/*.jpeg  ./jpegsdir
```

Now, if you want to create a file with the list of the jpegs file, you may accomplish that with some similar to this:
```
  echo  "$(dirname $line)"/*.jpeg >> ./jpglist.txt  
```

I hope it helps.

---

### Post by pmorton on 2010-12-06
Thanks for the reply, papibe. I've altered the code to:

```
#!/bin/bash

while read line
do
   cp  "$(dirname $line)"/*.jpeg  ./MyJpegDir/

done < ./filelist.txt
```

but the glob still won't expand. I get the (multiple) error message:

*cp: cannot stat `./topdir/nextdir/bottomdir/*.jpeg': No such file or directory*

The jpgeg files, in case it's relevant, are hidden, so a typical file might look like:

./topdir/nextdir/bottomdir/.TypicalJpegFile.jpeg

Any further thoughts?

---

### Post by DaithiF on 2010-12-06
looks ok to me ... are there some directories which don't contain jpegs?  if so that would give rise to an error.

i would do it differently:

```
#!/bin/bash
shopt -s nullglob
while read line
do
   dir=${line%/*}
   for file in ${dir}/*.jpg
   do
      cp  "${dir}/$file"  ./MyJpegDir/
   done
done <./filelist.txt 
```

---

### Post by pmorton on 2010-12-06
If I adapt DaithiF's suggestion a bit to:

```
#!/bin/bash
shopt -s dotglob nullglob
while read line
do
    dir=${line%/*}
    cp   ${dir}/*.jpeg  ./MyJpegDir/

done < ./filelist.txt
```

it works. The nullglob I note stops any globs that won't expand  being treated literally. The dotglob allows the glob to pick up the dot at the start of the file name. (dotglob:if set, Bash includes filenames beginning with a `.' in the results of filename expansion.)

So that's solved. The only slight niggle is that, while all the jpegs are now copied, I get the (single)error message:

*cp: missing destination file operand after `.MyJpegDir/'*

Which doesn't seem to make any difference to a satisfactory result. Curious.

---

### Post by DaithiF on 2010-12-06
> **pmorton said:**
> So that's solved. The only slight niggle is that, while all the jpegs are now copied, I get the (single)error message:

*cp: missing destination file operand after `.MyJpegDir/'*

Which doesn't seem to make any difference to a satisfactory result. Curious.

The reason for the error message is also the reason I used an inner for loop rather than the direct cp *.jpg command that you have replaced it with.  One of your directories doesn't have a jpg file.  For that directory your cp line:
```
cp ${dir}/*.jpeg  ./MyJpegDir/

```gets expanded to:
```
cp ./MyJpegDir/

```see the problem?  

This isn't any better than what happens when nullglob isn't set.  In that case the cp line gets expanded to:
cp somedir/*.jpeg ./MyJpegDir/

and since there are no *.jpeg files in that directory you also get an error.

so to cut a long story short, using the inner for loop with the nullglob option set should have the right behaviour ... copy jpg files when they exist and not report an error when they don't.

---

### Post by pmorton on 2010-12-12
Thank you, DaithiF, for that comprehensive explanation. The subtleties of Bash never fail to amaze!
Regards.

---

