---
title: "Beginner Programming Challenge #10"
date: 2010-03-07
forum: Programming Talk
---

### Post by cprofitt on 2010-03-07
Welcome to the 10th programming challenge, sponsored by [The Ubuntu Beginners Team Development Focus Group]("https://wiki.ubuntu.com/BeginnersTeam/FocusGroups/Development"). I have been tasked with coming up with this challenge by virtue of 'winning' [programming challenge #9]("http://ubuntuforums.org/showthread.php?t=1407897"). 
[B]
background[/B]:
----- 
I have a connection with Lychrel numbers so I wanted to make this challenge something in relation to those. 

**lychrel numbers**:
-----
A Lychrel number is a natural number which cannot form a palindrome through the iterative process of repeatedly reversing its digits and adding the resulting numbers. The name "Lychrel" was coined by Wade VanLandingham; a rough anagram of his girlfriend's name Cheryl.

example: The reverse and add process produces the sum of a number and the number formed by reversing the order of its digits.eg. 56 + 65 = 121, 125 + 521 = 646, 9999 + 9999 = 19998


**task**:
-----
Find all the Lychrel candidate numbers below 10,000
[B]

:KS bonus points[/B]:
-----
Find all the Lychrel seed numbers below 10,000


**:confused: Disqualified Entries**:
-----
Any overly obfuscated code will be immediately disqualified without account for programmers skill. Please remember that these challenges are for beginners and therefore the code should be easily readable and well commented.

Any non-beginner entries will not be judged. Please use common sense when posting code examples. Please do not give beginners a copy paste solution before they have had a chance to try this for themselves.


**:KS Assistance**:
-----
If you require any help with this challenge please do not hesitate to come and chat to the development focus group. We have a channel on irc.freenode.net #ubuntu-beginners-dev

----------
OK -- time for you all to be :guitar: rockstars!

---

### Post by paultag on 2010-03-07
Looks great! Let's see some entries, people!

---

### Post by schauerlich on 2010-03-07
I'm not sure I'd call this a "beginner" challenge...

---

### Post by conehead77 on 2010-03-07
> **schauerlich said:**
> I'm not sure I'd call this a "beginner" challenge...

+1

Is 196 a Lychrel number? Nobody knows, it hasn't been proven yet. So 196 would be a Lychrel candidate number? But how many iterations should be made before calling a number a Lychrel candidate? And what is a Lychrel seed number?

---

### Post by s.fox on 2010-03-07
I think its a good challenge. 

I am going to do it in a language I am still a bit green with:  **Python** :D

-Silver Fox

---

### Post by s.fox on 2010-03-07
> **conehead77 said:**
> What is a Lychrel seed number?

From [Wikipedia]("http://en.wikipedia.org/wiki/Lychrel_number#Threads.2C_seed_and_kin_numbers"):
> 
Seed numbers are a subset of Lychrel numbers, that is the smallest number of each non palindrome producing thread. A seed number may be a palindrome itself.
-Silver Fox

---

### Post by schauerlich on 2010-03-07
> **conehead77 said:**
> +1

Is 196 a Lychrel number? Nobody knows, it hasn't been proven yet. So 196 would be a Lychrel candidate number? But how many iterations should be made before calling a number a Lychrel candidate? And what is a Lychrel seed number?

Wikipedia says that the largest number of iterations for a number under 10,000 to resolve to a palindrome is 24. So I'd say go for 30 iterations before calling it a lychrel candidate.

---

### Post by Bachstelze on 2010-03-07
Obligatory Haskell. ;)

[php]readInt             :: String -> Int
reverseInt          :: Int -> Int
isPalindrome        :: Int -> Bool
isCandidate         :: (Int, Int) -> Bool

readInt             = read

reverseInt n        = if n < 10
                        then n
                        else readInt (reverse (show n))

isPalindrome n      = if n < 10
                        then True
                        else ns == reverse ns
                            where ns = show n

isCandidate (30, _) = True
isCandidate (n, p)  = if isPalindrome p
                        then False
                        else isCandidate (n + 1, p + reverseInt p)

main = print [n | n <- [1..9999], isCandidate (0, n)][/php]

I'll do the seed-hunting later. I don't think it really needs commenting, but someone correct me if I'm wrong. :p

---

### Post by Bachstelze on 2010-03-07
> **schauerlich said:**
> Wikipedia says that the largest number of iterations for a number under 10,000 to resolve to a palindrome is 24. So I'd say go for 30 iterations before calling it a lychrel candidate.

Yup. I went up to 10,000 iterations, and it gave me the same results as 30.

---

### Post by howlingmadhowie on 2010-03-07
here's my first scheme implementation.  
```

(use-modules (ice-9 format))

(define num->chain
  (lambda (num)
    (if (< num 10)
        (list num)
        (cons (remainder num 10) (num->chain (quotient num 10))))))

(define reverse-chain
  (lambda (c)
    (define reverse-helper
      (lambda (l-in l-out)
        (if (null? l-in)
            l-out
            (reverse-helper (cdr l-in) (cons (car l-in) l-out)))))
    (reverse-helper c '())))

(define empty-chain? null?)

(define chain->num
  (lambda (chain)
    (if (empty-chain? chain)
        0
        (+ (car chain) (* 10 (chain->num (cdr chain)))))))

(define is-palindrome?
  (lambda (n)

    (define same-chain?
      (lambda (c1 c2)
        (cond ((empty-chain? c1)
               (if (empty-chain? c2)
                   #t
                   #f))
              ((empty-chain? c2)
               (if (empty-chain? c1)
                   #t
                   #f))
              ((= (car c1) (car c2))
               (same-chain? (cdr c1) (cdr c2)))
              (else #f))))

    (same-chain? n (reverse-chain n))))

(define find-lychrel-numbers
  (lambda (limit max-tries)

    (define iterate
      (lambda (chain)
        (num->chain (+ (chain->num chain) (chain->num (reverse-chain chain))))))

    (define is-lychrel-number?
      (lambda (chain try)
        (cond ((> try max-tries)
               #f)
              ((is-palindrome? chain)
               (chain->num chain))
              (else
               (is-lychrel-number? (iterate chain) (+ try 1))))))

    (define loop
      (lambda (number)
        (if (< number limit)
            (let ((result (is-lychrel-number? (num->chain number) 0)))
              (if (not result)
                  (format #t "~d is a candidate\n" number))
              (loop (+ 1 number))))))

    (loop 1)))

(find-lychrel-numbers 10000 40)

```

it works by storing the numbers in chains of digits and then reversing these chains and adding them. this saves the overhead of using int->string and string->int conversion.

in case anybody's interested, it takes this much time:
```

howlingmadhowie% time guile lychrel.scm 1>/dev/null
guile lychrel.scm > /dev/null  2,02s user 0,01s system 98% cpu 2,065 total

```

---

### Post by Bachstelze on 2010-03-07
> **howlingmadhowie said:**
> 
in case anybody's interested, it takes this much time:
```

howlingmadhowie% time guile lychrel.scm 1>/dev/null
guile lychrel.scm > /dev/null  2,02s user 0,01s system 98% cpu 2,065 total

```

Beat you ;)

```
firas@momiji ~ % time ./lychrel > /dev/null
./lychrel > /dev/null  0.23s user 0.00s system 94% cpu 0.242 total
```

---

### Post by howlingmadhowie on 2010-03-07
> **Bachstelze said:**
> Beat you ;)

```
firas@momiji ~ % time ./lychrel > /dev/null
./lychrel > /dev/null  0.23s user 0.00s system 94% cpu 0.242 total
```

interesting. haskell must have some pretty good number/string conversion functions. i imagine my code is slow because of the huge amounts of quotient and remainder functions in it, but i can get around that by writing a function to add two chains. maybe i'll do that and see if it's faster ...

---

### Post by snova on 2010-03-07
> **howlingmadhowie said:**
> interesting. haskell must have some pretty good number/string conversion functions. i imagine my code is slow because of the huge amounts of quotient and remainder functions in it, but i can get around that by writing a function to add two chains. maybe i'll do that and see if it's faster ...

Python seems to be similar. This code:

[PHP]int(str(n)[::-1])[/PHP]

will outperform this code:

[PHP]
def reverse_digits(n):
    r = 0
    while n:
        n, t = divmod(n, 10)
        r = r * 10 + t
    return r
[/PHP]

Though this isn't entirely surprising, as generally the more time Python code spends in C, the faster it runs.

---

### Post by schauerlich on 2010-03-07
A fairly simple C implementation. It uses recursion, which may be a little tricky for beginners, but hopefully my comments explain it well enough. It's certainly not the most efficient method (converting to a string, reversing the string and atol()'ing it), but it gets the job done. 

I decided to do recursion because I'm not very good at it. :)

```
[color=#BC7A00]#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_LYCHREL 10000
#define DEPTH 30
[/color]
[color=#B00040]void[/color] [color=#0000FF]reverse[/color]([color=#B00040]char[/color] [color=#666666]*[/color]str, [color=#B00040]char[/color] [color=#666666]*[/color]rev_str) {
  [color=#408080][i]// reverses str and stores it in rev_str
[/i][/color]  
  [color=#B00040]long[/color] len [color=#666666]=[/color] strlen(str); [color=#408080][i]// get the length of the string
[/i][/color]  [color=#B00040]long[/color] i;
  
  [color=#008000]**if**[/color] ([color=#666666]![/color]len) [color=#408080][i]// if the string is empty
[/i][/color]    [color=#008000]**return**[/color];
  
  [color=#008000]**for**[/color] (i [color=#666666]=[/color] [color=#666666]0[/color]; i [color=#666666]<[/color] len; i[color=#666666]++[/color]) { [color=#408080][i]// for each char in the string
[/i][/color]    [color=#408080][i]// put the i-th char from the back of str into the i-th position
[/i][/color]    [color=#408080][i]// of rev_str. For instance, put the second to last character of str
[/i][/color]    [color=#408080][i]// into the second position in rev_str.
[/i][/color]    rev_str[i] [color=#666666]=[/color] str[len [color=#666666]-[/color] i [color=#666666]-[/color] [color=#666666]1[/color]];
  } [color=#408080][i]// for i
[/i][/color]  
  [color=#408080][i]// C ends all of its strings in '\0' characters, so we need to add one
[/i][/color]  [color=#408080][i]// to the end so that string functions know where the string is
[/i][/color]  [color=#408080][i]// supposed to end
[/i][/color]  rev_str[len] [color=#666666]=[/color] [color=#BA2121]'\0'[/color];
  
} [color=#408080][i]// reverse()
[/i][/color]

[color=#B00040]int[/color] [color=#0000FF]islychrel[/color]([color=#B00040]long[/color] n, [color=#B00040]long[/color] d) {
  [color=#408080][i]// recursively decides if a number is a lychrel candidate after depth d
[/i][/color]  
  [color=#408080][i]// allocate strings for n and its reverse, and a long int for n's reverse
[/i][/color]  [color=#B00040]char[/color] nStr[[color=#666666]100[/color]], nRevStr[[color=#666666]100[/color]];
  [color=#B00040]long[/color] nRev;
  
  [color=#408080][i]// convert n to a string
[/i][/color]  sprintf(nStr, [color=#BA2121]"%ld"[/color], n);
  
  [color=#408080][i]// reverse n and put it in a string
[/i][/color]  reverse(nStr, nRevStr);
  
  [color=#408080][i]// convert that string to a long int
[/i][/color]  nRev [color=#666666]=[/color] atol(nRevStr);
  
  [color=#408080][i]// if we've reached the maximum recursion depth, we're done, so 
[/i][/color]  [color=#408080][i]// return true (ie, n is a lychrel candidate)
[/i][/color]  [color=#008000]**if**[/color] (d [color=#666666]<=[/color] [color=#666666]0[/color])
    [color=#008000]**return**[/color] [color=#666666]1[/color];
  
  [color=#408080][i]// if the number is a palindrome, we're done and should return false
[/i][/color]  [color=#408080][i]// (n is NOT a lychrel candidate)   
[/i][/color]  [color=#008000]**if**[/color] (d [color=#666666]!=[/color] DEPTH [color=#666666]&&[/color] n [color=#666666]==[/color] nRev)
    [color=#008000]**return**[/color] [color=#666666]0[/color];
  
  [color=#408080][i]// now we go around again, this time checking if the number plus its reverse is
[/i][/color]  [color=#408080][i]// a palindrome. We decrement the depth so that once it gets to zero, we give up
[/i][/color]  [color=#408080][i]// and the recursion "unwinds"
[/i][/color]  [color=#008000]**return**[/color] islychrel(n [color=#666666]+[/color] nRev, d [color=#666666]-[/color] [color=#666666]1[/color]);
  
} [color=#408080][i]// islychrel()
[/i][/color]


[color=#B00040]int[/color] [color=#0000FF]main[/color]([color=#B00040]int[/color] argc, [color=#B00040]char[/color] [color=#666666]*[/color]argv[]) {
  [color=#B00040]long[/color] i;
  
  [color=#408080][i]// iterate through 0 - MAX_LYCHREL (for this challenge, 10000)
[/i][/color]  [color=#408080][i]// and print it out if it's a lychrel candidate
[/i][/color]  [color=#008000]**for**[/color] (i [color=#666666]=[/color] [color=#666666]0[/color]; i [color=#666666]<=[/color] MAX_LYCHREL; i[color=#666666]++[/color])
    [color=#008000]**if**[/color] (islychrel(i, DEPTH))
      printf([color=#BA2121]"%ld[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], i);
  
  [color=#008000]**return**[/color] [color=#666666]0[/color];
  
} [color=#408080][i]// main()
[/i][/color]
```

```
real	0m0.039s
user	0m0.023s
sys	0m0.004s
```

---

### Post by schauerlich on 2010-03-07
I decided to try it in python, a language I never really got into... wrote this in about 5 minutes. It's pretty much the same as [my C entry](http://ubuntuforums.org/showpost.php?p=8932014&postcount=14), but python lists and easy casting between strings and ints made it much faster to write.

```
[color=#408080]*#!/usr/bin/env python*[/color]

DEPTH [color=#666666]=[/color] [color=#666666]30[/color]
MAX_LYCHREL [color=#666666]=[/color] [color=#666666]10000[/color]

[color=#008000]**def**[/color] [color=#0000FF]islychrel[/color](n, d):
    [color=#408080]*# recursively decides if a number is a lychrel candidate,*[/color]
    [color=#408080]*# giving up after d tries.*[/color]
    
    [color=#408080]*# convert n to a string*[/color]
    nStr [color=#666666]=[/color] [color=#008000]str[/color](n)
    
    [color=#408080]*# reverse it. This uses a funky way of slicing nStr*[/color]
    nRevStr [color=#666666]=[/color] nStr[::[color=#666666]-[/color][color=#666666]1[/color]]
    
    [color=#408080]*# make an int out of the reversed string*[/color]
    nRev [color=#666666]=[/color] [color=#008000]int[/color](nRevStr)
    
    [color=#408080]*# d will equal zero when we've hit our maximum recursion*[/color]
    [color=#408080]*# depth - that is, when we've gone through a bunch of times*[/color]
    [color=#408080]*# without finding a palindrome. This means the number IS a*[/color]
    [color=#408080]*# lychrel candidate and we should return True*[/color]
    [color=#008000]**if**[/color] d [color=#666666]<=[/color] [color=#666666]0[/color]:
        [color=#008000]**return**[/color] [color=#008000]True[/color]
    
    [color=#408080]*# if the number and its reverse are equal, then the*[/color]
    [color=#408080]*# number is a palindrome. This means the number*[/color]
    [color=#408080]*# is NOT a lychrel candidate and we should return False*[/color]
    [color=#008000]**if**[/color] d [color=#666666]!=[/color] DEPTH [color=#AA22FF]**and**[/color] n [color=#666666]==[/color] nRev:
        [color=#008000]**return**[/color] [color=#008000]False[/color]
    
    [color=#408080]*# if neither of our base cases are met, then we should try*[/color]
    [color=#408080]*# the same thing again, this time adding the number and its*[/color]
    [color=#408080]*# reverse, and decrementing the depth.*[/color]
    [color=#008000]**return**[/color] islychrel(n [color=#666666]+[/color] nRev, d [color=#666666]-[/color] [color=#666666]1[/color])

[color=#008000]**def**[/color] [color=#0000FF]main[/color]():
    [color=#408080]*# for every number between 0 and 10000,*[/color]
    [color=#408080]*# if the number is a lychrel candidate,*[/color]
    [color=#408080]*# print it*[/color]
    [color=#008000]**for**[/color] i [color=#AA22FF]**in**[/color] [color=#008000]range[/color]([color=#666666]0[/color], MAX_LYCHREL):
        [color=#008000]**if**[/color] islychrel(i, DEPTH):
            [color=#008000]**print**[/color] i

[color=#008000]**if**[/color] __name__ [color=#666666]==[/color] [color=#BA2121]"__main__"[/color]:
    main()

```
```
real	0m0.188s
user	0m0.164s
sys	0m0.016s
```

---

### Post by howlingmadhowie on 2010-03-07
okay. this one finds the seeds as well:

