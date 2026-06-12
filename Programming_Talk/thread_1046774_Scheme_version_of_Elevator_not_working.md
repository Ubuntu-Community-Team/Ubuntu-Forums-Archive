---
title: "Scheme version of Elevator not working"
date: 2009-01-21
forum: Programming Talk
---

### Post by Mr.Macdonald on 2009-01-21
I tried to solve the challege in Scheme, but I cant get it to work.

The code compiles ok, but the internal functions don't do what I want them to?

```
(define (xor a b)
  (and (or a b)
       (not (and a b))))

(define (sort l)
  (cond ((< (length l) 1) l)
	(else (let ((pnt (car l)))
		(define (split l l0 l1)
		  (cond ((null? l) (append (sort l0)
					   (sort l1)))
			((< (car l) pnt) (split (cdr l)
						(cons (car l) l0)
						l1))
			((> (car l) pnt) (split (cdr l)
						l0
						(cons (car l) l1)))
			(else (append (list (car l))
				      (split (cdr l) l0 l1)))))
		(split (reverse l) '() '())))))
		

(define (mk-elevator)
  (let ((ups '())
	(downs '())
	(cur 0))
    (define (add flr)
      (if (< cur flr)
	  (set! ups (sort (cons flr ups)))
	  (set! downs (reverse (sort (cons flr downs))))))
    (define (more)
      (not (xor (null? ups)
	       (null? downs))))
    (define (move)
      (cond ((not (more)) 'Done)
	    ((and (<= (length ups)
		     (length downs))
		  (not (zero? (length ups))))
	     (set! cur (car ups))
	     (print cur)
	     (set! ups (cdr ups)))
	    ((and (> (length ups)
		     (length downs))
		  (not (zero? (length downs))))
	     (set! cur (car downs))
	     (print cur)
	     (set! downs (cdr downs)))
	    (else 'Done)))
    (define (dispatch fname)
      (cond ((equal? fname 'add) add)
	    ((equal? fname 'more) more)
	    ((equal? fname 'move) move)))
    dispatch))

(define (add-flr ele flr)
  ((ele 'add) flr))

(define (move-ele ele)
  ((ele 'move)))

(define (more-ele ele)
  ((ele 'more)))

(define (fin-ele ele)
  (cond ((not (more-ele ele)) 'Done)
	(else (move-ele ele)
	      (fin-ele ele))))
```

I was hoping I could use like so,
```

(define ele1 (mk-elevator))
> (add-flr ele1 1)
> (add-flr ele1 4)
> (add-flr ele1 6)
> (add-flr ele1 2)
> (fin-ele ele1)
1
2
4
6

```

I know it doesn't follow the challege rules.
And don't completely change it, I want to learn

---

### Post by Mr.Macdonald on 2009-01-21
I know someone uses Scheme

---

### Post by Mr.Macdonald on 2009-01-22
Where are the Schemers?

If you need commenting tell me, but this is an attempt at object oriented

EDIT: I fixed one problem, (more) should be (not (and (null? ups) (null? downs)))

---

### Post by WitchCraft on 2009-01-22
> **Mr.Macdonald said:**
> Where are the Schemers?

If you need commenting tell me, but this is an attempt at object oriented

What's scheme? It looks like LISP.

---

### Post by Tony Flury on 2009-01-22
> **Mr.Macdonald said:**
> Where are the Schemers?

If you need commenting tell me, but this is an attempt at object oriented

OOP and comments are not contradictory - an appropriate level of comments is a good idea in what ever language and whatever pattern or style you are using.

WitchCraft : I think Scheme is a dialect of Lisp - isn't it ? 

