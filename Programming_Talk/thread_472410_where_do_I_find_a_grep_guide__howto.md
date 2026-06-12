---
title: "where do I find a grep guide / howto"
date: 2007-06-13
forum: Programming Talk
---

### Post by vadania on 2007-06-13
This seemed the best place to put a CLI question:

Where can I find an easy to read grep guide? (not man pages, please!). Some reg exp info would be nice, too! For example, i have lots of entries in a directory and I do *ls -l* in that dir. How do I filter the results by file/directory name?

I guess it would be something like this:
*ls -l | grep something*

What exactly is that something? What options should I put there?
This is a simple example and I want to start learning about grep, but man pages seemed not to be the best start. I would like something like a wiki, because documentation there is usually formated (bold, italic, code, headlines, bullets) and therefore easier for me to read.

-- By the way, grep filters lists by using regular expressions, right?

---

### Post by diatribe on 2007-06-13
[http://en.wikipedia.org/wiki/Grep](http://en.wikipedia.org/wiki/Grep)
[http://www.gnu.org/software/grep/doc/grep_13.html#SEC13](http://www.gnu.org/software/grep/doc/grep_13.html#SEC13)

---

### Post by finer recliner on 2007-06-13
yes grep uses regular expressions. in fact, thats what the r and e in grep stands for ;)

i like this site for lots of different examples:
[http://tldp.org/LDP/abs/html/string-manipulation.html](http://tldp.org/LDP/abs/html/string-manipulation.html)

for a very quick intro:
say you are in a directory with lots of different files. and say you want to view only the jpeg files in that directory. you could do:
```
$ls | grep *.jpg
```
ls is the keyword to list files in a directory
| (pipe) is the keyword to take the output from the command on the left and turn it into input for the command on the right.
grep is the command to search for specific patterns in strings
* is a regex symbol meaning wildcard. it will match to any string
so when we use *.jpg we are looking for any string that ends in a .jpg

hope this helps

---

### Post by FuturePast on 2007-06-13
> **finer recliner said:**
> 
```
$ls | grep *.jpg
```

I hate to be pedantic but that example would not work and should rather be
```
$ ls|grep ".*\.jpg"

#or easier still

$ ls|grep jpg
```

---

