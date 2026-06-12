---
title: "Prime Time: C, Lisp, and Python"
date: 2009-07-17
forum: Programming Talk
---

### Post by JordyD on 2009-07-17
I created three programs, all the same functions, and used 'time' on their executables. They were written in C, Lisp, and Python. They all find all the prime numbers between 0 and 100000. I found it interesting, so I figured I'd share the results.

It's most impressive when you run them yourself.

These are their runtimes:
C:
```
real	0m0.312s
user	0m0.076s
sys	0m0.040s
```
Lisp:
```
real	0m0.996s
user	0m0.508s
sys	0m0.056s
```
Python:
```
real	0m0.494s
user	0m0.176s
sys	0m0.064s

```

This is the code I used:
C:
```
#include <stdio.h>
#include <stdbool.h>
#include <math.h>

bool check_prime(int num)
{
	int dividend;
	double check_to = sqrt(num);

	for (dividend = 2; dividend <= check_to; dividend++) {
		if (num % dividend == 0) {
			return false;
		}
	}

	return true;
}

void primes_in_range (int from, int to)
{
	int current;

	for (current = from; current <= to; current++) {
		if (check_prime(current))
			printf("%d\n", current);
	}
}

int main()
{
	primes_in_range(0, 100000);
}

```
Lisp:
```
(proclaim '(optimize (speed 3) (safety 0) (debug 0)))
(defun check-prime (num)
  (declare (type fixnum num))
  (if (< 2 num)
      (let ((chk-to 2))
	(loop for dividend from 2 upto chk-to
	   do (when (equal (rem num dividend) 0)
		(return nil))
	   finally (return t)))
      t))
(defun primes-in-range (start stop)
  (declare (type fixnum start stop))
  (loop for current from start to stop
     do (when (check-prime current)
	  (format t "~a~%" current))))
```
Python:
```
import psyco; psyco.full()
from math import sqrt

def check_prime(num):
	dividend = 0
	check_to = int(sqrt(num)) + 1
	
	for dividend in range(2, check_to):
		if num % dividend == 0:
			return False
	return True

def primes_in_range(start, stop):
	current = 0
	
	for current in range(start, stop):
		if check_prime(current):
			print current
			
primes_in_range(0, 100000)
```

If you think you can make the code faster, go ahead, and I'll update the time results.

If you want to add a language, post it. I won't add it to the OP, but it would be interesting to see other languages, too.

As for the Lisp code, I created an executable by loading it into sbcl and executing:
```
(save-lisp-and-die "prime-lisp" :executable t :toplevel
		   (lambda ()
		   (primes-in-range 0 100000)
		   (quit)))
```

The C code was compiled with gcc:
```
gcc -o prime-c prime.c
```

The python code was interpreted normally:
```
python prime.py
```

The version of python used: 2.6.2

I ran these on Ubuntu 9.04 on a Dell Latitude D610.

Keep in mind that I'm very much a novice, so if you see some way to improve any of the code or anything, tell me.

Also keep in mind that these aren't very fair comparisons, considering that it's only testing one kind of function.

---

### Post by Mirge on 2009-07-17
What are you using to benchmark them?

---

### Post by JordyD on 2009-07-17
> **Mirge said:**
> What are you using to benchmark them?

The 'time' command.

---

### Post by Can+~ on 2009-07-17
Try running the python one again (do not delete the .pyc).

Also, there's a serious lag when printing the value of a variable that adds noise to your test, this affects all of them.

---

### Post by nvteighen on 2009-07-17
You're being unfair with Python... Your asking Python to bytecompile and then execute... You should have compiled it and then reinvoke Python to execute it from the .pyc to make this a fair test.

Do this:
```

python -c "import *filename without extension*"

```

That will generate the .pyc file.

---

### Post by JordyD on 2009-07-17
I will do that and update the python results when done.

---

### Post by arcdrag on 2009-07-17
I know algorithm efficiency isn't your goal here...but getting the first 100K primes can be done in well under a second with the right algorithm in C.

---

### Post by tribaal on 2009-07-17
Algorithmically, you should only check up to the square root of the number, not "number / 2"...
Computing the square root is a trivial operation compared to going from "square root" to "num /2", especially for large numbers.

But that affects your 3 versions, so it's still kind of valid, while artificial.

Have fun :)

- Trib'

---

### Post by Can+~ on 2009-07-17
Also, it would be nice to see the result in [Pyrex]("http://www.cosc.canterbury.ac.nz/greg.ewing/python/Pyrex/").

---

### Post by JordyD on 2009-07-17
Python did not improve by much:

**OLD:**
```
real	2m37.319s
user	1m51.447s
sys	0m1.016s
```

**NEW:**
```
real	2m18.495s
user	1m50.503s
sys	0m0.688s
```

Maybe I already compiled to bytecode earlier and forgot? I think I ran it once as a test, then ran it again with a 'time' prepended to the command.

I will now update my OP.

---

### Post by Can+~ on 2009-07-17
Well, I know this is out of place, but I have a Different Algorithm (I just found it on my harddrive).

[PHP]#!/usr/bin/env python

import time

def timer(func, *args, **kargs):
	
	def timedfunc(*args, **kargs):
		tdelta = time.time()
		func(*args, **kargs)
		tdelta = time.time() - tdelta
		
		print "Measured time %.4f[s]:" % tdelta
	
	return timedfunc

def primegen(max):
	
	test = lambda x: x%2 and x%3 and x%5 and x%7
	
	# preconditions
	for iter in (1, 2, 3, 5, 7):
		if iter < max+1:
			yield iter
	
	# next
	for iter in xrange(6, max+1, 6):
		
		if test(iter-1):
			yield iter-1
		
		if test(iter+1):
			yield iter+1

@timer
def start():
	for i in primegen(100000):
		print i

start()[/PHP]

It does a prime test for each (6n+1) and (6n-1), thus, skipping some unnecessary numbers. Plus, it has it's own decorator to measure time and using the yield statement.

With this algorithm it takes 0.6114[s] with my old Athlon.

*edit: whoops, found an error, that's what you get by copying old code

*edit2: To make it clear, this is wrong.

---

### Post by JordyD on 2009-07-17
> **tribaal said:**
> Algorithmically, you should only check up to the square root of the number, not "number / 2"...
Computing the square root is a trivial operation compared to going from "square root" to "num /2", especially for large numbers.

But that affects your 3 versions, so it's still kind of valid, while artificial.

Have fun :)

- Trib'

God, that improves speed by a lot. For **Python** (I will edit this as I add it to the others):
**EDIT:** I ran from prime.pyc this time.
**OLD:**
```
real	2m18.495s
user	1m50.503s
sys	0m0.688s
```
**NEW:**
```
real	0m2.755s
user	0m1.560s
sys	0m0.056s
```

**LISP:**
**OLD:**
```
real	0m59.112s
user	0m42.651s
sys	0m0.464s
```
**NEW:**
```
real	0m1.072s
user	0m0.480s
sys	0m0.068s

```

**C:**
**OLD:**
```
real	0m3.038s
user	0m2.216s
sys	0m0.052s
```
**NEW:**
```
real	0m0.312s
user	0m0.076s
sys	0m0.040s

```

---

### Post by fr4nko on 2009-07-17
I have made the test with ocaml. Here the ocaml code:
```

let check_prime p' =
  let rec check_prime_rec p n up_to =
    if n > up_to then
      true
    else
      if p mod n = 0 then
    false
      else
    check_prime_rec p (n+1) up_to
  in
    check_prime_rec p' 2 (p' / 2)

let irange n =
  let rec citer ls i =
    if i > n then ls else citer (i :: ls) (i+1) in
    citer [] 0

let check_print n =
  if check_prime n then Printf.printf "%d\n" n
;;

List.iter check_print (irange 100000)

```that can be compiled with
> 
ocamlopt -c mlprime.ml
ocamlopt -o mlprime mlprime.cmx
and here the results that I obtain on my system:
c code:
real    0m1.039s
user    0m0.964s
sys    0m0.036s

ocaml code:
real    0m1.135s
user    0m1.088s
sys    0m0.016s

As you can see the difference is just a small percent. This clearly demonstrate the superiority of ocaml to create fast efficient code when compared to other high-level programming languages. In particular ocaml compares very favorably to lisp and to python.

I'm happy that this test has been proposed because it gives me the opportunity of demonstrating the power of ocaml.

:-)

Francesco

---

