---
title: "Lychrel Number -- C# -- one of my little pieces of code"
date: 2008-01-27
forum: Programming Talk
---

### Post by cprofitt on 2008-01-27
I am interested if anyone else has done tests for Lychrel numbers...
 
[php]
using System;
using System.Collections.Generic;
using System.Collections;
using System.Text;
using java.math;
 
        private class lychrel
        {
            private bool _palindrome = false;
            private bool _lychrel = true;
            private int _iterations = 0;
            private BigInteger _number;
 
            public lychrel(BigInteger originalNumber)
            {
                _number = originalNumber;
                computeLychrel();
            }
 
            public bool Palindrome
            {
                get
                {
                    return _palindrome;
                }
            }
 
            public bool Lychrel
            {
                get
                {
                    return _lychrel;
                }
            }
 
            public int Iterations
            {
                get
                {
                    return _iterations;
                }
            }
 
            private void computeLychrel()
            {
                // test for palindrome
                string original = _number.ToString();
                string reverse = sReverse(_number.ToString());
                BigInteger bi = new BigInteger(reverse);
                if (original == reverse)
                {
                    _palindrome = true;
                    _lychrel = false;
                }
                else
                {
                    if (_iterations < 400)
                    {
                        // perform 196 algorythm
                        _number = _number.add(bi);
                        _iterations += 1;
                        computeLychrel();
                    }
                }
            }
 
            private string sReverse(string test)
            {
                ArrayList al = new ArrayList();
                foreach(char c in test)
                {
                    al.Add(c);
                }
 
                al.Reverse();
 
                string r = "";
 
                foreach (char c in al)
                {
                    r += c;
                }
 
                return r;
            }
        }        
[/php]
C#
 
I have it stop the loop at 400 right now to avoid it running for ever and ever...
 
anyone ever play games with numbers like this?
 
My goal is to re-write this in Python in the next few weeks...
 
I also have a stat class... Median, Skew, etc... written in C# if anyone needs something like that.

---

### Post by seventhc on 2008-01-28
You should do it for 196 until it finally becomes a palindromic number....if it ever does. ;)

---

### Post by LaRoza on 2008-01-28
> **seventhc said:**
> You should do it for 196 until it finally becomes a palindromic number....if it ever does. ;)

Hey! Don't give away the ending....

---

### Post by lnostdal on 2008-01-28
i did a try .. mh, i'm quite rusty tho :)

