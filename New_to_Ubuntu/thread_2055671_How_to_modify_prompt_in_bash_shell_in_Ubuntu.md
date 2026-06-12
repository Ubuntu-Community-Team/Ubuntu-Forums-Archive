---
title: "How to modify prompt in bash shell in Ubuntu?"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by Cor. Dunn on 2012-09-09
Hi All,

So I recently started learning Ubuntu and playing with the terminal (I'm using Unix Power Tools, is it a good book?), and I'm stuck on the first thing that I got to ,which is to modify the prompt of the shell.

I typed

$ echo $SHELL

and

$ printenv SHELL

just to make sure I did indeed have bash shell. The tutorial I found online told me that, for example, to modify the prompt, all you have to do is type:

PS1 = "NEW PROMPT : "

but when I did that, it would say PS1: command not found. 

I'm kind of frustrated, I'm at it for two days now, any help?

Thanks

---

### Post by Bashing-om on 2012-09-09
Cor. Dunn;

  Hi ! ...

Here is a tutorial that should prove useful:
[http://ubuntuforums.org/showthread.php?t=31247](http://ubuntuforums.org/showthread.php?t=31247)

IRT your last ... I expect that the leading "$" is a place holder indicating a general prompt (not to be entered on your command line prompt) ... The first command I tried and I got no output to terminal either.
 printenv SHELL: returns /bin/bash on my system (notice no leading "$").

[INDENT]HTH <==BDQ
[/INDENT]

---

### Post by sandyd on 2012-09-09
> **Cor. Dunn said:**
> Hi All,

So I recently started learning Ubuntu and playing with the terminal (I'm using Unix Power Tools, is it a good book?), and I'm stuck on the first thing that I got to ,which is to modify the prompt of the shell.

I typed

$ echo $SHELL

and

$ printenv SHELL

just to make sure I did indeed have bash shell. The tutorial I found online told me that, for example, to modify the prompt, all you have to do is type:

PS1 = "NEW PROMPT : "

but when I did that, it would say PS1: command not found. 

I'm kind of frustrated, I'm at it for two days now, any help?

Thanks

Stop putting spaces in between the '=' and the new prompt

i.e.
```

PS1="NEW PROMPT : "

```

Now, I have to kill this tty just to get rid of the new prompt...

Just a fun note - You can do something like
```

PS1=$PS1" (Laptop) :"
```

And $PS1 will display the original command prompt.
Will output something like
```

sandy@sandyd-laptop (Laptop):
```
And if I change directories...
```

sandy@sandyd-laptop:~/Documents (Laptop):
```

---

### Post by Cheesemill on 2012-09-10
Some examples for you:

[http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/c141.html](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/c141.html)
[https://bbs.archlinux.org/viewtopic.php?id=50885](https://bbs.archlinux.org/viewtopic.php?id=50885)

---