### Post by nvteighen on 2009-07-17
I did an experiment in Scheme. I've tested two pure-functional versions (therefore, I replaced all Common Lisp's iterations by tail-recursions) of the same program, both from the optimized compiled files. The difference is that while the first uses the OP's algorithm, the second uses an infinite stream of primes to simulate the Sieve of Eratosthenes (is a code you can find in a very basic fashion at the SICP book).

EDIT: Now it works. The lazy evaluated performs better than the eager evaluated! (20 secs vs. 24 secs... of course, none of both can play against the rest :P)

```

;; Primes (tail-recursive version of OP's algorithm)
;;
;; Benchmark:
;; real    0m24.818s (Slower than below!)
;; user    0m0.000s
;; sys     0m0.000s

(declare (usual-integrations)) ; Optimizing

(define (primes start stop)
  (define (check-prime num)
    (if (< num 2)
        #f
        (let ((chk-to (sqrt num)))
          (let loop ((dividend 2))
            (if (>= dividend chk-to)
                #t
                (if (= (modulo num
                               dividend)
                       0)
                     #f
                     (loop (+ dividend
                              1))))))))

  (let loop ((i start)
             (primes-found '()))
    (if (> i stop)
        (reverse primes-found)
        (loop (+ i 1)
              (if (check-prime i)
                  (cons i
                        primes-found)
                  primes-found)))))

(begin
  (display (primes 1 100000))
  (quit))

```

```

;; Primes (Lazy evaluated)
;; 
;; Benchmark:
;; real    0m20.192s (Faster than above!)
;; user    0m0.000s
;; sys     0m0.000s

(declare (usual-integrations)) ; Optimizing

(define (primes start stop)
  (define (generate-stream start)
    (cons-stream start
                 (generate-stream (+ start
                                     1))))

  (define (sieve stream)
    (let ((current (stream-car stream)))
      (cons-stream current
                   (sieve (stream-filter (lambda (x)
                                           (not (= (modulo x
                                                           current)
                                                   0)))
                                         (stream-cdr stream))))))
                                                         
  ;; Body... essentially just something that collects the infinite stream into a
  ;; finite list
  (let loop ((my-sieve (sieve (generate-stream (if (< start 2)
                                                   2
                                                   start))))
             (primes-found '()))
    (let ((current (stream-car my-sieve))
          (next (stream-cdr my-sieve)))
      (if (> current 
             stop)
          (reverse primes-found)
          (loop next
                (cons current
                      primes-found))))))

(begin
  (display (primes 1 100000))
  (quit))

```

---

### Post by Cl0ud9 on 2009-07-17
I don't know if it will make a big difference, but the rem function is faster than the mod function in lisp. They are used in exactly the same way.

```

(= (mod 9 2) (rem 9 2))
T

```

---

### Post by JordyD on 2009-07-17
> **Cl0ud9 said:**
> I don't know if it will make a big difference, but the rem function is faster than the mod function in lisp. They are used in exactly the same way.

```

(= (mod 9 2) (rem 9 2))
T

```

**OLD:**
```
real	0m1.072s
user	0m0.480s
sys	0m0.068s
```
**NEW:**
```
real	0m1.030s
user	0m0.504s
sys	0m0.064s
```

Not much of a difference, but it'll stay.

I'll update the OP.

---

### Post by JordyD on 2009-07-17
> **fr4nko said:**
> I have made the test with ocaml. Here the ocaml code:
```

let check_prime p' =
  let rec check_prime_rec p n up_to =
    if n > up_to then
      true
    else
      if p mod n = 0 then
    false
      else
    check_prime_rec p (n+1) up_to
  in
    check_prime_rec p' 2 (p' / 2)

let irange n =
  let rec citer ls i =
    if i > n then ls else citer (i :: ls) (i+1) in
    citer [] 0

let check_print n =
  if check_prime n then Printf.printf "%d\n" n
;;

List.iter check_print (irange 100000)

```that can be compiled with
and here the results that I obtain on my system:
c code:
real    0m1.039s
user    0m0.964s
sys    0m0.036s

ocaml code:
real    0m1.135s
user    0m1.088s
sys    0m0.016s

As you can see the difference is just a small percent. This clearly demonstrate the superiority of ocaml to create fast efficient code when compared to other high-level programming languages. In particular ocaml compares very favorably to lisp and to python.

I'm happy that this test has been proposed because it gives me the opportunity of demonstrating the power of ocaml.

:-)

Francesco

Neat. :D Maybe I should learn OCaml. (After Lisp, maybe)

I await the day we find a higher-level language faster than C. I will be so happy.

**EDIT:** :D It prints the numbers backwards.

**EDIT2:** I get these results on my system:
**C:**
```
real	0m0.285s
user	0m0.084s
sys	0m0.016s

```
**OCaml:**
```
real	0m2.627s
user	0m2.436s
sys	0m0.016s

```

---

### Post by nvteighen on 2009-07-17
Ok, now my experiment worked... See my post above.

---

### Post by fr4nko on 2009-07-17
There is a very fast algorithm to check is a number is prime based on Fermat small theorem. The only problem is that in principle some prime can be detected as prime even is they are not, not it is actually a pseud primality test. It is nevertheless very rare that the algorithm will fail and it happen only for huge numbers. So this algorithm can be used for almost all practical purposed.

Here an implementation in ocaml:
```

let pseudoprime_test_values = [2;3;5;7;11;13;17;19]

let mod_power a n p =
  let rec power_iter res i =
    if i = n then res else
      power_iter ((a * res) mod p) (i+1)
  in
    power_iter a 1

let is_pseudoprime n =
  let tvalues = List.filter (fun x -> x < n) pseudoprime_test_values in
    List.for_all (fun v -> mod_power v (n-1) n = 1) tvalues

```Of course it can be easily translated in C or python if you want. This algorithm is much better of any naive algorithm you may use.

For the curious, the Fermat small theorem says that for any prime 'p' and any integer 'a' not divided by p the following equality holds:
  
a^(p-1)       = 1 mod p

Francesco

---

### Post by lavinog on 2009-07-17
> **Can+~ said:**
> 
Also, there's a serious lag when printing the value of a variable that adds noise to your test, this affects all of them.

Why not just count the number of primes instead of printing them, or store them in an array.
Printing the output can skew results based on terminal size...etc

---

### Post by JordyD on 2009-07-17
> **nvteighen said:**
> Ok, now my experiment worked... See my post above.

I'm glad I chose to learn Lisp over Scheme.

---

### Post by fr4nko on 2009-07-17
> **JordyD said:**
> Neat. :D Maybe I should learn OCaml. (After Lisp, maybe)

I await the day we find a higher-level language faster than C. I will be so happy.
Well, I believe ocaml is certainly worth of learning.

Talking about a language faster than C, it does not exists because in C the code is very close to direct machine code so you can write highly optimised code. FORTRAN can be faster then C for some number crunching applications but the language is horrible so it is not a very interesting to learn.

For the curious, here the assembler code generated with C for the check_prime function:
```

check_prime:
        pushl   %esi
        pushl   %ebx
        movl    12(%esp), %esi
        movl    %esi, %eax
        shrl    $31, %eax
        leal    (%eax,%esi), %ebx
        sarl    %ebx
        cmpl    $1, %ebx
        jle     .L2
        movl    %eax, %edx
        movl    $2, %ecx
        leal    (%esi,%eax), %eax
        andl    $1, %eax
        cmpl    %edx, %eax
        jne     .L4
        jmp     .L3
        .p2align 4,,7
        .p2align 3
.L5:
        movl    %esi, %edx
       movl    %esi, %eax
        sarl    $31, %edx
        idivl   %ecx
        testl   %edx, %edx
        je      .L3
.L4:
        addl    $1, %ecx
        cmpl    %ecx, %ebx
        jge     .L5
.L2:
        movl    $1, %eax
        popl    %ebx
        popl    %esi
        ret
        .p2align 4,,7
        .p2align 3
.L3:
        xorl    %eax, %eax
        popl    %ebx
        popl    %esi
        ret

```and by ocaml for the check_prime_rec function:
```

camlMlprime__check_prime_rec_60:
.L104:
        movl    %eax, %edi
        movl    %ecx, %esi
        cmpl    %esi, %ebx
        jle     .L103
        movl    $3, %eax
        ret
        .align  16
.L103:
        movl    %ebx, %ecx
        sarl    $1, %ecx
        testl   %ecx, %ecx
        je      .L102
        movl    %edi, %eax
        sarl    $1, %eax
        cltd
        idivl   %ecx
        jmp     .L101
        .align  16
.L102:
       movl    $caml_bucket_Division_by_zero, %eax
        movl    caml_exception_pointer, %esp
        popl    caml_exception_pointer
        ret
        .align  16
.L101:
        sall    $1, %edx
        incl    %edx
        cmpl    $1, %edx
        jne     .L100
        movl    $1, %eax
        ret
        .align  16
.L100:
        addl    $2, %ebx
        movl    %edi, %eax
        movl    %esi, %ecx
        jmp     .L104

```As you can see they are absolutely comparable and ocaml is also checking the division by zero and it raise an exception if it happens.

