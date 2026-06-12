---
title: "Is my lisp lithpy enough?"
date: 2010-08-30
forum: Programming Talk
---

### Post by Michael3477 on 2010-08-30
I've done a bit of programming in the past, some stuff in Python and Clojure. I wrote this simple bit of common lisp to help me with my time tables because I  never bothered to memorise them. 

The code works, but I'm not sure if i really did it the "right way". I'd like some comments on how I can improve the style. I probably should of wrote some comments in it, but everything seemed so self explanatory. 

btw, I didn't really bother to read a tutorial on CL, I just googled whatever I needed to know syntax wise. 

[PHP]
(defun uglyrandom ()
  (nth (random 5) '(6 7 8 9 12)))
(defun incorrect(a b)
  (format t "incorrect. The answer is ~a~%"(* a b))
  (format t "please enter the correct answer now "))

(defun answer(a b reps)
  (let ((answ (read)))
    (cond ((/= answ (* a b))
       (incorrect a b)
       (if (/= (read) (* a b))
           (format t "you are stupid.~%")
           (question (- reps 1))))
      ((eql answ (* a b))
          (question (- reps 1))))))

(defun question(reps)
  (if (> reps 0)
      (let ((a (uglyrandom))
         (b (uglyrandom)))
     (format t "~a X ~a =" a b)
     (answer a b reps))))

(defun start-rand()
  (format t "Hello how many questions do you want to do?")
  (let ((reps (read)))
    (question reps)))
[/PHP]

---

### Post by schauerlich on 2010-08-30
Your indentation/spacing is a bit off, and you forgot the quote on '(6 7 8 9 12), but other than that it's fine.

```
([color=#008000]defun[/color] [color=#19177C]uglyrandom[/color] ()
  ([color=#008000]nth[/color] ([color=#008000]random[/color] [color=#666666]5[/color]) [color=#666666]'[/color]([color=#666666]6[/color] [color=#666666]7[/color] [color=#666666]8[/color] [color=#666666]9[/color] [color=#666666]12[/color])))

([color=#008000]defun[/color] [color=#19177C]incorrect[/color] ([color=#19177C]a[/color] [color=#19177C]b[/color])
  ([color=#008000]format[/color] [color=#880000]t[/color] [color=#BA2121]"incorrect. The answer is ~a~%" [/color]([color=#008000]*[/color] [color=#19177C]a[/color] [color=#19177C]b[/color]))
  ([color=#008000]format[/color] [color=#880000]t[/color] [color=#BA2121]"please enter the correct answer now: "[/color]))

([color=#008000]defun[/color] [color=#19177C]answer[/color] ([color=#19177C]a[/color] [color=#19177C]b[/color] [color=#19177C]reps[/color])
  ([color=#008000]**let**[/color] (([color=#19177C]answ[/color] ([color=#008000]read[/color])))
    ([color=#008000]cond[/color] (([color=#008000]/=[/color] [color=#19177C]answ[/color] ([color=#008000]*[/color] [color=#19177C]a[/color] [color=#19177C]b[/color]))
           ([color=#19177C]incorrect[/color] [color=#19177C]a[/color] [color=#19177C]b[/color])
           ([color=#008000]**if**[/color] ([color=#008000]/=[/color] ([color=#008000]read[/color]) ([color=#008000]*[/color] [color=#19177C]a[/color] [color=#19177C]b[/color]))
               ([color=#008000]format[/color] [color=#880000]t[/color] [color=#BA2121]"you are stupid.~%"[/color])
               ([color=#19177C]question[/color] ([color=#008000]-[/color] [color=#19177C]reps[/color] [color=#666666]1[/color]))))
          (([color=#008000]=[/color] [color=#19177C]answ[/color] ([color=#008000]*[/color] [color=#19177C]a[/color] [color=#19177C]b[/color]))
           ([color=#19177C]question[/color] ([color=#008000]-[/color] [color=#19177C]reps[/color] [color=#666666]1[/color]))))))

([color=#008000]defun[/color] [color=#19177C]question[/color] ([color=#19177C]reps[/color])
  ([color=#008000]**if**[/color] ([color=#008000]>[/color] [color=#19177C]reps[/color] [color=#666666]0[/color])
      ([color=#008000]**let**[/color] (([color=#19177C]a[/color] ([color=#19177C]uglyrandom[/color]))
            ([color=#19177C]b[/color] ([color=#19177C]uglyrandom[/color])))
        ([color=#008000]format[/color] [color=#880000]t[/color] [color=#BA2121]"~a X ~a = "[/color] [color=#19177C]a[/color] [color=#19177C]b[/color])
        ([color=#19177C]answer[/color] [color=#19177C]a[/color] [color=#19177C]b[/color] [color=#19177C]reps[/color]))))

([color=#008000]defun[/color] [color=#19177C]start-rand[/color] ()
  ([color=#008000]format[/color] [color=#880000]t[/color] [color=#BA2121]"Hello how many questions do you want to do?"[/color])
  ([color=#008000]**let**[/color] (([color=#19177C]reps[/color] ([color=#008000]read[/color])))
    ([color=#19177C]question[/color] [color=#19177C]reps[/color])))
```

Another way to do it would be more imperative with the loop macro, but both work.

---

### Post by nvteighen on 2010-08-31
Haha... I feel Clojure's influence in that code :)

Ok, there's a problem... It's completely unnecessary to have answer call again question just to decrease the reps counter. If you want to keep this functional-like style (it's just "functional-like" because of the IO...). The best seems to be that question handles that on its own, using the so-called tail-recursion technique (something that reveals that in my heart, I'm a Schemer :P)

The idea is that answer should only "react" if the input is incorrect... If it's correct, the function returns back to question, which immediately recurses again and asks something else.

```

(defun uglyrandom ()
  (nth (random 5) '(6 7 8 9 12)))

(defun incorrect (ans)
  (format t "incorrect. The answer is ~a~%" ans)
  (format t "please enter the correct answer now: "))

(defun answer (a b)
  (let ((correct-ans (* a b)))
    (if (/= (read) correct-ans)
        (progn ; Creating a "block"
          (incorrect correct-ans)
          (if (/= (read) correct-ans)
              (format t "you are stupid.~%"))))))

(defun question (reps)
  (if (<= reps 0) ; <= to catch neg numbers
      reps
      (let ((a (uglyrandom))
            (b (uglyrandom)))
        (format t "~a X ~a = " a b)
        (answer a b)
        (question (- reps 1))))) ; Scheme-like!

(defun start-rand ()
  (format t "Hello how many questions do you want to do?")
  (let ((reps (read)))
    (question reps)))

```

---

### Post by nvteighen on 2010-08-31
Uh... a second version, slightly more abstracted... Now you could extend this for more than multiplication:

```

(defun uglyrandom ()
  (nth (random 5) '(6 7 8 9 12)))

(defun incorrect (ans)
  (format t "incorrect. The answer is ~a~%" ans)
  (format t "please enter the correct answer now: "))

(defun answer (correct-ans)
  (if (/= (read) correct-ans)
      (progn ; Creating a "block"
        (incorrect correct-ans)
        (if (/= (read) correct-ans)
            (format t "you are stupid.~%")))))

(defun question (reps)
  (if (= reps 0)
      reps
      (let ((a (uglyrandom))
            (b (uglyrandom)))
        (format t "~a X ~a = " a b)
        (answer (* a b)) ; Change this to whatever you want!
        (question (- reps 1)))))

(defun start-rand ()
  (format t "Hello how many questions do you want to do?")
  (let ((reps (read)))
    (question reps)))

```

---

### Post by Michael3477 on 2010-08-31
Hey, thanks for both of your posts. 
[schauerlich]("http://ubuntuforums.org/member.php?u=278749"): I'm not sure why the quote wasn't in my original post ( '(1 2...)) guess I buggered up the ol c& p somehow >.<

nvteighen: Thanks for the code! I was struggling with why my (if (..)) wasn't working how I expected it to. Also, how you've made the code reusable is a big help. I was looking at the code before wondering how I could change it so I didn't have to write everything again for a simple times-table type thing. (1x1, 1x2, 1x3...). 

It's strange how as soon as you see the answer, it's painfully obvious. I've changed my code to match yours, and put in a times-table type thing. to make sure I fully understood everything. 

If anyones interested here's the updated code. 

```

(defun uglyrandom ()
  (nth (random 5) '(6 7 8 9 12)))
(defun incorrect(ans)
  (format t "incorrect. The answer is ~a~%" ans)
  (format t "please enter the correct answer now "))

(defun answer (correct-ans)
  (if (/= (read) correct-ans)
      (progn ;This lets more than one thing be evaluated in if statement yay
    (incorrect correct-ans)
    (if (/= (read) correct-ans)
        (format t "you are stupid.~%")))))

(defun question(reps)
  (if (= reps 0)
      "woo"
      (let ((a (uglyrandom))
         (b (uglyrandom)))
     (format t "~a X ~a =" a b)
     (answer (* a b))
     (question (- reps 1)))))

(defun start-rand()
  (format t "Hello how many questions do you want to do?")
  (question (read)))

(defun table (times-n &optional (rep 1))
  (if (> rep 12)
      "good work!"
      (progn 
    (format t "~a X ~a = " rep times-n)
    (answer (* rep times-n))
    (table times-n (+ rep 1)))))

(defun start-table()
  (format t "Which table? ")
  (table (read)))

```

---

### Post by worseisworser on 2010-08-31
```

(defun answer (correct-ans)
  (if (/= (read) correct-ans)
      (progn ; Creating a "block"
        (incorrect correct-ans)
        (if (/= (read) correct-ans)
            (format t "you are stupid.~%")))))

```

..could have been..

```

(defun answer (correct-ans)
  (when (/= (read) correct-ans)
    (incorrect correct-ans)
    (when (/= (read) correct-ans)
      (format t "you are stupid.~%"))))

```

It might not seem as much, but after a while using WHEN or UNLESS means a tiny less bit of time is spent mentally parsing code; especially when the blocks of code in question are a bit bigger.

---

### Post by Michael3477 on 2010-09-01
> **worseisworser said:**
> It might not seem as much, but after a while using WHEN or UNLESS means a tiny less bit of time is spent mentally parsing code; especially when the blocks of code in question are a bit bigger.

Thanks for the tip. It does actually seem a little better to me. I won't go changing the code anymore, though. If it ain't broke don't fix it :P

But next time I'll probably end up using when/unless especially if the codes a little chaotic, which it probably will seem to be to me.

---