```

(use-modules (ice-9 format))

(define reverse-chain
  (lambda (c)
    (define reverse-helper
      (lambda (l-in l-out)
	(if (null? l-in)
	    l-out
	    (reverse-helper (cdr l-in) (cons (car l-in) l-out)))))
    (reverse-helper c '())))

(define num->chain
  (lambda (num)
    (if (< num 10)
	(list num)
	(cons (remainder num 10) (num->chain (quotient num 10))))))


(define empty-chain? null?)

(define add-chains
  (lambda (c1 c2)

    (define add-links
      (lambda (l1 l2 carry)
	(let ((num (+ l1 l2 carry)))
	  (if (> num 9)
	      (cons 1 (- num 10))
	      (cons 0 num)))))

    (define loop
      (lambda (c1 c2 carry)
	(cond ((and (null? c1) (null? c2))
	       (if (> carry 0)
		   (list carry)
		   '()))
	      ((null? c1)
	       (let ((new-link (add-links 0 (car c2) carry)))
		 (cons (cdr new-link) (loop '() (cdr c2) (car new-link)))))
	      ((null? c2)
	       (let ((new-link (add-links (car c1) 0 carry)))
		 (cons (cdr new-link) (loop (cdr c1) '() (car new-link)))))
	      (else
	       (let ((new-link (add-links (car c1) (car c2) carry)))
		 (cons (cdr new-link) (loop (cdr c1) (cdr c2) (car new-link))))))))

    (loop c1 c2 0)))

(define chain->num
  (lambda (chain)
    (if (null? chain)
	0
	(+ (car chain) (* 10 (chain->num (cdr chain)))))))

(define is-palindrome?
  (lambda (n)

    (define same-chain?
      (lambda (c1 c2)
	(cond ((empty-chain? c1)
	       (if (empty-chain? c2)
		   #t
		   #f))
	      ((empty-chain? c2)
	       (if (empty-chain? c1)
		   #t
		   #f))
	      ((= (car c1) (car c2))
	       (same-chain? (cdr c1) (cdr c2)))
	      (else #f))))

    (same-chain? n (reverse-chain n))))

(define find-lychrel-seeds
  (lambda (limit max-tries)

    (define iterate
      (lambda (chain)
	(add-chains chain (reverse-chain chain))))
    
    (define is-lychrel-number?
      (lambda (chain try l return)
	(cond ((> try max-tries)
	       l)
	      ((is-palindrome? chain)
	       (return (chain->num chain)))
	      (else
	       (is-lychrel-number? (iterate chain) (+ try 1) (cons (chain->num chain) l) return)))))

    (define loop
      (lambda (number results)
	(if (< number limit)
	    (let ((result (call/cc (lambda (k) (is-lychrel-number? (num->chain number) 0 '() k)))))
	      (if (list? result)
		  (loop (+ 1 number) (cons result results))
		  (loop (+ 1 number) results)))
	    (reverse results))))
    
    (define get-last-elements
      (lambda (l)
	(if (null? l)
	    '()
	    (cons (car (reverse (car l))) (get-last-elements (cdr l))))))

    (let ((lychrel-numbers (loop 1 '())))

      (define my-list-test?
	(lambda (in1 in2 pred?)
	  (let loop ((obj1 in1)
		     (obj2 in2))
	    (cond ((null? obj1) #f)
		  ((pred? (car obj1) obj2) #t)
		  (else (loop (cdr obj1) obj2))))))

      (define in-list?
	(lambda (l elem)
	  (my-list-test? l elem =)))

      (define seed-already-found?
	(lambda (list-of-lists l2)
	  (my-list-test? list-of-lists l2 same-seed?)))

      (define same-seed?
	(lambda (l1 l2)
	  (cond ((null? l1) #f)
		((in-list? l2 (car l1)) #t)
		(else
		 (same-seed? (cdr l1) l2)))))

      (define inner-loop
	(lambda (seed-list lychrel-list)
	  (cond ((null? lychrel-list) seed-list)
		((seed-already-found? seed-list (car lychrel-list))
		 (inner-loop seed-list (cdr lychrel-list)))
		(else (inner-loop (cons (car lychrel-list) seed-list) (cdr lychrel-list))))))

      (let ((lychrel-seed-lists (inner-loop '() lychrel-numbers)))

        (cons (get-last-elements lychrel-numbers) (list (reverse (get-last-elements lychrel-seed-lists))))))))

(display (find-lychrel-seeds 10000 40))
(newline)

```

it's quite ugly code atm. i'll clean it up a bit later.

it outputs two lists. the first one is the list of lychrel numbers, the second is the list of seeds:

```

howlingmadhowie% time guile lychrel.scm
((196 295 394 493 592 689 691 788 790 879 887 978 986 1495 1497 1585 1587 1675 1677 1765 1767 1855 1857 1945 1947 1997 2494 2496 2584 2586 2674 2676 2764 2766 2854 2856 2944 2946 2996 3493 3495 3583 3585 3673 3675 3763 3765 3853 3855 3943 3945 3995 4079 4169 4259 4349 4439 4492 4494 4529 4582 4584 4619 4672 4674 4709 4762 4764 4799 4852 4854 4889 4942 4944 4979 5078 5168 5258 5348 5438 5491 5493 5528 5581 5583 5618 5671 5673 5708 5761 5763 5798 5851 5853 5888 5941 5943 5978 5993 6077 6167 6257 6347 6437 6490 6492 6527 6580 6582 6617 6670 6672 6707 6760 6762 6797 6850 6852 6887 6940 6942 6977 6992 7059 7076 7149 7166 7239 7256 7329 7346 7419 7436 7491 7509 7526 7581 7599 7616 7671 7689 7706 7761 7779 7796 7851 7869 7886 7941 7959 7976 7991 8058 8075 8079 8089 8148 8165 8169 8179 8238 8255 8259 8269 8328 8345 8349 8359 8418 8435 8439 8449 8490 8508 8525 8529 8539 8580 8598 8615 8619 8629 8670 8688 8705 8709 8719 8760 8795 8799 8809 8850 8868 8885 8889 8899 8940 8958 8975 8979 8989 8990 9057 9074 9078 9088 9147 9164 9168 9178 9237 9254 9258 9268 9327 9344 9348 9358 9417 9434 9438 9448 9507 9524 9528 9538 9597 9614 9618 9628 9687 9704 9708 9718 9777 9794 9798 9808 9867 9884 9888 9898 9957 9974 9978 9988) (196 879 1997 7059))
guile lychrel.scm  3,90s user 0,03s system 98% cpu 3,992 total

```

maybe i'll tidy up the code a bit tomorrow

---

### Post by Bachstelze on 2010-03-07
New version that tries to extract the seeds but still gives a few false positives... I also added a few comments to make things clearer.

[php]readInt             :: String -> Integer
reverseInt          :: Integer -> Integer
nextIt              :: Integer -> Integer
isPalindrome        :: Integer -> Bool
digitsSum           :: Integer -> Integer
equalDigitsSum      :: Integer -> Integer -> Bool
groupByDigitsSum    :: [Integer] -> [[Integer]]
inSameThread        :: Integer -> Integer -> Bool
isCandidate         :: (Integer, Integer) -> Bool
extractSeeds        :: [Integer] -> [Integer]

-- readInt is just an instance of read.
-- Takes a string of digits as input, returns the corresponding Integer
readInt             = read

-- reverseInt takes an Integer as input and returns it with its digits
-- in reverse order.
reverseInt n        = readInt (reverse (show n))

-- Self explanatory ;)
nextIt n            = n + (reverseInt n)

-- Returns True iff the Integer passed as input is a palindrome.
isPalindrome n      = ns == reverse ns
                        where ns = show n

-- Takes a 2-uple (n, p) as input.
-- n: number we want to test
-- p: number of iterations so far (=0 for an initial call)
-- Returns True iff n is a Lychrel candidate, i.e. no palindrome has been
-- found after 30-p iterations.
isCandidate (_, 30) = True
isCandidate (n, 0)  = isCandidate (nextIt n, 1)
isCandidate (n, p)  = if isPalindrome n
                        then False
                        else isCandidate (nextIt n, p+1)
                        
-- Takes an Integer as input and returns the sum of its digits.
digitsSum n | n < 10    = n
            | otherwise = (mod n 10) + digitsSum (quot n 10)

-- Self explanatory ;)
equalDigitsSum n p  = digitsSum n == digitsSum p

-- Takes a list of Integers and returns a list of lists of Integers
-- where the digits of all Integers in the same "sublist" have the same sum.
-- We do this because in each "sublist", there will be at most one seed,
-- and if there is one, it will be the first element of the list.
groupByDigitsSum []     = []
groupByDigitsSum (n:ns) = eqn:(groupByDigitsSum noteqn)
                            where   eqn = n:[p | p <- ns, equalDigitsSum n p]
                                    noteqn = [p | p <- ns, p `notElem` eqn]

-- Returns True iff a and b are in the same thread, i.e. they "meet" after
-- a sufficient number of iterations.
inSameThread a b
        -- We need this so we don't try indefinitely to make a and b "meet".
        | a > 100000000 = False
        | a > b         = inSameThread b a
        | a == b        = True
        | nextIt a == b = True
        | otherwise     = inSameThread (nextIt a) (nextIt b)

-- Extract the seeds from a list of candidates
extractSeeds []         = []
extractSeeds (n:ns)     = n:(extractSeeds [p | p <- ns, not (inSameThread n p)])

main = do
        -- List of all candidates < 10,000
        let candidates = [n | n <- [1..9999], isCandidate(n, 0)]

        putStrLn "Lychrel candidates < 10,000:"
        print candidates
        putStrLn ""
        putStrLn "Possible seeds < 10,000:"

        -- List of all possible seeds, i.e. the first element of each group of
        -- candidates whose digits have the same sum.
        let possibleSeeds = [head l | l <- groupByDigitsSum candidates]
        print possibleSeeds

        -- Bad news: we still have some non-seeds.
        -- Good news: inSameThread is going to help us!
        --
        -- if a is in possibleSeeds but it not actually a seed, it will be in
        -- the thread grown from a seed.
        putStrLn ""
        print (extractSeeds possibleSeeds)[/php]

```
firas@momiji ~ % ./lychrel
Lychrel candidates < 10,000:
[196,295,394,493,592,689,691,788,790,879,887,978,986,1495,1497,1585,1587,1675,1677,1765,1767,1855,1857,1945,1947,1997,2494,2496,2584,2586,2674,2676,2764,2766,2854,2856,2944,2946,2996,3493,3495,3583,3585,3673,3675,3763,3765,3853,3855,3943,3945,3995,4079,4169,4259,4349,4439,4492,4494,4529,4582,4584,4619,4672,4674,4709,4762,4764,4799,4852,4854,4889,4942,4944,4979,4994,5078,5168,5258,5348,5438,5491,5493,5528,5581,5583,5618,5671,5673,5708,5761,5763,5798,5851,5853,5888,5941,5943,5978,5993,6077,6167,6257,6347,6437,6490,6492,6527,6580,6582,6617,6670,6672,6707,6760,6762,6797,6850,6852,6887,6940,6942,6977,6992,7059,7076,7149,7166,7239,7256,7329,7346,7419,7436,7491,7509,7526,7581,7599,7616,7671,7689,7706,7761,7779,7796,7851,7869,7886,7941,7959,7976,7991,8058,8075,8079,8089,8148,8165,8169,8179,8238,8255,8259,8269,8328,8345,8349,8359,8418,8435,8439,8449,8490,8508,8525,8529,8539,8580,8598,8615,8619,8629,8670,8688,8705,8709,8719,8760,8778,8795,8799,8809,8850,8868,8885,8889,8899,8940,8958,8975,8979,8989,8990,9057,9074,9078,9088,9147,9164,9168,9178,9237,9254,9258,9268,9327,9344,9348,9358,9417,9434,9438,9448,9507,9524,9528,9538,9597,9614,9618,9628,9687,9704,9708,9718,9777,9794,9798,9808,9867,9884,9888,9898,9957,9974,9978,9988,9999]

Possible seeds < 10,000:
[196,689,879,1495,1497,1997,4079,4799,7599,8089,8799,8899,9999]

[196,879,1495,1997,7599,8799,9999]

```

---

### Post by cprofitt on 2010-03-07
Most of the entries have a basic flaw in their design. Review what a Lychrel number is and check your code.

---

### Post by howlingmadhowie on 2010-03-08
> **cprofitt said:**
> Most of the entries have a basic flaw in their design. Review what a Lychrel number is and check your code.

err, what's wrong? the entries i've looked at print a list of the candidate lychrel numbers under 10000. isn't that what you wanted?

---

### Post by Some Penguin on 2010-03-08
The entries already posted tend to reject numbers that are palindromes.

---

### Post by howlingmadhowie on 2010-03-08
> **Some Penguin said:**
> The entries already posted tend to reject numbers that are palindromes.

from wikipedia:
> 
A Lychrel number is a natural number which cannot form a palindrome through the iterative process of repeatedly reversing its base 10 digits and adding the resulting numbers. 


the way i read that is that the entries already posted are doing the right thing.

---

### Post by howlingmadhowie on 2010-03-08
i modified the code to use some of the in-built scheme functions, like reverse and equal?. this shortens the code considerably but also introduces an element of cargo-cult programming.

```

(define reverse-chain reverse)

(define num->chain
  (lambda (num)
    (if (< num 10)
	(list num)
	(cons (remainder num 10) (num->chain (quotient num 10))))))

(define empty-chain? null?)

(define add-chains
  (lambda (c1 c2)
    (num->chain (+ (chain->num c1) (chain->num c2)))))

(define chain->num
  (lambda (chain)
    (if (null? chain)
	0
	(+ (car chain) (* 10 (chain->num (cdr chain)))))))

(define same-chain? equal?)

(define is-palindrome?
  (lambda (n)
    (same-chain? n (reverse-chain n))))

(define find-lychrel-seeds
  (lambda (limit max-tries)

    (define iterate
      (lambda (chain)
	(add-chains chain (reverse-chain chain))))
    
    (define is-lychrel-number?
      (lambda (chain try return)
	(cond ((> try max-tries)
	       '())
	      ((and (> try 0) (is-palindrome? chain))
	       (return (chain->num chain)))
	      (else
	       (cons (chain->num chain) (is-lychrel-number? (iterate chain) (+ try 1) return))))))

    (define loop
      (lambda (number results)
	(if (< number limit)
	    (let ((result (call/cc (lambda (k) (is-lychrel-number? (num->chain number) 0 k)))))
	      (if (list? result)
		  (loop (+ 1 number) (cons result results))
		  (loop (+ 1 number) results)))
	    (reverse results))))

    (define get-first-elements
      (lambda (ll)
	(if (null? ll)
	    '()
	    (cons (car (car ll)) (get-first-elements (cdr ll))))))

    (let ((lychrel-numbers (loop 1 '())))

      (define my-list-test?
	(lambda (in1 in2 pred?)
	  (let loop ((obj1 in1)
		     (obj2 in2))
	    (cond ((null? obj1) #f)
		  ((pred? (car obj1) obj2) #t)
		  (else (loop (cdr obj1) obj2))))))

      (define in-list?
	(lambda (l elem)
	  (my-list-test? l elem =)))

      (define seed-already-found?
	(lambda (list-of-lists l2)
	  (my-list-test? list-of-lists l2 same-seed?)))

      (define same-seed?
	(lambda (l1 l2)
	  (cond ((null? l1) #f)
		((in-list? l2 (car l1)) #t)
		(else
		 (same-seed? (cdr l1) l2)))))

      (define inner-loop
	(lambda (seed-list lychrel-list)
	  (cond ((null? lychrel-list) seed-list)
		((seed-already-found? seed-list (car lychrel-list))
		 (inner-loop seed-list (cdr lychrel-list)))
		(else (inner-loop (cons (car lychrel-list) seed-list) (cdr lychrel-list))))))

      (let ((lychrel-seed-lists (inner-loop '() lychrel-numbers)))

	(cons (get-first-elements lychrel-numbers) (list (reverse (get-first-elements lychrel-seed-lists))))))))

(display (find-lychrel-seeds 10000 40))
(newline)

```

--edit--
okay, i've modified the code to also return palindromes which are lychrel candidates.

---

### Post by s.fox on 2010-03-08
> **howlingmadhowie said:**
> 
the way i read that is that the entries already posted are doing the right thing.

I thought so too.  Can clarification be added please if we are wrong?

-Silver Fox

---

### Post by Some Penguin on 2010-03-08
[http://www.p196.org/lychrel%20records.html]("http://www.p196.org/lychrel%20records.html")

Well, if you go by that -- 9999 is a suspected Lychrel number, tested to over 60M iterations.  The question is whether it can form a palindrome by that process -- going zero iterations does not appear to be permitted.

---

### Post by Bachstelze on 2010-03-08
> **howlingmadhowie said:**
> from wikipedia:


the way i read that is that the entries already posted are doing the right thing.

> Seed numbers are a subset of Lychrel numbers, that is the smallest number of each non palindrome producing thread. A seed number may be a palindrome itself. The first three examples are shown in bold in the list above.

Since a seed is necessarily a Lychrel number *and* may be a palindrome itself, a palindrome seed would be a palindrome Lychrel number.

---

### Post by howlingmadhowie on 2010-03-08
> **Bachstelze said:**
> Since a seed is necessarily a Lychrel number *and* may be a palindrome itself, a palindrome seed would be a palindrome Lychrel number.

i think op means that we should take something like 9999 to be a lychrel candidate, so we have to change our code to start checking after one iteration.

---

### Post by Bachstelze on 2010-03-08
> **howlingmadhowie said:**
> i think op means that we should take something like 9999 to be a lychrel candidate, so we have to change our code to start checking after one iteration.

*You* have to change your code. I already have. ;)

---

### Post by cprofitt on 2010-03-08
> **howlingmadhowie said:**
> i think op means that we should take something like 9999 to be a lychrel candidate, so we have to change our code to start checking after one iteration.

That is accurate if you are saying one iteration of the 196-algorithm.

---

### Post by Marlonsm on 2010-03-08
I'm working on mine.
It's in python and I'm not sure on how accurate is it yet.
It's a quite difficult challenge.

