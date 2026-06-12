---
title: "Grep / awk"
date: 2013-05-02
forum: Programming Talk
---

### Post by GrouchyGaijin on 2013-05-02
Hi Guys,

I have a decent command line script that will let me add, edit and view my Google tasks.
I've fed the output into Conky using kaivalagi's conkyText script.


This gives me:

```

GrouchyGaijin's list
   0 [ ] Test Task 
     Due Date: Fri, May 03, 2013
   1 [ ] Another Test Task
     Due Date: Fri, May 03, 2013

```

Is there a way I can automatically change the output of the script to go from the above example to
```

0; Test Task; Due Date: Fri, May 03, 2013
1; Another Test Task; Due Date: Fri, May 03, 2013

```

Or does that fact that the length and content of the output will change depending on the tasks make it impossible?

---

### Post by papibe on 2013-05-02
Hi GrouchyGaijin.

I think 'awk' would be more suitable for that job.

This works (except some trailing spaces):
```
$ awk '/\[ \]/ {n=$1; $1=$2=$3=""; printf("%s;%s; ",n,$0); getline; print $0}'  file.txt

0;   Test Task;      Due Date: Fri, May 03, 2013
1;   Another Test Task;      Due Date: Fri, May 03, 2013

```
Regards.

---

### Post by GrouchyGaijin on 2013-05-03
Thank you!
I truly do appreciate the help.

After I run my script I now get:

```

0;   Example Task;      Due Date: Fri, May 03, 2013
1;   Another example task;      Due Date: Fri, May 03, 2013
2;   Task3;      Due Date: Fri, May 03, 2013


```

Which is exactly what I asked for.  You truly do rock.
I was wondering if you could tell me how to remove the 0 1 and 2 at the beginning but keep the semi-colon?

---

### Post by papibe on 2013-05-03
I highlighted the parts that take care of the number:
```
awk '/\[ \]/ {**[COLOR="#FF0000"]n=$1[/COLOR]**; $1=$2=$3=""; printf("**[COLOR="#FF0000"]%s[/COLOR]**;%s; "**[COLOR="#FF0000"],n[/COLOR]**,$0); getline; print $0}'  file.txt
```
So if you get rid of that:
```
$ awk '/\[ \]/ {$1=$2=$3=""; printf(";%s; ",$0); getline; print $0}'  file.txt

;   Test Task;      Due Date: Fri, May 03, 2013
;   Another Test Task;      Due Date: Fri, May 03, 2013

```
Alternatively, you can also use this other version:
```
awk '/\[ \]/,gsub("^.*]","") {printf(";%s; ",$0); getline; print $0}'  file.txt
```

Let us know if you need more details to understand the code.
Regards.

---

### Post by GrouchyGaijin on 2013-05-03
Thank you.
Actually I have no understanding of what you did, but would really like to be able to do this without bothering people for help.
I'll check the awk man page, but often I simply don't understand the manual.

---

### Post by schragge on 2013-05-04
How about
```
awk -F'\n[ \t]*' -vRS='[0-9]+ *[[] []] *' -vOFS='; ' 'NR>1{print "",$1,$2}' file.txt
```
or even
```
awk -F\\n -vRS='[0-9]+ *[[] []]' 'NR>1,$0=";"$1";"$2' file.txt
```:?:

---

### Post by GrouchyGaijin on 2013-05-04
@Schragge  Thanks man, once again you come to my coding aid.

---

