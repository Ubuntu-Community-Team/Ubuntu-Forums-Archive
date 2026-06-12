---
title: "Git Alias Setting"
date: 2010-04-29
forum: Programming Talk
---

### Post by huangyingw on 2010-04-29
Hello,
	I am a git fans.
	And as a super lazy man, I have updated the $HOME/.gitconfig file as bellow:
	```

	ad = add
	bi = bisect
	br = branch
	bra = branch -a
	ci = commit -am
	
```
	But with this configuration, for example, if I need to do a commit,I still need to type the following
	 command:
	```

	git ci "my message"
	
```
	I want a shorter one, I don't like to type git, instead I like following:
	```

	gci "my message"
	
```
	So I try this line in $HOME/.gitconfig
	```

	gci = git commit -am
	
```
	But this does not work.
	Could someone tell me how to shorten this?

---

### Post by the_unforgiven on 2010-04-29
You could do that with bash aliasing:
```
$ alias gci='git commit -am'
```
For more info, consult [bash manual]("http://www.gnu.org/software/bash/manual/bashref.html#index-alias-128").

---

### Post by huangyingw on 2010-04-29
> **the_unforgiven said:**
> You could do that with bash aliasing:
```
$ alias gci='git commit -am'
```
For more info, consult [bash manual]("http://www.gnu.org/software/bash/manual/bashref.html#index-alias-128").
Thanks, I have tried this. But it does not work after rebooting. Is there a permanent way, or configuration file where could permanently update this?

---

### Post by the_unforgiven on 2010-04-29
> **huangyingw said:**
> Thanks, I have tried this. But it does not work after rebooting. Is there a permanent way, or configuration file where could permanently update this?
You could put them in normal $HOME/.bashrc script or source some other file from it.
For example, here is part of my .bashrc:
```

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

```

---

### Post by huangyingw on 2010-04-30
> **the_unforgiven said:**
> You could put them in normal $HOME/.bashrc script or source some other file from it.
For example, here is part of my .bashrc:
```

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

```
Oh yes, what I like is this. Great news.

---