Francesco

---

### Post by fr4nko on 2009-07-17
> **JordyD said:**
> 
**EDIT2:** I get these results on my system:
**C:**
```
real    0m0.285s
user    0m0.084s
sys    0m0.016s

```**OCaml:**
```
real    0m2.627s
user    0m2.436s
sys    0m0.016s

```
Very strange. You are sure you have used ocamlopt to compile the ocaml code ? you should not use ocamlc because it does produce interpreted bytecode.

---

### Post by JordyD on 2009-07-17
> **fr4nko said:**
> Very strange. You are sure you have used ocamlopt to compile the ocaml code ? you should not use ocamlc because it does produce interpreted bytecode.

I did use ocamlopt. Perhaps it does not like my CPU? It also jumps when it runs. I get results in chunks.

I will test it on my other computer.

---

### Post by CptPicard on 2009-07-17
> **JordyD said:**
> I'm glad I chose to learn Lisp over Scheme.

Scheme is a Lisp... but, the point of Scheme is not this sort of stuff, it's the ideas in it instead. :)

Anyway, a couple of things... loading the lisp image probably adds a lot to your runtime... you may want to test using the built-in "time" function:

```

(time (some-operation))

```

Second, look up in the docs for the ways to explicitly declare your variable types. This way, a simple numeric algorithm like this ought to essentially compile into pretty much the same machine code you'd get from the C version. (You can even check with "disassemble").

---

### Post by hessiess on 2009-07-17
> **JordyD said:**
> I'm glad I chose to learn Lisp over Scheme.

Scheme *is* a dialect of Lisp, Like Common Lisp, Clojure etc.

---

### Post by JordyD on 2009-07-17
> **CptPicard said:**
> Scheme is a Lisp... but, the point of Scheme is not this sort of stuff, it's the ideas in it instead. :)

Anyway, a couple of things... loading the lisp image probably adds a lot to your runtime... you may want to test using the built-in "time" function:

```

(time (some-operation))

```

Second, look up in the docs for the ways to explicitly declare your variable types. This way, a simple numeric algorithm like this ought to essentially compile into pretty much the same machine code you'd get from the C version. (You can even check with "disassemble").

Neat. I'll try that and post the results when done.

About the built-in time function:
I was aware of it, but I wanted to see how they fared as stand-alone executables. Granted I didn't do that with python (need an interpreter), but in all fairness, I can still do a ./prime.py, where with lisp I would have to do an sbcl --load prime.lisp.

> **hessiess said:**
> Scheme *is* a dialect of Lisp, Like Common Lisp, Clojure etc.

Well, yes, I was aware that it's a dialect of Lisp, but I am still happier that I learned Common Lisp instead of Scheme.

---

### Post by JordyD on 2009-07-17
> **JordyD said:**
> I did use ocamlopt. Perhaps it does not like my CPU? It also jumps when it runs. I get results in chunks.

I will test it on my other computer.

Same results on my other computer.

---

### Post by cyberslayer on 2009-07-17
> **Can+~ said:**
> 
def primegen(max):
	
	test = lambda x: x%2 and x%3 and x%5 and x%7
code

This algorithm is wrong; you cannot test if a number is prime by only dividing it by 2, 3, 5 and 7.  Your program will say that 121 = 11 * 11 is prime since it is not divisible by 2, 3, 5 or 7.

---

### Post by Can+~ on 2009-07-17
> **cyberslayer said:**
> This algorithm is wrong; you cannot test if a number is prime by only dividing it by 2, 3, 5 and 7.  Your program will say that 121 = 11 * 11 is prime since it is not divisible by 2, 3, 5 or 7.

That's why I said I had an error. (Added a *edit2 to make it clear)

The reason of that mistake was that, back then, I used the [Sieve of Eratosthenes]("http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes") for the <100; and now I just upped the maximum.

---

### Post by JordyD on 2009-07-17
I did this:
```
(defun check-prime (num)
  (declare (type fixnum num))
  (if (< 2 num)
      (do ((dividend 2 (1+ dividend))
	   (chk-to (sqrt num)))
	  ((equal (rem num dividend) 0))
	(when (<= chk-to dividend)
	  (return t)))
      t))
(defun primes-in-range (from to)
  (declare (type fixnum from to))
  (do ((current from (1+ current)))
      ((> current to))
    (when (check-prime current)
      (format t "~a~%" current))))
```

Now when timed:
**OLD:**
```
real	0m1.030s
user	0m0.504s
sys	0m0.064s
```
**NEW:**
```
real	0m0.996s
user	0m0.508s
sys	0m0.056s

```

I think I need more declares with the corresponding types, but I cannot figure out how to declare the types of the variables in my do loops.

---

### Post by arcdrag on 2009-07-17
> **cyberslayer said:**
> This algorithm is wrong; you cannot test if a number is prime by only dividing it by 2, 3, 5 and 7.  Your program will say that 121 = 11 * 11 is prime since it is not divisible by 2, 3, 5 or 7.

The quickest simple algorithm for the first 1M primes is simply to declare an array of a million bools all initialized to true.  Then, starting at 2, traverse the array, and each time you hit a prime number (a true value), set every multiple of that number to false.  

Of course this is far more memory intensive...but will print out the first 1M numbers far faster than you printed out the first 100K

---

### Post by Jakob Von Gunten on 2009-07-17
Why compare the intepreted code to compiled code?

If speed is important does the programmer consider Python or Lisp? no.

If speed is not so important then Python or Lisp can be put to use.

Comparing the execution of compiled and interpreted code, of course the compiled will always be faster, what is the point?

---

### Post by HavocXphere on 2009-07-17
Cool thread.

Python:
```
check_to = sqrt(num)
```
```
check_to = int(sqrt(num))
```
Results in a minor but consistent gain. (And removes a warning too) 

Also, in this type of test you really need to get rid of the printing. It distorts things in a major way. A "pure" calculation time /w output would be much better imo.

---

### Post by JordyD on 2009-07-17
> **Jakob Von Gunten said:**
> Why compare the intepreted code to compiled code?

If speed is important does the programmer consider Python or Lisp? no.

If speed is not so important then Python or Lisp can be put to use.

Comparing the execution of compiled and interpreted code, of course the compiled will always be faster, what is the point?

I said in the beginning of the thread that this is not a fair test.

This is not to show what language is 'best'. I just ran tests on three versions of a prime number generator and thought others would find it interesting, so I posted it.

Plus, that Lisp code, as far as I know, is compiled.

---

### Post by JordyD on 2009-07-17
Whoops! I've not been updating the Python times in the OP. Sorry. I've updated it now. (2 min -> 2 sec)

---

### Post by JordyD on 2009-07-17
> **HavocXphere said:**
> Cool thread.

Python:
```
check_to = sqrt(num)
```
```
check_to = int(sqrt(num))
```
Results in a minor but consistent gain. (And removes a warning too) 

Also, in this type of test you really need to get rid of the printing. It distorts things in a major way. A "pure" calculation time /w output would be much better imo.

I've done this (sqrt thing).

I was not getting any warning. What version of Python do you have?

---

### Post by HavocXphere on 2009-07-17
> **JordyD said:**
> I've done this (sqrt thing).

I was not getting any warning. What version of Python do you have?
2.6.2

It gets drowned in the output. Oh, and I didn't compile it. I just created a script. I only saw the warning when I piped the output:
```
time python test.py > error.txt
```
```
test.py:7: DeprecationWarning: integer argument expected, got float
  for dividend in range(2, check_to):

```

---

### Post by Can+~ on 2009-07-17
You can also use x**0.5, not that it will add any gain, but I think it's prettier :KS

---

### Post by unknownPoster on 2009-07-17
> **arcdrag said:**
> The quickest simple algorithm for the first 1M primes is simply to declare an array of a million bools all initialized to true.  Then, starting at 2, traverse the array, and each time you hit a prime number (a true value), set every multiple of that number to false.  

Of course this is far more memory intensive...but will print out the first 1M numbers far faster than you printed out the first 100K

Also known as the Sieve of Eratosthenes

---

### Post by c0mput3r_n3rD on 2009-07-17
Lisp looks so odd....
and very intimidating...

---

