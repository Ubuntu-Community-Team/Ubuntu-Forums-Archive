---
title: "bash: what do these parentheses mean?"
date: 2009-08-17
forum: Programming Talk
---

### Post by PGScooter on 2009-08-17
Hi,

I would like to understand the following code better:
```
diff <(du -ab | sort) <(du -ab directory2 | sort)
```
(source url) [http://ubuntuforums.org/showthread.php?t=883491](http://ubuntuforums.org/showthread.php?t=883491)

Is there a name for the function that the parentheses accomplish?

My interpretation is that the parentheses act as a substitute for where normally a filename would be. Is there a place I can read more about these parentheses and double <'s ?

Thanks.

---

### Post by djbushido on 2009-08-17
The parentheses I believe act as an execution point - meaning that bash executes the command in parentheses - "du" stands for disk usage - and then substitutes that in. So what this is doing is comparing the disk usage of two directories. not specifying a directory in the first section (du -ab) means that it uses the current directory.
Correct me if I'm wrong, but I'm relatively confident that I'm not.

---

### Post by supirman on 2009-08-17
Normally, commands within parentheses execute within a [subshell]("http://tldp.org/LDP/abs/html/subshells.html").  The < signs are [input redirection]("http://tldp.org/LDP/abs/html/io-redirection.html").  In this example, these are combined into what is known as [process substitution]("http://tldp.org/LDP/abs/html/process-sub.html").  

For a good source of information on bash scripts, see the [The Advanced Bash Scripting Guide]("http://tldp.org/LDP/abs/html/").

---

