---
title: "bash help: mv this not that"
date: 2009-06-17
forum: Programming Talk
---

### Post by soulbazz on 2009-06-17
Hey all, I'm a long time reader but a new member and had a question that I couldn't find an answer to online.

Here is the problem,

I have a list of file names I want to use in a .txt file 

example: 
foo1.ascii
foo2.ascii
foo3.ascii


and I have a directory containing hundreds of similar files (including those in the list), 

example:
TEST/foo*.ascii   

I want to move every file NOT in my list.txt to another directory.

so basically something like 

mv TEST/!foo[123].ascii NEWDIRECTORY/ 

I hope this post isn't too confusing, as I said this is my first time posting here :D. Thanks in advance for your help!!

ps I would like to use bash for this because that is what the rest of my code is in

cheers,
b

---

### Post by soltanis on 2009-06-17
```

cd TEST
mkdir tmp/
cat list.txt | xargs -n 1 -I _ mv _ tmp/
mv * NEWDIRECTORY/
mv tmp/* ./
rm -r tmp/

```

In short,

move all the files you don't want moved into a temp directory, move the rest, then move the other files back and delete the temp. There is probably a more elegant solution, but this gets it done.

---

### Post by unutbu on 2009-06-17
Put this in exclude.txt: 
```

foo1.ascii
foo2.ascii
foo3.ascii

```


Then run```

rsync -a --exclude-from="exclude.txt" TEST/ NEWDIRECTORY/
```

---

### Post by ghostdog74 on 2009-06-17
assume no directory name with foo*
```

ls -1 file*| awk 'BEGIN{
 while(( getline l < "list_of_exclude_files.txt")>0){  a[l]  }
 q="\047"
 dest="/destination"
}
(! ($0 in a ) ){
  cmd="mv "q $0 q" "dest
  print cmd
  # system(cmd) #uncomment to use
}' 

```

---

### Post by kaibob on 2009-06-17
I'm trying to learn shell scripting and enjoy threads such as this because they give me a chance to practice. I had trouble with this one but came up with the following:

```
#!/bin/bash

cd /source/directory

IFS=$'\n'

for DIRFILE in *.ascii ; do
   MATCH=0
   for LISTFILE in $(<filelist) ; do
      [ "$DIRFILE" = "$LISTFILE" ] && MATCH=1
   done
   [ $MATCH = 0 ] && cp "$DIRFILE" /target/directory
done
```

I tested this script and it does seem to work, including with files that contain spaces. The script assumes that the text file is named filelist and is in the source directory. Also, I used cp rather than mv as a precaution, and, in practice, IFS probably should be reset at the end of the script. 

My script seems a bit convoluted for a simple task, so I'll look forward to other solutions.

---

### Post by ghostdog74 on 2009-06-17
> **kaibob said:**
> I'm trying to learn shell scripting and enjoy threads such as this because they give me a chance to practice. I had trouble with this one but came up with the following:

```
#!/bin/bash

cd /source/directory

IFS=$'\n'

for DIRFILE in *.ascii ; do
   MATCH=0
   for LISTFILE in $(<filelist) ; do
      [ "$DIRFILE" = "$LISTFILE" ] && MATCH=1
   done
   [ $MATCH = 0 ] && cp "$DIRFILE" /target/directory
done
```

I tested this script and it does seem to work, including with files that contain spaces. The script assumes that the text file is named filelist and is in the source directory. Also, I used cp rather than mv as a precaution.

My script seems a bit convoluted for a simple task, so I'll look forward to other solutions.
if you have 1000 ascii files, you will be reading LISTFILE 1000 times... put the contents of LISTFILE in memory (eg arrays). then you only need to check each ascii file against items in memory.

---

### Post by kaibob on 2009-06-17
> **ghostdog74 said:**
> if you have 1000 ascii files, you will be reading LISTFILE 1000 times... put the contents of LISTFILE in memory (eg arrays). then you only need to check each ascii file against items in memory.

Thanks for the response ghostdog74. I can understand how an array would be much more efficient; unfortunately, I haven't learned arrays yet, although it is on my list of things to master. 

A while back, I wrote a script where I had a list of items (pages in a PDF actually), and I then had to remove certain pages from the list. I didn't have the knowledge to do this, but Geirha was kind enough to respond to my post with a few lines of code utilizing an array with the unset command. Similarly, creating an array that contains all files in the source directory and then removing those files contained in the text file would seem to be a very efficient approach.

---

### Post by ghostdog74 on 2009-06-17
bash supports arrays. go to the chapter on arrays in Advance bash guide (see my sig) to learn more. personally, i don't use bash arrays as they are awkward/unfriendly to use. i would suggest you get more knowledge on awk instead.

---

### Post by slakkie on 2009-06-17
> **ghostdog74 said:**
> bash supports arrays. go to the chapter on arrays in Advance bash guide (see my sig) to learn more. personally, i don't use bash arrays as they are awkward/unfriendly to use. i would suggest you get more knowledge on awk instead.

I find them to be very useful, but then again, my awk knowledge is limited..

---

### Post by slakkie on 2009-06-17
> **soltanis said:**
> ```

cd TEST
mkdir tmp/
cat list.txt | xargs -n 1 -I _ mv _ tmp/
mv * NEWDIRECTORY/
mv tmp/* ./
rm -r tmp/

```

In short,

move all the files you don't want moved into a temp directory, move the rest, then move the other files back and delete the temp. There is probably a more elegant solution, but this gets it done.

That cat list.txt | xargs can be rewritten to: mv $(cat list.txt) $dest_dir

