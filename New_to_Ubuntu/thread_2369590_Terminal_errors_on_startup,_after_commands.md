---
title: "Terminal errors on startup, after commands"
date: 2017-08-24
forum: New to Ubuntu
---

### Post by schan1031 on 2017-08-24
I'm relatively new to ubuntu, have used it for a couple months now, and recently installed 16.04 on a new computer. Had an assortment of problems I've managed to sort out, but am currently stuck with one.

When I first open a terminal, I get the messages

```
__git_complete: command not found__git_ps1: command not found

```

After any command I run afterwards, I again get the message:

```
__git_ps1: command not found

```

I believe I have to edit my .bash_profile and source the correct files, but I'm not sure what location or which files.

I also want to bring the color and formatting back to my terminal, but adding a PS1 = etc line in my bash_profile doesn't apply until I source the bash_profile, and doesn't carry over if I open a new terminal.

---

### Post by &amp;KyT$0P# on 2017-08-24
What's in your [FONT=Courier New]~/.bashrc[/FONT] ?

---

