---
title: "Any way to use this awk command with shell variables?"
date: 2010-07-29
forum: Programming Talk
---

### Post by alphaniner on 2010-07-29
I came across this awk command for printing the contents of a text file between two strings:

```
awk '/START/{flag=1;next} /END/{flag=0} flag {print}' file
```

But I can't figure out how to make it work with a shell variable.  Actually, one variable as part of two different strings, 'name="${Dir}"' and '<!--END${Dir}-->'.  A sed command does essentially the same thing, the actual command I'm using being

```
sed -e "1,/name=\"${Dir}\"/d" -e "/<.--END${Dir}-->/,\$d"
```

but this doesn't work if the 'start' line if the first line of the file.  I have no idea why.

---

### Post by gmargo on 2010-07-29
You can build the awk command in stages.  Example:
```

#!/bin/sh

# awk '/START/{flag=1;next} /END/{flag=0} flag {print}' input1.txt 

Dir="/this/is/dir"

#name="/this/is/dir"
#<!--END/this/is/dir-->

pat1="name=\"${Dir}\""
pat2="<!--END${Dir}-->"

echo pat1=$pat1
echo pat2=$pat2

# escape the forward slashes in patterns
pat1p=$(echo $pat1 | sed 's?/?\\/?g')
pat2p=$(echo $pat2 | sed 's?/?\\/?g')
echo pat1p=$pat1p
echo pat2p=$pat2p

awktext="/${pat1p}/{flag=1;next} /${pat2p}/{flag=0} flag {print}"

echo awktext=$awktext

awk "$awktext" input2.txt

```

---

### Post by alphaniner on 2010-07-29
Thanks, it worked prefectly.  I didn't know you could use variables in that way.

---

### Post by ghostdog74 on 2010-07-29
the "awk" way to pass shell variable to awk is using its -v option

```

shellvar="something"
awk -v var="$shellvar" '$0 ~ var{print}' file

```

this way, there is no messy single/double quotes and your commands look neater. Add more -v if required.

---

### Post by alphaniner on 2010-07-30
> **ghostdog74 said:**
> the "awk" way to pass shell variable to awk is using its -v option

```

shellvar="something"
awk -v var="$shellvar" '$0 ~ var{print}' file

```

this way, there is no messy single/double quotes and your commands look neater. Add more -v if required.

I tried that method and also something like this:

```
awk '{print v1, v2}' v1=$VAR1 v2=$VAR2 input_file
```

but couldn't get either of them to work.

---

### Post by ghostdog74 on 2010-07-30
its -v, ie
```

awk  ..... -v v1="$var1" 

```
look at the awk usage man page (or the one in my sig) for correct syntax!

---

### Post by alphaniner on 2010-08-02
> **ghostdog74 said:**
> its -v, ie
```

awk  ..... -v v1="$var1" 

```
look at the awk usage man page (or the one in my sig) for correct syntax!

```
$ awk '/ex2/{flag=1;next} /old/{flag=0} flag {print}' file
index3.html
index.html
la
makepage0.sh
makepage2.sh
makepage.sh
$ A=ex2;B=old
$ awk -v v1="$A" -v v2="$B" '/v1/{flag=1;next} /v2/{flag=0} flag {print}' file
$ awk -v v1=ex2 -v v2=old '/v1/{flag=1;next} /v2/{flag=0} flag {print}' file
$ awk '/v1/{flag=1;next} /v2/{flag=0} flag {print}' file -v v1="$A" -v v2="$B"
awk: cannot open -v (No such file or directory)
$ awk '/v1/{flag=1;next} /v2/{flag=0} flag {print}' -v v1="$A" -v v2="$B" file
awk: cannot open -v (No such file or directory)
$ awk '/v1/{flag=1;next} /v2/{flag=0} flag {print}' v1="$A" v2="$B" file
$

```

I tried it all again in case I had done something wrong, but again no workey.  The variables at the end method came from [tek-tips]("http://www.tek-tips.com/faqs.cfm?fid=1281").

---

### Post by ghostdog74 on 2010-08-02
> **alphaniner said:**
> ```
$ awk '/ex2/{flag=1;next} /old/{flag=0} flag {print}' file
index3.html
index.html
la
makepage0.sh
makepage2.sh
makepage.sh
$ A=ex2;B=old
$ awk -v v1="$A" -v v2="$B" '/v1/{flag=1;next} /v2/{flag=0} flag {print}' file
$ awk -v v1=ex2 -v v2=old '/v1/{flag=1;next} /v2/{flag=0} flag {print}' file
$ awk '/v1/{flag=1;next} /v2/{flag=0} flag {print}' file -v v1="$A" -v v2="$B"
awk: cannot open -v (No such file or directory)
$ awk '/v1/{flag=1;next} /v2/{flag=0} flag {print}' -v v1="$A" -v v2="$B" file
awk: cannot open -v (No such file or directory)
$ awk '/v1/{flag=1;next} /v2/{flag=0} flag {print}' v1="$A" v2="$B" file
$

```

I tried it all again in case I had done something wrong, but again no workey.  The variables at the end method came from [tek-tips]("http://www.tek-tips.com/faqs.cfm?fid=1281").

when you pass in a variable from shell, and when you have /v1/, this tells awk to find the string "v1" , not the variable v1. To search for string stored in variable v1, you use ~

```

awk '$0 ~ v1 { print "..." }' file

```

---

### Post by alphaniner on 2010-08-02
> **ghostdog74 said:**
> when you pass in a variable from shell, and when you have /v1/, this tells awk to find the string "v1" , not the variable v1. To search for string stored in variable v1, you use ~

```

awk '$0 ~ v1 { print "..." }' file

```

I think I'm starting to get it now.  The following works:
```
awk -v v1="$A" -v v2="$B" '$0 ~ v1{flag=1;next} $1 ~ v2{flag=0} flag {print}' file
```

Is that the proper way to do it?  In any case, thanks for the help!

---

### Post by ghostdog74 on 2010-08-02
> **alphaniner said:**
> 
Is that the proper way to do it?  
yes.

---

