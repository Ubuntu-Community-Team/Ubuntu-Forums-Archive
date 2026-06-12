---
title: "Ubuntu terminal colors"
date: 2014-11-22
forum: New to Ubuntu
---

### Post by michal14 on 2014-11-22
I know this issue was raised multiple times, but I still don't get it. I run Ubuntu 12.04 (Virtualbox). When I type ls -la for example I cannot see proper colours for files. But after reloading . .bashrc it seems to work fine. After closing and reopening terminal,  again, I cannot see any colours in listing. What is causing it to reset back ?

Thanks

---

### Post by sisco311 on 2014-11-22
I will assume that you are using gnome-terminal as your terminal emulator and bash as your user's default shell.  

It seams that ~/.bashrc is not sourced when the shell starts. This is a normal behaviour if the terminal emulator starts a login shell. You can check if it starts a login shell or not under Edit -> Profile Preferences -> Command

If you want ~/.bashrc to be sourced when you start the terminal, uncheck the *Run command as login shell *box or source ~/.bashrc at the end of the ~/.bash_profile file

You can read more about the "dot files" here: [http://mywiki.wooledge.org/DotFiles](http://mywiki.wooledge.org/DotFiles)

---

### Post by Michal_Vantuch on 2014-11-23
Ok, thank you, that is working.

---

