---
title: "sh and bash"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by cat2005 on 2012-11-26
What is the difference between sh and bash when using a terminal?

I recently did a fresh install 64bit ubuntu then added KDE.  I made 2 accounts. 

My 1st account is my sudo person and his terminal shows "bash" at the top.  It will also show user@name$

My 2nd account is my regular daily use person and his terminal shows "sh" at the top.  It does not show user@name$.  It only shows $.

Why is that?  I previously had 32bit 10.10 and I don't think it behaved like that.  If it did then I never noticed.

---

### Post by Vaphell on 2012-11-26
sh (dash in case of ubuntu) and bash are flavors of shell, there are few others.
```
cat /etc/shells
```

Bash is more feature rich but some call it bloated (if that's even possible in case of a command line environment)
Roughly speaking bash and (da)sh are similar syntactically and sh scripts are more or less bash compatible, but not the other way around - bash specific syntax will fail in sh.

Apparently default shells for user accounts in your system are different and have their prompt set up differently
[http://askubuntu.com/questions/87853/what-is-default-shell-for-terminal](http://askubuntu.com/questions/87853/what-is-default-shell-for-terminal)

---

### Post by codemaniac on 2012-11-26
There is a environment variable called 'SHELL' that holds the name of your currently running shell.
see
```
echo $SHELL
```

---

### Post by rnerwein on 2012-11-26
> **cat2005 said:**
> What is the difference between sh and bash when using a terminal?

I recently did a fresh install 64bit ubuntu then added KDE.  I made 2 accounts. 

My 1st account is my sudo person and his terminal shows "bash" at the top.  It will also show user@name$

My 2nd account is my regular daily use person and his terminal shows "sh" at the top.  It does not show user@name$.  It only shows $.

Why is that?  I previously had 32bit 10.10 and I don't think it behaved like that.  If it did then I never noticed.

the sh is not really a sh. it's a symbolic link to the dash and the dash is the standard command interpreter for the system. conform with POSIX 1003.2 and 1003.2a specifications for the shell.
but in my opinion both has a little handicap: they are dynamic linked. in former times the
original shell was hard linked. why ? can you emagine the system crashes and a includes library has damaged ? NO shell !?  try "ldd bash" and "ldd dash"

---

### Post by CaptainMark on 2012-11-26
Here the code to change it either way ```
sudo usermod -s /path/to/shell username
```Replace /path/to/shell with either /usr/bin/bash or /usr/bin/sh and username with your username obviously
Did you create the 2nd user (sh) via the terminal, I did this once and any *ubuntu distro makes the default shell sh not bash,
If you created the second user with a GUI tool then KDE makes the default shell as sh, I don't use KDE but I wouldn't have thought this is the case as bash is a much more common default shell

---

### Post by cat2005 on 2012-11-27
> **CaptainMark said:**
> Here the code to change it either way ```
sudo usermod -s /path/to/shell username
```Replace /path/to/shell with either /usr/bin/bash or /usr/bin/sh and username with your username obviously
Did you create the 2nd user (sh) via the terminal, I did this once and any *ubuntu distro makes the default shell sh not bash,
If you created the second user with a GUI tool then KDE makes the default shell as sh, I don't use KDE but I wouldn't have thought this is the case as bash is a much more common default shell
 
Yes, I made the 2nd user using KDE's "Kuser" gui.  If I understand correctly, then I can change it to bash using your directions?

---

### Post by cat2005 on 2012-11-30
I could change it Kuser.  Solved.  No need for command line.

---

