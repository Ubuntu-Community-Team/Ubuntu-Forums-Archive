---
title: "Bash smart copying"
date: 2009-06-29
forum: Programming Talk
---

### Post by MeLight on 2009-06-29
Hi,
new to bash programming and would like to know what would be the best way to do this: lets say we have a folder (a) in which we have files with two extensions .1 and .2. I want to copy file xxx from folder a to folder b only if it appears with both extensions, ie xxx.1 and xxx.2 both exist in a, then I would copy them both to b.
Thanx

---

### Post by Habbit on 2009-06-29
This might do the trick - I haven't tested it, though, and my Bash skills are not that fine lately ;)
```
#!/bin/bash
# Invoked as ./script.sh source/folder ../the/target/directory
srcfolder=$1
tgtfolder=$2

for file1 in $srcfolder/*.1 ; do
    file2 = ${file1/.1}.2   # Remove .1 extension, append .2
    if [ -f $file2 ] ; then # Check that file.2 exists
        cp -p $file1 $file2 $tgtfolder # Copy both
    fi
done
```

---

### Post by ghostdog74 on 2009-06-29
```

#!/bin/bash
awk 'BEGIN{
    # only use .2 to verify .1 
    q="\047"
    destination="/home/destination"
}
FILENAME ~ /\.1$/{
    split(FILENAME,f1,".")
    one[f1[1]]   
    nextfile
}
FILENAME ~ /\.2$/{
    split(FILENAME,f2,".")
    two[f2[1]]
    nextfile
}
END{
  for(o in two) {    
    if ( o in one ){        
        cmd= "cp "o".1 "o".2 " destination # use "mv" as desired
        print cmd
        system(cmd)
    }    
  }
}' *.[12] 


```

output
```

# ls -1
temp  <<--------this is destination
xxx.1
xxx.2
yyy.1
yyy.2
zzz.1  <<------------- only file without .2 extension

# ./test.sh
cp yyy.1 yyy.2 /home/destination
cp xxx.1 xxx.2 /home/destination

# ls -1 temp
xxx.1
xxx.2
yyy.1
yyy.2


```

---

### Post by MeLight on 2009-06-29
Thanx for the replies guys.
Habbit, I ran your script like this:
```
sh smart_copy.sh out_par pairs
```
and it gave me this error:
```
smart_copy.sh: 11: Bad substitution
```

ghostdog, i didn't really understand how to run your script.
thx

---

### Post by geirha on 2009-06-29
> **MeLight said:**
> Thanx for the replies guys.
Habbit, I ran your script like this:
```
sh smart_copy.sh out_par pairs
```
and it gave me this error:
```
smart_copy.sh: 11: Bad substitution
```


That's because Habbit's script is a bash script, while you ran it with sh which does not have all the features of bash. A script that works with sh, will work with bash, but not the other way round.

Either make it executable and run it with ```
./smart_copy.sh out_par pairs
``` in which case it will run it with the interpreter in the she-bang (#!/bin/bash), or run it specifically with bash
```
bash smart_copy.sh out_par pairs
```

---

### Post by ghostdog74 on 2009-06-29
> **MeLight said:**
> 
ghostdog, i didn't really understand how to run your script.
thx
i have already shown you how to run it.

---

### Post by geirha on 2009-06-29
Oh hang on, I just noticed that the script has a syntactical error (space around the = sign). Here's a revised edition of Habbit's script, that also works with sh, and will handle paths with spaces
```
#!/bin/sh
# Invoked as ./script.sh source/folder ../the/target/directory
for file1 in "$1"/*.1; do
    file2="${file1%.1}.2"   # Remove .1 extension, append .2
    [ -f "$file2" ] && cp -v "$file1" "$file2" "$2" # Copy both
done

```

---

### Post by MeLight on 2009-06-29
geihra thanx a lot! It's running perfectly now. Is bash sensitive to white spaces in general?

ghostdog, yeah sorry, I see it now

---

### Post by geirha on 2009-06-29
> **MeLight said:**
> geihra thanx a lot! It's running perfectly now. Is bash sensitive to white spaces in general?


A bit vague question... but I guess the answer is yes.
```

var=value   # Good, sets the variable var with the given value 
var= value  # Runs the command value, and passes var='' to its environment
var = value # Runs the command var with the two arguments; "=" and "value"

if [[ "$var" = "foo" ]]  # Good, evaluates to true if $var equals "foo"
if [[ "$var"="foo" ]]    # Legal, but will not compare "$var" with "foo"
if [["$var" = "foo"]]    # Syntax error

```

---

