---
title: "[LISP (Scheme)] Efficiency of My Program"
date: 2008-09-11
forum: Programming Talk
---

### Post by Sinkingships7 on 2008-09-11
This program works, as in it does what is specified in the comment. But it seems a little too verbose. I was wondering if there was a more syntactically efficient way to write it.

```
[color=#408080]*;Define a procedure that takes three numbers as arguments and returns the sum of the squares of the two larger numbers. *[/color]

([color=#008000]**define **[/color]([color=#0000FF]sum-of-larger-squares[/color] [color=#19177C]x[/color] [color=#19177C]y[/color] [color=#19177C]z[/color])
  ([color=#0000FF]cond[/color]
    (([color=#008000]**and **[/color]([color=#008000]> [/color][color=#19177C]x[/color] [color=#19177C]z[/color]) ([color=#008000]> [/color][color=#19177C]y[/color] [color=#19177C]z[/color]))
     ([color=#008000]+ [/color]([color=#008000]* [/color][color=#19177C]x[/color] [color=#19177C]x[/color]) ([color=#008000]* [/color][color=#19177C]y[/color] [color=#19177C]y[/color])))
    (([color=#008000]**and **[/color]([color=#008000]> [/color][color=#19177C]x[/color] [color=#19177C]y[/color]) ([color=#008000]> [/color][color=#19177C]z[/color] [color=#19177C]y[/color]))
     ([color=#008000]+ [/color]([color=#008000]* [/color][color=#19177C]x[/color] [color=#19177C]x[/color]) ([color=#008000]* [/color][color=#19177C]z[/color] [color=#19177C]z[/color])))
    (([color=#008000]**and **[/color]([color=#008000]> [/color][color=#19177C]z[/color] [color=#19177C]x[/color]) ([color=#008000]> [/color][color=#19177C]y[/color] [color=#19177C]x[/color]))
     ([color=#008000]+ [/color]([color=#008000]* [/color][color=#19177C]z[/color] [color=#19177C]z[/color]) ([color=#008000]* [/color][color=#19177C]y[/color] [color=#19177C]y[/color])))))

([color=#0000FF]sum-of-larger-squares[/color] [color=#666666]2[/color] [color=#666666]10[/color] [color=#666666]5[/color])

```

---

### Post by Sinkingships7 on 2008-09-11
I realized a better way to go about it would be:

```
([color=#008000]**define **[/color]([color=#0000FF]add-squares[/color] [color=#19177C]a[/color] [color=#19177C]b[/color])
    ([color=#008000]+ [/color]([color=#008000]* [/color][color=#19177C]a[/color] [color=#19177C]a[/color]) ([color=#008000]* [/color][color=#19177C]b[/color] [color=#19177C]b[/color])))

([color=#008000]**define **[/color]([color=#0000FF]sum-of-larger-squares[/color] [color=#19177C]x[/color] [color=#19177C]y[/color] [color=#19177C]z[/color])
  ([color=#0000FF]cond[/color]
    (([color=#008000]**and **[/color]([color=#008000]> [/color][color=#19177C]x[/color] [color=#19177C]z[/color]) ([color=#008000]> [/color][color=#19177C]y[/color] [color=#19177C]z[/color]))
     ([color=#0000FF]add-squares[/color] [color=#19177C]x[/color] [color=#19177C]y[/color]))
    (([color=#008000]**and **[/color]([color=#008000]> [/color][color=#19177C]x[/color] [color=#19177C]y[/color]) ([color=#008000]> [/color][color=#19177C]z[/color] [color=#19177C]y[/color]))
     ([color=#0000FF]add-squares[/color] [color=#19177C]x[/color] [color=#19177C]z[/color]))
    (([color=#008000]**and **[/color]([color=#008000]> [/color][color=#19177C]z[/color] [color=#19177C]x[/color]) ([color=#008000]> [/color][color=#19177C]y[/color] [color=#19177C]x[/color]))
     ([color=#0000FF]add-squares[/color] [color=#19177C]y[/color] [color=#19177C]z[/color]))))

([color=#0000FF]sum-of-larger-squares[/color] [color=#666666]2[/color] [color=#666666]10[/color] [color=#666666]5[/color])

```

If anyone has more ideas, feel free to contribute. I found a satisfactory answer, so this thread is no longer any sort of priority, but I'd always to be interested to see what you come up with.

---

### Post by DavidBell on 2008-09-12
I don't do lisp so syntax is probably wrong, but why can't you do something like

```

(define (add-squares-if-first-two-bigger a b c)
    (cond
       ((and (> a c) (> b c))
         (+ (* a a) (* b b)))

(define (sum-of-larger-squares x y z)
  ((add-squares-if-first-two-bigger x y z)
   (add-squares-if-first-two-bigger y z x)
   (add-squares-if-first-two-bigger z x y))

(sum-of-larger-squares 2 10 5)

```

---

### Post by nvteighen on 2008-09-12
> **DavidBell said:**
> I don't do lisp so syntax is probably wrong, but why can't you do something like