### Post by JordyD on 2009-07-17
> **c0mput3r_n3rD said:**
> Lisp looks so odd....
and very intimidating...

I think it looks very structured and logical.

**EDIT:** As a Lisp novice, I'd say that C looks structured and linear, while Lisp looks like it dances (possibly the indentation) yet structured (definitely the indentation). That's *looks*, though.

---

### Post by TheStatsMan on 2009-07-17
I a fortran90 version of the original algorithm. I typed in CAPS to be traditional. It takes almost exactly the same time as the c code on my machine with -O3 optimisations in both cases.

[php]      LOGICAL FUNCTION ISPRIME(NUM)
        INTEGER I, NUM,CHECKTO
        ISPRIME=.TRUE.

        CHECKTO=AINT(SQRT(REAL(NUM)));
        DO I=2,CHECKTO
            IF(MODULO(NUM,I)==0) THEN
               ISPRIME=.FALSE.
           END IF
        ENDDO  
        RETURN
      END FUNCTION ISPRIME
      
      SUBROUTINE  PRIMESINRANGE(START,FINISH)
        INTEGER CURRENT, START, FINISH
        DO CURRENT = START,FINISH
            IF(ISPRIME(CURRENT)/=0) THEN
                WRITE(*,*) CURRENT 
            END IF
        END DO 

      END SUBROUTINE PRIMESINRANGE
      
      PROGRAM  PRINTPRIMES
        CALL PRIMESINRANGE(0,100000)
      END PROGRAM PRINTPRIMES[/php]

---

### Post by JordyD on 2009-07-17
> **TheStatsMan said:**
> I a fortran90 version of the original algorithm. I typed in CAPS to be traditional. It takes almost exactly the same time as the c code on my machine with -O3 optimisations in both cases.

[php]      LOGICAL FUNCTION ISPRIME(NUM)
        INTEGER I, NUM,CHECKTO
        ISPRIME=.TRUE.

        CHECKTO=AINT(SQRT(REAL(NUM)));
        DO I=2,CHECKTO
            IF(MODULO(NUM,I)==0) THEN
               ISPRIME=.FALSE.
           END IF
        ENDDO  
        RETURN
      END FUNCTION ISPRIME
      
      SUBROUTINE  PRIMESINRANGE(START,FINISH)
        INTEGER CURRENT, START, FINISH
        DO CURRENT = START,FINISH
            IF(ISPRIME(CURRENT)/=0) THEN
                WRITE(*,*) CURRENT 
            END IF
        END DO 

      END SUBROUTINE PRIMESINRANGE
      
      PROGRAM  PRINTPRIMES
        CALL PRIMESINRANGE(0,100000)
      END PROGRAM PRINTPRIMES[/php]

Yay for old school. I'd like to see how fast this runs.

---

### Post by lisati on 2009-07-17
> **JordyD said:**
> Yay for old school. I'd like to see how fast this runs.

+1: Fortran was one of the first languages I learned. Haven't used it for nearly 30 years.

---

### Post by Can+~ on 2009-07-17
Here's the code on [orangutan]("http://www.dangermouse.net/esoteric/ook.html").

[PHP]Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook! Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook! Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook! Ook. Ook! Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook! Ook. Ook. Ook? Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook.
Ook? Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook. Ook! Ook! Ook! Ook!
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook!
Ook! Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook. Ook! Ook!
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook.
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook!
Ook! Ook! Ook! Ook! Ook! Ook. Ook! Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook! Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook! Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook! Ook. Ook! Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook! Ook. Ook. Ook? Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook.
Ook? Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook. Ook! Ook! Ook! Ook!
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook!
Ook! Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook. Ook! Ook!
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook.
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook!
Ook! Ook! Ook! Ook! Ook! Ook. Ook! Ook! Ook! Ook! Ook! Ook!
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook.
Ook? Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook. Ook! Ook! Ook! Ook!
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook!
Ook! Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook. Ook! Ook!
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook.[/PHP]

Nah.. just kidding, I copied the code for hello world a few times, it's plain gibberish.

---

### Post by lavinog on 2009-07-17
> **Can+~ said:**
> Here's the code on [orangutan]("http://www.dangermouse.net/esoteric/ook.html").

[PHP]Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
...
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook.[/PHP]

Nah.. just kidding, I copied the code for hello world a few times, it's plain gibberish.
How does someone comment their code with that language?

---

### Post by JordyD on 2009-07-17
> **Can+~ said:**
> Here's the code on [orangutan]("http://www.dangermouse.net/esoteric/ook.html").

[PHP]Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook! Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook! Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook! Ook. Ook! Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook! Ook. Ook. Ook? Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook.
Ook? Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook. Ook! Ook! Ook! Ook!
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook!
Ook! Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook. Ook! Ook!
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook.
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook!
Ook! Ook! Ook! Ook! Ook! Ook. Ook! Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook! Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook! Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook! Ook. Ook! Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook! Ook. Ook. Ook? Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook.
Ook? Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook. Ook! Ook! Ook! Ook!
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook!
Ook! Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook. Ook! Ook!
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook.
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook!
Ook! Ook! Ook! Ook! Ook! Ook. Ook! Ook! Ook! Ook! Ook! Ook!
Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook.
Ook? Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook.
Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook. Ook! Ook! Ook! Ook!
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook!
Ook! Ook. Ook. Ook. Ook. Ook. Ook. Ook. Ook! Ook. Ook! Ook!
Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook! Ook.[/PHP]

Nah.. just kidding, I copied the code for hello world a few times, it's plain gibberish.

What is this? A language with three actions? Ook. Ook! Ook?

---

### Post by Can+~ on 2009-07-17
> **JordyD said:**
> What is this? A language with three actions? Ook. Ook! Ook?

