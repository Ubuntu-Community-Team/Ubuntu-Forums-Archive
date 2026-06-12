---
title: "shell script to delete before/after a pattern"
date: 2011-12-19
forum: Programming Talk
---

### Post by Blackbug on 2011-12-19
I need to delete n no. of lines above a PATTERN and m no of lines below the PATTERN
I tried using sed ```
sed '/PATTERN/,+12d' old.xml> new.xm
```
 
But this deletes after the pattern, I need something to delete before the pattern also.
 
Please suggest

---

### Post by sisco311 on 2011-12-19
Sounds like your homework...

Anyway, I'd use ed: [http://wiki.bash-hackers.org/howto/edit-ed](http://wiki.bash-hackers.org/howto/edit-ed)

Something like:```

ed -s file <<< $'g/PATTERN/-X,.d\n,p'
ed -s file <<< $'g/PATTERN/.,+Xd\d,p'

```

I will let you figure out how to combine the commands in a single one and how to write to the file directly instead of printing the result to stdout.

---

### Post by Blackbug on 2011-12-19
well i am too grown up for a homework..but yes its related to my work.. i have to analize around 100,000 xml files and need to delete a specific set of lines from them, thus need a script..
i have used sed for deleting after a pattern, but couldnt find anythin useful for delete n lines before a pattern

---

### Post by Telengard C64 on 2011-12-20
I whipped up an AWK program which I think does what you want. No guarantees though.

```
#! /usr/bin/awk -f

# Deletes n lines before pattern and m lines after.
# It is your own responsibility to evaluate the fitness of this program.

BEGIN {
    # set the following initializers as you please
    # FS=" "
    # OFS=" "
    n=5
    m=3
}

/line 11/ { # insert your desired regex "pattern" between the slashes
    pattern_line=NR
    filename=FILENAME
    exit
}

END {
    while (getline < filename) {
	++line
	if (line < pattern_line - n) print
	if (line == pattern_line)    print
	if (line > pattern_line + m) print
    }
    close(filename)
}
```

Here's the input file I fed it.

```
$ cat data.xml
line 1
line 2
line 3
line 4
line 5
line 6
line 7
line 8
line 9
line 10
line 11
line 12
line 13
line 14
line 15
line 16
line 17
line 18
line 19
line 20
$
```

Here's the output produced.

```
$ ./del-n-before-m-after.awk data.xml
line 1
line 2
line 3
line 4
line 5
line 11
line 15
line 16
line 17
line 18
line 19
line 20
$
```

[man awk](http://manpages.ubuntu.com/manpages/mawk)

If the program doesn't work for you then it would help to know which AWK you have.

```
awk -Wversion
```

---

### Post by Arndt on 2011-12-20
> **Blackbug said:**
> well i am too grown up for a homework..but yes its related to my work.. i have to analize around 100,000 xml files and need to delete a specific set of lines from them, thus need a script..
i have used sed for deleting after a pattern, but couldnt find anythin useful for delete n lines before a pattern

Are you sure your XML files are in such a well-defined format that you can use standard text tools on them? It may be better to use XML tools like xslt.

---

### Post by Blackbug on 2011-12-20
> **sisco311 said:**
> Sounds like your homework...
 
Anyway, I'd use ed: [http://wiki.bash-hackers.org/howto/edit-ed](http://wiki.bash-hackers.org/howto/edit-ed)
 
Something like:```

ed -s file <<< $'g/PATTERN/-X,.d\n,p'
ed -s file <<< $'g/PATTERN/.,+Xd\d,p'

```
 
I will let you figure out how to combine the commands in a single one and how to write to the file directly instead of printing the result to stdout.
 
 
Thanks for the help i used "ed" for deleting before pattern.
My script is not an idle way to do things, but somehow it worked and i removed the necessary elements from 100000 xml files.
 
```
 
FILENAME=$1
TEMP_FILE="$FILENAME.temp"
TEMP_FILE1="$FILENAME.temp1"
sed '/<PATTERN>/ i\TEMP' $FILENAME >$TEMP_FILE
ed -s $TEMP_FILE <<< $'g/TEMP/-91,.d\n,p' > $TEMP_FILE1
sed '/<PATTERN>/,+12d' $TEMP_FILE1>"$FILENAME.final"
rm $TEMP_FILE $TEMP_FILE1
```
 
I was short of time so didnt considered best way, now will optimize it.
 
Thanks for suggestions

---

### Post by Blackbug on 2011-12-20
> **Telengard C64 said:**
> I whipped up an AWK program which I think does what you want. No guarantees though.
 
```
#! /usr/bin/awk -f
 
# Deletes n lines before pattern and m lines after.
# It is your own responsibility to evaluate the fitness of this program.
 
BEGIN {
    # set the following initializers as you please
    # FS=" "
    # OFS=" "
    n=5
    m=3
}
 
/line 11/ { # insert your desired regex "pattern" between the slashes
    pattern_line=NR
    filename=FILENAME
    exit
}
 
END {
    while (getline < filename) {
    ++line
    if (line < pattern_line - n) print
    if (line == pattern_line)    print
    if (line > pattern_line + m) print
    }
    close(filename)
}
```
 
Here's the input file I fed it.
 
```
$ cat data.xml
line 1
line 2
line 3
line 4
line 5
line 6
line 7
line 8
line 9
line 10
line 11
line 12
line 13
line 14
line 15
line 16
line 17
line 18
line 19
line 20
$
```
 
Here's the output produced.
 
```
$ ./del-n-before-m-after.awk data.xml
line 1
line 2
line 3
line 4
line 5
line 11
line 15
line 16
line 17
line 18
line 19
line 20
$
```
 
[man awk]("http://manpages.ubuntu.com/manpages/mawk")
 
If the program doesn't work for you then it would help to know which AWK you have.
 
```
awk -Wversion
```
 
Thanks for your script it was really nice and useful but somehow the xml tags in my files werent happy about it and was giving some errors, didnt had time to solve the issue so just opted for the workaround posted above.
 
Thanks anyway

---

### Post by sisco311 on 2011-12-20
> **Arndt said:**
>  It may be better to use XML tools like xslt.

+1

You can't realistically parse tag-based markup languages like HTML and XML using Bash or utilities such as grep, sed or cut.

---

