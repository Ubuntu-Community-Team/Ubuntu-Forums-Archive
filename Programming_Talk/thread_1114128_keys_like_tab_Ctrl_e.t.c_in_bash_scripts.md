---
title: "keys like tab Ctrl e.t.c in bash scripts"
date: 2009-04-02
forum: Programming Talk
---

### Post by Claus7 on 2009-04-02
Hello,

I would like to write a script which will be able to recognize the keyboard keys and be able to run.

For example in the various ubuntu releases the version of gfortran is different from version to version. So something like this:

gfortran(...) file.f90

should suffice from transferring scripts.
There exists gfortran, gfortran-4.1 and so on.
Has anyone any idea of how this can be done? The \t after gfortran seems not to work.

Thanks for any help,
Regards!

---

### Post by Arndt on 2009-04-02
> **Claus7 said:**
> Hello,

I would like to write a script which will be able to recognize the keyboard keys and be able to run.

For example in the various ubuntu releases the version of gfortran is different from version to version. So something like this:

gfortran(...) file.f90

should suffice from transferring scripts.
There exists gfortran, gfortran-4.1 and so on.
Has anyone any idea of how this can be done? The \t after gfortran seems not to work.

Thanks for any help,
Regards!

It sounds like you want to use the file name expansion patterns, like for example gfortran*. This matches everything that starts with the string "gfortran". If that is only one thing, it's equivalent to pressing Tab in an interactive shell. There may be a way to switch on the interactive keyboard commands in a non-interactive shell, but I wouldn't recommend it. They are meant to be precisely interactive, so you have less control of what happens when the script can't interact.

---

### Post by Claus7 on 2009-04-03
Hello,

thank you for your answer. I have to say that I have tested what you propose and it didn't work. Even typing <tab> after the gfortran string, yet to no avail. 

I have to admit that I was expecting the * to work, yet this isn't the case. It sais that command gfortran* not found. Even with gfortran\*. It is weird because I do use #!/bin/bash and I do not get why this isn't working.

I would like something to be very robust. I cannot afford not having a good control over these scripts. What I can do is change every time the version of the compiler I'm using, yet I was hopping if this could be done automatically. 

Regards!

---

### Post by ghostdog74 on 2009-04-03
is that all to your script. if you have more, show them

---

### Post by Arndt on 2009-04-03
> **Claus7 said:**
> Hello,

thank you for your answer. I have to say that I have tested what you propose and it didn't work. Even typing <tab> after the gfortran string, yet to no avail. 

I have to admit that I was expecting the * to work, yet this isn't the case. It sais that command gfortran* not found. Even with gfortran\*. It is weird because I do use #!/bin/bash and I do not get why this isn't working.

I would like something to be very robust. I cannot afford not having a good control over these scripts. What I can do is change every time the version of the compiler I'm using, yet I was hopping if this could be done automatically. 

Regards!

The asterisk pattern works for file name arguments, but it doesn't work for commands. It would if the current directory were where the command is located, but that's usually not the case.

This may work for you:

```
find `echo $PATH | tr ':' ' '` -name gfortran\*
```

---

### Post by Claus7 on 2009-04-04
Hello,

thank you all for your answers. 

@Ghostdog : there is really no reason to print my whole script. What it does in the specific part I'm interested in is checking which version of fortran compiler exists and compile my .f90 files. Then the output from this action is taken in a file, which I post process. I do understand why are you telling me this, yet it has nothing to do with the rest of my script. E.g. I erase some files afterwards, so what I'm asking is pretty specific on what you see in my first post.

@Arndt : Very helpful your command. As you already knew, it finds the absolute path of the fortran compiler. Yet, I cannot make out how I will be able to pipe this command with my e.g. test.f90 file. The simple pipe doesn't work. Assigning it as a variable (the path) and then use it, it still doesn't work. 

Has anyone any idea of how from the command given by Arndt, which produces the absolute path of the gfortran command to use this path somehow in order to compile a program?

Thank you once again,
Regards!

---

### Post by Arndt on 2009-04-04
> **Claus7 said:**
> Hello,

@Arndt : Very helpful your command. As you already knew, it finds the absolute path of the fortran compiler. Yet, I cannot make out how I will be able to pipe this command with my e.g. test.f90 file. The simple pipe doesn't work. Assigning it as a variable (the path) and then use it, it still doesn't work. 

Has anyone any idea of how from the command given by Arndt, which produces the absolute path of the gfortran command to use this path somehow in order to compile a program?

Thank you once again,
Regards!

Personally, I would ensure that the Fortran compiler had one known name everywhere where I wanted to use it, by creating a symbolic link from /usr/bin/gfortran-whatever to /usr/bin/gfortran, for example. But maybe you don't have that much control over the execution environment. I find it strange that the Fortran system doesn't have one stable name for invoking the compiler.

To set a variable to the result of my command should be easy:

```
FORTRAN_CMP=`find \`echo $PATH | tr ':' ' '\` -name gcc\*`
$FORTRAN_CMP file.f90
```

The \ are needed to ensure that the inner ` doesn't end the outer ` prematurely.

---

### Post by Claus7 on 2009-04-04
Hello,

thank you Arndt! This is exactly what I was looking for. Your explanation for the "\" before the inner "`" was very comprehensible. So, I had to enclose the whole command to "`", so as to be able to use the entire command as a variable and execute my fortran code.

Sometimes it is difficult to go and write or remember to go and write to every computer the link you provide so as to have no problem with the version of the compiler. Especially if you have many many scripts which deal with many parameters. I think that the different versions enclose much more options to the compiler so as in the end to comply with the 2003(8?) standards.

So I had to avoid mimicking the keys in order to solve my problem.

It was very helpful,
Regards!

---

### Post by slavik on 2009-04-04
you can also do $(command) instead of `command`

---

### Post by Arndt on 2009-04-04
> **slavik said:**
> you can also do $(command) instead of `command`

Good to know, and it doesn't need the inner quoting. But if one should come across a real Bourne shell (not bash), the $( ) construct isn't available, I think.

---