[http://en.wikipedia.org/wiki/Esoteric_programming_language](http://en.wikipedia.org/wiki/Esoteric_programming_language)

---

### Post by JordyD on 2009-07-17
> **Can+~ said:**
> [http://en.wikipedia.org/wiki/Esoteric_programming_language](http://en.wikipedia.org/wiki/Esoteric_programming_language)

I've been there before. :D I've never heard of Orangutan.

Anyways, my favorite is LOLCODE.

---

### Post by JordyD on 2009-07-17
> **lavinog said:**
> How does someone comment their code with that language?

From the site:
> Since the word "ook" can convey entire ideas, emotions, and abstract thoughts depending on the nuances of inflection, Ook! has no need of comments. The code itself serves perfectly well to describe in detail what it does and how it does it. Provided you are an orang-utan.

---

### Post by lavinog on 2009-07-18
I tried some changes with the python code:
[php]
#!/usr/bin/env python

# prime number generator
from math import sqrt

def getprimes(num_start,num_end):
    #create list of numbers
    primes=[]
    
    #Cannot have any primes less than 2
    num_start=max(2,num_start)
    
    #Make sure the range makes sense
    if num_end < num_start: return primes
    
    #Calculate the point where we can quit doing math
    end_prime_limit=int(sqrt(num_end))+1
    
    # create range list from first primenumber 2
    r=[x for x in range(2,num_end)]
        
    #initialize nextprime
    nextprime=0
    
    #loop until no more calculations are needed
    while nextprime<end_prime_limit:
        
        # assume that the first value in list must be a prime
        nextprime=r.pop(0)
        
        # See if this prime exists within the range
        if nextprime >= num_start:
            primes.append( nextprime )
        
        # remove any value that is divisable by nextprime
        r = [x for x in r if x % nextprime != 0]
    
    # assume remaining values have to be prime and add to prime list
    primes+=[x for x in r if x >= num_start]
        
    return primes


def check_prime(num):
    dividend = 0
    check_to = int(sqrt(num))+1
    
    for dividend in range(2, check_to):
        if num % dividend == 0:
            return False
    return True

def primes_in_range(start, stop):
    current = 0
    primes=[]
    for current in range(start, stop):
        if check_prime(current) == True:
            primes.append(current)
    return primes



def main():
    import time
    ts=time.time()
    primes1=primes_in_range(0, 100000)
    exec_time=time.time()-ts
    print('primes_in_range time: '+str(exec_time))
    
    ts=time.time()
    primes2=getprimes(0,100000)
    exec_time=time.time()-ts
    print('getprimes time: '+str(exec_time))
    
    
    errors=( set(primes1)^set(primes2) )
    err1=list(set(primes1)&errors)
    err2=list(set(primes2)&errors)
    err1.sort()
    err2.sort()
    
    print('-'*15+'Discrepancies in primes_in_range'+'-'*15)
    print(err1)
    
    print('-'*15+'Discrepancies in getprimes'+'-'*15)
    print(err2)
    
    
main()
[/php]
Output
```

primes_in_range time: 1.68894290924
getprimes time: 0.294527053833
---------------Discrepancies in primes_in_range---------------
[0, 1]
---------------Discrepancies in getprimes---------------
[]

```
The discrepancies part was because primes_in_range was originally claiming the following as prime numbers:
```
[0, 1, 4, 6, 8, 9, 15, 25, 35, 49, 121, 143, 169, 289, 323, 361, 529, 841, 899, 961, 1369, 1681, 1763, 1849, 2209, 2809, 3481, 3599, 3721, 4489, 5041, 5183, 5329, 6241, 6889, 7921, 9409, 10201, 10403, 10609, 11449, 11663, 11881, 12769, 16129, 17161, 18769, 19043, 19321, 22201, 22499, 22801, 24649, 26569, 27889, 29929, 32041, 32399, 32761, 36481, 36863, 37249, 38809, 39203, 39601, 44521, 49729, 51529, 51983, 52441, 54289, 57121, 57599, 58081, 63001, 66049, 69169, 72361, 72899, 73441, 76729, 78961, 79523, 80089, 85849, 94249, 96721, 97343, 97969]

```

the problem was because the range function doesn't include the check_to value. Since int(sqrt(6))=2 and range(2,2)=[] 
[php]check_to = int(sqrt(num))
for dividend in range(2, check_to):[/php]

[s]I am sure that my function would fail if it is given a higher starting value, but it was my first attempt.[/s]
Edit: I cleaned it up some, made it so it can handle various ranges, and added comments

---

### Post by lavinog on 2009-07-18
I tried it with the different versions of python:
```

$ python2.5 py_prime.py 
calculating prime numbers between 0 and 1000000
getprimes time: 6.42114782333
primes_in_range time: 25.7403838634

$ python2.6 py_prime.py 
calculating prime numbers between 0 and 1000000
getprimes time: 6.52157092094
primes_in_range time: 25.8246600628

$ python3 py_prime.py 
calculating prime numbers between 0 and 1000000
getprimes time: 8.69975090027
primes_in_range time: 23.7864408493

```
Interesting that python3 slows down my function but speeds up the original both by 2 secs

---

### Post by Packard on 2009-07-18
Here is another python script based on the "Sieve of Eratosthenes":

```

import math

def getAllPrimes(lowerBound, upperBound):
    candidates = range(max(lowerBound, 2), upperBound)

    maxLoop = math.sqrt(upperBound)

    notPrimeMarker = set()

    for p in range(2, int(maxLoop)):
        for notPrime in range(2*p, upperBound,p):
                notPrimeMarker.add(notPrime)
    
    return list(set(candidates) - notPrimeMarker)
        

myPrimes = getAllPrimes(0, 100000)

print myPrimes

```

```

real	0m0.759s
user	0m0.364s
sys	0m0.008s

```

---

### Post by nvteighen on 2009-07-18
> **JordyD said:**
> 
Well, yes, I was aware that it's a dialect of Lisp, but I am still happier that I learned Common Lisp instead of Scheme.

Time for some realistic discussion about Common Lisp and Scheme.

First, I have to say I was using MIT/GNU Scheme in my tests. It's the "canonical" Scheme implementation.

Sadly, Scheme is much slower than Common Lisp because its compiler is really bad at optimizations. Compiler technology is much more advanced in Common Lisp and yields really good native code, while you have seen what Scheme's native compiler does.

The Scheme byte-compiler is even worse. The eager evaluated version needed 38 secs (vs. 24 secs when native-compiled) and the lazy evaluated gets surprisingly out of memory (vs. 20 secs. when native-compiled)... :p

While Scheme remains an academic language with little practical usage, Common Lisp is used as a practical language and therefore, the compiling techniques have been improved much more. Yes, my Scheme version is theorically impressive... it generates a **truly infinite list of all primes** using the Sieve of Eratosthenes and then just selects what corresponds to the range asked by the user. Much nicer than testing dividends, no doubt... sadly, at the cost of efficiency.

But I have no regret on having learned Scheme. It has made me a better programmer... and it's making my Common Lisp learning process much easier (Scheme is IMO a much better introduction to Lisp than CL... It's simpler and more transparent to learn the basics of Lisp and functional programming).

---

### Post by fr4nko on 2009-07-18
> **JordyD said:**
> I did use ocamlopt. Perhaps it does not like my CPU? It also jumps when it runs. I get results in chunks.

I will test it on my other computer.
Well, I don't why you get these bad results with ocaml. My only guess is that may be input/ouput can play a role in the speed. I've made a version with minimalist input/output to test just the execution speed. Here the code:

```

#include <stdio.h>
#include <stdbool.h>

bool check_prime(int num)
{
    int dividend;
    int check_to = num / 2;

    for (dividend = 2; dividend <= check_to; dividend++) {
        if (num % dividend == 0) {
            return false;
        }
    }

    return true;
}

void primes_in_range (int from, int to)
{
  int current;
  int count = 0;

  for (current = from; current <= to; current++)
    {
      if (check_prime(current))
    count ++;
    }

  printf ("found %d prime between %d and %d\n", count, from, to);
}

int main()
{
    primes_in_range(0, 100000);
}

```and in ocaml
```


let check_prime p' =
  let rec check_prime_rec p n up_to =
    if n > up_to then true else
      if p mod n = 0 then
    false
      else
    check_prime_rec p (n+1) up_to
  in
    check_prime_rec p' 2 (p' / 2)

let irange n =
  let rec citer ls i =
    if i < 0 then ls else citer (i :: ls) (i-1) in
    citer [] n

let check_print count n =
  if check_prime n then count + 1 else count
;;

let max_n = 100000;;

let count = List.fold_left check_print 0 (irange max_n) in
  Printf.printf "found %d prime between %d and %d\n" count 0 max_n
;;

```and here the results.
> 
francesco@vaio:~/tmp$ time ./mlprime 
found 9594 prime between 0 and 100000

real    0m1.142s
user    0m1.136s
sys    0m0.004s
francesco@vaio:~/tmp$ time ./cprime
found 9594 prime between 0 and 100000

real    0m1.008s
user    0m0.984s
sys    0m0.000s

If someone could do a test I would be interested. Here the code to compile:
> 
for ocaml:
> ocamlopt -c mlprime.ml && ocamlopt -o mlprime mlprime.cmx

and C:
gcc -O2 -fomit-frame-pointer -c cprime.c && gcc -o cprime cprime.o
Francesco

---

### Post by TheStatsMan on 2009-07-18
This is what I get with the Ocaml code

[php]Original Ocaml

real    0m5.658s
user    0m5.636s
sys    0m0.020s

Modified Ocaml
real    0m5.625s
user    0m5.620s
sys    0m0.000s

Original C
real    0m0.166s
user    0m0.040s
sys    0m0.012s[/php]

---

### Post by CptPicard on 2009-07-18
Just something to add to nvteighen's post... the difference in compilation speed between Scheme and CL comes from the fact that in CL the function/value namespace separation thing helps the compiler quite a bit, I believe. In Scheme you need to be resolving values all the time and seeing if they are indeed a function that is then callable. Scheme may be more elegant but it results in a performance hit...

Also JordyD, do take note that nobody actually uses the "do" construct, it's hideous (your version is really hard to read). It may have a role in some "low-level" code and macros and such... for iteration, most common-lispers use the "loop" macro, it is very versatile and more readable. Check out the chapter "Loop for black belts" in Practical Common Lisp.

---

### Post by JordyD on 2009-07-18
> **CptPicard said:**
> Just something to add to nvteighen's post... the difference in compilation speed between Scheme and CL comes from the fact that in CL the function/value namespace separation thing helps the compiler quite a bit, I believe. In Scheme you need to be resolving values all the time and seeing if they are indeed a function that is then callable. Scheme may be more elegant but it results in a performance hit...

Also JordyD, do take note that nobody actually uses the "do" construct, it's hideous (your version is really hard to read). It may have a role in some "low-level" code and macros and such... for iteration, most common-lispers use the "loop" macro, it is very versatile and more readable. Check out the chapter "Loop for black belts" in Practical Common Lisp.

Thank you, I'll read that section. Maybe I can improve the readability of the Lisp version.

---

### Post by fr4nko on 2009-07-18
> **TheStatsMan said:**
> This is what I get with the Ocaml code

[php]Original Ocaml

real    0m5.658s
user    0m5.636s
sys    0m0.020s

Modified Ocaml
real    0m5.625s
user    0m5.620s
sys    0m0.000s

Original C
real    0m0.166s
user    0m0.040s
sys    0m0.012s[/php]
Ok, so I just don't understand. In my system the difference between C and ocaml compiled with ocamlopt is between 5 and 10 % max. This is logical because ocaml produce highly efficient assembler code very close to what C would produce.

???

Francesco

---

### Post by JordyD on 2009-07-18
> **JordyD said:**
> Thank you, I'll read that section. Maybe I can improve the readability of the Lisp version.

OK, so this is what I have now:
```
(defun check-prime (num)
  (declare (type fixnum num))
  (if (< 2 num)
      (let ((chk-to 2))
	(loop for dividend from 2 upto chk-to
	   do (when (equal (rem num dividend) 0)
		(return nil))
	   finally (return t)))
      t))
(defun new-primes-in-range (start stop)
  (declare (type fixnum start stop))
  (loop for current from start to stop
       do (when (check-prime current)
	    (format t "~a~%" current))))
```

Better?

---

### Post by JordyD on 2009-07-18
> **fr4nko said:**
> Ok, so I just don't understand. In my system the difference between C and ocaml compiled with ocamlopt is between 5 and 10 % max. This is logical because ocaml produce highly efficient assembler code very close to what C would produce.

???

Francesco

What kind of CPU do you have? Again, maybe the compiler favors a specific architecture.

---

### Post by fr4nko on 2009-07-18
> **JordyD said:**
> What kind of CPU do you have? Again, maybe the compiler favors a specific architecture.
I have an Intel Core Duo CPU T8300 @ 2.4 GHz running a 2.6.28 kernel (ubuntu 9.04). So basically is 32bit dual core intel. And you ?

Francesco

---

### Post by JordyD on 2009-07-18
> **fr4nko said:**
> I have an Intel Core Duo CPU T8300 @ 2.4 GHz running a 2.6.28 kernel (ubuntu 9.04). So basically is 32bit dual core intel. And you ?

Francesco

Intel Pentium M Processor 1.86GHz.
Same kernel.

The other computer I tested on:
Hyper-threaded Intel Pentium 4 CPU 3.4GHz
Same kernel.

I got these from GNOME System Monitor.

---

### Post by TheStatsMan on 2009-07-18
From what I have read ocaml (I have been looking in to Ocaml for quite some time) should be similar speed to C, I doubt cpu has anything to do with it, there must be some logical reason. I have a 2.4 GHz core 2 duo, running 64 bit ubuntu FWIW.

---

### Post by JordyD on 2009-07-18
> **TheStatsMan said:**
> From what I have read ocaml (I have been looking in to Ocaml for quite some time) should be similar speed to C, I doubt cpu has anything to do with it, there must be some logical reason. I have a 2.4 GHz core 2 duo, running 64 bit ubuntu FWIW.

I agree, especially considering the range of CPUs we have.

---

### Post by fr4nko on 2009-07-18
Give me an ssh account with normal non-admin user privileges on you computer and I will be able to find the problem on your system... :-)

