---
title: "awk 'print' in a bash script"
date: 2006-09-18
forum: Programming Talk
---

### Post by darth_vector on 2006-09-18
i am trying to write a bash script that requires the kind of functionality shown below:```
#!/bin/bash
FILE=$1
COL_TO_PRINT=$2
cat $FILE | awk '{print $COL_TO_PRINT}'
```and for the life of me I can't work out how to do it. of course doing an ```
awk '{print $2}'
```wont work because awk interprets this as the second column of the file, not the second argument of the script.

any help would be appreciated...

---

### Post by cwaldbieser on 2006-09-19
> **darth_vector said:**
> i am trying to write a bash script that requires the kind of functionality shown below:```
#!/bin/bash
FILE=$1
COL_TO_PRINT=$2
cat $FILE | awk '{print $COL_TO_PRINT}'
```and for the life of me I can't work out how to do it. of course doing an ```
awk '{print $2}'
```wont work because awk interprets this as the second column of the file, not the second argument of the script.

any help would be appreciated...

```

$ awk '{print ENVIRON["COL_TO_PRINT"];}' $FILE

```
You could also use the "awk var=value 'program goes here'" syntax.

---

### Post by darth_vector on 2006-09-19
cheers, i will give her a go this arvo...

---

### Post by darth_vector on 2006-09-19
after doing an```
export COL_TO_PRINT
```it worked like a dream.

thanks mate :)

---

