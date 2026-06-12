---
title: "Shell script: Always write two digit numer"
date: 2008-09-22
forum: Programming Talk
---

### Post by Moezzie on 2008-09-22
Hey guys!

Im writing a little shell script that generates a given amount of text files. The filenames all have to follow a certain format.
Each filename has a number at the end that increases for every file. If this number is below 10 i only get one number. It would be good to always have a two digit number here.

What i would like to achieve is to have the script put an extra 0 in front of the numbers 1-9 so that every file looks something like this:
1972p03r01.txt
1972p03r02.txt
1972p03r03.txt
...
1972p03r12.txt

Ive heard about something called wild cards that could do such a thing. I havnt been able to find any info on that though.
This is what i've got so far:
```


                  
echo "Number of files:"
read number                         # Number of files to create
 
echo "List of temporary files : "
for ((i=1; i <= $number; i++))
    do
        FILE="1973p04r$i.txt"       # Put a 0 in front of $i if $i < 10. How?
        echo $FILE                  # show file name
        > $FILE                     # create files
done

```

Feel free to ask more questions. I know i can be a pretty messy explainer.
Thanks for you help!

---

### Post by MarkieB on 2008-09-22
no longer participating in ubuntuforums.org

---

### Post by ghostdog74 on 2008-09-22
here's an example using printf
```

# a=10
# printf "%02d" $a
10
# printf "%03d" $a
010
#   

```

---

### Post by Moezzie on 2008-09-22
> **MarkieB said:**
> can't you simply put in a test?

```
[ $i -lt 10 ]; FILE="1973p04r0$i.txt"
[ $i -ge 10 ]; FILE="1973p04r$i.txt"
```

Thanks MarkieB! This works excellent.
I paired it together with an if-statement and it does exactly what it needs to. 

If anybody needs something similar, here is the working code:
```

#!/bin/bash
# Shell script to generate text files with a predefined format
# Feel free to modify or use in your own projects
# Author: Moezzie

 
echo "Year:"
read year
echo "Part:"
read part
echo "Number of files:"
read number

echo "List of files : "
for ((i=1; i <= $number; i++))
    do
        if [ $i -lt 10 ];         # If $i is smaller than 10
        then
            FILE="$year""p$part""r0$i.txt"    # Set filename with extra 0
        else
            FILE="$year""p$part""r$i.txt"     # Set filename without extra 0
        fi

        echo $FILE                # show file name
        > $FILE                   # create files
done

```

---

### Post by MarkieB on 2008-09-22
no longer participating in ubuntuforums.org

---

