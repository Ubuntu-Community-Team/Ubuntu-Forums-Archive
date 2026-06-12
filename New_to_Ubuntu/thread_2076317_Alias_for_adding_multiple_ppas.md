---
title: "Alias for adding multiple ppas"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by ferhtgoldaraz on 2012-10-25
I'm trying to crate an alias, but can't figure out how to make it work. I've tried to add this to bash_aliases, then sourced .bashrc (the part about bash_aliases is already uncommented):

```
alias addppas="for i in $@; do sudo add-apt-repository -y $1; shift; done"
```

I'm not that good whith bash... The idea is that you would be able to type in:

```
addppas ppa1 ppa2 ...
```

and it would add them all.

Thanks in advance, reference to info is also welcome

---

### Post by ferhtgoldaraz on 2012-10-25
Since bash outputs:

```
bash: syntax error near unexpected token `ppa:ubuntu-wine/ppa'
```

I thought maybe changing $1 to '$1'... Didn't help anything.

I forgot to say this is ubuntu 12.10 x64 in a pretty normal acer.

---

### Post by ferhtgoldaraz on 2012-10-25
I've found out that the position parameters get interpeted when creating the alias, rather than during it's execution, and that I should instead use a function. So I wrote this in .bashrc:

```

# My functions
function addppas() {
  for i in $@
  do
    sudo add-apt-repository -y $1
    shift
  done
}

```

And it doesn't work, but now bash says:
```
bash: syntax error near unexpected token `&'
```

What? :confused:

---

### Post by ferhtgoldaraz on 2012-10-25
I had to close the terminal and reopen it. Some failed attempt of function must have been recorded in that environment.

If any one is interested, here is the working function:

```

addppas ()
{
  for i in $@
  do
    sudo add-apt-repository -y $1
    shift
  done
  sudo apt-get update
}

```

And here are some aliases:

```

alias addppa="sudo add-apt-repository"
alias aptinstall="sudo apt-get install"
alias aptupgrade="sudo apt-get upgrade"
alias aptautoremove="sudo apt-get autoremove"
alias aptupdate="sudo apt-get update"

```

You can copy-paste the function at the end of .bashrc (It's in your home folder, as a hidden file. Run gedit .bashrc from a new terminal, or better yet hit Ctrl + F2 and type it in).

As for the aliases, Ctrl + F2...

```

gedit .bash_aliases

```

Copy-paste them as above, and save. That will let you type in those short words instead of the tedious ones that are between ""s

Self-responded at the end :P

Hope somebody finds this at least a bit useful :)

---

### Post by Vaphell on 2012-10-25
why do you use for loop and shift together? loop will go through all the values either way, you don't need to help it by pushing parameters to the front
```
for i; do sudo add-apt-repository -y $i; done
``` is enough

---

### Post by ferhtgoldaraz on 2012-10-25
Wow, thanks. I don't know almost anything about bash.

Much better!

---

