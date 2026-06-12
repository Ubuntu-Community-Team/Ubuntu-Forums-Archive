---
title: "[*buntu 13.04] Aliases forgotten after terminal close"
date: 2013-09-13
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2013-09-13
Hello all!

I have made a set of aliases that I would like to implement. However when I try:

```
alias "quit"="exit"
```

it works:)! Until I try the command again by opening another terminal:(:

```
-@-$ quit
No command 'quit' found, did you mean:
 Command 'qgit' from package 'qgit' (universe)
 Command 'quilt' from package 'quilt' (main)
 Command 'quiz' from package 'bsdgames' (universe)
 Command 'luit' from package 'x11-utils' (main)
 Command 'quot' from package 'quota' (main)
quit: command not found
-@-:~$ 
```

How can I make the alias permanent?

---

### Post by sisco311 on 2013-09-13
Just put them in your ~/.bashrc file. Or you could create a separate file for your aliases and source it in ~/.bashrc

 I keep my aliases in ~/.bash_aliases and use the following line in my ~/.bashrc file to source it:
 ```
[ -f "$HOME/.bash_aliases" ] && . "$HOME/.bash_aliases"
```

---

### Post by whitesmith on 2013-09-13
It works fine on my 12.04 LTS. Perhaps Raring has a regression with respect to 12.04 LTS. Edit with note to Sisco's posting: I don't use files for aliases, since mine are usually ephemeral. That could be the difference.

---

### Post by Jonathan Precise on 2013-09-13
> **sisco311 said:**
> Just put them in your ~/.bash_aliases and use the following line in your ~/bashrc file to source it:
```
[ -f ~/.bash_aliases ] && . ~/.bash_aliases
```

Would this work:

```
"quit"="exit"
```

as a [FONT=courier new].bash_aliases[/FONT] file?

PS. Thank you!

---

### Post by Jonathan Precise on 2013-09-13
> **whitesmith said:**
> It works fine on my 12.04 LTS. Perhaps Raring has a regression with respect to 12.04 LTS.

I used to have ubuntu-12.04-LTS and it worked! Just curious why 13.04 (the one I now use) has this?

---

### Post by sisco311 on 2013-09-13
Nope you have to use the `alias' keyword:
```
alias quit='exit'
```

Here is the content of my bash_aliases file:
```

alias ll='ls -ahl'
alias la='ls -a'

alias ..='cd ..'
alias ...='cd ../..'

alias grep='grep --color=auto'

alias top='htop'

alias xs='cd'
alias vf='cd'
alias cdx='cd ~/xtmp'
alias cda='cd /home/apps'
alias cdt='cd ~/torrent'

alias pacman='pacman'
alias s='sudo pacman -S'
alias r='sudo pacman -R'
alias rns='sudo pacman -Rns'
alias syu='sudo pacman -Syu'
alias ss='pacman -Ss'
alias su='sudo pacman -Su'

alias ping='ping -v'

alias q='exit'
alias e='exit'

alias m='mousepad'
alias n='nano'
alias nb='nano ~/files/bash'

alias f='cat ~/files/forum'

alias punk='mplayer -really-quiet http://65.60.32.242:8600 < /dev/null &'

alias a='adb shell busybox'

alias ntp='sudo ntpd -qg'
```

---

### Post by Dennis N on 2013-09-13
Any alias you define in the terminal is lost when you close the terminal. To retain them you put your alias definitions in a file which is read each time the terminal is started.

Two possibilities:

I put all alias definitions into **~/.bash_aliases**. If this file doesn't already exist, create it. It is just a text file.

Example:

```
#Roxanne's Alias File
#bash_aliases is run each time the terminal is started

alias dosgames='dosbox /home/dn/dosgames/'
alias tcv='dosbox /home/dn/dosgames/TCV/COVE.EXE'
alias brix='dosbox /home/dn/dosgames/brix/BRIX1.EXE'
alias chess='dosbox /home/dn/dosgames/chess/GMCHESS.EXE'
alias castle='dosbox /home/dn/dosgames/brain/BRAIN.EXE'

```

Some people put them into ~/.bashrc instead.

---

### Post by Jonathan Precise on 2013-09-13
Thank you Dennis N and sisco311!
[I]Now marked as [solved]!
Edit: Now marked as unsolved due to confusion.
Edit: Now marked as [solved] due to clarification.[/I]

---

### Post by Jonathan Precise on 2013-09-13
> **sisco311 said:**
> I use the following line in my ~/.bashrc file to source it:
 ```
[ -f "$HOME/.bash_aliases" ] && . "$HOME/.bash_aliases"
```

Does this work:

```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

---

### Post by sisco311 on 2013-09-13
> **Jonathan Precise said:**
> Does this work:

```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

Yes, they do the same thing.

EDIT: Oh, I see, if it exists, ~/.bash_aliases is sourced in Ubuntu's default .bashrc file.

---

### Post by Jonathan Precise on 2013-09-13
> **sisco311 said:**
> Yes, they do the same thing.

Ok thank you!

---

