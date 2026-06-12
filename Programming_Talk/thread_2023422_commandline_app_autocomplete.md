---
title: "commandline app autocomplete"
date: 2012-07-12
forum: Programming Talk
---

### Post by psychotix on 2012-07-12
Hi,

I'm thinking of creating a commandline utility. As a feature,  I'd like it to be able to autocomplete on argument strings sort of like how bash autocompletes files or directories w/ Tab. 

Is there a library out there that will allow me to do this? By pressing Tab, the utility would give suggestions for a list of options stored in a file.

Thanks,

---

### Post by papibe on 2012-07-12
Hi psychotix.

A practical option is to study the current auto completion scripts. They all reside here:
```
/etc/bash_completion.d
```
Be careful not to modify them, as usually bad autocompletion scripts screw up the terminal experience :D.

Just a thought.
Regards.

---

### Post by Bachstelze on 2012-07-12
That's not at all what he wants though, he wants to have Tab-completion in his program, not in Bash.

---

### Post by lukeiamyourfather on 2012-07-12
The user will have to be running the program already and then give arguments instead of giving them while launching the program. The auto complete in the terminal already is done by the shell, but the shell has no way to know what your arguments are (or their options). Traditionally giving bad arguments just spits back the help.

---

### Post by psychotix on 2012-07-12
I think I'll look at what papibe suggested.

Thanks!

---

