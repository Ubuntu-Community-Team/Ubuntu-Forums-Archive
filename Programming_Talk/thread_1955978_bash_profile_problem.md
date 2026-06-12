---
title: "bash profile problem"
date: 2012-04-10
forum: Programming Talk
---

### Post by Nikolazigic on 2012-04-10
I am trying to add matlab but I have problems.
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:/usr/local/MATLAB/R2011a/bin$PATH"
export PATH=$PATH
fi
What is wrong?

---

### Post by r-senior on 2012-04-10
> **Nikolazigic said:**
> I am trying to add matlab but I have problems.
```
[COLOR="Gray"]if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
    . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:/usr/local/MATLAB/R2011a/bin**[COLOR="Red"]:[/COLOR]**$PATH"
export PATH=$PATH
fi[/COLOR]
```
What is wrong?
Missing a colon in the path? I've added it in red

---

### Post by Nikolazigic on 2012-04-10
Thanks.

---

### Post by Vaphell on 2012-04-10
i'd add that you put that in the wrong place, that part is only executed only when $HOME/bin directory exists. If you have it, your path will work, if not - guess what ;-)
you should leave it as it was before and write a second line adding your custom path to PATH outside if-fi block, together with export moved from if-fi.

---

