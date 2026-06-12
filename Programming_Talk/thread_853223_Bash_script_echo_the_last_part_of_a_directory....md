---
title: "Bash script: echo the last part of a directory..."
date: 2008-07-08
forum: Programming Talk
---

### Post by richjoyce on 2008-07-08
Ok thats a bad subject, can't really explain in one line.

I have a script that runs a loop like this:

find . -type d | grep foobar$ | while read dir  ## Get a list of directories that end in foobar

inside the loop I want to print only the LAST part of the directory, right now its a big long directory from the root like this : /foo/bar/other/stuff/mystuff.foobar

how can I get it to print only mystuff.foobar??

I think this can be done with awk, but i can't figure it out...

Can anyone help?
Thanks.

---

### Post by skelooth on 2008-07-08
bash has a pattern matching utility.

* I FORGET THE EXACT SYNTAX * so if this doesn't work, just do a quick google search.

${variable##*/}

bash pattern matching returns whatever it DOESN'T match.

# starts from left
## from left and greedy
% from right
%% and greedy

Again, double check the syntax because I'm rusty.

---

### Post by gnusci on 2008-07-08
use **tail** with the option **-n** and then the number of lines you want to print

**> cat file | tail -n 20**

this example print the last 20 lines.

---

### Post by Martin Witte on 2008-07-08
> **skelooth said:**
> bash has a pattern matching utility.

* I FORGET THE EXACT SYNTAX * so if this doesn't work, just do a quick google search.

${variable##*/}
Almost right:
```
martin@sony:~$ echo $HOME
/home/martin
martin@sony:~$ echo ${HOME##/*/}
martin
martin@sony:~$ 

```
see [this ]("http://www.unix.com.ua/orelly/unix/ksh/ch04_03.htm#KSH-CH-4-SECT-3.3") for explanation

---

### Post by WW on 2008-07-08
Try this:
```

find . -type d -name '*foobar' -exec basename '{}' ';'

```
For example,
```

$ ls
Afoobar/     Bfoobar/     foobar.d/    junk/        junk.foobar  obar/
$ find . -type d -name '*foobar' -exec basename '{}' ';'
Afoobar
Bfoobar
$

```


EDIT: Replace
**-exec basename '{}' ';'**
with
**-printf '%f\n'**
Same result, but more efficient.
Thanks, ghostdog74!

---

### Post by ghostdog74 on 2008-07-08
if you are just going to get the file name (no matter what directory it resides) , just give the -name option to find and use printf (GNU find)
```

find . -name "*foobar" -printf "%f\n"

```

---

### Post by ghostdog74 on 2008-07-08
> **gnusci said:**
> use **tail** with the option **-n** and then the number of lines you want to print

**> cat file | tail -n 20**

this example print the last 20 lines.
think its not what OP required. anyway, UUOC
```

tail -n 20 file

```

---

### Post by richjoyce on 2008-07-08
Thanks skeeloth and Martin Witte, that works perfectly for my script!

---