Francesco

---

### Post by CptPicard on 2009-07-18
> **JordyD said:**
> Better?

Yes... "loop" also has something that lets you declare the types of the iteration variables... it's a ":type" keyword parameter somewhere IIRC.

Now, stick this at the top of your file:

```

(declare (optimize (speed 3) (safety 0)))

```

SBCL will start complaining about information it is lacking to optimize everything to the max. I really love that particular feature. :)

---

### Post by lavinog on 2009-07-18
> **Packard said:**
> Here is another python script based on the "Sieve of Eratosthenes":

```

import math

def getAllPrimes(lowerBound, upperBound):
    candidates = range(max(lowerBound, 2), upperBound)

    maxLoop = math.sqrt(upperBound)

    notPrimeMarker = set()

    for p in range(2, int(maxLoop)):
        for notPrime in range(2*p, upperBound,p):
                notPrimeMarker.add(notPrime)
    
    return list(set(candidates) - notPrimeMarker)
        

myPrimes = getAllPrimes(0, 100000)

print myPrimes

```


```

$ python2.6 py_prime.py
calculating prime numbers between 0 and 1000000
getprimes time: 6.84277319908
getAllPrimes time: 3.87559008598
primes_in_range time: 30.2220668793

$ python3 py_prime.py
calculating prime numbers between 0 and 1000000
getprimes time: 8.18154406548
getAllPrimes time: 3.25986504555
primes_in_range time: 23.4960279465

```
Yours is faster, and it gets a slight speed improvement with python3

---

### Post by JordyD on 2009-07-18
> **CptPicard said:**
> Yes... "loop" also has something that lets you declare the types of the iteration variables... it's a ":type" keyword parameter somewhere IIRC.

Now, stick this at the top of your file:

```

(declare (optimize (speed 3) (safety 0)))

```

SBCL will start complaining about information it is lacking to optimize everything to the max. I really love that particular feature. :)

When I do a C-c C-k in EMACS, SBCL says, "The function SPEED is undefined."

**EDIT:** I hate these shortcuts. Especially since I use vim most of the time. Whenever I want to save I reach for the ESC key.

---

### Post by CptPicard on 2009-07-18
> **JordyD said:**
> When I do a C-c C-k in EMACS, SBCL says, "The function SPEED is undefined."

Interesting... well, been some time since I've been writing compiler hints. That's roughly how it is supposed to look like; rtfm ;)

---

### Post by JordyD on 2009-07-18
> **CptPicard said:**
> Interesting... well, been some time since I've been writing compiler hints. That's roughly how it is supposed to look like; rtfm ;)

:D I changed it to this:
```
(proclaim '(optimize (speed 3) (safety 0) (debug 0)))
(defun check-prime (num)
  (declare (type fixnum num))
  (if (< 2 num)
      (let ((chk-to 2))
	(loop for dividend from 2 upto chk-to
	   do (when (equal (rem num dividend) 0)
		(return nil))
	   finally (return t)))
      t))
(defun primes-in-range (start stop)
  (declare (type fixnum start stop))
  (loop for current from start to stop
     do (when (check-prime current)
	  (format t "~a~%" current))))
```

But, um. It slowed it down. (three consecutive runs)
```
real	0m1.080s
user	0m0.232s
sys	0m0.132s
```
```
real	0m1.219s
user	0m0.248s
sys	0m0.188s

```
```
real	0m1.252s
user	0m0.224s
sys	0m0.132s

```

---

