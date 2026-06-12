---
title: "Bash: passing arguments with spaces"
date: 2010-02-11
forum: Programming Talk
---

### Post by tolanri on 2010-02-11
Hi, I'm working on script, and I need to pass information to it with path to file. However, if the path contains spaces, script will break
I'm calling the script with ./script.sh "/home/tolanri/some/file/with archive.rar"

```

#!/bin/bash
path=$1

function checkcontent() {
echo $path

    for filename in `find "$path" -type f`
    do
    echo $filename
        if [ `file "$filename" | grep -c "RAR archive data"` -eq 1 ]; then
            return 1
        fi
    done
    
    return 0
}

checkcontent
if [ $? -eq 1 ]; then
[...]

```

---

### Post by matchett808 on 2010-02-11
cant remember 100% but i think that the correct syntax is something along the lines of 
"sh ./script /path/to/file\ i\ need\ in\ script"

(without the bunny ears "") lol

---

### Post by matchett808 on 2010-02-11
infact just checked in a terminal....that should hopefully make ur script work...

---

### Post by tolanri on 2010-02-11
Thanks, but unfortunately rTorrent client passes path information in "/path/to file" format. So I should somehow modify $1 format before passing it into function, but how do I do that?

---

### Post by dwhitney67 on 2010-02-11
I suspect it is the for-loop that is causing the issues; I say because I was able to write a trivial program that read in a path chock-full of white-space, and use it with the 'find' command.  It was the results from the 'find' command that were unusable.

Try something like:
```

#!/bin/bash

path=$1

find "$path" -type f | while read filename
do
        echo $filename

        # continue with whatever it is that you want...
done

```

---

### Post by matchett808 on 2010-02-11
I cant check it with rtorrent it is removed from my computer but from the looks of it

when you call a bash script the variables $1 $2 $3 $4 etc, are separated by whitespace....
ie. mv /file1 /file2
see....mv was the command and /file1 is $1 and file2 is $2......so when running your script like this:
./script.sh "/home/tolanri/some/file/with archive.rar"
$1 is "/home/tolanri/some/file/with
and $2 is archive.rar"
(you could check this by adding -  echo $1; echo $2 - to your script...)
so for bash to ignore the whitespace it needs a special charecter which is \ ....

you can use tab-completion for a filename to verify this...

---

### Post by tolanri on 2010-02-11
dwhitney67's solution worked great!

Thank you, both of you :)

---

