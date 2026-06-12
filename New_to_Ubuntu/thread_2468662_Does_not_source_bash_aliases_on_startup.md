---
title: "Does not source bash_aliases on startup"
date: 2021-11-07
forum: New to Ubuntu
---

### Post by tokacp on 2021-11-07
Hi guys, I've created bash_aliases file in my home dir. Then I've added the following script into bash_rc, which was supposed to source the bash_aliases on startup of the system. Unfortunately this doesn't happen. Everytime I need to do source .bash_aliases manually. Is there a way to fix it?
This is the snippet from bash_rc:

```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

Thank you for help

---

### Post by The Cog on 2021-11-07
I think it's .bashrc, not .bash_rc.

---

### Post by tokacp on 2021-11-07
Yes, it is .bashrc. Any idea how to fix the issue from OP?

---

### Post by The Cog on 2021-11-07
That depends on what's wrong. The above (using .bashrc) works for me when I log in. What do you mean by 'on startup of the system'? Is this something different to the user login? Remember that as the system is booting, '~' won't map to your home directory. What's the context you are looking at?

---

### Post by tokacp on 2021-11-07
OK, what's wrong:
I have to manually call: source .bash_aliases each time I open new terminal.
How I'd like it to work:
I have a script in bashrc that would be automatically executed so I don't have to do anything and the aliases I have defined in bash_aliases are working.

---

### Post by Impavidus on 2021-11-07
The lines in ~/.bashrc to source ~/.bash_aliases were added automatically on my system when I created my user – which was ages ago, as I've transferred my home directory all the way from Ubuntu 10.04. The file ~/.bash_aliases wasn't created automatically, but when I create one manually, it works when I start a new terminal. So it should all work.

A few things you could check:
- Are all filenames correct? ~/.bashrc and ~/.bash_aliases must match exactly, including the dot and being in the home directory.
- Is your .bashrc completely executed? If there's an exit statement somewhere, execution may be terminated prematurely. As a simple check, add the line "echo bashrc complete" as the final line of your .bashrc. When you start a new terminal, it should print "bashrc complete".
- Do you indeed run a bash shell?

---

### Post by ActionParsnip on 2021-11-07
Does your user have read access to the aliases file?

---

### Post by The Cog on 2021-11-07
I don't see why you have a problem - it works for me. My .bashrc already contains the lines you showed, but I've had that file for years so it may not match recent versions. I just added a line so I can see if it's trying to source them:
```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    echo Sourcing aliases...
    . ~/.bash_aliases
fi
```

and in .bash_aliases, I put:
```
echo Settinging aliases...
alias foo='echo foofoofoo'

```
And when I open a new terminal, I see this:
```
Sourcing .bash_aliases...
Settinging aliases...
```
Which bits are you missing?

---

### Post by tokacp on 2021-11-07
OK, I know why is this happening. The reason is that I later in bashrc have a call to fish. How would I overcome that issue? That is, if I don't call fish from bashrc, all works as intended, but as soon as I put call to fish in bashrc again it stops working. I assume I should somehow let fish know about it? Via some fish config files?

---

### Post by tokacp on 2021-11-07
OK, managed to fix it. Simply adding the call to source aliases in config.fish did the trick.
Thank you all for helping me!

---

### Post by Impavidus on 2021-11-07
So you actually run a fish shell instead of a bash shell (although you run it inside the bash shell). That explains it. Environment variables get exported from bash to whatever runs in bash, but aliases don't, obviously. When you close the fish shell without closing the terminal, you will return to the bash shell where the aliases will work. There must be cleaner ways to do this.

If your problem is fixed, could you mark this thread as solved?

---

