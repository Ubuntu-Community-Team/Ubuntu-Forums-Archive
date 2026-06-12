---
title: "Help with diff"
date: 2009-01-01
forum: Programming Talk
---

### Post by HLEBARKATA on 2009-01-01
Hi all,
I try with diff to compare 2 text files, but I want only to
get the exact output.
I mean like 
file 1:          

Hello             
World             
How               
Are               
You

file 2:
Hello                    
How               
Are               
You

diff file1 file2 to have the output "World"

Thanks for any help

---

### Post by ghostdog74 on 2009-01-01
check the diff man page whether there are options for output formatting, otherwise, just simply
```

diff file1 file2 | awk '/^</{$1="";print}'   

```

---

### Post by HLEBARKATA on 2009-01-01
The first thing I did was to have a look at the man page but this option 
doesnt exists or I havent seen it.
 diff file1 file2 | awk '/^</{$1="";print}'
removes all new lines and dont work (More than half of the differences dont show up)

---

### Post by ghostdog74 on 2009-01-01
show a sample of what the diff output is, and then how you want it to look like.

---

