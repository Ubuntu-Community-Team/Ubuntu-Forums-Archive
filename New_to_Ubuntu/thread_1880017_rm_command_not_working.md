---
title: "rm command not working"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by gouf on 2011-11-12
I'm taking an Introduction to Unix/Linux course at my community college, and for an assignment on learning basic scripting, we were asked to write a script that created five aliases and test them to see if they worked. During this process, I created an alias for 'rm' that went:

alias rm='del'

When I check my aliases, it lists the above alias, but when I try to use "rm" or "del" in the terminal, it tells me in both instances "del: command not found." I checked in /bin and the rm executable is still there, so I at least didn't delete that somehow.

Ultimately, I could just reinstall Ubuntu on my virtual machine, but I'd prefer to use that as a last resort if possible.

Thanks ahead of time!

---

### Post by m_duck on 2011-11-12
That'll be because the alias is the wrong way around. You have aliased the non-existent command 'del' to run when you type 'rm', which is why 'rm' no longer works, and 'del' doesn't work since, again, it's not a command.

The syntax is:```
alias what_you_want_to_write='what_you_want_to_run'
```So what I believe you are aiming for is:```
alias del='rm'
```

---

### Post by gouf on 2011-11-12
Wow, that is an embarrassing mistake. Thank you for helping me!

---

### Post by m_duck on 2011-11-12
Heh, we all make them. Glad I could help.

---

