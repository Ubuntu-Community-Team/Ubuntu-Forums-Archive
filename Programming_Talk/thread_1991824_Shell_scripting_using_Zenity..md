---
title: "Shell scripting using Zenity."
date: 2012-05-31
forum: Programming Talk
---

### Post by melrokz on 2012-05-31
Zenity is a great idea for GUI prompts in shell scripts. But it can also be used as a progress bar. No idea how. Please correct my script at:

[http://paste.ubuntu.com/1015968/](http://paste.ubuntu.com/1015968/)

I must admit it's very silly ;)

1. Line 4 has an error. What I meant is *.jpg and *.png. Please advise.
2. Zenity does not display anything. 
3. Why the ( and ) in line 4 and 9?
4. Please explain how the progress bar is generated.
5. How do I get files in the format 001.jpg, 002.jpg etc.

Greatly appreciate your help,
Melvin C V.

---

### Post by hakermania on 2012-05-31
You just needed to understand a bit how zenity works. Well, everything inside the brackets ( ) is being watched by zenity. Every number you echo there within 0-100 zenity takes it as percentage and updates its progressbar. Here's your fully working code:
```

#!/bin/bash
if [[ "$1" == "" ]]; then
   echo "Please specify a directory"
   exit
else
   if ! [ -d "$1" ]; then
      echo "directory $1 does not exist"
      exit
   fi
fi
cd $1
#getting the count of the images that have to be renamed
#assuming no hidden files are being renamed
image_count=$(ls | grep -e ".jpg" -e ".png" | wc -l)
echo "$image_count files are going to be modified"
count_now=0;
i=1;
(for file in *.jpg *.png; do
   # Code that processes files
   mv "$file" "$i.$file" 2> /dev/null
   let count_now=count_now+1
   let i=i+1;
   #calculating percentage
   percent=$(echo "scale=2; $count_now*100/$image_count" | bc)
   echo "$percent"
done) | zenity --progress --auto-close --title="Renaming Files"  \
               --text="Processing files ..."  --percentage=0

```Example usage:
[IMG]http://i.imgur.com/lAcGM.png[/IMG]

---

### Post by melrokz on 2012-05-31
Thanks. What does this command do?

```
echo "scale=2; $count_now*100/$image_count" | bc
```

---

### Post by melrokz on 2012-05-31
Zenity needs to be more intelligent than using any echoed variable as the percentage, lol

---

### Post by melrokz on 2012-05-31
Can't we simplify the code? :) Like that one below. Is that right?

at line 24:

```
percent=$((($count_now * 100) / $image_count))
```

---

### Post by hakermania on 2012-05-31
> **melrokz said:**
> Thanks. What does this command do?

```
echo "scale=2; $count_now*100/$image_count" | bc
```

It calculates the percentage. It divides the count_now with the number of all the images. This will result in something like '0.23'. Then it multiplies it by 100 and it becomes '23'. Then, this is being echoed for zenity to get.

```
scale=2;
``` means that all I need is 2 decimal points, no more. For example, if the division is 7/22, just let it 0.31 and no 0.318181818

> **melrokz said:**
> Zenity needs to be more intelligent than using any echoed variable as the percentage, lol
I find it pretty awesome and handy, actually.

> **melrokz said:**
> Can't we simplify the code? :) Like that one below. Is that right?

at line 24:

```
percent=$((($count_now * 100) / $image_count))
```

I don't think that it is right. I now that 'bc' does the work.

Code looks simple to me :D

---

### Post by melrokz on 2012-05-31
Thanks for your help, I really appreciate it :) I hope this is the right place for more shell scripting doubts :)

---

### Post by hakermania on 2012-05-31
Programming Talk is the right place for such discussions!

---

### Post by markbl on 2012-05-31
> **melrokz said:**
> Can't we simplify the code? :) Like that one below. Is that right?
```
percent=$((($count_now * 100) / $image_count))
```
Modern shells like bash support this form of arithmetic expression which clearly is superior (cleaner, better looking, shorter, & much more efficient) to using bc etc, which is one of the old ways we used to do it. Note that the above can be shortened to
```

percent=$((count_now * 100 / image_count))

```

I.e. you don't need to $ reference variables in such an arithmetic expression.

---

### Post by hakermania on 2012-05-31
> **markbl said:**
> Modern shells like bash support this form of arithmetic expression which clearly is superior (cleaner, better looking, shorter, & much more efficient) to using bc etc, which is one of the old ways we used to do it. Note that the above can be shortened to
```

percent=$((count_now * 100 / image_count))

```

I.e. you don't need to $ reference variables in such an arithmetic expression.

Thanks for this. Does it work in other shells or only in bash?

---

### Post by markbl on 2012-05-31
> **hakermania said:**
> Thanks for this. Does it work in other shells or only in bash?
Well I know at least the same form of arithmetic expressions are supported in korn shell (ksh) so I guess others do also?

I have a Solaris 2.5 box installed and never updated since the mid 90's using ksh and it supports $((a + b)) etc. So it's an old construct.

---

### Post by sisco311 on 2012-05-31
Moved to **Programming Talk**.

[Arithmetic expansion]("http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_06_04") is specified by [POSIX]("http://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html").

Even more info here: [http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression) :)

---

### Post by melrokz on 2012-06-02
Now floating point operations need to be managed by bc. Bash doesn't support it.

---

### Post by sisco311 on 2012-06-02
> **melrokz said:**
> Now floating point operations need to be managed by bc. Bash doesn't support it.

True, but do you really need to know the percentage with 2 decimal accuracy?

And, ls prints its output in human readable form, it will cause bugs in scripts. I'd do something like:
```

#!/bin/bash

...
files=()
shopt -s nullglob
for file in *.png *.jpg
do
    if [[ -f "$file" ]]
    then
        files+=("$file")
    fi
done

n=1
total=${#file[*]}

for file in "${files[@]}"
do
    mv -b -- "$file" "$n.$file"
    printf '%d\n' "$(( n*100/total ))"
    ((n++))
done | zenity ...
```

---

