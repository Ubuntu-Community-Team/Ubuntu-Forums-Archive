---
title: "Getting"
date: 2006-04-30
forum: Programming Talk
---

### Post by newdarkness on 2006-04-30
For some reason I never seem to get my gcj working - the below error occours - does anybody have an idea what might cause this? ```
lars@l-m4:~$ echo "public class x{public static void main(String[]a){System.out.println(a[0]);}}" > x.java
lars@l-m4:~$ gcj x.java
/usr/lib/gcc/i486-linux-gnu/4.1.0/../../../../lib/crt1.o: In function `_start':../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status
lars@l-m4:~$

```

---

### Post by stuporglue on 2006-04-30
Does the program you're trying to compile have a main method?

---

### Post by newdarkness on 2006-04-30
yes, the program is certainly working with javac and has a main method


[I]*sorry about the title, I am quite sure to have written
Getting GCJ to work[/I]

---

### Post by tageiru on 2006-04-30
[QUOTE=newdarkness]does anybody have an idea what might cause this?[/QUOTE]
GCJ needs the -C flag in order to generate bytecode, just invoking it with a .java file will produce an ELF binary (in that case it needs to know where the main method is with the --main flag as indicated by your error)

The manpages describe this in detail.

---

