---
title: "complete-word"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by MikeL1227 on 2008-10-23
The tab key does not auto complete words and the up arrow does not scroll to previous commands - we're using cshell and nothing in the .login seems to be disabling things - anyone have thoughts?

---

### Post by The Cog on 2008-10-23
Those features are features of the bash shell I think, rather than general behaviour of all shells. It's the reason I always nag sysadmins to install bash on solaris hen I work on Sun boxes.

---

### Post by tCarls on 2008-10-23
csh uses ESC instead of tab for completion. You may need to run "set autolist" first. Not sure how to make the up arrow work. csh is really a pretty terrible shell. Do you at least have tcsh? It's the same as csh but with file line completion and command line editing. I would "cat /etc/shells" to see what my other options were.

---

### Post by estyles on 2008-10-23
Yeah, I remember using csh when I was in college, and eventually found out that we had zsh as an option, and it was so much better it blew my mind.  I could never figure out why anyone would use csh instead of zsh when they had a choice, nor why csh would be the default, for that reason - maybe it's lighter on memory?

I haven't played around with bash enough to know everything it can do, but since switching to ubuntu, it's become my favorite shell.

---

### Post by MikeL1227 on 2008-10-24
Thanks ALL - I'll look into switching to bash.

---

