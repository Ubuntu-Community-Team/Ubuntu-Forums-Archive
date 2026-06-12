---
title: "(Bash) What is the difference between using and not using &quot;env&quot;?"
date: 2018-08-06
forum: Programming Talk
---

### Post by Paddy Landau on 2018-08-06
In Bash, what is the difference between these two commands?
```
FOO=bar myscript
env FOO=bar myscript
```
As far as I can tell, they are identical.

The only reason to use [FONT=lucida console]env[/FONT] that I can see is if you want to first empty a variable or the entire environment, with the "[FONT=lucida console]--unset[/FONT]" or "[FONT=lucida console]-[/FONT]" options respectively. Is there any other reason to use (or not use) [FONT=lucida console]env[/FONT]?

---

### Post by edadasiewicz on 2018-08-06
From the "point of view" of myscript they will be the same.  But the 2nd line will actually cause 2 processes to be executed since env is an executable which will get overlayed by myscript.

---

### Post by Paddy Landau on 2018-08-06
> **edadasiewicz said:**
> From the "point of view" of myscript they will be the same.  But the 2nd line will actually cause 2 processes to be executed since env is an executable which will get overlayed by myscript.
Hmm, interesting. I guess that the answer, then, is not to use [FONT=lucida console]env[/FONT] unless there is a specific reason to do so.

---

### Post by edadasiewicz on 2018-08-06
The only time I have ever used env is in a shebang statement -- i.e. "#!/usr/bin/env bash" as the first statement of a bash shell script, "#!/usr/bin/env python3" as the first statement in a python3 script, ...

---

### Post by Skaperen on 2018-08-06
other scripting languages use _[FONT=courier new]#!/usr/bin/env[/FONT]_ too.  that's to get a PATH search to find the script interpreter when there is no sure location to find it.  scripts being distributed to a variety of platforms do that to deal with a variety of places where the interpreter might be.  it is usually safe to assume interpreters are in one of the directories listed in the PATH environment variable.

---

### Post by Paddy Landau on 2018-08-07
> **edadasiewicz said:**
> The only time I have ever used env is in a shebang statement…
> **Skaperen said:**
> … that's to get a PATH search…
I forgot about that. I also use it in my scripts. I understand that (say) [FONT=courier new]#!/usr/bin/env bash[/FONT] is more portable than [FONT=courier new]#!/bin/bash[/FONT].

On the other hand, if you need to pass options to the interpreter, such as [FONT=courier new]#!/bin/bash -x[/FONT], you can't use [FONT=courier new]#!/usr/bin/env bash -x[/FONT].

Apparently, the [choice is contentious]("https://unix.stackexchange.com/a/29620/41226"), but I think that on balance it is preferable to use [FONT=courier new]#!/usr/bin/env[/FONT] for "normal" development.

---

