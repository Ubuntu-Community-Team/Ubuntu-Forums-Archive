---
title: "alias hostname on console"
date: 2013-04-06
forum: Programming Talk
---

### Post by Lee_Machine on 2013-04-06
So I'm changing hostnames on my servers but I would like to have the old hostname be displayed at the BASH prompt, ie username@hostname. I've tried defining this in both the local bashrc file as well as the gobal. The same goes for the local and global bash_profile files. Any ideas?

Something like this seems to be on the right track, but I cannot get the syntax to work.


```

HOST= hostname
PROMPT_COMMAND='printf "\033]0;%s@%s:%s\007" "${USER}" "${HOST%%*}" "${PWD}"'

```

Thanks for the help.

---

### Post by r-senior on 2013-04-06
I'm going to assume Bash shell. 

Did you try using PS1?

*~/.bashrc*
```

...

export HOST="oldhostname"
export PS1="\u@$HOST:\w$ "
```

You can also include non-printing characters in PS1; refer to the section entitled PROMPTING in the Bash manual page.

---

### Post by ofnuts on 2013-04-06
If you just want it displayed; hardcode it in PS1:
```

PS1="\u@old.host.name:\w$ "

```

---

### Post by Lee_Machine on 2013-04-06
> **r-senior said:**
> I'm going to assume Bash shell. 

Did you try using PS1?

*~/.bashrc*
```

...

export HOST="oldhostname"
export PS1="\u@$HOST:\w$ "
```

You can also include non-printing characters in PS1; refer to the section entitled PROMPTING in the Bash manual page.


Thank you! That worked :)

---

