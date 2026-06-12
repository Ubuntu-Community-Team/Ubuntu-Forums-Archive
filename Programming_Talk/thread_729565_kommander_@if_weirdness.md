---
title: "kommander @if weirdness"
date: 2008-03-20
forum: Programming Talk
---

### Post by cesera on 2008-03-20
If I run this code in kommander:

```
@if(@Answer.text != @env(C2M_EN_TEXT))
   echo "different"
@endif
@if(@Answer.text == @env(C2M_EN_TEXT))
   echo "same"
@endif
```

it prints both 'different' and 'same', I have not idea why this is happening, how can two strings be different yet the same?

If anyone can help me out here I would greatly appreciate it.

-------------------

Running Kommander 1.2.1 on KDE 3.5.6

---

### Post by mike_g on 2008-03-20
I never even heard of kommander, so I'm probably wrong here, but it may be possible that the language does not do string comparisons with == operators. Maybe you need to call a function or something (like you would strcmp in C)???

---

### Post by cesera on 2008-03-20
> **mike_g said:**
> I never even heard of kommander, so I'm probably wrong here, but it may be possible that the language does not do string comparisons with == operators. Maybe you need to call a function or something (like you would strcmp in C)???
 Kommander is a utility to very easily build a gui interface to applications in kde. It does have a @String.compare function, but that give exactly the same result.

---

