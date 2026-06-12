---
title: "Problem with AWK"
date: 2008-06-17
forum: Programming Talk
---

### Post by sridhar_423 on 2008-06-17
Hi all,

I have a problem with awk. I'm not able to figure where I'm doing wrong
I have the absolute path of a file stored in a variable. Now, I want to parse only the path and not the file name from the variable.
e.g. string=/home/exp/fms/temp.txt
I want to retrieve the path i.e. /home/exp/fms/

I tried the below command without any luck
```
 echo $string | awk -F"/" 'c="";{for(i=1;i<NF;i++)c+="/"+$i;print c}'
Output: 0
```

i tried the below command also.. Output is blank in this case
```
 echo $string | awk -F"/" 'BEGIN{for(i=1;i<NF;i++) if($i!="")c+="/"+$i}END {print c}'
Output: 
```

Can anyone help me with this

Thanks
Sridhar

---

### Post by ghostdog74 on 2008-06-17
```

echo $string | awk -F"/" '{$NF=""}1' OFS="/"

```

---

### Post by sridhar_423 on 2008-06-17
great.. works like a charm... I have been banging my head on this

Thanks a lot

---

### Post by sridhar_423 on 2008-06-17
I'll read more on awk and try to understand the command you have provided.
But, I would like to know why the command I specified above didn't work.
Can you briefly explain why it failed (If its not difficult for you to explain it)

thanks a lot
Sridhar

---

### Post by ghostdog74 on 2008-06-17
the  "+" sign in awk is the addition operator. To concatenate strings, just don't specify anything. 
```

echo $string | awk -F"/" '{for(i=2;i<NF;i++)c=c"/"$i;print c}'

```

---

### Post by risby on 2008-06-17
> **sridhar_423 said:**
> 
```
 echo $string | awk -F"/" 'c="";{for(i=1;i<NF;i++)c+="/"+$i;print c}'
Output: 0
```i tried the below command also.. Output is blank in this case
```
 echo $string | awk -F"/" 'BEGIN{for(i=1;i<NF;i++) if($i!="")c+="/"+$i}END {print c}'
Output: 
```Can anyone help me with this


You are using an arithmetic operator "+" on the strings.

In awk strings are concatenated simply by putting them in sequence:
```

echo $string | awk -F/ '{for(i=1;i<NF;i++)c=c $i "/";print c}'

```NB The field separator being the first character means to awk that the first field is null so I've appended the slash in my solution

Ah, I see I've been beaten to it.

---

### Post by sridhar_423 on 2008-06-17
ghostdog & risby

thanks a lot for the explanation. :-)

---

### Post by sridhar_423 on 2008-06-30
The commands given above worked on HP-UX Os.. but they're failing on SunOS.
Any idea? 

It would be very helpful if anyone can provide me with a link which will explain me the command that ghostdog74 has written. That 1 after $NF="" is the biggest mystery for me..

Thanks,
Sridhar

---

### Post by geirha on 2008-06-30
In case you are not aware, there's a common command that will do this for you.
```

$ dirname /var/tmp/foo.txt
/var/tmp
$ basename /var/tmp/foo.txt
foo.txt

```

---

### Post by ghostdog74 on 2008-06-30
> **sridhar_423 said:**
> The commands given above worked on HP-UX Os.. but they're failing on SunOS.
Any idea? 

It would be very helpful if anyone can provide me with a link which will explain me the command that ghostdog74 has written. That 1 after $NF="" is the biggest mystery for me..

Thanks,
Sridhar

use nawk on Solaris. Read the Gawk manual if you are free.

---

### Post by ghostdog74 on 2008-06-30
> **geirha said:**
> In case you are not aware, there's a common command that will do this for you.
```

$ dirname /var/tmp/foo.txt
/var/tmp
$ basename /var/tmp/foo.txt
foo.txt

```

there's even no need to use any outside tools if OP is in bash.
I am sure you know about substrings :).  
```

a=/home/1/2/file
# echo ${a%/*}
/home/1/2

```

---

