---
title: "Bash alias expansion"
date: 2008-08-15
forum: Programming Talk
---

### Post by joesmoe10 on 2008-08-15
Hey, I want to alias long directory paths that I use frequently.

So in my ~/.bash_aliases I have something like this
```
alias longpath='~/really/long/path'
```

Then I want to be able to use this alias with commands like cd or mv but the alias doesn't get expanded and bash spits out an error
```
cd longpath
bash: cd: longpath: No such file or directory
```

How can I get bash to expand the aliases I make?

---

### Post by kailden on 2008-08-15
I do alias longpath='cd ~/really/long/path'
and then just type longpath instead of cd at the shellprompt.
YMMV.

You could also do an export LONGPATH="/home/kailden/really/long/path"
and do a cd $LONGPATH at the shellprompt, but I think then that anything like the ~ character won't get expanded...

---

### Post by Reiger on 2008-08-15
No but IIRC the tilde (~) can be replaced with $HOME ...

---

### Post by joesmoe10 on 2008-08-15
I used to include the cd in the alias like so
```
alias longpath='cd ~/really/long/path'
```

but then you can't use it for other commands like this
```
mv file longpath
```

---

### Post by mssever on 2008-08-15
You could use a bash function. Here's a start, but it's missing something. It strips out the first directory of genuine directories. Perhaps someone can spot what I'm missing.
```
function cd {
  local target="$1"
  
  local longpath1=/some/long/path
  local longpath2=/some/other/path
  
  local cmd="$(eval echo "\"\$$target\"")"
  [[ $cmd =~ ^\$ ]] && cmd="${cmd:1}"
  if [ -z "$cmd" ]; then
    builtin cd "$cmd"
  else
    builtin cd "$cmd"
  fi
  return $?
}
```

---

### Post by jinksys on 2008-08-15
You are confusing aliases with variables.

Aliases are essentially commands.

For example:

```

alias corndog='mkdir delicious'

$> corndog <--- this will be subsituted with *mkdir delicious*


```

You want variables...

```

gohome="cd $HOME/"

$> $gohome  <--- will be substituted for /home/username/

$/home/wally> _

```

Once you've crafted the variable you need, you can put it in your ~/.bashrc config file and it'll be saved for future bash sessions.

```

Make sure you export it:

export MYVAR="whatever it does"


```

Bash programming Howtos:

Beginner: [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
Advanced: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by joesmoe10 on 2008-08-16
I think I found the problem from the man pages for alias

"aliases allow a string to be substituted for a word when it is used as the **first** word of a simple command"

Anyway, thanks for the help

---

### Post by K7522 on 2008-08-16
I'm glad you found your issue joesmoe10, as for me... I just found out how to go to my /really/long/stupidly/crazy/boring with spaces/hArd/to TYpE/places.

Thank you all!

---

### Post by mssever on 2008-08-17
> **K7522 said:**
> I'm glad you found your issue joesmoe10, as for me... I just found out how to go to my /really/long/stupidly/crazy/boring with spaces/hArd/to TYpE/places.

Thank you all!
I assume that you know about tab completion. I tend to use long filenames, with plenty of spaces and other special characters. Since I use tab completion, I rarely have to actually type those names in full.

---

### Post by dtmilano on 2008-08-18
CDPATH bash environement variable would also be helpful in some cases. Check 'man bash'.

---

