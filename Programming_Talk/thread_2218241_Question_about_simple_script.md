---
title: "Question about simple script?"
date: 2014-04-20
forum: Programming Talk
---

### Post by usermane2 on 2014-04-20
Hello,

I would like to write a small program/script and am looking for advice  on how to do so. I do not have a preference about which method or  language to use, hopefully looking for the simplest way to do this.

I have a program that runs on text files e.g. "program file1.txt file2.txt"

I have 20 folders that each have 5-10 text files. I want to  automatically get the name of the largest size text file from each of  the 20 folders, and then run the program on these 20 files as described  above.

Ideally I could point my script to a folder, and it will automatically  find the largest .txt file in each of the subdirectories and run  "program file1.txt file2.txt file3.txt ..."

Any ideas on how to most efficiently accomplish this? Ideas or links to tutorials if applicable are helpful.

Thank you

---

### Post by Vaphell on 2014-04-20
```
#!/bin/bash

files=()

for d in ${1-.}/*/
do
    IFS=$'\t' read -rd $'\0' _ f < <( stat --printf '%s\t%n\0' ${d%/}/*.txt 2>/dev/null | sort -znr )
    [[ -f $f ]] && files+=( "$f" )
done

printf -- '%s\n' "${files[@]}"
program "${files[@]}"
```

---

### Post by Habitual on 2014-04-20
> **usermane2 said:**
> Ideas or links to tutorials if applicable are helpful.

[Various Linux Guides I have collected]("https://www.linuxquestions.org/questions/blog/habitual-558710/various-linux-guides-i-have-collected-35954/")

---

### Post by usermane2 on 2014-04-20
Vaphell,

Thank you so much. Now I have to spend some time studying the code to try and understand what is going on. Would I have to save (copy) this script into the directory I wanted it to begin from, or could I just run it from the directory where I want it to start? I will try to work on passing an option to the script on run - the path of the directory to begin from.

Also your signature links are helpful.


Habitual,

Thank you for the resources. I have some reading to do =)

---

### Post by Vaphell on 2014-04-20
You may have the script wherever you want, it **** defaults to . if param is missing. **${1-.}** takes care of that.

you might add something like this at the top of the script to bail if the param is bad.
```
[[ -d ${1-.} ]] || { echo "dir doesn't exist"; exit 1; }
```

```
stat --printf '%s\t%n\0' ${d%/}/*.txt 2>/dev/null
```
run *stat* for all *.txt in currently processed subdir with output format defined as 'size[tab]filename', with results separated by null char \0.

```
sort -znr
```
Sort the output in reverse numerical order (-nr) having in mind to use null (-z).

```
IFS=[COLOR="#0000FF"]$'\t'[/COLOR] read -rd [COLOR="#0000FF"]$'\0'[/COLOR] _ f < <( ... )
```
Given that you need only 1 file, redirect the whole thing to a single read configured to understand [COLOR="#0000FF"]\0[/COLOR]. It will take the first result and discard the rest. The first result is split on [COLOR="#0000FF"][tab][/COLOR] to 2 vars _ and f'.

```
[[ -f $f ]]
```
take $f and see if it's a proper file - it's a safeguard against empty dirs which would generate empty stat output ($f at the end would be ''). If $f passes the test, append $f to the array storing final results.
```
files+=( "$f" )
```

Once you have array filed with files, you can access all elements with **"${array[@]}"**. The end.

---

### Post by usermane2 on 2014-04-20
You're the man. I'll try to let you know how it goes.

---

