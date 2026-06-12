---
title: "Can't set &quot;c-brace-offset&quot; in emacs.  Please help!"
date: 2010-10-13
forum: Programming Talk
---

### Post by Jack Kelly on 2010-10-13
Hi there,

I'm fairly new to emacs but I'm enjoying it.

By default it indents code like this:

```

if (a<b)
  {
    do something;
  }
```but I want my curly brackets to be lined up like this:

```

if (a<b)
{
    do something;
}
```A bit of googling suggests that I need to set the variable "c-brace-offset" to -2.  But no matter what I do, I can't get emacs to notice any setting of "c-brace-offset".  Emacs is definitely taking note of my .emacs file because I've successfully changed a few other settings.

Any tips on getting emacs to take note of the c-brace-offset variable?!

(I'm trying to write C++ code on Ubuntu 10.04 with emacs 23.1)

---

### Post by r-senior on 2010-10-13
I don't use Emacs so I'll admit this is a guess, but have you tried setting it to zero? My reasoning being that you are just trying to remove the extra indent applied to a brace that starts a line, not fighting the normal indent.

---

### Post by pbrane on 2010-10-13
Mine is set like this in ~/.emacs 
```

 '(c-basic-offset 2)
  '(c-default-style (quote (**(c-mode . "k&r")** (java-mode . "java") (other . "gnu"))))

```

I think it has more to do with the code style than the offset.

---

### Post by r-senior on 2010-10-13
Your code doesn't appear to be using K&R, which would place the opening brace at the end of the line in conditionals. The extra indent looks like GNU style. How about changing "gnu" to "bsd" (Allman) and see if that works:

[http://en.wikipedia.org/wiki/Indent_style]("http://en.wikipedia.org/wiki/Indent_style#Allman_style_.28bsd_in_Emacs.29")

Presumably there is a mode that can distinguish C++ to do it properly rather than leaving it using the "other" setting. Perhaps cc-mode?

---

### Post by Jack Kelly on 2010-10-13
many thanks for the replies.  yup, setting the C++ coding style to K&R works!  Many thanks!  But now I think about it, perhaps I should adopt the Stroustrup style.

thanks again,
jack

---

