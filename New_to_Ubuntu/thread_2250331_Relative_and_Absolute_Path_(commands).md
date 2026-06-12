---
title: "Relative and Absolute Path (commands)"
date: 2014-10-28
forum: New to Ubuntu
---

### Post by daniel208 on 2014-10-28
Hello! I am new to ubuntu and I have a simple question of commands...
I have an exercise that ask's me to copy a file from a relative path and an absolute path, what's the difference? and how can I structure my commands to do it?
thank you!

PS: is this a good topic on the fórum to talk about commands?

---

### Post by mastablasta on 2014-10-28
it is a place to talk about commands, but not a place to solve homework:

[http://en.wikipedia.org/wiki/Path_(computing)](http://en.wikipedia.org/wiki/Path_(computing))

also:
```
man cp
```

and:  [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by whitesmith on 2014-10-28
I usually don't help with homework, but I have a second.

A relative path is, obviously, relative to something, often the user's home directory. So, a relative directory off this would be ~/Documents. (By Linux convention, ~ refers to the user's home directory, as does $HOME). The equivalent absolute path would start at the root and meander to the same place: /home/your_user_name/Documents. Have a look at the 2nd reference in my sig line. Talking about the command line is OK here as long as you don't go into specifics about hacking the superuser's account, but I think we're safe in that respect for a while. Regards.

---

### Post by Impavidus on 2014-10-28
I never thought of ~/Documents being a relative path. ./Documents or simply Documents, yes, because these are relative to the current directory. Note that ~ (like ~username) is already expanded by the shell, so cp won't even know whether you used ~ or /home/username. Of course ~/ is somewhat more relative than /home/username, as it is user dependent. Let's call it a relatively relative path.

---

### Post by whitesmith on 2014-10-28
I chose the example because it's clear to a beginner who understands the root concept that ~/Documents is relative to something or else it would have be stated as /home/your-user-name/Documents or some such notation. Better examples might be cited, but perhaps at the cost of confusing a beginner. I love "relatively relative." Cheers.

---

### Post by chopra on 2014-10-30
> **whitesmith said:**
> I chose the example because it's clear to a beginner who understands the root concept that ~/Documents is relative to something or else it would have be stated as /home/your-user-name/Documents or some such notation. Better examples might be cited, but perhaps at the cost of confusing a beginner. I love "relatively relative." Cheers.

Taking the terms relative and absolute in the proper context, ./ and ../ are relative, ~/ and ~user/ are absolute, as their meaning doesn't depend on the present working directory.  Relative to the effective or logged in user (in the case of ~) is irrelevant with respect to how the terms are generally defined.

Here's a more interesting question: ~+/, in the bash shell, is synonimous with ./, and so is effectively relative path (although it seems rather pointless), but it expands to /...../ full path, so it's absolute from the command's perspective.  The same point applies to ~-/ in the bash shell, except it's the previous directory (still effectively relative).

Another question: What about the dash in the case of "cd -" ? The man page for bash, and other shells, refers to it as an "argument" for the cd command, but it seems more logical to consider it to be an option, rather than an argument.  After all, it's specific to the cd command, and it can't be combined with subdirectories (can't do cd -/subdirectory, but you can do cd ~/subdir, or cd ../subdir, etc.)

Chopra

---

