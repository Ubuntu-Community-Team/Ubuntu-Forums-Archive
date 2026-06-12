---
title: "Help with replacing multiple strings."
date: 2012-02-18
forum: Programming Talk
---

### Post by shymega on 2012-02-18
Hi,

I'm trying to replace strings in a HTML Template and replace them with pre-defined variables. 

I have tried sed but it just leaves the file as it was.

I am using BASH.

Thanks,
sm

---

### Post by r-senior on 2012-02-18
> **shymega said:**
> I have tried sed but it just leaves the file as it was.
Sed is a stream editor - it edits a stream as it passes through. So you usually need something like:

```
sed -e 's/who/how/g' < infile.txt > outfile.txt
```

---

### Post by shymega on 2012-02-18
I've just tried that - It still leaves the file as it was.

I'm aiming to replace a word (traffic, client and health) with a variable in my script. I've modified that sed command that you posted so it looks like this:
```

sed -e 's/traffic/'$TRAF'/g' < templatestatus.html > status.html

```

Thanks for the input.

--
sm

---

### Post by r-senior on 2012-02-18
Could you demonstrate your problem with short, sample files and show the commands you are entering and the result you get?

---

### Post by shymega on 2012-02-18
Here is the output of my sample commands:

```


Terminal> TRAF='111'
Terminal> touch status
Terminal> nano status
Terminal> sed -e 's/traffic/'$TRAF'/g' < templatestatus.html > status.html
Terminal> cat status
traffic
Terminal>


```

---

### Post by josephmills on 2012-02-18
> **shymega said:**
> Here is the output of my sample commands:

```


Terminal> TRAF='111'
Terminal> touch status
Terminal> nano status
Terminal> sed -e 's/traffic/'$TRAF'/g' < templatestatus.html > status.html
Terminal> cat status
traffic
Terminal>


```

Terminal> TRAF="111"
Terminal> touch status
Terminal> nano status
Terminal> sed -e 's/traffic/$TRAF/g'  templatestatus.html  status.html
Terminal> cat status
traffic
Terminal>

or 
```
#!usr/bin/env bash
clear
error="something went wrong"
TRAF="111";
touch status;
nano status;
if
sed -e 's|traffic|$TRAF|g'  templatestatus.html  status.html
then 
echo "your file name has been changed"
else 
echo "$error" 
fi

```

---

### Post by shymega on 2012-02-18
Thank you very much josephmills, it's working now.

I really appreciate it.

By the way, I +1'ed your thread for Ubuntu Membership.

--
sm

---

