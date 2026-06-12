---
title: "PS1 issue, Unable change setting."
date: 2015-04-08
forum: New to Ubuntu
---

### Post by Phil_Jackson on 2015-04-08
Hello,

I'm a new user to Linux and have been trying to save a new prompt setting for bash. I have tried editing bash.bashrc with my new setting which is "[\d \t]\u@\h:\w\$" I'm using Ubuntu server 14.02.04 on vmWare. Another question is in the bash. Bashrc it says if I'm not going to use color edit etc/profile I have also tried editing that as well but I can't seem to get my setting to work after saving them and when I log back in. Not sure what else I can try, if I'm not explaining this correctly let me know and I will try again. Thanks for the help

---

### Post by Impavidus on 2015-04-08
/etc/bash.bashrc is the system-wide configuration, which is overridden by the user's configuration file. Try changing ~/.bashrc instead (the .bashrc file in your home directory).

---

### Post by Phil_Jackson on 2015-04-09
Thanks, that solved my problem. It's working perfectly now.

---

