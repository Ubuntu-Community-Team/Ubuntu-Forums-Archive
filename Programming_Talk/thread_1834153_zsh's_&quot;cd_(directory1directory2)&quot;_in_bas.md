---
title: "zsh's &quot;cd (directory1|directory2)&quot; in bash"
date: 2011-08-27
forum: Programming Talk
---

### Post by Intrepid Ibex on 2011-08-27
Hey,

How do you do this Zsh's "cd to any of the listed directories" feature in Bash?:
```
cd (directory1|directory2)
```

Because Bash doesn't like it:
```
bash: syntax error near unexpected token `('
```

Thanks for your time,
Intrepid Ibex

---

### Post by apollothethird on 2011-08-27
> **Intrepid Ibex said:**
> Hey,

How do you do this Zsh's "cd to any of the listed directories" feature in Bash?:
```
cd (directory1|directory2)
```Because Bash doesn't like it:
```
bash: syntax error near unexpected token `('
```Thanks for your time,
Intrepid Ibex

Can you elaborate on the objective.  If I knew the expected outcome I'm sure I'd understand better what it's not doing correctly.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by sisco311 on 2011-08-27
You have to enable extglob:
```

shopt -s extglob
cd @(directory1|directory2)

```

See: `man bash | less +/extglob'

---

### Post by Intrepid Ibex on 2011-08-28
> **sisco311 said:**
> You have to enable extglob:
```

shopt -s extglob
cd @(directory1|directory2)

```

See: `man bash | less +/extglob'
Wow. Thanks.

Have a Mario Star: :KS

---

