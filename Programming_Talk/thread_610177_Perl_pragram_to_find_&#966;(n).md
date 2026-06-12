---
title: "Perl pragram to find &#966;(n)"
date: 2007-11-11
forum: Programming Talk
---

### Post by shingalated on 2007-11-11
I need a perl program to make a table of n in the first column and &#966;(n) in the second column. (Phi = the number of relative primes to n)
This is all I have so far...  I don't know how to make it a loop or how to write the part that finds what &#966;(n) is.


#!/bin/perl
#Program to make table of &#966;(n)
$n=0;
$num2 = $num1+1;
$num1 = $num2;

$n = $n +1;
$n = $num2;
%table = ("n", $n, "phi (n)", $num2);

---

### Post by flibitboat on 2007-11-11
oh yes, i have seen this type of problme before and it is one of the most complicated i have ever seen before.  it looks like you are **** out of luck because  there is no possible way to do it so get over youself and blow a chipmunk.

---

### Post by shingalated on 2007-11-11
> **flibitboat said:**
> oh yes, i have seen this type of problme before and it is one of the most complicated i have ever seen before.  it looks like you are **** out of luck because  there is no possible way to do it so get over youself and blow a chipmunk.

Oh, that was wonderful...Thanks for your help.

---

### Post by slavik on 2007-11-11
start with writing a program that finds the relative prives when given n ...

---

### Post by Lux Perpetua on 2007-11-11
> **flibitboat said:**
> oh yes, i have seen this type of problme before and it is one of the most complicated i have ever seen before.  it looks like you are **** out of luck because  there is no possible way to do it so get over youself and blow a chipmunk.Thank you for your completely unhelpful post. 

@shingalated - Hint: two numbers are relatively prime when their GCD (greatest common divisor) is 1. So it might help to write a function that finds the GCD of two numbers. 

(If speed is an issue, then there are more efficient ways to approach this, such as using the fact that if m and n are relatively prime, then phi(m)*phi(n) = phi(m*n).)

---

### Post by shingalated on 2007-11-11
How do I turn the:

$n = $n +1;
$n = $num2;
%table = ("n", $n, "phi (n)", $num2);

part into a loop so than n increases by one each time?

---

### Post by evymetal on 2007-11-11
> **shingalated said:**
> 
#!/bin/perl
#Program to make table of &#966;(n)
$n=0;
$num2 = $num1+1;
$num1 = $num2;

$n = $n +1;
$n = $num2;
%table = ("n", $n, "phi (n)", $num2);

Try:
```

#!/bin/perl
#Program to make table of &#966;(n)
$n=0;
$maxn = 100;
while ($n<=$maxn){
    # function will go here.
    $n = $n +1;
}


```

Google "Perl Loops".

I'm not sure what you are doing within the loop though... 
You'll also have to look up associative arrays, I'm not sure why you are saving each row to an array.

---

### Post by smartbei on 2007-11-12
Posting about Project Euler questions in a public forum... tsk tsk :p.

You may want to learn more about perl (or rather, any programming language) in a more general way. Perhaps I am wrong but I get the sense that you are just starting to program and I suggest that you start from an earlier Project Euler problem or from general tutorials.

@flibitboat: This is definately possible, as I have solved it :).

---

### Post by Npl on 2007-11-12
the hard part is doing a prime-factorization on n - if you mean finding a **fast** algorithm for big n, cause noone found one yet.
once you have your prime-factorization its simple. if n = p^k  (where p is prime), then phi(n) = p^(k-1) * (p-1). once you got the phi-values for all different prime(-powers) you merely multiplicate them

eg.
n = 177 = 13 * 3^2
phi(13^1) = 1*12 = 12
phi(3^2) = 3*2 = 6
phi(177) = phi(13)*phi(9) = 12*6 = 72

how you do it in perl is your problem :-\"

---

### Post by slavik on 2007-11-12
there is a way to find the GCD of two numbers in a non-brute force way ;)

---

### Post by shingalated on 2007-11-12
Thank you.  I think I can figure it out from here.

---

