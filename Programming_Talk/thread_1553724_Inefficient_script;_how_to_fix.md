---
title: "Inefficient script; how to fix?"
date: 2010-08-15
forum: Programming Talk
---

### Post by tarahmarie on 2010-08-15
So, here is my script to intelligently divide text files by paragraphs.

```

#!/bin/bash
bookcounter=0
linecounter=0
sed -i 's/\r$//' iliad.txt
while read line
do
    ((linecounter+=1))
    if [[ $linecounter -gt 300 && -z "$line" || -z "$output_file" ]]; then
        linecounter=0
        ((bookcounter+=1))
        formatted_bookcounter=$(printf "%03d" $bookcounter)
        output_file=iliad${formatted_bookcounter}.txt
        echo "...starting segment $output_file"
        echo "Iliad - segment $formatted_bookcounter" > $output_file
        echo "===================" >> $output_file
        echo "" >> $output_file
    fi
    echo "$line" >> $output_file
done < iliad.txt

```

Here's the thing...I want to be able to use this script again and again, but as something that operates on a target file instead of having to open the script and edit it with the name of the file I'll be using.  I don't really know where to start on that one; I'm learning bash bit by bit.  Is there some way to specify an operator? Is there a best practice?

---

### Post by geirha on 2010-08-15
Wrap a for-loop around that whole thing (see ''help for''), and use parameter expansion to extract the basename and extension of the input file. (see [http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073))
```
#!/bin/bash
for input_file; do
  bookcounter=0 linecounter=0
  while read -r line; do
    ...
      output_file=${input_file%.*}$formatted_bookcounter.${input_file##*.}
    ...
  done < <(sed $'s/\r$//' "$input_file")
done

```

```
./script illad.txt foo.txt bar.txt ...
```

---

### Post by DaithiF on 2010-08-15
Hi, I interpreted the request as just to make the file to be operated on a parameter rather than hardcoded in the file, rather than necessarily a request to be able to do multiple files in one go.  (though the latter would be just a short step from the former).

in any case, heres one that takes a single file as its parameter.  adapt as geirha suggests if you want to make it work for multiple
```
#!/bin/bash

book=$1

[[ -z $book ]] && { echo "No argument supplied, exiting!"; exit 1; }

[[ ! -e $book ]] && { echo "Can't find a file with the name $book, exiting"; exit 1; }

title=${book%.*}
bookcounter=0
linecounter=0
sed -i 's/\r$//' "$book"
while read line
do
    ((linecounter+=1))
    if [[ $linecounter -gt 300 && -z "$line" || -z "$output_file" ]]; then
        linecounter=0
        ((bookcounter+=1))
        formatted_bookcounter=$(printf "%03d" $bookcounter)
        output_file="${title}${formatted_bookcounter}.txt"
        echo "...starting segment $output_file"
        echo "$title - segment $formatted_bookcounter" > $output_file
        echo "===================" >> $output_file
        echo "" >> $output_file
    fi
    echo "$line" >> $output_file
done < "$book"

```

---

### Post by ghostdog74 on 2010-08-16
as your file gets bigger, bash's while read loop gets slower. Learn to use awk to process files. Its faster than bash's while read loop on big files( and small), and awk can do more than what bash can.

the awk statement below assumes your paragraph's are seperated by blank lines, and not every 300 lines.
```

awk 'BEGIN{RS=""}{print $0 > c++".txt"}' file

```
And each paragraph's file name is tagged with a number denoted by "c" variable.

You might also want to take a look at csplit and split (man csplit/split) to separate files by context or number of bytes etc..

---

### Post by tarahmarie on 2010-09-01
> **DaithiF said:**
> Hi, I interpreted the request as just to make the file to be operated on a parameter rather than hardcoded in the file, rather than necessarily a request to be able to do multiple files in one go.  (though the latter would be just a short step from the former).

in any case, heres one that takes a single file as its parameter.  adapt as geirha suggests if you want to make it work for multiple
```
#!/bin/bash

book=$1

[[ -z $book ]] && { echo "No argument supplied, exiting!"; exit 1; }

[[ ! -e $book ]] && { echo "Can't find a file with the name $book, exiting"; exit 1; }

title=${book%.*}
bookcounter=0
linecounter=0
sed -i 's/\r$//' "$book"
while read line
do
    ((linecounter+=1))
    if [[ $linecounter -gt 300 && -z "$line" || -z "$output_file" ]]; then
        linecounter=0
        ((bookcounter+=1))
        formatted_bookcounter=$(printf "%03d" $bookcounter)
        output_file="${title}${formatted_bookcounter}.txt"
        echo "...starting segment $output_file"
        echo "$title - segment $formatted_bookcounter" > $output_file
        echo "===================" >> $output_file
        echo "" >> $output_file
    fi
    echo "$line" >> $output_file
done < "$book"

```

I wanted to let you know; I hadn't had a chance to test this script until now. It's elegant, works perfectly and intuitively, and cranks out portions exactly as I wanted it to. Thanks!

---

