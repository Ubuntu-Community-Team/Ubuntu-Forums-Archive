---
title: "What's the meaning of &quot;typeset -il start&quot;?"
date: 2015-04-08
forum: Programming Talk
---

### Post by hugolia2 on 2015-04-08
I am converting a Korn Shell script to Bash and found the declare line:

    **[FONT=courier new]typeset -il start[/FONT]**

I searched the web and different books but found no reference about the "**[FONT=courier new]-il[/FONT]**" option.
I found that "[FONT=courier new]**-i**[/FONT]" is for integer and "**[FONT=courier new]-l[/FONT]**" is for lowercase string. But I found no description of the combination.

Could it be a variation of the "[FONT=courier new]**-i**[/FONT]" option? Maybe a long integer?

---

### Post by steeldriver on 2015-04-08
Your inference appears to be correct:

```

              -l     Used with -i, -E or -F, to indicate long integer, or long
                     float.  Otherwise, all  upper-case  characters  are  con&#8208;
                     verted  to  lower-case.   The  upper-case  option, -u, is
                     turned off.  Equivalent to -M tolower .

```

(from the ksh93 manpage - I'm not sure if all versions support it)

---

