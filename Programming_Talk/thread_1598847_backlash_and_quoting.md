---
title: "backlash and quoting"
date: 2010-10-17
forum: Programming Talk
---

### Post by SteelCore on 2010-10-17
```
$ echo hi\tthere
hitthere
```

```
$echo "hi\tthere"
hi\tthere
```

In my understanding in the first command the backlash is an escape sequence which makes any special character after it lose their meaning, It is not really a character and therefore doesn't appear in the output.
In the second command, double quoting suppresses expansions but not backlashes so its special meaning holds. Then why does it appear in the output?
Thanks for any help.

---

### Post by spjackson on 2010-10-17
> **SteelCore said:**
> ```
$ echo hi\tthere
hitthere
``````
$echo "hi\tthere"
hi\tthere
```In my understanding in the first command the backlash is an escape sequence which makes any special character after it lose their meaning, It is not really a character and therefore doesn't appear in the output.
In the second command, double quoting suppresses expansions but not backlashes so its special meaning holds. Then why does it appear in the output?
Thanks for any help.
I'm guessing that you are using bash. If not then different rules may apply.

"man bash" says: "Enclosing characters in double quotes... the backslash retains its special meaning only when followed by one of the following  characters: $,  `,  ", \, or <newline>."

Your backslash is in double quotes and is not followed by one of the above characters, so it has no special meaning.

---

### Post by Diametric on 2010-10-18
Reason #148 why I need to man up and read the man page.  Get it...map up...jeez, I crack myself up.

---

