---
title: "Help on running a programme on ubuntu."
date: 2005-08-31
forum: Programming Talk
---

### Post by mczi on 2005-08-31
Thanks for the help on my last trouble but now that I have that I can compile on ubuntu I can't run the programmes after compiling them. I do not know if I'm wrong but after compiling I type the name of the file at the command prompt but it says 'command not found'.

I'm using 'C'.
This is the final step and help will be greatly appreciated!!! ](*,)

---

### Post by invalid on 2005-08-31
to run a compiled program you type:

./program

If for some reason this is not permitted, you need to
chmod +x program
but it should work with the first command

Cheers,
Cb

---

### Post by deathseeker25 on 2005-08-31
[QUOTE=invalid]to run a compiled program you type:

./program

If for some reason this is not permitted, you need to
chmod +x program
but it should work with the first command

Cheers,
Cb[/QUOTE]

Sure use this and i think you'll never have problems. I never had problems with my own programs and i use these commands.

Stay well []

---

### Post by varunus on 2005-08-31
[QUOTE=mczi]Thanks for the help on my last trouble but now that I have that I can compile on ubuntu I can't run the programmes after compiling them. I do not know if I'm wrong but after compiling I type the name of the file at the command prompt but it says 'command not found'.

I'm using 'C'.
This is the final step and help will be greatly appreciated!!! ](*,)[/QUOTE]

This is because linux won't run programs in any directory; it'll only run programs from directory's in your PATH variable.  To make it run a program from the current directory, type:

```
./programname
```

and press enter.

---

