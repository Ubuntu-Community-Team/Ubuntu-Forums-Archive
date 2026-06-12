---
title: "[SOLVED] Bash Variable from Data Question"
date: 2008-12-04
forum: Programming Talk
---

### Post by melrom on 2008-12-04
Hi-

I'm creating a shell script that will be taking in data and I want to create separate variables that contain the name of the data taken in.

for instance, if the data obtained is in a variable called $var1 = "txt", I want to create a new variable named "txt_count" somehow using $var1. I am also wondering if I can later test these variables in an if statement, using the same kind of concept. 

Something along the lines of $var1_count. 

I can't just use an if statement, as I am dealing with a lot of data that I want to do this for.

For instance, in the vain of filenames, if I had txt, jpg, ogg, cpp, I'd want to create corresponding variables txt_count, jpg_count, ogg_count, and cpp_count [except that I am doing this with over 100 pieces of data]. And then later, I want to be able to say, based on having only this $var1 [which could be equal to txt, jpg, ogg, or cpp], and say does $var1_count exist in an if statement or something along those lines.

I'm not sure if this is possible in bash.

---

### Post by melrom on 2008-12-04
note, something like this:

```

var="0"
"$var"_count="2"
echo $var_count

```

yields

```

 0_count=2: command not found

```

I suppose an easier problem to tackle would be can I create variables like this?

If I have a file containing:
```

txt
cpp
ogg

```

And I read those [individually] off of the file into a variable called $ftype, could I then make a new variable which is the basically equal to the value of $ftype. Basically, it's like psuedo-dynamically creating variables. Is that possible?

---

### Post by geirha on 2008-12-04
Possible, yes, but you really should avoid such programming. Instead, you could use arrays for example. Here's a small bash script checking all files in the current directory, counting the number of files with the same extensions:

```

#!/bin/bash

# Declare $extensions and $counts to be arrays. Not really necessary, but it
# shows that you intend these to be arrays.
declare -a extensions
declare -a counts

for file in *.*; do
    # Set $ext to $file with everything up to the last '.' removed.
    ext="${file##*.}"

    # Check if $extensions has this extension already and increment the count
    # for that extension if that is the case
    for ((i=0; i < ${#extensions[*]}; i++)); do
        if [ "$ext" = "${extensions[i]}" ]; then
            ((counts[i]++))
            break
        fi
    done
    # If $i equals the size of the array, there wasn't an entry for that
    # extension already, so we add a new element to the arrays.
    if [ $i -eq ${#extensions[*]} ]; then
        extensions[i]="$ext"
        counts[i]=1
    fi
done

# Print the results
for ((i=0; i < ${#extensions[*]}; i++)); do
    echo "There are ${counts[i]} files with '${extensions[i]}' extension"
done

```

To do what you originally wanted, you'd need to use eval
```

$ var=txt
$ eval ${var}_count=2
$ echo $txt_count
2

```

---

### Post by melrom on 2008-12-05
Yes, I was thinking about using arrays. Thanks for both tips! =)

---

