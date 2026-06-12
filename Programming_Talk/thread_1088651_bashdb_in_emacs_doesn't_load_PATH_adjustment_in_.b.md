---
title: "bashdb in emacs doesn't load PATH adjustment in .bash_profile or .bashrc"
date: 2009-03-06
forum: Programming Talk
---

### Post by flylehe on 2009-03-06
Hi,
I like to add my own executable's path to PATH. While .bashrc is a place to go, I need to run my bash script under bashdb in emacs, which does not invoke a shell, so I always get the "command not found" error. I want to add the PATH adjustment in .bash_profile, but it's weird this file is not invoked during login in Ubuntu. To make sure the .bash_profile is read when login, I enable the 'Run command as a login shell' option. This way in typical shell session in emacs PATH is shown to be modified, however under bashdb in emacs PATH is still not including the executable path. Some way to fix this? Thanks!

---

### Post by unutbu on 2009-03-06
> I want to add the PATH adjustment in .bash_profile, but it's weird this file is not invoked during login in Ubuntu. 

I don't know what files bashdb reads, but if setting the PATH at login time will work for you, then editing or creating a ~/.profile rather than a ~/.bash_profile file should work:
```

export PATH=$PATH:/home/user/your/path/
```

---

### Post by flylehe on 2009-03-06
After adjusting PATH in .bash_profile, if I debug in terminal with bashdb, the PATH is the one modified; but if I debug in emacs with bashdb, the PATH is still the old one. So I guess the problem might be more emacs related than bashdb related?

---

### Post by flylehe on 2009-03-06
Thank you!
Adding the line to .profile works! What's the difference between .profile and .bash_profile under Ubuntu?

---

### Post by unutbu on 2009-03-06
Oh great! I'm glad it worked for you.

According the bash man page, bash does read .bash_profile. I don't know why it doesn't work. However, when you create a new user on Ubuntu, it is given a ~/.profile file, so I guess that is a strong hint Ubuntu wants you to use it for profile configuration :)

---

