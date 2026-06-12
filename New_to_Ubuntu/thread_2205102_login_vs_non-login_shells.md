---
title: "login vs non-login shells"
date: 2014-02-12
forum: New to Ubuntu
---

### Post by orrymr on 2014-02-12
Hi all,

I know that this has been covered in great depth, but I'm still having trouble understanding what's going on. From Wikipedia: 

```

 When started as an interactive login shell Bash reads and executes /etc/profile (if it exists). (Often this file calls /etc/bash.bashrc.)
 After reading that file, it looks for ~/.bash_profile, ~/.bash_login, and ~/.profile in that order, and reads and executes the first one that exists and is readable.
 When a login shell exits Bash reads and executes ~/.bash_logout (if it exists).
 When started as an interactive shell (but not a login shell) Bash reads and executes ~/.bashrc (if it exists). This may be inhibited by using the --norc option. The --rcfile file option will force Bash to read and execute commands from file instead of ~/.bashrc.

```

What I did to check this was to add a line at the end of each startup file which echoes out the name of that file. 
What I get when I enter the command bash is, predictably,

```

.bashrc

```

This makes sense since this is a non-login shell, and so it only checks my .bashrc file.

But if I enter bash -l, I get the following:

```

/etc/profile
.bashrc
.profile
.bash_profile

```

Now, since I only have a .bash_profile and .profile file I expected to see 

```

/etc/profile
.bash_profile

```

Why am I seeing .profile if .bash_profile exists, and more confusingly why am I seeing .bashrc at all?

Thanks guys

---