It's taking about 6 seconds to run up to 10000 and it finds lots of numbers, I'm not sure if they are all Lychrel candidates.
I'll try again latter.

---

### Post by Bachstelze on 2010-03-08
> **Marlonsm said:**
> I'm working on mine.
It's in python and I'm not sure on how accurate is it yet.
It's a quite difficult challenge.

It's taking about 6 seconds to run up to 10000 and it finds lots of numbers, I'm not sure if they are all Lychrel candidates.
I'll try again latter.

You can look at howlingmadhowie's and my entries to check your results. ;)

---

### Post by schauerlich on 2010-03-08
I've updated my entries to account for numbers that are initially palindromes.

---

### Post by howlingmadhowie on 2010-03-08
btw.  i couldn't find a list online, so here is a list of the results my program finds.  if there are any errors in this list, please tell me and i'll correct it :)

```

Lychrel candidates
 196  295  394  493  592  689  691  788  790  879  887  978  986

1495 1497 1585 1587 1675 1677 1765 1767 1855 1857 1945 1947 1997 

2494 2496 2584 2586 2674 2676 2764 2766 2854 2856 2944 2946 2996 

3493 3495 3583 3585 3673 3675 3763 3765 3853 3855 3943 3945 3995 

4079 4169 4259 4349 4439 4492 4494 4529 4582 4584 4619 4672 4674 4709 
4762 4764 4799 4852 4854 4889 4942 4944 4979 4994 

5078 5168 5258 5348 5438 5491 5493 5528 5581 5583 5618 5671 5673 5708 
5761 5763 5798 5851 5853 5888 5941 5943 5978 5993 

6077 6167 6257 6347 6437 6490 6492 6527 6580 6582 6617 6670 6672 6707 
6760 6762 6797 6850 6852 6887 6940 6942 6977 6992 

7059 7076 7149 7166 7239 7256 7329 7346 7419 7436 7491 7509 7526 7581 
7599 7616 7671 7689 7706 7761 7779 7796 7851 7869 7886 7941 7959 7976 
7991 

8058 8075 8079 8089 8148 8165 8169 8179 8238 8255 8259 8269 8328 8345 
8349 8359 8418 8435 8439 8449 8490 8508 8525 8529 8539 8580 8598 8615 
8619 8629 8670 8688 8705 8709 8719 8760 8778 8795 8799 8809 8850 8868 
8885 8889 8899 8940 8958 8975 8979 8989 8990 

9057 9074 9078 9088 9147 9164 9168 9178 9237 9254 9258 9268 9327 9344 
9348 9358 9417 9434 9438 9448 9507 9524 9528 9538 9597 9614 9618 9628 
9687 9704 9708 9718 9777 9794 9798 9808 9867 9884 9888 9898 9957 9974 
9978 9988 9999

Lychrel seeds
196 879 1997 7059 9999

```

---

### Post by Lux Perpetua on 2010-03-09
I'm sorry, but I can't make heads or tails of the Wikipedia definitions of "seed" and "thread." (Surely I'm not the only one.) Would somebody who actually understands what a seed is kindly explain it **in his/her own words**? If we can consider a concrete example, let's look at 4799. If my computation is correct, this seems to be a Lychrel candidate. Is it a seed?

---

### Post by howlingmadhowie on 2010-03-09
> **Lux Perpetua said:**
> I'm sorry, but I can't make heads or tails of the Wikipedia definitions of "seed" and "thread." (Surely I'm not the only one.) Would somebody who actually understands what a seed is kindly explain it **in his/her own words**? If we can consider a concrete example, let's look at 4799. If my computation is correct, this seems to be a Lychrel candidate. Is it a seed?

have a look at the first two lychrel candidates, 196 and 295.
if you iterate over 196 by reversing the digits and summing them you get:
```

 196 
 196 +  691 =   887 
 887 +  788 =  1675
1675 + 5761 =  7436
7436 + 6347 = 13783
...

```
the same sequence for 295 looks like this:
```

 295 +  592 =   887
 887 +  788 =  1675
1675 + 5761 =  7436
7436 + 6347 = 13783
...

```
which apart from the first term is identical to the sequence for 196. for this reason we call 196 a seed lychrel number and 295 is a kin. 

however, the sequence for 879 looks like this (additions omitted):
```

879 
1857 
9438 
17787 
96558 
182127 
903408
...

```
which, to the best of anyone's knowledge, never turns into the sequence based on 196.  for this reason, 879 is another lychrel seed.

---

### Post by Marlonsm on 2010-03-09
Here is mine, in Python:
[php]testNumber = 12
def reverse(toReverse):
	return int(str(toReverse)[::-1])
Lychrel = []
nonLychrel = [1,2,3,4,5,6,7,8,9,10,11]
seeds = []
while testNumber < 10001:
	testList = []    #This is the thread
	tries = 0
	if testNumber in Lychrel:   #If the number was already found out, no need to find again
		testNumber += 1
	elif testNumber in nonLychrel:
		testNumber += 1
	else:
		nowTesting = testNumber
		tries = 0
		while tries < 26:  #It'll try 24 times and in the 25th, add the number to the list
			testList.append(nowTesting)
			if nowTesting == reverse(nowTesting): #If it becomes an anagram, add to nonLychrel list
				for item in testList:
					if item not in nonLychrel:
						nonLychrel.append(item)
				tries = 26
			else: #If not, add the reverse and try again
				nowTesting += reverse(nowTesting)
				testList.append(nowTesting)
				tries += 1
				if tries == 25: #After 25 tries, add to the Lychrel list
					for item in testList:
						if item not in Lychrel:
							Lychrel.append(item)
					seeds.append(testNumber) #Add the number that started the thread to the seed list
		testNumber += 1
for number in range (1,10000): #Print all Lychrel numbers up to 10000
	if number in seeds:
		print number, "<--- Is Seed"
	elif number in Lychrel:
		print number[/php]

I'm not sure if it's accurate, specially about the seeds. It's also not very fast. I'll try to improve it later...

---

### Post by cprofitt on 2010-03-09
> **Marlonsm said:**
> Here is mine, in Python:

I'm not sure if it's accurate, specially about the seeds. It's also not very fast. I'll try to improve it later...

It is not accurate at this point. Review what a Lychrel number is and look through the thread as others have clarified it as well.

---

### Post by Lux Perpetua on 2010-03-09
> **howlingmadhowie said:**
> have a look at the first two lychrel candidates, 196 and 295.
if you iterate over 196 by reversing the digits and summing them you get:
```

 196 
 196 +  691 =   887 
 887 +  788 =  1675
1675 + 5761 =  7436
7436 + 6347 = 13783
...

```
the same sequence for 295 looks like this:
```

 295 +  592 =   887
 887 +  788 =  1675
1675 + 5761 =  7436
7436 + 6347 = 13783
...

```
which apart from the first term is identical to the sequence for 196. for this reason we call 196 a seed lychrel number and 295 is a kin. 

however, the sequence for 879 looks like this (additions omitted):
```

879 
1857 
9438 
17787 
96558 
182127 
903408
...

```
which, to the best of anyone's knowledge, never turns into the sequence based on 196.  for this reason, 879 is another lychrel seed.Thank you, howlingmadhowie. I'm with you so far. But let's consider 4799: 
```
       
4799
14773
52514
...
```
Note that 52514 is also an iterate of 196: ```
196
887
1675
7436
13783
52514
...
```Is 4799 considered a seed or not? The Wikipedia article makes it sound as if it would be, since the sequence (4799, 14773, 52514, 94039, ...) should be considered a thread, right? It surely matches the description "sequence of numbers that may or may not lead to a palindrome through the reverse and add process." This sequence is distinct from any subsequence of (196, 887, 1675, 7436, 13783, 52514, 94039, ...) because the former contains 14773, while the latter does not. (The article says the "original seed" (or "kin," whatever that is) is not included in the thread, so 4799 and 196 don't count when comparing the threads, but 14773 should still count, because it's not the "original" number. This is the only way I can make sense of it.)

---

### Post by howlingmadhowie on 2010-03-09
> **Lux Perpetua said:**
> Thank you, howlingmadhowie. I'm with you so far. But let's consider 4799: 
```
       
4799
14773
52514
...
```
Note that 52514 is also an iterate of 196: ```
196
887
1675
7436
13783
52514
...
```Is 4799 considered a seed or not? The Wikipedia article makes it sound as if it would be, since the sequence (4799, 14773, 52514, 94039, ...) should be considered a thread, right? It surely matches the description "sequence of numbers that may or may not lead to a palindrome through the reverse and add process." This sequence is distinct from any subsequence of (196, 887, 1675, 7436, 13783, 52514, 94039, ...) because the former contains 14773, while the latter does not. (The article says the "original seed" (or "kin," whatever that is) is not included in the thread, so 4799 and 196 don't count when comparing the threads, but 14773 should still count, because it's not the "original" number. This is the only way I can make sense of it.)

yepp. 4799 is a kin of 196. the rule of thumb is, that if after a certain point a thread for one number becomes the same as the thread for a lower number after a certain point, then the higher number is a kin of the lower number.

---

### Post by weichimaster on 2010-03-09
This definition has a heavy dependency on base 10, which is arbitrary.

What happens if we re-run using binary rather than base 10? Presumably  there is a smallest binary Lychrel seed. (I would do it myself, but I'm at work). I think this may simplify the underlying mathematics, and make the requirements for a number to be Lychrel clearer.

---

### Post by Bachstelze on 2010-03-09
> **weichimaster said:**
> This definition has a heavy dependency on base 10, which is arbitrary.

What happens if we re-run using binary rather than base 10? Presumably  there is a smallest binary Lychrel seed. (I would do it myself, but I'm at work). I think this may simplify the underlying mathematics, and make the requirements for a number to be Lychrel clearer.

We know very well that a number is only a Lychrel number in a given base. Here, we work in base 10. Arbitrary? Yes, but choosing base 2 would be arbitrary as well.

---

### Post by weichimaster on 2010-03-09
> **Bachstelze said:**
> We know very well that a number is only a Lychrel number in a given base. Here, we work in base 10. Arbitrary? Yes, but choosing base 2 would be arbitrary as well.

Agreed. However, my understanding is that there is a yet no proof that 196 is actually a Lychrel number in base 10. There is merely a demonstration that the algorithm does not stop after a very large number of iterations.

I'm a decent pure mathematician, but a mediocre programmer. My thought was that by looking in base 2 the underlying structure to Lychrel numbers may become clearer. 
The binary Lychrel numbers are likely to be the simplest of any possible base.

So my master plan is:

1) Find candidate binary Lychrel numbers
2) Attempt to prove that none, some or all of these numbers are Lychrel
3) See if the proof can be extended to other bases.
4) Prove 196 is (or isn't) Lychrel

As a side note, Roger Penrose in one of his books has an example of a barmy looking algorithm that can create massively big numbers from small starting points. However, it's possible to use transfinite induction to prove that his particular algorithm always halts (possibly needing very many iterations).

---

### Post by Mathiasdm on 2010-03-09
This was fun :) Ideal break while working on my thesis.

```

def reverse(number):
    return int(str(number)[::-1])

def iterate(number, reverse_number):
    new_number = number + reverse_number
    return [new_number, reverse(new_number)]

def is_lychrel(number, iterations):
    reverse_number = reverse(number)
    for i in range(iterations):
        [number, reverse_number] = iterate(number, reverse_number)
        if number == reverse_number:
            return False
    return True

lychrel = []

for i in range(10000):
    if is_lychrel(i, 30):
        lychrel.append(i)

print lychrel

```

```

time python lychrel.py 
[196, 295, 394, 493, 592, 689, 691, 788, 790, 879, 887, 978, 986, 1495, 1497, 1585, 1587, 1675, 1677, 1765, 1767, 1855, 1857, 1945, 1947, 1997, 2494, 2496, 2584, 2586, 2674, 2676, 2764, 2766, 2854, 2856, 2944, 2946, 2996, 3493, 3495, 3583, 3585, 3673, 3675, 3763, 3765, 3853, 3855, 3943, 3945, 3995, 4079, 4169, 4259, 4349, 4439, 4492, 4494, 4529, 4582, 4584, 4619, 4672, 4674, 4709, 4762, 4764, 4799, 4852, 4854, 4889, 4942, 4944, 4979, 4994, 5078, 5168, 5258, 5348, 5438, 5491, 5493, 5528, 5581, 5583, 5618, 5671, 5673, 5708, 5761, 5763, 5798, 5851, 5853, 5888, 5941, 5943, 5978, 5993, 6077, 6167, 6257, 6347, 6437, 6490, 6492, 6527, 6580, 6582, 6617, 6670, 6672, 6707, 6760, 6762, 6797, 6850, 6852, 6887, 6940, 6942, 6977, 6992, 7059, 7076, 7149, 7166, 7239, 7256, 7329, 7346, 7419, 7436, 7491, 7509, 7526, 7581, 7599, 7616, 7671, 7689, 7706, 7761, 7779, 7796, 7851, 7869, 7886, 7941, 7959, 7976, 7991, 8058, 8075, 8079, 8089, 8148, 8165, 8169, 8179, 8238, 8255, 8259, 8269, 8328, 8345, 8349, 8359, 8418, 8435, 8439, 8449, 8490, 8508, 8525, 8529, 8539, 8580, 8598, 8615, 8619, 8629, 8670, 8688, 8705, 8709, 8719, 8760, 8778, 8795, 8799, 8809, 8850, 8868, 8885, 8889, 8899, 8940, 8958, 8975, 8979, 8989, 8990, 9057, 9074, 9078, 9088, 9147, 9164, 9168, 9178, 9237, 9254, 9258, 9268, 9327, 9344, 9348, 9358, 9417, 9434, 9438, 9448, 9507, 9524, 9528, 9538, 9597, 9614, 9618, 9628, 9687, 9704, 9708, 9718, 9777, 9794, 9798, 9808, 9867, 9884, 9888, 9898, 9957, 9974, 9978, 9988, 9999]

real	0m0.123s
user	0m0.120s
sys	0m0.010s

```

---

### Post by Lux Perpetua on 2010-03-09
> **weichimaster said:**
> 
So my master plan is:

1) Find candidate binary Lychrel numbers
2) Attempt to prove that none, some or all of these numbers are Lychrel
3) See if the proof can be extended to other bases.
4) Prove 196 is (or isn't) LychrelThere are numbers that can be proved (easily) to by Lychrel in base 2 and some other bases. I really like the discussion on mathpages.com: [http://www.mathpages.com/home/kmath004.htm](http://www.mathpages.com/home/kmath004.htm) 
> **howlingmadhowie said:**
> yepp. 4799 is a kin of 196. the rule of thumb is, that if after a certain point a thread for one number becomes the same as the thread for a lower number after a certain point, then the higher number is a kin of the lower number.I think I see the light now. For every positive integer x, consider the set S(x) = {f(x), f(f(x)), f(f(f(x))), ...}, where f(a) = a + reverse(a). So, obviously x is Lychrel if and only if S(x) contains no palindromes. 

Also, let's say Lychrel numbers x and y are "cousins" if S(x) shares any elements with S(y). (I'm avoiding the term "kin" because I think it might mean something slightly different.) This is equivalent the condition that S(x) and S(y) agree on all large enough integers, i. e., that there is some N such that for all n > N, either n is in both of S(x) and S(y) or it's in neither. Indeed, if S(x) and S(y) both contain z, then they agree on all integers greater than or equal to z. 

If we define the "family" of a Lychrel number x to be the set of all of its Lychrel cousins, then it's easy to see that the distinct families partition the set of Lychrel numbers, so each Lychrel number is in exactly one family. (Mathematicians would say that the relation of being cousins defines an *equivalence relation*, and the families are its *equivalence classes*.) Each family has a unique smallest member, which we call its "seed." 

(I'm working from howlingmadhowie's explanation now, not the Wikipedia article.)

---

### Post by howlingmadhowie on 2010-03-10
> **Lux Perpetua said:**
> There are numbers that can be proved (easily) to by Lychrel in base 2 and some other bases. I really like the discussion on mathpages.com: [http://www.mathpages.com/home/kmath004.htm](http://www.mathpages.com/home/kmath004.htm) 
I think I see the light now. For every positive integer x, consider the set S(x) = {f(x), f(f(x)), f(f(f(x))), ...}, where f(a) = a + reverse(a). So, obviously x is Lychrel if and only if S(x) contains no palindromes. 

Also, let's say Lychrel numbers x and y are "cousins" if S(x) shares any elements with S(y). (I'm avoiding the term "kin" because I think it might mean something slightly different.) This is equivalent the condition that S(x) and S(y) agree on all large enough integers, i. e., that there is some N such that for all n > N, either n is in both of S(x) and S(y) or it's in neither. Indeed, if S(x) and S(y) both contain z, then they agree on all integers greater than or equal to z. 

If we define the "family" of a Lychrel number x to be the set of all of its Lychrel cousins, then it's easy to see that the distinct families partition the set of Lychrel numbers, so each Lychrel number is in exactly one family. (Mathematicians would say that the relation of being cousins defines an *equivalence relation*, and the families are its *equivalence classes*.) Each family has a unique smallest member, which we call its "seed." 

(I'm working from howlingmadhowie's explanation now, not the Wikipedia article.)

yep :)

---

### Post by cprofitt on 2010-03-11
Just curious if anyone else would like to post an entry...

---

### Post by schauerlich on 2010-03-12
Well, since no one has added anything, I'll make another entry... this time, in overdone, poorly written C++ :) Enjoy.