I would do it like this I guess:

```

egrep_pattern() {
    local FILE=$1
    REGEXP=""

    for i in $(cat $FILE); do
        if [ -z "$REGEXP" ] ; then
                REGEXP=$i
        else
                REGEXP="$i|$REGEXP"
        fi
    done
}

mv_exclude() {
    local exclude_file=$1
    shift;
    local src_dir=$1
    local dst_dir=$2
    egrep_pattern $exclude_file
    cd $src_dir
    # remove echo if you want to execute this
    echo mv $(ls -1 | egrep -wv "$REGEXP") $dst_dir
    cd -
}

mv_exclude $@

```

Some extra checks need to be in here to check if directories exists before moving. And if you want to work with relative paths you might need to move the mv command into a for-loop.

---

### Post by kaibob on 2009-06-18
> **ghostdog74 said:**
> bash supports arrays. go to the chapter on arrays in Advance bash guide (see my sig) to learn more.

Loading the files listed in the text file into memory with an array seems pretty straightforward. My revised script, which appears to work, is as follows:

```
#!/bin/bash

cd /source/directory

IFS=$'\n'

LISTFILES=( $(<filelist) )

for DIRFILE in *.ascii ; do
   MATCH=0
   for LISTFILE in ${LISTFILES[@]} ; do
      [ "$DIRFILE" = "$LISTFILE" ] && MATCH=1
   done
   [ $MATCH = 0 ] && cp "$DIRFILE" /target/directory
done
```

---

### Post by ghostdog74 on 2009-06-18
> **slakkie said:**
> That cat list.txt | xargs can be rewritten to: mv $(cat list.txt) $dest_dir

won't work if file names have spaces...

---

### Post by soulbazz on 2009-06-18
wow, thank you all for the replies!

It looks like I have allot of options to try out! :D

---

### Post by soulbazz on 2009-06-18
I ended up using a script most like Soltanis's suggestion but added the mv suggestion from Slakkie...it seemed the easiest to understand for my limited knowledge

For whatever reason I couldn't get the rsync command to work, I don't recall the error now and don't have the time to fool around trying it again


Also 'getline' didn't work 
bash: getline: command not found
   edit: nevermind I used it wrong

Again thank you all for the suggestions, they were all really helpful. Once I have some time I'll try to fool around with the others and get them to work too

---

### Post by kaibob on 2009-06-18
I don't mean to hijack this thread, but the OP has resolved his issue, so hopefully he won't mind.

I created two arrays. One contains the files listed in files.txt; the other contains all files in the current directory.

```
LISTFILES=( $(<files.txt) )

DIRFILES=( $(ls) )
```

As noted earlier, the text file lists some but not all of the files contained in the current directory. So, I want to remove or unset all of the array items in DIRFILES that are present in LISTFILES. I researched this a bit and apparently a for loop is the method utilized to unset array items, but that's where I get stuck. 

I guess the code would be something like:

```
for FILE in "${LISTFILES[@]}"; do
unset DIRFILES[???]      
done
```

Is it possible to do what I want, and if so how is this done?

Thanks.

kaibob

---

### Post by soulbazz on 2009-06-19
kaibob- hijack away, I would also be interested in learning how to do that

---

### Post by stroyan on 2009-06-19
kaibob-
Don't use ls to list files for assignment.
That will break up file names that include spaces or tabs.
You can just use "DIRFILES=(*)".
(That will list files in directory order rather than alphabetical sorting.)

Your setting of LISTFILES will also have trouble with lines containing spaces.
You need to temporarily change the value of IFS to just a newline.
That way each line of the file will become one array element.

To unset the DIRFILES entries that match LISTFILES you will need to loop through every index of DIRFILES using "${!DIRFILES[@]}".
You then unset the matching entries by index.
Here is an example-
```

#!/bin/bash
DIRFILES=(*)
OIFS="$IFS"
IFS=$'\n'
LISTFILES=( $(<files.txt) )
IFS="$OIFS"
for i in ${!DIRFILES[@]}
do
 for f in "${LISTFILES[@]}"
 do
 if [ "${DIRFILES[$i]}" == "$f" ]
 then
  unset DIRFILES[$i]
 fi
 done
done
for f in "${DIRFILES[@]}"
do
 echo "$f"
done

```

The recently released bash 4.0 has new features that could be applied to this task.
(Bash 4.0 has not yet been included in an ubuntu release.)
The "mapfile" builtin will read a file into an array with one line.
The "associative array" feature will allow you to use strings for array indices.
The DIRFILES array could be created as an array indexed by file names.
Then the unset operation would work without an explicit loop.
Here is an example-
```

#!/usr/local/bin/bash
typeset -A DIRFILES
for f in *
do
 DIRFILES["$f"]=1
done
mapfile -t LISTFILES <files.txt
for f in "${LISTFILES[@]}"
do
 unset DIRFILES["$f"]
done
for f in "${!DIRFILES[@]}"
do
 echo "$f"
done

```

---

### Post by kaibob on 2009-06-19
stroyan

Thank you for the reply and the script, which worked great (after a momentary user glitch). The most important part--which I would have never gotten--is ${!DIRFILES[@]}. I also appreciate the other advice--such as (*) rather than ( $(ls) ). 

The new array features of Bash 4 sound like they will be most helpful. I'm just learning Bash arrays, so the new features are a bit over my head right now, but hopefully I will have a better understanding by the time Bash 4 arrives in Ubuntu.

Thanks again for the help and the most thorough explanation.

kaibob

---

