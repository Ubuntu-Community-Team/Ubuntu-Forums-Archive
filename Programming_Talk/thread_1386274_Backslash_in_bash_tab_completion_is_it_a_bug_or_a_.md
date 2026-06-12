---
title: "Backslash in bash tab completion: is it a bug or a feature?"
date: 2010-01-20
forum: Programming Talk
---

### Post by MeMooMeM on 2010-01-20
Hi everyone,

Try this:

cd $

and hit Tab. This causes a blackslash to appear before the dollar sign, which is really annoying, especially when trying to change directory to a folder name that is kept as an environmental variable, e.g. $THEFOLDERFOO.

Any ideas to disable this? Is this really necessary for reasons that I cannot think of? Thanks!

---

### Post by Simian Man on 2010-01-20
> **MeMooMeM said:**
> Any ideas to disable this? Is this really necessary for reasons that I cannot think of?

Use ZSH instead?

---

### Post by wmcbrine on 2010-01-20
I'm not getting a backslash.

---

### Post by MadCow108 on 2010-01-20
it must be configurable somewhere
it occurs on a machine at work with bash 3.1 but not on another one with 3.0
and not on my home pc with 4.0

but I'm to lazy to look up where to change it :)

---

### Post by sinbadbuddha on 2010-01-20
When I tried it, it output a list of environment variables, as expected. You might want to update bash, though. Still, I can't think for the life of me why this would be a problem.

Anyway, I wouldn't call it a bug; it is just the way your version of bash does tab completion, i.e it completes file names, unescaped '$' signs are not allowed in files, so it escapes special characters before searching for them, and although not finding any files beginning with '$' in the path, it 'completes' anyway.

---