```
[color=#BC7A00]#include <sstream>
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>

#define MAX_LYCHREL 10000
#define ITERATIONS 30
[/color]
[color=#008000]**using**[/color] [color=#008000]**namespace**[/color] std;

[color=#008000]**template**[/color] [color=#666666]<[/color][color=#008000]**typename**[/color] T[color=#666666]>[/color]
[color=#008000]**class**[/color] [color=#0000FF]**Number**[/color] {
  T value;
  
[color=#008000]**public**[/color][color=#666666]:[/color]
  Number() {}
  Number(T n) [color=#666666]:[/color] value(n) {}
  
  T getValue() {[color=#008000]**return**[/color] value;}
  
  T [color=#008000]**operator**[/color][color=#666666]-[/color]() {
    [color=#408080][i]// returns the reverse of value
[/i][/color]    [color=#408080][i]// makes a string out of it, reverses the string,
[/i][/color]    [color=#408080][i]// then turns it back into type T
[/i][/color]    string str;
    
    str [color=#666666]=[/color] [color=#666666]+[/color]([color=#666666]*[/color][color=#008000]**this**[/color]);
    reverse(str.begin(), str.end());
    
    [color=#008000]**return**[/color] ([color=#666666]*[/color][color=#008000]**this**[/color]) [color=#666666]&[/color] str;
  } [color=#408080][i]// rev()
[/i][/color]  
  string [color=#008000]**operator**[/color][color=#666666]+[/color]() {
    [color=#408080][i]// returns a string version by placing 
[/i][/color]    [color=#408080][i]// it in a stream and then extracting it
[/i][/color]  
    stringstream ss;
    ss [color=#666666]<<[/color] value;
  
    [color=#008000]**return**[/color] ss.str();
  } [color=#408080][i]// to_string()
[/i][/color]  
  T [color=#008000]**operator**[/color][color=#666666]&[/color]([color=#008000]**const**[/color] string str) {
    [color=#408080][i]// returns the T value of a string
[/i][/color]    stringstream ss;
    T v [color=#666666]=[/color] [color=#666666]0[/color];
    T buffer;
    
    ss [color=#666666]<<[/color] str;
    
    [color=#008000]**while**[/color] (ss [color=#666666]>>[/color] buffer) {
      v [color=#666666]+=[/color] buffer;
    } [color=#408080][i]// while
[/i][/color]    
    [color=#008000]**return**[/color] v;
  } [color=#408080][i]// to_long()
[/i][/color]  
  [color=#B00040]bool[/color] [color=#008000]**operator**[/color][color=#666666]>[/color]([color=#B00040]int[/color] n) {
    [color=#008000]**return**[/color] value [color=#666666]>[/color] n;
  } [color=#408080][i]// operator>()
[/i][/color]  
  [color=#B00040]bool[/color] [color=#008000]**operator**[/color][color=#666666]==[/color](Number n) {
    [color=#008000]**return**[/color] value [color=#666666]==[/color] n.getValue();
  } [color=#408080][i]// operator==()
[/i][/color]  
  Number [color=#666666]&[/color][color=#008000]**operator**[/color][color=#666666]=[/color](Number n) {
    value [color=#666666]=[/color] n.getValue();
    [color=#008000]**return**[/color] ([color=#666666]*[/color][color=#008000]**this**[/color]);
  } [color=#408080][i]// operator=()
[/i][/color]  
  Number [color=#666666]&[/color][color=#008000]**operator**[/color][color=#666666]+=[/color](Number n) {
    value [color=#666666]+=[/color] n.getValue();
    [color=#008000]**return**[/color] ([color=#666666]*[/color][color=#008000]**this**[/color]);
  } [color=#408080][i]// operator+=()
[/i][/color]  
  [color=#008000]**template**[/color] [color=#666666]<[/color][color=#008000]**typename**[/color] S[color=#666666]>[/color]
  [color=#008000]**friend**[/color] ostream [color=#666666]&[/color][color=#008000]**operator**[/color][color=#666666]<<[/color](ostream [color=#666666]&[/color]os, Number[color=#666666]<[/color]S[color=#666666]>[/color] [color=#666666]&[/color]rhs);
}; [color=#408080][i]// class Number
[/i][/color]
[color=#008000]**template**[/color] [color=#666666]<[/color][color=#008000]**typename**[/color] S[color=#666666]>[/color]
ostream [color=#666666]&[/color][color=#008000]**operator**[/color][color=#666666]<<[/color](ostream [color=#666666]&[/color]os, Number[color=#666666]<[/color]S[color=#666666]>[/color] [color=#666666]&[/color]rhs) {
  [color=#408080][i]// output value
[/i][/color]  os [color=#666666]<<[/color] rhs.value;
  [color=#008000]**return**[/color] os;
} [color=#408080][i]// operator<<()
[/i][/color]
[color=#008000]**template**[/color] [color=#666666]<[/color][color=#008000]**typename**[/color] T, [color=#008000]**typename**[/color] C[color=#666666]>[/color]
[color=#008000]**class**[/color] [color=#0000FF]**LychrelTemplate**[/color] {
  T max_value;
  T max_iterations;
  C container;

  [color=#B00040]bool[/color] [color=#008000]**operator**[/color][color=#666666]==[/color](T value) {
    [color=#408080][i]// returns true if lychrel number, false otherwise
[/i][/color]    vector[color=#666666]<[/color][color=#B00040]int[/color][color=#666666]>[/color] [color=#666666]*[/color]v [color=#666666]=[/color] [color=#008000]**new**[/color] vector[color=#666666]<[/color][color=#B00040]int[/color][color=#666666]>[/color];
    
    [color=#008000]**for**[/color] ([color=#B00040]int[/color] i [color=#666666]=[/color] [color=#666666]0[/color]; max_iterations [color=#666666]>[/color] i; [color=#666666]++[/color]i)
      v[color=#666666]->[/color]push_back(i);
    
    [color=#008000]**for**[/color] (vector[color=#666666]<[/color][color=#B00040]int[/color][color=#666666]>::[/color]iterator itr [color=#666666]=[/color] v[color=#666666]->[/color]begin(); itr [color=#666666]!=[/color] v[color=#666666]->[/color]end(); [color=#666666]++[/color]itr) {
      T rev_value [color=#666666]=[/color] [color=#666666]-[/color]value;
      [color=#008000]**if**[/color] ([color=#666666]*[/color]itr [color=#666666]&&[/color] value [color=#666666]==[/color] rev_value) {
        [color=#008000]**delete**[/color] v;
        [color=#008000]**return**[/color] [color=#008000]**false**[/color];
      } [color=#408080][i]// if
[/i][/color]      value [color=#666666]+=[/color] rev_value;
    } [color=#408080][i]// for i
[/i][/color]
    [color=#008000]**delete**[/color] v;
    [color=#008000]**return**[/color] [color=#008000]**true**[/color];
  } [color=#408080][i]// islychrel()
[/i][/color]  
[color=#008000]**public**[/color][color=#666666]:[/color]
  LychrelTemplate() {}
  LychrelTemplate(T mv, T mi) [color=#666666]:[/color] max_value(mv), max_iterations(mi) {}
  [color=#666666]~[/color]LychrelTemplate() {}
  
  LychrelTemplate [color=#666666]&[/color] [color=#008000]**operator**[/color][color=#666666]++[/color]() {
    [color=#408080][i]// finds all of the lychrel numbers and sticks them in a container
[/i][/color]    vector[color=#666666]<[/color][color=#B00040]int[/color][color=#666666]>[/color] [color=#666666]*[/color]v [color=#666666]=[/color] [color=#008000]**new**[/color] vector[color=#666666]<[/color][color=#B00040]int[/color][color=#666666]>[/color];
    
    [color=#008000]**for**[/color] ([color=#B00040]int[/color] i [color=#666666]=[/color] [color=#666666]0[/color]; max_value [color=#666666]>[/color] i; [color=#666666]++[/color]i)
      v[color=#666666]->[/color]push_back(i);
    
    [color=#008000]**for**[/color] (vector[color=#666666]<[/color][color=#B00040]int[/color][color=#666666]>::[/color]iterator itr [color=#666666]=[/color] v[color=#666666]->[/color]begin(); itr [color=#666666]!=[/color] v[color=#666666]->[/color]end(); [color=#666666]++[/color]itr) {
      [color=#008000]**if**[/color] (([color=#666666]*[/color][color=#008000]**this**[/color]) [color=#666666]==[/color] [color=#666666]*[/color]itr)
        container.push_back([color=#666666]*[/color]itr);
    } [color=#408080][i]// for i
[/i][/color]    
    [color=#008000]**delete**[/color] v;
    [color=#008000]**return**[/color] [color=#666666]*[/color][color=#008000]**this**[/color];
  } [color=#408080][i]// find_candidates()
[/i][/color]
  [color=#008000]**template**[/color] [color=#666666]<[/color][color=#008000]**typename**[/color] A, [color=#008000]**typename**[/color] B[color=#666666]>[/color] 
  [color=#008000]**friend**[/color] ostream [color=#666666]&[/color][color=#008000]**operator**[/color][color=#666666]<<[/color](ostream [color=#666666]&[/color]os, LychrelTemplate[color=#666666]<[/color]A, B[color=#666666]>[/color] [color=#666666]&[/color]rhs);

}; [color=#408080][i]// class LychrelTemplate
[/i][/color]
[color=#008000]**template**[/color] [color=#666666]<[/color][color=#008000]**typename**[/color] A, [color=#008000]**typename**[/color] B[color=#666666]>[/color]
ostream [color=#666666]&[/color][color=#008000]**operator**[/color][color=#666666]<<[/color](ostream [color=#666666]&[/color]os, LychrelTemplate[color=#666666]<[/color]A, B[color=#666666]>[/color] [color=#666666]&[/color]rhs) {
  [color=#408080][i]// output all of the lychrel numbers
[/i][/color]  [color=#008000]**for**[/color] ([color=#008000]**typename**[/color] B[color=#666666]::[/color]iterator itr [color=#666666]=[/color] rhs.container.begin(); itr [color=#666666]!=[/color] rhs.container.end(); [color=#666666]++[/color]itr)
    os [color=#666666]<<[/color] [color=#666666]*[/color]itr [color=#666666]<<[/color] endl;
  [color=#008000]**return**[/color] os;
}


[color=#008000]**typedef**[/color] Number[color=#666666]<[/color][color=#B00040]long[/color] [color=#B00040]int[/color][color=#666666]>[/color] Num;
[color=#008000]**typedef**[/color] LychrelTemplate[color=#666666]<[/color]Num, vector[color=#666666]<[/color]Num[color=#666666]>[/color] [color=#666666]>[/color] Lychrel;


[color=#B00040]int[/color] main([color=#B00040]int[/color] argc, [color=#B00040]char[/color] [color=#666666]*[/color]argv[]) {
  Lychrel l(Num(MAX_LYCHREL), Num(ITERATIONS));
  
  cout [color=#666666]<<[/color] [color=#666666]++[/color]l;
  
  [color=#008000]**return**[/color] [color=#666666]0[/color];
} [color=#408080][i]// main()
[/i][/color]
```

```
real	0m0.230s
user	0m0.221s
sys	0m0.006s
```

Just goes to show you... good python can be just as fast as bad C++ :)

---

### Post by Lux Perpetua on 2010-03-12
Here are two implementations of essentially the same algorithm. Rather than iterating a number a fixed number of times, I chose to iterate it until it reached a predetermined size. Seventeen digits seems to work for numbers up to 10,000. The main benefit of this approach is how easily it lets us find seeds. By the time an iterate of a Lychrel number x reaches some large fixed size, it's very likely that its sequence S(x) (in my notation from [an earlier post](http://ubuntuforums.org/showpost.php?p=8942440&postcount=43)) has already joined the sequence of its seed s. Thus, if g(a, t) is the first iterate of a to reach t digits, then g(x, t) is the same as g(s, t) as long as t is large enough. Thus, to determine whether x is a seed, we don't need to store all iterates of all smaller numbers; we only need to store the first iterate to reach t digits. There is exactly one of these numbers for each seed candidate--only five for numbers up to 10,000! 

The first is my original implementation, in C++. The program "lives" in base ten; there's no need to convert between base-ten representations and machine representations. The program is both simple and fast. I think it could probably be sped up a little bit more by avoiding the use of STL vectors or using them more intelligently, and perhaps avoiding the STL container set<dec_int> and implementing a more efficient set structure (perhaps some sort of trie). 

```
/* Lychrel numbers in base ten. This program is engineered to use only
 * basic arithmetic (addition & subtraction), no multiplication or
 * division. This is accomplished by doing all our arithmetic directly
 * in base ten. This also nicely circumvents all issues related to the
 * finite size of built-in integral types; you can iterate up to hundreds
 * of digits if you want (try it!).
 */

#include <iostream>
#include <sstream>
#include <vector>
#include <set>
#include <cstdlib>

using namespace std;

/* An integer, represented as a sequence of decimal digits. */
struct dec_int {
    vector<char> digits;
    
    /* Takes care of carries after an addition. */
    void fix() {
        int n = digits.size();
        for (int k = 0; k < n-1; ++k) {
            if (digits[k] >= 10) {
                digits[k] -= 10;
                ++digits[k+1];
            }
        }
        if (digits[n-1] >= 10) {
            digits[n-1] -= 10;
            digits.push_back(1);
        }
    }

    /* Default initialized value is 0. */
    dec_int() {
        /* To avoid problems, digits should always have at
         * least one digit (possibly 0).
         */
        digits.push_back(0);
    }

    const dec_int & operator ++ () {
        ++digits[0];

        fix();

        return *this;
    }

    /* Adds its reversal to itself. Returns true if
     * this results in a palindrome, and false otherwise.
     */
    bool reverse_add() {
        int n = digits.size();

        int k = 0;
        for ( ; k+k < n; ++k)
            digits[k] += digits[n-k-1];
        for ( ; k < n; ++k)
            digits[k] = digits[n-k-1];

        fix();

        n = digits.size();

        for (int k = 0; k+k < n-1; ++k)
            if (digits[k] != digits[n-k-1]) 
                return false;
        return true;
    }
};

/* Input from an istream; sets failbit if the operation failed. */
istream & operator >> (istream & is, dec_int & i) {
    string buf;
    if (!(is >> buf)) return is;
    
    int len = buf.size();
    i.digits.resize(len);
 
    for (int k = 0; k < len; ++k) {
        char c = buf[k] - '0';
        if (c < 0 || c >= 10) {
            is.setstate(ios::failbit);
            return is;
        }
        i.digits[len-k-1] = c;
    }

    return is;
}

ostream & operator << (ostream & os, const dec_int & i) {
    for (int k = i.digits.size()-1; k >= 0; --k)
        os << char('0' + i.digits[k]);
    return os;
}

/* The STL set container needs this. */
bool operator < (const dec_int &i, const dec_int &j) {
    int is = i.digits.size(), js = j.digits.size();
    if (is < js) return true;
    if (js < is) return false;
    for (int k = is - 1; k >= 0; --k) {
        if (i.digits[k] < j.digits[k]) return true;
        if (j.digits[k] < i.digits[k]) return false;
    }
    return false;
}

void usage(const char *s) {
    cerr << "Usage: " << s
         << " N trap" << endl;
    exit(EXIT_FAILURE);
}

int main(int argc, char *argv[]) {
    if (argc < 3) usage(argv[0]);

    /* N: we'll find all Lychrel candidates up to N. */
    istringstream s(argv[1]);
    dec_int N;
    if (!(s >> N)) usage(argv[0]);

    /* trap: we'll iterate each number until it reaches `trap' digits
     * and then declare it to be a Lychrel candidate.
     */
    istringstream t(argv[2]);
    unsigned int trap;
    if (!(t >> trap)) usage(argv[0]);

    /* cache will store one element from each "family" (the first one
     * whose number of digits equals `trap'). This is a memory-efficient
     * way to detect seeds. 
     */
    set<dec_int> cache;

    dec_int i;

    while (i < N) {
        ++i;

        dec_int j(i);

        bool lychrel = true;
        while (j.digits.size() < trap) {
            if (j.reverse_add()) {
                lychrel = false;
                break;
            }
        }

        if (lychrel) {
            cout << i;
            pair<set<dec_int>::iterator, bool> p = cache.insert(j);
            if (p.second) cout << " (seed)";
            cout << endl;
        }
    }

    return 0;
}
```
Typical results: ```
> g++ -ansi -Wall -pedantic -O3 ly02.cpp -o lychrel
> time lychrel 10000 17 > /dev/null

real    0m0.025s
user    0m0.020s
sys     0m0.000s

```For my second implementation, I hacked howlingmadhowie's Scheme code to use my algorithm. I was surprised how much that sped it up. ```
;; howlingmadhowie's basic "chain" manipulation functions

(define reverse-chain reverse)

(define num->chain
  (lambda (num)
    (if (< num 10)
	(list num)
	(cons (remainder num 10) (num->chain (quotient num 10))))))

(define empty-chain? null?)

(define add-chains
  (lambda (c1 c2)
    (num->chain (+ (chain->num c1) (chain->num c2)))))

(define chain->num
  (lambda (chain)
    (if (null? chain)
	0
	(+ (car chain) (* 10 (chain->num (cdr chain)))))))

(define same-chain? equal?)

(define is-palindrome?
  (lambda (n)
    (same-chain? n (reverse-chain n))))

(define iterate
  (lambda (chain)
    (add-chains chain (reverse-chain chain))))

;; My version of the algorithm follows.