### Post by ahmatti on 2009-07-20
I used Psyco (JIT for python, [http://psyco.sourceforge.net/](http://psyco.sourceforge.net/)) with the code in the OP and it run about 4x faster! All I did was installed python-psyco:

```
sudo apt-get install python-psyco
```

and added one line of code in the beginning of JordyD's code:

```
import psyco; psyco.full()
```

**And the results:**

Time for the original python code on my laptop:
```

real	0m2.079s
user	0m1.980s
sys	0m0.096s

```

Time with Psyco:
```

real	0m0.504s
user	0m0.408s
sys	0m0.084s

```

---

### Post by JordyD on 2009-07-20
Cool. I'll test that on my laptop and give the results of that run.

Results:
**OLD:**
```
real	0m2.384s
user	0m1.300s
sys	0m0.080s
```
**NEW:**
```
real	0m0.494s
user	0m0.176s
sys	0m0.064s

```

I think that's amazing. It's now faster than the Lisp version, although that could either be because it's just fast or I'm bad with Lisp.

---

### Post by ahmatti on 2009-07-20
Glad you like it! I only just find out about Psyco a few days ago and your code was a nice oppoturnity for me to test it, so thanks! I think you forgot to update the code in OP though...

---

### Post by JordyD on 2009-07-20
> **ahmatti said:**
> Glad you like it! I only just find out about Psyco a few days ago and your code was a nice oppoturnity for me to test it, so thanks! I think you forgot to update the code in OP though...

Yes, that's true. I always forget something. I'll update that now.

---

### Post by arcdrag on 2009-07-20
Just out of curiosity, has anyone done a comparison of execution times when compiled in Windows with Visual Studio?

---

### Post by JordyD on 2009-07-20
> **arcdrag said:**
> Just out of curiosity, has anyone done a comparison of execution times when compiled in Windows with Visual Studio?

I believe if someone does that, it would be best to place it in it's own thread. This is comparing everything on the same computer, which only has Ubuntu 9.04, and I don't wish to dual-boot. If you compare it on a different computer running Windows, it would be giving incorrect results because they're two different computers.

I would be interested in the results, though.

---

### Post by ahmatti on 2009-07-20
I wrote this in R just for fun and comparison, the result from:

```
R --vanilla <primes.R 
```

```

real    0m16.612s
user    0m16.245s
sys     0m0.364s

```

In case you're curious, it only runs about 1s faster if R is already loaded... 


And the code:

```
checkprime <- function(num){
  dividend <- 0
  checkto  <- round(sqrt(num))
  for (dividend in 2:checkto){
    if (num %% dividend == 0) return(FALSE)
  }
  return(TRUE)
}
               
primes_in_range <- function(start, end){
  current <- 0
  for (current in start:end){
    if (checkprime(current) == TRUE){
    print(current)
    }
  }  
}

primes_in_range(0, 100000)

```

---

### Post by JordyD on 2009-07-20
Interpreted?

---

### Post by ahmatti on 2009-07-20
> **JordyD said:**
> Interpreted?

Yes, R ([www.r-project.org](www.r-project.org)) is an interactive high level scripting language (or an FOSS implementation of S language) for data and statistical analysis. Its fast to write, but the loops are slow and I couldn't think of a way to vectorize this...

---

### Post by JordyD on 2009-07-20
> **ahmatti said:**
> Yes, R ([www.r-project.org](www.r-project.org)) is an interactive high level scripting language (or an FOSS implementation of S language) for data and statistical analysis. Its fast to write, but the loops are slow and I couldn't think of a way to vectorize this...

Neat. I probably won't ever learn it, but I like the function declarations.

---

### Post by unutbu on 2009-07-20
There is a slight logical error in the python implementation.
In check_prime function needs
```
range(2, check_to+1)
```
rather than
```

range(2, check_to)
```

On this line:
```
    for dividend in range(2, check_to+1):
```

Otherwise, the loop is not checking up-to-and-including check_to.
(A side-effect of the bug is that 4 is being reported as a prime...)

And while we're at it, perhaps change 
```

        if check_prime(current) == True:
```

to
```

        if check_prime(current):
```

---

### Post by JordyD on 2009-07-20
> **unutbu said:**
> There is a slight logical error in the python implementation.
In check_prime function needs
```
range(2, check_to+1)
```
rather than
```

range(2, check_to)
```

On this line:
```
    for dividend in range(2, check_to+1):
```

Otherwise, the loop is not checking up-to-and-including check_to.
(A side-effect of the bug is that 4 is being reported as a prime...)

And while we're at it, perhaps change 
```

        if check_prime(current) == True:
```

to
```

        if check_prime(current):
```

I did not notice this. Probably because it prints so much that I can't scroll up to see what it printed first. I will change this.

**EDIT:** Why "if check_prime(current):" -> "if check_prime(current) == True:". Would this not be slower? Plus, it's the same thing.

I changed the assignment of check_to to the square root + 1. It reads better that way (IMO).

So it looks like:
```
check_to = int(sqrt(num)) + 1
```

---

### Post by unutbu on 2009-07-20
> Why "if check_prime(current):" -> "if check_prime(current) == True:". Would this not be slower? Plus, it's the same thing.

Well, somewhere I read that using
```

if (condition) == True
```

is bad form since "if" is always going to check if condition == True.
I assume if it is "bad form" then it can not be faster, though I haven't check this.

---

### Post by JordyD on 2009-07-20
> **unutbu said:**
> Well, somewhere I read that using
```

if (condition) == True
```

is bad form since if is always going to check if condition == True.
I assume if it is "bad form" then it can not be faster, though I haven't check this.

Ahh, sorry, I had not looked at my code recently and I had thought that this is how I wrote it (without True).

I thought you were saying to change it to plus "== True:", not subtract that.

Anyways, I'll change my code.

---

### Post by fr4nko on 2009-07-20
May be someone with a quad core can try this parallelized version:
```

#include <stdio.h>
#include <stdbool.h>
#include <math.h>

bool check_prime(int num)
{
    int dividend;
    int check_to = floor(sqrt(num));

    for (dividend = 2; dividend <= check_to; dividend++) {
        if (num % dividend == 0) {
            return false;
        }
    }

    return true;
}

void primes_in_range (int from, int to)
{
    int current;

#pragma omp parallel for
    for (current = from; current <= to; current++) {
        if (check_prime(current))
            printf("%d\n", current);
    }
}

int main()
{
  int j;
  for (j = 0; j < 10; j++)
    primes_in_range(0, 800000);
}

```it can be compiled with the following:
> 
gcc -fopenmp -O2 -fomit-frame-pointer -c cmpprime.c
gcc -o cmpprime cmpprime.o -lm -lgomp
On my system make no difference.

Francesco

---

### Post by pepperphd on 2009-07-20
Anyone tried putting 'register' before the commonly accessed and modified variable declarations in the C version?

---

### Post by JordyD on 2009-07-20
> **pepperphd said:**
> Anyone tried putting 'register' before the commonly accessed and modified variable declarations in the C version?

What does it do?

---

### Post by fr4nko on 2009-07-20
The register keyword suggest to the C compiler to keep the variable in the CPU register instead of using the stack. It can improve the speed of some tight loop but nowadays I consider that any decent compiler can figure out by himself when is better to use the register or not.

Francesco

---

### Post by monraaf on 2009-07-20
> **fr4nko said:**
> May be someone with a quad core can try this parallelized version:
```

#include <stdio.h>
#include <stdbool.h>
#include <math.h>

bool check_prime(int num)
{
    int dividend;
    int check_to = floor(sqrt(num));

    for (dividend = 2; dividend <= check_to; dividend++) {
        if (num % dividend == 0) {
            return false;
        }
    }

    return true;
}

void primes_in_range (int from, int to)
{
    int current;

#pragma omp parallel for
    for (current = from; current <= to; current++) {
        if (check_prime(current))
            printf("%d\n", current);
    }
}

int main()
{
  int j;
  for (j = 0; j < 10; j++)
    primes_in_range(0, 800000);
}

```it can be compiled with the following:
On my system make no difference.

Francesco

On a dual-core:

```

        normal:    with gomp:
-------------------------------
real	0m9.188s   0m5.646s
user	0m9.153s   0m7.768s
sys	0m0.020s   0m0.360s

```

Nice!

---

### Post by JordyD on 2009-07-20
> **fr4nko said:**
> The register keyword suggest to the C compiler to keep the variable in the CPU register instead of using the stack. It can improve the speed of some tight loop but nowadays I consider that any decent compiler can figure out by himself when is better to use the register or not.

Francesco

So it's not often used because (good) compilers can figure it out by themselves?

---

### Post by fr4nko on 2009-07-20
exactly. I can also add that gcc *is* a good compiler and that's enough... :-)

---

### Post by JordyD on 2009-07-20
> **fr4nko said:**
> exactly. I can also add that gcc *is* a good compiler and that's enough... :-)

Leading to why I've never heard of it before. :D

---

### Post by fr4nko on 2009-07-20
Nice!
I've discovered that on my laptop to see any difference I need to do something like
> 
time ./cprime &> /dev/null

because otherwise the I/O limit the speed and the CPU never get charged.

Francesco

---

### Post by Ariel David Moya Sequeira on 2009-07-20
As a scientist, I'd suggest to do these tests several times and then compute the average execution time. I'm going to test UCBLogo's power with these algorithms, just to compare.

I know many have the following in mind, but I have to say: excecution time depends on the Operating System, hardware and a plethora of other specifications. So, comparisons must be made based on computations on one computer, under the sme circumstances.

---

### Post by tom66 on 2009-07-20
Even faster:

```

#include <stdio.h>
#include <stdbool.h>
#include <math.h>

bool check_prime(int num)
{
    register int dividend;
    int check_to = (int)(sqrt(num));

    for (dividend = 2; dividend <= check_to; dividend++) {
        // speed up modulo.
        if (num > dividend) {
        	// speed up modulo if power of two.
        	if ((dividend & (dividend - 1)) == 0)
        	    if(num & dividend == 0)
        	        return false;
        	
        	if (num % dividend == 0) {
        	    return false;
        	}
        }
    }

    return true;
}

void primes_in_range (int from, int to)
{
    register int current;

#pragma omp parallel for
    for (current = from; current <= to; current += 2) { // even numbers, excluding two, are NEVER primes.
        if (check_prime(current))
            printf("%d\n", current);
    }
}

int main()
{
  register int j;
  
  // Two is a special case. Output it.
  printf("2\n");
  
  for (j = 0; j < 10; j++)
    primes_in_range(3, 800000);
}

```

I am not sure it is producing correct output but it should be. I have optimised the division loop.

```

real	0m1.875s
user	0m2.900s
sys	0m0.068s

```

Compile using:

```

gcc -fopenmp -O2 -fomit-frame-pointer -c p.c && gcc -o p p.o -lm -lgomp

```

---

### Post by tom66 on 2009-07-20
Sorry, there was a bug in the last code. The modulo code was broken. Just change the check_prime function to this:

```

bool check_prime(int num)
{
    register int dmn1;
    register int dividend;
    int check_to = (int)sqrt((int)num);

    for (dividend = 2; dividend <= check_to; dividend++) {
        // speed up modulo.
        if (num > dividend) {
            dmn1 = dividend - 1;
            
        	// speed up modulo if power of two.
        	if ((dividend & dmn1) == 0)
        	    if(num & dmn1 == 0)
        	        return false;
        	
        	if (num % dividend == 0) {
        	    return false;
        	}
        }
    }

    return true;
}

```

---

### Post by gunksta on 2009-07-21
Ahmatti: You REALLY shouldn't use loops in R.

:-)

Here was the original looped R code:

```

checkprime <- function(num){
  dividend <- 0
  checkto  <- round(sqrt(num))
  for (dividend in 2:checkto){
    if (num %% dividend == 0) return(FALSE)
  }
  return(TRUE)
}
               
primes_in_range <- function(start, end){
  current <- 0
  for (current in start:end){
    if (checkprime(current) == TRUE){
    print(current)
    }
  }  
}

primes_in_range(0, 100000)

```I ran some tests (N=10).
Average Time = 8.08 seconds (User)
Standard Deviation 0.22 seconds (User)


R is bad at loops. That's why we don't use them! Compare these results to my vectorized R code below.

**EDIT:** My original code for is.prime (and ahmatti's) contain an error where 2 is returned as NOT prime. I've corrected this in the code below.

```

is.prime <- function(num){
  if (num==2) return(1) else {
    check <- 2:round(sqrt(num))
    min(num%%check)
  }
}
               
primes_in_range <- function(start, end){
  numbers <- start:end
  out <- lapply(numbers, is.prime)
  primes <- which(out==1)
  numbers[primes]
}
  

primes_in_range(0, 100000)


```I'm sure I could optimize it some more, but a basic vectorized code brings R's times down to something much more similar to Python. Since both are interpreted languages, I'll accept that as acceptable. (Note: R is not really meant to shine in this sort of test but that's a separate discussion.)

I re-ran my tests (N=10). 
Average Time = 2.55 seconds (User)
Standard Deviation=0.06 seconds (User).

Not only is the vectorized code much faster, it's more consistent. For both code snippets I timed it with: 
```
time --verbose R --vanilla -f primes.R
```Using --vanilla is especially important since my R session loads several custom scripts and what not which could have (minimally) affected the output of the code (although it would have affected both more or less equally).

---

### Post by ahmatti on 2009-07-22
> **gunksta said:**
> Ahmatti: You REALLY shouldn't use loops in R.

:-)

