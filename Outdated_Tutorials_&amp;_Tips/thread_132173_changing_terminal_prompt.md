---
title: "changing terminal prompt"
date: 2006-02-17
forum: Outdated Tutorials &amp; Tips
---

### Post by lmellen on 2006-02-17
:-k  Does anybody know how to change the value of the variable "h" in:

    " PS1='${debian_chroot:+($debian_chroot)}\u@\h\w\$ ' "

This is the code for the terminal prompt in .bashrc.
It's no big deal but if I can shorten my prompt I'd like to. 
I'd also simply like to know how.

export PS1=    only changes the prompt for one session.
                                  Thanks -- larry

---

### Post by lmellen on 2006-02-18
Never mind, all that is necessary is to change:
           " PS1='${debian_chroot:+($debian_chroot)}\u@\h\w\$ ' "
   to
             PS1= "anything you want"   
Change it in .bashrc
Thanks cwaldbieser!!!!   --Larry

---

### Post by pt78 on 2006-02-19
[QUOTE=lmellen]:-k  Does anybody know how to change the value of the variable "h" in:

    " PS1='${debian_chroot:+($debian_chroot)}\u@\h\w\$ ' "

This is the code for the terminal prompt in .bashrc.
It's no big deal but if I can shorten my prompt I'd like to. 
I'd also simply like to know how.

export PS1=    only changes the prompt for one session.
                                  Thanks -- larry[/QUOTE]
Here is huge howto: [http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/)
And here bunch of examples: [http://www.dreaming.org/~giles/bashprompt/prompts/](http://www.dreaming.org/~giles/bashprompt/prompts/)

---