;; returns first iterate of chain with >= `trap' digits,
;; or '() if some iterate of chain is a palindrome before then
(define iterate-until
  (lambda (chain trap)
    (let ((chain2 (iterate chain)))
      (cond ((>= (length chain) trap) (chain->num chain))
            ((is-palindrome? chain2) '())
            (else (iterate-until chain2 trap))))))

;; does l contain x?
(define contains?
  (lambda (l x)
    (cond ((null? l) #f)
          ((= x (car l)) #t)
          (else (contains? (cdr l) x)))))

;; when called with cache, lychrel-list, & seed-list = '():
;; returns a pair of lists, respectively containing Lychrel candidates
;; & seeds from start to end in reverse order. trap is how large the
;; iterates of a number should be allowed to grow (in digits) before
;; declaring it to be Lychrel.
(define find-seeds
  (lambda (start end trap cache lychrel-list seed-list)
    (if (> start end) `(,lychrel-list ,seed-list)
      (let ((last (iterate-until (num->chain start) trap)))
          (cond ((null? last) 
                  (find-seeds (+ 1 start) end trap cache 
                              lychrel-list seed-list))
                ((contains? cache last)
                  (find-seeds (+ 1 start) end trap cache
                              (cons start lychrel-list) seed-list))
                (else
                  (find-seeds (+ 1 start) end trap
                              (cons last cache)
                              (cons start lychrel-list)
                              (cons start seed-list))))))))

