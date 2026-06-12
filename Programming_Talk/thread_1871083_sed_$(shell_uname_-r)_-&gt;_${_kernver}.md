---
title: "sed: $(shell uname -r) -&gt; ${_kernver}"
date: 2011-10-28
forum: Programming Talk
---

### Post by Intrepid Ibex on 2011-10-28
Hey,

I'm trying to change the variable **$(shell uname -r)** to **${_kernver}** with sed, but am unable to do so:
```
~> sed -i -e "s|$(shell uname -r)|${_kernver}|" src/Makefile
[I](~> bash: shell: command not found)
[/I]~> sed: -e expression #1, char 0: no previous regular expression
```

Heeeeelp.

---

### Post by karlson on 2011-10-28
> **Intrepid Ibex said:**
> Hey,

I'm trying to change the variable **$(shell uname -r)** to **${_kernver}** with sed, but am unable to do so:
```
~> sed -i -e "s|$(shell uname -r)|${_kernver}|" src/Makefile
[I](~> bash: shell: command not found)
[/I]~> sed: -e expression #1, char 0: no previous regular expression
```

Heeeeelp.

$ is a special character in regular expressions you should \ escape it
```

sed -i -e "s|\$(shell uname -r)|\${_kernver}|" test

```

---

