---
title: "Need help in compiling"
date: 2007-04-03
forum: Programming Talk
---

### Post by gil michael on 2007-04-03
hi,

i wrote a c program, and i tried to compile it using gcc in the next format:

gcc -std=c99 -pedantic-errors -Wall mtm.c mtm.o -o mtm

(mtm.o is an object file i got from a friend)

i get the next error:

 mtm.o: Relocations in generic ELF (EM: 2)
mtm.o: could not read symbols: File in wrong format
collect2: ld returned 1 exit status

What is the problem? how can i compile more than one file using gcc?

Thanks,

Gil

---

### Post by Wybiral on 2007-04-03
Was it a Linux object file?

Can you maybe attach the object file so we can verify that its a Linux object file?

---

### Post by rplantz on 2007-04-03
> **gil michael said:**
> hi,

i wrote a c program, and i tried to compile it using gcc in the next format:

gcc -std=c99 -pedantic-errors -Wall mtm.c mtm.o -o mtm

I don't understand why you have both the source (mtm.c) and object (mtm.o) files in this command. Perhaps it's a syntax I don't know about.
> 
(mtm.o is an object file i got from a friend)

Do you know how your friend produced this object file? Are you using the same options?
> 
i get the next error:

 mtm.o: Relocations in generic ELF (EM: 2)
mtm.o: could not read symbols: File in wrong format
collect2: ld returned 1 exit status

My guess is that one of you is using the ELF format and the other isn't. I don't know enough about the various standards to know if the problem is with using c99.
> 
What is the problem? how can i compile more than one file using gcc?

To compile and link separate files, simply list them on the command line:
```

gcc myProg.c mySub.c friends_file.o -o myProg

```
Notice that you can list both source and object files. gcc is smart enough to tell the difference and do the right thing.

---

