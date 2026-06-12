---
title: "prolog ocaml comparison"
date: 2008-10-29
forum: Programming Talk
---

### Post by MarkieB on 2008-10-29
no longer participating in ubuntuforums.org

---

### Post by slavik on 2008-10-29
it would be an interesting discussion (I have never seen ocaml code, only prolog)

---

### Post by Kadrus on 2008-10-29
> I have never seen ocaml code
Here's one..thought I would do project euler 1,so everyone can see what im doing.
```
let rec mylist = function
   |0->[]
   |n->n::(mylist(n-1));;
List.fold_left (+) 0 (List.filter (fun x-> x mod 3=0 || x mod 5=0)(mylist 999));;

```
Running it in interactive mode.
Ocaml has a nice standard Library.
I wouldn't compare Ocaml and Prolog both.Ocaml is a functional programming language that has object orientation.
Prolog is a logic programming language mostly used for artifical intelligence.
I've seen some prolog code but never written one.

---

### Post by MarkieB on 2008-11-02
no longer participating in ubuntuforums.org

---

### Post by jimi_hendrix on 2008-11-02
imo...with minimal experience with either...prolong seems to be where you state facts (dan and bob are sons of rob) and rules (sons of the same parent are brothers)...ocaml is like said before...functional OOP

---

### Post by kknd on 2008-11-02
Can't be compared at all (prolog = "logic", ocaml = "functional").

Prolog has some nice features like "default" backtracking and  "param inference".

Example:

In the file test.pl I defined:

rocks(prolog).
rocks(ocaml).

Then I entered the prompt (using swi-prolog):
?- ['test.pl'].
% test.pl compiled 0.00 sec, 520 bytes
true.

?- rocks(prolog).
true.

?- rocks(X).
X = prolog (typed ';' for the next match)
X = ocaml.

Nice!

---

