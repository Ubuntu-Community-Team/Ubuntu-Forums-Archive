---
title: "how to make alias permenant"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by wilson888888888 on 2012-03-14
i used the alias command to shorten some long commands im too lazy to type:
alias chrome='google-chrome'
but whenever i close the terminal all the aliass i made are cleared. How do i make them permanent?

---

### Post by jerome1232 on 2012-03-14
Put them in ~/.bash_aliases, you may need to create the file.

---

### Post by papibe on 2012-03-14
Hi wilson888888888. Welcome to the forums!

Personal alias are store on the file .bashrc or .bash_aliases right in your home directory. You can also reference it like this ~/.bashrc

The regular 'ls' does not show it on the directory, as files that start with a dot are hidden from regular listing. Also nautilus (the file manager) won't show it unless you go into 'View -> Show Hidden Files' (or just press Ctrl+H).

I would advice you to first make a copy of the file (just to be extra safe):
```
cp .bashrc .bashrc.old
```
Then edit the file by doing:
```
gedit .bashrc
```
There, the best place to add your alias is right below the section that says:
```
# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

```
I hope that helps, and tell us how it goes.
Regards.

---

### Post by wilson888888888 on 2012-03-14
i added the aliases in the .bashrc like this:
# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'
alias chrome='google-chrome'
alias earth='google-earth'
but the commands still don't work, and they don't show up in the list when I use the alias command

---

### Post by matt_symes on 2012-03-14
Hi

Close the terminal and reopen it. This will re-read your ~/.bashrc file.

You can also source it, if you don't want to close the terminal.

```
source ~/.bashrc
```

Kind regards

---

### Post by wilson888888888 on 2012-03-14
thanks for the help! now everything works

---

