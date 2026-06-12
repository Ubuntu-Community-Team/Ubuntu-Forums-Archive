---
title: "Emacs help: command for eq. of &quot;astyle -U&quot;?"
date: 2009-04-13
forum: Programming Talk
---

### Post by mltucker on 2009-04-13
Hi,

I am a new user of Emacs and really appreciate things like source indentation.  I get a lot of source code with things like

```

int someFunction( double someParam )
    {
        for ( int ii = 0; i < 10; i++ )
            ...
    }

```

I can get emacs to reindent everything with C-M-\, but I often use the command

astyle -U

to unpad the extra spaces around "double someParam" and before "int ii", etc.

My questions are,

a. Is there some function in emacs that will do this for me without having to run a shell or shell command?
b. Is this something that could be easily implemented in elisp?

Both would be useful -- b since I'd like to be able to do these types of things eventually.

Thanks.

-Mark

---

