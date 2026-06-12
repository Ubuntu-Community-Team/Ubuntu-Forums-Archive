---
title: "How to use variable set from terminal in TCL ?"
date: 2009-04-01
forum: Programming Talk
---

### Post by tusharv on 2009-04-01
Hi All,

I have set one variable PROJECT_PATH.
So How can I use this variable in any TCL file ?

Thanks,
Tushar

---

### Post by stevescripts on 2009-04-01
I *assume* here, that you are talking about setting an environment variable - if so,
it will live in tcl's environment array.

From an interactive tclsh:

```

puts $env(PROJECT_PATH)

```

To get the entire contents of what tcl knows as the environment array:

```

parry env

```

Hope this answers your question?

Steve

---

### Post by tusharv on 2009-04-01
Hi stevescripts,

Yes Your ans satisfies my need.
And regarding your second code ```
parry env
``` I think It should be ```
parray env
```

Thanks,
Tusharv

---

### Post by stevescripts on 2009-04-02
Typo ... duh!:mad:

---

