---
title: "How to edit/prepend current line in a while read loop in bash?"
date: 2012-02-01
forum: Programming Talk
---

### Post by Birion on 2012-02-01
Hi, I've been trying to write a bash script that reads a file with single words delimited by newlines, looking for the first line that does not start with a specific character (e.g. #), does something based on the line, and puts # at the beginning of the line to mark it done.

```

$ cat ~/example.txt
#cat
#dog
cat
dog
fish

```

```


SOURCE_FILE=~/example.txt

while read line
do
    ISDONE=`echo $line | sed "s/^(.).*/\$1/" -` # this line may be wrong, since I'm not at a computer that can run bash, so I can't remember exactly (and the computer that can is currently Internet-less and far away), but it's correct in the script
    if [[ $ISDONE -eq "#" ]]
    then
        continue
    else
        case $line in
            ... # do stuff here based on the contents of the line
        esac
        # here's the problem
        # I wanted to put something like
        sed "$line s/^/#/"
        # but I kept hitting some errors
        exit
    fi
done < $SOURCE_FILE


```

so that after running the script once, the file should look like

```

$ cat ~/example.txt
#cat
#dog
#cat
dog
fish

```

---

### Post by mobilediesel on 2012-02-01
> **Birion said:**
> Hi, I've been trying to write a bash script that reads a file with single words delimited by newlines, looking for the first line that does not start with a specific character (e.g. #), does something based on the line, and puts # at the beginning of the line to mark it done.

```

$ cat ~/example.txt
#cat
#dog
cat
dog
fish

```

so that after running the script once, the file should look like

```

$ cat ~/example.txt
#cat
#dog
#cat
dog
fish

```

This should do it:
```
SOURCE_FILE=~/example.txt

while read line
do
    if [[ ${line:0:1} != "#" ]]
    then
        case $line in
            ... # do stuff here based on the contents of the line
        esac
        sed -i "0,/^${line}$/ s/^/#/"
        exit
    fi
done < $SOURCE_FILE
```
The **${line:0:1}** returns only the first character of $line.
**!=** to test that **${line:0:1}** is not equal to "#".
The **-i** makes sed edit the file in place.
The **0,** makes sure sed only changes the first occurrence.
**/^${line}$/** makes sure it matches the exact line.

---

### Post by Birion on 2012-02-01
Thanks. I didn't know about the ${line:0:1} use, so I'm glad to learn something new (and perhaps simplify some other scripts that relied on the echo|sed combination I used). Unfortunately, it'll be hours before I can try it out, but from your explanation, it seems to do exactly what I wanted.



...I really need to learn sed... :/

---

