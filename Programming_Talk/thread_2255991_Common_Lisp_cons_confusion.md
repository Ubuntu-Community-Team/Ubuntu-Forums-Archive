---
title: "Common Lisp cons confusion"
date: 2014-12-09
forum: Programming Talk
---

### Post by veddox on 2014-12-09
Hello everybody,

after working through a Common Lisp book over the past two months, I started on my first small project - and promptly ran into problems...

The project is a commandline battleships game, let me give you a code excerpt before I go any further:

```

(defun next-coordinates (start direction) "What are the next coordinates in line?"
    (let ((inc-x 0) (inc-y 0) (next-pos start))
        (cond ((equalp direction 'up) (setf inc-y -1))
            ((equalp direction 'down) (setf inc-y 1))
            ((equalp direction 'right) (setf inc-x 1))
            ((equalp direction 'left) (setf inc-x -1))
            ((equalp direction 'top-right) (setf inc-x 1) (setf inc-y -1))
            ((equalp direction 'top-left) (setf inc-x -1) (setf inc-y -1))
            ((equalp direction 'bottom-right) (setf inc-x 1) (setf inc-y 1))
            ((equalp direction 'bottom-left) (setf inc-x -1) (setf inc-y 1)))
        (setf (first next-pos) (+ inc-x (first next-pos)))
        (setf (second next-pos) (+ inc-y (second next-pos)))
        (if (valid-coordinates-p next-pos) 
            next-pos NIL)))

;FIXME The problem function
(defun calculate-ship-position (bow direction size) "Calculate the positions of this ship"
    (if (zerop size) NIL
        (cons bow (calculate-ship-position (next-coordinates bow direction) direction (decf size)))))

```

What the function (calculate-ship-position) is supposed to do is to return a list of square coordinates that a ship of the given size will occupy, given the inputed bow coordinates and direction. I.e. calling (calculate-ship-position '(2 1) 'down 3) should return the list '((2 1) (2 2) (2 3)). Unfortunately, what it *does* return is '((2 4) (2 4) (2 4)), and I have no clue why.

I know that (next-coordinates) works as it should. I have tried implementing (calculate-ship-position) iteratively or recursively, as here, but that makes no difference to the output. I stepped through the function, and found that it builds up the result list in the following steps: '((2 1)) - '((2 2) (2 2)) - '((2 3) (2 3) (2 3)) - '((2 4) (2 4) (2 4))

I know that the problem is with the following line:
```
(cons bow (calculate-ship-position (next-coordinates bow direction) direction (decf size)))
```
Somehow, cons is not working the way I expect it to work. It's probably some incredibly stupid newbie error, but it has defeated me :-( 
Could somebody please help me there?

---

### Post by spjackson on 2014-12-09
I don't think there's anything wrong with your use of cons in calculate-ship-position. I think your problem is rather your use of setf here:
```

        (setf (first next-pos) (+ inc-x (first next-pos)))
        (setf (second next-pos) (+ inc-y (second next-pos)))

```
My Common Lisp is rather rusty, but this seems to work:
```

(defun next-coordinates (start direction) "What are the next coordinates in line?"
    (let ((inc-x 0) (inc-y 0))
        (cond ((equalp direction 'up) (setf inc-y -1))
            ((equalp direction 'down) (setf inc-y 1))
            ((equalp direction 'right) (setf inc-x 1))
            ((equalp direction 'left) (setf inc-x -1))
            ((equalp direction 'top-right) (setf inc-x 1) (setf inc-y -1))
            ((equalp direction 'top-left) (setf inc-x -1) (setf inc-y -1))
            ((equalp direction 'bottom-right) (setf inc-x 1) (setf inc-y 1))
            ((equalp direction 'bottom-left) (setf inc-x -1) (setf inc-y 1)))
        (let ((next-pos (list (+ inc-x (first start)) (+ inc-y (second start)))))
             (if (valid-coordinates-p  next-pos)
                  next-pos NIL))))

```

---

### Post by veddox on 2014-12-10
????

It works! *incredulous face*

I really don't understand this... When I tested (next-coordinates) before, it worked no problem - and I don't understand what difference your code makes compared to mine? Could you enlighten me?

But thank you very very much for your help, that bug really had me stumped!

---

### Post by spjackson on 2014-12-10
next-coordinates does indeed return the correct value (as your testing shows), but setf has a side-effect.

In essence, when you pass 'bow' as the 'start' parameter of next-coordinates and then assign it to next-pos, each of these variables is a reference to the same list, not separate copies of the list. When you use setf on next-pos you are directly updating the contents of that list. So the values of 'start' and 'bow' are also changed.

As you come out of your recursive calls to calculate-ship-position and each (cons bow ...) occurs, the value of bow is whatever next-pos was at the deepest call level.

At least, that is my understanding, but it's a very long time since I did much with Common Lisp.

---

### Post by veddox on 2014-12-11
Ah, now I get it! Thank you very much!

No wonder my Lisp book told me to beware of side-effects - what a devilish bug! ;-)

---

