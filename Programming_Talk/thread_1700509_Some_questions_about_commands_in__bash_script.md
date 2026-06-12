---
title: "Some questions about commands in  bash script"
date: 2011-03-05
forum: Programming Talk
---

### Post by vl72 on 2011-03-05
1) Tell me, please. How to work with files and folders in BASH-script if theirs names consist of some words?
For example, name of file «File with some words in it.txt», name of folder «Folder where I saved my pictures»  
When I try execute this script and file «File with some words in it.txt» doesn't exist in my home folder  I receive next errors:
```

#!/bin/bash
cd $HOME
var_1='File with some words in it.txt'
var_2='File\ with\ some\ words\ in\ it.txt'

if [ `ls $var_2 | wc -l` -gt 0 ]    
    then
	    echo 'Yes!'
    else
	    echo 'No!'
fi

```

ls: cannot access File\: No such file or directory
ls: cannot access with\: No such file or directory
ls: cannot access some\: No such file or directory
ls: cannot access words\: No such file or directory
ls: cannot access  in\: No such file or directory
ls: cannot access it.txt: No such file or directory

2)  How to create folder if its name consist of some words?
For example, name of folder «Folder where I saved my pictures».

3) What command can give me numeric position string character (word, phrase) that I have to  search into another string from the start or from the end this string?
For example, I search word «cat» in string «Black and white dogs and cats like to eat meat» (1)
Numeric position word &#8220;cat&#8221; is  26 from the start string (1) and 21 from the end.

4) What command can append data in a new row (line) at the end of a text file? I want to direct output from cycle into the same text file. For example, this text file must have 10 lines after 10 cycle iteration, one record per line.

---

### Post by hakermania on 2011-03-05
Well, use brackets :)
```

myfolder="/home/alex/My Pictures"
#Answer to [1]
cd "$myfolder"
#Answer to [2]
rm -r "$myfolder"
#I don't know the answer to 3
#Answer to [4]
echo "This line will be appended" **>>** file

```

---

### Post by Vox754 on 2011-03-05
> **hakermania said:**
> Well, use brackets :)


LOL, brackets?

Seriously, hakermania, you need to work on your skills if you want to be considered a decent programmer.

Disclaimer: any advice hakermania gives should be taken with care.

Use single quotes or double quotes to preserve the spaces in variables.
```

var_1='File with some words in it.txt'
var_2="File with some words in it.txt"

```

In general, using single quotes will take a string literally, while using double quotes will allow expansion.

When using the variable, enclose it in double quotes. If you enclose it in single quotes, the variable will not expand.
```

touch "$var_2"  # Will create the file
touch '$var_2'  # Will not expand

```

You can also escape the spaces with the backslash, but then, don't use quotes, or they will be treated literally.
```

var_3=File\ with\ some\ words\ in\ it.txt

```

Always use your variables double quoted.
```

cd "$HOME"
mkdir "$var_4"
rm "$var_5"

```

There are places where it's safe not to quote the variables, for example, when they don't contain spaces. But for starters, always double quote the variables.

For more information, don't search "File with some words in it".

Search for "bash filenames with spaces".

[http://ubuntuforums.org/showthread.php?t=1630220&highlight=bash+files+spaces](http://ubuntuforums.org/showthread.php?t=1630220&highlight=bash+files+spaces)

[http://ubuntuforums.org/showthread.php?t=1612116&highlight=bash+files+spaces](http://ubuntuforums.org/showthread.php?t=1612116&highlight=bash+files+spaces)

Etc. Many threads.

---

