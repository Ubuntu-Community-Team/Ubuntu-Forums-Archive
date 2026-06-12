---
title: "find into array and quotation problem"
date: 2010-09-29
forum: Programming Talk
---

### Post by jamesisin on 2010-09-29
I am building an array from a *find* command.  I am having trouble with my syntax and presumably the problem is quotation marks.


```
read -p "Please provide the root folder under which I will work recursively: "
   if [ -d "$REPLY" ]; then
      printf "\nI have confirmed this is a directory.\n\n"
      directory="$REPLY"
   else
      printf "\nI cannot confirm this is a directory.\n\n"
      exit 1
   fi

albumfind=""
declare -a albumfind
   albumfind="( $( find "$directory" -type f -name \*.[Aa][Pp][Ee] -o -name \*.[Ff][Ll][Aa][Cc] ))"
   a=${#albumfind[*]} # count array
   
echo "The count is "$a" files."

printf "The array albumfind is "$albumfind", dog.\n\n"
   
for (( i=0; i<${a}; i++ ));
   do echo ${albumfind[$i]}
   done

printf "\n\nNothing to see here folks.  This is how it ought to look.\n\n"

find $directory -type f -name \*.[Aa][Pp][Ee] -o -name \*.[Ff][Ll][Aa][Cc]
```

As you can see I am using the same *find* command twice in the script.  However, no matter how I arrange my quotation marks I cannot get them to display the same results.  The final line is working as expected (of course), but the array is either one element or 75 (compared to the actual count of 25).

Can someone help me with my syntax?

---

### Post by jamesisin on 2010-09-29
For someone who is really good with arrays this is probably quite basic.  I know exactly where the problem is; I just don't know how to fix it.

The output of *find* is delineated into lines.  This is true if I take the output at the terminal or if I direct it into a file.  However, when I send that output into an array, the array creates a new element each time it encounters a space and so I end up breaking several lines into separate elements.

I want each line of output from *find* to be treated as though it were quoted.  I just don't know how to get there from where I am.

---

### Post by jamesisin on 2010-09-30
Coming along, as it were.  I have found a way to get individual lines arrayed as individual elements.

```
directory=/some/file/with/subs/and/flacs

find "$directory" -type f -name \*.[Aa][Pp][Ee] -o -name \*.[Ff][Ll][Aa][Cc] > /tmp/whyme

awk '
BEGIN{RS=""}
{
  n=split($0,arr)
  asort(arr)
  for(i=0;i<=n;i++)
     print arr[i]
}' /tmp/whyme

declare -a albumfind
   let linecount=0
   while read LINE; do
      albumfind[$linecount]=$LINE
      ((linecount++))
   done < /tmp/whyme

echo Element count: ${#albumfind[@]}
echo ${albumfind[@]}
printf "\n\n"
echo ${albumfind[5]}
```

The *echo* and *printf* stuff is just so I can see what my output is doing and will go away.

The *awk* is not finished, but it's supposed to sort the lines.  The problem is it is sorting by whitespace and I just want it to sort by line breaks.  (As such it's output is not yet directed.)

Questions or suggestions are welcome.

---

### Post by lavinog on 2010-09-30
use the following if you want to change the field separator to just line breaks:
```

IFS='
'

```

if you need to return IFS back to normal just unset it:
```

unset IFS

```

IFS is a special variable that tells bash how to separate fields.
By default is is set to space, tab, and newline.

So if you do the following in a folder with files that have spaces:
```
for file in *
```
you are likely going to have errors.

Using IFS as above should fix that:
```

IFS='
'
for file in *
do
foo file
done

```

---

### Post by jamesisin on 2010-09-30
Thanks.  I went through a few changes since then.  I found that although the array was printing as a block (not parsing by line) the array was being built correctly.  This is the code I'm using to do that:

```
find "$directory" -type f -name \*.[Aa][Pp][Ee] -o -name \*.[Ff][Ll][Aa][Cc] > /tmp/whyme

declare -a albumfind
   let linecount=0
   while read albumline; do
      albumfind[$linecount]=$albumline
      ((linecount++))
   done < /tmp/whyme
```

I would have rather done this with a variable but I couldn't get the variable to behave the same (though the variable prints correctly it remains a single element).

I've used IFS in the past (often in for loops), but I didn't see a way to make it improve this block (make it shorter or fewer steps or less processing).

Please let me know if you can improve on this code snippet.

(Also, I have abandoned the sorting because though the elements are arrayed in a disordered manner they are *always* disordered in the same manner so it doesn't matter for what I'm doing.)

---

### Post by jamesisin on 2010-09-30
The final product for any interested parties:

[http://www.soundunreason.com/InkWell/?p=2485](http://www.soundunreason.com/InkWell/?p=2485)

---

