---
title: "source command"
date: 2013-06-13
forum: New to Ubuntu
---

### Post by Generic1 on 2013-06-13
Hi,

when and for what I should use the command "source .bashrc" - what I can do with this command.
Thanks a lot for answers.

Best Regards,
Generic1

---

### Post by Lars Noodén on 2013-06-13
Well, the general answer is that you would [source](http://manpages.ubuntu.com/manpages/raring/en/man1/bash.1.html) a file when you want to execute it in the current shell environment.  That would include especially the paths and environment variables that you happen to have set in your current environment.  Now when you would want to do that, I can't think of any specific examples.  I can only remember that I have done it in the past, but not often.

source is built into the shell, usually bash for Ubuntu.

---

### Post by Cheesemill on 2013-06-13
The only reason to use 'source ~/.bashrc' is if you have edited your .bashrc file and want the new settings to take effect in the current terminal session instead of having to start a new session. As a side note you can use . as an alias for source....
```
. ~/.bashrc
```

---