;; The following is admittedly a bit convoluted...
(display ((lambda (l) `(,(reverse (car l)) ,(reverse (car (cdr l)))))
          (find-seeds 1 10000 17 '() '() '())))
(newline)
```Typical results: ```
> time guile ly-hmh-mod02.scm > /dev/null

real    0m1.748s
user    0m1.687s
sys     0m0.000s

```Of course, it isn't competitive with the C++ version. I started implementing base-ten arithmetic as in my C++ program, but it seemed to slow it down, so I stopped and kept howlingmadhowie's implementation.

---

### Post by Marlonsm on 2010-03-13
I fixed mine, it's not fast, but now the result is right about the seeds:
[php]testNumber = 12
def reverse(toReverse):
	return int(str(toReverse)[::-1])
Lychrel = []
nonLychrel = [1,2,3,4,5,6,7,8,9,10,11]
seeds = []
while testNumber < 10001:
	testList = []    #This is the thread
	tries = 0
	if testNumber in Lychrel:   #If the number was already found out, no need to find again
		testNumber += 1
	elif testNumber in nonLychrel:
		testNumber += 1
	else:
		nowTesting = testNumber
		tries = 0
		while tries < 26:  #It'll try 24 times and in the 25th, add the number to the list
			testList.append(nowTesting)
			if nowTesting == reverse(nowTesting): #If it becomes an anagram, add to nonLychrel list
				for item in testList:
					if item not in nonLychrel:
						nonLychrel.append(item)
				tries = 26
			else: #If not, add the reverse and try again
				nowTesting += reverse(nowTesting)
				tries += 1
				if tries == 25: #After 25 tries, add to the Lychrel list
					seed = 1
					for item in testList:
						if item not in Lychrel:
							Lychrel.append(item)
						elif item in Lychrel: #if not all items in the thread are new, the first number is not a seed
							seed = 0
					if seed == 1:
						seeds.append(testNumber) #Add the number that started the new thread to the seed list
		testNumber += 1
for number in range (1,10000): #Print all Lychrel numbers up to 10000
	if number in seeds:
		print number, "<--- Is Seed"
	elif number in Lychrel:
		print number[/php]

---

### Post by cprofitt on 2010-03-14
Entries have slowed... unless we get more entries I will work through the entries and select a 'winner' by March 18th.

---

### Post by JoeWheeler on 2010-03-15
Hi guys, I'm a nooby programmer and this is actually my first python program so I'm sure it could be more efficient; but I'm still proud of it!
```
def testLychrel(number, revNumber):
    c = 0
    while c < 30:
        number = number + revNumber
        revNumber = reverseNum(number)
        if number == revNumber:
            return False
    c = c + 1
    return True
def reverseNum(cand):
    return int(str(cand)[::-1])

for n in range(1, 10000):
    revN = reverseNum(n)
    if testLychrel(n, revN) == True:
        print n
        

``````

real    0m0.295s
user    0m0.228s
sys    0m0.016s

196
295
394
493
592
689
691
788
790
879
887
978
986
1495
1497
1585
1587
1675
1677
1765
1767
1855
1857
1945
1947
1997
2494
2496
2584
2586
2674
2676
2764
2766
2854
2856
2944
2946
2996
3493
3495
3583
3585
3673
3675
3763
3765
3853
3855
3943
3945
3995
4079
4169
4259
4349
4439
4492
4494
4529
4582
4584
4619
4672
4674
4709
4762
4764
4799
4852
4854
4889
4942
4944
4979
4994
5078
5168
5258
5348
5438
5491
5493
5528
5581
5583
5618
5671
5673
5708
5761
5763
5798
5851
5853
5888
5941
5943
5978
5993
6077
6167
6257
6347
6437
6490
6492
6527
6580
6582
6617
6670
6672
6707
6760
6762
6797
6850
6852
6887
6940
6942
6977
6992
7059
7076
7149
7166
7239
7256
7329
7346
7419
7436
7491
7509
7526
7581
7599
7616
7671
7689
7706
7761
7779
7796
7851
7869
7886
7941
7959
7976
7991
8058
8075
8079
8089
8148
8165
8169
8179
8238
8255
8259
8269
8328
8345
8349
8359
8418
8435
8439
8449
8490
8508
8525
8529
8539
8580
8598
8615
8619
8629
8670
8688
8705
8709
8719
8760
8778
8795
8799
8809
8850
8868
8885
8889
8899
8940
8958
8975
8979
8989
8990
9057
9074
9078
9088
9147
9164
9168
9178
9237
9254
9258
9268
9327
9344
9348
9358
9417
9434
9438
9448
9507
9524
9528
9538
9597
9614
9618
9628
9687
9704
9708
9718
9777
9794
9798
9808
9867
9884
9888
9898
9957
9974
9978
9988
9999

```

---

### Post by Marlonsm on 2010-03-15
Another one, much faster than the other. But doesn't calculates the seeds.
[php]def reverse(toReverse):
	return int(str(toReverse)[::-1])
def isLychrel(number):
	for i in range (1,25):
		if number == reverse(number):
			return False
		else:
			number += reverse(number)
	return True
for number in range (1,10000):
	if isLychrel(number) == True:
		print number[/php]

---

### Post by Lux Perpetua on 2010-03-15
Marlonsm, I think it was concluded from cprofitt's cryptic comments that a palindrome can in fact be Lychrel (if none of its subsequent iterates are palindromes). In that case, you would be missing a few Lychrel numbers.

---

### Post by Marlonsm on 2010-03-15
> **Lux Perpetua said:**
> Marlonsm, I think it was concluded from cprofitt's cryptic comments that a palindrome can in fact be Lychrel (if none of its subsequent iterates are palindromes). In that case, you would be missing a few Lychrel numbers.

I think you're right. I was working to add seeds to my program, and I've also changed that.
Here it is:
[php]def reverse(toReverse):
	return int(str(toReverse)[::-1])
def isSeed(number, Lychrel):  #This tests if the thread is new, if so, the starting number is a seed
	if number in Lychrel:
		return False
	Lychrel.append(number)
	return True
def isLychrel(number, Lychrel, iterations): #Tries the number 30 times before assuming it's Lychrel
	for i in range (1,iterations):
		number += reverse(number)
		if number == reverse(number):
			return False
	if isSeed(number, Lychrel) == True:
		return "seed"
	else:
		return "Lychrel"
def main(upTo, iterations):
	Lychrel = []
	for number in range (1,upTo): #Run for all numbers up to 10000 and print the results
		Lych = isLychrel(number, Lychrel, iterations)
		if Lych == "seed":
			print number, "<--- Is seed"
		elif Lych == "Lychrel":
			print number
upTo = input("Do you want to find Lychrel candidates up to which number? ")
iterations = input("How many iterations do you want before a number is considered Lychrel? ")
main(upTo, iterations)[/php]

EDIT (03/19) made a small change in the way it checks seeds, now it checks only the last number, not the whole thread and added an user input.

---

### Post by munky99999 on 2010-03-16
Hey hey. Here's my attempt at C++ of this.

```
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>
#include <sstream>

using namespace std;

long long a, e, d;
//global variables so functions can share. Sharing is caring!

void backwards(long long y){

    vector<long long> numb;
    numb.push_back (y);
//puts the int into the vector used later. Vector can do math better then string.

    stringstream sstr;
    sstr << y;
    string numbrev = sstr.str();

    //stringstream to bring long y to the string.

    reverse(numbrev.begin(), numbrev.end());

    //reverses the string such that it reverses the number. 19 goes to 91.
    //This reverse algorithm doesnt work on vectors the same way.
    stringstream sstr2;
    sstr2 << numbrev;
    long long c;
    sstr2 >> c;
    d = (c + (numb[0]));
    //I then need to stringstream to a long so I can do math on the string.

    stringstream sstr3;
    sstr3 << d;
    string numbrev2 = sstr3.str();
    //I use stringstream AGAIN to move the new calculated long into a string

    reverse (numbrev2.begin(), numbrev2.end());
    //now I move the calculated long; now string, reversing it.

    stringstream sstr4;
    sstr4 << numbrev2;
    sstr4 >> e;
    //stringstream! to the global e long
    }//yaay function backwards is done.


void lyrchel(long long n){
    long counter = 0;

    backwards(n);
    //doing the lyrchel(sp?) backwards thing.

    if ( counter < 31 ){
        //this is looping for the whole depth thing. Most others went 30 but my results are all wierd.
        while (e != d){
        backwards(d);
        counter++;
            if ( counter == 30 ){
            cout << a << endl;
            break;

            }
        }//the while bracket
    }

}//lyrchel ftw.

int main()
{
    for (a=1; a < 10000; a++){
    lyrchel(a);
    }
}


```

The output is this.
```
196
295
394
493
592
689
691
788
790
879
887
978
986
1495
1497
1585
1587
1675
1677
1765
1767
1855
1857
1945
1947
1997
2494
2496
2584
2586
2674
2676
2764
2766
2854
2856
2944
2946
2996
3493
3495
3583
3585
3673
3675
3763
3765
3853
3855
3943
3945
3995
4079
4169
4259
4349
4439
4492
4494
4529
4582
4584
4619
4672
4674
4709
4762
4764
4799
4852
4854
4889
4942
4944
4979
4994
5078
5168
5258
5348
5438
5491
5493
5528
5581
5583
5618
5671
5673
5708
5761
5763
5798
5851
5853
5888
5941
5943
5978
5993
6077
6167
6257
6347
6437
6490
6492
6527
6580
6582
6617
6670
6672
6707
6760
6762
6797
6850
6852
6887
6940
6942
6977
6992
7059
7076
7149
7166
7239
7256
7329
7346
7419
7436
7491
7509
7526
7581
7599
7616
7671
7689
7706
7761
7779
7796
7851
7869
7886
7941
7959
7976
7991
8058
8075
8079
8089
8148
8165
8169
8179
8238
8255
8259
8269
8328
8345
8349
8359
8418
8435
8439
8449
8490
8508
8525
8529
8539
8580
8598
8615
8619
8629
8670
8688
8705
8709
8719
8760
8778
8795
8799
8809
8850
8868
8885
8889
8899
8940
8958
8975
8979
8989
8990
9057
9074
9078
9088
9147
9164
9168
9178
9237
9254
9258
9268
9327
9344
9348
9358
9417
9434
9438
9448
9507
9524
9528
9538
9597
9614
9618
9628
9687
9704
9708
9718
9777
9794
9798
9808
9867
9884
9888
9898
9957
9974
9978
9988
9999
```




Seems the numbers I am getting are wrong... Compared to others. If I make the depth higher. I lose numbers which I thought were certainly. Like 196. Not sure where that fails up. Seemingly it works though. Most of those numbers dont become palidromes.


/Updated code! I was over running LONG.

---

### Post by Marlonsm on 2010-03-16
> **munky99999 said:**
> Hey hey. Here's my attempt at C++ of this.


Seems the numbers I am getting are wrong... Compared to others. If I make the depth higher. I lose numbers which I thought were certainly. Like 196. Not sure where that fails up. Seemingly it works though. Most of those numbers dont become palidromes.

I think you're not running it for long enough. 89 and 98 take a long time to become palindromes.
When I was testing mine I had a problem that it tried only half the times it was supposed to, so I also got 89 as result.

---

### Post by munky99999 on 2010-03-16
> **Marlonsm said:**
> I think you're not running it for long enough. 89 and 98 take a long time to become palindromes.
When I was testing mine I had a problem that it tried only half the times it was supposed to, so I also got 89 as result.

Right. At depth of 30 they havent become palindromes i believe. However If I set the depth to like 100. It eliminates those. The problem I found. It also eliminates everything under 739; but 196 should be?

If I set the depth to 10,000 it eliminates loads more but 196 is also sill gone.

Makes me wonder where my code is hanging up at; or where I go to collect the prize money for proving 196 is not a lyrchel. :)

---

### Post by schauerlich on 2010-03-16
[From wikipedia](http://en.wikipedia.org/wiki/Lychrel_number):

> 89 takes an unusually large 24 iterations (the most of any number under 10,000 that is known to resolve into a palindrome) to reach the palindrome 8813200023188.

If your program doesn't find the correct candidates in 30 iterations, then it is wrong.

---

### Post by cprofitt on 2010-03-16
We seem to have a bit of life now... so I will take another look tomorrow to see if we announce close the contest or not.

---

### Post by munky99999 on 2010-03-16
> **schauerlich said:**
> [From wikipedia](http://en.wikipedia.org/wiki/Lychrel_number):



If your program doesn't find the correct candidates in 30 iterations, then it is wrong.

Updated my code. It seemingly works just fine now.

I checked out wiki and went to the actual iteration for 89. Noticed. Hey that goes way over long. So I changed my code to use long long. Works just fine.

I also changed from 30 to 3000 depth. Made no difference :)

---

### Post by Lux Perpetua on 2010-03-17
> **Lux Perpetua said:**
> I think it could probably be sped up a little bit more by avoiding the use of STL vectors or using them more intelligently, and perhaps avoiding the STL container set<dec_int> and implementing a more efficient set structure (perhaps some sort of trie). I went ahead and made a new program with those modifications. Also, for the sake of speed, I went with a more straighforward (but memory-gluttonous) algorithm: keep a record of each non-palindrome ever visited (in an existence trie), making each record point to a table entry which is set to record its Lychrel-status. This way, we can stop iterating as soon as we find any number that has already been visited (whether Lychrel or not). 

This illustrates a basic but awesome data structure: the existence trie. It's a map data type implemented as a tree, but the keys aren't stored anywhere: the set of keys is encoded completely in the structure of the tree itself. ```
[color=#408080][i]/* Lychrel numbers in base ten. This program is engineered to use only
 * basic arithmetic (addition & subtraction), no multiplication or
 * division. This is accomplished by doing all our arithmetic directly
 * in base ten. This also nicely circumvents all issues related to the
 * finite size of built-in integral types; you can iterate up to hundreds
 * of digits if you want (try it!).
 */[/i][/color]
[color=#BC7A00]
#include <iostream>
#include <sstream>
#include <cstdlib>
#include <cassert>
#include <cstring>
[/color]
[color=#008000]**using**[/color] [color=#008000]**namespace**[/color] std;

[color=#408080][i]/* decimal representation of an integer. The maximum size in digits
 * must be known in advance (which is fine for this problem).
 */[/i][/color]
[color=#008000]**struct**[/color] dec_int {
    [color=#B00040]char[/color] [color=#666666]*[/color]digits;
    size_t size;
    size_t max;

    [color=#408080]*/* restore after an addition */*[/color]
    [color=#B00040]void[/color] fix() {
        [color=#008000]**for**[/color] (size_t k [color=#666666]=[/color] [color=#666666]0[/color]; k [color=#666666]<[/color] size; [color=#666666]++[/color]k) {
            [color=#008000]**if**[/color] (digits[k] [color=#666666]>=[/color] [color=#666666]10[/color]) {
                digits[k] [color=#666666]-=[/color] [color=#666666]10[/color];
                [color=#666666]++[/color]digits[k[color=#666666]+[/color][color=#666666]1[/color]];
            }
        }
        [color=#008000]**if**[/color] (digits[size]) [color=#666666]++[/color]size;
    }

    dec_int([color=#B00040]int[/color] m) [color=#666666]:[/color] size([color=#666666]0[/color]), max(m) {
        digits [color=#666666]=[/color] [color=#008000]**new**[/color] [color=#B00040]char[/color][max];
        memset(digits, [color=#666666]0[/color], max);
    }

    [color=#666666]~[/color]dec_int() {
        [color=#008000]**delete**[/color] [] digits;
    }

    [color=#008000]**const**[/color] dec_int [color=#666666]&[/color] [color=#008000]**operator**[/color] [color=#666666]=[/color] ([color=#008000]**const**[/color] dec_int [color=#666666]&[/color]i) {
        assert( max [color=#666666]==[/color] i.max );
        memcpy(digits, i.digits, max);
        size [color=#666666]=[/color] i.size;
        [color=#008000]**return**[/color] [color=#666666]*[/color][color=#008000]**this**[/color];
    }

    [color=#008000]**const**[/color] dec_int [color=#666666]&[/color] [color=#008000]**operator**[/color] [color=#666666]++[/color] () {
        [color=#666666]++[/color]digits[[color=#666666]0[/color]];

        fix();

        [color=#008000]**return**[/color] [color=#666666]*[/color][color=#008000]**this**[/color];
    }

    [color=#408080][i]/* adds its reversal to itself. Returns true if
     * this results in a palindrome, and false otherwise.
     */[/i][/color]
    [color=#B00040]bool[/color] reverse_add() {
        size_t k [color=#666666]=[/color] [color=#666666]0[/color];
        [color=#008000]**for**[/color] ( ; k[color=#666666]+[/color]k [color=#666666]<[/color] size; [color=#666666]++[/color]k)
            digits[k] [color=#666666]+=[/color] digits[size[color=#666666]-[/color]k[color=#666666]-[/color][color=#666666]1[/color]];
        [color=#008000]**for**[/color] ( ; k [color=#666666]<[/color] size; [color=#666666]++[/color]k)
            digits[k] [color=#666666]=[/color] digits[size[color=#666666]-[/color]k[color=#666666]-[/color][color=#666666]1[/color]];

        fix();

        [color=#008000]**for**[/color] (k [color=#666666]=[/color] [color=#666666]0[/color]; k[color=#666666]+[/color]k [color=#666666]<[/color] size[color=#666666]-[/color][color=#666666]1[/color]; [color=#666666]++[/color]k)
            [color=#008000]**if**[/color] (digits[k] [color=#666666]!=[/color] digits[size[color=#666666]-[/color]k[color=#666666]-[/color][color=#666666]1[/color]]) 
                [color=#008000]**return**[/color] [color=#008000]**false**[/color];
        [color=#008000]**return**[/color] [color=#008000]**true**[/color];
    }
};

ostream [color=#666666]&[/color] [color=#008000]**operator**[/color] [color=#666666]<<[/color] (ostream [color=#666666]&[/color] os, [color=#008000]**const**[/color] dec_int [color=#666666]&[/color] i) {
    [color=#008000]**for**[/color] ([color=#B00040]int[/color] k [color=#666666]=[/color] i.size[color=#666666]-[/color][color=#666666]1[/color]; k [color=#666666]>=[/color] [color=#666666]0[/color]; [color=#666666]--[/color]k)
        os [color=#666666]<<[/color] [color=#B00040]char[/color]([color=#BA2121]'0'[/color] [color=#666666]+[/color] i.digits[k]);
    [color=#008000]**return**[/color] os;
}

[color=#408080][i]/* This is a bare-bones implementation of an existence trie,
 * the most basic type of trie. It has some serious memory overhead
 * (1 int + 10 pointers per node), but this is compensated by the
 * ease of implementation and speed of insertions & queries.
 */[/i][/color]
[color=#008000]**struct**[/color] trie_node;
[color=#008000]**typedef**[/color] trie_node [color=#666666]*[/color]trie_link;

[color=#008000]**struct**[/color] trie_node {
    [color=#408080][i]/* height is the number of digits needed to specify an
     * integer from this node
     */[/i][/color]
    [color=#B00040]int[/color] height;

    [color=#408080][i]/* when height = 0, this is a leaf node, in which case
     * the `data' field is the relevant part.
     */[/i][/color]
    [color=#008000]**union**[/color] {
        trie_link links[[color=#666666]10[/color]];
        [color=#B00040]int[/color] data;
    };

    trie_node([color=#B00040]int[/color] k) [color=#666666]:[/color] height(k) {
        [color=#008000]**if**[/color] (height [color=#666666]>[/color] [color=#666666]0[/color]) {
            [color=#008000]**for**[/color] ([color=#B00040]int[/color] j [color=#666666]=[/color] [color=#666666]0[/color]; j [color=#666666]<[/color] [color=#666666]10[/color]; [color=#666666]++[/color]j) {
                links[j] [color=#666666]=[/color] [color=#666666]0[/color];
            }
        } [color=#008000]**else**[/color] {
            data [color=#666666]=[/color] [color=#666666]0[/color];
        }
    }

    [color=#666666]~[/color]trie_node() {
        [color=#008000]**if**[/color] (height [color=#666666]>[/color] [color=#666666]0[/color]) {
            [color=#008000]**for**[/color] ([color=#B00040]int[/color] j [color=#666666]=[/color] [color=#666666]0[/color]; j [color=#666666]<[/color] [color=#666666]10[/color]; [color=#666666]++[/color]j) {
                [color=#008000]**if**[/color] (links[j]) {
                    [color=#008000]**delete**[/color] links[j];
                }
            }
        }
    }

};

[color=#408080][i]/* a set of tries, one for each number of digits. (This isn't the
 * only way to do it, but it makes things particularly simple if each
 * trie has a constant depth for all leaves.)
 */[/i][/color]
[color=#008000]**struct**[/color] trie_forest {
    trie_link [color=#666666]*[/color]tries;
    [color=#B00040]int[/color] t;

    trie_forest([color=#B00040]int[/color] n) [color=#666666]:[/color] t(n) {
        tries [color=#666666]=[/color] [color=#008000]**new**[/color] trie_link[t];
        [color=#008000]**for**[/color] ([color=#B00040]int[/color] k [color=#666666]=[/color] [color=#666666]0[/color]; k [color=#666666]<[/color] t; [color=#666666]++[/color]k) {
            tries[k] [color=#666666]=[/color] [color=#008000]**new**[/color] trie_node(k);
        }
    }
    [color=#666666]~[/color]trie_forest() {
        [color=#008000]**for**[/color] ([color=#B00040]int[/color] k [color=#666666]=[/color] [color=#666666]0[/color]; k [color=#666666]<[/color] t; [color=#666666]++[/color]k) {
            [color=#008000]**delete**[/color] tries[k];
        }
        [color=#008000]**delete**[/color] [] tries;
    }

    [color=#408080][i]/* attempts to insert i with given data; if i was already there,
     * returns (false, existing data) and doesn't modify the trie;
     * otherwise, returns (true, new data) and performs the insertion.
     * It turns out this is the only operation we need.
     */[/i][/color]
    pair[color=#666666]<[/color][color=#B00040]bool[/color], [color=#B00040]int[/color][color=#666666]>[/color] insert([color=#008000]**const**[/color] dec_int [color=#666666]&[/color] i, [color=#B00040]int[/color] data) {
        [color=#B00040]int[/color] size [color=#666666]=[/color] i.size;
        assert( size [color=#666666]<[/color] t );

        [color=#B00040]int[/color] height [color=#666666]=[/color] size;
        trie_link prev;
        trie_link current [color=#666666]=[/color] tries[size];

        [color=#008000]**while**[/color] (current [color=#666666]&&[/color] height) {
            [color=#666666]--[/color]height;
            prev [color=#666666]=[/color] current;
            current [color=#666666]=[/color] current[color=#666666]->[/color]links[i.digits[height]];
        }

        [color=#008000]**if**[/color] (current) {
            [color=#008000]**return**[/color] pair[color=#666666]<[/color][color=#B00040]bool[/color], [color=#B00040]int[/color][color=#666666]>[/color]([color=#008000]**false**[/color], current[color=#666666]->[/color]data);
        }

        [color=#408080]*/* Now current == 0, height >= 0 */*[/color]

        current [color=#666666]=[/color] prev;
        [color=#008000]**while**[/color] (height [color=#666666]>=[/color] [color=#666666]0[/color]) {
            [color=#B00040]int[/color] c [color=#666666]=[/color] i.digits[height];
            current[color=#666666]->[/color]links[c] [color=#666666]=[/color] [color=#008000]**new**[/color] trie_node(height);
            current [color=#666666]=[/color] current[color=#666666]->[/color]links[c];
            [color=#666666]--[/color]height;
        }
        current[color=#666666]->[/color]data [color=#666666]=[/color] data;
        [color=#008000]**return**[/color] pair[color=#666666]<[/color][color=#B00040]bool[/color], [color=#B00040]int[/color][color=#666666]>[/color]([color=#008000]**true**[/color], data);
    }
};

[color=#B00040]void[/color] usage([color=#008000]**const**[/color] [color=#B00040]char[/color] [color=#666666]*[/color]s) {
    cerr [color=#666666]<<[/color] [color=#BA2121]"Usage: "[/color] [color=#666666]<<[/color] s
        [color=#666666]<<[/color] [color=#BA2121]" N trap"[/color] [color=#666666]<<[/color] endl;
    exit(EXIT_FAILURE);
}

[color=#B00040]int[/color] main([color=#B00040]int[/color] argc, [color=#B00040]char[/color] [color=#666666]*[/color]argv[]) {
    [color=#008000]**if**[/color] (argc [color=#666666]<[/color] [color=#666666]3[/color]) usage(argv[[color=#666666]0[/color]]);

    [color=#408080]*/* N: we'll find all Lychrel candidates up to N. */*[/color]
    istringstream s(argv[[color=#666666]1[/color]]);
    [color=#B00040]unsigned[/color] [color=#B00040]int[/color] N;
    [color=#008000]**if**[/color] ([color=#666666]![/color](s [color=#666666]>>[/color] N)) usage(argv[[color=#666666]0[/color]]);

    [color=#408080][i]/* trap: we'll iterate each number until it exceeds `trap' digits
     * and then declare it to be a Lychrel candidate.
     */[/i][/color]
    istringstream t(argv[[color=#666666]2[/color]]);
    [color=#B00040]unsigned[/color] [color=#B00040]int[/color] trap;
    [color=#008000]**if**[/color] ([color=#666666]![/color](t [color=#666666]>>[/color] trap)) usage(argv[[color=#666666]0[/color]]);

    trie_forest cache(trap[color=#666666]+[/color][color=#666666]1[/color]);

    [color=#408080][i]/* table entry semantics:
     * bit 0 -> whether Lychrel, bit 1 -> whether seed
     * (other bits unused)
     */[/i][/color]
    [color=#B00040]char[/color] [color=#666666]*[/color]table [color=#666666]=[/color] [color=#008000]**new**[/color] [color=#B00040]char[/color][N[color=#666666]+[/color][color=#666666]1[/color]];

    dec_int i(trap[color=#666666]+[/color][color=#666666]1[/color]), j(trap[color=#666666]+[/color][color=#666666]1[/color]);
    [color=#B00040]unsigned[/color] [color=#B00040]int[/color] a [color=#666666]=[/color] [color=#666666]0[/color];

    [color=#008000]**while**[/color] (a [color=#666666]<[/color] N) {
        [color=#666666]++[/color]i;
        [color=#666666]++[/color]a;

        j [color=#666666]=[/color] i;
        table[a] [color=#666666]=[/color] [color=#666666]0x3[/color];

        [color=#008000]**while**[/color] (j.size [color=#666666]<=[/color] trap) {
            pair[color=#666666]<[/color][color=#B00040]bool[/color], [color=#B00040]int[/color][color=#666666]>[/color] p(cache.insert(j, a));

            [color=#008000]**if**[/color] ([color=#666666]![/color]p.first) {
                table[a] [color=#666666]=[/color] table[p.second] [color=#666666]&[/color] [color=#666666]0x1[/color];
                [color=#008000]**break**[/color];
            }

            [color=#008000]**if**[/color] (j.reverse_add()) {
                table[a] [color=#666666]=[/color] [color=#666666]0[/color];
                [color=#008000]**break**[/color];
            }
        }

        [color=#008000]**if**[/color] (table[a]) {
            cout [color=#666666]<<[/color] i;
            [color=#008000]**if**[/color] (table[a] [color=#666666]&[/color] [color=#666666]0x2[/color]) cout [color=#666666]<<[/color] [color=#BA2121]" (seed)"[/color];
            cout [color=#666666]<<[/color] endl;
        }
    }

    [color=#008000]**delete**[/color] [] table;
    [color=#008000]**return**[/color] [color=#666666]0[/color];
}

```Typical results: ```
> g++ -ansi -Wall -pedantic -O3 -mtune=native ly07.cpp -o ly07
ly07.cpp: In member function ‘std::pair<bool, int> trie_forest::insert(const dec_int&, int)’:
ly07.cpp:166: warning: array subscript has type ‘char’
> time ly07 1000000 57 > /dev/null

real    0m1.473s
user    0m1.293s
sys     0m0.157s

```To verify the correctness of the code, I compute 173 seeds up to 1000000 (if I stop iterating once an iterate exceeds 100 digits).> **munky99999 said:**
> Updated my code. It seemingly works just fine now.

I checked out wiki and went to the actual iteration for 89. Noticed. Hey that goes way over long. So I changed my code to use long long. Works just fine.

I also changed from 30 to 3000 depth. Made no difference :)I hate to point out the obvious, but 3000 iterates will not fit within any built-in type without overflowing, so unless you started using extended-precision arithmetic...

---

### Post by Marlonsm on 2010-03-17
> **Lux Perpetua said:**
> I went ahead and made a new program with those modifications. Also, for the sake of speed, I went with a more straighforward (but memory-gluttonous) algorithm: keep a record of each non-palindrome ever visited (in an existence trie), making each record point to a table entry which is set to record its Lychrel-status. This way, we can stop iterating as soon as we find any number that has already been visited (whether Lychrel or not). 

This illustrates a basic but awesome data structure: the existence trie. It's a map data type implemented as a tree, but the keys aren't stored anywhere: the set of keys is encoded completely in the structure of the tree itself.

Although it's a good idea, I'm not really sure if it's actually faster.

Iterating a number is quite a fast task. Maybe it's not worth the extra memory and time to keep that list of already-found numbers just to save a few iterations.
If you look at my first try (in Python), it also does that, but there was no significant speed-up. Maybe in C it's different, tho, or maybe mine was just not well coded.
When I have time I'll try using that in my second code (much better than the first one), to see what happens to the speed.

---

### Post by Lux Perpetua on 2010-03-17
> **Marlonsm said:**
> Although it's a good idea, I'm not really sure if it's actually faster.

Iterating a number is quite a fast task. Maybe it's not worth the extra memory and time to keep that list of already-found numbers just to save a few iterations.
If you look at my first try (in Python), it also does that, but there was no significant speed-up. Maybe in C it's different, tho, or maybe mine was just not well coded.
When I have time I'll try using that in my second code (much better than the first one), to see what happens to the speed.It did apparently make a big difference, and the difference only got bigger as I increased the upper limit. I can identify all the seeds up to ten million in about 22 seconds with the new C++ program, using a digit-limit of 60. With the old C++ program, it takes about 286 seconds. That's more than ten times as long. I can't do it this instant, but I'd like to look into the causes of the speedup more when I have more time (and of course, everybody should feel free to hack/experiment with my code until then).

**Update**

I rewrote my first program with my new data structures (avoiding STL vectors and using my trie_forest instead of set<dec_int>) and did some profiling. I'll call the old algorithm (which only caches one iterate per family) "program A" and the new algorithm (which caches all non-palindromes) "program B". I compiled both for profiling (flag -p) and ran them both with parameters N=1000000, trap=37. Here's a quick summary showing how much time each program spend doing what operations: 

```

               |  program A  |  program B  
---------------+-------------+-------------
reverse_add    |      94%    |      26%
trie insertion |       1%    |      45%
increment      |       4%    |      12%

```The 94% in reverse_add for program A is definitely worth trying to optimize. (Program A calls dec_int::reverse_add 13,302,664 times, while program B only calls it 1,019,550 times.)

---

### Post by Marlonsm on 2010-03-18
I modified both my codes and came to a conclusion.
The second one takes about 0.4s to run up to 10000, without skiping already found numbers. If I make it skip only the already found Lychrel, it'll take 0.6 seconds. But if I make it skip both found Lychrel and non-Lychrel, it takes some 6 or 7 seconds. Same happens to the first one.
So (at least for me) it's not worth keeping a list of already found numbers to skip them while iterating, it's taking more time to check and keep the list than to iterate the numbers.

---

### Post by Lux Perpetua on 2010-03-19
Marlonsm - I bet you're using an inefficient data structure. For reference, here's my "cache everything" python code: ```
import sys

N = int(sys.argv[1])
t = int(sys.argv[2])

def reverse(x):
    return int(str(x)[::-1])

# cache maps a number to the smallest number
# whose thread contains it. We'll add entries
# to cache as we find them. 
cache = dict()
lychrels = set()

for n in xrange(1, N + 1):
    m = n
    mr = reverse(n)

    seed = True
    lychrel = True

    while len(str(m)) < t:
        m = m + mr
        mr = reverse(m)
        
        if cache.has_key(m):
            seed = False
            if cache[m] not in lychrels:
                lychrel = False
            break
        
        cache[m] = n

        if m == mr:
            lychrel = False
            break
    
    if lychrel:
        lychrels.add(n)
        print n,
        if seed:
            print "(seed)",
        print
```
Here's my "bare minimum cache" python code (which doesn't store any results but the last iterate of each thread, which is used to detect seeds): ```
import sys

N = int(sys.argv[1])
t = int(sys.argv[2])

def reverse(x):
    return int(str(x)[::-1])

cache = set()

for n in xrange(1, N + 1):
    m = n
    mr = reverse(n)

    lychrel = True

    while len(str(m)) < t:
        m = m + mr
        mr = reverse(m)
        
        if m == mr:
            lychrel = False
            break

    if lychrel:
        print n,
        if m not in cache:
            cache.add(m)
            print "(seed)",
        print
```The first one beats the second one handily on my machine (with parameters, say, N=100000, t=30). I'm not sure why, but your (later) program actually seems to be slightly faster than my second program, but it's still quite a bit slower than the first one.

---

### Post by schauerlich on 2010-03-19
Once again the beginner's challenge has turned into a speed competition. :)

---

### Post by s.fox on 2010-03-19
> **schauerlich said:**
> Once again the beginner's challenge has turned into a speed competition. :)

I was just thinking the same myself.   Perhaps the next challenge will not go the same way :D

---

### Post by Marlonsm on 2010-03-19
> **Lux Perpetua said:**
> Marlonsm - I bet you're using an inefficient data structure. For reference, here's my "cache everything" python code: 
(Code)
The first one beats the second one handily on my machine (with parameters, say, N=100000, t=30). I'm not sure why, but your (later) program actually seems to be slightly faster than my second program, but it's still quite a bit slower than the first one.
I used lists, as it was the only way I could think of.

> **schauerlich said:**
> Once again the beginner's challenge has turned into a speed competition. :)

It's quite normal... People do the code, and while there is no winner, they keeps trying to improve it, and usually, improving means making it faster.

---

### Post by Lux Perpetua on 2010-03-19
> **Lux Perpetua said:**
> I'm not sure why, but your (later) program actually seems to be slightly faster than my second program, but it's still quite a bit slower than the first one.Oh, duh. My program is actually faster. I forgot to raise the iteration count in your program.
> **schauerlich said:**
> Once again the beginner's challenge has turned into a speed competition. :)Well, yes and no. There are limits to how far I'll go to achieve a fast program; speed itself isn't the only goal. However, speed is a positive attribute, so if I can speed up my program without making it much more complicated, I'll probably do so. This particular problem is a good example: the naive solutions are pretty simple and slow, but it doesn't take much to get a significantly faster solution. It might even be as simple as switching out one data structure for a functionally equivalent one. For example: 
> **Marlonsm said:**
> I used lists, as it was the only way I could think of.
Yeah, lists are pretty slow when it comes to searching. For a typical list (implemented as a linked list), searching requires iterating through the whole list, which obviously becomes slow as the list becomes large. That's why data structures like "set" and "dict" exist. They don't actually provide any functionality that lists don't have: indeed, one could easily implement either abstract data type as a list if desired. However, there are much faster data structures like trees and hash tables that are preferred if the number of keys/entries is large. To be fair, trees & hash tables also slow down as you insert more stuff, but at a much more acceptable rate. The time required to search a list with N items is roughly proportional to N, while the time required to search a (balanced) tree with N items is proportional to log(N). The time required to search a hash table with N entries is on average roughly *constant*...that is, if you can provide a really great hash function. (In the worst case, a hash table might degrade to logarithmic-time or even linear-time depending on the implementation.)

---

### Post by compjoev on 2010-03-20
about chall # 10 see 
[http://www.p196.org](http://www.p196.org)
 
 
 
has many lists much info about this.

---

### Post by conehead77 on 2010-03-20
One more entry: Haskell, a monadic approach.

[PHP]import Control.Monad ((>=>))

findNextNumber:: Integer -> Maybe Integer 
findNextNumber x
    | isPalin x = Nothing
    | otherwise = Just $ computeNext x
    where isPalin x = (read $ reverse $ show x) == x
    
computeNext :: (Read a, Num a) => a -> a
computeNext x = (read $ reverse $ show x) + x

findLychrel ::  Integer -> (Integer, Maybe Integer)
findLychrel x = (x, myFold x)

myFold :: Integer -> Maybe Integer
myFold = (foldr (>=>) return $ replicate 30 findNextNumber) . computeNext 

findLychrels :: [Integer] -> [(Integer, Maybe Integer)]
findLychrels = filter (\(_, x) -> x /= Nothing) . map findLychrel

main = mapM_ print $ findLychrels [1..10000][/PHP]
It prints the Lychrel numbers together with the number which was calculated in the last iteration:

```

(196,Just 4413700670963144)
(295,Just 4413700670963144)
(394,Just 4413700670963144)
(493,Just 4413700670963144)
(592,Just 4413700670963144)
(689,Just 8827391431036288)
(691,Just 4413700670963144)
(788,Just 8827391431036288)
(790,Just 4413700670963144)
(879,Just 84049023732085137)
(887,Just 8827391431036288)
(978,Just 84049023732085137)
(986,Just 8827391431036288)
(1495,Just 17653692772973576)
(1497,Just 157207047464179185)
(1585,Just 17653692772973576)
(1587,Just 157207047464179185)
(1675,Just 17653692772973576)
(1677,Just 157207047464179185)
(1765,Just 17653692772973576)
(1767,Just 157207047464179185)
(1855,Just 17653692772973576)
(1857,Just 157207047464179185)
(1945,Just 17653692772973576)
(1947,Just 157207047464179185)
(1997,Just 9352262944502522638)
(2494,Just 17653692772973576)
(2496,Just 157207047464179185)
(2584,Just 17653692772973576)
(2586,Just 157207047464179185)
(2674,Just 17653692772973576)
(2676,Just 157207047464179185)
(2764,Just 17653692772973576)
(2766,Just 157207047464179185)
(2854,Just 17653692772973576)
(2856,Just 157207047464179185)
(2944,Just 17653692772973576)
(2946,Just 157207047464179185)
(2996,Just 9352262944502522638)
(3493,Just 17653692772973576)
(3495,Just 157207047464179185)
(3583,Just 17653692772973576)
(3585,Just 157207047464179185)
(3673,Just 17653692772973576)
(3675,Just 157207047464179185)
(3763,Just 17653692772973576)
(3765,Just 157207047464179185)
(3853,Just 17653692772973576)
(3855,Just 157207047464179185)
(3943,Just 17653692772973576)
(3945,Just 157207047464179185)
(3995,Just 9352262944502522638)
(4079,Just 85191620502609247)
(4169,Just 85191620502609247)
(4259,Just 85191620502609247)
(4349,Just 85191620502609247)
(4439,Just 85191620502609247)
(4492,Just 17653692772973576)
(4494,Just 157207047464179185)
(4529,Just 85191620502609247)
(4582,Just 17653692772973576)
(4584,Just 157207047464179185)
(4619,Just 85191620502609247)
(4672,Just 17653692772973576)
(4674,Just 157207047464179185)
(4709,Just 85191620502609247)
(4762,Just 17653692772973576)
(4764,Just 157207047464179185)
(4799,Just 85191620502609247)
(4852,Just 17653692772973576)
(4854,Just 157207047464179185)
(4889,Just 85191620502609247)
(4942,Just 17653692772973576)
(4944,Just 157207047464179185)
(4979,Just 85191620502609247)
(4994,Just 9352262944502522638)
(5078,Just 85191620502609247)
(5168,Just 85191620502609247)
(5258,Just 85191620502609247)
(5348,Just 85191620502609247)
(5438,Just 85191620502609247)
(5491,Just 17653692772973576)
(5493,Just 157207047464179185)
(5528,Just 85191620502609247)
(5581,Just 17653692772973576)
(5583,Just 157207047464179185)
(5618,Just 85191620502609247)
(5671,Just 17653692772973576)
(5673,Just 157207047464179185)
(5708,Just 85191620502609247)
(5761,Just 17653692772973576)
(5763,Just 157207047464179185)
(5798,Just 85191620502609247)
(5851,Just 17653692772973576)
(5853,Just 157207047464179185)
(5888,Just 85191620502609247)
(5941,Just 17653692772973576)
(5943,Just 157207047464179185)
(5978,Just 85191620502609247)
(5993,Just 9352262944502522638)
(6077,Just 85191620502609247)
(6167,Just 85191620502609247)
(6257,Just 85191620502609247)
(6347,Just 85191620502609247)
(6437,Just 85191620502609247)
(6490,Just 17653692772973576)
(6492,Just 157207047464179185)
(6527,Just 85191620502609247)
(6580,Just 17653692772973576)
(6582,Just 157207047464179185)
(6617,Just 85191620502609247)
(6670,Just 17653692772973576)
(6672,Just 157207047464179185)
(6707,Just 85191620502609247)
(6760,Just 17653692772973576)
(6762,Just 157207047464179185)
(6797,Just 85191620502609247)
(6850,Just 17653692772973576)
(6852,Just 157207047464179185)
(6887,Just 85191620502609247)
(6940,Just 17653692772973576)
(6942,Just 157207047464179185)
(6977,Just 85191620502609247)
(6992,Just 9352262944502522638)
(7059,Just 798587266661795886)
(7076,Just 85191620502609247)
(7149,Just 798587266661795886)
(7166,Just 85191620502609247)
(7239,Just 798587266661795886)
(7256,Just 85191620502609247)
(7329,Just 798587266661795886)
(7346,Just 85191620502609247)
(7419,Just 798587266661795886)
(7436,Just 85191620502609247)
(7491,Just 157207047464179185)
(7509,Just 798587266661795886)
(7526,Just 85191620502609247)
(7581,Just 157207047464179185)
(7599,Just 798587266661795886)
(7616,Just 85191620502609247)
(7671,Just 157207047464179185)
(7689,Just 798587266661795886)
(7706,Just 85191620502609247)
(7761,Just 157207047464179185)
(7779,Just 798587266661795886)
(7796,Just 85191620502609247)
(7851,Just 157207047464179185)
(7869,Just 798587266661795886)
(7886,Just 85191620502609247)
(7941,Just 157207047464179185)
(7959,Just 798587266661795886)
(7976,Just 85191620502609247)
(7991,Just 9352262944502522638)
(8058,Just 798587266661795886)
(8075,Just 85191620502609247)
(8079,Just 739178512204881936)
(8089,Just 17714514998995145177)
(8148,Just 798587266661795886)
(8165,Just 85191620502609247)
(8169,Just 739178512204881936)
(8179,Just 17714514998995145177)
(8238,Just 798587266661795886)
(8255,Just 85191620502609247)
(8259,Just 739178512204881936)
(8269,Just 17714514998995145177)
(8328,Just 798587266661795886)
(8345,Just 85191620502609247)
(8349,Just 739178512204881936)
(8359,Just 17714514998995145177)
(8418,Just 798587266661795886)
(8435,Just 85191620502609247)
(8439,Just 739178512204881936)
(8449,Just 17714514998995145177)
(8490,Just 157207047464179185)
(8508,Just 798587266661795886)
(8525,Just 85191620502609247)
(8529,Just 739178512204881936)
(8539,Just 17714514998995145177)
(8580,Just 157207047464179185)
(8598,Just 798587266661795886)
(8615,Just 85191620502609247)
(8619,Just 739178512204881936)
(8629,Just 17714514998995145177)
(8670,Just 157207047464179185)
(8688,Just 798587266661795886)
(8705,Just 85191620502609247)
(8709,Just 739178512204881936)
(8719,Just 17714514998995145177)
(8760,Just 157207047464179185)
(8778,Just 798587266661795886)
(8795,Just 85191620502609247)
(8799,Just 739178512204881936)
(8809,Just 17714514998995145177)
(8850,Just 157207047464179185)
(8868,Just 798587266661795886)
(8885,Just 85191620502609247)
(8889,Just 739178512204881936)
(8899,Just 17714514998995145177)
(8940,Just 157207047464179185)
(8958,Just 798587266661795886)
(8975,Just 85191620502609247)
(8979,Just 739178512204881936)
(8989,Just 17714514998995145177)
(8990,Just 9352262944502522638)
(9057,Just 798587266661795886)
(9074,Just 85191620502609247)
(9078,Just 739178512204881936)
(9088,Just 17714514998995145177)
(9147,Just 798587266661795886)
(9164,Just 85191620502609247)
(9168,Just 739178512204881936)
(9178,Just 17714514998995145177)
(9237,Just 798587266661795886)
(9254,Just 85191620502609247)
(9258,Just 739178512204881936)
(9268,Just 17714514998995145177)
(9327,Just 798587266661795886)
(9344,Just 85191620502609247)
(9348,Just 739178512204881936)
(9358,Just 17714514998995145177)
(9417,Just 798587266661795886)
(9434,Just 85191620502609247)
(9438,Just 739178512204881936)
(9448,Just 17714514998995145177)
(9507,Just 798587266661795886)
(9524,Just 85191620502609247)
(9528,Just 739178512204881936)
(9538,Just 17714514998995145177)
(9597,Just 798587266661795886)
(9614,Just 85191620502609247)
(9618,Just 739178512204881936)
(9628,Just 17714514998995145177)
(9687,Just 798587266661795886)
(9704,Just 85191620502609247)
(9708,Just 739178512204881936)
(9718,Just 17714514998995145177)
(9777,Just 798587266661795886)
(9794,Just 85191620502609247)
(9798,Just 739178512204881936)
(9808,Just 17714514998995145177)
(9867,Just 798587266661795886)
(9884,Just 85191620502609247)
(9888,Just 739178512204881936)
(9898,Just 17714514998995145177)
(9957,Just 798587266661795886)
(9974,Just 85191620502609247)
(9978,Just 739178512204881936)
(9988,Just 17714514998995145177)
(9999,Just 1765733527616337576)

```

---

### Post by Marlonsm on 2010-03-21
> **Lux Perpetua said:**
> Yeah, lists are pretty slow when it comes to searching. For a typical list (implemented as a linked list), searching requires iterating through the whole list, which obviously becomes slow as the list becomes large. That's why data structures like "set" and "dict" exist. They don't actually provide any functionality that lists don't have: indeed, one could easily implement either abstract data type as a list if desired. However, there are much faster data structures like trees and hash tables that are preferred if the number of keys/entries is large. To be fair, trees & hash tables also slow down as you insert more stuff, but at a much more acceptable rate. The time required to search a list with N items is roughly proportional to N, while the time required to search a (balanced) tree with N items is proportional to log(N). The time required to search a hash table with N entries is on average roughly *constant*...that is, if you can provide a really great hash function. (In the worst case, a hash table might degrade to logarithmic-time or even linear-time depending on the implementation.)

I've tried it again using sets, it was faster, but not enough. It took 0.6 seconds instead of 0.16.
But I've tried using sets in the part it checks if a number is a seed and I got a small improvement, 0.14s instead of 0.16.
Here is my code (I think it's final):
[php]def reverse(toReverse):
	return int(str(toReverse)[::-1])
def isSeed(number, Lychrel):  #This tests if the thread is new, if so, the starting number is a seed
	if number in Lychrel:
		return False
	Lychrel.add(number)
	return True
def isLychrel(number, Lychrel, iterations): #Tries the number many times before assuming it's Lychrel
	for i in range (1,iterations):
		number += reverse(number)
		if number == reverse(number):
			return False
	if isSeed(number, Lychrel) == True:
		return "seed"
	else:
		return "Lychrel"
def main(upTo, iterations):
	Lychrel = set([])
	for number in range (1,upTo): #Run for all numbers up to the intended one and print the results
		Lych = isLychrel(number, Lychrel, iterations)
		if Lych == "seed":
			print number, "<--- Is seed"
		elif Lych == "Lychrel":
			print number
upTo = input("Do you want to find Lychrel candidates up to which number? ")
iterations = input("How many iterations do you want before a number is considered Lychrel? ")
main(upTo, iterations)[/php]

---

### Post by cprofitt on 2010-03-22
Testing speed is a good exercise, but as a beginners contest this is not about the final speed result. I will close the entries Thursday GMT 00:00 and announce the winners by Saturday.

---

### Post by HellBoz on 2010-03-22
What I'm doing wrong if my application says 89 is a Lychrel number ?

---

### Post by Lux Perpetua on 2010-03-22
> **HellBoz said:**
> What I'm doing wrong if my application says 89 is a Lychrel number ?It could be that you're not iterating it high enough (IIRC, it takes somewhere around 24 iterations to resolve into a palindrome), or that you're overflowing your integers before it turns into a palindrome.

---

### Post by HellBoz on 2010-03-22
> **Lux Perpetua said:**
> It could be that you're not iterating it high enough (IIRC, it takes somewhere around 24 iterations to resolve into a palindrome), [COLOR=Red]or that you're overflowing your integers before it turns into a palindrome.[/COLOR]

So if I run into an overflow, it's ( theoretically ) not a Lychrel number ?

---

### Post by munky99999 on 2010-03-22
> **HellBoz said:**
> So if I run into an overflow, it's ( theoretically ) not a Lychrel number ?

Use the largest int value.

Long Long needed to be used for my program. Long was being overflowed.


I was thinking of setting up postgresql in order to use arbitrary precision datatypes. I dont really know how to create my own datatype.

---

### Post by HellBoz on 2010-03-22
> **munky99999 said:**
> Use the largest int value.

Long Long needed to be used for my program. Long was being overflowed.


I was thinking of setting up postgresql in order to use arbitrary precision datatypes. I dont really know how to create my own datatype.

Already tried - still getting the same result. Anyway, switched to Ruby - overflow problem solved **.

** One problem solved, another acquired .. :D

---

### Post by HellBoz on 2010-03-22
[PHP]#!/usr/bin/env ruby

def revnum(num)
    return num.to_s().reverse.to_i()
end

for num in (11..10000)
    sum = num + revnum(num)
    if (sum == revnum(sum))
        # Palindrome found .. 
    elsif
        for iteration in (2..30)
            sum = sum + revnum(sum)
            if (sum == revnum(sum))
                # Palindrome found ..
                break
            else
                if (iteration == 30)
                    print num.to_s() + " "
                    break
                end
            end
        end
    end
end
[/PHP]

```
ruby lychrel.rb
```

---

### Post by WillFerrellLuva on 2010-03-25
my solution in c++

```

#include <cmath>
#include <iostream>
#include <vector>
#include "big_int.h"

using namespace std;



bool palindrome_check(big_int p_check)
{
	bool palindrome_answer = false;
	if( p_check == p_check.reverse_digits() )
	{
		palindrome_answer = true;
	}
	return palindrome_answer;
}

bool lychrel_check(big_int l_check)
{
	bool lychrel_answer = true;
	int i = 0;
	
	do{
		
		l_check  = l_check + l_check.reverse_digits();
		lychrel_answer = !(palindrome_check(l_check));
		i++;
		
	}while( lychrel_answer && i <= 30);
	
	return lychrel_answer;
}

int main()

{
	vector<big_int> candidates;
	big_int one;
	
	for (int i = 1; i < 10000; i++)
	{
		
		one.set(i);
		if(lychrel_check(one))
		{
			candidates.push_back(one);
		}
	}
	
	cout << "Lychrel candidates: ";
	for(unsigned int i = 0; i < candidates.size(); i++)
	{
		candidates[i].display();
		cout << " ";
	}
	cout << endl;
	

	return 0;

}

```


and big_int is here:  (excluded header for brevity)

```

#include "big_int.h"
#include <cmath>
using namespace std;

big_int::big_int()

{
	bint = {0};

}

void big_int::set(int value)
{
	for(int i = size-1; i >= 0; i--) //starting from big end of int
	{
		if( (value / pow(10, i))  >= 1 ) //if next biggest digit is non zero
		{
			bint[i] = floor(value / pow(10, i));  //set the digit in the array
			value -= ( floor(value / pow(10, i)) * pow(10, i)); //remove the amount put into the array from the original number
		}
		else
		{
			bint[i] = 0;
		}
	}
}

void big_int::display() const

{

	//find out what digit to start printing from so i'm not printing out 100 0s
	bool done = false;
	int place_holder = 0;
	int i = size - 1;
	do{
		if( bint[i] > 0 )
		{
			done = true;
			place_holder = i;
		}
	
		i--;
		
	}while( (!done) && (i >= 0) );
	

	//display contents of bint[]
	for(int j = place_holder; j >= 0; j--)
	{
		cout << bint[j];
	}

}



big_int big_int::reverse_digits()
{
	big_int finish;
	//find biggest digit in bint[]
	bool done = false;
	int place_holder = 0;
	int i = size - 1;
	do{
		if( bint[i] > 0 )
		{
			done = true;
			place_holder = i;
		}
	
		i--;
		
	}while(!done && (i >= 0) );
	
	for(int j = 0; j <= place_holder; j++)
	{
		finish.bint[j] = bint[ place_holder - j ];
	}
	
	return finish;
}

big_int big_int::operator+(big_int one)
{
	big_int answer;
	int remainder = 0;
	for(int i = 0; i < size; i++) //start from small end of number
	{
		answer.bint[i] = one.bint[i] + bint[i] + remainder;
		if(answer.bint[i] > 9)  //there is a remainder
		{
			remainder = floor( answer.bint[i] / 10 );
			answer.bint[i] = answer.bint[i] - 10;
			
		}
		else		//there is no remainder
		{
			remainder = 0;
		}
	}
	
	return answer;
}

bool big_int::operator==(big_int two)
{
	bool answer = false;
	
	int i = 0;
	do
	{
		answer = (bint[i] == two.bint[i]);
		i++;
	}while (answer && (i < size));
	
	return answer;
}

```

My program gives the following as Lychrel candidates under 10,000:

```

Lychrel candidates: 196 295 394 493 592 689 691 788 790 879 887 978 986 1495 
1497 1585 1587 1675 1677 1765 1767 1855 1857 1945 1947 1997 2494 2496 2584 2586 
2674 2676 2764 2766 2854 2856 2944 2946 2996 3493 3495 3583 3585 3673 3675 3763 
3765 3853 3855 3943 3945 3995 4079 4169 4259 4349 4439 4492 4494 4529 4582 4584 
4619 4672 4674 4709 4762 4764 4799 4852 4854 4889 4942 4944 4979 4994 5078 5168 
5258 5348 5438 5491 5493 5528 5581 5583 5618 5671 5673 5708 5761 5763 5798 5851 
5853 5888 5941 5943 5978 5993 6077 6167 6257 6347 6437 6490 6492 6527 6580 6582 
6617 6670 6672 6707 6760 6762 6797 6850 6852 6887 6940 6942 6977 6992 7059 7076 
7149 7166 7239 7256 7329 7346 7419 7436 7491 7509 7526 7581 7599 7616 7671 7689 
7706 7761 7779 7796 7851 7869 7886 7941 7959 7976 7991 8058 8075 8079 8089 8148 
8165 8169 8179 8238 8255 8259 8269 8328 8345 8349 8359 8418 8435 8439 8449 8490 
8508 8525 8529 8539 8580 8598 8615 8619 8629 8670 8688 8705 8709 8719 8760 8778 
8795 8799 8809 8850 8868 8885 8889 8899 8940 8958 8975 8979 8989 8990 9057 9074 
9078 9088 9147 9164 9168 9178 9237 9254 9258 9268 9327 9344 9348 9358 9417 9434 
9438 9448 9507 9524 9528 9538 9597 9614 9618 9628 9687 9704 9708 9718 9777 9794 
9798 9808 9867 9884 9888 9898 9957 9974 9978 9988 9999 


```

---

### Post by schauerlich on 2010-03-25
Numbers which are themselves palindromes can still be Lychrels. That means that 9999 is a candidate. You should only start checking palindromes after the first iteration.

---

### Post by WillFerrellLuva on 2010-03-25
ty for the info, I for some reason didnt think that palindromes counted.  I made the fix and updated my answer ;)

---

### Post by HellBoz on 2010-03-25
> **schauerlich said:**
> Numbers which are themselves palindromes can still be Lychrels. That means that 9999 is a candidate. You should only start checking palindromes after the first iteration.

Mine says 9999 is a lychrel, too, tough I check for it only after the first iteration.

---

### Post by WillFerrellLuva on 2010-03-25
was looking at the posts and noticed that you are able to use a terminal command to show how fast your program executed.  i did :

```

chris@chris-desktop:~/Code/Projects/Challenge 10$ time ./driver > /dev/null

real	0m0.275s
user	0m0.272s
sys	0m0.000s


```

is that good?  can someone please explain what the 3 numbers mean (yes I know I am a noob)?

---

### Post by schauerlich on 2010-03-25
> **WillFerrellLuva said:**
> is that good?  can someone please explain what the 3 numbers mean (yes I know I am a noob)?

Try running it a few times, caching will make later runs faster. 

Real time is how long it is from when you hit enter to when the program finishes running. User time is how time "your" code spends running. System time is how much time system calls (like "fork" or "exec") spend running.

---

### Post by cprofitt on 2010-03-25
--- here is the code I had when asking the question ---

[PHP]# written by cprofitt 2/26/2010
# version .0.1

import time

def is_lychrel(n):
    n = str(n)
    for count in xrange(0, 50):
        n = str(int(n) + int(n[::-1]))
        if n == n[::-1]: return False
    return True

starttime = time.time()
for n in xrange(0,10000):
    if is_lychrel(n): print n

stoptime = time.time()
print 'Time to complete: %s secs' % (stoptime - starttime)[/PHP]

The time to complete was:  0.500995874405 secs

I will begin judging the entries tonight.

---

### Post by Lux Perpetua on 2010-03-25
real = total elapsed time; user = time spent in user space (i. e., your code proper and library functions); and sys = time spent in kernel space (i. e., syscalls like read(), write(), etc.). You can obtain all of this from the "time" manual page (**man time** in your terminal).

---

### Post by cprofitt on 2010-03-25
The winner of the challenge goes to: [Bachstelze]("http://ubuntuforums.org/member.php?u=51114")

He was the first to understand what was wrong with his code when I mentioned most were not correct.

This challenge was less about elegant code and more about realizing that the best most efficient code in the world is really, really bad if it is answering the wrong question.

Honorable Mentions to:
[Marlonsm]("http://ubuntuforums.org/member.php?u=792604"), [howlingmadhowie]("http://ubuntuforums.org/member.php?u=141322") and [Mathiasdm]("http://ubuntuforums.org/member.php?u=124600") (great fast code)

It's up to [Bachstelze]("http://ubuntuforums.org/member.php?u=51114") to come up with the next challenge. Thanks to all participants. I hope everyone was able to take something away from this challenge!

---

### Post by schauerlich on 2010-03-26
I was about to post a modifcation to my C entry. :| Oh well, this one is just for fun.

It's much quicker, using arithmetic to reverse the digits instead of string manipulation.

```
[color=#BC7A00]#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_LYCHREL 10000
#define DEPTH 30
[/color]
[color=#B00040]long[/color] [color=#0000FF]reverse[/color]([color=#B00040]long[/color] n) {
  [color=#B00040]long[/color] nRev [color=#666666]=[/color] [color=#666666]0[/color];
  
  [color=#408080][i]// let's say n = 123 when we come into the function
[/i][/color]  [color=#008000]**while**[/color] (n) {
    [color=#408080][i]// after one iteration, n = 12, nRev = 3
[/i][/color]    
    [color=#408080][i]// shift nRev's digits to the left by one
[/i][/color]    nRev [color=#666666]*=[/color] [color=#666666]10[/color];
    [color=#408080][i]// n = 12
[/i][/color]    [color=#408080][i]// nRev = 30
[/i][/color]    
    [color=#408080][i]// Get the last digit from n and add it to nRev
[/i][/color]    [color=#408080][i]// n / 10 = 1 remainder 2, so n % 10 = 2
[/i][/color]    nRev [color=#666666]+=[/color] n [color=#666666]%[/color] [color=#666666]10[/color];
    [color=#408080][i]// n = 12
[/i][/color]    [color=#408080][i]// nRev = 32
[/i][/color]    
    [color=#408080][i]// shift n's digits to the right by one
[/i][/color]    n [color=#666666]/=[/color] [color=#666666]10[/color];
    [color=#408080][i]// n = 1
[/i][/color]    [color=#408080][i]// nRev = 32
[/i][/color]    
    [color=#408080][i]// after we go around again, n = 0 and nRev = 321
[/i][/color]    [color=#408080][i]// since n = 0, we leave the loop and return nRev
[/i][/color]  }
  
  [color=#008000]**return**[/color] nRev;
} [color=#408080][i]// reverse()
[/i][/color]

[color=#B00040]int[/color] [color=#0000FF]islychrel[/color]([color=#B00040]long[/color] n, [color=#B00040]long[/color] d) {
  [color=#408080][i]// recursively decides if a number is a lychrel candidate after depth d
[/i][/color]  
  [color=#408080][i]// reverse n and store it in a long
[/i][/color]  [color=#B00040]long[/color] nRev [color=#666666]=[/color] reverse(n);
  
  [color=#408080][i]// if we've reached the maximum recursion depth, we're done, so 
[/i][/color]  [color=#408080][i]// return true (ie, n is a lychrel candidate)
[/i][/color]  [color=#008000]**if**[/color] (d [color=#666666]<=[/color] [color=#666666]0[/color])
    [color=#008000]**return**[/color] [color=#666666]1[/color];
  
  [color=#408080][i]// if the number is a palindrome, we're done and should return false
[/i][/color]  [color=#408080][i]// (n is NOT a lychrel candidate)   
[/i][/color]  [color=#008000]**if**[/color] (d [color=#666666]!=[/color] DEPTH [color=#666666]&&[/color] n [color=#666666]==[/color] nRev)
    [color=#008000]**return**[/color] [color=#666666]0[/color];
  
  [color=#408080][i]// now we go around again, this time checking if the number plus its reverse is
[/i][/color]  [color=#408080][i]// a palindrome. We decrement the depth so that once it gets to zero, we give up
[/i][/color]  [color=#408080][i]// and the recursion "unwinds"
[/i][/color]  [color=#008000]**return**[/color] islychrel(n [color=#666666]+[/color] nRev, d [color=#666666]-[/color] [color=#666666]1[/color]);
  
} [color=#408080][i]// islychrel()
[/i][/color]


[color=#B00040]int[/color] [color=#0000FF]main[/color]([color=#B00040]int[/color] argc, [color=#B00040]char[/color] [color=#666666]*[/color]argv[]) {
  [color=#B00040]long[/color] i;
  
  [color=#408080][i]// iterate through 0 - MAX_LYCHREL (for this challenge, 10000)
[/i][/color]  [color=#408080][i]// and print it out if it's a lychrel candidate
[/i][/color]  [color=#008000]**for**[/color] (i [color=#666666]=[/color] [color=#666666]0[/color]; i [color=#666666]<=[/color] MAX_LYCHREL; i[color=#666666]++[/color])
    [color=#008000]**if**[/color] (islychrel(i, DEPTH))
      printf([color=#BA2121]"%ld[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], i);
  
  [color=#008000]**return**[/color] [color=#666666]0[/color];
  
} [color=#408080][i]// main()
[/i][/color]
```

```

eric@river:~/src/begchal/10$ gcc -O3 lychrelfast.c -o l.out
eric@river:~/src/begchal/10$ time ./l.out > /dev/null
real	0m0.008s
user	0m0.004s
sys	0m0.003s

```

---

### Post by WillFerrellLuva on 2010-03-26
ty for the info about time, i will have to check out the man page.

I 1st tried to do this challenge using integers but as you might guess I ran into overflow problems, so I hastily decided to create my own big_int class to work with (and learned some about operator overloading in the process).  I didnt even consider using longs :-(.  

@ schauerlich - wow your time really blew mine out of the water :-)
I would guess that my big_int class slowed my program down because I was working with 100 digit arrays, and probably had messy operator overloads.

---

### Post by schauerlich on 2010-07-25
Well, now that I've learned a bit of Scheme, I figured I'd give howie some competition. :)

```
(define *depth* 30)
(define *max-lychrel* 10000)

(define (reverse-num n)
  (define (rev-iter n n-rev)
    (if (zero? n)
        n-rev
        (rev-iter (quotient n 10) (+ (* 10 n-rev) (remainder n 10)))))
  (rev-iter n 0))

(define (is-lychrel? n d)
  (let ((n-rev (reverse-num n)))
    (cond ((<= d 0)
           #t)
          ((and (not (= d *depth*)) (= n n-rev))
           #f)
          (else
           (is-lychrel? (+ n n-rev) (- d 1))))))

(define (find-lychrels i)
  (let ((so-far '()))
    (define (find-iter i so-far)
      (cond ((= i 0) 
             so-far)
            ((is-lychrel? i *depth*)
             (find-iter (- i 1) (cons i so-far)))
            (else
             (find-iter (- i 1) so-far))))
    (find-iter i so-far)))

(find-lychrels *max-lychrel*)
```

The algorithm is basically the same as the rest of my entries.

---

### Post by schauerlich on 2010-09-18
And again in ruby. :)

```
[color=#880000]DEPTH[/color] [color=#666666]=[/color] [color=#666666]30[/color]
[color=#880000]MAX_LYCHREL[/color] [color=#666666]=[/color] [color=#666666]10000[/color]

[color=#008000]**class**[/color] [color=#0000FF]**Integer**[/color]
  [color=#008000]**def**[/color] [color=#0000FF]is_lychrel?[/color](d[color=#666666]=[/color][color=#880000]DEPTH[/color])
    [color=#008000]**def**[/color] [color=#0000FF]reverse[/color]
      [color=#008000]**return**[/color] [color=#008000]self[/color][color=#666666].[/color]to_s[color=#666666].[/color]reverse[color=#666666].[/color]to_i
    [color=#008000]**end**[/color]

    [color=#008000]**if**[/color] d [color=#666666]==[/color] [color=#666666]0[/color]
      [color=#008000]**return**[/color] [color=#008000]true[/color]
    [color=#008000]**elsif**[/color] (d [color=#666666]!=[/color] [color=#880000]DEPTH[/color]) [color=#AA22FF]**and**[/color] ([color=#008000]self[/color] [color=#666666]==[/color] [color=#008000]self[/color][color=#666666].[/color]reverse)
      [color=#008000]**return**[/color] [color=#008000]false[/color]
    [color=#008000]**end**[/color]

    [color=#008000]**return**[/color] ([color=#008000]self[/color] [color=#666666]+[/color] [color=#008000]self[/color][color=#666666].[/color]reverse)[color=#666666].[/color]is_lychrel?(d[color=#666666]-[/color][color=#666666]1[/color])
  [color=#008000]**end**[/color]
[color=#008000]**end**[/color]

[color=#008000]puts[/color] ([color=#666666]1[/color][color=#666666].[/color].[color=#880000]MAX_LYCHREL[/color])[color=#666666].[/color]select { [color=#666666]|[/color]x[color=#666666]|[/color] x[color=#666666].[/color]is_lychrel? }

```

---

### Post by JackDarkStone on 2011-06-08
I wouldn't consider this a beginner challenge.

---

### Post by cprofitt on 2011-06-11
> **JackDarkStone said:**
> I wouldn't consider this a beginner challenge.

Jack:

Perhaps, but it is a fairly simple program once you understand the problem.

---

### Post by Spae on 2013-02-06
That was fun and challenging
```
def rev_N(N):							#reverse a number
    return int(str(N)[::-1])

def main():
    for N in range(11,10001,1):					#Testing numbers 11 to 10000
        attempt_N = 0
        original_number = N
        number = original_number
        reverse = rev_N(number)

        while attempt_N < 30 and number != reverse:		#try 30 times or until a palindrome has been found
            attempt_N = attempt_N + 1 				#counting tries	

            if number != reverse and attempt_N == 30:		#After attempt_N attempts a palindrome has not been formed
                print(original_number,'is a lychrel candidate') #until the 30th iteration
        
            elif number != reverse:				#if the numbers are not equal yet:
                number = number + reverse			#add them together to make new number
                reverse = rev_N(number)				#and new reverse number
main()
```
#I realise it tests some numbers twice like 59 and 95, and then 95 and 59. Not sure if it's easy to fix that.

---

### Post by Bachstelze on 2013-02-06
Thread closed in 3, 2, 1...

---

### Post by matehussilvapb on 2013-09-14
You can't prove that a number is lychrel number ... You can take n iterations to get to a palindrome and prove it's a non-lychrel number, but if you want to determine it's a lychrel number you'll need to take all the possible iterations, and that's an infinite number of iterations. Sorry man great try !

---

