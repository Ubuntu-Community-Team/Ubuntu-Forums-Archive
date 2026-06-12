---
title: "zsh: pass named parameter to script"
date: 2013-04-16
forum: Programming Talk
---

### Post by kkjaergaard on 2013-04-16
I want to run my zsh script something like this:

```
./myscript.sh -w some-text -m some-other-text
```

I then want to get the information in the -w and -m parameter, just like most other unix programs. The syntax of the script execution is not important, but the named reference to parameters is. Is there an easy way to do so in zsh?

BTW: What is this thing called?

---

### Post by steeldriver on 2013-04-16
It's usually called 'getopts' or 'getopt' - I don't use zsh myself but it appears to have a builtin version - see

```
man zshbuiltins
```

---

### Post by kkjaergaard on 2013-04-16
Thanks, just what I was looking for.

---

