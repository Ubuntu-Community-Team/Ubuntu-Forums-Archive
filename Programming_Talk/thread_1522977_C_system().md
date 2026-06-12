---
title: "C system()"
date: 2010-07-02
forum: Programming Talk
---

### Post by Finalfantasykid on 2010-07-02
I have a program which uses the system() function and currently I am redirecting the output of the command to a text file so that it can be read later in the program.  However I would rather have it store the output of the command directly in the program as a char* or something like that so that I am not wasting time constantly writing files then reading them.  Is there a way to do this?

In php it is easy since the exec() function has an optional parameter to store the output.  I would like something with the same functionality.

---

### Post by SaintDanBert on 2010-07-02
I have always opened a named pipe in my programs and passed the
pipe details to the shell that results from the system() call as an
output parameter.

My program then watches the pipe and read the data as it gets written.
When system() shell ends and closes the pipe, the program sees end of file and responds accordingly.

~~~ 0;-Dan

---

### Post by soltanis on 2010-07-02
You can also use the popen function, see **man 3 popen**.

---

### Post by Finalfantasykid on 2010-07-02
> **soltanis said:**
> You can also use the popen function, see **man 3 popen**.

Thanks that did exactly what I wanted

---

### Post by SaintDanBert on 2010-07-05
> **soltanis said:**
> You can also use the popen function, see **man 3 popen**.

I had forgotten about **popen( )**.
Lots of rust on my C-skills.
Slightly younger dust...

Thanks,
~~~ 0;-Dan

---