```

(define (add-squares-if-first-two-bigger a b c)
    (cond
       ((and (> a c) (> b c))
         (+ (* a a) (* b b)))

(define (sum-of-larger-squares x y z)
  ((add-squares-if-first-two-bigger x y z)
   (add-squares-if-first-two-bigger y z x)
   (add-squares-if-first-two-bigger z x y))

(sum-of-larger-squares 2 10 5)

```

Well, it's plainly wrong: this is what you get when talking about Lisp without knowing it... ;) (but, hey, why not learn it!)

```
([color=#008000]**define **[/color]([color=#0000FF]add-squares-if-first-two-bigger[/color] [color=#19177C]a[/color] [color=#19177C]b[/color] [color=#19177C]c[/color])
  ([color=#0000FF]cond[/color]
   (([color=#008000]**and **[/color]([color=#008000]> [/color][color=#19177C]a[/color] [color=#19177C]c[/color]) ([color=#008000]> [/color][color=#19177C]b[/color] [color=#19177C]c[/color]))
    ([color=#008000]+ [/color]([color=#008000]* [/color][color=#19177C]a[/color] [color=#19177C]a[/color]) ([color=#008000]* [/color][color=#19177C]b[/color] [color=#19177C]b[/color])))) [color=#408080]*; you forgot a paren*[/color]

([color=#008000]**define **[/color]([color=#0000FF]sum-of-larger-squares[/color] [color=#19177C]x[/color] [color=#19177C]y[/color] [color=#19177C]z[/color])
  ([color=#008000]**begin **[/color][color=#408080]*; necessary*[/color]
    ([color=#0000FF]add-squares-if-first-two-bigger[/color] [color=#19177C]x[/color] [color=#19177C]y[/color] [color=#19177C]z[/color])
    ([color=#0000FF]add-squares-if-first-two-bigger[/color] [color=#19177C]y[/color] [color=#19177C]z[/color] [color=#19177C]x[/color])
    ([color=#0000FF]add-squares-if-first-two-bigger[/color] [color=#19177C]z[/color] [color=#19177C]x[/color] [color=#19177C]y[/color]))) [color=#408080]*; you forgot a paren*[/color]

([color=#0000FF]sum-of-larger-squares[/color] [color=#666666]2[/color] [color=#666666]10[/color] [color=#666666]5[/color])

```

Ok, the problem with that is the (begin ...), when you group with it is undefined by the standard. Usually it is the last value computed, but what if the condition is met for the first procedure and not the others? Then, your result gets lost because of the following procedures you called.

Now, back to the OP:
What I'd do is to call add-squares and determine arguments upon the conditions. Why? Because add-squares is always called and the "variant" part are the arguments.

So, I create a procedure local to add-squares that examinates the arguments and packs the correct pair into a cons. This is captured by a local variable called args... And then, we just call add-squares using selecting the elements in the pair.

This ensures a very nice modularity. If you want to add or remove conditions, you just change the local function!

In code:
```
([color=#008000]**define **[/color]([color=#0000FF]add-squares[/color] [color=#19177C]a[/color] [color=#19177C]b[/color])
  ([color=#008000]+ [/color]([color=#008000]* [/color][color=#19177C]a[/color] [color=#19177C]a[/color]) 
     ([color=#008000]* [/color][color=#19177C]b[/color] [color=#19177C]b[/color])))

([color=#008000]**define **[/color]([color=#0000FF]sum-of-larger-squares[/color] [color=#19177C]x[/color] [color=#19177C]y[/color] [color=#19177C]z[/color])
  ([color=#008000]**define **[/color]([color=#0000FF]choose[/color] [color=#19177C]x[/color] [color=#19177C]y[/color] [color=#19177C]z[/color])
    ([color=#0000FF]cond[/color]
     (([color=#008000]**and **[/color]([color=#008000]> [/color][color=#19177C]x[/color] [color=#19177C]z[/color]) ([color=#008000]> [/color][color=#19177C]y[/color] [color=#19177C]z[/color]))
      ([color=#008000]cons [/color][color=#19177C]x[/color] [color=#19177C]y[/color]))
     (([color=#008000]**and **[/color]([color=#008000]> [/color][color=#19177C]x[/color] [color=#19177C]y[/color]) ([color=#008000]> [/color][color=#19177C]z[/color] [color=#19177C]y[/color]))
      ([color=#008000]cons [/color][color=#19177C]x[/color] [color=#19177C]z[/color]))
     (([color=#008000]**and **[/color]([color=#008000]> [/color][color=#19177C]z[/color] [color=#19177C]x[/color]) ([color=#008000]> [/color][color=#19177C]y[/color] [color=#19177C]x[/color]))
      ([color=#008000]cons [/color][color=#19177C]y[/color] [color=#19177C]z[/color]))))
  ([color=#008000]**let **[/color](([color=#0000FF]args[/color] ([color=#0000FF]choose[/color] [color=#19177C]x[/color] [color=#19177C]y[/color] [color=#19177C]z[/color])))
    ([color=#0000FF]add-squares[/color] ([color=#008000]car [/color][color=#19177C]args[/color]) ([color=#008000]cdr [/color][color=#19177C]args[/color]))))

([color=#0000FF]sum-of-larger-squares[/color] [color=#666666]2[/color] [color=#666666]10[/color] [color=#666666]5[/color])

```

---

