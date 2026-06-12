---
title: "Shell String Operations"
date: 2008-05-05
forum: Programming Talk
---

### Post by omrsafetyo on 2008-05-05
I am trying to use the following substring expression:
```

${string:position:length}

```
Except that I am trying to pass a variable as the length, and I can't quite figure out how to do it.  Instead I get an error message:
```

sub1=${name1:1:${lffn}}: 0403-011 The specified substitution is not valid for this command.

```

Anyone know if this is possible, and how to do it?

Many thanks.

---

### Post by omrsafetyo on 2008-05-05
Solved:

```
 sub1=`expr substr $name1 1 $lffn`
```

---

### Post by WW on 2008-05-05
I just tried a simple version of this, and it worked.  Are you sure $lffn is a correct length?  Are you sure you are using *bash*?

In the following I created a short script with no #! in the first line. I'll run the script with bash and with sh:
```

$ [color=blue]cat strtest.sh[/color] 
name1=1234567890
p=4
sub1=${name1:0:${p}}
echo $sub1
$ [color=blue]bash strtest.sh[/color] 
1234
$ [color=blue]sh strtest.sh[/color] 
strtest.sh: 3: Syntax error: Bad substitution
$ 

```

---

### Post by omrsafetyo on 2008-05-06
I'm actually using ksh - and the man pages I have available locally did not address string substitution at all.

As soon as I substituted my second expression it worked.  I was also echoing all variables at this point, as I usually do when building a script - so I am quite sure that the variable was the correct length.

---

