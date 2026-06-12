---
title: "need to autumata some things... terminal apps"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by lunaluna on 2008-06-07
how can i automate a specific terminal procedure so it can stat on boot up and see it in terminal like top and some other "sudo" apps(in the same terminal-tabs-even better!) without having to this manual everytime?

---

### Post by rampageoberon on 2008-06-07
I've done this with an iptables script. I usually make the script and stick it in the directory /etc/init.d/ and then run the following to make them start on boot

```
sudo rcconf
```

You can try that, but I know there are some other possibly better ways of doing this

Hope that helps

---

### Post by lunaluna on 2008-06-07
maybe something like "save current session as <name>"
and the next time click the "specific session to start"
a really handy one so i don't have to that every time
i dont know if it is possible though...

---

### Post by lunaluna on 2008-06-09
....      bump

---

### Post by gr4nf on 2008-06-09
in ~, every user has a file called ".bashrc". Edit this, and it will be run on startup every time you log in. If you want to have some things automated every time you type a command, do the following:

I. make a new file in /usr/local/bin. Name it what you want the command to be.
II. put whatever shell commands in it that you want to be run on the entry of the command.
III. run the command "chmod +x" on whatever the file is (i.e. "chmod +x /usr/local/bin/(whatever)").
IV. test it in the terminal by typing the command.

---

