---
title: "LINUX and C (simple question )"
date: 2006-09-09
forum: Programming Talk
---

### Post by kitt on 2006-09-09
Hello all,
Ive compiled a C program using gcc, and i want to run it as a bash command. The program takes many arguements as input, and running ./a.out simply prints the output which the program returns when it is executed without any arguements..
So, what do i do?? I am new to the LINUX (oh yes, i use Ubuntu )..
I would be glad if anyone helps me out with this...Thanks

---

### Post by nereid on 2006-09-09
Hi,

just do it like you would do it in Windows.

```

./a.out ARGUMENT1 ARGUMENT2 ARGUMENT3 .. ARGUMENTX

```

For example you would call echo like this

```

echo "Hello World"

```

Which will print "Hello World" on the screen.

---

