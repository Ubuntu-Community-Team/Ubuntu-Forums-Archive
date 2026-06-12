---
title: "Bash Script - Variable Not Recognized"
date: 2008-02-10
forum: Programming Talk
---

### Post by Gen2ly on 2008-02-10
I am learning about making a bash script and need help.  The script I did includes a couple variables but are being printed verbatim (i.e. unprocessed):

```
#!/bin/bash

# Creates an invisible link - good for post ownership.

currentdate=$(date +"%Y/%m/%d")

echo "Enter Name of Post:"
read name

echo '<a href="http://linuxtidbits.wordpress.com/$currentdate/$name/>&nbsp</a>"' | sed 's/[ \t]/-/g' | sed 's/\(.*\)/\L\1/'
```

This outputs:
```
<a-href="http://linuxtidbits.wordpress.com/$currentdate/$name/>&nbsp</a>"
```

How can I get the variable $currentdate and variable $name to be processed correctly ?

---

### Post by yabbadabbadont on 2008-02-10
```
echo '<a href="http://linuxtidbits.wordpress.com/'$currentdate/$name'/>&nbsp</a>"' | sed 's/[ \t]/-/g' | sed 's/\(.*\)/\L\1/'
```

```
/home/daffy/temp $ cat go.sh 
#!/bin/bash

# Creates an invisible link - good for post ownership.

currentdate=$(date +"%Y/%m/%d")

echo "Enter Name of Post:"
read name

echo '<a href="http://linuxtidbits.wordpress.com/'$currentdate/$name'/>&nbsp</a>"' | sed 's/[ \t]/-/g' | sed 's/\(.*\)/\L\1/'
/home/daffy/temp $ ./go.sh 
Enter Name of Post:
test
<a-href="http://linuxtidbits.wordpress.com/2008/02/09/test/>&nbsp</a>"

```
:D

---

### Post by Gen2ly on 2008-02-10
definitely humbled, very nice.

I think your saying

the file temp will put this value in.

Itsn't there better ... way to do it?

---

### Post by Gen2ly on 2008-02-10
refuses to work anyhow.

---

### Post by yabbadabbadont on 2008-02-10
I just cut and pasted from the terminal window.  That output includes the command prompts....  you didn't use them in your code did you?  ;)

---

### Post by Gen2ly on 2008-02-10
Oh thats pretty clever.  Just noticed the '' around the variables.  thanks alot.

---

### Post by ghostdog74 on 2008-02-10
> **Dirk.R.Gently said:**
> 

echo '<a href="http://linuxtidbits.wordpress.com/$currentdate/$name/>&nbsp</a>"' | sed 's/[ \t]/-/g' | sed 's/\(.*\)/\L\1/'[/CODE]


```

echo "<a href=\"http://linuxtidbits.wordpress.com/$currentdate/$name/>&nbsp</a>\"" | sed 's/[ \t]/-/g' | sed 's/\(.*\)/\L\1/

```

---

