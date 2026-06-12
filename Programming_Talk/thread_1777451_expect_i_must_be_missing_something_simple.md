---
title: "expect: i must be missing something simple"
date: 2011-06-07
forum: Programming Talk
---

### Post by decoherence on 2011-06-07
For various reasons, I need to run expect from within a shell script.

I've simplified the problem down to a short, contrived example. I need the following to print 'yoohoooooo'

```
#!/bin/sh

myhostname="yoohoooooo"
export myhostname
/usr/bin/expect << EOF 
puts $env(myhostname)
EOF

```

but I get 

(myhostname)

thanks for any suggestions! i know nothing about tcl or expect but i've seen various examples where the above supposedly works.

ADD: I should note that this works if it is just a straight expect script.... so any tips on reading those variables in to the expect portion of the shell script? thanks

ADD2: i seemed to have solved it

```
[code]#!/bin/sh

myhostname="yoohoooooo"
/usr/bin/expect << EOF 
puts $myhostname
EOF

```

as usual, making things more complicated than they need to be...

---

