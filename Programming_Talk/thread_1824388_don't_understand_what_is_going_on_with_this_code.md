---
title: "don't understand what is going on with this code"
date: 2011-08-13
forum: Programming Talk
---

### Post by slashwannabe94 on 2011-08-13
Hello all, i know this may be a stupid question but i can't get my head around it. 

I was writing a script to list files, subdirectories, files with zero length and the disk storage used in my home directory. I was given this code by someone on the forums. It works and does what i want it to do. But their is no point in using code that i don't understand. I have no clue what is going on when it runs. 

I understand the lines highlighted in red. But nothing else. 

files=()
while IFS= read -d '' -r file
do
    files+=("$file")
done< <(find ./ -maxdepth 1 -type f -print0)
[COLOR=Red]echo "The number of files in the current directory =[/COLOR] ${#files[@]}"
[COLOR=Red]echo -n "The number of subdirectories = "
ls -a -I .. -1 --file-type --group-directories-first | grep / | wc -l
echo -n "The number of files with zero length = " 
find . -maxdepth 1 -type f -size 0c | wc -l 
echo -n "The amount of disk storage used by this directory = "
du -h -c /home/static | tail -n 1[/COLOR]

Any help is much appreciated. Thanks guys, 

SlashWannabe94

---

### Post by Bachstelze on 2011-08-13
In a nutshell, declares files as an empty array and then adds eeach line of the output of the find command as an element in the array. See man find and man builtins.

---

### Post by dwhitney67 on 2011-08-13
The following lists all of the files (not sub-directories), due to the **-type f** option, that are within the current directory; it does **not** delve into sub-directories due to the **-maxdepth 1** option.  **print0** tells 'find' to to print all results in a single string with filenames separated by a white-space.  A newline is **not** appended to the string.
```

find ./ -maxdepth 1 -type f -print0

```
Try running the command above from a terminal to see the results yourself.

This next part redirects the output (string) of the 'find' command to a sub-shell:
```

done< <(find ...

```
where the output is tokenized by using a single-space as a delimiter (IFS is the Internal Field Separator).  This is what is transpiring here:
```

while IFS= read -d '' -r file

```
Each tokenized string that is extracted is assigned to the variable 'file'.

For each file that is found, an array, which is initially empty, is augmented:
```

files+=("$file")

```
This is repeated until the entire string that is produced by 'find' is processed.

You might find it helpful to insert an echo statement within the loop so that you can observe each file as it is found from the 'find' result; for example:
```

files=()
while IFS= read -d '' -r file
do
**echo "Found file: $file"**
files+=("$file")
done< <(find ./ -maxdepth 1 -type f -print0)

```

---

### Post by ofnuts on 2011-08-13
> **dwhitney67 said:**
> 

You might find it helpful to insert an echo statement within the loop so that you can observe each file as it is found from the 'find' result; for example:
```

files=()
while IFS= read -d '' -r file
do
**echo "Found file: $file"**
files+=("$file")
done< <(find ./ -maxdepth 1 -type f -print0)

```

What I don't get is why he isn't using plain "find  ./ -maxdepth 1 -type f -print0 | wc -l" for this, and, if there is  a reason, why he doesn't do the same for the other lists.

---

### Post by slashwannabe94 on 2011-08-13
thanks guys. You cleared it all up for me :) 
these forums kick a** :D 

Thanks, 
SlashWannabe94

---

