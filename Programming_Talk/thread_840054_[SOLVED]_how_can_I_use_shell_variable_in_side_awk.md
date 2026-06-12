---
title: "[SOLVED] how can I use shell variable in side awk"
date: 2008-06-25
forum: Programming Talk
---

### Post by brijith on 2008-06-25
Hai,


How can I use A shell variable in side an awk when I use AWK in side a shell script. Is it possible? If it is can you give a simple example that shows how it can be..



**[COLOR="Red"]Thanks [/COLOR]**

---

### Post by geirha on 2008-06-25
You generally don't want to do that. Perhaps if you give some example code, someone will find a better solution for it.

I'll try to explain why your variables don't work as expected though. Bash treats the quotes '' and "" differently. The single-quotes '' are called hardquotes, bash treats everything inside it as text, and will not replace variables with their values. The double-quotes "" are called soft quotes. Bash treats some parts of it as code, including variables. That means, that whenever you use a symbol in your awk, that bash may interpret instead, you need to escape it with a \.

```
$ word=world
$ echo hello | awk '{ print $1,$word; }'  # Both are treated as awk variables, so it 
                                          # won't work

$ echo hello | awk "{ print $1,$word; }"  # Both are treated as bash variables, so $1 
                                          # will not be hello, and it will fail if $1 
                                          # is empty or unset.

$ echo hello | awk "{ print \$1,$word; }" # Since the $ in \$1 is escaped, bash 
                                          # will change it to $1 and leave it alone 
                                          # for awk to interpret. $word is replaced by 
                                          # bash, with $word's value.

```

Try doing it a different way and you might save yourself from a lot of headaches.

---

### Post by ghostdog74 on 2008-06-25
sure. you can pass your shell variable into awk using -v option
```

myvar="something"
awk -v var="$myvar" '{ print var }' file

```

---

### Post by geirha on 2008-06-25
Right, and if I had just waited for ghostdog74 to come around with an elegant solution, I could've saved me the trouble of explaining why my bad solution is bad. Ignore my previous post ;)

---

### Post by ghostdog74 on 2008-06-25
actually,  without -v option
```

# var="help"
# awk 'BEGIN{print "'$var'" }'
help

```
just a bit extra quoting.

---

### Post by brijith on 2008-06-25
Hi,


Another Doubt, How can I use **cut** on a shell variable.

```
str="mac:maya"

cat -d: -f1 $str            # does not works 
`echo "$str" | cat -d: -f1` # does not works 

```

**Please help!!**

**[COLOR="Red"]Thanks[/COLOR]**

---

### Post by ghostdog74 on 2008-06-25
first , get your spelling correct and secondly, you don't need the backticks
```

str="mac:maya"
echo "$str" | <get_your_spelling_correct> -d: -f1

```
lastly, you can also use awk
```

echo "$str" | awk -F":" '{print $1}'

```

---

### Post by dtmilano on 2008-06-25
This also works and you don't have to explicitily define every variable on the command line
> $ export A=A
$ awk END {print ENVIRON["A"]} < /dev/null

---

### Post by brijith on 2008-06-25
```
#!/bin/bash
usernames="brijith"
lst=`awk -v user="$usernames" -F: 'BEGIN {OFS=":"};user==$1 {print $3,$4}' /etc/passwd`
uid=echo "$str" | cut -d: -f1
gid=echo "$str" | cut -d: -f2
echo "$usernames -- $uid $gid"
```

Above Scripts Does Not Work Can you Correct it?  What I need is the **uid** and **gid** of the given user. In two shell variable.

---

### Post by geirha on 2008-06-25
```
uid=`grep ^$username: /etc/passwd | cut -d: -f3`
gid=`grep ^$username: /etc/passwd | cut -d: -f4`
uid=`id -u $username`
gid=`id -g $username`

```

---

### Post by ghostdog74 on 2008-06-25
> **brijith said:**
> ```
#!/bin/bash
usernames="brijith"
lst=`awk -v user="$usernames" -F: 'BEGIN {OFS=":"};user==$1 {print $3,$4}' /etc/passwd`
uid=echo "$str" | cut -d: -f1
gid=echo "$str" | cut -d: -f2
echo "$usernames -- $uid $gid"
```

Above Scripts Does Not Work Can you Correct it?  What I need is the **uid** and **gid** of the given user. In two shell variable.
firstly, where does "$str" comes from. anyway, unless your requirement is more complicated, just do it in awk.
```

awk  'BEGIN { user="user2"; FS=":"}
$1==user { print "uid: " $3, "gid: "$4}
' /etc/passwd


```

---

### Post by brijith on 2008-06-25
Hi,
Me again with another issue  :)

```
for files in `find <some_folder_name> -name "*"`; do
		echo "File Name $files"
done 

```

The above code works Perfectly if there is no space in file name and directory names in the searching folder -**<some_folder_name>**-. But it fails if there is space in the file name or folder names.  

I hope you understood what I said.  How to solve this issue ?

**[COLOR="Red"]Thanks[/COLOR]**

---

### Post by ghostdog74 on 2008-06-25
> **brijith said:**
> Hi,
Me again with another issue  :)

```
for files in `find <some_folder_name> -name "*"`; do
		echo "File Name $files"
done 

```

The above code works Perfectly if there is no space in file name and directory names in the searching folder -**<some_folder_name>**-. But it fails if there is space in the file name or folder names.  

I hope you understood what I said.  How to solve this issue ?

**[COLOR="Red"]Thanks[/COLOR]**

use a while loop and quote your variables!
```

find <some_folder_name> -name "*" | while read FILE
do
 echo "$FILE"
done


```

---

