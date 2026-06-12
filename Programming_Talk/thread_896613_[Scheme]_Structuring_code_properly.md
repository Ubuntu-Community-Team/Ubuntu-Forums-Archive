---
title: "[Scheme] Structuring code properly"
date: 2008-08-21
forum: Programming Talk
---

### Post by nvteighen on 2008-08-21
Hi,
In my journey through Scheme, I've hit against a little rock I'd like to ask you about.

Look at this code:
```

(define factorial
  (lambda (x)
    (if (= x 0) 1
        (* x (factorial (- x 1))))))

(define main
  (lambda (x)
	(if (number? x)
		(factorial x)
		'Error!)))

(display (main (read))) ; Here any client code should be valid.

```

Is the use of (main) a Scheme-ish way to do things or is rather a C-ism? I want to separate the (display) from any data processing such as parsing user's input and, of course, of (factorial)... So that any external code could be able to use the functionality of this module. Or should I condense (main) and (factorial) to a single "function"?

In other words, is there such a concept as "structured functional programming" and how would you implement it Scheme (or any Lisp)?

---

### Post by Wybiral on 2008-08-21
That looks rational to me. My knowledge of scheme comes from [SICP]("http://mitpress.mit.edu/sicp/") (the Authority), where they basically break everything into smaller, reusable functions. They even advocate writing code as though you had those smaller components (even if you hadn't written them yet).

---

### Post by nvteighen on 2008-08-21
> **Wybiral said:**
> That looks rational to me. My knowledge of scheme comes from [SICP]("http://mitpress.mit.edu/sicp/") (the Authority), where they basically break everything into smaller, reusable functions. They even advocate writing code as though you had those smaller components (even if you hadn't written them yet).

It's nice to know I comply with the Authority. Thanks!

(And yes, SICP is great... better than all Scheme "tutorials")

---

### Post by CptPicard on 2008-08-21
IMO you're just being complicated... no need for "main", you just run your program by calling whatever evaluates to the desired result :)

---

### Post by Jessehk on 2008-08-21
I'm really not sure if you care about this at all (since the actual factorial code might have just been a quick example to illustrate your point regarding structuring code), but you'd almost always write the tail-recursive version instead. 

You'll never reach a stack recursion limit and performance will increase dramatically.
```

(define factorial
  (lambda (n)
    (define loop
      (lambda (accum i)
        (if (> i n)
            accum
            (loop (* accum i) (+ i 1)))))
    (loop 1 1)))

; Runs seemingly instantaneously
(factorial 10000)

```

---

### Post by nvteighen on 2008-08-21
> **CptPicard said:**
> IMO you're just being complicated... no need for "main", you just run your program by calling whatever evaluates to the desired result :)

What I meant with "main" was that I have the "core" function that performs the factorial and then one that evaluates the user's input. But I think this will be a bit more of your taste?

```

(define factorial
  (lambda (x)
    (if (not (number? x))
		#f
		(let loop ((accum 1)
			   (i 0))
		  (if (> i x)
			  accum
			  (loop (* accum (+ i 1)) (+ i 1)))))))

(display (factorial (read)))

```

> **Jessehk said:**
> I'm really not sure if you care about this at all (since the actual factorial code might have just been a quick example to illustrate your point regarding structuring code), but you'd almost always write the tail-recursive version instead. 

You'll never reach a stack recursion limit and performance will increase dramatically.


Actually, it was my first Scheme exercise, before I understood what tail recursion is... and the first version was pretty imperative, using (set!) instead of (let). Thanks!

But, any reason why you don't use named let?

---

