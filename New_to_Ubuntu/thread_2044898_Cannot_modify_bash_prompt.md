---
title: "Cannot modify bash prompt"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by davidlinn on 2012-08-20
I'm trying to make my bash prompt git aware. 

[https://github.com/git/git/blob/master/contrib/completion/git-prompt.sh](https://github.com/git/git/blob/master/contrib/completion/git-prompt.sh)
[https://github.com/git/git/blob/master/contrib/completion/git-completion.bash](https://github.com/git/git/blob/master/contrib/completion/git-completion.bash)

I have copied both these files to my home directory and modified my .bashrc file as mentioned in the file. I did chmod a+x to make the scripts executable and ran exec bash. No changes are happening though. What am I doing wrong ?

---

### Post by The Cog on 2012-08-20
I think you have to log out and in again (out of the GUI) before the change will be picked up.

---

### Post by drmrgd on 2012-08-20
Does sourcing the .bashrc file not work?

```
source ~/.bashrc
```

I'm not sure I know what you mean by running "exec bash", but this is the easiest way to reflect the changes you made to .bashrc without logging out and back in.

---

### Post by davidlinn on 2012-08-20
Nope. No changes are happening. I wonder if there is something wrong in the instructions given.

---

### Post by marlow59 on 2012-08-20
Try this : [http://coffeecoders.de/2011/09/make-your-bash-prompt-git-aware/](http://coffeecoders.de/2011/09/make-your-bash-prompt-git-aware/)

Hope it helps.

---

### Post by davidlinn on 2012-08-20
I'd seen that link. I had the same problem.

I figured it out. Silly mistake really. I was defining PS1 at the beginning of the file while it was getting reassigned later.

---

### Post by ktmom on 2012-09-02
I had to remove the "export" from each line when copying lines into .bashrc.  Place these lines below the 'case "$TERM" ' block.

original ([http://coffeecoders.de/2011/09/make-your-bash-prompt-git-aware/](http://coffeecoders.de/2011/09/make-your-bash-prompt-git-aware/))
```
export GIT_PS1_SHOWDIRTYSTATE=true
export GIT_PS1_SHOWUNTRACKEDFILES=true
export GIT_PS1_SHOWSTASHSTATE=true
export PS1="${PS1::$((${#PS1}-3))}\$(__git_ps1 ' [\[\e[34;1m\]%s\[\e[0m\]]')\$ "
```

to
```
GIT_PS1_SHOWDIRTYSTATE=true
GIT_PS1_SHOWUNTRACKEDFILES=true
GIT_PS1_SHOWSTASHSTATE=true
PS1="${PS1::$((${#PS1}-3))}\$(__git_ps1 ' [\[\e[34;1m\]%s\[\e[0m\]]')\$ "
```

---

