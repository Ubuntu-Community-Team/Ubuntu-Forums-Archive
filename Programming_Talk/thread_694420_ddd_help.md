---
title: "ddd help"
date: 2008-02-12
forum: Programming Talk
---

### Post by rob21 on 2008-02-12
I am using C in Linux. While in the ddd debugger, whenever I click "Run" and the Run Dialogue Box appears, in the argument field I type "> file.in" which is the name of the file that has the data that I want to test. I get to the spot in my program that is causing a segmentation fault, however, all the data in my "file.in" is erased. What am I doing wrong?
                              thanks

---

### Post by lnostdal on 2008-02-12
hehe :) try this

```

lars@ibmr52:~/programming/clojure$ echo "this is a test" > test.tmp
lars@ibmr52:~/programming/clojure$ cat test.tmp
this is a test
lars@ibmr52:~/programming/clojure$ > test.tmp
lars@ibmr52:~/programming/clojure$ cat test.tmp
lars@ibmr52:~/programming/clojure$ 

```

edit:
ok, tbh .. i don't know if that is what is happening in your case .. just a thought .. you can use the gdb interface at the bottom of ddd and type in:

```

run file.in

```

also try typing in *help run* .. it's been a while since i used DDD, and at my end the "run arguments" dialog does not seem to pop up when i press run via the gui

---

