---
title: "BASH: variables auto-round numbers to nearest whole!?"
date: 2007-11-29
forum: Programming Talk
---

### Post by ryanVickers on 2007-11-29
apparently, this command, which it is very crucial has the ability to use decimals, rounds everything to the nearest whole (1, 2, 3, etc.) ```
test_number=$(($prime_number/$current_number));
```

any idea of a better way to set the variable "test_number" to be the quotient of "prime_number" and "current_number"?

---

### Post by hod139 on 2007-11-29
There's no floating point math in bash.  See [FAQ 22]("http://wooledge.org:8000/BashFAQ#head-a0a7db50634591d972c13ac2b890f4f297c1fe74"): [http://wooledge.org:8000/BashFAQ](http://wooledge.org:8000/BashFAQ)

---

### Post by ryanVickers on 2007-11-29
ok, I"ll see what I can do with that! :p

---

### Post by meatpan on 2007-11-29
> **ryanVickers said:**
> 
any idea of a better way to set the variable "test_number" to be the quotient of "prime_number" and "current_number"?

The 'bc' program is a useful calculator that is fairly easy to use in scripts.  In the example above, I think you can achieve the desired behavior with:

```

test_number=$(echo scale=3\; $prime_number '/' $current_number | bc) 

```

From the outside-in, the $(..) is for command substitution.  You could also use backtiks, but they get confused with apostrophes on the forums ;) 

The 'echo scale=3\;' is kind of ugly, but necessary so bc will print a decimal precision of 3.  $prime_number '/' $current_number are operator/operands for bc.  Everything is piped to bc.  The return is saved in test_number.


Another solution is using an inline awk statement, which might be a better choice if your equation gets more complex (or you want to make sure $current_number != 0).


EDIT:  The FAQ link posted by hod139 gives a *much* better explanation of what I have tried to say.

---

### Post by ryanVickers on 2007-11-30
no, this post was much more useful, thanks :p
I couldn't make heads or tails of how to go about making the other thing work... lol

now it seems to *all* (as in, the line shown here...) be working, but the script an a whole isn't yet. :mad:
why is this incapable of noticing that test_number contains a decimal!!!???
```
if [[ $test_number =~ "." ]]; then
```

---

### Post by geirha on 2007-11-30
[quote=bash's manpage]An additional binary operator, =~, is available, with  the  same
              precedence  as  ==  and  !=.  When it is used, the string to the
              right of the operator is considered an extended regular  expres&#8208;
              sion and matched accordingly (as in regex(3)).[/quote]

In regex, "." matches any symbol, so as long as $test_number is not an empty string, it will evaluate to true. To match for a punctuation mark, you need to escape it with a backslash: "\."
```
$ [[ 12 =~ "." ]] && echo true || echo false
true
$ [[ 12.2 =~ "." ]] && echo true || echo false
true
$ [[ 12 =~ "\." ]] && echo true || echo false
false
$ [[ 12.2 =~ "\." ]] && echo true || echo false
true

```

---

### Post by ryanVickers on 2007-11-30
now it just takes a lot of CPU and does nothing, which makes me think it's finding nothing as prime instead of everything...

---

### Post by sagarhshah on 2008-01-25
```

test_number=$(echo scale=3\; $prime_number '/' $current_number | bc)

```

This was just what I was looking for my script thanks :D

---

