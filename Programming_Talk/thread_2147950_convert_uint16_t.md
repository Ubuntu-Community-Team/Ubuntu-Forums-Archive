---
title: "convert uint16_t"
date: 2013-05-23
forum: Programming Talk
---

### Post by ferizhandi on 2013-05-23
hi all

how can i convert uint16_t to char*?!
i want to display value of uint16_t and i don't want to use printf or ... . i want to use system call function.

---

### Post by Bachstelze on 2013-05-23
> i want to use system call function. 

And just for kicks, which system call do you plan to use?

---

### Post by ferizhandi on 2013-05-23
i want to use "write()".

---

### Post by ofnuts on 2013-05-23
Then convert the value to string using sprintf() or snprintf() and write() the result.

---

### Post by dwhitney67 on 2013-05-23
> **ferizhandi said:**
> hi all

how can i convert uint16_t to char*?!
i want to display value of uint16_t and i don't want to use printf or ... . i want to use system call function.

There are two ways to write a number to a file using write().  You can convert the number to a string, and then write it (see ofnuts recommendation).  Or you can write the value in binary.  Which form do you require?

P.S.  Actually, if you require to write as text, then just use fprintf().  write() is really suitable for low-level output.

---

### Post by nvteighen on 2013-05-24
Unless you require to save this data as binary (in which case you have to use read/write), you're better using the higher level C standard I/O operations (fprintf et al.) so you get an automatic conversion from uint16_t to char * and viceversa. Be aware that this may be really useful if you plan to use output this value to stdout or if this value is to be retrieved from user input. Moreover, using ASCII files are much easier to debug than binary ones as only the former are human readable with a text editor.

(Just my two cents)

---