[http://paste.lisp.org/display/54924](http://paste.lisp.org/display/54924)


[php]
#| From wikipedia:
A Lychrel number is a natural number which cannot form a palindrome through the iterative process of repeatedly reversing its base 10 digits and adding the resulting numbers.
|#


(defmacro for ((var initial-value pred &optional update-value) &body body)
  "Similar to the `for' keyword in other languages."
  (if update-value
      `(do ((,var ,initial-value ,update-value)) ((not ,pred))
         ,@body)
      `(do ((,var, initial-value)) ((not ,pred))
         ,@body)))


(defparameter *max-number-of-tries* 2000
  "How many times to try the reverse and add process.")


(defun reverse-of (number)
  "Return a number based on the reverse sequence of digits in `number'."
  (parse-integer (nreverse (princ-to-string number))))


(defun palindrome-p (number)
  "Returns `number' if `number' is a palindrome. NIL otherwise."
  (if (= (reverse-of number) number)
      number
      nil))


(defun reverse-and-add-of (number)
  "Returns the sum of `number' and the number designated by reversing the
 digits in `number'."
  (+ number (reverse-of number)))


(defun reverse-and-add-process (number &optional (max-tries *max-number-of-tries*))
  "Returns the following values:
* T or NIL, based on whether the algorithm thinks `number' is a lychrel number.
* `current-number', 
* `steps', the number of reverse and add operations executed.
"
  (let ((step 1) (current-number number))
    (loop
       (setf current-number (reverse-and-add-of current-number))
       (if (palindrome-p current-number)
           ;; Not a lychrel number, for sure.
           (return (values nil current-number step))
           (when (= (incf step) max-tries)
             ;; Might be a lychrel number; we give up.
             (return (values t current-number step)))))))


(defun lychrel (number)
  (multiple-value-bind (lychrel-p resulting-number steps)
      (reverse-and-add-process number)
    (if lychrel-p
        (format t "After ~A steps, ~A is still not a palindrome (it's a lychrel candidate in this test).~%"
                steps number)
        (format t "After ~A steps, ~A became the palindrome ~A and is thus not a lychrel number.~%"
                steps number resulting-number))))




#|
Some tests:

cl-user> (lychrel 56)
After 1 steps, 56 became the palindrome 121 and is thus not a lychrel number.
nil
cl-user> (lychrel 57)
After 2 steps, 57 became the palindrome 363 and is thus not a lychrel number.
nil
cl-user> (lychrel 59)
After 3 steps, 59 became the palindrome 1111 and is thus not a lychrel number.
nil
cl-user> (lychrel 89)
After 24 steps, 89 became the palindrome 8813200023188 and is thus not a lychrel number.
nil
cl-user> (lychrel 10911)
After 55 steps, 10911 became the palindrome 4668731596684224866951378664 and is thus not a lychrel number.
nil
cl-user> (lychrel 1186060307891929990)
After 261 steps, 1186060307891929990 became the palindrome 44562665878976437622437848976653870388884783662598425855963436955852489526638748888307835667984873422673467987856626544 and is thus not a lychrel number.
nil
cl-user> (lychrel 196)
After 2000 steps, 196 is still not a palindrome (it's a lychrel candidate in this test).
nil
cl-user> (for (i 10 (< i 100) (incf i))
           (lychrel i))
After 1 steps, 10 became the palindrome 11 and is thus not a lychrel number.
After 1 steps, 11 became the palindrome 22 and is thus not a lychrel number.
After 1 steps, 12 became the palindrome 33 and is thus not a lychrel number.
After 1 steps, 13 became the palindrome 44 and is thus not a lychrel number.
After 1 steps, 14 became the palindrome 55 and is thus not a lychrel number.
After 1 steps, 15 became the palindrome 66 and is thus not a lychrel number.
After 1 steps, 16 became the palindrome 77 and is thus not a lychrel number.
After 1 steps, 17 became the palindrome 88 and is thus not a lychrel number.
After 1 steps, 18 became the palindrome 99 and is thus not a lychrel number.
After 2 steps, 19 became the palindrome 121 and is thus not a lychrel number.
After 1 steps, 20 became the palindrome 22 and is thus not a lychrel number.
After 1 steps, 21 became the palindrome 33 and is thus not a lychrel number.
After 1 steps, 22 became the palindrome 44 and is thus not a lychrel number.
After 1 steps, 23 became the palindrome 55 and is thus not a lychrel number.
After 1 steps, 24 became the palindrome 66 and is thus not a lychrel number.
After 1 steps, 25 became the palindrome 77 and is thus not a lychrel number.
After 1 steps, 26 became the palindrome 88 and is thus not a lychrel number.
After 1 steps, 27 became the palindrome 99 and is thus not a lychrel number.
After 2 steps, 28 became the palindrome 121 and is thus not a lychrel number.
After 1 steps, 29 became the palindrome 121 and is thus not a lychrel number.
After 1 steps, 30 became the palindrome 33 and is thus not a lychrel number.
After 1 steps, 31 became the palindrome 44 and is thus not a lychrel number.
After 1 steps, 32 became the palindrome 55 and is thus not a lychrel number.
After 1 steps, 33 became the palindrome 66 and is thus not a lychrel number.
After 1 steps, 34 became the palindrome 77 and is thus not a lychrel number.
After 1 steps, 35 became the palindrome 88 and is thus not a lychrel number.
After 1 steps, 36 became the palindrome 99 and is thus not a lychrel number.
After 2 steps, 37 became the palindrome 121 and is thus not a lychrel number.
After 1 steps, 38 became the palindrome 121 and is thus not a lychrel number.
After 2 steps, 39 became the palindrome 363 and is thus not a lychrel number.
After 1 steps, 40 became the palindrome 44 and is thus not a lychrel number.
After 1 steps, 41 became the palindrome 55 and is thus not a lychrel number.
After 1 steps, 42 became the palindrome 66 and is thus not a lychrel number.
After 1 steps, 43 became the palindrome 77 and is thus not a lychrel number.
After 1 steps, 44 became the palindrome 88 and is thus not a lychrel number.
After 1 steps, 45 became the palindrome 99 and is thus not a lychrel number.
After 2 steps, 46 became the palindrome 121 and is thus not a lychrel number.
After 1 steps, 47 became the palindrome 121 and is thus not a lychrel number.
After 2 steps, 48 became the palindrome 363 and is thus not a lychrel number.
After 2 steps, 49 became the palindrome 484 and is thus not a lychrel number.
After 1 steps, 50 became the palindrome 55 and is thus not a lychrel number.
After 1 steps, 51 became the palindrome 66 and is thus not a lychrel number.
After 1 steps, 52 became the palindrome 77 and is thus not a lychrel number.
After 1 steps, 53 became the palindrome 88 and is thus not a lychrel number.
After 1 steps, 54 became the palindrome 99 and is thus not a lychrel number.
After 2 steps, 55 became the palindrome 121 and is thus not a lychrel number.
After 1 steps, 56 became the palindrome 121 and is thus not a lychrel number.
After 2 steps, 57 became the palindrome 363 and is thus not a lychrel number.
After 2 steps, 58 became the palindrome 484 and is thus not a lychrel number.
After 3 steps, 59 became the palindrome 1111 and is thus not a lychrel number.
After 1 steps, 60 became the palindrome 66 and is thus not a lychrel number.
After 1 steps, 61 became the palindrome 77 and is thus not a lychrel number.
After 1 steps, 62 became the palindrome 88 and is thus not a lychrel number.
After 1 steps, 63 became the palindrome 99 and is thus not a lychrel number.
After 2 steps, 64 became the palindrome 121 and is thus not a lychrel number.
After 1 steps, 65 became the palindrome 121 and is thus not a lychrel number.
After 2 steps, 66 became the palindrome 363 and is thus not a lychrel number.
After 2 steps, 67 became the palindrome 484 and is thus not a lychrel number.
After 3 steps, 68 became the palindrome 1111 and is thus not a lychrel number.
After 4 steps, 69 became the palindrome 4884 and is thus not a lychrel number.
After 1 steps, 70 became the palindrome 77 and is thus not a lychrel number.
After 1 steps, 71 became the palindrome 88 and is thus not a lychrel number.
After 1 steps, 72 became the palindrome 99 and is thus not a lychrel number.
After 2 steps, 73 became the palindrome 121 and is thus not a lychrel number.
After 1 steps, 74 became the palindrome 121 and is thus not a lychrel number.
After 2 steps, 75 became the palindrome 363 and is thus not a lychrel number.
After 2 steps, 76 became the palindrome 484 and is thus not a lychrel number.
After 3 steps, 77 became the palindrome 1111 and is thus not a lychrel number.
After 4 steps, 78 became the palindrome 4884 and is thus not a lychrel number.
After 6 steps, 79 became the palindrome 44044 and is thus not a lychrel number.
After 1 steps, 80 became the palindrome 88 and is thus not a lychrel number.
After 1 steps, 81 became the palindrome 99 and is thus not a lychrel number.
After 2 steps, 82 became the palindrome 121 and is thus not a lychrel number.
After 1 steps, 83 became the palindrome 121 and is thus not a lychrel number.
After 2 steps, 84 became the palindrome 363 and is thus not a lychrel number.
After 2 steps, 85 became the palindrome 484 and is thus not a lychrel number.
After 3 steps, 86 became the palindrome 1111 and is thus not a lychrel number.
After 4 steps, 87 became the palindrome 4884 and is thus not a lychrel number.
After 6 steps, 88 became the palindrome 44044 and is thus not a lychrel number.
After 24 steps, 89 became the palindrome 8813200023188 and is thus not a lychrel number.
After 1 steps, 90 became the palindrome 99 and is thus not a lychrel number.
After 2 steps, 91 became the palindrome 121 and is thus not a lychrel number.
After 1 steps, 92 became the palindrome 121 and is thus not a lychrel number.
After 2 steps, 93 became the palindrome 363 and is thus not a lychrel number.
After 2 steps, 94 became the palindrome 484 and is thus not a lychrel number.
After 3 steps, 95 became the palindrome 1111 and is thus not a lychrel number.
After 4 steps, 96 became the palindrome 4884 and is thus not a lychrel number.
After 6 steps, 97 became the palindrome 44044 and is thus not a lychrel number.
After 24 steps, 98 became the palindrome 8813200023188 and is thus not a lychrel number.
After 6 steps, 99 became the palindrome 79497 and is thus not a lychrel number.
nil
cl-user> 

|#
[/php]

---

### Post by seventhc on 2008-01-28
> **LaRoza said:**
> Hey! Don't give away the ending....
Did I ruin the mystery>>>???:-$

---

### Post by Wybiral on 2008-01-28
> **lnostdal said:**
>  ... 

Welcome back lnostdal, we needed some lisp know-how around here!

---

### Post by LaRoza on 2008-01-28
> **Wybiral said:**
> Welcome back lnostdal, we needed some lisp know-how around here!

Oh good :) We seemed to have been lacking in functional programmers on this forum. (That sounds insulting doesn't it)

---

### Post by cprofitt on 2008-01-28
> **seventhc said:**
> You should do it for 196 until it finally becomes a palindromic number....if it ever does. ;)

Hence the limit... 196 is just the first number... there are others.

---

### Post by cprofitt on 2008-01-28
[QUOTE=lnostdal;4221073]i did a try .. mh, i'm quite rusty tho :)

[http://paste.lisp.org/display/54924](http://paste.lisp.org/display/54924)


Lisp... I will have to take a look at that. I started with 'functional' languages I think.

---