As for the actual problem, Mr Macdonald I have no problem, to be honest Lisp just looks like line noise to me (maybe not as bad as perl but i have no idea what any of it means.

---

### Post by WitchCraft on 2009-01-22
> **Tony Flury said:**
> OOP and comments are not contradictory - an appropriate level of comments is a good idea in what ever language and whatever pattern or style you are using.

WitchCraft : I think Scheme is a dialect of Lisp - isn't it ? 

As for the actual problem, Mr Macdonald I have no problem, to be honest Lisp just looks like line noise to me (maybe not as bad as perl but i have no idea what any of it means.

wikipedia:
**Scheme** is a [multi-paradigm programming language]("http://en.wikipedia.org/wiki/Multi-paradigm_programming_language"). It is one of the two main [dialects]("http://en.wikipedia.org/wiki/Programming_language_dialect") of [Lisp]("http://en.wikipedia.org/wiki/Lisp_programming_language") and supports a number of programming paradigms but is best known for its support of [functional programming]("http://en.wikipedia.org/wiki/Functional_programming"). It was developed by [Guy L. Steele]("http://en.wikipedia.org/wiki/Guy_L._Steele") and [Gerald Jay Sussman]("http://en.wikipedia.org/wiki/Gerald_Jay_Sussman") in the 1970s. Scheme was introduced to the academic world via a series of papers now referred to as Sussman and Steele's [Lambda Papers]("http://en.wikipedia.org/wiki/Lambda_Papers"). 


How do I compile scheme programs ?
I'd like to try.

---

### Post by nvteighen on 2009-01-22
Here's a Schemer to the rescue! :D

Ok, first and most important: what implementation are you using?

Anyway, MIT/GNU Scheme is yielding these results. To make this work, I had to redefine "print" to "display".

```

1 ]=> 
;Loading "ele.scm"... done
;Value: fin-ele

1 ]=> (define ele1 (mk-elevator))

;Value: ele1

1 ]=> (add-flr ele1 1)

;Value: ()

1 ]=> (add-flr ele1 4)

;Value 11: (1)

1 ]=> (add-flr ele1 6)

;Value 12: (4 1)

1 ]=> (add-flr ele1 2)

;Value 14: (6 4 1)

1 ]=> (fin-ele ele1)

;Value: done

```

I have no clue why the last one is just printing "done"... But I fear an implementation-mismatch here...

There's something definitely wrong on how it is storing the data. I see you resort to imperative programming, and from my experience, Scheme gets really messy when you use set! and such.

What it seems from your code is that you want something that sorts stuff in "real time". Well, actually, an elevator is just that, so we're fine if the sorting function is fine. 

Let's see:
```

1 ]=> 
;Loading "ele.scm"... done
;Value: fin-ele

1 ]=> (sort '(1 2 3 4))

;Value 11: (1 2 3 4)

1 ]=> (sort '(2 3 1))

;Value 12: (2 1 3)

1 ]=> (sort '(2 4 5 1))

;Value 13: (2 1 4 5)

```

To me, it seems perfect. And there you have: a pure-functional elevator!! Understand it: in Scheme you think in terms of really high abstraction... If you look at my sig, you'll find a card game in Scheme where players are implemented just as a list, for example.

To introduce "real-time sorting", you have to introduce state (set!). I think you can simplify the whole thing a lot if you think it this way: whatever that determines where each floor has to be placed is the sorting function, so having an ups/downs abstraction in the elevator object is to me useless. Just make it an input taker, make it re-sort after each input and then save that new state.

---

### Post by Mr.Macdonald on 2009-01-22
You can't compile to machine code, its interpreted and way too dynamic

---

### Post by CptPicard on 2009-01-22
> **nvteighen said:**
> Understand it: in Scheme you think in terms of really high abstraction... If you look at my sig, you'll find a card game in Scheme where players are implemented just as a list, for example.

Sssshh!!  That solution doesn't even have *pointers* in it! How could that solution possibly be worth anything as it's probably orders of magnitude slower than one written in assembler?? I find it hard to believe that anyone who implemented that could actually understand how an elevator actually works.

And besides, the more unclear and full of machine-specific technical details a solution is, the more leet and Real Programming (tm) it is! You should know this already...

> **Mr.Macdonald said:**
> You can't compile to machine code, its interpreted and way too dynamic

Actually, scheme can do bytecode, and there is even a native code compiler with a little bit of type hint information added to the language. And of course Common Lisp implementations such as SBCL are full compilers that compile to native (they do have the runtime library for REPL, GC support etc but that's slightly different)...

---

### Post by Mr.Macdonald on 2009-01-22
Heres the updated version that works, (sorting doesn't for what ever reason)

```
(define (xor a b)
  (and (or a b)
       (not (and a b))))

(define (sort l)
  (cond ((< (length l) 1) l)
	(else (let ((pnt (car l)))
		(define (split l l0 l1)
		  (cond ((null? l) (append (sort l0)
					   (sort l1)))
			((< (car l) pnt) (split (cdr l)
						(cons (car l) l0)
						l1))
			((> (car l) pnt) (split (cdr l)
						l0
						(cons (car l) l1)))
			(else (append (list (car l))
				      (split (cdr l) l0 l1)))))
		(split (reverse l) '() '())))))
		

(define (mk-elevator)
  (let ((ups '())
	(downs '())
	(cur 0))
    (define (add flr)
      (if (< cur flr)
	  (set! ups (sort (cons flr ups)))
	  (set! downs (reverse (sort (cons flr downs))))))
    (define (more)
      (not (and (null? ups)
		(null? downs))))
    (define (outs)
      (print ups)
      (print downs)
      cur)
    (define (move)
      (cond ((not (more)) 'Done)
	    ((and (<= (length ups)
		     (length downs))
		  (not (zero? (length ups))))
	     (set! cur (car ups))
	     (print cur)
	     (set! ups (cdr ups)))
	    ((and (> (length ups)
		     (length downs))
		  (not (zero? (length downs))))
	     (set! cur (car downs))
	     (print cur)
	     (set! downs (cdr downs)))
	    ((zero? (length ups))
	     (set! cur (car downs))
	     (print cur)
	     (set! downs (cdr downs)))
	    ((zero? (length downs))
	     (set! cur (car ups))
	     (print cur)
	     (set! ups (cdr ups)))
	    (else 'Fin)))
    (define (dispatch fname)
      (cond ((equal? fname 'add) add)
	    ((equal? fname 'more) more)
	    ((equal? fname 'move) move)
	    ((equal? fname 'outs) outs)))
    dispatch))

(define (add-flr ele flr)
  ((ele 'add) flr))

(define (move-ele ele)
  ((ele 'move)))

(define (more-ele ele)
  ((ele 'more)))

(define (fin-ele ele)
  (cond ((not (more-ele ele)) 'Done)
	(else (move-ele ele)
	      (fin-ele ele))))
```

I use SCM, but do I have a concept wrong. I don't understand whats imperative, the let statement is needed as far as I can see.

---

### Post by CptPicard on 2009-01-22
> **Mr.Macdonald said:**
> 
I use SCM, but do I have a concept wrong. I don't understand whats imperative, the let statement is needed as far as I can see.

Your code turns from pure-functional into something that has side-effects (and therefore, you move towards imperative programming) when you use set!. That is something that rewrites a binding -- in pure-functional programming, bindings *never change* once they have been assigned once.

It may feel a bit counter-intuitive to get rid of something as seemingly fundamental as the concept of "variable" (in pure-functional programs, there are no "variables" -- they never "vary")... but you'll get the hang of it ;)

---

### Post by Wybiral on 2009-01-22
Not actually helpful to the real problem, but I'm going to highly recommend against using variable names like 'l' as it tends to look like '1' (same rule with 'O' and '0'). It makes your sort function require more effort to read.

In fact, IMO, one character variable names really only make sense to me when it's for something like an iterator or for simple F(x) lambdas/function.

---

### Post by Mr.Macdonald on 2009-01-22
> It may feel a bit counter-intuitive to get rid of something as seemingly fundamental as the concept of "variable" (in pure-functional programs, there are no "variables" -- they never "vary")... but you'll get the hang of it 

I understand that but is this problem solveable without being using set!. My understanding of the power of Lisp was that it has very unique variable scopes. For example:

```
(define (ex a b)
	(let ((x (* a b))) 
		(lambda (y)
			(lambda (g) (+ g (* y x))))))
(define func ((ex 3 2) 5))
```

Although useless, it demonstrates a small bit of the scopes.
func is now a function that has four variables inside yet you only ever pass in one.

Some problems are not solvable with purely functional, like a nice iterator or a random number generator.


I learned this from the videos at [[COLOR="Blue"]_MIT_[/COLOR]]("http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/")

---

### Post by CptPicard on 2009-01-22
> **Mr.Macdonald said:**
> I understand that but is this problem solveable without being using set!. My understanding of the power of Lisp was that it has very unique variable scopes. For example:

Well, you are correct that lambdas and their closures are a very strong feature, but these are different things from side-effects using set!.. I have not taken a good look at your code so I can't really answer the specific question, but set! "reassigns" whatever is in lexical scope for that symbol (it can be inside a lambda's closure), producing a side-effect.

> 
Some problems are not solvable with purely functional, like a nice iterator or a random number generator.

It's an interesting claim because it's wrong. :) Pure-functional programming is Turing-complete. 

See here how you can do a random number generator using monads in Haskell without resorting to state:

[http://en.wikibooks.org/wiki/Programming:Haskell_monads](http://en.wikibooks.org/wiki/Programming:Haskell_monads)

Now, those things may be "difficult", and an "iterator" can just be somewhat meaningless in pure-functional programming because it is by definition rather stateful... but, I can think of ways of approaching iteration using continuations (call/cc) which are perfectly compatible with the pure-functional model.

---

### Post by Mr.Macdonald on 2009-01-22
There has to be somthing that requires a set! call!
(I do like functional programming but I also feel that set! does simplify alot of things)


Because functional programming has no "time", projects with multiple interfaces wouldn't work. You wouldn't know who did what first.
And without time, every time you start a random number generator up, you would get the same sequence streaming out.

Now these could be possible, but very hard and not worth it.

EDIT: I just noticed that the "thanking" seemed to disappear

---

### Post by CptPicard on 2009-01-22
> **Mr.Macdonald said:**
> There has to be somthing that requires a set! call!

No, from theoretical perspective, there really is not. Lambda calculus itself has nothing but function definition and application, and what you're able to "define" is very minimal (in particular there is no "reassignment" for variables). However, you are on a right track from a practical perspective...

> 
(I do like functional programming but I also feel that set! does simplify alot of things)

Sure. That's why I prefer Lisp over something like Haskell, because I can have mutable state when I want it. However, being able to modularize your code (keeping side effects inside a "black box") and being aware of pure-functional design tactics is beneficial in itself... that way you can use side-effects when you know you want and need them.

> 
Because functional programming has no "time", projects with multiple interfaces wouldn't work. You wouldn't know who did what first.

Well, who said your pure-functional program has to actually interact with anything, as long as it exists in perfect abstract harmony with the universe inside the computer.. ;)

"Time" is often handled just as some sort of infinite list of different system states (note: the state does not change, there is just always a new state).

But you're right that for example in Haskell I/O was a huge problem before they came up with the Monad concept... monads allow you to stay within the model and "chain" stuff that there is an order to things... if I have understood the concept correctly.

> 
Now these could be possible, but very hard and not worth it.

So, as I said, they're possible, but they are the hard part indeed. They are worth it because if the compiler is able to trust that there is no mutable state anywhere in the system, all sorts of powerful optimizations become available, not to mention that stuff like parallelism is all of a sudden all that much easier... (because there is no mutable state, there is no shared mutable state, so you can just forget about need for synchronization etc)

---

### Post by Mr.Macdonald on 2009-01-22
Another Point is that a true function follows this:
```
For every f(x) and value a,
f(a) = c
And
f(a) will never equal d such that
d != c

```

Also
> "Time" is often handled just as some sort of infinite list of different system states (note: the state does not change, there is just always a new state).

This infinite list will always be the same unless the user always supplys one (its and argument)

this means that it one where to make a random number generator and you supply the same arguments to the environment and to the function. Then you get the same results.


This isn't random, because random numbers aren't functional.
```
f(a) = d
f(a) = c
And d and c don't have to be equal
```



Now this doesn't make functional programming languages bad, because everything in nature can be calculated (except quantum, but strings may soon fix that) nothing is random.

---

### Post by CptPicard on 2009-01-22
> **Mr.Macdonald said:**
> Another Point is that a true function follows this:

And this is why pure-functional languages have full substitutability, which is very powerful support for all kinds of optimizations. Mind you, the reason why using "set!" is said to produce side-effects is exactly this -- if there is no set! in the code anywhere, then the condition holds, otherwise calls to functions do not always result in the same result for the same parameter.

> 
this means that it one where to make a random number generator and you supply the same arguments to the environment and to the function. Then you get the same results.

Pseudo-random-number generators already produce the same results with the same random seed. :)

You can always consider the entire environment for the program to be input, so the infinite-stream model doesn't break pure-functionality. Actually Haskell used to do I/O as "infinite lists", but the monad style of doing things prevailed later on.

---

### Post by nvteighen on 2009-01-23
> **CptPicard said:**
> Sssshh!!  That solution doesn't even have *pointers* in it! How could that solution possibly be worth anything as it's probably orders of magnitude slower than one written in assembler?? I find it hard to believe that anyone who implemented that could actually understand how an elevator actually works.

And besides, the more unclear and full of machine-specific technical details a solution is, the more leet and Real Programming (tm) it is! You should know this already...


:D

Ok, back to topic and to OP:
Your second solution is too complex. It works, ok, but it's written in such a way that it wouldn't matter whether it's written in Scheme, Java, C or ASM.

What you want is just to know the order of how floors will be visited, so coding a sorting function is all you need. I know it sounds weird, but Scheme (and Lisp) works that way.

Look at this (again, MIT/GNU Scheme):
```

;; Dealing system
(define (make-dealer deck cards-num player-list)

  ;; List auxiliary searcher
  (define (list-get-index lst query pred?)
    (let loop ((i 0)
               (lookup lst))
      (cond ((null? lookup) #f)
            ((pred? (car lookup) query) i)
            (else
             (loop (+ i 1)
                   (cdr lookup))))))

  ;; Deals stream generator
  (define (make-deals-stream deck n)
    (let ((card (list-ref deck 
                          (random (length deck)))))
      (cond ((= n 0) the-null-card)
            ((null? deck) the-null-card)
            (else
             (cons-stream card
                          (make-deals-stream (delete card 
                                                     deck)
                                             (- n 1)))))))

  ;; make-dealer body
  (let ((deals-stream (make-deals-stream deck 
                                         (* cards-num 
                                            (length player-list)))))
    (lambda (player)
      (let ((switch (list-get-index player-list 
                                    player 
                                    eq?)))
        (let loop ((i 0)
                   (hand '()))
          (if (= (length hand) cards-num)
              hand
              (loop (+ i 1)
                    (cons (stream-ref deals-stream
                                      (+ (* switch
                                            cards-num)
                                         i))
                          hand))))))))

(define (deal-next dealer player)
  (dealer player))

```

This is maybe the most clever piece of Scheme I've written :) It's a card dealing system with no state except for the call to random. Why? Because we don't need it. You may think of dealing as taking cards succesively, which would need state, or as I did: take the necessary amount of cards all together at the same time and then, according to their position deal then to the corresponding player. This needs a stream, of course: you can't deal the same card twice, so the deck changes... but it changes in one single predictable way, so we have a function for it that's delayed.

What I want you to look is that sometimes you think in terms of objects rather than in functions. In reality, a dealer and a player are the very same object... and in C or C++, I'd have implemented it that way. But as functions, they're different: one deals and the other plays. If you start looking at stuff as functions, you'll reach the point where functional programming will make a lot of sense... even more than imperative. Of course, your code will look a lot more esoteric, but really clever.

So, what does an elevator with respect to the input it takes? Well, it just sorts it according to some function. You don't need even to print the numbers... you just return a list of the ordered floors and that's it. What's the function? Well, that's another story, but as the elevator is expected to behaive the same way given the same parameters, then, it's surely a pure-functional solution.

---

### Post by Mr.Macdonald on 2009-01-23
with the elevator you can't just take in a list, because in life and elevator can move, take input, take more input, move again, etc. These could happen in any order, at any _TIME_. thus requiring a state. Your sorting idea could help the elevator pick which floor to goto next, but you must be able to add floors "at runtime".

The functional style is far simpler and conceptual, but wrong because there isn't "time".

On anther not what kind of optimizations are available. Is it memorizing the outputs for certian inputs (theres some name for it).

---

### Post by nvteighen on 2009-01-23
> **Mr.Macdonald said:**
> with the elevator you can't just take in a list, because in life and elevator can move, take input, take more input, move again, etc. These could happen in any order, at any _TIME_. thus requiring a state. Your sorting idea could help the elevator pick which floor to goto next, but you must be able to add floors "at runtime".

The functional style is far simpler and conceptual, but wrong because there isn't "time".

On anther not what kind of optimizations are available. Is it memorizing the outputs for certian inputs (theres some name for it).
Ok, yes. But it's not the only possible way to see it. Conceptually, by passing a list and using a pure-functional approach, you're doing very much the same: passing a given state of the elevator and see what happens in that case.

---

### Post by Mr.Macdonald on 2009-01-23
Passing a list is essentially predicting the future, what if the first command was to goto floor 2, then goto floor 1. If I pass a list '(2 1). then sort will stay at one and the goto 2. not what actually happens

---

### Post by CptPicard on 2009-01-23
> **Mr.Macdonald said:**
> Passing a list is essentially predicting the future, what if the first command was to goto floor 2, then goto floor 1. If I pass a list '(2 1). then sort will stay at one and the goto 2. not what actually happens

And this is why you do essentially understand what some of the central problems in pure-functionality are, but still for some reason get stuck on them. ;)

Yes, in a pure-functional model you sometimes want to assume you can predict the future. Theoretically, it makes no difference, and even in practice, these sorts of "practical issues" can be handled pretty nicely. Either you make use of an endless stream (that certainly has underlying state, but the big picture can still be viewed as stateless as everything is "done") or you isolate your side-effects in something like a monad...

It's hard to point out where exactly you're wrong because mostly you're right... it's just that it's not such a big deal as you may think.

---

