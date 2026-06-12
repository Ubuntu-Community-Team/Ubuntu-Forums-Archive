---
title: "Bash: Copy files without asking prompt"
date: 2012-03-01
forum: Programming Talk
---

### Post by ryanrio95 on 2012-03-01
Hi.

This is absolutely beginner talk.
But i know that when i use cp -f it doesn't ask me if i want to overwrite.
It just overwrites. But i want to make this command faster by skipping the files that are already existing in the destination directory.
Does anyone know the option to add for this?

Regards.

---

### Post by winh8r on 2012-03-01
enter:


```
man cp
```

for a full list of options when using the cp command with explanations of what each option does.

Hope this helps you

---

### Post by Vaphell on 2012-03-01
maybe this
```
$ cp --help
...
-n, --no-clobber             do not overwrite an existing file (overrides
                                 a previous -i option)
...
```

---

### Post by ryanrio95 on 2012-03-01
Thanks, that should help me out.

---

