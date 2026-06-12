---
title: "OCaml mutex problem"
date: 2010-04-06
forum: Programming Talk
---

### Post by ayushjsh on 2010-04-06
Hi im a newbie programmer in OCaml and was trying out a code which involved Mutex ,

My code is something like this :

let m = mutex.create();;

and the error i get is ::

let m = _mutex_.create() ;;

unbound value mutex

also i need to use this under windows

ive checked many places but i cant get this to work. I found answers like i need to include packages like unix.cma and threads.cma but i really cant figure out how ??? can anyone give me a complete solution to this problem ??

---

### Post by kcode on 2010-04-11
Assuming we have this in main.ml
```

let m = Mutex.create();;
Printf.printf "%s\n" "Hello AJ";;

```

We can build it this way
```

ocamlbuild -libs unix,threads -cflags -I,+threads -lflags -I,/usr/lib/ocaml/3.10.0/threads main.native

```

```

$ ./main.native
$ Hello AJ

```

---

