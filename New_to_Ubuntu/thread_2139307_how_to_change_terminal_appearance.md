---
title: "how to change terminal appearance"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by andrewjs18 on 2013-04-26
how do I set up the ubuntu terminal so all terminal sessions show the user's name, the computer and then their directory?

for example:
[IMG]http://i.imgur.com/VxnYG5l.jpg[/IMG]

but some other users on my server show up like this:
[IMG]http://i.imgur.com/RbopJOE.jpg[/IMG]

I'd like them to all be like the 1st image.

---

### Post by Impavidus on 2013-04-26
What the prompt (that's how that line is called) looks like is defined by the variable $PS1. It should be defined in .bashrc. Compare the .bashrc files of the users with nice prompts with those of users with ugly prompts and modify some .bashrc files.

---

