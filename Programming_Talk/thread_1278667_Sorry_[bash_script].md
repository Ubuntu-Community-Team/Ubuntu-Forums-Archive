---
title: "Sorry [bash script]"
date: 2009-09-29
forum: Programming Talk
---

### Post by play05 on 2009-09-29
Sorry cariboo907.. :(
My bad.Ok right now i had done it but still got error[newbie in bash].Maybe you can give me a hint. :)

This is my code i had done :

#! /bin/bash

for INTG in one two three four five 
do
 read INTG
 echo "The sum is"
 echo $(one + two + three + four + five)
done
exit 0

And the question: reads 5 integer from user at one time using **for..do loop**.Can you give me hint how to do this with for loop.It easy if just read it only,but using for loop pretty confusing me?

---

### Post by lloyd_b on 2009-09-29
> **play05 said:**
> Sorry cariboo907.. :(
My bad.Ok right now i had done it but still got error[newbie in bash].Maybe you can give me a hint. :)

This is my code i had done :

#! /bin/bash

for INTG in one two three four five 
do
 read INTG
 echo "The sum is"
 echo $(one + two + three + four + five)
done
exit 0

And the question: reads 5 integer from user at one time using **for..do loop**.Can you give me hint how to do this with for loop.It easy if just read it only,but using for loop pretty confusing me?

A simpler way of using the "for" loop is a bash trick: {start..end}.  For instance, "for COUNT in {1..5}" will loop through the integers 1 through 5, providing a good way to iterate a loop a specific number of times.

Your main problem is that you are reading the value into INTG, but never adding it into a total variable.  You need a separate TOTAL variable (initialized to zero), to which to add the value input on each iteration of the loop.  Then, after the end of the loop, output the value in the TOTAL variable.

I could give you a script to do this, but this sounds like a homework problem, so all you get is hints...

Lloyd B.

---

### Post by Can+~ on 2009-09-29
You got it almost right, the thing is that the for..loop is just for repeating 5 times an operation, you don't exactly need that variable for anything, here's a hint:

[PHP]total=0 # this one will keep track of the value
for count in {1..5}
do
	read x
	#complete here
done[/PHP]

---

### Post by wmcbrine on 2009-09-29
Every variable reference in bash requires a "$".

Printing out the sum should occur *after* the loop. Unless you're trying to do a running total... in which case, fail, because you're adding up uninitialized variables.

Finally, $[] is used for arithmetic in bash, not $().

---

### Post by play05 on 2009-09-29
Thanks everyone,i can understand little bit but still got error.I had modified the script.Below is the following script

#! /bin/bash

count =0
for INTG in {1..5}
do
 read x
 count=`expr $count + $x`
done
echo "The total of sum ="
echo $total

So how should i sum it correctly.In c,it gonna be count=count+x or count +=x
But i bash i don't really understand how it work =(.
Is it a must to put `expr`?? :confused:

---

### Post by wmcbrine on 2009-09-29
There is no need to use expr, and you incur a performance penalty for doing so (not that it matters in a script this size, but anyway). Use square brackets, like I said. But your expr expression *would* work, if the rest of the script were correct.

More importantly, you switch between "count" and "total", trying to print the value of total before ever having defined it.

Finally, there should be no space in the initialization of count.

---

### Post by kaibob on 2009-09-29
> **wmcbrine said:**
> Finally, $[] is used for arithmetic in bash, not $().

According to the Bash Reference Manual and Bash man page, arithmetic expansion is in the form of $((expression)). I was curious how it is done with $[expression]. I tried this in a terminal window and it didn't work.

EDIT:

Well, I was wrong, it does work:

> $ total=$((2+2)) ; echo $total
4
$ total=$[2+2] ; echo $total
4

---

