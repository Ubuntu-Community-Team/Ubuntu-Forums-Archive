---
title: "dialog --menu and external data"
date: 2009-09-07
forum: Programming Talk
---

### Post by Noccy on 2009-09-07
I've been looking and looking and I just can't seem to find an answer to this problem.

I'm trying to invoke "dialog --menu" with an external dataset. For example, I wrote a quick bash function that lists the directories in the "./data/" dir, and concatenates that with the contents of the ".description" file found in each of the subdirectories, rendering something like:

```
"foo" "description for foo" "bar" "description for bar" "baz" "description for baz"
```

However, I can't seem to be able to feed that data into the dialog tool; I always end up with a menu that looks like:

```
"foo" "description
for foo"
"bar" "description
for bar"
...
```

...or an error about the parameter count mismatch. I've tried dumping it all into a variable and feeding that, calling it using the backticks (`), etc. but to no avail.

I'm trying to set up an automated postinstall script that installs and configures USB 3G modems for wireless broadband. I have already got all the configuration files and tools needed to get them working, but I don't want to embed the menu statically in the script.

Thanks in advance :)

---

### Post by DaithiF on 2009-09-07
Hi, 
this seems to work for me:
for a structure like this:
```
./foo
./foo/.description
./bar
./bar/.description

```

```
args=$(for d in *; do echo \"$d\" \"$(cat $d/.description)\"; done | tr '\n' ' ' )
echo $args
"bar" "description for bar" "foo" "description for foo"
echo $args | xargs dialog --menu "please choose" 10 80 5   
```

---

### Post by Noccy on 2009-09-07
> **DaithiF said:**
> Hi, 
this seems to work for me:

Thank you! xargs seem to have been the missing link there :) You learn something new every day :D

Chris

---

