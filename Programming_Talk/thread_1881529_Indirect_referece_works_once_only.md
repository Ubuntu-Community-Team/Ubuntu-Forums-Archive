---
title: "Indirect referece works once only"
date: 2011-11-15
forum: Programming Talk
---

### Post by rpaskudniak on 2011-11-15
Greetings, family.

I have recently started trying to use indirect references in ksh93. That is, when I set variable-b to the name of variable-a and obtain the value of variable-a by dereferencing variable-b.  (Sorta like pointers.)

I have been able to make it work but not in the manner I had expected.  I'm hoping someone can point out my flaw.

Let's start with my "control" script, where I have made no real effort to use the indirect reference.
```
 1 #!/bin/ksh
 2 #
 3 4 one=1
 5 two=2
 6 three=3
 7 four=4
 8 five=5
 9
10 for DIGIT in one two three four five
11 do
12   NUMBER=$DIGIT
14   echo $DIGIT ${NUMBER}
15 done
```
(The missing line numbers ar where I have removed commented code)
Here is the output of that:
> one one
two two
three three
four four
five five
This is very much as expected.

Now let's declare NUMBER to be an indirect reference:
```
 1 #!/bin/ksh
 2 #
 3 typeset -n NUMBER
 4 one=1
 5 two=2
 6 three=3
 7 four=4
 8 five=5
 9
10 for DIGIT in one two three four five
11 do
12   NUMBER=$DIGIT
14   echo $DIGIT ${NUMBER}
15 done
```
The output of this attempt is:
> one **[COLOR="Red"]1[/COLOR]**
two two
three three
four four
five five
Hey, it worked only the first time; after that it gave me the names I threw into it instead of chasing down the values behind those names.

OK, what happens if I repeat the typeset command each time around the loop.  If I do this I don't need to do it on line 3.  Here goes:
```
 1 #!/bin/ksh
 2 #
 3 #typeset -n NUMBER
 4 one=1
 5 two=2
 6 three=3
 7 four=4
 8 five=5
 9
10 for DIGIT in one two three four five
11 do
12   NUMBER=$DIGIT
13   typeset -n NUMBER=$DIGIT
14   echo $DIGIT ${NUMBER}
15 done
```
And the output of that is:
> one 1
two 2
three 3
four 4
five 5
AHA!  THAT'S the output I was looking for!  But it annoys me that I should need to repeat the typeset command for every new string name [of a variable] to which I set NUMBER.  It looks like one typeset declaration is not enough.

Is there some way I can use one typeset directive and have it last the duration of the script?

Thanks much for advice.  This will affect the nature of shell scripts I am planning.

---

### Post by crdlb on 2011-11-15
I don't know anything about ksh except what I just read in its manpage, but 'typeset -n' doesn't seem to work the way you think it does. As far as I can tell, it creates a permanent name reference.

```

#!/bin/ksh

typeset -n foo
foo=bar
# ^^ is equivalent to:
## typeset -n foo=bar
# also:
## nameref foo=bar

# after the initial binding, any assignment to foo
# will just change the value of bar
foo=7

echo "bar =" $bar # => 7
echo "foo refers to" ${!foo} # => bar


```

Perhaps 'eval' could be an alternative:```

eval NUMBER=$DIGIT
```

As I said, I'm not an expert; I try to avoid languages that end in 'sh'.

---

