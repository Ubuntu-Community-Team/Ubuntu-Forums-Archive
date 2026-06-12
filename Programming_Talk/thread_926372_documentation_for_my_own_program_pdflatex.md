---
title: "documentation for my own program pdf/latex"
date: 2008-09-21
forum: Programming Talk
---

### Post by monkeyking on 2008-09-21
Hi,
I'm almost done with my program,
and I want to write some documention.
End product in latex/pdf.
I've been using latex for some years in math, so using latex is not a problem.

I've been looking into doxygen,
but it looks to heavy for me.

I basicly just want to extract a list of method/functions from my cpp file.
And then document the most important functions.

And also give some code examples.

But I have no idea what enviroment I should use, that is,
keeping latex from formatting it as regular text.

Does anyone have an idea about, what to use,
or some advice  about how to write this documentation.

thanks

---

### Post by Pro-reason on 2008-09-21
> **monkeyking said:**
> 
But I have no idea what enviroment I should use, that is,
keeping latex from formatting it as regular text.

I'm not sure what you mean by that.

---

### Post by monkeyking on 2008-09-22
> **Pro-reason said:**
> I'm not sure what you mean by that.

I don't want latex to try formatting it as a normal text,
by that I mean it shouldn't change my indentation etc.

When ever I type en math equations I would type in some thing like
```

\begin{eqnarray}
my math stuff
\end{eqnarray}

```
I'm looking for something like this, where I can put in my c/c++ code in.

thanks for your relply

---

### Post by Lux Perpetua on 2008-09-22
The verbatim environment is good if you just want monospaced plain text with spaces preserved. (Remember to \usepackage{verbatim}.)

---

### Post by hugmenot on 2008-09-22
You can directly include cpp files and code snippets with the listings package. Optionally listings can add some c++ specific syntax highlighting to the code.

---

