---
title: "very basic latex question"
date: 2006-04-09
forum: Programming Talk
---

### Post by orlox on 2006-04-09
I'm having a very simple, but annoying problem in latex. I need to write "0000008.FIT_0, and when trying to build the document, it says that what I wrote was wrong because of the _ that corresponds to the character used to subscript something. How can I solve this? This also made me thought, what if I want to write something like \frac{}{} so it displays just like simple text?

---

### Post by mentok on 2006-04-09
Try 0000008.FIT\_0

](*,)

---

### Post by hod139 on 2006-04-10
The backslash is the escape character.  So to write the frac command:
```
\\frac\{\}\{\}
```
or to make it stick out you can use a verbatim environment
```

[COLOR=#800000]\verb[/COLOR][COLOR=#a08000] \frac{}{} [/COLOR]{} foo % Need the {} to get the space before foo 
[COLOR=#f00000]\begin[/COLOR]{[COLOR=#0000d0]verbatim[/COLOR]} [COLOR=#a08000]
\frac{}{}[/COLOR] [COLOR=#f00000]
\end[/COLOR]{[COLOR=#0000d0]verbatim[/COLOR]}

```

---