Not only is the vectorized code much faster, it's more consistent.

Hi Gunksta,
I totally agree, but it was late when I wrote that and couldn't think of vectorized solution. I also kind of wanted to see if R loops really deserve their reputation of running snail speed, well seems that they do...

**Anyway, I really wanted to thank you for a nice solution!** Your solution was about 2 times faster than my original one on my PC (1.6 Ghz Turion, Feisty 9.04 32bit) (16.6 s): 

```

real	0m6.766s
user	0m6.404s
sys	0m0.120s

```

Note though (well you probably know this, but maybe others don't) that lapply also has an internal loop, so it is not actual vectorization and can be in some cases even slower than a for loop. I tried replacing lapply with a loop and speed difference is about 0.2 s in favor of lapply this time (given the small std's I'm not going to post it here ;))

**EDIT:** OK, I just made a small change to your and was able to speed it up a few seconds:

```

real	0m4.072s
user	0m3.824s
sys	0m0.084s

```

And the change was replacing: 

```

test <- rep(num, length(check))
min(test%%check)

```

with:
```

min(num %% check)

```

---

### Post by gunksta on 2009-07-22
> **ahmatti said:**
> Hi Gunksta,
```

test <- rep(num, length(check))
min(test%%check)

```with:
```

min(num %% check)

```

That makes sense. For grins and giggles I will use this edit and think about it at work to see if I can come up with any other optimizations.

---

### Post by smartbei on 2009-07-22
I jut noticed something - in the python test code you use range(). The range function in python is significantly slower than the xrange function, especially for large values of N. the use is exactly the same, just add an x. Changing this in both the places where range is used reduced the time by about 0.01 on average on my computer.

By the way, I hope you realize that on this test the only reason the python program is so close to the C one is 1) the use of psyco which makes the memory use go way up and 2) the fact that you are printing the output, which slows all of the programs down significantly.

---

### Post by nvteighen on 2009-07-22
> **smartbei said:**
> I jut noticed something - the range function in python is significantly slower than the xrange function, especially for large values of N. the use is exactly the same, just add an x. Changing this in both the places where range is used reduced the time by about 0.01 on average on my computer.


Because range() returns a list, while xrange() an iterator object. IIRC, Python 3.0 replaces range()'s behaivor by xrange()'s and removes xrange().

---

### Post by slavik on 2009-07-23
Perl code.

```

time perl -e '
use integer; 
print "2\n"; 
for ($i=3; $i<=100000; $i+=2) { 
  print $i."\n" if prime($i); 
};

sub prime { 
  $n = shift; 
  $sq = sqrt($n); 
  for ($j=3;$j<=$sq;$j++) { 
    return 0 if ($n%$j == 0); 
  } 
  return 1; 
}
'

```

```

slavik@slavik-desktop:~$ time perl -e 'use integer; print "2\n"; for ($i=3; $i<=100000; $i+=2) { print $i."\n" if prime($i); }; sub prime { $n = shift; $sq = sqrt($n); for ($j=3;$j<=$sq;$j++) { return 0 if ($n%$j == 0); } return 1; }' > /dev/null

real	0m0.483s
user	0m0.480s
sys	0m0.004s
slavik@slavik-desktop:~$ 

with output (no redirect to dev null):
real	0m0.551s
user	0m0.444s
sys	0m0.048s


```

edit: after some optimization:
```

slavik@slavik-desktop:~$ time perl -e 'use integer; print "2\n"; for ($i=3; $i<=100000; $i+=2) { print $i."\n" if prime($i); }; sub prime { $n = shift; $sq = sqrt($n); for ($j=3;$j<=$sq;$j+=2) { return 0 if ($n%$j == 0); } return 1; }' > /dev/null

real	0m0.326s
user	0m0.324s
sys	0m0.004s
slavik@slavik-desktop:~$ 

with output:
real	0m0.363s
user	0m0.300s
sys	0m0.040s

```

Hint: 2 is the only even prime.

---

### Post by Nigmastar on 2012-11-09
> **ahmatti said:**
> I wrote this in R just for fun and comparison, the result from:
 
```
R --vanilla <primes.R 
```
 
```

real    0m16.612s
user    0m16.245s
sys     0m0.364s

```
 
In case you're curious, it only runs about 1s faster if R is already loaded... 
 
 
And the code:
 
```
checkprime <- function(num){
  dividend <- 0
  checkto  <- round(sqrt(num))
  for (dividend in 2:checkto){
    if (num %% dividend == 0) return(FALSE)
  }
  return(TRUE)
}
 
primes_in_range <- function(start, end){
  current <- 0
  for (current in start:end){
    if (checkprime(current) == TRUE){
    print(current)
    }
  }  
}
 
primes_in_range(0, 100000)

```
 
 
Hi! Your code is so slow because of the print comand which make to run like a slug. In this way, putting all the prime numbers found in a vector and returning it via return(output) at the end, you can save lots of time, from 16s to around 6.5s. But the major step is in compiling the function via the "compiler" package. 
 
 
```
 
library("compiler")
 
checkprime <- function(num){
  checkto  <- round(sqrt(num))
  for (dividend in 2:checkto){
    if (num %% dividend == 0) return(FALSE)
  }
  return(TRUE)
}
 
checkprime<-cmpfun(checkprime)
 
primes_in_range <- function(start, end){
  output  <- 0
  for (current in start:end){
    if (checkprime(current) == TRUE){
      output <- c(output,current)
    }
  }
  return(output)
}
 
primes_in_range<-cmpfun(primes_in_range)
 
system.time(primes_in_range(0, 100000))

```
 
Before compiling
```
  
user  system elapsed   
6.26    0.00    6.27

```
 
After compiling
```
 
user  system elapsed
1.88    0.00    1.87

``` 
 
Hope that helps!Bye!

---

