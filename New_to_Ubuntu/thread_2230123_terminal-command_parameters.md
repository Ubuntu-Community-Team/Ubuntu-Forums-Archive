---
title: "terminal-command parameters"
date: 2014-06-17
forum: New to Ubuntu
---

### Post by hill0093 on 2014-06-17
In MS Windows command window one types e.g.:
dir /?
ls /?
etc
to get a display of parameters for the command.
What is similar in ubuntu?

---

### Post by Lars Noodén on 2014-06-17
For any program you can look at the built-in manual page using [man](https://help.ubuntu.com/community/man) and get a quick summary of the options.

```

man ls
man sudo

```

If the page is well-written you get the general parameters at the top and more details, including example usage, as you scroll down.  The pages vary in quality though.

---

### Post by steeldriver on 2014-06-17
Many commands have a --help option to provide basic usage information (usually much less detailed than the full manpage)

```

ls --help

```

For bash shell builtins, the equivalent is help in front of the command e.g.

```

help help
help: help [-dms] [pattern ...]
    Display information about builtin commands.

```

---

