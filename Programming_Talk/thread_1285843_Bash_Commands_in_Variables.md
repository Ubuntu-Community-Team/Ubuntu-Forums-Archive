---
title: "Bash Commands in Variables"
date: 2009-10-08
forum: Programming Talk
---

### Post by Hase on 2009-10-08
I'm being stupid here.  Maybe just tired.  Anyone help?

```
aaron@corona ~/code$ cat up
#! /bin/bash
COMMAND='sudo aptitude update && sudo aptitude safe-upgrade'
echo "$COMMAND"
$COMMAND

```

I'm sure it's something simple, it's just not coming to me and Googling hasn't been fruitful.

Results in:
```
aaron@corona ~/code$ up
sudo aptitude update && sudo aptitude safe-upgrade
/usr/local/bin/up: line 4: sudo aptitude update && sudo aptitude safe-upgrade: command not found

```

---

### Post by Hase on 2009-10-17
Okay. Double quotes mostly works.

```
aaron@corona ~/code$ cat up
#! /bin/bash
COMMAND=[COLOR="Red"]"[/COLOR]sudo aptitude update && sudo aptitude safe-upgrade[COLOR="Red"]"[/COLOR]
echo "$COMMAND"
$COMMAND
```

But it still doesn't like the "&&".  Anyone?

```
aaron@corona ~$ up
sudo aptitude update && sudo aptitude safe-upgrade
E: The update command takes no arguments

```

---

### Post by m_duck on 2009-10-17
I'm not sure about the bash command in a variable, but you could achieve the same using an alias. Edit ~/.bashrc and add:```
alias up='sudo apt-get update && sudo apt-get upgrade'
```Then source ~/.bashrc so it updates the alias```
source ~/.bashrc
```From then on you should be able to call ***up*** and it will run that command.

Apologies if you were just wanting to be able to do it in bash - I can't help in that respect.

---

### Post by Hase on 2009-10-17
Thanks for the suggestion.  I use several aliai (:confused:) currently.  This is kind of just an exercise and has a little more portability.

---

### Post by lswb on 2009-10-17
Try 

eval $command

In your example everything after the first "aptitude" command is being passed as arguements to "aptitude" rather than being evaluated by the shell. When "eval" is used all arguments are passed to the shell for evaluation.

---

### Post by Hase on 2009-10-17
> **lswb said:**
> Try 

eval $command

In your example everything after the first "aptitude" command is being passed as arguements to "aptitude" rather than being evaluated by the shell. When "eval" is used all arguments are passed to the shell for evaluation.

Aha!  Perfect!  I was not familiar with that but solved it all.  Thank you much!

---

