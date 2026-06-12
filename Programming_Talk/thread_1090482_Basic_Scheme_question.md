---
title: "Basic Scheme question"
date: 2009-03-08
forum: Programming Talk
---

### Post by evymetal on 2009-03-08
I've been trying to play around with Scheme a little, but I can't work out where I'm going wrong. 

I know this may not be the best way to write this procedure, but I'm confused about why I can't call it

```

(define fact
    (lambda 
        (x1)
        (if
            (eqv? x1 1)
            x1
            (
                (* x1 (apply fact (- x1 1) )
            )
        )
    )
)

(begin

    (display 
        (number->string 
            (apply fact 1)
        )
    )
    newline
)

```


and I am getting the following errors (I'm using Bigloo as the interpreter)

```

#            (apply fact 1)
#            ^
# *** WARNING:bigloo:toplevel-init
Type error --  `pair' expected, `long' provided

#            (apply fact 1)
#            ^
# *** WARNING:bigloo:toplevel-init
Type error --  `pair' expected, `long' provided

```

What am I doing wrong? surely if I pass (1) then it will just evaluate to 1, and it doesn't seem to make much sense to me if you have to pass '(1).

---

### Post by evymetal on 2009-03-08
Ah, solved it - I was being dumb and using "apply" when i wasn't passing a list.

this works
```

(define (fact x)
    (if
        (eqv? x 0)
        1
        (* 
            x
            (fact (- x 1) )
        )
    )
)


(begin
    (display 
        (number->string 
            (fact 3)
        )
    )
    newline
)

```

---

### Post by CptPicard on 2009-03-08
Hint, for more "standard" indentation style people are used to reading:


```

(define (fact x)
    (if (eqv? x 0)
        1
        (* x (fact (- x 1)))))

(begin
    (display (number->string (fact 3)))
    newline)

```

---

