---
title: "help creating a simple word scramble program in LISP"
date: 2010-12-09
forum: Programming Talk
---

### Post by aaron4osu on 2010-12-09
I'm new to lisp and I'm trying to create a simple word scramble program, but am stuck on a few things. I want it to read each word of a text file and scramble all of the letters except the first and last letters. 
i'd figure there should be two methods; one to scramble a word and another to read in words of a text file and call the scramble method on each one. 

Here is what I have so far. 

for the scramble method I need help with the middle part. I was thinking something with the reverse function but not sure how to use it. 
```
 

(defun scramble (word) 
(if (< (length word) 4) 
word 
(append (list (first word)) ...need help here..... (last word)) 
) 
) 

``` 

then for the read in method I have this so far 

```
 
(defun readAndscramble(filename) 
(with-open-file (stream filename) 
(do ((char (read-char stream nil) (read-char stream nil)) 


``` 

any help would be greatly appreciated.

---

### Post by Arndt on 2010-12-09
> **aaron4osu said:**
> I'm new to lisp and I'm trying to create a simple word scramble program, but am stuck on a few things. I want it to read each word of a text file and scramble all of the letters except the first and last letters. 
i'd figure there should be two methods; one to scramble a word and another to read in words of a text file and call the scramble method on each one. 

Here is what I have so far. 

for the scramble method I need help with the middle part. I was thinking something with the reverse function but not sure how to use it. 
```
 

(defun scramble (word) 
(if (< (length word) 4) 
word 
(append (list (first word)) ...need help here..... (last word)) 
) 
) 

``` 

then for the read in method I have this so far 

```
 
(defun readAndscramble(filename) 
(with-open-file (stream filename) 
(do ((char (read-char stream nil) (read-char stream nil)) 


``` 

any help would be greatly appreciated.

If you indent your code, it becomes readable.

Why a capital A in "And" but no capital S in "scramble"? Personally, I like separation with hyphens better.

Think about how you want to scramble the words first. Once you know the algorithm, you can put it into Lisp. Will the scrambling be random, or deterministic?

---

### Post by saulgoode on 2010-12-09
Assuming you have a procedure to randomize a list, the following should work (I omitted the test for short words for the sake of clarity).
```
(defun scramble (word) 
  (concatenate 'string
               (subseq word 0 1) 
               (coerce (randomize-list (coerce (subseq word 
                                                       1 
                                                       (- (length word) 1) ) 
                                               'list ) ) 
                       'string ) 
               (subseq word (- (length word) 1) (length word)) ) )
```

Here is the randomize-list procedure I used (may not be optimal):
```
(defun randomize-list (list)
  (mapcar #'car
          (sort (mapcar (lambda (c) 
                                (cons c (random 1.0)) )
                        list)
                #'> :key #'cdr ) ) )
```

Here are some runs:

[INDENT]> (scramble "anticoagulent")
"ageatonniclut"
> (scramble "anticoagulent")
"ainlueatcgnot"
> (scramble "anticoagulent")
"augeinotncalt"
> (scramble "anticoagulent")
"aegcitnauolnt"[/INDENT]

I do not know enough about Lisp I/O to help with that (I am more familiar with the Scheme dialect).

---

### Post by aaron4osu on 2010-12-10
thanks saulgood.  
I'm almost there.
here is what I have now. i'm getting an error so something is not right.
thanks, aaron   

```
(defun scramble (word) 
      (concatenate 'string
       (subseq word 0 1) 
      (coerce (randomize-list (coerce (subseq word 
        1 (- (length word) 1) )  'list ) )  'string ) 
         (subseq word (- (length word) 1) (length word)) ) )
```

(```
defun randomize-list (list)  
  (mapcar #'car
          (sort (mapcar (lambda (c) 
                                (cons c (random 1.0)) )
                        list)
                #'> :key #'cdr ) ) )
```

```
; Reads a file of text and scrambles the words.
(defun read-and-scramble(filename) 
	; Read in words
	(with-open-file (stream filename)
    		(do ((char (read-char stream nil) (read-char stream nil))
		     (word nil)
		     )
        	    ((null char))
		
      	  (if (alpha-char-p char)
			(setq word (append word (list char)))
			(progn
			   (format t "~a" (coerce (scramble word) 'string))
			   (format t "~a" (coerce (list char) 'string))
			   (setq word nil)
			)))))
```

---

### Post by Arndt on 2010-12-10
> **aaron4osu said:**
> thanks saulgood.  
I'm almost there.
here is what I have now. i'm getting an error so something is not right.
thanks, aaron   

```
(defun scramble (word) 
      (concatenate 'string
       (subseq word 0 1) 
      (coerce (randomize-list (coerce (subseq word 
        1 (- (length word) 1) )  'list ) )  'string ) 
         (subseq word (- (length word) 1) (length word)) ) )
```

(```
defun randomize-list (list)  
  (mapcar #'car
          (sort (mapcar (lambda (c) 
                                (cons c (random 1.0)) )
                        list)
                #'> :key #'cdr ) ) )
```

```
; Reads a file of text and scrambles the words.
(defun read-and-scramble(filename) 
	; Read in words
	(with-open-file (stream filename)
    		(do ((char (read-char stream nil) (read-char stream nil))
		     (word nil)
		     )
        	    ((null char))
		
      	  (if (alpha-char-p char)
			(setq word (append word (list char)))
			(progn
			   (format t "~a" (coerce (scramble word) 'string))
			   (format t "~a" (coerce (list char) 'string))
			   (setq word nil)
			)))))
```

When do you get an error? In which function, for which input?

---

