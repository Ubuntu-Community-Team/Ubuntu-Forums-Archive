---
title: "alias disappears"
date: 2013-03-13
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-03-13
I run lxde in lubuntu and my terminal is LXTerminal 0.1.11

I created some aliases, but when I close the terminal then reopen it, they have disappeared and I have to create them again.

Is this normal? How can I make them permanent?

---

### Post by Impavidus on 2013-03-13
Yes, that's normal. You can make them permanent by putting them in your **.bashrc** file (or, as in my case, in a file included by the .bashrc file). My **.bashrc** contains```

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```which is there by default. My **.bash_aliases** contains the actual alias definitions:```

alias ll='ls --color=auto -l'
alias la='ls --color=auto -a'
alias lal='ls --color=auto -al'
alias ls='ls --color=auto'

```
These files are in your home directory, but they are hidden. You can see them in nautilis after you hit ctrl-h.

---

### Post by sudodus on 2013-03-13
> **Kevin McCready said:**
> I run lxde in lubuntu and my terminal is LXTerminal 0.1.11

I created some aliases, but when I close the terminal then reopen it, they have disappeared and I have to create them again.

Is this normal? How can I make them permanent?

Yes, this is normal. You can make them persistent by entering them into your .bashrc file

```
leafpad /home/$USER/.bashrc
```

I suggest that you add the lines for the aliases near (right after) the already existing aliases.

run ```
source /home/$USER/.bashrc
``` to get the aliases into an open terminal. New terminal windows will get the aliases automatically. You can find your old (wiped) aliases in your terminal window with the arrow-up key (repeatedly) or with this command
```
history | grep alias
```
and cut and paste them into your editor for .bashrc

---

### Post by Kevin McCready on 2013-03-13
Great. Thanks so much again!

---

