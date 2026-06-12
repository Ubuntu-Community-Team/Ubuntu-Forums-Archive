---
title: "Shell issues &quot;&gt;&quot;, What does it want"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Ralph L on 2008-10-03
I don't really understand how to use terminal and bash.  Sometimes when I type in a command, it comes back with >.  I expect that I didn't put enough parameters in the command when I typed it, but I don't know.  Would somebody explain this to me.

Example:
ralph@ralph-laptop:~$ gnome-eject "DOTTIE'S IP"
> 

What do I do now?  Also, is there any documentation that explains this.  I couldn't find any.

Thanks

Ralph

---

### Post by kylet450 on 2008-10-03
Sometimes it does that if the command is taking a long time.

It happens if you do: wine cmd

>
>
>

But your not trying to do that.

Try and retype it after the >
Or leave the terminal open to see what it happens.

Best that i could do mate - sorry.

---

### Post by bhadotia on 2008-10-03
This usually means a command prompt for the command you typed.
You can learn bash [here]("http://linuxcommand.org/")- I'm doing the same:D

---

### Post by bodhi.zazen on 2008-10-03
In general the prompt is waiting for additional information from you.

[http://www.davidpashley.com/articles/bash-prompts.html](http://www.davidpashley.com/articles/bash-prompts.html)

For example, you may continue a long line with a \

or if you forgot to close your quotes

gnome-eject "DOTTIE'S IP

without the closing quote

will give you the PS2, which be default is >

type " to continue ...

[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

---

### Post by nowshining on 2008-10-03
this also happends if maybe u put an extra space a slash, etc.. or something other after the command, etc.. or as others suggested it's awaiting for more commands from u...

---

### Post by bhadotia on 2008-10-03
> **bodhi.zazen said:**
> In general the prompt is waiting for additional information from you.

[http://www.davidpashley.com/articles/bash-prompts.html](http://www.davidpashley.com/articles/bash-prompts.html)

For example, you may continue a long line with a \

or if you forgot to close your quotes

gnome-eject "DOTTIE'S IP

without the closing quote

will give you the PS2, which be default is >

type " to continue ...

[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)
Thanks for the informative links.:D

---

### Post by bodhi.zazen on 2008-10-03
> **bhadotia said:**
> Thanks for the informative links.:D

You are most welcome ;)

---

