---
title: "HOWTO Save a few seconds of your life with alias"
date: 2005-11-13
forum: Outdated Tutorials &amp; Tips
---

### Post by closet geek on 2005-11-13
If you're a command line user like myself no doubt the hassle of typing:

```

sudo apt-get install package

```
everytime you want to grab a package causes you strife. Let aliases help.

At a shell simply type:

```

alias apt='sudo apt-get install'
alias remove='sudo apt-get remove'
alias search='apt-cache search'

```
from now on you can simply type:

```

apt package

```
to install a package.

```

remove package

```
to remove a package.

and, you've guessed it:

```

search package

```
to look for a package.

To make these aliases stick add entries for them in your .bashrc or .bash_profile files.

Of coures you don't have to use my shortcuts, perhaps you'd prefer apt-search for search it's up to you such is the power of aliases. It should be noted that 'install' is already a command in Linux hence my choice of 'apt'.

cg

---

### Post by lizardking on 2005-11-13
very useful...

cool!

thnx man!

---

### Post by 23meg on 2005-11-13
To make these permanent you can put the alias lines to your ~/.bash_profile file.

---

### Post by henriquemaia on 2005-11-14
```
alias apt='sudo apt-get install'
alias remove='**sude** apt-get remove'
alias search='apt-cache search'
```

You have an error there. It should be **sudo.** Just for the sake of not misleading Ubuntu newcomers.

Apart from that, great tip. Thanks.

---

### Post by closet geek on 2005-11-14
[QUOTE=henriquemaia]```
alias apt='sudo apt-get install'
alias remove='**sude** apt-get remove'
alias search='apt-cache search'
```

You have an error there. It should be **sudo.** Just for the sake of not misleading Ubuntu newcomers.

Apart from that, great tip. Thanks.[/QUOTE]

Oops! It should be no great suprise I also have:

```

alias sude='sudo'

```

In my bash_profile ](*,) 

cg

---

### Post by escobar on 2005-11-17
[QUOTE=closet geek]If you're a command line user like myself no doubt the hassle of typing:

```

sudo apt-get install package

```
everytime you want to grab a package causes you strife. Let aliases help.

At a shell simply type:

```

alias apt='sudo apt-get install'
alias remove='sudo apt-get remove'
alias search='apt-cache search'

```
from now on you can simply type:

```

apt package

```
to install a package.

```

remove package

```
to remove a package.

and, you've guessed it:

```

search package

```
to look for a package.

To make these aliases stick add entries for them in your .bashrc or .bash_profile files.

Of coures you don't have to use my shortcuts, perhaps you'd prefer apt-search for search it's up to you such is the power of aliases. It should be noted that 'install' is already a command in Linux hence my choice of 'apt'.

cg[/QUOTE]


[QUOTE=closet geek]If you're a command line user like myself no doubt the hassle of typing:

```

sudo apt-get install package

```
everytime you want to grab a package causes you strife. Let aliases help.

At a shell simply type:

```

alias apt='sudo apt-get install'
alias remove='sudo apt-get remove'
alias search='apt-cache search'

```
from now on you can simply type:

```

apt package

```
to install a package.

```

remove package

```
to remove a package.

and, you've guessed it:

```

search package

```
to look for a package.

To make these aliases stick add entries for them in your .bashrc or .bash_profile files.

Of coures you don't have to use my shortcuts, perhaps you'd prefer apt-search for search it's up to you such is the power of aliases. It should be noted that 'install' is already a command in Linux hence my choice of 'apt'.

cg[/QUOTE]

I think I missed something. I can use the aliases after entering them into terminal, but they no longer work after reboot. Here's my .bash profile:

# .bash_profile
alias purge='sudo aptitude purge'
alias apt='sudo apt-get install'
alias edit='sudo gedit'

# Get the aliases and functions
if [ -f ~/.bashrc ]; then
	. ~/.bashrc
fi


# User specific environment and startup programs

PATH=$PATH:$HOME/bin

export PATH
unset USERNAME

-Keep in mind I added my aliases under EVERY section of this file. When I try running any of them (ex. purge gedit) I get 'command not found'. Can someone post theirs to compare?

---

### Post by souled on 2005-11-18
Hmmm... try this method. ```
gedit .bashrc
``` Then find this section ```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#   . ~/.bash_aliases
#fi

```

