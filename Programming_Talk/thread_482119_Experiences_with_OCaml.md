---
title: "Experiences with OCaml?"
date: 2007-06-23
forum: Programming Talk
---

### Post by Ubuntist on 2007-06-23
Would anyone who has used OCaml care to comment on its merits?

Over the last several months, I've been getting back into programming after a long hiatus.  I've been perusing the available languages in an attempt to decide which best suit my purposes.  I do a lot of heavily numerical work, including simulations.  Ideally, I would learn lots of languages in some depth, but there are so many languages these days that that's not practical.

---

### Post by Jessehk on 2007-06-23
Just keep in mind that I'm a high school student, and as such, my opinion is probably worth very little. :)

I like OCaml. Some of its merits include safety, speed, and it's functional core (though it has *while* loops, *for* loops, and mutable data) while also including some OOP facilities. It has a code profiler (ocamlprof), a bytecode compiler that produces portable executables (ocamlc), a native compiler that produces platform-dependant (and fast!) executables (ocamlopt), a debugger (ocamldebug), and documentation generator (ocamldoc), and its own version of lex and yacc (ocamllex and ocamlyacc) (though I've never used these tools).

It's particularly known for it's **very** strong type system. There are _no_ implicit conversions between types. For example (taken from the interactive top-level. Normal code rarely has ";;" in it):

```

# 2 + 3 ;;
- : int = 5
# 2 + 3.0 ;;
This expression has type float but is here used with type int
# 2.0 +. 3.0 ;;
- : float = 5.

```

In addition, it can determine the types of functions based on the actions that are taken inside the functions.

For example:
```

# let square n = n * n ;;
val square : int -> int = <fun>
# square 3 ;;
- : int = 9
# square 3.0 ;;
This expression has type float but is here used with type int

```

It has a variety of libraries: lists, arrays, hash tables, str (for regexp and high-level string processing), num (for arbitrary size numbers), unix (for interacting the with OS),  openGL bindings, etc.

Personally, I find it's a bit too low-level for scripts, but as a replacement for C or C++ (it's only about 10% slower), it's amazing. Your program will only compile if it is guaranteed to run without any unexpected errors (ie, if you've covered all corner cases with exceptions) and the types all work out. As a result, if it compiles, it will usually be correct the first time you run it.
I've also heard it's great for numerical computing. In particular, somebody named Jon Harrop sells a self-published, highly praised book called *OCaml for Scientists*. It might be worth looking in to.

EDIT: An example with List.map
```

# let square n = n * n ;;
val square : int -> int = <fun>
# List.map square [1; 2; 3; 4; 5] ;;
- : int list = [1; 4; 9; 16; 25]

```

EDIT2: Check out this online tutorial: [http://www.ocaml-tutorial.org/](http://www.ocaml-tutorial.org/)

---

### Post by Ubuntist on 2007-06-26
Thanks very much, Jessehk, for your detailed and helpful reply.

I do like the look of OCaml.  I like its careful attention to type consistency.  After a few months using Ruby and Python, I just can't see what's so great about dynamic typing and have often made errors that would have been caught early in a strictly-typed language.

I also like its speed, which is important for what I do.

What I'm less sure about is how well its functional orientation would suit me -- I've never really tried the functional paradigm.

---

### Post by Jessehk on 2007-06-26
> **Ubuntist said:**
> 

What I'm less sure about is how well its functional orientation would suit me -- I've never really tried the functional paradigm.

Well, it's certainly not purely functional like Haskell. In Haskell, side-effects are not allowed, so you have to do everything like changing state through monads. Haskell is a lot more elegant than OCaml, but it's slower, harder to learn, and monads can be annoying to work with (I'm just starting to understand them). On the other hand, it has a larger community than OCaml, probably because of it's extreme helpfulness (they probably have the nicest IRC channel ever. 5 of them worked through state monads with me for half an hour), it's reputation of difficulty (who doesn't like a challenge? ;)), and its elegance.

---

