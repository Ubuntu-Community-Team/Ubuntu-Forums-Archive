---
title: "Why can't I use cat in a shell script?"
date: 2008-06-19
forum: Programming Talk
---

### Post by kevdog on 2008-06-19
I want to grep a particular comment or line from within a bunch of files.  For example within a particular directory if I do the following:

# cat * | grep comment

This will find the line(s) containing the Regex comment contained within all the files in the directory.

I can't accomplish this however in a shell script.  In fact the cat command doesn't seem to work will from within a shell script at all.  I think I read somewhere the when used in shell scripts, every word is assigned a variable.  Is there a work around?

---

### Post by Phenax on 2008-06-19
The way you are using cat is [bad form]("http://partmaps.org/era/unix/award.html#cat%5B/url").

This way works, is easier, and eliminates the redundancy and extra process of cat.
```

grep comment *

```Don't want the filename prefix?
```

grep -h comment *

```Or recursively
```

grep -R comment ./dir/

```

---

### Post by LaRoza on 2008-06-19
Works fine over here.
```

~$cat p.sh
#!/bin/bash

cat p.c | grep "main"
~$./p.sh
int main(void)
~$

```

---

### Post by Phenax on 2008-06-19
> **LaRoza said:**
> Works fine over here.
```

~$cat p.sh
#!/bin/bash

cat p.c | grep "main"
~$./p.sh
int main(void)
~$

```

Indeed it does work. Perhaps he is executing the script from another directory hoping to get the content of that directory?

---

### Post by kevdog on 2008-06-19
Here is an example:

```

#!/bin/bash

file=( `ls | tr '\n' ' '` )

echo -e "Size of array: ${#file[@]}\n"
#echo -e "Array: $file\n"

for filename in ${file[@]}
do
   echo -e "Filename: $filename \n"
   **[SIZE=3]filecontent=( `cat $filename` )[/SIZE]**  <---Line doesnt work -- rather than each line being one element in the array, it seems each word on the line is an individual array element.  Do I need like a field separator or something.

   for line in ${filecontent[@]}
   do
      echo $line;
      if [ $line = "comment" ]
      then
          echo $line
      fi
   done
done

echo -e "Done\n"

```


Also I want to grep an array for a value -- I know you can do it in perl, but how about in a shell script?

---

### Post by rikxik on 2008-06-20
Try this:

```

#!/bin/bash

file=( `ls | tr '\n' ' '` )

echo -e "Size of array: ${#file[@]}\n"
#echo -e "Array: $file\n"

for filename in ${file[@]}
do
   echo -e "Filename: $filename \n"
   OIFS=$IFS
   IFS=$(echo "\006")
   filecontent=( `cat $filename` )

   for line in ${filecontent[@]}
   do
      echo $line;
      if [ $line = "comment" ]
      then
          echo $line
      fi
   done
   IFS=$OIFS
done

echo -e "Done\n"

```

Output:

```

Size of array: 2

Filename: a.txt

line 1 from a.txt
line 2 from a.txt
Filename: b.txt

line 1 from b.txt
line 2 from b.txt
Done

```


HTH

---

### Post by ghostdog74 on 2008-06-20
> **kevdog said:**
> Here is an example:

```

#!/bin/bash

file=( `ls | tr '\n' ' '` )

echo -e "Size of array: ${#file[@]}\n"
#echo -e "Array: $file\n"

for filename in ${file[@]}
do
   echo -e "Filename: $filename \n"
   **[SIZE=3]filecontent=( `cat $filename` )[/SIZE]**  <---Line doesnt work -- rather than each line being one element in the array, it seems each word on the line is an individual array element.  Do I need like a field separator or something.

   for line in ${filecontent[@]}
   do
      echo $line;
      if [ $line = "comment" ]
      then
          echo $line
      fi
   done
done

echo -e "Done\n"

```


Also I want to grep an array for a value -- I know you can do it in perl, but how about in a shell script?

let's leave arrays aside for a while. what you are doing above is long winded and uncommon way to parse a file. It can essentially be done using grep/awk as described by Phenax

---

### Post by kevdog on 2008-06-20
Yes I see that is a much more efficient way of doing things.  So much to learn.

---