Uncomment (erase the #) the last three lines of that section. Then do ```
gedit .bash_aliases
``` and add your aliases to that file there. Then type ```
 bash
``` to restart bash and make it read your new aliases.

---

### Post by escobar on 2005-11-19
[QUOTE=souled]Hmmm... try this method. ```
gedit .bashrc
``` Then find this section ```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

#if [ -f ~/.bash_aliases ]; then
#   . ~/.bash_aliases
#fi

```

Uncomment (erase the #) the last three lines of that section. Then do ```
gedit .bash_aliases
``` and add your aliases to that file there. Then type ```
 bash
``` to restart bash and make it read your new aliases.[/QUOTE]

Hmm, 'gedit .bashrc' pulls up:

# .bashrc

# User specific aliases and functions

# Source global definitions
if [ -f /etc/bashrc ]; then
	. /etc/bashrc
fi

Doesn't seem to match your instructions. I'm guessing I missed something else? Thanks for your help so far.

---

### Post by escobar on 2005-11-21
[QUOTE=escobar]Hmm, 'gedit .bashrc' pulls up:

# .bashrc

# User specific aliases and functions

# Source global definitions
if [ -f /etc/bashrc ]; then
	. /etc/bashrc
fi

Doesn't seem to match your instructions. I'm guessing I missed something else? Thanks for your help so far.[/QUOTE]

*bump*

---

### Post by souled on 2005-11-21
I'm pretty sure you can add those three lines to your .bashrc that I had.

Or just add the whole section, just uncomment the last three lines. Leave the description commented if you decide to put it in your .bashrc.

---

### Post by escobar on 2005-11-21
[QUOTE=souled]I'm pretty sure you can add those three lines to your .bashrc that I had.

Or just add the whole section, just uncomment the last three lines. Leave the description commented if you decide to put it in your .bashrc.[/QUOTE]


I really hate coming off like I'm slow but part of my problem was adding my aliases under ANY of these lines didn't work. I'll try again when I get home to be sure though. Thanks again.

---

### Post by bwog on 2005-11-24
What happens when you want to install the package called apt?

Anyway, aliases can be tricky, especially when sudo is in the alias or in as part of a command using sudo.

---

### Post by bcrow on 2005-11-25
Why not use aptitude in the alias instead of apt-get? Aptitude keeps track of which packagse are installed merely as dependencies, and when you remove the original package with aptitude remove, it removes the packages you don't need as well. Much better than having to unclutter ocasionally with deborphan or something.

---

### Post by oskude on 2005-11-25
[QUOTE=bcrow]Why not use aptitude in the alias instead of apt-get? Aptitude keeps track of which packagse are installed merely as dependencies, and when you remove the original package with aptitude remove, it removes the packages you don't need as well. Much better than having to unclutter ocasionally with deborphan or something.[/QUOTE]and i thought aptitude is just a front-end for apt-get... may i remove apt-get and make a link from aptitude to apt-get ;)

---

### Post by yesplease on 2005-11-25
I think that Synaptic is the best, it gives you a lot of info on the packages, dependent packages and recomended packages.

Bwog's post was about the dangers of aliasses, not about the package manager.

---

### Post by angrykeyboarder on 2005-11-25
[quote=closet geek]

```

alias apt='sudo apt-get install'
alias remove='sudo apt-get remove'
alias search='apt-cache search'

``` [/quote] 
I've been doing this for quite some time now. But extra-lazy person that I am, mine are:

```
alias agi='sudo apt-get install'
alias agr='sudo apt-get remove'
alias acs='apt-cache search'
alias agu='sudo apt-get update'
alias agg='sudo apt-get upgrade'
```

---

### Post by escobar on 2005-11-26
[QUOTE=escobar]I really hate coming off like I'm slow but part of my problem was adding my aliases under ANY of these lines didn't work. I'll try again when I get home to be sure though. Thanks again.[/QUOTE]

Here's my bash.rc file:

[I]#.bashrc

#User specific aliases and functions
alias purge='sudo aptitude purge'
alias apt='sudo apt-get install'
alias edit='sudo gedit'
alias sources.list='/etc/apt/sources.list'
alias grub.lst=/boot/grub/menu.lst

# Source global definitions
if [ -f /etc/bashrc ]; then
	. /etc/bashrc
fi[/I]

It seemed to work fine after saving it then typing "bash" into terminal. Nothing else was required. Not sure what I was doing wrong. Thanks everyone.

---

### Post by The Beast. on 2008-05-08
Thanks!!! I was really struggling with aliases. Now I got it working..............

---

### Post by BoHu on 2009-01-04
alias icanhas='sudo apt-get install'

---

