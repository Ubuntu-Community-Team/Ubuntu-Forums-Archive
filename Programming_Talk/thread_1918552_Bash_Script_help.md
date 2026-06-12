---
title: "Bash Script help"
date: 2012-02-01
forum: Programming Talk
---

### Post by [Renegade] on 2012-02-01
Hi, 

I'm looking for some help with doing the following with a BASH script:

> If some files in f2, ..., fn are not regular files, then print an error message to STDERR at the end,
displaying each missing file at once. For example, if files foo1 and foo2 are missing, print
``ERROR: missing files foo1, foo2''.

Here is my attempt:

```

for i in "$@"; do
  if ![ -f $i ]; then
    NON_REG="${NON_REG}${i}"
  fi
done
  echo -n "ERROR: missing files "$NON_REG""

```

Can anybody suggest where the problem may be?

---

### Post by Vaphell on 2012-02-01
[ ... ] is not a kind of ordinary parentheses, it's an equivalent of *test ... <end marker>* and because of that it requires separating spaces everywhere. Shell in general is very sensitive to lacking or excessive spaces.
Besides why have that ! outside when you can put it inside?

```
$ if ! [ 'a' = 'a' ]; then echo TRUE; else echo FALSE; fi
FALSE
$ if ![ 'a' = 'a' ]; then echo TRUE; else echo FALSE; fi
if [ 0 0.24 0.24 0 18 18] concat 'a' = 'a' ]; then echo TRUE; else echo FALSE; fi
bash: [: too many arguments
$ if [ ! 'a' = 'a' ]; then echo TRUE; else echo FALSE; fi
FALSE
```

---

### Post by Lars Noodén on 2012-02-01
> **Vaphell said:**
> [ ... ] is not a kind of ordinary parentheses, it's an equivalent of *test ... <end marker>* 

Just a note of interest, you can see it with the following:

```

ls -l /usr/bin/\[

```

---

### Post by sisco311 on 2012-02-01
On a second note, /usr/bin/[ (**man 1 test**) and the [ (**help test** and **help [**) BASH builtin aren't the same commands. ;)

@OP: You also forget to redirect the output of echo to STDERR. See: 
[http://wiki.bash-hackers.org/howto/redirection_tutorial](http://wiki.bash-hackers.org/howto/redirection_tutorial)
[http://mywiki.wooledge.org/BashGuide/InputAndOutput#Redirection](http://mywiki.wooledge.org/BashGuide/InputAndOutput#Redirection)

BashFAQ 055 (link in my signature) and

[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals#Conditional_Blocks_.28if.2C_test_and_.5B.5B.29)

---

