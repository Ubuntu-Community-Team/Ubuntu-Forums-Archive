---
title: "Bash if"
date: 2015-02-15
forum: Programming Talk
---

### Post by calzakk on 2015-02-15
Just wondering, anybody know the answer?

Why do you have to use 'then' with an 'if'?

```
if [ expression ]; then
  #do something
else
  #do something else
fi
```

What's the point of 'then'? Why isn't the following valid?

```
if [ expression ]
  #do something
else
  #do something else
fi
```

---

### Post by sudodus on 2015-02-15
The bash syntax was made like that. We may think it should not be like that, but so much is using bash, that it will probably not be changed.

---

### Post by ofnuts on 2015-02-15
> **calzakk said:**
> Just wondering, anybody know the answer?

Why do you have to use 'then' with an 'if'?

```
if [ expression ]; then
  #do something
else
  #do something else
fi
```

What's the point of 'then'? Why isn't the following valid?

```
if [ expression ]
  #do something
else
  #do something else
fi
```

There are penty of languages with an ilf/then/else syntax even if most languages created after C generally borrow some of their syntax from it and so are then-less.

---

### Post by calzakk on 2015-02-15
I thought there might be a genuine reason for it. No worries if not, I was just wondering.
It's obviously accepted and legacy, it's the way things are and cannot easily be changed!

---

### Post by ofnuts on 2015-02-15
> **calzakk said:**
> I thought there might be a genuine reason for it. No worries if not, I was just wondering.
It's obviously accepted and legacy, it's the way things are and cannot easily be changed!
It's not "legacy", it's "difference". In the 80s I saw a lot of programmers complaining about the strange C syntax...  I have even seen people recommending to use:
```

#define BEGIN  {
#define END }

```

---

### Post by SeijiSensei on 2015-02-15
You can replace
```

if [ something ]
then
   something else
fi

``` 
with
```
[ logical test ] && do_something
```
For instance,
```
[ "$(ls)" = "" ] && echo "Empty Directory!"
```
The spaces are important since they are delimiters in bash.

If you need more complex logicals with "elif", you'll need to use "then".

---

### Post by Vaphell on 2015-02-15
the reason for that is that you can have more than 1 expression after if and *then *is what makes the whole *if *expression unambiguous.
```
$ if true; true; true; then echo true; else echo false; fi
true
$ if true; true; false; then echo true; else echo false; fi
false
```

Last command decides the outcome.
Why is that the case with if in the first place i don't know. Maybe it's for consistency with other language constructs. The while loop follows the same principle (needs *do* to start the loop body) and there is a valid use case for multiple commands in it. That case would be reading from multiple files/process substitutions in parallel.

```
$ while read -u3 x; read -u4 y; do echo "x: $x, y: $y"; done 3< <( echo $'1\n2\n3' ) 4< <( echo $'2\n3' )
x: 1, y: 2
x: 2, y: 3
```

in this example fd 3 and fd 4 get assigned to commands constituting input and separate *reads *in the control portion of the loop access them. Note that the state of the loop is controlled by the status of the very last command, just like in case of if. Here $x should get 1 more value, but $y ran out of values to read and the loop ends.

---

### Post by Holger_Gehrke on 2015-02-16
> **calzakk said:**
> 
Why do you have to use 'then' with an 'if'?
```
if [ expression ]; then
  #do something
else
  #do something else
fi
```


The syntax for 'if' from 'man bash':
```

if list; then list; [ elif list; then list; ] ... [ else list; ] fi
```

The list (of commands) after 'then' is executed if the list (of commands) before it has an exit-status of '0' (No errors). The '[' in your example is just  a short form of the 'test' command. The 'then' is necessary so you (and the bash) can tell where the first list ends and the second begins.

---

### Post by calzakk on 2015-02-21
> **Vaphell said:**
> the reason for that is that you can have more than 1 expression after if and *then *is what makes the whole *if *expression unambiguous.
```
$ if true; true; true; then echo true; else echo false; fi
true
$ if true; true; false; then echo true; else echo false; fi
false
```

Last command decides the outcome.

Interesting, I didn't know you could do that! So 'then' does have a genuine purpose after all.

---

### Post by calzakk on 2015-02-21
> **SeijiSensei said:**
> You can replace
```

if [ something ]
then
   something else
fi

``` 
with
```
[ logical test ] && do_something
```

Again, this is interesting. I need to buy a book on shell scripting, I've obviously a lot to learn!

---

### Post by ofnuts on 2015-02-21
> **calzakk said:**
> Again, this is interesting. I need to buy a book on shell scripting, I've obviously a lot to learn!

This is based on the implementation of logical operators in bash (and in many other languages). The expression is evaluated left to right, and parts on the right aren't evaluated as soon as it can be determined that they cannot change the final result. So in a string of and's the evaluation stops when the current result is 0 and in a string of or's it ends when the current result is 1. Hence things like:
```

# if a file,  "-d $file" is false so evaluation continues with the echo  command,
# otherwise "-d $file" is true so evaluation stops there (true or anything is always true) and the  "echo" isn't executed.
[[ -d $file ]] || echo "$f is not a directory" 

# if a directory,  "-d $file" is true so evaluation continues with the echo  command,
# otherwise "-d $file" is false so evaluation stops there (false and anything is always false) and the  "echo" isn't executed.
[[ -d $file ]] && echo "$f Is a directory"  

```

---

### Post by Vaphell on 2015-02-22
yep, boolean logic shortcircuiting implemented in many languages depends on the fact that in specific cases you can tell the result right off the bat.

TRUE/SUCCESS OR ??? = TRUE
FALSE/FAILURE AND ??? = FALSE

in both cases ??? can be omitted because it doesn't influence the outcome so that can be exploited to create a 'perform only if' mechanism

It's very similar to math operations on non-negative numbers where you have only 2 logical categories: 0 and non-0
0 * whatever is 0 (case of FALSE AND)
non-0 + whatever is non-zero (case of TRUE OR)

you could say that AND/multiplication is non-increasing (stay the same or go down), so if you start with the lowest possible value you are guaranteed to end up with it. Same with OR/addition - it's non-decreasing (stay the same or go up) so if you start with the greatest value, you are guaranteed to have it as a final result.


1 here stands for non-0
```
1 * 1 * 1 * 1 * 0 * 1 * 0 * 0 * ....
   =1  =1  =1  =0 lowest possible value, not going to change in pure multiplication/AND-ing
   
0 + 0 + 0 + 1 + 0 + 0 + 1 + 1 + ....
   =0  =0  =1 highest possible value, not going to change in pure addition/OR-ing
```

---

