---
title: "awk - need help comparing 2 files"
date: 2010-06-30
forum: Programming Talk
---

### Post by melissawong on 2010-06-30
Hi, I've been trying to write a script to compare 2 files (file 1 & file 2) but failed. I found a script online that works but it's long and slow. Here's what i wanna do: 
If col1&2 of file 1 matches col1&2 of file 2, print col1&col2 file 1 + col3 file 2. Otherwise, print col123 from file 1. For example:

File 1:
a 1 A
a 2 T
a 3 C

File 2:
a 2 Y
a 3 R

output:
a 1 A
a 2 Y
a 3 R

Any help will be appreciated. 
Cheers, Melissa

---

### Post by geirha on 2010-06-30
Maybe something like this?
```
awk 'NR==FNR && a[$1" "$2]=$3 {} NR>FNR { k=$1" "$2; if (k in a) print k,a[k]; else print $0}' file2 file1
```

It reads file2 first and fills up an array, using fields 1 and 2 as keys, field 3 as value. When it then reads file1 it checks whether field 1 and 2 is in that array, if it is, print the array's contents, otherwise, print the line from file1.

---

### Post by Some Penguin on 2010-06-30
Why 'awk'?  If you're permitted to use other tools, and to assume that file1 never has duplicate <col1,col2> pairs, it's pretty trivial -- use a hash table.

---

### Post by melissawong on 2010-06-30
> **geirha said:**
> Maybe something like this?
```
awk 'NR==FNR && a[$1" "$2]=$3 {} NR>FNR { k=$1" "$2; if (k in a) print k,a[k]; else print $0}' file2 file1
```It reads file2 first and fills up an array, using fields 1 and 2 as keys, field 3 as value. When it then reads file1 it checks whether field 1 and 2 is in that array, if it is, print the array's contents, otherwise, print the line from file1.

Great! It works very well. Thanks for the explanation too. What does '{} NR>FNR ' mean?

---

### Post by soltanis on 2010-07-01
FNR is the current record number in the file that is being processed, while NR is the total number of records that have been processed since AWK began executing. In the script, he's using it to tell whether he is still processing the first file or if he has gotten to the second file yet (if NR>FNR, then we're processing the second file; otherwise if NR==FNR, we're processing the first file).

These conditions are being used as the patterns to select the appropriate pattern/action pairs for each record (which is how awk operates).

What I can't figure out is why
```

a[$1" "$2]=$3

```

Was being used as part of the pattern (it could've just as easily been part of the action, and it would've been clearer that way, but awk isn't known for clarity).

---

### Post by melissawong on 2010-07-01
You mean like this? This works for me even without '{}'

awk 'NR==FNR {a[$1" "$2]=$3;next} NR>FNR { k=$1" "$2; if (k in a) print k,a[k]; else print $0}' file2 file1

But why add '{}' ? I never seen this in any awk scripts.

---

### Post by geirha on 2010-07-01
You are absolutely right, it should've been part of the action (though in this case it makes no difference, only less readability).
```

awk 'NR==FNR { a[$1" "$2]=$3 } NR>FNR { k=$1" "$2; if (k in a) print k,a[k]; else print $0}' file2 file1

```
And with some newlines and indentation, it may be even more readable.
```

awk '
NR==FNR { 
    a[$1" "$2]=$3 
} 
NR>FNR { 
    k=$1" "$2; 
    if (k in a) 
        print k,a[k]; 
    else 
        print $0
}
' file2 file1
```

---

